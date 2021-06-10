
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
        function onPreloadComplete(){
            //call the methods that will create a 64-bit version of thumbnail here.
            var newImg = getImagePortion(imgObject, 120, 150, 150, 80, 2);
            //place image in appropriate div
            console.log("1111");
            //img.setAttribute('crossOrigin', 'anonymous');
            document.getElementById("images").innerHTML = "<img alt='' crossOrigin='anonymous' src=''+newImg+'' />";
        }

        //图像截取
        function getImagePortion(imgObj, newWidth, newHeight, startX, startY, ratio){
            /* the parameters: - the image element - the new width - the new height - the x point we start taking pixels - the y point we start taking pixels - the ratio */
            //set up canvas for thumbnail
            var tnCanvas=document.getElementById("myCanvas");
            /*var ctx=c.getContext("2d");
            var img=document.getElementById("scream");

            img.onload = function() {
                ctx.drawImage(img,10,10);
            }*/

            //var tnCanvas = document.createElement('canvas');
            var tnCanvasContext = tnCanvas.getContext('2d');
            tnCanvas.width = newWidth; tnCanvas.height = newHeight;



            /* use the sourceCanvas to duplicate the entire image. This step was crucial for iOS4 and under devices. Follow the link at the end of this post to see what happens when you don’t do this */
            var bufferCanvas = document.createElement('canvas');
            var bufferContext = bufferCanvas.getContext('2d');
            bufferCanvas.width = imgObj.width;
            bufferCanvas.height = imgObj.height;
            bufferContext.drawImage(imgObj, 0, 0);

            /* now we use the drawImage method to take the pixels from our bufferCanvas and draw them into our thumbnail canvas */
            tnCanvasContext.drawImage(bufferCanvas, startX,startY,newWidth * ratio, newHeight * ratio,0,0,newWidth,newHeight);
            //return tnCanvas.toDataURL();

        }
    </script>
</head>

<body>
    1111
<!--<div class="crop">
    <img src="https://z3.ax1x.com/2021/05/28/2ifoc9.png" class="crop" alt="Paper Sculpture Large">
</div>-->
<!--<div id="images"></div>-->
<canvas id="myCanvas"></canvas>
</body>



