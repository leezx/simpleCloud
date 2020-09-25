# voronoys shiny详细剖析
- [github repos](https://github.com/voronoys/voronoys_sc)

# website code tree
![](voronoys-tree.png)
- R shiny里的一切都是函数，函数间可以嵌套，搞清楚函数的输入输出。
- 根目录有3个函数，`ui, server, global`，代码都很简短，只是wrapper，分别放了 所有页面基本布局、所有独立页面的source code、packages全局变量以及source code。
- 以上只是wrapper，具体代码在`tabs`文件夹里，每个R代码都是一个独立页面，有自己的输入和输出逻辑。
- `functions`文件夹里有两个通用的绘图和数据处理函数，分工非常明确。
- `www`文件夹里是网站的基本素材（图像、logo、pdf），其中最重要的是`styles.css`，控制了网站所有的格式。
- `html`文件夹里是footer和Google分析的通用html文件，很好修改。
- 其他都是一些可有可无的文件

# 拆解首页
- `ui.R`
- `ui/home.R`，
- `server/home.R`，
- `styles.css`

# 拆解一个页面，分析逻辑
- 导航栏每个page的名称在UI里的title修改
- Elections page
- 位置`tabs/ui/eleicoes.R`
- 位置`tabs/server/eleicoes/eleicoes_brasil.R`

## 剖析
- UI比较简单直接，不同的tab分开写，在一个wrapper里source一下，`tabPanel`里面嵌套一个`tabsetPanel`，`tabsetPanel`继续嵌套`tabPanel`，最终的`tabPanel`比较简单，全部由`column`完成布局，选项框用了`shinyWidgets`的`pickerInput`和`actionBttn`；结果页面首先用了`conditionalPanel`输出默认结果提示。
- SERVER有点复杂，大量使用了`observeEvent`，根据输入参数选择法反馈，改变了后续的参数`updatePickerInput`；然后在`reactive`函数里对input的参数做了一些数据处理；然后用`eventReactive`来针对submit按钮执行操作；最后，把结果render到`output`。【这里renderLeaflet是针对地图的，我们用不到】



# 细节
- https://convertico.com/ - png to ico, the small logo in the tab
- [css图片居中(水平居中和垂直居中)](https://www.cnblogs.com/yiven/p/9645686.html)
- http://www.uugai.com/ - 免费logo设计
