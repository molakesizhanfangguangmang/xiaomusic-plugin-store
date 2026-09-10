# xiaomusic 插件商城

给 [xiaomusic](https://github.com/hanxi/xiaomusic)（小爱音箱网页控制面板）的插件包分发页。

这里只放打包好的插件 zip。想装哪个，下载 zip，通过 xiaomusic 控制面板的「上传工具」页装进去。

适用版本：`hanxi/xiaomusic:v0.6.1`。

---

## 可用插件

| 插件 | 版本 | 下载 | 说明 |
| --- | --- | --- | --- |
| 删除歌曲 | 1.0.0 | [delete-song-1.0.0.zip](plugins/delete-song-1.0.0.zip) | 从已下载（`download/`）的歌里单选一首，二级确认后永久删除 |
| 链接下载音频 | 1.0.0 | [bili-url-download-1.0.0.zip](plugins/bili-url-download-1.0.0.zip) | 粘贴 B 站视频/分享链接（或其它 yt-dlp 能解析的 URL），抽音轨转 mp3 落到 `download/` |
| 工具区安装包 | 1.0.0 | [xiaomusic-tools-installer-1.0.0.zip](plugins/xiaomusic-tools-installer-1.0.0.zip) | 上面两个插件依赖的工具区本体 + 上传接口，整包，含一键安装/卸载脚本 |
| 刷新歌曲时长 | 1.0.0 | [另见独立仓库](https://github.com/molakesizhanfangguangmang/xiaomusic-plugin-duration-refresh) | 勾选本地歌曲重算时长并覆盖缓存；**需另打后端补丁**，装法见其仓库 |

前两个是单插件包；第三个是工具区本体，装插件之前得先有它。

最后一个**与前三个性质不同**：它除了插件页，还需要一份后端补丁（要覆盖容器里的 `.py`），
所以插件 zip 与补丁都放在它自己的仓库里，本页不放。装之前先读那个仓库的 README。

---

## 怎么用

前提：目标 xiaomusic 已经装好工具区，也就是先装上面那个「工具区安装包」。

把它解开，在能执行 docker 的宿主机上跑：

```sh
./install.sh
```

装好后打开控制面板，主页有「工具」入口 → 工具卡片页 →「上传工具」，选本页下载的插件 zip 即可。

不想用上传页，也可以手动装：把插件 zip 解开，目录拷进容器内
`/app/xiaomusic/static/xiaomusic_tools/<id>/`，再把该目录登记进同级的 `tools.json`。

插件包的格式（`manifest.json` 字段、目录结构）见 [`xiaomusic-tools`](https://github.com/molakesizhanfangguangmang/xiaomusic-tools) 仓库的 README。

---

## 目录

```
plugins/          插件包 zip，按 <id>-<version>.zip 命名
registry.json     插件清单（id/title/icon/desc/version/url），沿用 tools.json 字段
README.md         本页
```

---

## 相关仓库

- [`xiaomusic-tools`](https://github.com/molakesizhanfangguangmang/xiaomusic-tools)：工具区本体、上传接口、一键安装/卸载包。
- [`xiaomusic-web-delete-tool`](https://github.com/molakesizhanfangguangmang/xiaomusic-web-delete-tool)：删除歌曲 + 链接下载音频这两个工具的开发仓库。
- [`xiaomusic-plugin-duration-refresh`](https://github.com/molakesizhanfangguangmang/xiaomusic-plugin-duration-refresh)：刷新歌曲时长（插件页 + 后端补丁）。

---

## 许可

MIT
