# xiaochengxu
 微信小程序开发

##### iphone 6  1px = 1rpx  ,按着iphone6的设计图大小进行设计小程序草图

##### 在app.js中调用网络请求，请求的结束之后可能在初次加载页面的onLaunch和onshow生命周期之后。 所以务必在初次加载页面定义app.userInfoReadyCallback事件，在网络请求之后执行该事件。  
    if (this.userInfoReadyCallback) {
                  this.userInfoReadyCallback(token, intid);
                }
    app.userInfoReadyCallback = () => {
          console.warn("invoke after login");
          this.toLive();
          app.userInfoReadyCallback = null; //
        }
