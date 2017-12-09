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

##### 生命周期切换
    当前页面	     路由后页面	            触发的生命周期（按顺序）
    A	              A	                  Nothing happend
    A	              B	                  A.onHide(), B.onLoad(), B.onShow()
    A	              B（再次打开）	        A.onHide(), B.onShow()
    C	              A	C.onUnload(),     A.onShow()
    C	              B	C.onUnload(),     B.onLoad(), B.onShow()
    D	              B	D.onUnload(),     C.onUnload(), B.onLoad(), B.onShow()
    D（从转发进入）	  A	D.onUnload(),     A.onLoad(), A.onShow()
    D（从转发进入）	  B	D.onUnload(),      B.onLoad(), B.onShow()
