# iBorder-Corner-Smoothing
iOS-like Rounded Corner in CSS

This project uses SVG curves exported from Figma after enabling Corner Smoothing. The curves are then dynamically generated with JavaScript to create smooth, continuous rounded corners. By leveraging the Houdini API, we can efficiently render these iOS-like rounded corner effects directly in CSS, making it easy to apply smooth, consistent corners in your projects.

iOS 风格圆角的 CSS 实现

这个项目利用了在 Figma 中启用 60% Corner Smoothing 后导出的 SVG 曲线，并通过 JavaScript 动态生成遮罩路径。结合 Houdini API，能够高效地在 CSS 中实现类似 iOS 图标的连续圆角效果。这样，你可以在项目中轻松地使用平滑且一致的 iOS 圆角。

## Demo

![](https://github.com/1-Dot/iBorder-Corner-Smoothing/blob/main/demo2.png?raw=true)

## Using

demo.html

```html
<script>
    (CSS.paintWorklet || paintWorklet).addModule('iborder.js')
</script>
<div class="iborder-test">
    <div>Test</div>
</div>
```

style.css

```css
/* Use a wrapper for shadow */
.iborder-test {
    filter: drop-shadow(10px 10px 4px #1a73e8);
}

.iborder-test>div {
    --iborder-radius: 36;
    background-color: red;
    mask-image: paint(iborder);
    width: 400px;
    height: 100px;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 2rem;
}

/* Use ::before as stroke */
.iborder-test>div::before {
    --iborder-radius: 36;
    --iborder-width: 4;
    background-color: #000; /*The color of the border*/
    mask-image: paint(iborder-s);
    content: "";
    inset: 0;
    position: absolute;
    pointer-events: none;
}
```

