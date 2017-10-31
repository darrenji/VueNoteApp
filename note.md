> 组件的构成

左边的Toolbar.vue组件，中间的NotesList.vue组件，右边的Editor组件，当然还有一个根组件App.vue。

> 根组件APP是如何交给页面文件index.html的？

是放在`main.js`中的一个Vue实例，交给index.html文件的。


```
new Vue({
    store,
    el: 'body',
    components: {
        App
    }
})
```
> 根组件App里有什么？

没啥，就是包含了其它子组件。


```
export default {
    components: {
        Toolbar,
        NotesList,
        Editor
    }
}
```
> 有哪些状态？

在state里有表示所有note的一个对象数组，表示当前note的一个对象。

> vuex是如何被Vue使用的？

首先要注册，然后把vuex的实例交给Vue实例。


```
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.Store({
    state,
    mutations
})
```

以上，通过`Vue.use(Vuex)`来注册vuex,然后导出以备在`main.js`中的Vue实例使用。

> Toolbar组件如何工作？

添加note的按钮。触动actions中的方法， dispatch mutations中的方法，在mutations中实际是在state中的对象数组里添加了一个对象，并把state中表示当前note的设置为新的note.

删除note按钮。触动actions中的方法，dispatch mutations中的方法，在mutations中实际是调用$remove方法从数组中删除对象，并重新设置当前note为数组对象的第一个元素。

收藏按钮。其实是在设置当前note的favorite属性。

> NotesList组件如何工作？

根据显示方式，从state中获取不同的数据和样式。有一个事件，实际是设置当前的note.

> Editor组件如何工作？

显示当前note的内容。其中的事件是设置当前note的text属性。









