This repository contains single-page browser tests for simulcast.
The simulcast stream is split into three different streams using SDP munging in order to expose
the result both visually as well as to getStats()

* [Chrome, legacy](https://aggresss.github.io/simulcast-playground/html/chrome)
    1. 将 CreateOffer 生成的 SDP 进行修改，在 Unified Plan 模式下也出现同一个 m-line 中多个 track，通过 SSRC + 1 的方式加入 track，并且加入 'a=ssrc-group:SIM' 然后用修改后的 SDP setLocalDescription，这样 Chrome 会识别出 Simulcast;
    2. 将 修改后的 SDP 中多个 track 拆分开，使用 group/mid 进行组合，每个 track 为一个独立的 Media Stream，将这次修改过的 SDP 发送到对端作为真正的 Offer，是对端可以识别 3 个 MediaStream 并进行渲染播放；

* [Chrome, spec](https://aggresss.github.io/simulcast-playground/html/rid-as-mid)


* [Firefox](https://aggresss.github.io/simulcast-playground/html/firefox)
    * 实现方式

See the [WebRTCHacks blog post](https://webrtchacks.com/a-playground-for-simulcast-without-an-sfu/) for more information.

# License
MIT
