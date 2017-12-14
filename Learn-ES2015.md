#Learn ES2015
#学习ES2015

[原文](https://babeljs.io/learn-es2015/)

###   Introduction　　
###   介绍

ECMAScript 2015 is an ECMAScript standard that was ratified in June 2015.
ES2015 is a significant update to the language, and the first major update to the language since ES5 was standardized in 2009. Implementation of these features in major JavaScript engines is underway now.

See the ES2015 standard for full specification of the ECMAScript 2015 language.


ECMAScript 2015是一门在2015年6月被批准的ECMAScript语法。ES2015是语言的重大更新，这是自2009年ES5标准化以来第一次重大更新。主要实现现在正在进行中的JavaScript引擎的特点。

请参阅2015的ES2015标准，以了解ECMScript 2015标准化。

###   ECMAScript 2015 Features   ###
###   ECMScrippt 2015 特性   ###

####    Arrows and Lexical This    #####
####    箭头和this    ####

Arrows are a function shorthand using the => syntax. They are syntactically similar to the related feature in C#, Java 8 and CoffeeScript. They support both expression and statement bodies. Unlike functions, arrows share the same lexical this as their surrounding code. If an arrow is inside another function, it shares the “arguments” variable of its parent function.

箭头是一个缩写函数使用 => 语法。它们的语法构成上和C#、Java 8、CoffeeSCript的特性有相似的联系。它们都支持表达和声明结构。和函数不同，箭头和周围的代码共享相同的词法。如果一个箭头里面包括另个函数，它共享父函数的参数变量。

    // Expression bodies
	var odds = evens.map(v => v + 1);
    var nums = evens.map((v, i) => v + i);

	// Statement bodies
    nums.forEach(v => {
     if (v % 5 === 0)
      fives.push(v);
    });

    // Lexical this
    var bob = {
      _name: "Bob",
      _friends: [],
      printFriends() {
        this._friends.forEach(f =>
          console.log(this._name + " knows " + f));
     }
    };

    // Lexical arguments
    function square() {
     let example = () => {
      let numbers = [];
      for (let number of arguments) {
        numbers.push(number * number);
     }

      return numbers;
    };

    return example();
    }

    square(2, 4, 7.5, 8, 11.5, 21); // returns: [4, 16, 56.25, 64, 132.25, 441]

####    Classes    ####
####    类    ####
ES2015 classes are a simple sugar over the prototype-based OO pattern. Having a single convenient declarative form makes class patterns easier to use, and encourages interoperability. Classes support prototype-based inheritance, super calls, instance and static methods and constructors.

ES2015类是一个简单基于面对对象原型修饰的类。有个简单方便的说明表格让类的结构更容易被使用，并鼓励互通性操作。类支持基于原型的继承，实现静态方法和构造类。


    class SkinnedMesh extends THREE.Mesh {
      constructor(geometry, materials) {
        super(geometry, materials);
        this.idMatrix = SkinnedMesh.defaultMatrix();
        this.bones = [];
        this.boneMatrices = [];
     //...
      }
      update(camera) {
     //...
        super.update();
      }
      static defaultMatrix() {
        return new THREE.Matrix4();
      }
    }

####    Enhanced Object Literals    ####
####    加强对象字面值    ####

Object literals are extended to support setting the prototype at construction, shorthand for foo: foo assignments, defining methods and making super calls. Together, these also bring object literals and class declarations closer together, and let object-based design benefit from some of the same conveniences.

对象字面量延伸到支持设置原型构造,foo:foo赋值的简写，定义方法和调用。总之，这些也带来了对象字面量和类的声明更为紧密，让基于对象设计的行为有着同样的方便性。

    var obj = {
    // Sets the prototype. "__proto__" or '__proto__' would also work.
       __proto__: theProtoObj,
    // Computed property name does not set prototype or trigger early error    for
    // duplicate __proto__ properties.
      ['__proto__']: somethingElse,
    // Shorthand for ‘handler: handler’
      handler,
    // Methods
      toString() {
     // Super calls
       return "d " + super.toString();
    },
    // Computed (dynamic) property names
      [ "prop_" + (() => 42)() ]: 42
    };

The __proto__ property requires native support, and was deprecated in previous ECMAScript versions. Most engines now support the property, but some do not. Also, note that only web browsers are required to implement it, as it's in Annex B. It is available in Node.

__proto__性质需要本地支持。它在之前版本ECMAScript中被弃用。现在大多数引擎都支持这一特性，但是也有一些不支持。注意仅仅只要在web浏览器是必须要实现它。在附录B中，它可用到节点。


####    Template Strings    ####
####    模板字符串    ####

Template strings provide syntactic sugar for constructing strings. This is similar to string interpolation features in Perl, Python and more. Optionally, a tag can be added to allow the string construction to be customized, avoiding injection attacks or constructing higher level data structures from string contents.

