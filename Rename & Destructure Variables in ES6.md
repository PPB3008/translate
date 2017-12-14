# Rename & Destructure Variables in ES6 #

[原文](http://wesbos.com/destructuring-renaming/)

Last post we took a look at an intro to destructuring. Let’s take a look at another use case which would be renaming your variables. Sometimes data comes back in some odd names, and you might not necessarily want to use a property key as the end variable name. Maybe you don’t like that variable name or it’s already taken in your scope.

最后一篇文章，让我们介绍一下解构赋值。让我们看下另个用例，将会重名命你的变量。有时候数据返回一些奇怪的名字，你可能不一定想使用这个属性键作为最终的变量名。也许你不一定喜欢那个变量名或者它已经在你的作用域以内。


```
const twitter = 'twitter.com';
const wes = {
  first: 'Wes',
  last: 'Bos',
  links: {
    social: {
      twitter: 'https://twitter.com/wesbos',
      facebook: 'https://facebook.com/wesbos.developer',
    },
    web: {
      blog: 'https://wesbos.com'
    }
  }
};
```

For example here, I already used twitter as a variable. I can’t use it again, but I’m stuck, because this object gives me twitter as a key and this object gives me twitter as a key. What you can do is you can rename them as you destructure them.

例如这个例子，我已经使用twitter作为一个变量。我不能再次使用它，但是我困住，因为这个对象给我twitter作为一个键值给我。你可以做的是，当你对他们进行拆解时，可以重命名他们。

So – I want the twitter property, but I want to call it tweet. I want the facebook property, but I want to call it fb.

因此 - 我想要twitter的性质，但是我想要把它叫做tweet。我想要facbook的性质，但是我想要把它叫做fb。


```
const { twitter: tweet, facebook: fb } = wes.links.social;
```

The above code will pull the wes.links.social.twitter into a variable called tweet and similarly for facebook.

上面的代码讲拉wes.links.social.twitter入一个被称为tweet和fb的变量。

[其实我想翻译得是这篇]http://wesbos.com/destructuring-objects/)，这篇知识点最近我有用到过，但是不知道是这个知识点。

