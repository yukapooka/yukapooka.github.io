---

layout: post
title:  "Proper Fragment Communication in Android"
author: stephen
categories: [ Android, Fragment ]
tags: [red, yellow]
image: https://cdn-images-1.medium.com/max/10622/0*iTuGX5LepofXOCsv
description: "Don’t let the system hang up on your fragment’s listener"

---

You may have already read tons of articles covering this topic. It’s legitimate to wonder why I’d write an additional one.

I’m mentioning the *proper way* when, in fact, several solutions exist. The Android ecosystem has evolved since its beginnings, and you may wish to leverage [ViewModels](https://developer.android.com/topic/libraries/architecture/viewmodel?gclid=CjwKCAjwv4_1BRAhEiwAtMDLsgUPYGAEh1HAFlebOllUHvz0dEjmr2WnQlCQi4uA1r4FY5vx5vjtqBoCKSYQAvD_BwE&gclsrc=aw.ds) or even third-party libraries such as [RxJava](https://github.com/ReactiveX/RxJava) or [EventBus](https://github.com/greenrobot/EventBus).

If you are interested in knowing more about ViewModels, I’d recommend checking out this excellent article:

> [**Communicate between fragments and activity using LiveData**](https://android.jlelse.eu/communicate-between-fragments-and-activity-using-livedata-631526d6357a)
>
> <small></small>

Although all of the above present advantages, you may be in a situation where you are unable to use them. You’re then back to square one with the good old-fashioned interface solution.

With that said, working with interfaces works perfectly and remains the lightest approach possible, as it doesn’t require any third-party library.

However, developers often fail to configure them properly.

---

# Fragment-to-Activity Communication

Let’s assume you have an activity embedding a fragment. Upon a specific event happening on your fragment, you want to notify your activity so that it reacts to this event.

Here is a basic example with a fragment declaring an interface to propagate events to anyone implementing it:

<script src="https://gist.github.com/svinouze/1a8abeb67937a197fdbd09075c2efdbd.js" charset="utf-8"></script>

And the activity implementing the interface:

<script src="https://gist.github.com/svinouze/b5ffb47d4c8d1a8aebbe4a6768083e21.js" charset="utf-8"></script>

To settle the contract, the activity must declare itself to the fragment as a listener.

The question is: where do we call this method? You may, for instance, choose to call it inside the `onCreate` method.

What about if the fragment gets destroyed? Is the activity still listening to the fragment’s events?

The answer is no if the system, for any reason, destroyed the fragment and not the activity. Your activity will create another fragment instance but won’t re-attach the listener to it. No events from the fragment will be propagated to your activity, leaving it in a corrupted state.

To properly handle all cases, you must bind your listener when your activity is notified your fragment has been attached:

<script src="https://gist.github.com/svinouze/4b9101988107e048325d3f037133ece3.js" charset="utf-8"></script>

With this configuration, you tightly couple your activity with your fragment.

---

# Nested Fragment Communication

If you happen to have a fragment hosting another fragment, you can use the same mechanism to communicate between those two fragments. Fragments also offer an `onAttachFragment` callback to notify you when your child fragment is attached.

---

# Please Use the Proper Attach Callback

The `onAttachFragment` callback was recently added in [API 24](<https://developer.android.com/reference/android/app/Fragment#onAttachFragment(android.app.Fragment)>), then backported with the newest [androidX support package](<https://androidx.de/androidx/fragment/app/Fragment.html#onAttachFragment(androidx.fragment.app.Fragment)>). I still come across the usage of the former `onAttach` method inside the fragment that defines the interface.

<script src="https://gist.github.com/svinouze/4b9101988107e048325d3f037133ece3.js" charset="utf-8"></script>

Although both solutions are valid, I’d recommend using the newest, as it prevents the fragment from knowing which components implement its interface. Fragments should not be responsible for attaching their own listener.

Moreover, by doing this, you force the fragment’s caller to implement its interface — even though the caller doesn’t need to react to the fragment events. It’s simply bad architecture.

Anyway, the Android team updated the [official documentation](https://developer.android.com/training/basics/fragments/communicating) in that favor.

---

# Thoughts About Fragment Communication

I’ve had the chance to experiment with all of the solutions above. So far, I’ve been loyal to interfaces, as they provide a consistent mechanism — whether I need to communicate between fragments or between a fragment and an activity.

No matter how you proceed, you’ll be fine as long as you understand how a fragment’s lifecycle works.
