---
title: "vscode latexshop 插件配置问题"
categories:
tags:
---
```
"name": "xelatex",

"command": "xelatex", //添加编译的参数

"args": [

"-synctex=1",

"-interaction=nonstopmode",

"-file-line-error",

"-output-directory=%OUTDIR%",

"%DOCFILE%",

]
```

注意只能是这种形式

- `-output-directory=xxx`，其他的参数不可(`-outDir=xxx`不可)
- 指定文件夹和文件必须跟在最后
