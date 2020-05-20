---

layout: post
author: stephen
title:  Stop Using Post/PostDelayed in Your Android Views
description: Prevent avoidable crashes
categories: [ Android, Handler, Lifecycle ]
image: https://cdn-images-1.medium.com/max/11074/0*BwWQN0ol_F5dP4dj
featured: true
hidden: true

---

Since its beginning, Android has provided a [Handler](https://developer.android.com/reference/android/os/Handler) API. As the documentation states, it allows you to deliver messages from a queue on a [Looper](https://developer.android.com/reference/android/os/Looper)’s thread.

```kotlin
Handler().postDelayed({
   doSomething()
}, delay)
```

This API is handy and yet so sneaky. Don’t let yourself be fooled when using it on a view. To understand where the danger lies, we need to dig deeper into the `View` class.

---

# Handlers for Views

`View` in Android leverages the `Handler` API. It acts as a passthrough with an inner `Handler` and exposes both `post()` and `postDelayed()` functions.

Have a closer look at its implementation (at the time I’m writing the article):

<script src="https://gist.github.com/StephenVinouze/63ac5307d5f0ea4c9aa47aa76c7881cc.js" charset="utf-8"></script>

I want you to pay attention to the Javadoc comment. The `removeCallbacks` line hints at something about removing the callback.

Let’s see it in action:

```
myView.postDelayed({
    myView.animateSomething()
}, delay)
```

In this example, I want to animate my view when a given delay expires.

Once the delay expired, what tells me my view still exists? That it’s still visible to the user?

You see, views have lifecycles. They may be destroyed at any time, either by the system or because your user navigates inside your app.

Since you queued a message inside a `Looper`, the system will deliver it if you don’t tell it to do otherwise. You expose your app to the possibility of a crash with a `NullPointerException`.

You understand now how *fundamental* this little comment is. I’ve seen so many crashes due to this API because developers failed to handle lifecycles.

---

# What If I Want to Delay an Action on a View?

You could still use this API and extract the `Runnable` declared inside your `Handler`. You’ll need to remove the callback whenever it’s relevant in your code, as hinted in the method’s comment.

```kotlin
private val animateRunnable = Runnable {
    myView.animateSomething()
}

myView.postDelayed(animateRunnable, delay)

// Somewhere in your code
myView.removeCallback(animateRunnable)
```

I advocate banning these methods because they’re misused or inappropriate.

For instance, if you’re using RxJava, you won’t need them anymore. Making a stream with either a delay or a timer is trivial. And you can dispose of your stream with ease.

```kotlin
val disposable = Observable.timer(delay, TimeUnit.MILLISECONDS)
    .subscribe {
        myView.animateSomething()
    }

// Somewhere in your code
disposable.dispose()
```

---

# What If I Need to Wait for Another Frame?

So far, I’ve only mentioned `postDelayed()`. To me, `post()` is by far the most misused API I’ve ever seen when applied to a `View`.

Why use `post()` when there’s no delay attached to it? Remember `Handler` is queuing messages in a `Looper`. Posting will queue the message and deliver it to the next frame.

Usually, I’ve seen developers using this because the view was not laid out. Imagine you want to animate a view as soon as it appears. You need its position and/or its size, depending on which animation you intent to achieve.

You must wait for the view to be measured. So you delegate the animation to the next frame and cross your fingers that the view will be ready. With this solution, two things stand out:

1. You have no guarantee your view will be measured on the next frame.

1. This code looks patchy as heck.

Like `postDelayed()`, there are more reliable mechanisms. You should use `ViewTreeObserver` instead, in particular the two following callbacks:

- [OnPreDrawListener](https://developer.android.com/reference/android/view/ViewTreeObserver.OnPreDrawListener) notifies you when a view is about to be laid out. At this point, the view has been measured

- [OnGlobalLayoutListener](https://developer.android.com/reference/android/view/ViewTreeObserver.OnGlobalLayoutListener) triggers an event whenever your view state changes

You must be careful when using those methods. You’re likely to create memory leaks if you forget to remove the listener once you performed your action.

```kotlin
myView.viewTreeObserver.addOnPreDrawListener(object: ViewTreeObserver.OnPreDrawListener {
    override fun onPreDraw(): Boolean {
        myView.animateSomething()
        myView.viewTreeObserver.removeOnPreDrawListener(this)
        return true
    }
})

myView.viewTreeObserver.addOnGlobalLayoutListener(object: ViewTreeObserver.OnGlobalLayoutListener {
    override fun onPreDraw(): Boolean {
        myView.animateSomething()
        myView.viewTreeObserver.removeOnGlobalLayoutListener(this)
    }
})
```

Even better, use [KTX extensions](https://developer.android.com/kotlin/ktx), and let them take care of the boilerplate for you.

```kotlin
myView.doOnPreDraw {
    myView.animateSomething()
}

myView.doOnLayout {
    myView.animateSomething()
}
```

That’s all folks! I may sound harsh when advocating to ban this mechanism. At the very least, I encourage you to chase them out and ponder whether they’re suited to the task.
