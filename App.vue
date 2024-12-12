<script>
  import websdk from "easemob-websdk/uniApp/Easemob-chat";
  import { ChatUIKit } from "./ChatUIKit";
  const EM_API_URL = "https://a1.easemob.com";
  const EM_WEB_SOCKET_URL = "wss://im-api-wechat.easemob.com/websocket";
  export default {
    onLaunch: function () {
      console.log("App Launch");
      this.initEaseIMClient();
    },
    onShow: function () {
      console.log("App Show");
    },
    onHide: function () {
      console.log("App Hide");
    },
    methods: {
      initEaseIMClient() {
        const chat = new websdk.connection({
          appKey: "easemob#easeim",
          url: EM_WEB_SOCKET_URL,
          apiUrl: EM_API_URL,
        });
        ChatUIKit.init({
          chat,
          config: {
            theme: {
              avatarShape: "circle",
            },
            isDebug: true,
          },
        });
        ChatUIKit.appUserStore.setUserInfo("hfp", {
          nickname: "王五",
          avatarurl:
            "https://wx2.sinaimg.cn/orj360/002uLDeXly1hwgvcut1whj60j60nyqct02.jpg",
        });
        ChatUIKit.hideFeature(["useUserInfo"]);
        uni.$EMUIKit = ChatUIKit;
      },
    },
  };
</script>

<style>
  /*每个页面公共css */
</style>
