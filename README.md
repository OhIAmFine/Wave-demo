# 用css实现动态波浪效果
- 现实中是没有办法直接用css绘制出三次贝塞尔曲线的。
- 但是我们可以通过设置border-radius的值通过css3的动画，动态实现波浪效果
```
.wave::before,
.wave::after{
        content: "";
        position: absolute;
        width: 400px;
        height: 400px;
        top: 0;
        left: 50%;
        background-color: rgba(255, 255, 255, .4);
        border-radius: 45%;
        transform: translate(-50%, -70%) rotate(0);
        animation: rotate 6s linear infinite;
        z-index: 10;
    }
.wave::after {
        border-radius: 47%;
        background-color: rgba(255, 255, 255, .9);
        transform: translate(-50%, -70%) rotate(0);
        animation: rotate 10s linear -5s infinite;
        z-index: 20;
    }

```
单纯的让一个 border-radius 接近 50 的椭圆形旋转，动画效果可能不是那么好，我们可以适当的添加一些其他变换因素，让动画效果看上去更真实：

- 在动画过程中，动态的改变 border-radius 的值；
- 在动画过程中，利用 transform 对旋转椭圆进行轻微的位移、变形；
- 上面也演示到了，多个椭圆同时转动，赋予不同时长的动画，并且添加轻微的透明度，让整个效果更佳逼真。
