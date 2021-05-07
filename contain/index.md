## contain 属性允许我们指定特定的 DOM 元素和它的子元素，让它们能够独立于整个 DOM 树结构之外。目的是能够让浏览器有能力只对部分元素进行重绘、重排，而不必每次都针对整个页面。

# 语法
```
{
  /* No layout containment. */
  contain: none;
  /* Turn on size containment for an element. */
  contain: size;
  /* Turn on layout containment for an element. */
  contain: layout;
  /* Turn on style containment for an element. */
  contain: style;
  /* Turn on paint containment for an element. */
  contain: paint;

  /* Turn on containment for layout, paint, and size. */
  contain: strict;
  /* Turn on containment for layout, and paint. */
  contain: content;
}
```

## contain: size
    设定了 contain: size 的元素的渲染不会受到其子元素内容的影响，类似于overflow:hidden,但是超出的子元素可见

## contain: paint
    设定了 contain: paint 的元素的子元素不会在此元素的边界之外被展示，类似于overflow:hidden；
    设定了 contain: paint 的元素在屏幕之外时不会渲染绘制；
    通过使用 contain: paint， 如果元素处于屏幕外，那么用户代理就会忽略渲染这些元素，从而能更快的渲染其它内容。

## contain: layout
    设定了 contain: layout 的元素即是设定了布局限制，也就是说告知 User Agent，此元素内部的样式变化不会引起元素外部的样式变化，反之亦然。
    启用 contain: layout 可以潜在地将每一帧需要渲染的元素数量减少到少数，而不是重新渲染整个文档，从而为浏览器节省了大量不必要的工作，并显着提高了性能。
    使用 contain：layout，开发人员可以指定对该元素任何后代的任何更改都不会影响任何外部元素的布局，反之亦然。
    因此，浏览器仅计算内部元素的位置（如果对其进行了修改），而其余DOM保持不变。因此，这意味着帧渲染管道中的布局过程将加快。

## contain: strict | contain: content
    contain: strict：同时开启 layout、style、paint 以及 size 的功能，它相当于contain: size layout paint
    contain: content：同时开启 layout、style 以及 paint 的功能，它相当于 contain: layout paint

