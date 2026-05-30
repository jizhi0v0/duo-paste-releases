# duo-paste-releases

DuoPaste 自动更新发布仓（公开）。**只放发布产物，不放源码。**

- `appcast.xml` — Sparkle feed，由源仓 `jizhi0v0/duo-paste`(私有) 的 release CI 自动生成 + push。
- Releases assets — 每个版本的签名 + 公证 `.dmg`，由 CI 上传。

客户端 daemon 通过 `SUFeedURL = https://raw.githubusercontent.com/jizhi0v0/duo-paste-releases/main/appcast.xml` 拉取。

更新包用 EdDSA(Ed25519) 签名，公钥编进 app（`SUPublicEDKey`），私钥在 CI secret `SPARKLE_ED_PRIVATE_KEY`。
