# FFmpeg Static Auto-Builds

## Patches Welcome
Known issues for which patches are welcome:

<!--*Nothing at the moment*-->

### 1. More Builds

There are currently no Windows ARM/MacOS builds. If you know how to add them to the workflow, make a PR



## Patches Applied
These patches have been applied to the builds:

### 1. [WebVTT decoding fix](https://ffmpeg.org/pipermail/ffmpeg-devel/2022-May/296353.html)

by [@tpikonen](https://github.com/tpikonen).
Fixes [yt-dlp#4127](https://github.com/yt-dlp/yt-dlp/issues/4127), [FFmpeg#8684](https://trac.ffmpeg.org/ticket/8684)

### 2. Support for HEVC over FLV

Assembled from patches by [@xiaoxial](https://github.com/VCDP/CDN/blob/master/FFmpeg_patches/0001-Add-SVT-HEVC-FLV-support-on-FFmpeg.patch), [@runner365](https://github.com/runner365/ffmpeg_rtmp_h265/blob/5.1/flvenc.c), and [Matthieu Patou](https://patchwork.ffmpeg.org/project/ffmpeg/patch/20210701141528.776-1-jamrial@gmail.com/).
See [this comment](https://github.com/yt-dlp/yt-dlp/pull/5823#issuecomment-1366868753) for details.

Fixes [yt-dlp#5874](https://github.com/yt-dlp/yt-dlp/issues/5874), [FFmpeg#6389](https://trac.ffmpeg.org/ticket/6389).



<!--
## Release-only patches
Patches that have been merged in FFmpeg master, but not in FFmpeg's latest release:

### 1. XXX
-->



## Historical Patches
Patches that were used in the past but are no longer needed as of **5.1**:

### 1. [Fix AAC HLS streams being truncated mid stream](https://patchwork.ffmpeg.org/project/ffmpeg/patch/20210927213133.28258-1-jeebjp@gmail.com)

by [@shirt](https://github.com/shirt-dev) and [@jeeb](https://github.com/jeeb), merged in [c205778](https://github.com/FFmpeg/FFmpeg/commit/c20577806f0a161c6867e72f884d020a253de10a).
Fixes [yt-dlp#618](https://github.com/yt-dlp/yt-dlp/issues/618), [yt-dlp#998](https://github.com/yt-dlp/yt-dlp/issues/998), [yt-dlp#1039](https://github.com/yt-dlp/yt-dlp/issues/1039), [FFmpeg#9433](https://trac.ffmpeg.org/ticket/9433)

### 2. [Fix for YouTube's VP9 encodes with non-monotonous DTS](https://ffmpeg.org/pipermail/ffmpeg-devel/2021-May/280189.html)

by [@danny-wu](https://github.com/danny-wu), merged in [68595b4](https://github.com/FFmpeg/FFmpeg/commit/68595b46cb374658432fff998e82e5ff434557ac)
Fixes [yt-dlp#871](https://github.com/yt-dlp/yt-dlp/issues/871), [youtube-dl#28042](https://github.com/ytdl-org/youtube-dl/issues/28042), [FFmpeg#9086](https://trac.ffmpeg.org/ticket/9086)

### 3. Long path support for Windows

by [@nihil-admirari](https://github.com/nihil-admirari).
Fixes [yt-dlp#1995](https://github.com/yt-dlp/yt-dlp/issues/1995),
[yt-dlp#1273](https://github.com/yt-dlp/yt-dlp/issues/1273),
[FFmpeg#8885](https://trac.ffmpeg.org/ticket/8885).

This patch has been substantially reworked by FFmpeg devs
[@softworkz](https://github.com/softworkz) and
[@mstorsjo](https://github.com/mstorsjo),
and merged in a series of commits:
[3fb9244](https://github.com/FFmpeg/FFmpeg/commit/3fb924464244bc317a5d19ab25625ae35abde512)
[4cdc14a](https://github.com/FFmpeg/FFmpeg/commit/4cdc14aa955805931b918d30d9c7349ab924dd52)
[6076dbc](https://github.com/FFmpeg/FFmpeg/commit/6076dbcb55d0c9b6693d1acad12a63f7268301aa)
[f579a1d](https://github.com/FFmpeg/FFmpeg/commit/f579a1d08b269b6dfc89596af20582c01950adb2)
[6b32ad5](https://github.com/FFmpeg/FFmpeg/commit/6b32ad59c8fe16fc792ca5a468b95ce5232ff6d1)
[c5aba39](https://github.com/FFmpeg/FFmpeg/commit/c5aba39a041fdaac267fc8c6a2ef745a94a2b0da)
[bc8f1bb](https://github.com/FFmpeg/FFmpeg/commit/bc8f1bbe233b435dc474df272dac0b5b6d0ef536)
[5d5a014](https://github.com/FFmpeg/FFmpeg/commit/5d5a01419928d0c00bae54f730eede150cd5b268)
[3b3c567](https://github.com/FFmpeg/FFmpeg/commit/3b3c567ad3d45a3f5d90668a1dd32f11b89fc4b5)
[fee765c](https://github.com/FFmpeg/FFmpeg/commit/fee765c2078ba03e346e311c86a447a116fe8c5f)
[cc5844d](https://github.com/FFmpeg/FFmpeg/commit/cc5844da988fb7ca1051775a3dac43de77bf3881)
[dfa062e](https://github.com/FFmpeg/FFmpeg/commit/dfa062ed3cae1d7ae3fdc52c7adda09cfc2e29b9)
[13350e8](https://github.com/FFmpeg/FFmpeg/commit/13350e81fd43cbd1aa3bbb7ed567e7dc7dd2b7f5)
[c381f54](https://github.com/FFmpeg/FFmpeg/commit/c381f5412fe810bd8118123aed9bd4f76b75b59d)
[69364a0](https://github.com/FFmpeg/FFmpeg/commit/69364a06c65d3437e8158cdffd98c2f6d1b84dd2)



## Credits

* [@BtbN](https://github.com/BtbN) for the [original workflow](https://github.com/BtbN/FFmpeg-Builds)
* [@nihil-admirari](https://github.com/nihil-admirari) for creating and maintaining this repo

---

PS: The commits are unsigned because of the periodic [automatic rebase](https://github.com/yt-dlp/FFmpeg-Builds/actions/workflows/rebase-on-upstream.yml)

### Build FFmpeg

* `./build.sh target variant [addins]`

On success, the resulting zip file will be in the `artifacts` subdir.

### Targets, Variants and Addins

Available targets:
* `win64` (x86_64 Windows)
* `win32` (x86 Windows)
* `linux64` (x86_64 Linux, glibc>=2.23, linux>=4.4)
* `linuxarm64` (arm64 (aarch64) Linux, glibc>=2.27, linux>=4.15)

The linuxarm64 target will not build some dependencies due to lack of arm64 (aarch64) architecture support or cross-compiling restrictions.

* `davs2` and `xavs2`: aarch64 support is broken.
* `libmfx` and `libva`: Library for Intel QSV, so there is no aarch64 support.

Available:
* `gpl` Includes all dependencies, even those that require full GPL instead of just LGPL.
* `lgpl` Lacking libraries that are GPL-only. Most prominently libx264 and libx265.
* `nonfree` Includes fdk-aac in addition to all the dependencies of the gpl variant.
* `gpl-shared` Same as gpl, but comes with the libav* family of shared libs instead of pure static executables.
* `lgpl-shared` Same again, but with the lgpl set of dependencies.
* `nonfree-shared` Same again, but with the nonfree set of dependencies.

All of those can be optionally combined with any combination of addins.
* `4.4` to build from the 4.4 release branch instead of master.
* `5.0` to build from the 5.0 release branch instead of master.
* `debug` to not strip debug symbols from the binaries. This increases the output size by about 250MB.