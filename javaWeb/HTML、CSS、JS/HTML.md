# VsCode推荐插件

<img src="D:\software\Typora_imgs\QQ_1744382886585.png" alt="QQ_1744382886585" style="zoom: 25%;" />

> 1. 在vscode中输入！一键回车便会出现一套模板
>
> 2. vscode 格式化代码：alt + shift + f

# HTML

## 标签

### 标题标签

1. 一级标题  ==\<h1> ... \</h1>==

2. 二级标题 ==\<h2> ... \</h2>==

3. ...

4. 六级标题：==\<h6> ... \</h6>==

### 字体样式标签

1. 加粗： ==\<strong> ... \</strong>==

2. 斜体：==\<em> ... \</em>==

### 换行标签

1. ==\<br/>==或者==\<br>==

### `水平线`

1. ==\<hr/>==或者==\< hr>==

### `段落标签`

1. ==\<p> 段落内容 \</p>==

### `图像标签`

1. 常见图像格式：jpg、png、bmp、gif

2. ==\<img src="path" alt="text" title="text" width="x" height="y"/>==
   1. src: 图片url路径
   2. alt： 图像展示错误时，展示的信息
   3. title：鼠标悬停到图片上时，展示的信息
   4. width：图片宽度
   5. height：图片高度

### `链接标签`

1. ==\<a href="链接路径" target="目标窗口位置"> 链接文本或图像 \</a>==
   1. href：链接路径
   2. target：链接在哪个窗口打开，常用值：_self、\_blank
   3. 链接文本或图像：文本超链接、图像超链接

<span style="color:green;font-size:20px;">三种形式</span>

<img src="D:\software\Typora_imgs\QQ_1744387621221.png" alt="QQ_1744387621221" style="zoom:50%;" />

1. ==页面间链接==
2. ==锚链接==

<img src="D:\software\Typora_imgs\QQ_1744387645967.png" alt="QQ_1744387645967" style="zoom: 50%;" />



> 1. 上图通过#+锚链接名在==本页面==中进行跳转
> 2. 不同页面间，需要==先跳转到锚链接所在页面==，在跳转到锚链接位置
>    1. 格式为：`href = xxx.html#marker` xxx.html根据页面之间的相对路径

2. ==功能性链接==

<img src="D:\software\Typora_imgs\QQ_1744388226765.png" alt="QQ_1744388226765" style="zoom:50%;" />
	`mailto:`是固定的。

### `列表`

1. **列表分类**

   1. 无序列表

      > type: 黑心小圆点disc      circle 空心圆圈     square黑心小方块
      >
      > ![QQ_1744385427224](D:\software\Typora_imgs\QQ_1744385427224.png)
      >
      > <img src="D:\software\Typora_imgs\QQ_1744385258966.png" alt="QQ_1744385258966" style="zoom:33%;" />
      >
      > 
      >
      > 

   2. **有序列表**

      > type: 默认有序数字1， A， a， I， i 共五个类型
      >
      > <img src="D:\software\Typora_imgs\QQ_1744386047684.png" alt="QQ_1744386047684" style="zoom: 67%;" />
      >
      > <img src="D:\software\Typora_imgs\QQ_1744385767618.png" alt="QQ_1744385767618" style="zoom: 33%;" /><img src="D:\software\Typora_imgs\QQ_1744385790862.png" alt="QQ_1744385790862" style="zoom: 33%;" />
      >
      > <img src="D:\software\Typora_imgs\QQ_1744385799908.png" alt="QQ_1744385799908" style="zoom: 33%;" />
      >
      > <img src="D:\software\Typora_imgs\QQ_1744385908198.png" alt="QQ_1744385908198" style="zoom: 33%;" />

   3. **定义列表**

      > <img src="D:\software\Typora_imgs\QQ_1744386147383.png" alt="QQ_1744386147383" style="zoom: 50%;" />



### `表格`

<img src="D:\software\Typora_imgs\QQ_1744386311383.png" alt="QQ_1744386311383" style="zoom:40%;" />

### `表单`

> **表单语法**
>
> <img src="D:\software\Typora_imgs\QQ_1744386473042.png" alt="QQ_1744386473042" style="zoom:50%;" />
>
> **表单元素**
>
> 1. ==\<input>元素==
>
>    ​	<span style="color:red">输入类型</span>
>
>    > 1. ==text==
>    >    \<input type="text"> 定义供**文本输入**的单行输入字段
>    > 2. ==password==
>    >    \<input type="password"> 定义**密码字段**
>    > 3. ==submit==
>    >    \<input type="submit" value="submit"> 定义**提交**表单数据至**表单处理程序**的按钮。value不写值默认为‘提交’
>    > 4. ==radio==
>    >    \<input type="radio"> 定义单选按钮，常见一般是多个单选框公用一个相同的name值，这样就能达成多个选项但是只能选择一个的效果
>    > 5. ==checkbox==
>    >    \<input type="checkbox"> 定义复选框.复选框允许用户在有限数量的选项中选择零个或多个选项
>    > 6. ==button==
>    >    \<input type="button"> 定义**按钮**
>
>    ​	<span style="color:red">HTML5输入类型</span>
>
>    > <img src="D:\software\Typora_imgs\QQ_1744634263616.png" alt="QQ_1744634263616" style="zoom:50%;" />
>    >
>    > - ==number==
>    >   \<input type="number">用于应该包含数字值的输入字段
>    > - ==email==
>    >   \<input type="email"> 用于应该包含电子邮件地址的输入字段。
>    > - ==datatime-local==
>    >   \<input type="datetime-local"> 允许用户选择日期和时间（无时区）
>    > - ==tel==
>
>    ​	<span style="color:red">输入限制</span>
>
>    > | 属性      | 描述                               |
>    > | :-------- | :--------------------------------- |
>    > | disabled  | 规定输入字段应该被禁用。           |
>    > | max       | 规定输入字段的最大值。             |
>    > | maxlength | 规定输入字段的最大字符数。         |
>    > | min       | 规定输入字段的最小值。             |
>    > | pattern   | 规定通过其检查输入值的正则表达式。 |
>    > | readonly  | 规定输入字段为只读（无法修改）。   |
>    > | required  | 规定输入字段是必需的（必需填写）。 |
>    > | size      | 规定输入字段的宽度（以字符计）。   |
>    > | step      | 规定输入字段的合法数字间隔。       |
>    > | value     | 规定输入字段的默认值。             |
>
> 2. ==\<select>元素==
>    书写格式：
>
>    \<select name="cars">
>    	\<option value="volvo">Volvo</option>
>    	\<option value="saab">Saab</option>
>    	\<option value="fiat">Fiat</option>
>    	\<option value="audi">Audi</option>
>    \</select>
>
>    列表通常会把首个选项显示为被选选项。
>
>    可以通过添加 selected 属性来定义预定义选项。
>
> 3. ==\<textarea>元素==
>
>    \<textarea name="message" rows="10" cols="30">
>    	The cat was playing in the garden.
>    \</textarea>
>
> 4. ==\<button>元素==
>
> 
>
> **表单输入元素属性**
>
> <img src="D:\software\Typora_imgs\QQ_1744386495648.png" alt="QQ_1744386495648" style="zoom:50%;" />
>
> 1. checked | 复选框中默认选项
>
> 2. selected | 表单中列表框默认的选项
>
> **表单的高级应用**
>
> 1. readonly[^只读]
>
> 2. disabled[^禁用]
>
> 3. hidden[^隐藏域]
>
> <span style="color:red">所有在表单中的元素都必须加上name属性，部分需要加上value值，否则提交时提交上去会无法上传数据。</span>

---

## 注释和特殊字符 

1. 注释：\<!-- 里面为注释内容 -->
2. ' ' ：`&nbsp;` 
3. '>' ：`&gt;`
4. '<' ：`&lt;`
5. ' " ' ：`&quot;`
6. '©' ：`@copy;`

---

## 脚注

[^只读]:文本状态为只读，不能修改和删除
[^禁用]:可以通过css进行自定义禁用元素样式;<br/>不会响应任何用户操作，例如点击、输入<br/> 禁用的元素在表单提交时不会被包含在内，即其值不会被发送到服务器<br/>使用于所有表单元素，包括input、button、select、textarea



[^隐藏域]:隐藏域会随着表单一起提交，服务器可以看到，但是用户看不到
