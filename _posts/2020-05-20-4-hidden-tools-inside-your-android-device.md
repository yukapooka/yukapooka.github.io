---

layout: post
author: stephen
title:  4 Hidden Tools Inside Your Android Device
description: Rediscover your developer options
categories: [ Android, Tools, Debugging ]
image: https://cdn-images-1.medium.com/max/9216/0*Hd6p_WzmZ_I13qJ1

---

Every Android developer begins their journey by enabling the developer mode on a device. Without this option, you cannot install your application on your phone.

Although this menu can unlock your device for deployment, it also contains many debugging tools. Some day, one of them may pull you out of a dire situation.

So before diving into the code, let’s take a moment and peek at the available tools inside the developer options. I won’t present them all. Instead, I will focus on four that have helped me a lot over the years.

---

# 1. Optimize View Rendering

When building a layout, you have countless possibilities to declare your view’s structure. Don’t expect your teammates to code it the same way you would.

However, you must keep in mind how your view performs. We all enjoy smooth applications, and view rendering depends on how efficient your structure is.

During my first few years as an Android developer, I didn’t know how to optimize my layouts. One day, one of my customers wasn’t thrilled about how laggy his application was. I had to investigate the source of the problem.

And then I came across [this article](https://developer.android.com/topic/performance/rendering/inspect-gpu-rendering#debug_overdraw).

It helped me to optimize my view rendering drastically. By removing overdraws and flattening my layout hierarchies, my application became way smoother.

Without further ado, go to your developer options. Inside “Debug GPU overdraw,” select “Show overdraw areas.” Open your application and inspect all the reddish areas.

![Heavy overdraw — Photo from [Android Developers](https://developer.android.com/topic/performance/rendering/inspect-gpu-rendering#debug_overdraw)](https://cdn-images-1.medium.com/max/1070/1*echIZd37JsWIM4NyHlFgtg.png) | ![Light overdraw — Photo from [Android Developers](https://developer.android.com/topic/performance/rendering/inspect-gpu-rendering#debug_overdraw).](https://cdn-images-1.medium.com/max/1070/1*BtfA7RgBHUcDn2wNPn2oaQ.png)

I must admit I don’t use this often these days. Since the introduction of `ConstraintLayout`, building flat views has never been easier.

I still happen to toggle this option on occasion. It could help you identify:

- Overly complex views, no matter how flat subviews are.

- Unnecessary background overdraw.

---

# 2. Keep Your App Responsive

When your application is doing too much work on the main thread, the system will try to compensate by skipping some frames. Your user will end up with a hanging interface, which can only lead to frustration.

In the worst-case scenario, your application may not respond during a certain amount of time. The system then presents an Application Not Responsive (ANR) dialogue on the user’s screen. You can find more information [in this article](https://developer.android.com/training/articles/perf-anr).

Preventing ANR seems obvious, yet it’s often overlooked. When you’re developing an Android application, you tend to focus on crashes for two reasons:

1. They symbolize the worst user experience.

2. There exist several tools to track them, such as [Firebase Crashlytics](https://firebase.google.com/docs/crashlytics/get-started?platform=android).

The absence of metrics for detecting ANR doesn’t help either. They’re also harder to debug, as optimization rather than a code fix is required to prevent a crash.

With that said, you should know that there is a tool inside the developer options to track them. It’s called the StrictMode.

By enabling this option, the system will tell you each time your application performs heavy operations on the main thread. You can detect thread and VM policies. When you violate one of them, you’ll get red borders around your screen flashing at you.

Both this cue and logs in the console can help you pinpoint what you’re doing wrong. To go deeper into this topic, I recommend having a look at this article:

> [**Android Dev Tool: Best practice with StrictMode**](https://android.jlelse.eu/android-dev-tool-best-practice-with-strictmode-a023e09030a5)
>
> <small></small>

You could combine StrictMode with Profile HWUI Rendering. This option displays bars with a threshold you should not exceed. Each time you do, frames are being skipped.

---

# 3. Ensure Your App Restores Itself Gracefully

I like to say we can sort applications out from the way they handle memory pressure. We develop for an environment with a limited amount of memory, so we should expect the system to shut down any part of our application. You must anticipate how your components will behave when the system recreates them.

Because we have no control over the system, you’ll find this hard to simulate. Fortunately, we have a convenient tool called “Don’t keep activity.”

With this option enabled, go from background to foreground and discover how your activity behaves when recreated.

Not only will you detect improper behaviors, but this option could help you debug crashes as well. I cannot count how many times this tool helped me debug an irreproducible crash. From all the developer options I have tried, it’s probably my favorite tool!

Now you may forget to turn this option off. Since you can have weird behaviors, I recommend letting your testers know when it’s active. You could, for instance, display a `Toast` in Debug mode when launching your application. You can detect it with this extension method:

<script src="https://gist.github.com/StephenVinouze/6a3bd1a90b14cf4d4dfd9fed00ea86ce.js" charset="utf-8"></script>

---

# 4. Limit Background Processes

We found a way to test memory pressure on our activities. What about our background processes?

Thanks to StrictMode, we saw how vital leveraging threads is. You should focus on striving to lighten the main thread. You may want to create background processes via a `Service`, for instance.

Yet in a multi-threaded application, you cannot expect how many processors your users’ phones can handle.

Also, you’re not the only application creating background processes. And the Android system has to make room sometimes. Some of them will stay in memory for a while. Some will be killed.

You must ensure that your application handles your processes’ recreation well.

Right below the “Don’t keep activity” option, you can find the “Limit background processes” field. It lets you restrict how many of them you accept to run simultaneously.

Be aware that this option has gone beyond the developer’s grasp. Several users are enabling it on their phone for:

- Performance reasons

- Battery-saving

Not everyone owns the latest flagship. The Android ecosystem is vast, and you must always consider how your app performs in it.

---

# Play Around With the Developer Options

Don’t be shy and try them out. Don’t neglect these tools. They could be your best chance to debug your application.

And the good thing is you don’t even have to install anything! You only need to visit them. They suffer from weak exposure inside this hidden menu.

I’ve only highlighted four debugging tools, but you should investigate the others as well. Depending on what you’re working on, some of them may benefit you more than they did me.

So grab your phone, play around with them, and give your app a treat!
