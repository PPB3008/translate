#Writing modular CSS (Part 1) —— BEM
#CSS模块化编写——BEM

[原文](https://zellwk.com/blog/css-architecture-1/?utm_source=CSS-Weekly&utm_campaign=Issue-257&utm_medium=web)

####导语
>15th mar 2017
>
Have you worked on large websites that spans more than a few pages? If you did, you probably realized the horrors of not conforming to a robust CSS architecture. You probably would also have researched on ways to write maintainable CSS.

>2017年3月15日
>
你是否曾经参与不止几个页面的大型网站的编写？如果你有，你应该已经意识到没有符合强大的CSS架构的恐怖。你应该也会知道何编写维护CSS的方法。

Since our industry is awesome, we don’t only have one recommended solution. Experts have jumped in and provided us with suggestions like BEM, OOCSS, SMACSS, Atomic Design and many others.

由于我们的行业是极好的，我们不仅只有一个推荐的解决方案，大神们投入了研究并给了我们许多解决方案，例如像BEM、OOCSS、SMACSS、Atomic的设计还有很多。

Now, instead of suffering from “I don’t know what to do”, the question becomes: “there’s so many ways. Which should I try?” Should I use everything, only one approach or create a custom architecture from the possible picks out there?.

因此现在，问题已经不是苦于“我不知道如何去做”，它已经变成了”我们有许多解决方案，我应该尝试哪个？“我应该尝试所有的方案，或者仅只用一个方案再或者创建了一个来从中可选择的自定义架构？

I started off with only one approach. Then, as I tried different approaches, I began to include what I thought made sense into my process. In this article, I want to share with you how I structure my CSS and why I do so. Hopefully, it’ll help you find your preferred method.

我开始只选择一个解决方案。之后，我试着用不同的解决方案，我开始把我认为有意义的东西包含在我的过程中。在这篇文章中，我想分享给你关于我如何组织CSS和我为什么这么做。我希望，这篇文章将帮助你找到你喜欢的解决方案。

##  What I look for in a good CSS Architecture  ##
##  当我在寻找一个出色的CSS架构  ##

I looked for four things when I cobbled together different methodologies to create my convention. They are:

当我把不同的方法连接到一起形成我自己的习惯时，我会寻找其四个特点。他们是：

1.I must instantly know whether it’s safe to edit a class without interrupting other any other CSS. This is most important, especially when I need to make quick changes. I don’t want to be afraid of changing cause I’ll break something else.

1.我必须要立即的知道它修改一个类名是否是安全的，有没有妨碍到其他的CSS。这个是非常重要的，尤其是当我需要去做个快速改变样式。我不想害怕改变会促使我破坏了其他结构的样式。

2.I must instantly know where a class fits in the grand scheme of things to prevent brain overload. This allows me to style things quickly without referencing back and forth.

2.我必须立即知道一个类被安置在这个伟大的工程什么地方去避免大脑被干预了造成负荷。它允许我快速改变样式，不用反复的引用style。

3.Classes must bloat HTML as little as possible since I switch off when I see a long list of class names.

3.类必须尽可能的少，因为当我看很长的类名我就会关机。

4，I must instantly know if a component uses JavaScript so I don’t accidentally break any the component if I changed its classes.

4.我必须立即知道如果一个组件使用了JavaScript，如果我改变了它的类名我不会意外地破坏到任何组件。

In my search, I found that a combination of BEM and namespacing fulfills the criteria I look for.

在我的探究中，我找到一个BEM和命名空间符合我期待的标准。
