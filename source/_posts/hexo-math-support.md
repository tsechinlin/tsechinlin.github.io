---
title: Hexo 支持数学公式渲染
date: 2019-11-06 21:54:12
tags: 
  - Hexo
categories: Web
---

基于 Hexo 搭建的个人博客，在默认情况下渲染数学公式无法达到预期的效果，可以通过更换 Hexo 的 markdown 渲染引擎以及修改相应配置来解决问题。
参考：[在 Hexo 中渲染 MathJax 数学公式](https://www.jianshu.com/p/7ab21c7f0674)

<!--more-->

## 问题原因

Hexo 的默认 markdown 渲染引擎为 `hexo-renderer-marked`, 该引擎会把一些特殊的 markdown 符号换为相应的 html 标签，这样会导致处理数学公式时经常将公式中的符号换为 html 标签，最终使得公式无法成功渲染。

## 解决方法

__更换 Hexo 的 markdown 渲染引擎__

将 Hexo 的 markdown 渲染引擎更换为 `hexo-renderer-kramed`。`hexo-renderer-kramed` 引擎是在默认的渲染引擎 `hexo-renderer-marked` 的基础上修改了一些 bug，两者比较接近，也比较轻量级。

```bash
npm uninstall hexo-renderer-marked --save
npm install hexo-renderer-kramed --save
```

更换之后行间公式的渲染就没问题了，但是行内公式的渲染还是有问题，需要解决语义冲突。

__解决语义冲突__

在博客根目录下，打开文件 `node_modules\kramed\lib\rules\inline.js`，修改第 11 行的 `escape` 变量定义。

```js
//escape: /^\\([\\`*{}\[\]()#$+\-.!_>])/,
  escape: /^\\([`*\[\]()#$+\-.!_>])/,
```

之后再修改第 20 行的 `em` 变量定义。

```js
//em: /^\b_((?:__|[\s\S])+?)_\b|^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
  em: /^\*((?:\*\*|[\s\S])+?)\*(?!\*)/,
```

__在主题中开启 mathjax 开关__

进入正在使用的主题目录，找到主题的 `_config.yml` 配置文件，将对 mathjax 的支持改为 `true`。

```yml
# Math Formulas Render Support
math:
  # Default (true) will load mathjax / katex script on demand.
  # That is it only render those page which has `mathjax: true` in Front-matter.
  # If you set it to false, it will load mathjax / katex srcipt EVERY PAGE.
  per_page: true

  # hexo-renderer-pandoc (or hexo-renderer-kramed) required for full MathJax support.
  mathjax:
    enable: true
    # See: https://mhchem.github.io/MathJax-mhchem/
    mhchem: false
```

__在文章开头设置支持 mathjax__

最后注意需要在有数学公式的文章中设置支持 mathjax。

```markdown
---
title: index.html
date: 2016-12-28 21:01:30
tags:
mathjax: true
---
```

通过上面的修改，文章中的数学公式就可以正常渲染了。

