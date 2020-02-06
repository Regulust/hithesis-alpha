# hithesis-alpha
# 哈尔滨工业大学LaTeX论文模板(添加开题/中期报告样式)


[TOC]

---


[hithesis-alpha](https://github.com/regulust/hithesis-alpha) 是在原 [hithesis](https://github.com/dustincys/hithesis) (~~v2.0.6 2018/12/05~~ v2.0.11 2019/01/09) 基础上进行的改编尝试，添加了开题/中期样式。添加过程不影响原有的关于毕业论文的设置与功能。

目前对研究生开题/中期样式支持较好，而本科生开题/中期报告存在部分问题，详见下文问题说明。

本项目继承原[hithesis](https://github.com/dustincys/hithesis) CC协议及[LaTeX Project Public License](https://www.latex-project.org/lppl/)。<br />由[hithesis-alpha](https://github.com/Regulust/hithesis-alpha) 采用 <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">知识共享署名-非商业性使用 4.0 国际许可协议</a>进行许可。
<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/80x15.png" /></a>

***Happy LaTeXing!***
*Notice: 如果只是用作毕业论文用途，推荐使用原版[hithesis](https://github.com/dustincys/hithesis)，最新版本更新了关于版芯等设置。*
## 更新记录

**update:**
*v2.0.11.0a 20200205*
- code更新到hithesis v2.0.11版本(主要添加library项控制右翻页等)；
- 修改了本科开题/中期封面code风格，参fu考zhi自[hithesis-beta](https://github.com/specialpointcentral/hithesis-beta)，按[教务处](http://jwc.hit.edu.cn/2566/list.htm)要求，移去班号项目，第二行标题改为居中（但\lishu问题依然没有解决，详见[issue](https://github.com/Regulust/hithesis-alpha/issues/1)；
- 更新研究生开题/中期封面code，使自动生成的封面与[研究生院样例](http://hitgs.hit.edu.cn/e0/b2/c3359a123058/page.psp)更加接近，但具体页面参数数值未精确校准。

*封面方面依然推荐尝试“变通方法”；*
*威海校区的童鞋可以参考使用[hithesis-beta](https://github.com/specialpointcentral/hithesis-beta)～*

**update:**
*v2.0.6.2a 20191212*
- 改动位置注释修改为 *_modified by hithesis-alpha*
- 修复在 noheader=true,stage=bachelor 时，页码与原hithesis项目设置(bsfrontpagenumberline、bsmainpagenumberline项)不一致的问题（调整了\fancyfoot的位置）；
- \documentclass中新增页眉设置 headersetting选项（合并原noheader选项）：
删除该项default默认自动显示页眉；
`headersetting=noheader`：全局“没有页眉”，某些老师可能要求开题、中期报告没有页眉，若在bachelor下使用，优先级高于bsheadrule；
`headersetting=customizeheader`：自定义页眉文字，在文件开头填写自定义文字\newcommand{\customheader}{自定义页眉}，该功能结合下文中的“变通方法”，hithesis-alpha可灵活用于综合考评、实验报告等许多其它场景。

**update:**
*v2.0.6.1a 20181221*
- 修改调整图表编号设置
添加判断，在开题/中期时，使图表编号为 section-1 的格式，而非 chapter-1，因为开题/中期报告没有chapter章这一层级

**Original:**
*V2.0.6a 20181219*
版本号命名方式：前三位为hithesis版本号，a表示alpha，若有第4位表示hithesis-alpha迭代。

## 使用说明
*推荐前往[hithesis](https://github.com/dustincys/hithesis)先阅读原说明或者在终端执行```texdoc hithesis```阅读原说明文档(需已安装TeXLive2017及更新版本)。*
- 基本使用方法与原来hithesis一致
先执行```latex hithesis.ins```(macOS/Linux) ```lualatex hithesis.ins```(Windows，未测试)，然后在主文档中正常选择学位类型 ```type=doctor/master/bachelor```
- 选择```stage=kaiti,zhongqi```
如需使用开题/中期报告时选填(需放在type项前)，去掉该项缺省为false，即为原来hithesisd的本硕博毕业论文格式(切换原模板时若makecover报错，请注意在main.tex中切换封面文件 -> \input{front/cover})。
- ~~选择```noheader=true```,
添加全局“没有页眉”选项，某些老师可能要求开题、中期报告没有页眉，去掉该项缺省为false，页眉正常显示，如果在bachelor下使用，优先级高于bsheadrule。~~ **v2.0.6.2a 已经合并入headersetting选项**

## 修改说明
### 选项
- 添加选项 ```stage=kaiti,zhongqi```
使用开题/中期报告时选填(需放在type项前)，去掉该项缺省为false，即为原来hithesis的本硕博毕业论文格式。
- ~~添加选项~~  ```noheader=true,false```
 ~~添加全局“没有页眉”选项，某些老师可能要求开题、中期报告没有页眉，去掉该项缺省为false，页眉正常显示，如果在bachelor下使用，优先级高于bsheadrule~~。   **v2.0.6.2a 已经合并入headersetting选项(`headersetting=noheader/customizeheader`)**
- 新建插入自定义宏包/命令文档custom_definition
有些专业需用到特殊的宏包，以及自己码文时自定义一些方便的快捷命令，可以统一放在./front/custom_definition.tex中

### 样式code
主要修改添加 hithesis.dtx 文件的部分代码，变动优先考虑不影响原hithesis的功能及样式。
- 添加hit@stage项，用于区分kaiti、zhongqi
- 添加noheader项，用于手动去掉页眉
- \fancypagestyle{hit@headings}添加开题/中期的显示设置
- 添加stageheader、stagestatus等字段定义，用于添加字符“开题/中期报告”字符
- 新定义开题/中期报告封面样式\hit@report@titlepage
- 分别添加 研究生/本科生 开题/中期报告封面
代码参考自[PlutoThesisProposal](https://github.com/dustincys/PlutoThesisProposal)，膜拜Dustincys大神。
- 修改section编号样式
开题/中期报告只有最高section层级，没有chapter层级，默认如果直接不写chapter 则section标号为"0.1".，所以重新定义了section编号样式，选择开题/中期时自动更改。
- 在文献环境{thebibliography}处添加开题/中期判断
在使用开题/中期报告模式下，若需要参考文献，将参考文献部分改为为带标号的section层级，但需要将参考文献```\bibliography{reference}```添加到body文档中，并注释掉主文档的该行，否则会另起新页。

\* *修改、添加的位置暂时以 "_added by t"注明，原本方便自己查找纠错，暂未更新到原hithesis的注释样式。-> v2.0.6.2a 改为"_modified by hithesis-alpha"*


## 问题及变通
### 存在的bug问题
- **本科生开题/中期的封面与学校样例存在差别**
开题报告等字符/行间距不符合；封面底部“哈尔滨工业大学教务处”未能更改隶书字体(这里我也没搞明白，理论上原来已经定义了\lishu命令，但使用无效)。*【关于\lishu 讨论见[issue](https://github.com/Regulust/hithesis-alpha/issues/1)】*
- **“题目”行居中方式与学校样例存在差别**
目前和标准模板还有些许区别，“题目”两个字与题目的内容是一同居中的，而研究生院、教务处模板可能是题目两个字位置固定，题目内容文字单独居中。
- **开题/中期报告封面部分代码风格老旧**
因为封面是由[PlutoThesisProposal](https://github.com/dustincys/PlutoThesisProposal) 项目中修改而来，代码风格仍是PlutoThesis时代，本人水平、精力有限，只能修改到让其运行起来，暂无力优化。*【Notice:2.0.11.0a 已更新】*

### 变通方法
- 目前bug问题主要存在于报告的封面页，如果自动生成封面无法满足需要，可以采用变通方法
首先，自行下载并填写学校word模板封面页，然后生成pdf文件，放入front文件夹，命名为report_cover.pdf，使用
```\includepdfmerge{front/report_cover.pdf}	``` 命令手动插入该pdf封面，并注释掉下面```\input{front/reportcover}```  及 ```\makecover``` 两行。

*\* 该变通方法可灵活适用于综合考评、实验报告等其它报告场景。*

附：

[窝工博士生培养过程相关文件/模板下载](http://hitgs.hit.edu.cn/e0/a8/c3416a123048/page.psp)

[窝工硕士生培养过程相关文件/模板下载](http://hitgs.hit.edu.cn/e0/b2/c3359a123058/page.psp)

[窝工本科毕业设计相关文件/模板下载](http://jwc.hit.edu.cn/2566/list.htm)

## 致谢及声明
首先感谢Dustincys大神编写的[Hithesis](https://github.com/dustincys/hithesis)模板及[PlutoThesisProposal](https://github.com/dustincys/PlutoThesisProposal)模板，膜拜。

本人也是才疏学浅，对LaTex的了解也是“一知半解”，只是自己用到，一时兴起，想着分享出来。该项目的首要原则为不影响原hithesis功能和显示，所以更改添加的代码冗杂不美观。暂时只是为满足自己使用需要，无精力进行完整测试及进一步优化。有交流需要请加入 hithesis 交流QQ群：259959600，大神超多。

再次对[Dustincys](https://github.com/dustincys)等窝工LaTeX各路大神表示感谢。

## 样式示例

![本科毕业设计中期封面](https://res.cloudinary.com/regulus/image/upload/c_scale,q_99,w_600/v1545221844/Github/templete_bachelor_zhongqi_0.jpg)

*本科毕业设计中期封面*

![本科毕业设计中期目录页](https://res.cloudinary.com/regulus/image/upload/c_scale,q_99,w_600/v1545221846/Github/templete_bachelor_zhongqi_1.jpg)

*本科毕业设计中期目录页*

![本科毕业设计中期封面内容页](https://res.cloudinary.com/regulus/image/upload/c_scale,q_99,w_600/v1545402059/Github/templete_bachelor_zhongqi_2.jpg)

*本科毕业设计中期内容页*

![硕士开题封面](https://res.cloudinary.com/regulus/image/upload/c_scale,q_99,w_600/v1545221838/Github/templete_master_kaiti_0.jpg)

*硕士开题封面*

![硕士开题目录页](https://res.cloudinary.com/regulus/image/upload/c_scale,q_99,w_600/v1545221847/Github/templete_master_kaiti_1.jpg)

*硕士开题目录页*

![硕士开题封面内容页](https://res.cloudinary.com/regulus/image/upload/c_scale,q_99,w_600/v1545402067/Github/templete_master_kaiti_2.jpg)

*硕士开题封面内容页*

---
 ***hithesis原说明文档 请查看 [README_hithesis.md](https://github.com/dustincys/hithesis) 。***

 >用的开心的小伙伴，可以考虑扫个红包码支持一下啊[打开支付宝首页搜“557241165”领红包]，嘻嘻嘻～
