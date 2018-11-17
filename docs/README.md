---
home: true
heroImage: /hero.png
actionText: 入坑指南 →
actionLink: /1-Preparations/
features:
- title: 🍳
  details: Windows 开发，解决那令人烦恼的非 Unix 终端环境。
- title: 💡
  details: Windows Subsystem for Linux，近似原生 Unix 的体验，又有着 Windows 强大的生产力。
- title: 🎉
  details: 与 Visual Studio Code 联合，打造最为健壮的 Windows 开发环境。
footer: 2018 ©Spencer Woo. Released under the CC BY-NC-ND 4.0 International License.
---

[![Build Status](https://img.shields.io/travis/spencerwooo/dowww.svg?style=flat-square)](https://travis-ci.org/spencerwooo/dowww)
[![GitHub stars](https://img.shields.io/github/stars/spencerwooo/dowww.svg?style=flat-square&label=⭐%20Stars)](https://github.com/spencerwoo/dowww)
![love](https://img.shields.io/badge/Made%20with-love-ff69b4.svg?style=flat-square)
![Windows](https://img.shields.io/badge/Windows-♥-FFE411.svg?logo=windows&style=flat-square)
[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-03A9F4.svg?style=flat-square)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

# 前言

首先达成一个共识：Windows 给 **编程初学者** 带来了很大的困难。比如 **缺乏好用的包管理系统**、**终端环境难看难用** 和 **环境变量不易配置** 等等，这些都让 Windows 在开发体验上难以匹敌 Linux 甚至 macOS。

WSL 的出现似乎缓解了这些烦恼。WSL —— Windows Subsystem for Linux，即适用于 Linux 的 Windows 子系统，是一个为在 Windows 10 上能够原生运行 Linux 二进制可执行文件的兼容层。WSL 的出现意味着我们可以借助它来给我们的 Windows 配置一个美观可用的 **学习编程的开发环境**，包括：

- 💻 Unix style 终端环境：`zsh` 和 `oh-my-zsh`
- 🔨 与 macOS 的 Homebrew 一样原理的包管理器：`apt`（针对 Ubuntu）
- 📰 与 Visual Studio Code 配合的编辑调试环境

# 为什么要做这样一个参考文档？

这是我根据我这半年来在 Windows 上面利用 WSL 进行开发编码摸索出来的经验总结。其主要原因在于 Windows 上面没有我可以忍受的包管理工具。在中国特殊的互联网环境下，我的 Chocolatey 从来没下载成功过，而 macOS 上有 Homebrew、Linux 各大发行版也都有各自的包管理工具，于是 WSL 成为了我在 Windows 下进行开发工作的首选环境。

> 有关 macOS 上面的包管理 Homebrew 的进阶用法，推荐阅读由少数派编辑 [@Minja](https://sspai.com/user/731139) 亲手操刀撰写的 > [像 Mac 高手一样管理应用，从 Homebrew 开始](https://sspai.com/post/42924)

![Chocolatey 又失败了](https://i.loli.net/2018/11/16/5bee9ef1d8a7d.png)

那么为什么我们不直接转移到 Linux 上面去开发呢？主要由于 Linux 桌面环境虽然在 2018 年的今天有很大的改善，但是相比 Windows 或 macOS 还有着十足的差距，程序假死、常用软件没有适配、部分发行版繁琐的配置等等。**对新手的不友好让刚接触代码的我们望而却步。**

不过同时，不得不承认，虽然 WSL 极大地方便、优化了我们在 Windows 上面的开发体验，但是很多东西都是需要进行一些配置才可以做到 **丝滑流畅** 的运行。并且，除了能够做到「又不是不能用」，我们还要追求一下开发环境的美丽养眼。这支教程也就应运而生了。

# 我都介绍了什么？

- 如何搭建一套比 Windows 原生开发工具体验更好的 Unix 开发环境
- 如何配置一个可能是 Windows 上可定制化程度最高的终端模拟器与终端环境
- 一些利用 Visual Studio Code 在 Windows 上与 WSL 中的工具配合进行开发和调试的 Tips（包括 Python 和 C/C++ 的开发）
- 利用 X-Server 直接打开 Linux 上的 GUI 窗口程序进行原生开发的操作指北

这些是我这里的参考指南所重点介绍的内容。以参加 ACM 的同学或是刚开始学习 C/C++ 的同学为例子，相信你经过这篇参考教程的配置（具体在这里 > [Dev on Windows with WSL | C/C++](https://spencerwoo.com/dowww/3-VSCode/3-4-C_Cpp.html)）之后：

- 可以从左边丑陋的 Dev C++ 进化为 Visual Studio Code：

![Dev C++ VS VSCode](https://i.loli.net/2018/11/09/5be546bb273b3.jpg)

- 可以从左边傻黑粗的 Command Prompt 或 Powershell 进化为 Unix style 的终端环境：

![2.jpg](https://i.loli.net/2018/11/09/5be5484eb47f4.jpg)
 
**配置简单、扫清障碍、转为学习、高效开发。** 🎉🎉🎉

但是还有一些内容，比如：

- 如何配置 Visual Studio Code 更好看
- 如何配置 Windows 下（或是 macOS 下）的终端环境更好看
- 如何配置 Windows 更好看

这些问题太过主观，在这里我最想解决的是如何让 WSL 下的工具能够更加丝滑的与 Windows 开发工具配合，来提高我们的开发效率。并且说实话，**教程中介绍的工具无需进一步的配置就足够美观了**。如有需求，可以查看我的往期文章（上面链接）进行自行查看甄别与折腾。

# 为什么我这样推荐 Visual Studio Code？

这个问题可以这样来理解：Visual Studio Code 与其他诸如 Atom, Sublime Text 3 和 Notepad++ 等等现代化代码编辑器相比，有哪里体验更加优质？

![VSCode](https://i.loli.net/2018/11/16/5bee9f02c0ad7.png)

**简单的说，Visual Studio Code：**

开源、免费、生态庞大、支持完善、调试便捷、定制化程度高。

**具体讲，Visual Studio Code：**

- 开源，是目前微软开源项目中最受欢迎的一个。
- 社区支持，有着成千上万的插件、主题、拓展来把它定制成为我们想要的样子。
- 内置非常完善的机制与 Git 集成版本控制工具集成，开发体验极佳。
- 内置调试工具能够力压其他任何编辑器，在我使用过程中从未见过调试功能有 Visual Studio Code 强大的编辑器。

而与此同时，Atom 虽然也很好看，但是由于优化问题其性能远比不上 Visual Studio Code。同时 Sublime Text 3 是闭源软件，需要付费购买，就如曾经 Sublime Text 上面可能是最受欢迎的主题 Material Theme 的作者所说（详见 Deprecation Note）：

> 它是一个：80$ commercial software that is 80% cracked or used in free mode.

这样看来，我推荐使用 Visual Studio Code 就更加有理由了。

# 体验

不得不承认，WSL 还在开发完善，有许许多多的 bug 等待修复，同时 Visual Studio Code 各大插件组也在努力适配 WSL。但是我想说，单就目前 Windows 上面糟糕的包管理系统来说，**进行轻量开发或是学习编程知识**，WSL 这一条技术栈都是更用户友好的。

![](https://i.loli.net/2018/11/16/5bee9f0b3c796.png)

**对于 WSL 终端环境来说：**

- 终端环境下的所有组件都可以完美运行，包括版本控制工具 `git`、远程登录工具 `ssh` 和包管理工具 `apt`（针对 Ubuntu 来说）等等。

**对于具体的编程语言在 VSCode 里面的开发来讲：**

- C/C++ 和 Node.js 由于插件开发组已经适配，因此可以完美的正常调试和开发，与原生的 Windows 工具别无两样。

- Python 由于插件开发组正在进行适配，经过一些努力和配置也是可以运行，处于「又不是不能用」的状态。

- 其他语言还需要考证，截至发稿，我的这只文档也只介绍了 C/C++/Python 的配置，因此还有很多需要补充的地方，希望有能力、有经验的同学前来帮我一起完善，感激不尽。🌹🌹🌹

希望这支参考指南能够在帮助你在 Windows 上面利用 WSL 进行开发的时候少走一些弯路。Happy coding!

目前仍然有很多地方需要完善，当然 WSL 本身也有很多小 bug，希望有经验的同学前来帮我共同完善本项目。鞠躬。

详细请见 > [💗💗💗 Help needed.](/3-VSCode/HelpNeeded.html)

# License 许可

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="創用 CC 授權條款" style="border-width:0; padding-top:10px;" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a>

本著作係採用<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">創用 CC 姓名標示-非商業性-禁止改作 4.0 國際 授權條款</a>授權。

---

💡 **Dev on Windows with WSL** ©Spencer Woo. Released under the CC BY-NC-ND 4.0 International License.

Authored and maintained by Spencer Woo.

[@Blog](https://spencerwoo.com/) · [ⒿJike](https://web.okjike.com/user/4DDA0425-FB41-4188-89E4-952CA15E3C5E/post) · [@GitHub](https://github.com/spencerwooo)