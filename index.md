
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
<canvas id="myCanvas" width="350" height="98" style="border:1px solid #d3d3d3;background:#ffffff;"></canvas>
<div class="crop" style="display:none">
    <img src="https://z3.ax1x.com/2021/06/11/2WP7B6.png" class="crop" alt="Paper Sculpture Large" id="crop" >
</div>
<!--<div id="images"></div>-->

<img id="ctoi" >
</body>

<script>
    var storelog = JSON.parse(localStorage.CocStore || '{ "name":{}, "time":{}, "num":{} }');
    var nowTime = new Date();
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
        tnCanvasContext.drawImage(img,420,1800,770,2000,0,0,770,2000);
/*        context.drawImage(img,sx,sy,swidth,sheight,x,y,width,height);
        img	规定要使用的图像、画布或视频。
        sx	可选。开始剪切的 x 坐标位置。
        sy	可选。开始剪切的 y 坐标位置。
        swidth	可选。被剪切图像的宽度。
        sheight	可选。被剪切图像的高度。
        x	在画布上放置图像的 x 坐标位置。
        y	在画布上放置图像的 y 坐标位置。
        width	可选。要使用的图像的宽度。（伸展或缩小图像）
        height	可选。要使用的图像的高度。（伸展或缩小图像）*/
       // document.getElementById("ctoi").src = tnCanvas.toDataURL("image/png");

    }

</script>
