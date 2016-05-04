Introduction to Functions in JavaScript
---

## Objectives

- Explain what a function is in JavaScript
- Write a function from scratch
- Explain what a return value is in JavaScript

## JavaScript Function, what's your... um... function?

![junction](http://i.imgur.com/L9e2Pua.gif)

So far, we've been writing values directly into our browser's console. This is a great way to test out JavaScript functionality and to get a feel for how it handles different values and operations, but it's not super extensible. What if, for example, we wanted to log `"Hello, world!"` a bunch of times? We could write the statement out repeatedly:

``` javascript
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
console.log('Hello, world!')
```

But that quickly gets tiresome, and it's easy to see how even small programs would come to rival _War and Peace_ in length.

The good news is, there's a better way! We can use a function!

Functions are ways of giving the JavaScript interpreter instructions that it can run over and over again. When we run a function's instructions, we say that we have _called_ the function. In JavaScript, functions are written with the `function` keyword:

``` javascript
function doNothing() {}
```

As you can see, when we declare a function, we start with the `function` keyword, followed by a name for the function (it's `doNothing` above), followed by a pair of parentheses. Then we have a pair of curly braces. The above function, as it's name implies, doesn't do much. Copy the function into your browser's console and then run it by typing the function name followed by two parentheses: `doNothing()`.

...

Anything happen? No? Good! Nothing happened because even though we declared the function, we didn't give it any instructions. (Conventionally, a function that does nothing is called a "noop" (pronounced "no op") — sometimes they come in handy!)

Let's declare another function and this time give it something to do. We pass a function instructions between the curly braces — this is called the _function body_.

``` javascript
function sayHello() {
  console.log('Hello!')
}
```

Here we have a function called `sayHello`; its body reads `console.log('Hello!')`. When you declare the function, you'll notice that nothing's happened yet. That's because we have to call it! Enter the following in your console:

``` javascript
sayHello()
```

You should see `'Hello!'` printed to your console!

![it's working](http://i.giphy.com/BoBOKNtlR8rTi.gif)

### Getting into an argument

This is understandably pretty exciting, but what if I told you that functions get even cooler? Every function declared in this way gets an `arguments` object by default. Let's explore it!


``` javascript
function argue() {
  console.dir(arguments)
}

argue() // Arguments[0]
```

Hm, that's pretty boring. But what if we pass something to the function? **We can pass arguments to a function between the parentheses**, like so:

``` javascript
argue(1) // Arguments[1]
```

Whoa! Did you see that? The function's `arguments` now have a length -- if we open them up (that's why we're using `console.dir`!), we should see something like:

![arguments](https://curriculum-content.s3.amazonaws.com/skills-based-js/arguments.png)

Hmmm, what if we pass more than one argument? **We can separate arguments with a comma**:

``` javascript
argue("dog", "cat") // Arguments[2]
```

Cool! We now have two arguments to work with. In fact, we can pass any number of arguments this way:

``` javascript
argue("frog", "toad", "tadpole", 1, Math.PI) // Arguments[5]
```

The problem is, these arguments are hard to keep track of. Technically, we can access them like (in the above example), `arguments[0]` for `"frog"`, `arguments[1]` for `"toad"`, etc. (All of this within the function body, by the way.) Again, we can do better!

### Arguments, take two

We can give our arguments names so that we can reference them more easily from the body of the function. For example, let's build a function that lets us say hello to someone by name.

``` javascript
function sayHelloTo(name) {
  console.log(`Hello, ${name}!`)
}

sayHelloTo("Jane") // "Hello, Jane!"
sayHelloTo("R2-D2") // "Hello, R2-D2!"
sayHelloTo(1) // "Hello, 1!"

// ^ Note that in the above, JavaScript coerces the number 1 to the string "1"
```

That's pretty cool. Note that `name` is only available in the body of the function. If we just type `name` in the console, we'll get an error because it's undefined!

If we rewrite the function, we can see that the `arguments` object is intact:

``` javascript
function sayHelloTo(name) {
  console.dir(arguments)
  console.log(`Hello, ${name}!`)
}

sayHelloTo("Jane") // Check out the results in console!
```

This means that we can pass additional arguments to the function, but we won't have a nice way of referencing them in the function body:


``` javascript
sayHelloTo("Han Solo", 1, 2)
```

In general, this means that you won't need to worry about the `arguments` object — we should strive to write programs so that it's safe to rely on only explicitly referenced arguments — but it's still good to know that `arguments` exists.

### Return of the Value

These functions we've been coding are pretty cool, but they don't actually do a whole lot — mostly they print things to the console. We've seen how we can make them a little bit more dynamic with arguments, but how do we make them do something for us?

You've probably noticed that when you call a function in console, a little `undefined` shows up below it. That's because these functions don't return anything, so they return the default value for all JavaScript functions, `undefined`. If we want to return a value other than `undefined`, we have to tell the function to do so ourselves:

```javascript
function add(x, y) {
  return x + y
}
```

See that `return` keyword? That tells JavaScript to pass back the value specified after `return` to us. For example, if we run `add(1, 2)` in the console, we'll see `3` instead of `undefined`.

Try that a few times, and try writing a function of your own that returns something. Maybe instead of logging `\`Hello, ${name}\``, we can return it?

## Resources

- [MDN - Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
