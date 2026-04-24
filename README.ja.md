# pose-cam

ブラウザで動作するリアルタイムの姿勢・手・顔検出アプリです。サーバー不要で完全ローカル動作します。

**ライブデモ**: https://ota.github.io/pose-cam/

## 機能

- カメラ映像から骨格をリアルタイム表示
- 5種類の姿勢検出モデルを切り替え可能
- 手の指関節検出（1手あたり21キーポイント）
- 顔メッシュ・顔パーツの可視化（478ランドマーク）
- カメラ切り替え・ミラーモード
- PC・スマートフォン対応

## モデル一覧

| モデル | サイズ | 備考 |
|-------|------|-------|
| MoveNet Lightning | 約3 MB | 高速・軽量 |
| MoveNet Thunder | 約12 MB | 高精度・やや重い |
| MP Pose Lite | 約3 MB | MediaPipe、軽量 |
| MP Pose Full | 約6 MB | MediaPipe、バランス型 |
| MP Pose Heavy | 約26 MB | MediaPipe、最高精度 |
| Hand Landmarker | 約8 MB | Hand ON時にロード |
| Face Landmarker | 約28 MB | Face ON時にロード |

## プライバシー

すべての推論はブラウザ内で完結します。カメラ映像が外部サーバーに送信されることはありません。モデルファイルは初回のみCDNからダウンロードされます。

## 技術スタック

- **TensorFlow.js** — WebGLバックエンドによるMoveNet推論
- **MediaPipe Tasks Vision (WASM)** — Pose / Hand / Face ランドマーク推論
- **WebRTC (getUserMedia)** — カメラ映像の取得
- **Canvas 2D API** — 骨格オーバーレイの描画

## 使い方

https://ota.github.io/pose-cam/ をブラウザで開き、カメラへのアクセスを許可するだけです。インストール不要。

ローカルで動かす場合：

```bash
python3 -m http.server 8080
# http://localhost:8080 をブラウザで開く
```

> 注意: WebAssemblyとカメラアクセスのブラウザセキュリティ制限により、`file://` では動作しません。HTTP/HTTPSで配信する必要があります。
