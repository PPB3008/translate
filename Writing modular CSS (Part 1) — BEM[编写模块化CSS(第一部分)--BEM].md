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

##  Starting with BEM  ##
##  BEM初接触  ##

BEM is the foundation to my approach. If you’ve never heard of BEM before, it stands for block, element and modifier. It looks incredibly ugly when you first feast your eyes on it.


BEM是我方法的基础。如果你在这之前从未听说过BEM，它的代表有block,element和modifier。当你第一次看它的时候，它看起来非常的难受。

    .block { /* styles */ }
    .block__element { /* styles */ }
    .block--modifier { /* styles */ }

I hated BEM to a point where I didn’t even give it a chance when I first got to know about it. I can’t remember what made me try BEM, but I realized how powerful it is to work with it. Let me explain by going through the entirety of what BEM is (with my modifications, of course).

我讨厌BEM,以至于在我第一次知道它的时候没有给它机会。我不记得是什么让我尝试了BEM。但是我意识到在工作中使用它是如何强大。让我解释一下BEM的全部内容（当然，我有修改）


##  Block  ##

A block is a component. It’s a little abstract, so let’s use examples instead.

block是一个组织。它有点抽象，因此让我们举个例子来替代说明。

Let’s say you’re building a contact form. In this case, the form can be a block. In BEM, blocks are written as class names, like this:

假设你正在建立一个表单。在这种情况下，表单可以是一个块。在BEM，blocks被编写为一个类名，像这样：

    .form { /* styles */ }

The reason BEM uses a .form class instead of the <form> element is because classes allow for infinite reusability, even if the fundamental element should change in style.

原因是BEM使用了.form类代替了<form>元素是因为类名允许被无限复用，即使最基本元素应该改变样式。


Buttons are good examples of blocks that can contain different possible styles. If you set the background color of a button element to be red, all buttons are forced to inherit the red background. Following which, you have to fix your code by overwriting your button elements (and probably end up with broken limbs in the process).


Buttons被认为是一个blocks的好例子，因为它可以包含不同风格的样式。如果你给一个button元素的背景设置为红色，所有的buttons元素恐怕就被迫继承了红色的背景。接下来。你必须重构你的代码，让你的button元素可以被重写（而且可能在这个过程会有导致代码夭折的可能）

    button {
    background-color: red;
    }

    .something button {
    background-color: blue; /* 😱 */
    }

If styled a button with a .button class instead, you can choose whether to use the .button class on any button elements. Then, if you need a different background color, all you do is to change to a new class, say .button--secondary, and you’re good to go!

如果一个button的样式是用.button类代替，你可以选择是否使用.button在任何button元素上。因此，如果你需要一个不同的颜色，你所要做的就是更换一个新的类，例如.button-secondary，你可以做得很好。

    .button {
    background-color: red;
    }

    .button--secondary {
    background-color: blue; /* 😄 */
    }

This brings us to the next part of BEM — modifiers.

这就带我们到BEM的下一部分 —— modifiers

##  Modifiers  ##
##  模块化  ##


Modifiers are flags that change the appearance of a said block. To use a modifier, you add --modifier to the block.

Modifiers是改变一个block的外观的标志。为了使用modifier，你可以添加modifier到block上。

Moving on with the button example from above, the modified button would be named .button--secondary.

继续使用上面的按钮例子，这个被修饰的按钮将被命名为.button-secondary。

In traditional BEM, when you use a modifier, you’re supposed to add the block and the modifier into your HTML so you don’t rewrite your .button styles in the new .button--secondary.

在传统的BEM中，当你使用一个modifier，你讲支持添加一个block和modiier到你的HTML里，因此你不用重写一个.button的样式在你的新.button-secondary类里。

HTML

    <button class="button">Primary button</button>
	<button class="button button--secondary">Secondary button</button>

CSS

    .button {
    padding: 0.5em 0.75em;
    background-color: red;
    }

    .button--secondary {
    background-color: green;
    }


Notice how there’s no need to redeclare paddings in .button--secondary because it’s already been declared in button? This is sweet since BEM ensures you write DRY CSS without a ton of effort.

请注意没有必要去重新声明.button-secondary的内边距，因为它已经在button中声明了？这是BEM的可爱确保你不用写太多干巴巴的CSS。

However, I don’t really like declaring the .button class in my HTML since .button--modifier already tells me that it’s a .button with a --secondary flag. Ideally, my HTML should look like this instead:

可是，我不知道我真的不喜欢在我的HTML里宣布.button类在我的.button--modifier已经告诉哦我这个是.button类的副类的标志。在我喜欢的情况下，我的HTML应该是这样代替的：

    <button class="button">Primary button</button>
    <button class="button--secondary">Secondary button</button>

It’s much cleaner, isn’t it?
Unfortunately, without the .button class in the HTML, we have to revert back to a non-DRY CSS approach:

是不是整洁得多了？
不幸的是，没有.button类在HTML中。我们不得不回到没有dryCSS的方法：

    .button {
    padding: 0.5em 0.75em;
    background-color: red;
    }

    .button--secondary {
    padding: 0.5em 0.75em; /* 😱 */
    background-color: green;
    }

Ugh, anything that’s not DRY sucks 😢. But there are two ways to write DRY CSS without the extra HTML bloat!

啊，如此没有dry简直一脸糟糕。但是这里有两种方法写dryCSS不需要额外的膨胀HTML。

Method 1: Use a mixin
The first way, if you use Sass or any other preprocessor, is to use a mixin to encapsulate all code that needs to be reused. In our button example, we just need to write padding into a mixin. Here, I name the mixin after the block:

方法1：使用mixin

这是第一个方法，如果你使用过sass或者其他任何处理器，是可以使用mixin去封装需要重复使用的代码。在我们的button的例子中，我们只是需要在mixin中写padding。这里，我把mixin为

    @mixin button {
      padding: 0.5em 0.75em;
    }

    .button {
       @include button; // 😄
       background-color: red;
    }

    .button--secondary {
       @include button; // 😄
       background-color: green;
    }


Hooray! Now we have the best of both worlds!🎉🎉🎉

好哇！现在我们有两全其美的方法。

But but… what if I don’t use Sass?!

但是。。。如果我不使用Sass呢？

Chill! 😄. The second method I’m about to share uses vanilla CSS, so you can use it too!

打了个寒颤。第二个方法我分享使用了vanilla css，你也可以使用它。







