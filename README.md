![Wordle+](https://raw.githubusercontent.com/angelofan/wordle/main/public/img/og_1200x630.png)
<div align="center">
  <a href="https://angelofan.github.io/wordle/" ><img src="https://github.com/angelofan/wordle/workflows/Publish/badge.svg?branch=main" alt="已部署的工作流程"/></a>
  <img src="https://img.shields.io/github/package-json/v/angelofan/wordle" alt="GitHub package.json 版本" />
</div>

<p align="center">
  <a href="https://github.com/angelofan/wordle/blob/main/README.md">简体中文</a> | <a href="https://github.com/angelofan/wordle/blob/main/README_en.md">English</a>
</p>

---

Josh Wardle（现已被《纽约时报》收购）制作的流行游戏 [Wordle](https://www.nytimes.com/games/wordle/) 的再制作版本，具有额外的模式和功能。
托管在 GitHub 页面上 [此处](https://angelofan.github.io/wordle/) 。

# 附加功能
- 单词是从单词列表中随机选择的，而不是按顺序选择的，并且答案不会存储在 浏览器本地存储（localStorage） 中，这使得作弊变得更加困难。 随机数的种子是从日期开始创建的，确保每个人都获得相同的随机数，以便人们仍然可以交流答案。
- 当您完成游戏时，单词的释义将显示在游戏模式结束时。
- 除了其他统计数据外，您的平均猜测和您的失败次数也会显示在获胜模式中。
- 当设定的游戏模式的计时器达到 0 时，它会变为刷新按钮，而不仅仅是停留在 00:00:00。
- 当设定的游戏模式的计时器达到 0 时，左上角会出现刷新按钮。
- 设置菜单中的提示小部件，其中包含有关游戏功能的实用信息。
- 右键单击格子上提交的单词将告诉您它的释义。
- 右键单击格子提交的单词将告诉您线索信息，显示有多少符合给出线索的单词。
- 右键单击最后提交的单词下方的行将告诉您还有几种猜测会给出有用的线索。
- 游戏模式设定在链接中，让您可以直接分享游戏模式。
- 您可以分享特定游戏期数的链接，让您可以重玩历史游戏，并与朋友分享特定回合的快速变化模式。
- 您可以通过从设置菜单访问并输入游戏期数或链接开始重玩以前的游戏。
- Service Worker，允许游戏作为渐进式网络应用程序轻松下载并离线运行。
- 放弃按钮。

## 附加模式
可以通过单击屏幕顶部的 单词竞猜 或向任一方向滑动棋盘来更改游戏模式。

**时时竞猜**: 每小时一个新词。

**无限竞猜**: 每次刷新都会有一个新单词，适合真正的瘾君子。

# 技术细节
这是用基于 Typescript 的 Svelte 编写的。 这是我（[原作者](https://github.com/MikhaD)）的第一个 Svelte 项目，旨在作为练习来帮助我学习并精通 Svelte。 它还使用一些基本的 scss 进行样式设置。

该项目是使用 `npm init vite@latest` 并选择 Svelte 模板进行初始化的。

该项目是由 [angelofan](https://github.com/angelofan) 从 [MikhaD 的 wordle 项目](https://github.com/MikhaD/wordle/) 翻译成简体中文的。

# 分叉这个项目
欢迎任何人分叉这个存储库并用它做他们喜欢的事情，只要他们遵循随附的许可证（GPL-3.0）。
如果您能链接回此存储库并在您的项目中归功于我，我也将不胜感激。

玩得开心 :)

# 分析
该项目包含基本的谷歌分析，记录以下信息：
- 访客数量
- 访问者所在国家/地区
- 他们是通过直接链接还是搜索引擎到达的
- 实时总人数

此信息无法链接回个人用户。 它仅供我个人使用，不与其他人共享。 这是我的第一个“重大”面向公众的项目，能够看到有多少人来自世界各地在玩这个项目是我继续致力于该项目的一个重要因素。

<details>
<summary>如何创建新模式</summary>

- 将模式名称添加到 `enums.ts` 中 GameMode 枚举的 **最后面**
- 在 `utils.ts` 的 newSeed 函数中添加该模式的案例
- 将 ModeData 对象添加到 `utils.ts` 中的 modeData 模式数组中
</details>
