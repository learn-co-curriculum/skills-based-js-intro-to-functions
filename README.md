# Introduction to Functions in JavaScript

## Objectives

1. Explain what a function is in JavaScript
2. Write a function from scratch
3. Explain what a return value is in JavaScript

## JavaScript Function, what's your... um... function?

![junction](https://i.imgur.com/L9e2Pua.gif)

So far, we've been writing directly into our browser's console. This is a great way to test out JavaScript functionality and to get a feel for how it handles different values and operations, but it's not super extensible. What if, for example, we wanted to log `"Hello, world!"` a bunch of times? We could write the statement out repeatedly:

```js
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

```js
function doNothing() {}
```

As you can see, when we declare a function, we start with the `function` keyword, followed by a name for the function (it's `doNothing` above), followed by a pair of parentheses. Then we have a pair of curly braces. The above function, as its name implies, doesn't do much. Copy the function into your browser's console and then run it by typing the function's name followed by two parentheses: `doNothing()`.

...

Anything happen? No? Good! Nothing happened because even though we declared the function, we didn't give it any instructions. (Conventionally, a function that does nothing is called a "noop" (pronounced "no op") — sometimes they come in handy!)

Let's declare another function and this time give it something to do. We pass a function instructions between the curly braces — this is called the _function body_.

```js
function sayHello() {
  console.log('Hello!')
}
```

Here we have a function called `sayHello`; its body reads `console.log('Hello!')`. When you declare the function, you'll notice that nothing's happened yet. That's because we have to call it! Enter the following in your console:

```js
sayHello()
```

You should see `'Hello!'` printed to your console!

![it's working](https://i.giphy.com/BoBOKNtlR8rTi.gif)

### Saying hello

Let's write a function to say hello to Isabel — be sure to follow along!

```js
function sayHelloToIsabel() {
  console.log("Hello, Isabel!")
}
```

We can now call the function by entering `sayHelloToIsabel()` in console — try it!

Now what if we want to say hello to Sofia? Well, we could write another function:

```js
function sayHelloToSofia() {
  console.log("Hello, Sofia!")
}
```

which we can call by entering `sayHelloToSofia()`.

Okay, now we're going to say hello to Brendan — you know the drill!

```js
function sayHelloToBrendan() {
  console.log("Hello, Brendan!")
}
```

Now let's call all three!

```js
sayHelloToIsabel()
sayHelloToSofia()
sayHelloToBrendan()
```

While these functions are undoubtedly useful, they're only useful if we only talk to Isabel, Sofia, and Brendan. Every time we want to greet someone new (or say something other than "Hello," for that matter), we need to define a new function.

What if there was some way to take what's similar about these functions — the fact that they all call `console.log()` with "Hello," a name, and an exclamation point — and substitute what's different (the name) as we go?

Turns out, we can! We can use something called an _argument_ to pass information to a function.

### Getting into an argument


**We can pass arguments to a function between its parentheses**, like so (follow along in console!):

```js
function doSomething(thing) {
  console.log(thing)
}

doSomething('anything')
```

Pretty cool, right?

### Saying hello, again

We found it kind of tiresome to say hello to everyone individually above — what if we told you there's a better way?

```js
function sayHelloTo(firstName) {
  console.log(`Hello, ${firstName}!`)
}

sayHelloTo('Isabel') // "Hello, Isabel!"
sayHelloTo("Jane") // "Hello, Jane!"
sayHelloTo("R2-D2") // "Hello, R2-D2!"
sayHelloTo(1) // "Hello, 1!"

// ^ Note that in the above, JavaScript coerces the number 1 to the string "1"
```

That's pretty cool. We're using what's called a _parameter_, in this case `firstName` in `function sayHelloTo(firstName)`. **Parameters** are placeholders that we put between the parentheses when declaring a function. When we invoke that function, we can pass **arguments** to the invocation (e.g., `'Isabel'` in `sayHelloTo('Isabel')`) that get stored as local, function-level variables that are available anywhere in the function body. Essentially, the arguments are the actual values that we pass to the function, and the parameters are the named references where we store those passed-in values. An argument can be any JavaScript expression — any piece of JavaScript code that evaluates to a value — from something as simple as `5` or `'Avi'` to something as complex as an entire function.

Note that we can only access arguments within the body of the function by referring to the parameter name, such as ``console.log(`Hello, ${firstName}!`)`` in the above code. If we try to call `firstName` outside of our `sayHelloTo()` function in the JavaScript console, we'll see a `ReferenceError` telling us that `firstName` is not defined.


### Saying something new

What if we want to say something other than "Hello"? Well, we can move the greeting to a parameter as well:

```js
function say(greeting, firstName) {
  console.log(`${greeting}, ${firstName}!`)
}
```

After entering the above in console, let's try `say("Goodbye", "Julio")` — we should see "Goodbye, Julio!" in the browser's console.

But what if we wanted to switch the order and say something like, "Julio, hello!"? Hm, that sentence still has two parts — let's try it:

```js
say("Julio", "hello")
```

You should now see "Julio, hello!" in console. What's going on? "Julio" is a name, not a greeting!

You've just illustrated an important point: **what matters with functions is not what the argument is _called_, but its location in the arguments list.**

### Return of the Value

These functions we've been coding are pretty cool, but they don't actually do a whole lot — mostly they print things to the console. We've seen how we can make them a little bit more dynamic with arguments, but how do we make them do something for us?

```js
function add(x, y) {
  return x + y
}
```

Now try `add(1, 2)` in console. See that? We got `3` back! What if we try `add(80, 9000)`? Whoa! We got 9080!

When we return inside a function, we're giving that value back to the world outside the function. Let's try something a little different: let's rewrite our `say()` function from above so that now instead of `console.log()`-ing what it says, it returns it.

```js
function say(greeting, firstName) {
  return `${greeting}, ${firstName}!`
}
```

(Note that we've used a template literal, which we learned about previously, in order to make our string easier to read.)

Now when we call `say("Hello", "Sofia")` we'll see `"Hello, Sofia!"` instead of `Hello, Sofia` and then `undefined` in the browser's console.

What's happening here? These differences seem _awfully_ subtle. Well, while we're working in the console, they _are_ subtle. The console tells us that when we return `${greeting}, ${firstName}`, we're returning a string by wrapping it in `"`; but when we just call `console.log("Hello", "Chuck!")`, we instead see only `Hello, Chuck!` (without quotes), followed by `undefined`.

When we call a function in the browser's console, the browser always tells us what the function returns. Thus, if we return `"Hello, Chuck!"`, the browser tells us, "I'm returning a string, and it looks like this." If we don't return anything from a function, however, the function returns the default value, `undefined` — so the browser says, "Hey, I'm returning undefined."

There's one last thing you should know about `return`. Let's say we wanted both to `return` and log a string in our `say()` function, we might try writing:

```js
function say(greeting, firstName) {
  return `${greeting}, ${firstName}!`
  console.log('I was called!')
}
```

Then we can call it with `say("Howdy", "partner")` — but we only see `"Howdy, partner!"` in the browser console, meaning that we only `return`-ed the value — we never logged "I was called!".

This is because `return` **ends the execution inside the function**, meaning that if we return, nothing will happen after that. To both log and return like we want to, we can switch the order around:

```js
function say(greeting, firstName) {
  console.log('I was called!')
  return `${greeting}, ${firstName}!`
}
```

Now the function should work as expected: `say("Howdy", "partner")`.

## Your turn!

Try rewriting some of the functions that we've written in this lesson to get used to the difference between `return`-ing and printing (`console.log()`-ing) to console. Try writing a function of your own that returns something. Maybe instead of logging ``Hello, ${firstName}``, we can return it?

## Resources

- [MDN - Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

<p class='util--hide'>View <a href='https://learn.co/lessons/skills-based-js-intro-to-functions'>Intro to Functions</a> on Learn.co and start learning to code for free.</p>
