---
title: 何谓 Code of Conduct？
description: Most developers code C++ like C. ——牛津词典

style: /assets/articles/code-of-conduct/style
mermaid: true
---

# 何谓 Code of Conduct？

> 2022 年 1 月 28 日、2 月 4–7 日。
>
> 本文的其它版本：[微信](https://mp.weixin.qq.com/s/zccs-RgZjSbonUMZg0jykg)、[WriteBug.com](https://www.writebug.com/explore/article/resvent1)。

一言以蔽之：行为准则（rules of behavior）。

<!-- 只想学单词的读者可以退出了。 -->

## 外延

[GitHub](https://github.com/) 上很多项目都有“![]({{ '/assets/articles/code-of-conduct/conduct.svg' | relative_url }}) Code of conduct”，这与“README”等被一同列为“社区标准”。

<figure>
<img src="{{ '/assets/articles/code-of-conduct/about-Jekyll-on-GitHub.png' | relative_url }}" alt='About 🌐 Jekyll is a blog-aware static site generator in Ruby. Site🔗: jekyllrb.com Tags: ruby, jekyll, markdown, static-site-generator, liquid, blog-engine. Community: Readme, MIT License, Code of conduct, 44k stars, 1.4k watching, 9.7k forks.'>
<figcaption markdown='1'>
[Jekyll 在 GitHub 上](https://github.com/jekyll/jekyll/)的“关于”（另见 [Insights → Community Standards](https://github.com/jekyll/jekyll/community) 页）
</figcaption>
</figure>

打开来往往是这么一些话。（以《[Contributor Covenant 2.0](https://www.contributor-covenant.org/zh-cn/version/2/0/code_of_conduct/)》为例）

> ## 我们的承诺
>
> 身为项目成员、贡献者、负责人，我们保证参与此社区的每个人都不受骚扰，不论其年龄、体型、身体条件、民族、性征、性别认同与表现、经验水平、教育程度、社会地位、国籍、相貌、种族、宗教信仰及性取向如何。
>
> 我们承诺致力于建设开放、友善、多元、包容、健康的社区环境。
>
> …………

[Stack Overflow](https://stackoverflow.com/conduct) 则具体一些。

> **如果你是来寻求帮助的，请尽可能降低其他人帮助的难度。**
>
> [遵守我们的指南](https://stackoverflow.com/help/how-to-ask)，记住社区里人人都只是志愿者。

> -   ✗ “您说的是人话吗？真的么？我为什么看不懂？”
> -   ✓ “我没太看懂你的问题……你似乎想问安装系统后如何添加分区，这样？”

## 内涵

<!-- 所谓“code of conduct”到底包括些什么？ -->

根据 [Open Source Guides 的建议](https://opensource.guide/zh-hans/code-of-conduct/#%E5%BB%BA%E7%AB%8B%E4%B8%80%E4%B8%AA%E8%A1%8C%E4%B8%BA%E5%AE%88%E5%88%99)，“code of conduct”应当描述这些：

-   何处有效？（只适用于 issues、pull requests，还是包括所有社区活动？）
-   适用于谁？（除了社区成员和项目维护者，是否包括赞助商？）
-   违反会怎样？
-   如何举报违规？

## 词典

好吧……可 code 不是代码吗，怎么是“准则”？

据[牛津](https://www.lexico.com/definition/code)等词典，code（作为名词）大致有这些意思：

1. A system of words, letters, figures, or other symbols substituted for other words, letters, etc., especially for the purposes of secrecy. 基本就是可拆字解释的“代码”。

    例：“sending messages in code” · “Morse code”（摩尔斯电码）· “the genetic code”（mRNA→ 蛋白质的那个“遗传密码”）

    同义词：cipher · secret language

2. <small>【计算机科学】</small>Program instructions. 编程写的东西，估计是大家最熟悉的，可看作上一义项的特例。

    例：“hundreds of lines of code”

3. A systematic collection of laws or regulations.

    例：“a revision of the penal code”（修订刑法典）

    同义词：law · laws · body of law · rules · regulations · constitution · system · charter · canon · jurisprudence

    - A set of conventions or moral principles governing behavior in a particular sphere.

        例：“a strict dress code”（严格的着装要求）· “a stern code of honor” · “To be worthy of that love, he adopted a strict code of moral conduct.”

        同义词：set of principles · set of standards · set of customs · manners

这里“code of conduct”的“code”正是第三个义项。类似的表达还有“an unwritten code”（不成文的规定）、“a code of practice”（行业规则）、“a code of ethics”（道德规范）。

词源上，code 最早的现代意义是第三个义项（法典），出现于 18 世纪中叶的中古英语（code）。这个词又最初源于拉丁语（cōdex），和今天英语中 codex 一样。（如图）据[牛津词典](https://www.lexico.com/definition/code)，这个词最初指查士丁尼等罗马大帝制订的法典。_cōdex_ 似乎原本指一种古人用来写字著书的木片。（→[Wiktionary](https://en.wiktionary.org/wiki/code#Etymology_1)、[牛津词典](https://www.lexico.com/definition/codex)）

<figure>
    <div class="mermaid">
        graph LR
            subgraph 现代英语
                code
                codex
            end
            
            latin[拉丁语<br>cōdex]
            --> italian[古法语<br>code]
            --> middle_english[中古英语<br>code]
            --> code
            
            latin -.-> codex
    </div>
    <figcaption>code 的词源</figcaption>
</figure>

（猜测并）总结一下，code 的意思一路泛化，罗马法典 → 法典 → 规范 → 代码，“code of conduct”中是“规范”。近几十年计算机技术发展，“代码”又渐渐专指编程写的东西。

至于 conduct，大家天天做物理实验，应该比较熟悉这个词，就不介绍了。只强调一下此处作名词，重音在前（`ˈkɒndʌkt/`；作动词时重音才在后，读`/kənˈdʌkt/`）。

（另外“*c*ode of *c*onduct”押头韵，重音一致也可能更舒服。押头韵的更多例子：知识类视频的“pause and ponder”、异步编程的`async`/`await`~~、“Bank of Beijing”~~……）

## 评论

-   出现书面的行为准则，说明这个项目或社区不再局限于相互熟识的人，陌生人参与成为常态，并且成员决心维护社区。行为准则同时明确了可以做什么，反映出欢迎和包容新成员。

-   不过单纯宣言式的行为准则本身未必有多大作用，无人努力就只是一纸空文。

    可能行为准则本来也不打算成为规章制度。它一般还指出鼓励什么，而非只列出违规行为。有点儿像诚信考试承诺书，宣传作用也许更大。

-   （在这些行为准则的适用范围内）我很难想出有哪个实际违规例子，不一定真有必要确定行为准则。当然，这也可解释为行为准则非常有效。

-   也请多关注无障碍设施：盲道、轮椅坡道、字幕、色彩对比度、多语言……还有实际的具体的人：发现别人搬东西或独自坐轮椅，给他开个门吧。

---

<details open markdown='1'>

<summary>附：牛津词典例句摘录</summary>

-   Most developers **code** C++ like C.
-   I no longer actively **code** in PHP.
-   It is a simple matter to **program** the computer to recognize such symbols.
-   All members of a species are **programmed to** build nests in the same way.
-   You can **build** database applications without writing any code.
-   They had to **execute** their dance steps with the greatest precision.
-   We **are committed to** the fundamental principles of democracy.
-   She didn't love him enough to **commit herself to** him.
-   He was **committed to** prison for contempt of court.
-   The police hope to encourage him to **retrieve** forgotten memories.
-   MI5 maintains a large **registry** of files on individuals and organizations.
-   He stopped to **browse around** a seconde-hand bookshop.
-   It was impossible to force a smile, to **simulate** pleasure.
-   I'm dying for a cup of **java**.

</details>
