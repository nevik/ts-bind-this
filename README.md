# TS ! `bind` ! `this`

*[View the slides](https://nevik.github.io/ts-bind-this/) (or their source [on the `gh-pages` branch](https://github.com/nevik/ts-bind-this/tree/gh-pages))*

Let's say you have the following TypeScript class:
```typescript
class OrderItem {
    public constructor(public readonly name: string) { }
    public onOrder() { alert(`You're ordering: ${this.name}!`); }
}
```

And let's say you want to hook instances of `OrderItem` up to some UI, and make `onOrder()` a callback for a button.

If you're used to languages like Java or C#, you may expect that you can pass an instance method as a callback like so:
```typescript
const pizza = new OrderItem('pizza');
const pizzaButton = ...; // a <button> for pizza
pizzaButton.addEventListener('click', pizza.onOrder);
```

But when you run that code, and then click the `<button>`, the dialog that you get doesn't actually contain the name of the item (`'pizza'`).

Why?

Because the `this` in JavaScript (and therefore in TypeScript) doesn't behave like the `this` in Java or C#.

In particular, JS's `this` is not always the "owning instance" of a method, but more generally is the *context of a function call*.

---

## Sources for this talk

_Note: "archive" links lead to a corresponding entry in [The Wayback Machine](http://web.archive.org)._

* [MDN reference on `this`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) ([archive](http://web.archive.org/web/20170710073807/https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this))
* [_How can I preserve lexical scope in TypeScript with a callback function_](https://stackoverflow.com/questions/14471975/how-can-i-preserve-lexical-scope-in-typescript-with-a-callback-function) on StackOverflow ([archive](http://web.archive.org/web/20170324071026/https://stackoverflow.com/questions/14471975/how-can-i-preserve-lexical-scope-in-typescript-with-a-callback-function))
* [_TypeScript “this” scoping issue when called in jquery callback_](https://stackoverflow.com/questions/20627138/typescript-this-scoping-issue-when-called-in-jquery-callback) on StackOverflow ([archive](http://web.archive.org/web/20161125032152/http://stackoverflow.com:80/questions/20627138/typescript-this-scoping-issue-when-called-in-jquery-callback))
* [_'this' in TypeScript_](https://github.com/Microsoft/TypeScript/wiki/'this'-in-TypeScript) on the TS wiki ([archive](http://web.archive.org/web/20170516155857/https://github.com/Microsoft/TypeScript/wiki/'this'-in-TypeScript))
* [JohnWeisz/BoundMethods](https://github.com/JohnWeisz/BoundMethods) on GitHub - an example of binding instance methods with a custom TypeScript decorator

## Further Reading

_Note: "archive" links lead to a corresponding entry in [The Wayback Machine](http://web.archive.org)._

* _all this_ on Bjorn Tipling's blog ([archive](http://web.archive.org/web/20161019171720/http://bjorn.tipling.com/all-this))
* [_Gentle explanation of 'this' keyword in JavaScript_](https://rainsoft.io/gentle-explanation-of-this-in-javascript/) by Dmitri Pavlutin ([archive](https://web.archive.org/web/20161022161501/https://rainsoft.io/gentle-explanation-of-this-in-javascript/))
* ['this' in the TypeScript manual](https://www.typescriptlang.org/docs/handbook/functions.html#this) ([archive](http://web.archive.org/web/20170719211402/https://www.typescriptlang.org/docs/handbook/functions.html#this))
* (hard mode:) [Section on `this`](http://www.ecma-international.org/ecma-262/6.0/#sec-this-keyword) in the ECMAScript 2015 spec ([archive](http://web.archive.org/web/20170722143553/http://www.ecma-international.org/ecma-262/6.0/#sec-this-keyword))

## License

The written content in this project (e.g. slides, README, etc.) is licensed under the [Creative Commons Attribution Share Alike 4.0 license](https://creativecommons.org/licenses/by-sa/4.0/) (see `LICENSE.CC-BY-SA-4.0.txt`).

The example code provided in this project is licensed under the [MIT license](https://opensource.org/licenses/MIT) (see `LICENSE.MIT.txt`).
