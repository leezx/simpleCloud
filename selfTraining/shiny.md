# shiny核心总结
- 整体框架：UI和server，UI里是用于设计layout的，确定输入layout和输出layout
- 输入layout，比如选参数等
- 输出layout，输出图像和table等
- server是用来接收参数、处理数据、然后输出到UI上显示的，逻辑非常清晰
- 其他：CSS等。

# key functions

## layout functions
- fluidPage() 液体页面
- fillPage(), fixedPage(), flowLayout(), navbarPage(), sidebarLayout(), splitLayout(), verticalLayout()
- [Application layout guide](https://shiny.rstudio.com/articles/layout-guide.html)

## 常见问题
### 设置整体的页面宽度，太宽很丑
在styles.css里设置`max-width: 1180px; margin:0 auto;`

### reactive的妙用，提速
如果总是实时处理参数的话，有时候非常费时，用reactive则可以避免这种尴尬。


# reference
- [Function reference version 1.5.0](https://shiny.rstudio.com/reference/shiny/1.5.0/)
- [shinyTutorial](https://bookdown.org/weicheng/shinyTutorial/ui.html) 
- [R powered web applications with Shiny (a tutorial and cheat sheet with 40 example apps)](http://zevross.com/blog/2016/04/19/r-powered-web-applications-with-shiny-a-tutorial-and-cheat-sheet-with-40-example-apps/)
- [R Shiny selectInput that is dependent on another selectInput](https://stackoverflow.com/questions/34929206/r-shiny-selectinput-that-is-dependent-on-another-selectinput)
- [Add Google Analytics to a Shiny app](https://shiny.rstudio.com/articles/google-analytics.html)
