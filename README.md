# looplay-demo
无缝轮播demo：

bug:
1.切到别的tab一定事件后切回来，轮播会乱。
到别的tab时，会懒惰，等切回来时一次完成
2.无法跳转到指定图片

解决方法：
```
document.addEventListener('visibilitychange', function(){
if(document.hidden){
document.clearInterval(time)
}else{
执行轮播的代码
}
console.log(document.hidden)})
//切走 true
```

添加跳转功能：
1.点击，改变translateX。
2.给每张图片添加current标识，可获取跳转前到上一张图片是哪张。
3.clone(true)第一张和最后一张图片。  //赋值所有
4.将克隆的第一张加到最后，将最后一张加到最前面。
.append()
.prepend()
5.给第一张添加点击事件，判断如果是从最后一张(非克隆的)跳转过来则
跳转到最后一张(克隆的第一张)，并添加one.('transitionend')事件。
```
.one('transitionend',function(){
$图片.hide()
.offset()
...  //跳转到第一张
.show())})
```
