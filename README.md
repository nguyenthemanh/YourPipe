<!-- prettier-ignore -->
<div align="center">

<img src="./AppScope/resources/base/media/app_icon.png" alt="YourPipe" height="96" />

# YourPipe

**YouTube client for OpenHarmony / HarmonyOS**

[![Version](https://img.shields.io/badge/version-0.7.0-blue?style=flat-square)](AppScope/app.json5)
[![HarmonyOS](https://img.shields.io/badge/HarmonyOS-6.1.0(23)-black?style=flat-square)](https://developer.huawei.com/consumer/en/harmonyos/)
[![Player](https://img.shields.io/badge/player-MPV-brightgreen?style=flat-square)](https://github.com/mpv-player/mpv)
[![License](https://img.shields.io/badge/license-GPL--3.0-yellow?style=flat-square)](LICENSE)

> Unofficial client. **Not affiliated with YouTube or Google.**

**Bản cải tiến** của tác giả gốc [Ember5843/YourPipe](https://github.com/Ember5843/YourPipe). Bản này thêm tiếng Việt so với bản gốc.

**Improved fork** of [Ember5843/YourPipe](https://github.com/Ember5843/YourPipe). Vietnamese UI is added on top of the original.

**改进版**，原作者：[Ember5843/YourPipe](https://github.com/Ember5843/YourPipe)。在原版基础上新增越南语界面。

**改良版**。原作者：[Ember5843/YourPipe](https://github.com/Ember5843/YourPipe)。オリジナルにベトナム語表示を追加。

[English](#english) · [中文](#中文) · [日本語](#日本語)

</div>

---

## Cài sẵn / Prebuilt

Tải bản đã build rồi cài, không cần mở DevEco Studio.

**[YourPipe-0.7.0.hap](https://github.com/nguyenthemanh/YourPipe/releases/latest/download/YourPipe-0.7.0.hap)** · HarmonyOS arm64 · `com.talon.yourpipe` · 0.7.0

```text
hdc install -r YourPipe-0.7.0.hap
```

Bật tùy chọn nhà phát triển trên máy. Đây là bản ký debug: nếu máy báo lỗi chữ ký, UDID chưa nằm trong hồ sơ ký, khi đó hãy build và ký bằng DevEco của bạn.

**EN:** Download the prebuilt HAP above and install it with `hdc`. Debug-signed. Turn on Developer options.
**中文：** 下载上方已构建的 HAP，用 `hdc` 安装。调试签名，请先打开开发者选项。
**日本語：** 上のビルド済み HAP をダウンロードし、`hdc` でインストールします。デバッグ署名です。開発者オプションを有効にしてください。

---

## English

**Improved fork** of [Ember5843/YourPipe](https://github.com/Ember5843/YourPipe), with Vietnamese added to the original. **YourPipe** is a YouTube client for **OpenHarmony / HarmonyOS**. It extracts streams inside the app and plays them with native **MPV** (vendored libmpv + FFmpeg), not a WebView.

- Home, search, channels, playlists, subscriptions, and favorites
- Native MPV playback, background audio, and offline downloads
- Cookie and device-QR sign-in, HTTP proxy, and on-device translation
- UI languages include English and Vietnamese, following the system or a manual choice
- Package: `com.talon.yourpipe` · HarmonyOS `6.1.0(23)` and later

Open this folder in DevEco Studio, sync OHPM, configure Signing Configs, then run on an arm64 device.

---

## 中文

本仓库是原作者 [Ember5843/YourPipe](https://github.com/Ember5843/YourPipe) 的**改进版**，在原版之上**新增越南语**。**YourPipe** 是面向 **OpenHarmony / HarmonyOS** 的 YouTube 客户端。应用在本地解析流，并通过原生 **MPV**（内置 libmpv + FFmpeg）播放，而不是 WebView。

- 首页、搜索、频道、播放列表、订阅与收藏
- 原生 MPV 播放、后台音频、离线下载
- Cookie 与设备二维码登录、HTTP 代理、本地翻译
- 界面语言包含英语和越南语，可跟随系统或手动选择
- 包名：`com.talon.yourpipe` · HarmonyOS `6.1.0(23)` 及以上

用 DevEco Studio 打开本目录，同步 OHPM，配置签名后，在 arm64 设备上运行。

---

## 日本語

本リポジトリは原作者 [Ember5843/YourPipe](https://github.com/Ember5843/YourPipe) の**改良版**で、オリジナルに**ベトナム語**を追加しています。**YourPipe** は **OpenHarmony / HarmonyOS** 向けの YouTube クライアントです。アプリ内でストリームを取り出し、WebView ではなくネイティブ **MPV**（同梱の libmpv + FFmpeg）で再生します。

- ホーム、検索、チャンネル、再生リスト、登録チャンネル、お気に入り
- ネイティブ MPV 再生、バックグラウンド音声、オフラインダウンロード
- Cookie と端末 QR ログイン、HTTP プロキシ、端末内翻訳
- 表示言語は英語とベトナム語に対応。システムに従うか、手動で選べます
- パッケージ名：`com.talon.yourpipe` · HarmonyOS `6.1.0(23)` 以降

DevEco Studio でこのフォルダを開き、OHPM を同期して署名を設定し、arm64 端末で実行してください。

---

## Overview

YourPipe is a YouTube client for **OpenHarmony / HarmonyOS**. It extracts streams in-app and plays them through a native **MPV** pipeline (vendored libmpv + FFmpeg), not a WebView player.

| | |
|---|---|
| **Package** | `com.talon.yourpipe` |
| **Version** | `0.7.0` |
| **Target SDK** | `26.0.0` (min `6.1.0(23)`) · HarmonyOS · stage model |
| **Devices** | phone · tablet · 2in1 · tv · car |

Guest VOD uses direct-link DASH through the **visionos** endpoint into MPV by default; signed-in playback defaults to the **SABR** dual-track local proxy (mweb). Playback is **MPV only**: the `libmpv_napi` module is a NAPI bridge over a vendored `libmpv.so`, originally derived from [libmdk-napi](https://github.com/wang-bin/libmdk-napi) (historical `mdk` names exist only in old commits).

---

## Features

- Home feed, search, channels, and playlists
- Subscriptions and favorites
- Native MPV playback (quality / codec options, PiP where supported)
- Background audio via continuous task + AV session
- Offline downloads into the local library
- Cookie (WebView) login and device QR (OAuth) login
- HTTP proxy settings
- Multi-provider translation (gtx / Google Cloud / MyMemory / Lingva / LibreTranslate / DeepL / LLM / custom)
- Live chat (read-only) on live videos
- Light / dark / system appearance and multiple UI locales
- Local library: downloads, imported files, watch history, playlists

Main tabs: **Home · Subscriptions · Favorites · Local**. Search and Options open as separate pages/sheets.

---

## Modules

```text
entry  →  mediaservice  →  youtube_core
  │              └────→  @yourpipe/libmpv-napi  (MPV bridge)
  └──────────→  youtube_core
```

| Module | Role |
|--------|------|
| `entry` | UI, pages, preferences, auth, PoToken WebView |
| `mediaservice` | Playback engine, AV session, local media proxy, offline download |
| `youtube_core` | YouTube extraction, cipher, HLS/SABR session, auth storage |
| `libmpv_napi` | NAPI bridge to MPV (+ vendored FFmpeg / libmpv on arm64) |

`arm64-v8a` is the product playback ABI. `x86_64` builds use a player stub (UI only).

---

## Requirements

- [DevEco Studio](https://developer.huawei.com/consumer/en/deveco-studio/) with HarmonyOS SDK **6.1.0(23)**
- Device or emulator (phone / tablet / 2in1 / tv / car)
- Real video playback needs an **arm64-v8a** device

---

## Getting started

1. Clone the repository:

   ```bash
   git clone https://github.com/nguyenthemanh/YourPipe.git
   cd YourPipe
   ```

2. Open the project root in DevEco Studio and sync ohpm dependencies.
   `build-profile.json5` is git-ignored (machine-local) — copy it from the
   committed template first: `cp build-profile.template.json5 build-profile.json5`.

3. Configure **signing** under **File → Project Structure → Signing Configs** (writes
   into your local, git-ignored `build-profile.json5`). **Never commit** keystores, passwords, profiles, or certificates.

4. Optional: if you use AppGallery Connect, put the AGC services config under  
   `entry/src/main/resources/rawfile/` (that file is git-ignored).

5. Select a device and **Run** from DevEco.

---

## Authentication

- **Cookie login** (WebView) and **device QR** (OAuth) are supported for personalization and restricted content.
- Device OAuth constants may mirror publicly documented community client values; treat them as community POC material, not YourPipe-owned credentials.

---

## References

Behavior and naming draw on these open projects (not alternate runtimes inside this app):

| Project | Role |
|---------|------|
| [NewPipe](https://github.com/TeamNewPipe/NewPipe) | Client UX reference |
| [NewPipe Extractor](https://github.com/TeamNewPipe/NewPipeExtractor) | Extraction / stream models |
| [PipePipe](https://github.com/InfinityLoop1308/PipePipe) | Player-client / extractor compatibility |
| [libmdk-napi](https://github.com/wang-bin/libmdk-napi) | Historical origin of the NAPI bridge structure and naming |
| [MPV](https://github.com/mpv-player/mpv) | Playback core (libmpv) |

---

## License

GPL-3.0. See [LICENSE](LICENSE). Upstream project: [Ember5843/YourPipe](https://github.com/Ember5843/YourPipe).

Portions and ideas reference NewPipe, NewPipe Extractor, PipePipe, MPV, and related work. Respect their licenses when redistributing.
