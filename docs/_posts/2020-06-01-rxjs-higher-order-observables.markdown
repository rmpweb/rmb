---
layout: post
title:  "RxJS Higher-order Observables"
---

<svg id="Layer_1" style="margin-bottom: 20px" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 1605 500.41"><defs><style>.cls-1{fill:#4d4d4d;}.cls-2{fill:#ff0090;}.cls-3{fill:url(#radial-gradient);}.cls-4{fill:url(#radial-gradient-2);}.cls-5{fill:url(#linear-gradient);}.cls-6{fill:url(#linear-gradient-2);}</style><radialGradient id="radial-gradient" cx="4.78" cy="1197.95" r="1.83" gradientTransform="matrix(214.63, 0, 0, -153.54, -203.24, 184410.15)" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#f80090"/><stop offset="1" stop-color="#4d008e"/></radialGradient><radialGradient id="radial-gradient-2" cx="4.38" cy="1198.66" r="1.66" gradientTransform="matrix(239.23, 0, 0, -180.97, -221.53, 217410.73)" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#57008e"/><stop offset="0.29" stop-color="#5c008e"/><stop offset="1" stop-color="#f80090"/></radialGradient><linearGradient id="linear-gradient" x1="8.72" y1="1192.34" x2="9.99" y2="1190.63" gradientTransform="matrix(75.19, 0, 0, -59.93, 20.32, 72148.85)" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#f70090"/><stop offset="0.67" stop-color="#e50090"/><stop offset="0.83" stop-color="#d6008f" stop-opacity="0.2"/><stop offset="1" stop-color="#c10090" stop-opacity="0"/></linearGradient><linearGradient id="linear-gradient-2" x1="12.04" y1="1187.01" x2="11.62" y2="1187.45" gradientTransform="matrix(54.25, 0, 0, -29.62, 16.9, 35604.68)" gradientUnits="userSpaceOnUse"><stop offset="0" stop-color="#b2008f" stop-opacity="0.15"/><stop offset="0.4" stop-color="#f70090" stop-opacity="0.4"/><stop offset="0.65" stop-color="#f60090" stop-opacity="0.89"/><stop offset="1" stop-color="#ff0090"/></linearGradient></defs><title>hoo</title><path class="cls-1" d="M1993.54,606.71V552.78c0-13.37-10-24.21-22.35-24.21H1804.68c-12.34,0-22.35,10.84-22.35,24.21V603h-81.77l-34-14.81,19.73-47.94a26.12,26.12,0,0,0,.46-18.53A23.5,23.5,0,0,0,1675,508.27L1523.48,435.1a20.85,20.85,0,0,0-17.11-.5A23.25,23.25,0,0,0,1494,447.36l-22.88,55.58-43-18.73a20.81,20.81,0,0,0-8.34-1.76H1373.2V428.21c0-13.37-10-24.21-22.36-24.21h-166.5C1172,404,1162,414.84,1162,428.21v54.25h-16.51c-52.19,0-94.65,46-94.65,102.51s42.46,102.5,94.65,102.5h270l272.44,118.78a20.84,20.84,0,0,0,8.35,1.75h272.12c52.19,0,94.65-46,94.65-102.5C2063,658.43,2033.54,618.69,1993.54,606.71Zm-25.19,152.87H1700.56L1428.12,640.8a20.84,20.84,0,0,0-8.35-1.75H1145.48c-27.54,0-49.94-24.26-49.94-54.08s22.41-54.09,49.94-54.09h270l272.44,118.78a20.84,20.84,0,0,0,8.35,1.75h272.12c27.54,0,49.94,24.26,49.94,54.09S1995.89,759.58,1968.35,759.58ZM1827,577h121.79v26H1827Zm-301.35-87.8,110.71,53.45-11.31,27.45L1512.58,521Zm-319-36.77h121.8v30h-121.8Z" transform="translate(-458 -340.18)"/><path class="cls-1" d="M1146,547.43c-19.12,0-34.66,16.84-34.66,37.54s15.54,37.53,34.66,37.53,34.65-16.84,34.65-37.53S1165.07,547.43,1146,547.43Zm0,48.42c-5.55,0-10.06-4.88-10.06-10.88s4.51-10.89,10.06-10.89,10,4.88,10,10.89S1151.5,595.85,1146,595.85Z" transform="translate(-458 -340.18)"/><path class="cls-1" d="M1967.12,668c-19.11,0-34.66,16.84-34.66,37.54S1948,743,1967.12,743s34.66-16.84,34.66-37.53S1986.23,668,1967.12,668Zm0,48.42c-5.54,0-10-4.88-10-10.88s4.51-10.89,10-10.89,10.05,4.88,10.05,10.89S1972.66,716.38,1967.12,716.38Z" transform="translate(-458 -340.18)"/><path class="cls-2" d="M491.9,659.12c-26.65-141.71,43.79-278.38,205.46-296.56-22.29-23.82-52.75-24-66.76-21.1-24.75,7.88-24,23.89-52,44.58-27.9,15.93-41.91,3.73-62.24,20.25s-6.13,54-14.63,61.36c-8.45,14.63-34.64,27.67-39.41,46.16-3.94,23.64,10.7,40.53,10.14,60.79,1.68,16.89-16.82,26.44-14.16,40.13,8,22.36,23.31,35.81,30.54,42,1.66,1.17,3.42,4,3.1,2.37Z" transform="translate(-458 -340.18)"/><path class="cls-3" d="M779.58,463a10.7,10.7,0,1,1,10.7-10.7,10.7,10.7,0,0,1-10.7,10.7ZM498.14,674.58c-25.61-123.16,53.65-226.07,207.14-175.41,90.06,52.69,203.36,49.26,208.46,15.2,12.61-40.83-57.41-125-162.12-146.92-207.71-40.53-319.7,184-253.48,307.13Z" transform="translate(-458 -340.18)"/><path class="cls-4" d="M838.88,688.31c30.84,3.34,60.12-4.06,87.25-26.17-41,45.72-92.24,68.7-151,75,28.08,23.87,55.15,34.62,81.06,30-72,19.86-132.29-2-205.64-75-3.85,19.66,16.93,50.3,38.33,69.86-124.21-53.85-135.1-221.61,16.37-262.88-157-75.44-245.81,71.14-202.18,191.28,42.68,92.53,156.41,163.76,281.07,148.09,60.54-7.41,151-49.16,187.9-148.09-26,23.36-72.57,43.71-93.33,45.27,70.28-35.13,108.22-94.81,97.57-176.38-14.56,34.66-33.77,61.27-57.8,79.55,51-79.55,42.28-120.68,4.51-165.87,27,74.31-7.93,156.78-84.06,215.41Z" transform="translate(-458 -340.18)"/><path class="cls-5" d="M802.81,773.92c-5.33-1,12.09,7.05-21.6-1.86s-68-17.51-130.71-80c-3.85,19.66,16.93,50.3,38.33,69.86,57.8,40.31,18.49,21.46,106.55,51.9,7.07-14.07,7.43-26.57,7.43-39.91Z" transform="translate(-458 -340.18)"/><path class="cls-6" d="M690.85,457.41s7.65-11.3,10.63-16.39c3.65-6.25,9.26-17.63,9.26-17.63s-58.93-19.23-73.39-21.57c-45,11.67-45.12,30.5-20,59.33,2.8,3.21,73.49-3.74,73.49-3.74Z" transform="translate(-458 -340.18)"/></svg>




Observables that emit numbers, strings, objects or arrays are referred to as first-order observables. Higher-order observables are observables that emit an observable. There are scenarios where we need to process the results of a first observable into a second observable. For instance, consider the example below: 


{% highlight typescript %}
of(4, 1, 3)
.subscribe(x => of(x).pipe(delay(x * 1000))
    .subscribe(result => console.log(result))
);
{% endhighlight %}


However we should avoid nested subscribes. They can become complex and it would be difficult to unsubscribe observables. This is where high-order mapping operators come into play.

# High Order Mapping operators

High-order mapping operators map each value from an outer observable to a new inner observable, automatically subscribe to and unsubscribe from the inner observable. Ultimately higher-order mapping operators emit resulting values to the output stream.

The most commonly used operators are `concatMap`, `mergeMap` and `switchMap`

# ConcatMap


The `concatMap` operator processes items in sequence. When the outer observable emits items, concatmap subscribes to the first inner observable. Once it completes it emits the result to the output stream and then subscribes to the next inner observable. The process repeats until all items complete.

{% highlight typescript %}
of(4, 1, 3)
    .pipe(
        concatMap(x => of(x).pipe(delay(x * 1000)))
    .subscribe(x => console.log(x));
{% endhighlight %}

Use `concatMap` when you want to process items in sequence. For example getting data in sequence from a set of ids.

# MergeMap

The `mergeMap` operator processes items in parallel. Whenever the outer observable emits an item, `mergeMap` automatically subscribes to its inner observable. Any inner observable that completes emits the result to the output stream. Since items are processed in parallel, the result stream may not be in sequential order, but rather in the order of the inner observable completion. For instance, in the example below, `1` completes first, then `3` and then `4`.

{% highlight typescript %}
of(4, 1, 3)
    .pipe(
        mergeMap(x => of(x).pipe(delay(x * 1000))))
    .subscribe(x => console.log(x));
{% endhighlight %}

Use `mergeMap` when you want to process items in parallel, when order is not important.

# SwitchMap

The `switchMap` operator switches to the most recent item emitted. When the outer observable emits an item, `switchmap` automatically stops previous and subscribes to the new inner observable.


{% highlight typescript %}
of(4, 1, 3)
    .pipe(
        switchMap(x => of(x).pipe(delay(x * 1000))))
    .subscribe(x => console.log(x));
{% endhighlight %}

Use `switchMap` to stop previous observable and switching to the next one. For example, retrieving list data on sort change or page change.


