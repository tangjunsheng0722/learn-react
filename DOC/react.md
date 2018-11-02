# REACT JS

##   1.什么是react：
```
    一个用于构建用户界面的JavaScript库
```
##   2.优点缺陷
```
    优点：
      1. 解析速度快：不直接对dom进行操作，引入了一个虚拟dom的概念，安插在jacascript逻辑和实际的dom之间，所以性能好。
      2. 跨浏览器兼容：虚拟dom为我们提供了标准化的API，帮我们解决了跨浏览器问题。
      3. 一切都是组件：代码更加模块化，复用性更高，可维护性更好。
      4. 单项数据流：Flux是一个用于在JavaScript应用中创建单向数据层的架构，它随着React视图库的开发而被Facebook概念化。
      5. 同构、纯粹的javascript：因为搜索引擎的爬虫程序依赖的是服务端响应而不是JavaScript的执行，预渲染你的应用有助于搜索引擎优化。
      6. 兼容性好：比如使用RequireJS来加载和打包，而Browserify和Webpack适用于构建大型应用。
    缺点：
      1.React本身只是一个V(MVC/MVVM)而不是一个完整的框架，需要和ReactRoute（待看），flux（待看）一起才能写大型应用。
      2. ...(再说)
```
##   3.入门知识点

### JSX语法
```
一种javascript的语法扩展，实现了js与html的混合使用，它完全是在javascript内部实现的
```
### 元素渲染
```
与浏览器的DOM元素不同，React 当中的元素事实上是普通的对象，ReactDOM可以确保浏览器DOM的数据内容与React元素保持一致
```
### 组件和属性对象（props）
 ```
 组件从概念上看就像是函数，它可以接收任意的输入值（称之为“props”），并返回一个需要在页面上展示的React元素。
 组件可以将UI切分成一些的独立的、可复用的部件，这样你就只需专注于构建每一个单独的部件。
 props是组件属性的集合，它是一个对象。
 ```
### 状态(state)与生命周期
> 状态与属性十分的相似，但是状态是私有的，他只受控于当前组件。不能直接的更改状态（state），setstate是改变组件状态的唯一方式。
```
 生命周期(钩子函数)： React生命周期分三种状态：1.初始化 2.更新 3.销毁
    初始化：
        getDefaultProps() （不常用） 设置默认的props，可以用defaultProps设置组件的默认属性
        getInitialState() （不常用） class语法构建组件是没有这个钩子函数的（怪不得没见过），可直接在constructor中定义this.state,此时可访问this.props
        componentWillMount()  只在组件初始化时调用，组件更新不调用，整个生命周期只调用一次，此时可以修改state
        render() react最重要的环节：创建虚拟dom，进行#diff算法#，更新dom树。不能修改state
        componentDidMount() 组件渲染后调用，只调用一次
    更新：组件state或者props不改变是不会触发这个环节的
        componentWillReceiveProps(nextProps) 组件接受新的props时调用
        shouldComponentUpdate(nextProps,nextState) react性能优化非常重要的一环。组件接受新的state或者props时调用，我们可以设置在此对比前后两个props和state是否相同，如果相同则返回false阻止更新，因为相同的属性状态一定会生成相同的dom树，这样就不需要创造新的dom树和旧的dom树进行diff算法对比，节省大量性能，尤其是在dom结构复杂的时候
        componentWillUpdata(nextProps, nextState) 组件初始化时不调用，只有在组件将要更新时才调用，此时可以修改state
        render()组件渲染
        componentDidUpdate() 组件初始化时不调用，组件更新完成后调用，此时可以获取dom节点
    卸载
        componentWillUnmount()  组件将要卸载时调用，一些事件监听和定时器需要在此时清除

```