# PhoneGapMedia
Media播放器

##使用Media构造播放器
>[链接]（daima/9/9-9.html）
##行内代码
'//播放音频文件
        function playAudio(src) {
            my_media = new Media(src,onSuccess,onError);//从目标文件中创建Media对象
            my_media.play();//播放音频
            if (mediaTimer == null) {//每秒更新一次媒体播放到的位置
                mediaTimer = setInterval(function () {
                    //获取媒体播放到的位置
                    my_media.getCurrentPosition(
                            //获取成功后调用的回调函数
                            function (position) {
                                if (position > -1){
                                    setAudioPosition((position/1000) + "sec");
                                }
                            },
                            //发生错误后调用的回调函数
                            function (e) {
                                console.log("ERROR getting pos= " + e);
                                setAudioPosition("Error: " + e);
                            }
                    );
                },1000);
            }
        }'
