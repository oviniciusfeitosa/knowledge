# Cascading Style Sheets(CSS)

## [Position](https://developer.mozilla.org/pt-BR/docs/Web/CSS/position)

## Blur background

```
<div
  className="rounder-md"
  style="background: url(https://source.unsplash.com/user/jackie/likes/1600x900) no-repeat"
>
  <div className="blur">
    <div>Content</div>
  </div>
</div>
```

Style:

```
.blur {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(16px);
  height: 100%;
  width: 100%;
}
```
