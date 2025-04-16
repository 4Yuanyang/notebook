# HTML5新增结构元素

## 语义化标签

> <img src="D:\software\Typora_imgs\QQ_1744688840040.png" alt="QQ_1744688840040" style="zoom:50%;" />
>
> **section**与**article**的**区别**：section是不能单独使用，而article可以。例如一篇博客，文章内容可以用article来包裹[可以重复使用]，其中的评论区可以用section包裹，不能单独拿出来使用，因为评论区依赖于该博客。



# HTML5新增网页元素

> <img src="D:\software\Typora_imgs\QQ_1744693044114.png" alt="QQ_1744693044114" style="zoom:50%;" />
>
> ==**datalist**==: datalist也有列表的作用，但是需要结合**input**标签，使用input的list属性指向datalist属性id的值
>
> ==**time**==：定义日期或时间。提供机器可读的格式，便于搜索引擎、辅助工具等解析
>
> ==**mark**==：在视觉上向用户呈现那些需要突出的文字
>
> <img src="D:\software\Typora_imgs\QQ_1744694069714.png" alt="QQ_1744694069714" style="zoom:67%;" />
>
> <img src="D:\software\Typora_imgs\QQ_1744694156225.png" alt="QQ_1744694156225" style="zoom:50%;" />
>
> ==**audio**==：
>
> 1. **语法：** \<==audio== src="音频路径"> \</audio>
>
> 2. **使用：** 
>
>    ```html
>    <audio src="audio-file.mp3" controls>
>      您的浏览器不支持音频播放
>    </audio>
>    ```
>
>    或者
>
>    ~~~html
>    <audio controls>
>      <source src="audio-file.mp3" type="audio/mpeg">
>      <source src="audio-file.ogg" type="audio/ogg">
>      您的浏览器不支持HTML5音频
>    </audio>
>    ~~~
>
> 3. **常见属性**
>
>    | 属性       | 描述                                                         |
>    | :--------- | :----------------------------------------------------------- |
>    | `autoplay` | 布尔属性，页面加载后自动播放（可能被浏览器限制，尤其是移动端） |
>    | `loop`     | 布尔属性，音频循环播放                                       |
>    | `muted`    | 布尔属性，默认静音                                           |
>    | `preload`  | 预加载策略：`auto`（全加载）、`metadata`（仅元数据）、`none`（不加载） |
>    | `controls` | 显示浏览器默认控制条                                         |
>
> 
>
> ==**vedio**==：
>
> ​	参考上面audio，基本使用用法基本一致，多了两个属性分别是width和height，可以用来调整视频的布局展示。
>
> ***注意***：对于autoplay在浏览器中无法展示效果，是因为浏览器默认禁止了音视频自动播放，可以通过修改浏览器配置或者再加上**muted**属性即可，即静音播放。



# HTML5新增全局属性

> <img src="D:\software\Typora_imgs\QQ_1744701435159.png" alt="QQ_1744701435159" style="zoom: 50%;" />
>
> **hidden**：可以通过js脚本进行控制

# html5新增input类型

> <img src="D:\software\Typora_imgs\QQ_1744701719855.png" alt="QQ_1744701719855" style="zoom:50%;" />
>
> **email**和**url**可以直接对输入内容进行判断是否符合要求，省去了服务器压力

# html5新增表单常用input属性

> <img src="D:\software\Typora_imgs\QQ_1744718040814.png" alt="QQ_1744718040814" style="zoom:50%;" />
>
> **required**：通常在开发中不会使用该属性，因为每个浏览器中的required所对应的提示固定且无法修改样式，可以就会产生与当前主题不符的提示

# 总结

> <img src="D:\software\Typora_imgs\QQ_1744718204421.png" alt="QQ_1744718204421" style="zoom:67%;" />
