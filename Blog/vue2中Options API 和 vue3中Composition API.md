## 概述

### Options API

在vue2中如何组织代码的，我们会在一个vue文件中methods，computed，watch，data中等等定义属性和方法，共同处理页面逻辑

缺点：一个功能往往需要在不同的vue配置项中定义属性和方法，比较分散，项目小还好，清晰明了，但是项目大了后，一个methods中可能包含20多个方法，你往往分不清哪个方法对应着哪个功能

![Options API](https://img-blog.csdnimg.cn/20200605155509976.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlc2ZzZWZncw==,size_16,color_FFFFFF,t_70)

### Composition API

在vue3的代码是根据逻辑功能来组织的，一个功能所定义的所有api会放在一起（更加的高内聚，低耦合），这样做，即时项目很大，功能很多，我们都能快速的定位到这个功能所用到的所有API

![Composition API](https://img-blog.csdnimg.cn/20200605160439258.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlc2ZzZWZncw==,size_16,color_FFFFFF,t_70)


## 两种方式对比

Composition API 主要灵感来源于React Hooks，目的是通过一组低侵入式的、函数式的 API，使得我们能够更灵活地「组合」组件的逻辑。

1.在组件比较复杂的情况下，可以将逻辑代码合到一起去，而不会被option强行分隔。这提高了代码质量的上限，同时也拉低了代码质量的下限。来自官方的一张对比图：
![官方Composition API对比图](https://segmentfault.com/img/remote/1460000024506510)

2.更好的进行复用。
在vue2中，想要复用部分逻辑的代码，都是通过mixin进去。但mixin进去的内容实际上很不直观，而且相同命名会被覆盖。而通过composition API，因为所有的方法都是引入的，可以将单独某个逻辑进行封装。例如对发送验证码倒计时功能进行封装。