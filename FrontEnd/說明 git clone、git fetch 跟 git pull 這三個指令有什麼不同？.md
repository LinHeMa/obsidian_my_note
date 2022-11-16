---
date: 2022-07-26
title: 說明 `git clone`、`git fetch` 跟 `git pull` 這三個指令有什麼不同？
aliases: []
tags:
  - git
  - pull
  - clone
  - merge
category: recap
from: appwork school
---
# 請說明 `git clone`、`git fetch` 跟 `git pull` 這三個指令有什麼不同？
## **git clone**

clone 指令會把線上的專案，「整個」複製一份到你的電腦裡，並且在你的電腦裡建立相對應的標案及目錄（包括 `.git` 目錄），通常這個指令只會在一開始的時候使用，clone 之後要再更新的話，通常是執行 `git fetch` 或 `git pull` 指令。

## **git fetch**

假設遠端節點叫做 `origin`，當執行 `git fetch` 指令的時候，Git 會比對本機與遠端（在這邊就是 `origin`）專案的差別，會「下載 `origin` 上面有但我本機目前還沒有」的內容下來，並且在本地端形成相對應的分支。

不過，fetch 指令只做下載，並不會進行合併。

## **git pull**

pull 指令其實做的事情跟 fetch 是一樣的，差別只在於 fetch 只有把檔案抓下來，但 pull 不只抓下來，還會順便進行合併。也就是說，本質上，git pull 其實就等於 git fetch 加上 merge 指令。

