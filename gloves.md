title: GLOVES

speaker: 十八赞

url: http://github.com/blankrain

transition: slide3

files: /js/zoom.js,/js/node_modules/rx/dist/rx.all.js,/js/node_modules/jquery/dist/jquery.js,/socket.io/socket.io.js,/js/snake-js.js,/js/markshowmorse.js

theme: moon

[幻片 data-on-enter="incallback" ]
# Gloves 介绍
Time:
x {:#abc}
---------
|Key|Value|
|-|-|
|Zi | 紫 |
|We | 薇 |
|Wo | 我 |
|Ai | 爱 |
|Ni | 你 |

[幻片 data-on-enter="incallback"]
<style>
  .inlove {
    color:rgba(255, 192, 203, 0.95);
  }
  .intouch {
    font-size:200%;
  }
</style>
紫 {:#zi}

薇 {:#we}

我 {:#wo}

爱 {:#ai}

你 {:#ni}
<script>
function incallback(){
  (function(window, document, io){
    var socket = io.connect(location.host+"/touchevent");
        socket.on("clickdata", byFelix);
      
  }(window, document, io));
var o=[zi,we,wo,ai,ni]

Rx.Observable.interval(1000).subscribe((x)=>{$(o[x % o.length]).toggleClass('inlove')})
}
function byFelix(d){
  $('#'+d.k.toLowerCase()).toggleClass('intouch');
  Rx.Observable.from($('#'+d.k.toLowerCase())).delay(500).subscribe((x)=>{$(x).removeClass('intouch')});
}
</script>



[幻片 data-on-enter="gameincallback"]

<div id="gameDiv"></div>
<script>
var game=null;
function gameincallback(){
  $("#gameDiv").html('')
  var gameDiv = document.getElementById("gameDiv");
	var settings = {
		    frameInterval : 120,
		    backgroundColor : '#152e4f',
        snakeColor:'green',
        scoreBoardColor:'#052e4f',
        scoreTextColor:'yellow'
	};

	game = new SnakeJS(gameDiv, settings);
  addGlovesSupport();
}

function addGlovesSupport(){
  (function(window, document, io){
    var socket = io.connect(location.host+"/touchevent");
        socket.on("clickdata", glovesGame);
      
  }(window, document, io));
}
function glovesGame(data){
  var em={'Zi':KeyMap.e,'We':KeyMap.s,'Wo':KeyMap.d,'Ai':KeyMap.f,'Ni':KeyMap.enter};
  var e={keyCode:em[data.k]};
  $(window).trigger('jq-keydown',e);
}

</script>

[幻片 data-on-enter="morseincallback"]
### Morse Code
<div class="">
    <input type="text" class="morseinput"/>
    
    <lable class="morseinput"></lable>
</div>
<style>
input.morseinput{
    color: green;
    width: 100%;
    font-size:larger;
    margin-top:20px;
    margin-bottom:20px;
    display:block;
}
</style>
<script>
function morseincallback(){
  $('input.morseinput').on('input',function(x){
    $('lable.morseinput').html(morse.decode($('input.morseinput').val()));
  });
}
</script>

[幻片]
## PPT介绍
* ### 什么是PPT?
    一般指微软的PowerPoint ,它是`演示文稿`的代名词.`演示文稿`是信息的载体,它负责沟通演讲者与听众.

    目前,微软的PPT,功能很多,也很强大,但是,太强太复杂了.需要一款简单轻便关注于内容本身的软件,那就是MarkShow

[幻片]
## MarkShow介绍
- ### 什么是MarkShow?
MarkShow就是用MarkDown语法来写PPT. 它的理念来源于MarkDown. 它应用于PPT,也就是`演示文稿`这么件事情.  
简而言之,`使用易读易写的纯文本格式编写演示文档`. 概念及范围缩小了一部分.相比而言,更具体了一些.

  概念及理念就这么多.

- ### 技术要点
 1. 源码基于 nodePPT 改造,新增部分中文语法.
 2. 整合finereport 报表服务,增加在线web数据展示.
 3. 云存储.
 4. atom编辑器及其插件开发.
