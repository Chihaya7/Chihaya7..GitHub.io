<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
    <title>untitled</title>
    <style type="text/css" media="screen">
        div.crop {
            height: 2004px;
            width: 756px;
            overflow: hidden;
        }
        div.crop img {
            width: 100%;
        }
    </style>

</head>

<body>
<div class="crop">
    <img src="https://z3.ax1x.com/2021/05/28/2ifoc9.png" class="crop" alt="Paper Sculpture Large" id="crop">
</div>
<!--<div id="images"></div>-->
<canvas id="myCanvas"></canvas>
<img id="ctoi" >
</body>

<script>
    var storelog = JSON.parse(localStorage.CocStore || '{ "name":{}, "time":{}, "num":{} }');
    var nowTime = new Date();
    var offset = nowTime.getTimezoneOffset()/60;
    var cur=Math.round(nowTime.getTime()/1000);

    //载入图像
    var loadTimer;
    var imgObject = new Image();
    imgObject.src = "https://z3.ax1x.com/2021/05/28/2ifoc9.png";
    imgObject.onLoad = onImgLoaded();
    console.log("1111");
    function onImgLoaded() {
        if (loadTimer != null) clearTimeout(loadTimer);
        if (!imgObject.complete) {
            loadTimer = setTimeout(function () {
                onImgLoaded();
            }, 3);
        } else {
            onPreloadComplete();
        }
    }


    //图像重新绘制
    /*function onPreloadComplete(){
     //call the methods that will create a 64-bit version of thumbnail here.
     var newImg = getImagePortion(imgObject, 120, 150, 150, 80, 2);
     //place image in appropriate div
     console.log("1111");
     //img.setAttribute('crossOrigin', 'anonymous');
     document.getElementById("images").innerHTML = "<img alt='' crossOrigin='anonymous' src=''+newImg+'' />";
     }*/
    function onPreloadComplete(){
        var tnCanvas=document.getElementById("myCanvas");
        var tnCanvasContext = tnCanvas.getContext('2d');
        var img=document.getElementById("crop");
        console.log("onPreloadComplete");
        //img.crossOrigin="anonymous";
        tnCanvasContext.drawImage(img,90,130,50,60,10,10,50,60);
       // document.getElementById("ctoi").src = tnCanvas.toDataURL("image/png");

    }

</script>
