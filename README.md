# Fishreadyes README（中文说明书，followed by English version manual）

卷累了，放松一下！全功能隐藏型阅读插件，提供 自动翻页，多级目录，书签，书内查找（支持正则），回退/前进，当前进度自动保存，跳页，等等多种阅读功能。

## Author
yctest9296

## 简单示例（后面的内容不看也没事）
- 启动/退出插件：安装插件后，会在最下方状态栏（status bar）上显示一个`播放按钮`（点击后会变成`暂停按钮`），点击后启动插件。点击第二下退出插件。

    *p.s. 启动后插件会自动打开预置模板代码`example_copy.js`（可更改，见[后文更换模板说明](#template)），并自动将光标定位在第22行（可更改，见[后文"{1}"`书籍内容刷新标志位`说明](#loc)），书籍（预置书籍为`xiyouji.txt`）的当前行的内容也会显示在此处。*

- 快捷键

    | 快捷键 | 功能 | 何时生效 |
    |:---:|:---:|:---:|
    |ctrl+,       |启动/退出插件             |-        |
    |ctrl+f       |书内查找          | 启动插件后         |
    |上/下键       |翻页          |启动插件后         |
    |ctrl+左/右键       |回退/前进          |启动插件后         |

    用户可以在`File-Preference-Keyboard Shortcuts`中更改/禁用上述按键绑定，也可以为其它命令，比如自动翻页、打开目录等功能绑定快捷键。

## 预览图
- 自动翻页功能预览图
    ![自动翻页功能预览图](https://github.com/yctest9296/Fishreadyes/blob/main/images/autoPaging.gif?raw=true)

## 控制功能 - 新增
- 设置临时`书籍内容刷新标志位`(`命令 Fishreadyes: Set TMP Identifier`)：为了更灵活的阅读，在`启动插件`期间（即，在启动插件之后），用户可在任意代码文件（不限制在[临时代码文件](#tmpfile)内）、任意位置设置临时`书籍内容刷新标志位`。
    - 操作步骤：
        - 在插件设置(`Preferences: Open User Settings`-`Fishreadyes: Child Lock`)中，去除童锁的勾选（默认童锁是勾选，即启用状态）。
        - 点击`播放按钮`启动插件时，仍会默认定位至`{1}`标志位刷新书籍内容。在这之后，将光标移至想要刷新书籍内容的位置，使用`ctrl+shift+p`打开命令面板，输入命令`Fishreadyes: Set TMP Identifier`以设置临时`书籍内容刷新标志位`。之后，插件就可以识别、并在此标志位的位置显示书籍内容。
        - 点击`暂停按钮`退出插件，显示的书籍内容自动隐藏。
    - 注：默认童锁是启用状态。因为每次书籍内容更新会修改当前文件内容，所以为了防止用户误用此功能修改了自己的重要代码（其实问题不大，即使修改了，undo一下不就没事了？）。


## 控制功能
- 启动/退出插件(`命令 Fishreadyes: Run Or Stop`)：安装插件后，会在最下方状态栏（status bar）上显示一个`播放按钮`（点击后会变成`暂停按钮`），点击后启动插件。点击第二下退出插件。
    - 启动插件后发生的事件：
        - 一些默认的按键绑定会更改（见[下文按键绑定更改说明](#keybind)）。
        - 状态栏（status bar）会显示阅读工具按钮，比如翻页、目录、书内查找等等。
        - 根据模板代码文件生成`临时代码文件`<a id="tmpfile"></a>（在tmp文件夹下，*随意修改/删除也没事*），插件自动将光标定位在用户指定位置(即`{1}`标志位，见[后文"{1}"`书籍内容刷新标志位`说明](#loc))、并在此处显示书籍内容。
        - 默认打开的是上次阅读的书籍，且阅读信息包括书签和进度也会保持上次阅读的状态。
    - 退出插件后发生的事件：
        - 按键绑定会自动解绑。
        - 状态栏（status bar）阅读工具按钮自动隐藏。
        - 显示的书籍内容自动隐藏。
- `用户书籍目录`<a id="bookpath"></a>：使用`命令 Fishreadyes: Copy Book Path`复制书籍目录地址，或使用`命令 Fishreadyes: Open Book Path`打开书籍目录，在此目录添加用户书籍。p.s. 也可以直接去打开，很好找，比如在windows中，这个目录一般是`C:\Users\用户名\.vscode\extensions\yctest9296.fishreadyes-版本号\doc`
- 更换模板代码文件流程(`命令 Fishreadyes: Create Template`)<a id="template"></a>
    1. 先打开任意用户代码文件(假设用户想要将此代码文件作为模板)。
    2. 使用`ctrl+shift+p`打开命令面板，输入命令`Fishreadyes: Create Template`以生成模板文件。
    3. 生成模板文件成功后，会在右下角弹出提示框`Create completed! Pls add identifier "{1}" manually in this template!`。
    4. 点击提示框中`Open and edit`按钮，会自动打开模板文件，用户在任意位置(建议选注释行)手动增加`{1}`这个`书籍内容刷新标志位`<a id="loc"></a>。之后，插件就可以识别、并在此标志位的位置显示书籍内容。
- 重置当前书籍(`命令 Fishreadyes: Soft Reset Current Book`)：如果阅读时出现异常情况，用户可以尝试此命令，重置并清空当前书籍的阅读状态。
- `按键绑定`：<a id="keybind"></a>
	- 安装插件后，`ctrl+,`绑定为`启动/退出插件`。
	- 启动插件后，
		- `ctrl+f`绑定为`书内查找`，
		- `上/下键`绑定为`翻页`，
		- `ctrl+左/右键`绑定为`回退/前进`。
	- 退出插件后，插件会自动解绑上述按键、恢复原功能。
	- 用户可以在`File-Preference-Keyboard Shortcuts`中更改/禁用上述按键绑定，也可以为其它命令，比如自动翻页、打开目录等功能绑定快捷键。


## 阅读功能（阅读工具按钮）
- 翻页
    - 按钮位于状态栏左侧。或使用`上/下键`快捷键。
    - 插件规定每翻一页为刷新、显示书籍内容的一行（一行50个字符）。
- 自动翻页
    - 按钮位于状态栏左侧。
    - 在插件设置(`Preferences: Open User Settings`-`Fishreadyes: Auto Paging`)中，可以设置自动翻页的间隔时间，单位是毫秒。默认是1000ms，即1秒翻页一次。
- 自定义多级目录
    - 按钮位于状态栏左侧。
    - 目录打开后会自动将光标定位至当前章节。
    - 默认的设置有两级目录，用于解析预置书籍（即`xiyouji.txt`）。
    - 目录解析时，支持用户的自定义正则表达式或字符串：
        - 在插件设置(`Preferences: Open User Settings`-`Fishreadyes: Chapter Split`)中，用户可自己添加多级目录，不限制目录级数。
        - 用户想恢复默认设置可以点击当前设置左侧的`齿轮按钮`-`Reset Setting`。
        - 提示：用户如果需要增加对多本书籍的目录解析，可以使用正则表达式的常见用法，比如在正则表达式中这么写：`/(解析书籍1目录的正则|解析书籍2目录的正则|等等)/`。
- 书签
    - 按钮位于状态栏左侧。
    - 支持添加/批量删除书签。
- 书内查找（支持正则）
    - 按钮位于状态栏左侧。或使用`ctrl+f`快捷键。
    - 用于在书内全文查找搜索，最多查找的内容为50个字符(也就是显示的一行的最大长度)。比如，正则`/.{0,50}/`返回的搜索结果为书籍每一行，而`/.{51}/`超出50字符的限制就返回搜索内容为空。
    - 支持跨一行搜索。
    - 搜索的结果列表中，优先定位在离当前阅读位置最近的结果。
    - 提示一下，返回搜索结果列表的最上方也有一个输入框(在这个输入框的placeholder中，我标记了`Optional: input to screen result`)，这个输入框是vscode默认功能，在此输入框输入内容默认为筛选当前搜索结果。
- 回退/前进
    - 按钮位于状态栏左侧。或使用`ctrl+左/右键`快捷键。
    - 插件会自动记录页码历史，比如用户从当前页5跳到页10，按`回退按钮`则会回退到页5，再按`前进按钮`则会前进到页10。
    - 最多保存100个页码历史。
- 当前进度
    - 按钮位于状态栏右侧。
    - 显示为`当前页码/总页码`。
    - 点击则触发`跳页`功能。
- 打开书籍
    - 按钮位于状态栏右侧。
    - 用于选择用户书籍。可在[上文提到的用户书籍目录](#bookpath))中添加或删除用户书籍。
- 当前阅读书名
    - 悬停在`打开书籍按钮`，会显示当前阅读书名。
- 跳页
    - 点击`当前进度按钮`，在输入框输入目标页码，按回车键确认跳转。
- 阅读状态信息
    - 阅读状态信息包括当前书名、阅读进度，和书签。
    - 每次页码变化或书签更新，插件会自动保存当前的阅读状态信息。

## 已知问题
- 修改当前阅读中使用的[临时代码文件](#tmpfile)(一般也不会有人修改。p.s. 修改或删除都没事)，有可能会让书籍内容显示异常。解决方法：关闭[临时代码文件](#tmpfile)，并点击`播放按钮`两次（即退出再启动插件）即可自动恢复。
- 如果用户使用python脚本作为模板代码，有时会有`1 file to analysis`的提示出现在状态栏（status bar）左侧，影响用户体验（其实也还好）。可能是因为python的pylance插件检查到了代码变动并花费一定时间分析（推测和用户模板代码长度或电脑性能相关）。解决方法：用户阅读时可以手动将pylance暂时禁用。

## 本插件仅供学习参考


---


# Fishreadyes README（English version manual）
Take a break and have a read! All-in-One "Slacking" Reading Extension. This comprehensive reading extension offers a wide array of functionalities tailored for an enjoyable reading experience, including auto-paging, multi-level directories, bookmarks, in-book search (with regex support), back/forward navigation, automatic saving of current progress, jumping to specific pages, and much more.

## Author
yctest9296

## Quick Start

- **Start/Stop Function**: After installing, a `Play Button` (that turns into a `Pause Button` upon click) appears on the bottom status bar. Click it to start the extension and click again to stop.

    *p.s. Upon starting, the extension automatically opens the predefined template code `example_copy.js` (modifiable, see [Template Replacement Instructions](#template_en)) and positions the cursor at line 22 (modifiable, see ["{1}" Book Content Refresh Placeholder](#loc_en)). The content of the current line of the book (default is `xiyouji.txt`) will also be displayed here.*

## Preview
- Auto-Paging Function Preview
    ![Auto-Paging Function Preview](https://github.com/yctest9296/Fishreadyes/blob/main/images/autoPaging.gif?raw=true)

- Keybindings

    | Keybindings | Function | When functional |
    |:---:|:---:|:---:|
    |ctrl+,       |Start/stop extension             |-        |
    |ctrl+f       |In-book search          | After extension started         |
    |up/down       |Flip Pages          |After extension started         |
    |ctrl+left/right       |Go back/forward          |After extension started         |

    Users can modify/disable these bindings or assign new shortcuts to functions, like auto paging and open directory in `File-Preference-Keyboard Shortcuts`.

## Control Functions - New added

- **Set Temporary Book Content Refresh Placeholder (`Command: Fishreadyes: Set TMP Identifier`)**: For more flexible reading, during the extension's active state, users can set a temporary book content refresh placeholder in any code file, at any location.
    - **Steps**:
        - Disable the Child Lock in extension settings (`Preferences: Open User Settings` - `Fishreadyes: Child Lock`).
        - Start the extension. It will default to the `{1}` placeholder for content refresh. Move the cursor to the desired location, open the Command Palette with `ctrl+shift+p`, and input `Fishreadyes: Set TMP Identifier` to set the temporary placeholder. The extension will then display book content at this new location.
        - Stop the extension to hide displayed content.
    - **Note**: Child Lock is enabled by default to prevent accidental modifications to important user code.


## Control Functions

- **Start/Stop Function (`Command: Fishreadyes: Run Or Stop`)**: After installation, a `Play Button` appears on the status bar. Click to start the extension and click again to stop.
    - **After Starting**:
        - Default keybindings are altered (see [Keybind Changes](#keybind_en)).
        - Reading tool buttons appear on the status bar, such as for flipping pages, accessing directories, and searching within the book.
        - A `Temporary Code File` <a id="tmpfile_en"></a> (in the tmp folder, *safe to modify/delete*) is generated based on the template code file. The extension automatically positions the cursor at the `{1}` placeholder (see ["{1}" Book Content Refresh Placeholder](#loc_en)) and displays the book content there.
        - The last read book is opened by default, with bookmarks and progress preserved.
    - **After Stopping**:
        - Keybindings are automatically unbound.
        - Reading tool buttons on the status bar hide.
        - Displayed book content disappears.

- **User Book Directory** <a id="bookpath_en"></a>: Use `Command: Fishreadyes: Copy Book Path` to copy the book directory path, or `Command: Fishreadyes: Open Book Path` to open it and add user books. Alternatively, navigate to the directory directly (e.g., in Windows, it's typically `C:\Users\Username\.vscode\extensions\yctest9296.fishreadyes-version\doc`).

- **Replace Template Code File (`Command: Fishreadyes: Create Template`)** <a id="template_en"></a>
    1. Open any user code file (intended to be used as a template).
    2. Use `ctrl+shift+p` to open the Command Palette, input `Fishreadyes: Create Template` to generate the template file.
    3. After successful generation, a prompt appears in the bottom-right corner, instructing to add `{1}` manually as the book content refresh placeholder in the template.
    4. Click `Open and edit` to automatically open the template file. Manually add `{1}` at any location (preferably a comment line)<a id="loc_en"></a>. The extension will then recognize and display book content at this placeholder.

- **Reset Current Book (`Command: Fishreadyes: Soft Reset Current Book`)**: In case of reading issues, use this command to reset and clear the current book's reading state.

- **Keybindings** <a id="keybind_en"></a>
    - After installation, `ctrl+,` is bound to `Start/Stop Extension`.
    - When the extension is active:
        - `ctrl+f` is bound to `Search Within Book`,
        - `Up/Down Arrows` are bound to `Flip Pages`,
        - `ctrl+Left/Right Arrows` are bound to `Back/Forward Navigation`.
    - Upon stopping the extension, bindings are automatically unbound, restoring original functions.
    - Users can modify/disable these bindings or assign new shortcuts in `File-Preference-Keyboard Shortcuts`.



## Reading Functions (Reading Tool Buttons displayed in bottom status bar)

- **Flip Pages**: Located on the left side of the status bar or use `Up/Down Arrows`. Each page flip displays one line of book content (50 characters per line).

- **Auto-Paging**: Located on the left side of the status bar. Set the interval in milliseconds in extension settings (`Preferences: Open User Settings` - `Fishreadyes: Auto Paging`). Default is 1000ms (1 second).

- **Custom Multi-Level Directories**: 
    - The button is located on the left side of the status bar.
    - When the directory is opened, the cursor will automatically be positioned to the current chapter.
    - The default setting includes a two-level directory for parsing pre-installed books (e.g., `xiyouji.txt`).
    - During directory parsing, custom regular expressions or strings are supported for users:
        - In the plugin settings (`Preferences: Open User Settings` -> `Fishreadyes: Chapter Split`), users can add multi-level directories themselves without any limitation on the number of levels.
        - If users want to restore the default settings, they can click the `Gear Button` on the left side of the current settings and select `Reset Setting`.
        - Tip: If users need to add directory parsing for multiple books, they can utilize common practices of regular expressions, for example, writing something like this in the regular expression: `/(regular expression for parsing book 1's directory|regular expression for parsing book 2's directory|etc.)/`.

- **Bookmarks**: Located on the left side of the status bar. Supports adding/batch deleting bookmarks.

- **In-Book Search (with Regex)**:
    - The button is located on the left side of the status bar, or you can use the `Ctrl+F` shortcut key.
    - Perform a search within the whole book, with a maximum search content limit of 50 characters (which is the maximum length of a displayed line). For example, the regex `/.{0,50}/` will return search results for every line of the book, whereas `/.{51}/` exceeds the 50-character limit and will return an empty search result.
    - Cross-line search is supported.
    - In the search results list, priority is given to locating the result closest to the current reading position.
    - As a reminder, there is also an input box at the top of the search results list (I have labeled the placeholder as `Optional: input to screen result`), which is a default feature of VS Code. Entering content in this input box will by default filter the current search results.

- **Back/Forward Navigation**: Located on the left side of the status bar or use `ctrl+Left/Right Arrows`. Automatically saves up to 100 page history entries.

- **Current Progress**: Located on the right side of the status bar. Displays `Current Page/Total Pages` and triggers the jump-to-page function upon click.

- **Open Book**: Located on the right side of the status bar. Selects user books. Can add/remove books from the [User Book Directory](#bookpath_en).

- **Current Book Title**: Hover over the `Open Book` button to display.

- **Jump to Page**: Click the `Current Progress` button, input the target page number, and press Enter to jump.

- **Reading State Information**: Includes current book title, reading progress, and bookmarks. Automatically saved upon page changes or bookmark updates.

## Known Issues

- Modifying the [Temporary Code File](#tmpfile_en) during reading (unlikely) may cause display issues. Solution: Close the file, click the `Play Button` twice (stop and then start the extension) to restore.
- Using Python scripts as template code may sometimes display "1 file to analysis" in the status bar, affecting the user experience (minor). This may be due to the pylance extension analyzing code changes. Solution: Temporarily disable pylance during reading.

## This extension is only for study reference