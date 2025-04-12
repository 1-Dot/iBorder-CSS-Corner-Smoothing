![](https://github.com/1-Dot/iBorder-Corner-Smoothing/blob/main/demo2.png?raw=true)

# iBorder
iOS-like Rounded Corners in CSS

iOS 风格圆角的 CSS 实现

This project uses SVG curves exported from Figma with 60% Corner Smoothing. JavaScript dynamically generates smooth, continuous corners. Using the Houdini API, these iOS-like effects render efficiently in CSS. It also supports borders and shadows with minimal code.

利用了在 Figma 中启用 60% Corner Smoothing 后导出的 SVG 曲线，通过 JavaScript 动态生成遮罩路径。结合 Houdini API，能够高效地在 CSS 中实现类似 iOS 图标的连续圆角效果。这样，你可以在项目中轻松地使用平滑且一致的圆角，同时支持用尽量少的行数为此圆角矩形创建描边和阴影，参见以下示例。

## Usage

`demo.html`

```html
<script>
    (CSS.paintWorklet || paintWorklet).addModule('iborder.js')
</script>
<div class="iborder-test">
    <div>Test</div>
</div>
```

`style.css`

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

/* Use ::before for stroke */
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

## Warning

Currently not working on Firefox and Safari