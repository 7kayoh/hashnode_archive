## UI Animations done right.

### Introduction

Whether you are UI coder or not, animating UI can be painful. Choosing the correct easing for the correct UI can take a lot of time, and usually the provided easings does not suit your UI well enough. Easings provided by Roblox in enumerations can not be modified, which can be disastrous if the easing is too exaggerated, or too weak.

It’s not only about easing. If you are animating an UI with an unpredictable value (user-defined, etc), maintaining the duration consistency for each animation can be difficult, and usually creates a hot mess in your codebase.

For one animation, it is fine, but if for multiple, uhhhh. Yeah, not a good idea.

### Why bother.

Why bother creating a new tweening library simply for custom easing? And why bother creating multiple formulas just to calculate the correct animation duration?

If you are encountering either these two problems, maybe it is time for you to learn a new concept –– **Spring motion**

<iframe src="https://player.vimeo.com/video/553697714?h=069a90dd7d&amp;app_id=122963" width="700" height="459" frameborder="0" scrolling="no"></iframe>

Spring-driven UI animation

Rather than defining an animation with time and easing. Define an animation with frequency and damping ratio. No matter how far away the end value is, the animation is always consistent, **it scales with the distance.**

With the damping ratio, you can create infinite possibilities on the animation behaviour –– whether to go overshoot, or smoothly. Solving the two problems we have mentioned in this article, completely.

### How

You do not need to study physics and reinvent the wheels to create spring motions. For Roblox, there are a couple of modules that does it for you. Such as [Spr from Fraktality](https://github.com/Fraktality/spr), or [Flipper from Reselim](https://github.com/Reselim/Flipper), et cetera.

Of course, it would be really hard to guess the animation behavior with only numbers. There is a [visualizer](https://www.desmos.com/calculator/rzvw27ljh9) for it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1646321917262/LCiGmcIqG.png)

Parameters view for the visualizer

In springs, the speed is faster when the frequency value is greater, where the damping ratio changes the converging behaviour, **in which, value lesser than 1 would create overshoot.**

That is pretty much how you implement spring motion for UI.

### Conclusion

Spring motion is great for UI animations, especially if you want custom easing, or want to have a consistent animation speed.

It’s also great for other applications, such as camera panning, camera manipulation, car physics, et cetera.

Of course, while spring motion seemed like an ideal solution for animations, it’s not always. Ask yourself is there any necessity to adopt spring motion before actually doing it. Sometimes it would backfire.