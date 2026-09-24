# DistApp

xiniu-APP 的应用分发页。

- 下载页托管在 GitHub Pages：<https://xiniu-app.github.io/DistApp/>
- **安装包走 GitHub Releases，不进 git**（见 `.gitignore` 的说明）

## 结构

```
.
├── index.html          应用列表
├── .nojekyll           告诉 Pages 不要跑 Jekyll（否则下划线开头的目录会被忽略）
└── <app>/
    ├── install-*.html  该应用的下载与安装说明（mac / ios）
    └── manifest.plist  iOS 应用才有：itms-services 安装清单，指向 Releases 里的 ipa
```

## 发布一个新版本

由各应用自己的发布脚本完成：

```bash
cd <macguard 项目目录> && bash tool/release.sh     # MacGuard
cd <trackflow 项目目录> && scripts/release.sh      # TrackFlow（iPhone Ad Hoc + Mac dmg + 安卓 apk，一个 Release）
cd <daymark 项目目录>   && scripts/release.sh      # DayMark（iOS，Ad Hoc）
cd <footprint 项目目录> && scripts/release.sh      # Footprint（iOS，Ad Hoc）
```

脚本会把安装包传到本仓库的 Releases，并刷新对应的 `install.html`。
