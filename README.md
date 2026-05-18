<img align="right" width="150" alt="logo" src="https://user-images.githubusercontent.com/5889006/190859553-5b229b4f-c476-4cbd-928f-890f5265ca4c.png">

# 我ㄉ Hugo 部落格

本部落格使用 [Hugo](https://gohugo.io/) 作為靜態網站產生器，並採用了 [Hugo theme Stack](https://github.com/CaiJimmy/hugo-theme-stack) 這個美觀的主題。特別感謝主題作者 [CaiJimmy](https://github.com/CaiJimmy) 提供如此出色的設計（Credit to CaiJimmy for the Hugo theme Stack）。

## 如何更新主題

本專案使用 Hugo modules 來載入主題。若想要手動更新主題到 `v3` 的最新版本，請在終端機執行以下指令：

```bash
hugo mod get -u github.com/CaiJimmy/hugo-theme-stack/v3
hugo mod tidy
```

> **注意：** 目前專案設定使用 `v3` 版本的主題。由於 Go module 的限制，如果未來主題發布了 `v4` 或更新版本，你需要手動修改 `config/module.toml` 檔案來進行大版本升級。

## 如何建立新文章

1. 在 `content/post/` 目錄下建立一個新的資料夾，並以文章標題命名（建議加上表情符號，如 `🗺️我的新文章`）。
2. 在該資料夾內建立與資料夾同名的 Markdown 檔案（如 `🗺️我的新文章.md`）。
3. 在 Markdown 檔案開頭加入 Front Matter 設定檔，範例如下：

```yaml
---
title: "🗺️我的新文章"
description: 文章簡短描述...
slug: my-new-post
date: 2026-05-18 10:21:12
tags: 
    - 標籤1
categories: 
    - 分類1
image: https://cdn.jsdelivr.net/gh/ncchen99/web-app-assets@main/blog/image/cover.jpg
---
```

## 如何上傳圖片至 CDN

為了加快圖片載入速度，本專案將圖片統一存放於獨立的 GitHub 儲存庫 `web-app-assets`，並透過 jsDelivr 產生 CDN 連結。

1. 準備好你要使用的圖片，建議將檔名更改為英文格式（例如 `my-image.jpg` 或 `my-image.svg`）。
2. 將圖片檔案移動到本機的 `web-app-assets/blog/image/` 目錄中。
3. 透過終端機進入 `web-app-assets` 專案目錄，將圖片提交（Commit）並推送（Push）到 GitHub：

```bash
cd ../web-app-assets # 根據你的實際路徑調整
git add blog/image/你的圖片.jpg
git commit -m "Add new images"
git push
```

4. 圖片推送到 GitHub 後，即可透過 jsDelivr 取得 CDN 網址，格式如下：
   `https://cdn.jsdelivr.net/gh/ncchen99/web-app-assets@main/blog/image/你的圖片.jpg`
5. 在文章的 Markdown 檔案中，使用以下語法插入圖片即可：
   `![圖片說明](https://cdn.jsdelivr.net/gh/ncchen99/web-app-assets@main/blog/image/你的圖片.jpg)`
