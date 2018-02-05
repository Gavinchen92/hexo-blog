---
title: redux的dispatch是异步的吗
date: 2018-02-05 14:29:54
tags:
---
  dispatch是异步的吗? 忘了在哪篇博文里面看到过说`dispatch`是异步的, 我有些怀疑, 但怎么反驳我也一下子说不上来.虽然以前看过`Redux`的源码, 也只是走马观花.

  今天正好有时间看了下`Redux`的源码, 正确答案是原生的`dispatch`是同步的, 但调用了`applyMiddleware`返回的`dispatch`可能是异步的.

  先看一下`dispatch`的源码
  ```js
    function dispatch(action) {
    if (!isPlainObject(action)) {
      throw new Error(
        'Actions must be plain objects. ' +
          'Use custom middleware for async actions.'
      )
    }

    if (typeof action.type === 'undefined') {
      throw new Error(
        'Actions may not have an undefined "type" property. ' +
          'Have you misspelled a constant?'
      )
    }

    if (isDispatching) {
      throw new Error('Reducers may not dispatch actions.')
    }

    try {
      isDispatching = true
      currentState = currentReducer(currentState, action)
    } finally {
      isDispatching = false
    }

    const listeners = (currentListeners = nextListeners)
    for (let i = 0; i < listeners.length; i++) {
      const listener = listeners[i]
      listener()
    }

    return action
  }
  ```
  一目了然, 中间没有任何异步操作

  然后我们再看看`applyMiddleware`返回的`dispatch`

  ```js
  function applyMiddleware(...middlewares) {
  return createStore => (...args) => {
    const store = createStore(...args)
    let dispatch = () => {
      throw new Error(
        `Dispatching while constructing your middleware is not allowed. ` +
          `Other middleware would not be applied to this dispatch.`
      )
    }
    let chain = []

    const middlewareAPI = {
      getState: store.getState,
      dispatch: (...args) => dispatch(...args)
    }
    chain = middlewares.map(middleware => middleware(middlewareAPI))
    dispatch = compose(...chain)(store.dispatch)

    return {
      ...store,
      dispatch
    }
  }
}
```

虽然传递给你的还是叫做`dispatch`的方法, 但是这个`dispatch`是经过`middlewares`层层加强点的, 所以此时`dispatch`是同步还是异步完全由使用者决定.

在我们日常开发的过程中, 我们会使用一些封装过的`redux`库, 比如`dva`, 如果你不去深究源码, 你就不知道此时是同步还是异步, 所以你把`dispatch`当作异步来处理的话是永远不会错的.
