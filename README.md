# 在ffmpeg中支持hevc/vp8/vp9/opus的flv格式
## 项目背景
1. 当前阿里云，金山云等众多cdn，已经支持hevc in rtmp/flv(采用增加codecid=12的方式)
2. 国外大厂和国外cdn支持hevc in rtmp/flv方式：[enhanced-rtmp](https://github.com/veovera/enhanced-rtmp)

<b>基于兼容上面两种hevc in rtmp/flv的方式，本库均支持。</b>

## 本库支持的版本(见对应的branch分支):
* 4.1
* 4.3
* 5.0
* 5.1
* 6.0(支持enhanced-rtmp)

## 国内cdn方式: 新增codecid
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

## 国外大厂和cdn方式：[enhanced-rtmp](https://github.com/veovera/enhanced-rtmp)
* mux/推流：需要设置: -f flv -flvflags ext_header
```markup
ffmpeg -re -i source.flv -c:v libx265 -c:a copy -f flv -flvflags ext_header rtmp://192.168.0.1/live/1000
```
* demux/拉流: 不需要格外操作，自动识别

## 编译

只需要把flv.h/flvdec.c/flvenc.c拷贝入libavformat文件夹中，后面ffmpeg正常编译即可。


