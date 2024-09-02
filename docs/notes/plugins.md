---
sidebar_position: 1
---

# 插件分享

如果没有开源项目的支持，就不会有现在的音流～

如果您觉得音流的某个功能帮到了您，可以考虑为这些项目点亮 🌟 或提供支持。

## 界面

### macos_ui

[macos_ui](https://github.com/macosui/macos_ui) 与 Flutter 自带的 Material Widgets 和 Cupertino Widgets 一样，都是为了实现在对应平台设计语言的组件库。

[点此查看](https://macosui.github.io/macos_ui/#/)在线演示。

![](https://oss.aqzscn.cn/resource/blog/img/2024/84187-8f40569512f26dedc256e709c73a4de9.png)

### fluent_ui

[fluent_ui](https://github.com/bdlukaa/fluent_ui) 是用于实现 Windows 平台 fluent 设计语言的组件库，这里面的组件相较于 `macos_ui` 里的组件功能更加完善。

[点此查看](https://bdlukaa.github.io/fluent_ui/)在线演示。

![](https://oss.aqzscn.cn/resource/blog/img/2024/65e8d-fc810c37b1bd57ddc5161705e21c8343.png)

### pulldown_button

[pulldown_button](https://github.com/notDmDrl/pull_down_button) 实现了类似 iOS 下拉菜单的效果，动画效果十分丝滑，如果能支持二级菜单就更完美了。

![](https://oss.aqzscn.cn/resource/blog/img/2024/faae1-9ad0cf3582cd7ff590b3e02645f19bc7.png)

## 平台特性

### macos_window_utils

[macos_window_utils](https://github.com/macosui/macos_window_utils.dart) 是 `macos_ui` 作者的另一作品，主要功能是控制窗口的各种属性，如是否模糊、是否隐藏标题栏等，配合 macos_ui 食用更佳。

### flutter_acrylic

[flutter_acrylic](https://github.com/alexmercerind/flutter_acrylic) 可以在 macOS、Windows、Linux 平台实现窗口模糊/透明效果，其中 macOS 依赖了 `macos_window_utils` 插件，因此如果使用此插件就无需再引入 `macos_window_utils` 了。

### window_manager

[window_manager](https://pub.dev/packages/window_manager) 可用于在桌面端控制窗口的一系列属性。

### tray_manager

[tray_manager](https://pub.dev/packages/tray_manager) 可以定义桌面端的系统托盘。

### windows_taskbar

[windows_taskbar](https://pub.dev/packages/windows_taskbar) 用于在 Windows 的任务栏图标上添加预览按钮与进度条，对于音乐播放器来说非常实用。

### flutter_carplay

[flutter_carplay](https://pub.dev/packages/flutter_carplay) 可用于在 iOS 平台实现 CarPlay 功能，最低支持 iOS 14.

作者已经很久没有更新过了，可以尝试其他开发者的修改版本。

目前一个比较困扰我的问题是如何在打开 CarPlay 时启动 Flutter 引擎，同时保证再从手机上打开 APP 时界面不会卡住。



## 网络

### dio

[dio](https://pub.dev/packages/dio) 是一个强大的 HTTP 网络请求库，其中的拦截器、请求取消、自定义适配器等特色功能都很好用，社区还提供了一些插件可让网络请求的处理更加轻松。

dart 的 HTTP 请求是自己实现的，仅适配了标准的 HTTP 请求，处理一些非标准的 HTTP 请求就会出问题，在这一点上是不如原生平台的网络请求的。

虽然 dio 目前也已经有了 [native_dio_adapter](https://github.com/cfug/dio/tree/main/plugins/native_dio_adapter) 插件可以通过原生平台发送请求，但只在安卓和 iOS 平台有效，这对于音流来说显然是不够的。

最近新出了个 [rhttp](https://github.com/Tienisto/rhttp)，原理是使用 FRB 插件通过 Rust 发送网络请求，可以观察一段时间，如果稳定的话可能会尝试切换到这个插件上。

### shelf

[shelf](https://pub.dev/packages/shelf) 可用于创建本地的 HTTP 服务器，可通过 [shelf_proxy](https://pub.dev/packages/shelf_proxy) 等相关插件简化处理步骤。

需要注意的是，iOS 平台创建的本地服务器会在应用不再位于前台后停用，应用需要检测本地服务是否可用并准备重启。

### connectivity_plus

[connectivity_plus](https://pub.dev/packages/connectivity_plus) 可用于检测应用当前的网络环境。

### network_info_plus

[network_info_plus](https://pub.dev/packages/network_info_plus) 可用于获取 Wi-Fi 信息，比如 IP 地址。

### url_launcher

[url_launcher](https://pub.dev/packages/url_launcher) 可用于在浏览器中打开链接。

## 音频

### media_kit

[media_kit](https://github.com/media-kit/media-kit) 是一个播放插件，可以用来播放视频或音频。与 flutter 平台其他播放插件不同的是，它的底层使用的是鼎鼎有名的 MPV，因此对[媒体格式](https://github.com/media-kit/media-kit?tab=readme-ov-file#supported-formats)的兼容性达到了十分恐怖的地步。

<details>
  <summary>点击查看支持格式</summary>

- 3dostr          3DO STR
- 4xm             4X Technologies
- aa              Audible AA format files
- aac             raw ADTS AAC (Advanced Audio Coding)
- aax             CRI AAX
- ac3             raw AC-3
- ace             tri-Ace Audio Container
- acm             Interplay ACM
- act             ACT Voice file format
- adf             Artworx Data Format
- adp             ADP
- ads             Sony PS2 ADS
- adx             CRI ADX
- aea             MD STUDIO audio
- afc             AFC
- aiff            Audio IFF
- aix             CRI AIX
- alaw            PCM A-law
- alias_pix       Alias/Wavefront PIX image
- alp             LEGO Racers ALP
- amr             3GPP AMR
- amrnb           raw AMR-NB
- amrwb           raw AMR-WB
- anm             Deluxe Paint Animation
- apac            raw APAC
- apc             CRYO APC
- ape             Monkey's Audio
- apm             Ubisoft Rayman 2 APM
- apng            Animated Portable Network Graphics
- aptx            raw aptX
- aptx_hd         raw aptX HD
- aqtitle         AQTitle subtitles
- argo_asf        Argonaut Games ASF
- argo_brp        Argonaut Games BRP
- argo_cvg        Argonaut Games CVG
- asf             ASF (Advanced / Active Streaming Format)
- asf_o           ASF (Advanced / Active Streaming Format)
- ass             SSA (SubStation Alpha) subtitle
- ast             AST (Audio Stream)
- au              Sun AU
- av1             AV1 Annex B
- avi             AVI (Audio Video Interleaved)
- avr             AVR (Audio Visual Research)
- avs             Argonaut Games Creature Shock
- avs2            raw AVS2-P2/IEEE1857.4
- avs3            raw AVS3-P2/IEEE1857.10
- bethsoftvid     Bethesda Softworks VID
- bfi             Brute Force & Ignorance
- bfstm           BFSTM (Binary Cafe Stream)
- bin             Binary text
- bink            Bink
- binka           Bink Audio
- bit             G.729 BIT file format
- bitpacked       Bitpacked
- bmp_pipe        piped bmp sequence
- bmv             Discworld II BMV
- boa             Black Ops Audio
- bonk            raw Bonk
- brender_pix     BRender PIX image
- brstm           BRSTM (Binary Revolution Stream)
- c93             Interplay C93
- caf             Apple CAF (Core Audio Format)
- cavsvideo       raw Chinese AVS (Audio Video Standard)
- cdg             CD Graphics
- cdxl            Commodore CDXL video
- cine            Phantom Cine
- codec2          codec2 .c2 demuxer
- codec2raw       raw codec2 demuxer
- concat          Virtual concatenation script
- cri_pipe        piped cri sequence
- dash            Dynamic Adaptive Streaming over HTTP
- data            raw data
- daud            D-Cinema audio
- dcstr           Sega DC STR
- dds_pipe        piped dds sequence
- derf            Xilam DERF
- dfa             Chronomaster DFA
- dfpwm           raw DFPWM1a
- dhav            Video DAV
- dirac           raw Dirac
- dnxhd           raw DNxHD (SMPTE VC-3)
- dpx_pipe        piped dpx sequence
- dsf             DSD Stream File (DSF)
- dshow           DirectShow capture
- dsicin          Delphine Software International CIN
- dss             Digital Speech Standard (DSS)
- dts             raw DTS
- dtshd           raw DTS-HD
- dv              DV (Digital Video)
- dvbsub          raw dvbsub
- dvbtxt          dvbtxt
- dxa             DXA
- ea              Electronic Arts Multimedia
- ea_cdata        Electronic Arts cdata
- eac3            raw E-AC-3
- epaf            Ensoniq Paris Audio File
- exr_pipe        piped exr sequence
- f32be           PCM 32-bit floating-point big-endian
- f32le           PCM 32-bit floating-point little-endian
- f64be           PCM 64-bit floating-point big-endian
- f64le           PCM 64-bit floating-point little-endian
- ffmetadata      FFmpeg metadata in text
- film_cpk        Sega FILM / CPK
- filmstrip       Adobe Filmstrip
- fits            Flexible Image Transport System
- flac            raw FLAC
- flic            FLI/FLC/FLX animation
- flv             FLV (Flash Video)
- frm             Megalux Frame
- fsb             FMOD Sample Bank
- fwse            Capcom's MT Framework sound
- g722            raw G.722
- g723_1          G.723.1
- g726            raw big-endian G.726 ("left aligned")
- g726le          raw little-endian G.726 ("right aligned")
- g729            G.729 raw format demuxer
- gdigrab         GDI API Windows frame grabber
- gdv             Gremlin Digital Video
- gem_pipe        piped gem sequence
- genh            GENeric Header
- gif             CompuServe Graphics Interchange Format (GIF)
- gif_pipe        piped gif sequence
- gsm             raw GSM
- gxf             GXF (General eXchange Format)
- h261            raw H.261
- h263            raw H.263
- h264            raw H.264 video
- hca             CRI HCA
- hcom            Macintosh HCOM
- hdr_pipe        piped hdr sequence
- hevc            raw HEVC video
- hls             Apple HTTP Live Streaming
- hnm             Cryo HNM v4
- ico             Microsoft Windows ICO
- idcin           id Cinematic
- idf             iCE Draw File
- iff             IFF (Interchange File Format)
- ifv             IFV CCTV DVR
- ilbc            iLBC storage
- image2          image2 sequence
- image2pipe      piped image2 sequence
- imf             IMF (Interoperable Master Format)
- ingenient       raw Ingenient MJPEG
- ipmovie         Interplay MVE
- ipu             raw IPU Video
- ircam           Berkeley/IRCAM/CARL Sound Format
- iss             Funcom ISS
- iv8             IndigoVision 8000 video
- ivf             On2 IVF
- ivr             IVR (Internet Video Recording)
- j2k_pipe        piped j2k sequence
- jacosub         JACOsub subtitle format
- jpeg_pipe       piped jpeg sequence
- jpegls_pipe     piped jpegls sequence
- jpegxl_pipe     piped jpegxl sequence
- jv              Bitmap Brothers JV
- kux             KUX (YouKu)
- kvag            Simon & Schuster Interactive VAG
- laf             LAF (Limitless Audio Format)
- lavfi           Libavfilter virtual input device
- live_flv        live RTMP FLV (Flash Video)
- lmlm4           raw lmlm4
- loas            LOAS AudioSyncStream
- lrc             LRC lyrics
- luodat          Video CCTV DAT
- lvf             LVF
- lxf             VR native stream (LXF)
- m4v             raw MPEG-4 video
- matroska,webm   Matroska / WebM
- mca             MCA Audio Format
- mcc             MacCaption
- mgsts           Metal Gear Solid: The Twin Snakes
- microdvd        MicroDVD subtitle format
- mjpeg           raw MJPEG video
- mjpeg_2000      raw MJPEG 2000 video
- mlp             raw MLP
- mlv             Magic Lantern Video (MLV)
- mm              American Laser Games MM
- mmf             Yamaha SMAF
- mods            MobiClip MODS
- moflex          MobiClip MOFLEX
- mov,mp4,m4a,3gp,3g2,mj2 QuickTime / MOV
- mp3             MP2/3 (MPEG audio layer 2/3)
- mpc             Musepack
- mpc8            Musepack SV8
- mpeg            MPEG-PS (MPEG-2 Program Stream)
- mpegts          MPEG-TS (MPEG-2 Transport Stream)
- mpegtsraw       raw MPEG-TS (MPEG-2 Transport Stream)
- mpegvideo       raw MPEG video
- mpjpeg          MIME multipart JPEG
- mpl2            MPL2 subtitles
- mpsub           MPlayer subtitles
- msf             Sony PS3 MSF
- msnwctcp        MSN TCP Webcam stream
- msp             Microsoft Paint (MSP))
- mtaf            Konami PS2 MTAF
- mtv             MTV
- mulaw           PCM mu-law
- musx            Eurocom MUSX
- mv              Silicon Graphics Movie
- mvi             Motion Pixels MVI
- mxf             MXF (Material eXchange Format)
- mxg             MxPEG clip
- nc              NC camera feed
- nistsphere      NIST SPeech HEader REsources
- nsp             Computerized Speech Lab NSP
- nsv             Nullsoft Streaming Video
- nut             NUT
- nuv             NuppelVideo
- obu             AV1 low overhead OBU
- ogg             Ogg
- oma             Sony OpenMG audio
- paf             Amazing Studio Packed Animation File
- pam_pipe        piped pam sequence
- pbm_pipe        piped pbm sequence
- pcx_pipe        piped pcx sequence
- pfm_pipe        piped pfm sequence
- pgm_pipe        piped pgm sequence
- pgmyuv_pipe     piped pgmyuv sequence
- pgx_pipe        piped pgx sequence
- phm_pipe        piped phm sequence
- photocd_pipe    piped photocd sequence
- pictor_pipe     piped pictor sequence
- pjs             PJS (Phoenix Japanimation Society) subtitles
- pmp             Playstation Portable PMP
- png_pipe        piped png sequence
- pp_bnk          Pro Pinball Series Soundbank
- ppm_pipe        piped ppm sequence
- psd_pipe        piped psd sequence
- psxstr          Sony Playstation STR
- pva             TechnoTrend PVA
- pvf             PVF (Portable Voice Format)
- qcp             QCP
- qdraw_pipe      piped qdraw sequence
- qoi_pipe        piped qoi sequence
- r3d             REDCODE R3D
- rawvideo        raw video
- realtext        RealText subtitle format
- redspark        RedSpark
- rka             RKA (RK Audio)
- rl2             RL2
- rm              RealMedia
- roq             id RoQ
- rpl             RPL / ARMovie
- rsd             GameCube RSD
- rso             Lego Mindstorms RSO
- rtp             RTP input
- rtsp            RTSP input
- s16be           PCM signed 16-bit big-endian
- s16le           PCM signed 16-bit little-endian
- s24be           PCM signed 24-bit big-endian
- s24le           PCM signed 24-bit little-endian
- s32be           PCM signed 32-bit big-endian
- s32le           PCM signed 32-bit little-endian
- s337m           SMPTE 337M
- s8              PCM signed 8-bit
- sami            SAMI subtitle format
- sap             SAP input
- sbc             raw SBC (low-complexity subband codec)
- sbg             SBaGen binaural beats script
- scc             Scenarist Closed Captions
- scd             Square Enix SCD
- sdns            Xbox SDNS
- sdp             SDP
- sdr2            SDR2
- sds             MIDI Sample Dump Standard
- sdx             Sample Dump eXchange
- ser             SER (Simple uncompressed video format for astronomical capturing)
- sga             Digital Pictures SGA
- sgi_pipe        piped sgi sequence
- shn             raw Shorten
- siff            Beam Software SIFF
- simbiosis_imx   Simbiosis Interactive IMX
- sln             Asterisk raw pcm
- smjpeg          Loki SDL MJPEG
- smk             Smacker
- smush           LucasArts Smush
- sol             Sierra SOL
- sox             SoX native
- spdif           IEC 61937 (compressed data in S/PDIF)
- srt             SubRip subtitle
- stl             Spruce subtitle format
- subviewer       SubViewer subtitle format
- subviewer1      SubViewer v1 subtitle format
- sunrast_pipe    piped sunrast sequence
- sup             raw HDMV Presentation Graphic Stream subtitles
- svag            Konami PS2 SVAG
- svg_pipe        piped svg sequence
- svs             Square SVS
- swf             SWF (ShockWave Flash)
- tak             raw TAK
- tedcaptions     TED Talks captions
- thp             THP
- tiertexseq      Tiertex Limited SEQ
- tiff_pipe       piped tiff sequence
- tmv             8088flex TMV
- truehd          raw TrueHD
- tta             TTA (True Audio)
- tty             Tele-typewriter
- txd             Renderware TeXture Dictionary
- ty              TiVo TY Stream
- u16be           PCM unsigned 16-bit big-endian
- u16le           PCM unsigned 16-bit little-endian
- u24be           PCM unsigned 24-bit big-endian
- u24le           PCM unsigned 24-bit little-endian
- u32be           PCM unsigned 32-bit big-endian
- u32le           PCM unsigned 32-bit little-endian
- u8              PCM unsigned 8-bit
- v210            Uncompressed 4:2:2 10-bit
- v210x           Uncompressed 4:2:2 10-bit
- vag             Sony PS2 VAG
- vbn_pipe        piped vbn sequence
- vc1             raw VC-1
- vc1test         VC-1 test bitstream
- vfwcap          VfW video capture
- vidc            PCM Archimedes VIDC
- vividas         Vividas VIV
- vivo            Vivo
- vmd             Sierra VMD
- vobsub          VobSub subtitle format
- voc             Creative Voice
- vpk             Sony PS2 VPK
- vplayer         VPlayer subtitles
- vqf             Nippon Telegraph and Telephone Corporation (NTT) TwinVQ
- w64             Sony Wave64
- wady            Marble WADY
- wav             WAV / WAVE (Waveform Audio)
- wavarc          Waveform Archiver
- wc3movie        Wing Commander III movie
- webm_dash_manifest WebM DASH Manifest
- webp_pipe       piped webp sequence
- webvtt          WebVTT subtitle
- wsaud           Westwood Studios audio
- wsd             Wideband Single-bit Data (WSD)
- wsvqa           Westwood Studios VQA
- wtv             Windows Television (WTV)
- wv              WavPack
- wve             Psion 3 audio
- xa              Maxis XA
- xbin            eXtended BINary text (XBIN)
- xbm_pipe        piped xbm sequence
- xmd             Konami XMD
- xmv             Microsoft XMV
- xpm_pipe        piped xpm sequence
- xvag            Sony PS3 XVAG
- xwd_pipe        piped xwd sequence
- xwma            Microsoft xWMA
- yop             Psygnosis YOP
- yuv4mpegpipe    YUV4MPEG pipe

</details>

我很难抑制我对它的喜爱之情，因为之前一直在苦苦寻找一款能代替 `just_audio` 的播放插件而不得。而现在在 media_kit 的帮助下，以前遇到的很多播放问题都已迎刃而解。

所以大家，都看到这里了，快去给 [media_kit](https://github.com/media-kit/media-kit) 点亮 🌟 吧～

:::note 开发技巧

直接使用默认配置，在鸿蒙系统播放高码率文件时会导致闪退问题。

```dart
NativePlayer get nativePlayer => player.platform as NativePlayer;

if (Platform.isAndroid) {
  // 修复 鸿蒙系统播放高码率文件时闪退问题
  await nativePlayer.setProperty("ao", "audiotrack,opensles,");
}
```

此处代码参考了 [spotube](https://github.com/KRTirtho/spotube) 项目的 [custom_player.dart](https://github.com/KRTirtho/spotube/blob/cb95663412fcc9a829c5657e0160132f13fb0649/lib/services/audio_player/custom_player.dart#L68)。

:::

### audio_service

[audio_service](https://github.com/ryanheise/audio_service) 用于通知系统当前正在播放的音乐并与系统控件交互，还可以用来保持音乐后台播放。

目前支持 Android、iOS、macOS，对 Windows 的支持可以参见我的[魔改版本](https://github.com/gitbobobo/audio_service)，一是加入了安卓状态栏歌词的支持，二是通过 [smtc_windows](https://github.com/KRTirtho/smtc_windows) 插件实现了对 Windows 的媒体通知的支持。

### audio_metadata_reader

[audio_metadata_reader](https://github.com/ClementBeal/audio_metadata_reader) 是一款用于读取音乐文件标签信息的插件，目前支持以下格式：

| File Format | Metadata Format(s)      | Read |
| ----------- | ----------------------- | ---- |
| MP3         | `ID3v2` `ID3v3` `ID3v4` | ✅   |
| MP4         | `iTunes-style ilst`     | ✅   |
| FLAC        | `Vorbis Comments`       | ✅   |
| OGG         | `Vorbis Comments`       | ✅   |
| Opus        | `Vorbis Comments`       | ✅   |

## Flutter 社区

### Flutter Candies

[Flutter 糖果社区](https://github.com/fluttercandies) 现在已经收录了很多有用的插件，用以补充官方组件缺少的功能。社区的组织者在[掘金](https://juejin.cn/user/254742428916408/posts)非常活跃，我已经默默关注了哈哈。

目前音流用到了 Flutter Candies 的以下插件：

- [extended_nested_scroll_view](https://github.com/fluttercandies/extended_nested_scroll_view) 解决歌曲列表页和歌手详情页列表内容滚动到透明 Header 下层的问题以及同步滚动的问题。
- [loading_more_list](https://github.com/fluttercandies/loading_more_list) 不使用 ScrollController 实现**加载更多**的功能。
- [scrollview_observer](https://github.com/fluttercandies/flutter_scrollview_observer) 实现动态切换宫格/列表视图的 **az 跳转**功能。
- [flutter_smart_dialog](https://github.com/fluttercandies/flutter_smart_dialog) 无 BuildContext 的**全局提示/通知**。