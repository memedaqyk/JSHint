## 引言
SublieText3本身没有很完备的错误检查机制，写JavaScript难免经常犯错误，而浏览器运行报错后再来修改又较为麻烦，所以推荐使用一个错误检查工具。在这是：SHint与JSHint Gutter。
> 注意：除Sublime之外，JSHint也支持其他很多编辑器与IDE，相关插件请查看 http://www.jshint.com/install/。

## 比较
JS的错误检查工具有很多如：JSLint，JSHint和ESLint...

----

1.JSLint
**优点**
- 配置是老道已经定好的，开箱即用。
**不足**
- 有限的配置选项，很多规则不能禁用
- 规范严格，凡是不符合老道所认为的好的风格的，都会有警告(这一项就看你是否完全认同老道了)
- 扩展性差
- 无法根据错误定位到对应的规则

----

2.JSHint
**优点**
- 有了很多参数可以配置
- 支持配置文件，方便使用
- 支持了一些常用类库
- 支持了基本的ES6
**不足**
- 不支持自定义规则
- 无法根据错误定位到对应的规则

----

3.ESLint
**优点**
- 默认规则里面包含了JSLint和JSHint的规则，易于迁移
- 可配置为警告和错误两个等级，或者直接禁用掉
- 支持插件扩展
- 可以自定义规则
- 可以根据错误定位到对应的规则
- 支持ES6
- 唯一一个支持JSX的工具
**不足**
- 需要进行一些自定义配置(因为太灵活了嘛，不过文档是很详细的)
- 慢 (它比其他两个都要慢)

----

## 安装JSHint
请先安装好NodeJS，然后在终端命令行中输入:
```nodejs
npm install -g jshint
```
> 注意：如果你是Windows用户，可以安装Git for windows，其附带的Git Bash可以运行大多数的linux命令。

## 安装与配置JSHint Gutter
JSHint Gutter安装非常简单，使用Sublime命令面板的PackageControl:Install Package，搜索安装即可.(不会的自己百度或Google)
安装完成后，在Sublime的Package Settings里找到JSHint Gutter，选择Set Plugin Options：
<img src="http://ojlmcfp94.bkt.clouddn.com/JSHint.png" alt="aa">
设置NodeJS执行文件所在的路径（node_path），并将lint_on_save（文件保存时检查）选项打开:
```json
"osx": "/usr/local/bin/node”,
"lint_on_load": true,
```
## 设置.jshintrc
在项目根目录或用户目录下新建一个文件：.jshintrc（windows用户应该在文件管理器里面创建.jshintrc.文件，然后它会自动改名为.jshintrc），在此文件里填写你的检查规则，以下是一个典型的.jshintrc：     
```json
{
  "curly": true,
  "eqeqeq": true,
  "immed": true,
  "noarg": true,
  "noempty": true,
  "quotmark": "single",
  "undef": true,
  "unused": true,
  "node": true
}
```

- 第二行：curly 表示所有的代码块必须使用大括号
- 第三行：eqeqeq 表示判断相等时，必须使用 ===
- 第四行：immed 表示立即执行函数必须用括号包起来 `(function () { } ());`
- 第五行：noarg 表示禁止使用 `arguments.caller` 和 `arguments.callee`
- 第六行：noempty 表示禁止出现空的代码块 `{ }`
- 第七行：quotmark 是引号的使用规则，有以下四个选项
 - false : 不检查
 - true : 检查一致性（要么都是单引号，要么都是双引号）
 - single : 必须都是单引号
 - double : 必须都是双引号
- 第八行：undef 表示所有的局部变量都必须先声明再使用
- 第九行：unused 表示禁止变量已经声明，但却不使用
- 第十行：node 表明你的项目是NodeJS项目，require等node特有的全局函数将通过检查

以上只是少数常见的配置项目，请到官网查看完整项目列表：[JSHint Options](http://www.jshint.com/docs/options/)
具体.jshintrc配置见github下的文件.jshintrc。
