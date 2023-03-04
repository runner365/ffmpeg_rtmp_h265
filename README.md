# 在ffmpeg中支持hevc/vp8/vp9/opus的flv格式

当前阿里云，金山云等众多cdn，已经支持hevc编码的rtmp直播。<br>
本库支持的版本(见对应的branch分支):
* 4.1
* 4.3
* 5.0
* 5.1
* 6.0

## rtmp codecid
hevc/vp8/vp9/opus在rtmp中的codecid没有官方协议定义，由国内众多知名cdn共同制定。
<pre>
<code>
FLV_CODECID_OPUS = 9 << FLV_AUDIO_CODECID_OFFSET

enum {
    FLV_CODECID_H263    = 2,
    FLV_CODECID_SCREEN  = 3,
    FLV_CODECID_VP6     = 4,
    FLV_CODECID_VP6A    = 5,
    FLV_CODECID_SCREEN2 = 6,
    FLV_CODECID_H264    = 7,
    FLV_CODECID_REALH263= 8,
    FLV_CODECID_MPEG4   = 9,
    FLV_CODECID_HEVC    = 12,
    FLV_CODECID_AV1     = 13,
    FLV_CODECID_VP8     = 14,
    FLV_CODECID_VP9     = 15,
};
</code>
</pre>

## 编译
只需要把flv.h/flvdec.c/flvenc.c拷贝入libavformat文件夹中，后面ffmpeg正常编译即可。

如何编译ffmpeg，可以参照：
如何编译支持srt的ffmpeg: [wiki](https://github.com/runner365/srt_encoder/wiki/How-to-compile-cn)

