---
title: css 悬浮按钮特效

categories: 
 - css

tags:
 - 动画特效
 - 伪元素

index_img: /img/cssHover/css_index.png
---

## 元素统一样式

```less
.demo {
  // 设置宽高
  width: 140px;
  height: 50px;
  // 设置文字水平居中
  text-align: center;
  // 设置文字垂直居中
  line-height: 50px;
  background: rgba(255, 255, 255, 0.2);
  color: #fff;
  // 设置鼠标悬浮样式
  cursor: pointer;
  // 设置禁止用户选中元素中的文字
  user-select: none;
}
```

## 利用伪元素，形成线性效果

### 双线延展

![双线延展](/img/cssHover/demo1_1.gif)

```less
.demo1_1 {
  position: relative;

  &::before,
  &::after {
    // 伪元素相对于元素定位
    content: "";
    position: absolute;
    width: 0;
    height: 2px;
    background: #9DADF0;
    // 在不知道宽度的情况下，保持水平居中
    // 先偏移元素的50%，再用translate偏移回伪元素本身宽度的50%
    left: 50%;
    transform: translateX(-50%);
    // 用transition属性实现过渡的效果
    transition: width 0.5s;
  }

  &::before {
    top: 0;
  }

  &::after {
    bottom: 0;
  }

  &:hover {

    // 悬浮之后，两个伪元素的宽度发生变化
    &::before {
      width: 100%;
    }

    &::after {
      width: 100%;
    }
  }
}

```

### 双线延展

![双线延展](/img/cssHover/demo1_2.gif)

```less
.demo1_2 {
  position: relative;

  &::before,
  &::after {
    content: "";
    position: absolute;
    top: 50%;
    width: 2px;
    height: 0;
    background: #9DADF0;
    transform: translateY(-50%);
    transition: height 0.5s;
  }

  &::before {
    left: 0;
  }

  &::after {
    right: 0;
  }

  &:hover {

    // 与demo1_1同理，悬浮之后，两个伪元素的高度发生变化
    &::before {
      height: 100%;
    }

    &::after {
      height: 100%;
    }
  }
}

```

### 双线交叉

![双线交叉](/img/cssHover/demo1_3.gif)

```less
.demo1_3 {
  position: relative;

  &::before,
  &::after {
    content: "";
    position: absolute;
    width: 0;
    height: 2px;
    background: #9DADF0;
    transition: width 0.5s;
  }

  // 与demo1_1同理，改变伪元素定位的位置，从不同的方向延展宽度
  &::before {
    left: 0;
    top: 0;
  }

  &::after {
    right: 0;
    bottom: 0;
  }

  &:hover {
    &::before {
      width: 100%;
    }

    &::after {
      width: 100%;
    }
  }
}

```

### 双线交叉

![双线交叉](/img/cssHover/demo1_4.gif)

```less
.demo1_4 {
  position: relative;

  &::before,
  &::after {
    content: "";
    position: absolute;
    width: 2px;
    height: 0;
    background: #9DADF0;
    transition: height 0.5s;
  }

  // 与demo1_1同理，改变伪元素定位的位置，从不同的方向延展高度
  &::before {
    left: 0;
    top: 0;
  }

  &::after {
    right: 0;
    bottom: 0;
  }

  &:hover {
    &::before {
      height: 100%;
    }

    &::after {
      height: 100%;
    }
  }
}

```

### 顶角延展

![顶角延展](/img/cssHover/demo1_5.gif)

```less

.demo1_5 {
  position: relative;

  // 两个span分别有两个伪元素，向四个不同的方向延展
  .leftTop {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;

    &::before,
    &::after {
      content: "";
      position: absolute;
      left: 0;
      top: 0;
      background: #9DADF0;
    }

    &::before {
      width: 0;
      height: 2px;
      transition: width 0.5s;
    }

    &::after {
      width: 2px;
      height: 0;
      transition: height 0.5s;
    }
  }

  .rightBottom {
    position: absolute;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;

    &::before,
    &::after {
      content: "";
      position: absolute;
      right: 0;
      bottom: 0;
      background: #9DADF0;
    }

    &::before {
      width: 0;
      height: 2px;
      transition: width 0.5s;
    }

    &::after {
      width: 2px;
      height: 0;
      transition: height 0.5s;
    }
  }

  &:hover {
    .leftTop {
      &::before {
        width: 100%;
      }

      &::after {
        height: 100%;
      }
    }

    .rightBottom {
      &::before {
        width: 100%;
      }

      &::after {
        height: 100%;
      }
    }
  }
}

```

### 四边旋转

![四边旋转](/img/cssHover/demo1_6.gif)

```less
.demo1_6 {
  position: relative;

  // 与demo1_5同理，改变span的定位，也改变每个span的伪元素的定位，使得四条线分别从不同的起点出发延展到不同的终点
  .leftTop {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;

    &::before,
    &::after {
      content: "";
      position: absolute;
      background: #9DADF0;
    }

    &::before {
      left: 0;
      top: 0;
      width: 0;
      height: 2px;
      transition: width 0.5s;
    }

    &::after {
      right: 0;
      top: 0;
      width: 2px;
      height: 0;
      transition: height 0.5s;
    }
  }

  .rightBottom {
    position: absolute;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;

    &::before,
    &::after {
      content: "";
      position: absolute;
      background: #9DADF0;
    }

    &::before {
      right: 0;
      bottom: 0;
      width: 0;
      height: 2px;
      transition: width 0.5s;
    }

    &::after {
      left: 0;
      bottom: 0;
      width: 2px;
      height: 0;
      transition: height 0.5s;
    }
  }

  &:hover {
    .leftTop {
      &::before {
        width: 100%;
      }

      &::after {
        height: 100%;
      }
    }

    .rightBottom {
      &::before {
        width: 100%;
      }

      &::after {
        height: 100%;
      }
    }
  }
}

```

## 利用内部子元素，形成遮罩效果

### 层叠渐进

![层叠渐进](/img/cssHover/demo2_1.gif)

```less
.demo2_1 {
  position: relative;
  overflow: hidden;

  .text {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
  }

  .mask1,
  .mask2 {
    position: absolute;
    left: -100%;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(128, 142, 193, 0.5);
  }

  // 通过改变子元素的定位，形成遮罩的效果
  // transition的速度设置成不同的数值，就可以产生层叠的效果
  .mask1 {
    transition: left 0.5s ease-in-out;
  }

  .mask2 {
    transition: left 0.8s ease-in-out;
  }

  &:hover {
    .mask1 {
      left: 0;

    }

    .mask2 {
      left: 0;
    }
  }

}

```

### 层叠倾斜

![层叠倾斜](/img/cssHover/demo2_2.gif)

```less
.demo2_2 {
  position: relative;
  overflow: hidden;

  .text {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
  }

  .mask1,
  .mask2 {
    position: absolute;
    // 两个伪元素定位到元素的外部
    left: -50px;
    bottom: 0;
    width: 50px;
    height: 150px;
    background: rgba(128, 142, 193, 0.5);
    transform: rotate(0deg);
    // 设置伪元素旋转角度在右下角
    transform-origin: right bottom;
  }

  // 与demo2_1同理，过渡时间设置成不一样的数值，由此产生层叠的效果
  .mask1 {
    transition: transform 0.5s ease-in-out;
  }

  .mask2 {
    transition: transform 0.8s ease-in-out;
  }

  &:hover {
    .mask1 {
      transform: rotate(90deg);

    }

    .mask2 {
      transform: rotate(90deg);
    }
  }

}

```

### 层叠扩散

![层叠扩散](/img/cssHover/demo2_3.gif)

```less
.demo2_3 {
  position: relative;
  overflow: hidden;

  .text {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
  }

  // 两个元素定位到元素中间
  .mask1,
  .mask2 {
    position: absolute;
    // x方向和y方向分别偏移元素的宽度和高度的50%
    left: 50%;
    top: 50%;
    width: 0;
    height: 0;
    background: rgba(128, 142, 193, 0.5);
    // 向回偏移伪元素自身宽度和高度的50%，达到剧中的效果
    transform: translate(-50%, -50%);
    border-radius: 50%;
  }

  .mask1 {
    transition: all 0.5s;
  }

  .mask2 {
    transition: all 0.3s;
  }

  &:hover {
    .mask1 {
      width: 150px;
      height: 150px;

    }

    .mask2 {
      width: 150px;
      height: 150px;
    }
  }
}

```

### 交叉渐进

![交叉渐进](/img/cssHover/demo2_4.gif)

```less
.demo2_4 {
  position: relative;
  overflow: hidden;

  .text {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
  }

  .mask1,
  .mask2 {
    position: absolute;
    width: 100%;
    height: 100%;
    transition: top 0.5s;
  }

  .mask1 {
    left: 0;
    top: -100%;

    &::before,
    &::after {
      content: "";
      position: absolute;
      top: 0;
      width: 25%;
      height: 100%;
      background: rgba(128, 142, 193, 0.5);
    }

    &::before {
      left: 0;
    }

    &::after {
      left: 50%;
    }
  }

  .mask2 {
    left: 0;
    top: 100%;

    &::before,
    &::after {
      content: "";
      position: absolute;
      top: 0;
      width: 25%;
      height: 100%;
      background: rgba(128, 142, 193, 0.5);
    }

    &::before {
      left: 25%;
    }

    &::after {
      left: 75%;
    }
  }

  &:hover {
    .mask1 {
      top: 0;
    }

    .mask2 {
      top: 0;
    }
  }
}


```

## 利用伪元素，形成切换效果

### 向上切换

![向上切换](/img/cssHover/demo3_1.gif)

```less
.demo3_1 {
  position: relative;

  &::before {
    content: "向上切换";
    position: absolute;
    left: 0;
    top: 20px;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: all 0.5s;
  }

  &::after {
    content: "向上切换";
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    opacity: 1;
    transition: all 0.5s;
  }

  &:hover {

    &::before {
      top: 0;
      opacity: 1;
    }

    &::after {
      top: -20px;
      opacity: 0;
    }
  }
}

```
## 完整代码

码云，动画特效仓库地址-[css-demo](https://gitee.com/yueban666/css-demo)
