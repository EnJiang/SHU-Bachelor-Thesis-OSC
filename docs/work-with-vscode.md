# Work with VSCode

## 1. 安装扩展与编译

在左侧扩展栏 (Extensions) 搜索 `James-Yu.latex-workshop`, 点击安装扩展 `LaTeX Workshop`:

```
┌─────────────────────────────────────────────── - □ x ┐
│ X| File Edit Selection View ...                      │
├───┬──────────────────────────────────────────────────┤
│ ◨ │ <-- Explorer                                     │
├───┤                                                  │
│...│                                                  │
├───┤                                                  │
│▢ ▢│ <-- Extentions (Four squares)                    │
│▢▢ │                                                  │
├───┤                                                  │
│...│                                                  │
├───┤                                                  │
│   │                                                  │
└───┴──────────────────────────────────────────────────┘
```

在项目根目录下创建目录 `.vscode`, 在 `.vscode` 中添加文件 `settings.json`; 添加完成后你的项目目录应该类似:

```
SHU-BACHELOR-THESIS-OSC
├── .vscode/
│   └── settings.json
├── ...
├── main.tex
└── ...
```

在 settings.json 中写入以下内容:

```json
{
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-output-directory=build",
                "main"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "./build/main"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "xelatex",
            "tools": [
                "xelatex"
            ],
        },
        {
            "name": "xe->bib->xe->xe",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
    ],
    "latex-workshop.latex.autoBuild.run": "never",
    "workbench.editorAssociations": {
        "*.pdf": "latex-workshop-pdf-hook"
    },
    "latex-workshop.message.error.show": true,
    "latex-workshop.message.warning.show": false,
    "latex-workshop.view.pdf.viewer": "tab",
    "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click",
    "latex-workshop.latex.outDir": "build",
}
```

打开根目录下的 [main.tex](../main.tex), 点击左侧栏的 TEX 按钮:

```
┌─────────────────────────────────────────────── - □ x ┐
│ X| File Edit Selection View ...                      │
├───┬──────────────────────────────────────────────────┤
│ ◨ │ <-- Explorer                                     │
├───┤                                                  │
│...│                                                  │
├───┤                                                  │
│...│                                                  │
├───┤                                                  │
│TEX│ <-- LaTex                                        │
├───┤                                                  │
│   │                                                  │
└───┴──────────────────────────────────────────────────┘
```

在打开的 LATEX 窗口中, 点击展开 `COMMANDS` 栏下的 `Build LaTeX project` 选项, 选择 `Recipe: xelatex` 或者 `Recipe: xe->bib->xe->xe` 进行编译.

## 2. 预览与双向搜索

打开 `main.tex`, 利用脚本或者扩展编译 Latex 文件, 成功后点击右上角的 `Open Preview to the Slide` (是一本书 📖 上面加个放大镜 🔍 的按钮) 进行预览.

```
┌─────────────────────────────────────────────── - □ x ┐
│ X| File Edit Selection View ...                      │
├───┬──────────────────────────────────────────────────┤
│   │ main.tex | README.md |                  □ ◨ □ ...│
├───┼──────────────────────────────────────────────────┤
│...│                                           ↑      │
├───┤                               Open Preview to    │
│...│                                     the Slide    │
├───┤                                                  │
│TEX│                                                  │
├───┤                                                  │
│   │                                                  │
└───┴──────────────────────────────────────────────────┘
```

- 双击 pdf 中的文字能搜索到对应 latex 文件中的源码.

- 点击 tex 源文件中的某一行 (光标需要处于这一行中), 按下组合键 `Ctrl` + `Alt` + `j` 即可跳转到 pdf 中对应部分.
