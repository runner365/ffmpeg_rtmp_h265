# 在ffmpeg中支持hevc的rtmp协议

当前阿里云，金山云等众多cdn，已经支持hevc编码的rtmp直播。

## rtmp codecid
hevc在rtmp中的codecid没有官方协议定义，由国内众多知名cdn共同制定。
FLV_CODECID_HEVC = 12
<pre>
<code>
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
};
</code>
</pre>

## 编译
只需要把flv.h/flvdec.c/flvenc.c拷贝入libavformat文件夹中，后面ffmpeg正常编译即可。

如何编译ffmpeg，可以参照：
如何编译支持srt的ffmpeg: [wiki](https://github.com/runner365/srt_encoder/wiki/How-to-compile-cn)

