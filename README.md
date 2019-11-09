# 跳格子小游戏主要部分记录

如果是此类型的小游戏,可以直接换地图，换皮服使用，可eui里方便操作，对刚学习使用白鹭的同学可做一个学习参考；
项目中Tool.ts,有一些常用的方法，拖动、动态列表点击、列表中不同位置的点击等可直接在项目里使用。

demo地址：https://source.nullno.com/egret-checkers/


手机查看：
![扫码查看](https://source.nullno.com/images/y1hbUUQkQpTD9dpSSmLm6lFK1xqRL3.jpeg)


### 地图制作
  
  地图数据参考:src\game\data\mainData.ts CLASS ->MapsData

  1.地图切片：地图可能会很大，需要用到ps切片功能(选择切片->切片划分->)等份切割，然后shift+ctrl+alt+s 
    保存后如resource\assets\main\map_1；
  
  2.奖励设定：更据地图中棋盘的样式设置参数类型；

  3.地图标点：这个比较简单 但需要一个个把设计地图上的格子中心坐标以需要的格式录入，本项目'2557/1254/北京/0/0-'
    解释为：[x/y/城市（无填-表示）/索引/奖励事件（2条中，无填-表示）];

  4.地图填充：把地图切片铺进eui.dataGroup中，参考src\game\scene\Map.ts  this.fillMap();
    
  
 
### 地图操作
  
  1.拖动交互：给地图添加拖动事件，这里会有一个地图边界设定，拖到地图的时候，上下左右边界尽可能不越过屏幕边界；

  2.放大缩小：为保持边界动态改变，不直接用scale属性，这里是把MapsData地图的参数值都x倍数，重新渲染地图，操作体验不好，肯定有其它  更优解决方案；

  
### 摇色子

   1.色子动画：更具1-6的色子图片，可以用tween自己写动画，有条件的用龙骨等工具做更逼真的色子动画；此项目用的是龙骨做的可扫码参考；

   2.动画结束：自己写动画可能需要设定时器，用龙骨动画 更据egret.Event.COMPLETE 一次播放回调完成执行后续事件；


### 走棋子

   1.坐标位移：看似是跳着在走，实际上就是坐标的位移，坐标是根据“地图制作”中的标点来的，然后在位移的过程中做一些符合跳跃的动画；

   2.棋子保持居中：左右肯定是要居中的，上下就保持合适的位置，跳动的过程中随着坐标改变，地图始终随着坐标而改变；


