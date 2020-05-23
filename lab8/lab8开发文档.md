# lab8开发文档
##### 19302010004 黄呈松

## 全局通用变量及函数
#### pic_now 表示现在图片

#### function setButton 
>修改按键颜色
```js
function setButton(index) {
    index--;
    for (let i = 0; i < buttons.length; i++) {
        buttons[i].setAttribute("class", "");
    }
    buttons[index].setAttribute('class', "on");
}
```
#### function showPic
>修改显示的图片
```js

function showPic(index) {
    pic_now = index;
    wrap.style.left = "-" + 600 * index + "px";
    setButton(index);
}

```
## 第一题
>显示对应图片
```js
function showLeft() {
    showPic((pic_now + 3) % 5 + 1);
}

function showRight() {
    showPic((pic_now) % 5 + 1);
}

```

## 第二题
>设置flag标志是否继续，循环切换图片
```js
container.onmouseover = function() {
    flag = false;
}
container.onmouseout = function() {
    flag = true;
}
setInterval(function() {
    if (flag) showRight();
}, 2000);
```
## 第三题
>设置onclick 改变图片
```js
for (let i = 0; i < buttons.length; i++) {
    buttons[i].setAttribute("onclick", "showPic(" + i + "+ 1)");
}
```

## 第四题
>设置属性可修改+移动光标
```js

$('td').each(function(index, e) {
    e.style.width = "100px";
    e.setAttribute("contenteditable", "true");
    e.onclick = function() {
        e.focus();
        e.style.backgroundColor = "white";
        let range = window.getSelection();
        range.selectAllChildren(e);
        range.collapseToStart();
    };
    e.onblur = function() {
        e.style.backgroundColor = "white";
    };
})

```