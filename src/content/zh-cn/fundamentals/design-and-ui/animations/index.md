project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description: 更好地了解动画及其在现代应用和网站中的用途。

{# wf_review_required #}
{# wf_updated_on: 2014-10-20 #}
{# wf_published_on: 2014-08-08 #}

# 动画 {: .page-title }

{% include "web/_shared/contributors/paullewis.html" %}


动画是使 Web 应用和网站吸引人的重要因素。 用户希望有快速响应和高度交互的用户界面。 但是，为界面设置动画未必很简单。 什么应设置动画，何时显示，以及动画应有哪种感觉？

## TL;DR {: .hide-from-toc }
- 使用动画作为一种给项目增加活力的方式。
- 动画应支持用户交互。
- 要注意设置动画的属性；有一些属性比其他属性开销更大！


## 选择合适的内容来设置动画

出色的动画可增添一层享受，增加项目对用户的吸引力。 可以将您喜欢的几乎所有内容设置动画，不管是宽度、高度、位置、颜色、背景，但您需要注意潜在的性能瓶颈，以及动画将如何影响您的应用的个性。 卡顿或选择不当的动画可能对用户体验产生负面影响，因此动画需要高性能并且恰当。

## 使用动画来支持交互

不要仅仅因为您可以做动画就随便做；它只会惹恼用户并妨碍操作。 相反，要有策略地放置动画以_增强_用户交互。 如果用户点击菜单图标，则让菜单从页面侧边伸出，或如果他们点击按钮，则可以使用少量辉光或弹跳来确认交互。 注意避免不必要地打断或妨碍用户活动的动画。

## 避免为开销大的属性设置动画

唯一比错误放置的动画更糟的事情是导致页面卡顿的动画。 这将让用户觉得失望和不悦，并且可能希望您根本不必费心去设置动画！

改变一些属性的开销比改变其他属性要多，因此更可能使动画卡顿。 因此，例如，与改变元素的文本颜色相比，改变元素的`box-shadow`将需要开销大很多的绘图操作。 改变元素的`width`可能比改变其`transform`要多一些开销。

您可以在[动画和性能](animations-and-performance.html) 指南中阅读有关动画性能考虑事项的更多内容，但是如果想要TL;DR，则坚持使用转换和透明度改变，以及利用`will-change`。 如果想确切知道给指定的属性设置动画会触发什么效果，请查阅[CSS 触发器](http://csstriggers.com)。


