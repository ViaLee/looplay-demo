# looplay-demo
无缝轮播demo：

bug:
切到别的tab一定事件后切回来，轮播会乱。
到别的tab时，会懒惰，等切回来时一次完成

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
