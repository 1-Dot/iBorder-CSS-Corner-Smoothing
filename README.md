# iBorder-Corner-Smoothing
CSS iOS-like rounded corner masks using the Houdini API

在 CSS 中高效方便地使用类似 iOS 图标的曲率连续圆角，使用 Houdini API

## Demo

![](https://github.com/1-Dot/iBorder-Corner-Smoothing/blob/main/demo.png?raw=true)

## Using

```html
<script>
    (CSS.paintWorklet || paintWorklet).addModule('corner-smoothing.js')
</script>
<div class="iborder-test">
    <div>Test</div>
</div>
```

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
}
```

