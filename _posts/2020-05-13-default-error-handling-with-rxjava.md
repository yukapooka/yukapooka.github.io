---

layout: post
title:  "Default Error Handling With RxJava"
author: stephen
categories: [ Android, RxJava, ErrorHandling ]
tags: [red, yellow]
image: https://miro.medium.com/max/1400/0*ckMeIWhZpuOzAd3-
description: "Use RxJavaPlugins error handler instead of implementing onError"

---

When working with RxJava, you’ll sooner or later end up dealing with this exception:

```
io.reactivex.exceptions.OnErrorNotImplementedException: The exception was not handled due to missing onError handler in the subscribe() method call.
```

Handling errors matter. [RxJava](https://github.com/ReactiveX/RxJava) throws an exception at you because you failed to take care of the problem. You must handle the error, or else your app will crash.

Whether it’s an `Observable`, `Single`, `Compleatable` or even a `Maybe`, each RxJava stream gives you an onError callback to handle such cases. You must implement this callback everywhere.

However, you don’t treat all errors the same way. Many of them don’t need a particular treatment. The reason is: you cannot expect where an exception can occur. Errors could come from anywhere in your stream. For instance, some piece of code can stop the stream at any time, resulting in a `CancellationException`.

So, what to do inside your `onError` callback? Maybe you could add a log to keep a trace of the issue.

At least, you’re ensuring your application doesn’t crash. That’s defensive code.

Bear with me; I’ll show you another way to handle errors when you need it without risking your app from crashing.

---

# A basic use case

Have a look at the polling stream below:

<script src="https://gist.github.com/StephenVinouze/8b41037017bf829eb8e70d189a2656ba.js" charset="utf-8"></script><script>

Each second, we refresh our view. Notice I haven’t handled the error. Well, what could go wrong? It’s not as if the `interval` method from RxJava will fail!

Now let’s extract the polling mechanism into another class. I called it `PollableViewModel`. `PollableView` shouldn't be aware of how the view model handles the polling. Only its contract: it polls each second.

<script src="https://gist.github.com/StephenVinouze/0eab00cdc36509e388d2d46fbbafb4c1.js" charset="utf-8"></script>

For some dumb reason, the `startPolling` upstream operates on the interval result. By trying to divide it by zero, the stream delivers an `ArithmeticException`.
In the downstream, the stream will throw an error when `PollableView` will call `poll()`. Since we didn't implement the `onError` callback, we get the infamous `OnErrorNotImplementedException`.

![](https://miro.medium.com/max/1400/0*UxZTGfRwLB_BJGut)

---

# Default error handling

In this use case, I forced an exception by using dumb code. However, an exception could be thrown for a reason beyond your grasp.

You can always decide to implement the `onError` callback.

<script src="https://gist.github.com/StephenVinouze/c2027d0c2270ac596232407f0c84c952.js" charset="utf-8"></script>

Here we’re logging the exception with [Timber](https://github.com/JakeWharton/timber). We’re somehow handling the exception by redirecting it into the log console.

I see two significant drawbacks:

1. It’s tedious to implement a callback without doing any real error handling. You can log the error or leave the block empty. It doesn’t bring you anything related to this specific error.

2. You have no mechanism to ensure you have dealt with all your callbacks. Which means it could still crash somewhere. And let’s face it, you’ll forget some. To answer this issue, you could leverage lint rules such as [RxLint](https://bitbucket.org/littlerobots/rxlint). But again, not doing any error handling.

Or you could decide to use the `RxJavaPlugins` error handler. It will receive all exceptions wherever `onError` implementations are missing. You can state what to perform when such cases occur.

Add this code inside your `onCreate` custom `Application` class:

```kotlin
RxJavaPlugins.setErrorHandler(Timber::e)
```

We can decide like above to log all uncaught exceptions. You can delete all onError implementations which don’t do any error handling as well. The `RxJavaPlugins` error handler has you covered. No more `OnErrorNotImplementedException` crash!

![](https://miro.medium.com/max/1400/0*Qut4Sv3Q_QfcFCFZ)

---

# Improving stack traces

By using the default error handling, some may point out the loss of some information from the stack trace.

Since the RxJava stack trace doesn’t stand out for its clarity anyway, I’d recommend combining the default error handler with [RxDogTag](https://github.com/uber/RxDogTag). You’ll get logs targeting the faulty stream. A big help when debugging!

```kotlin
RxDogTag.install()
RxJavaPlugins.setErrorHandler(Timber::e)
```

# Handle errors where it matters

Adding a default error handling may seem error-prone. You would be right to say we’re hiding potential issues.

But logging errors everywhere won’t bring you justice either — better tackling errors where it matters and fallback in logging. You won’t see your application crashing. Not to mention the joy of not adding default callback implementations to each stream.

In this example, I’ve pictured a basic error handling. Logging won’t be near enough to prevent your code from corrupted behaviors. In my company, we added another logging layer that would send reports as non-fatal crashes on Firebase. This layer filters exception types depending on what’s relevant to log.

The `RxJavaPlugins` error handler is flexible enough to let you perform what's best for you. I hope it will save you both time and avoidable crashes.
