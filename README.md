# hithesis-alpha
# 哈尔滨工业大学LaTeX论文模板(添加开题/中期报告样式) 

*V2.0.6a 20181219*

[hithesis-alpha](https://github.com/regulust/hithesis-alpha) 是在原 [hithesis](https://github.com/dustincys/hithesis) (v2.0.6 - 20181205) 基础上进行的尝试，添加了开题/中期样式。添加过程不影响原有的关于毕业论文的设置与功能。

目前对研究生开题/中期样式支持较好，而本科生开题/中期报告存在部分问题，详见下文问题说明。

本项目继承原[hithesis](https://github.com/dustincys/hithesis) CC协议及[LaTeX Project Public License](https://en.wikipedia.org/wiki/LaTeX_Project_Public_License)。

<a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/"><img alt="知识共享许可协议" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/4.0/80x15.png" /></a><br />由[hithesis-alpha](https://github.com/Regulust/hithesis-alpha) 采用 <a rel="license" href="http://creativecommons.org/licenses/by-nc/4.0/">知识共享署名-非商业性使用 4.0 国际许可协议</a>进行许可。

## 样式
![本科毕业设计中期封面](https://res.cloudinary.com/regulus/image/upload/v1545221844/Github/templete_bachelor_zhongqi_0.jpg)
![本科毕业设计中期目录页](https://res.cloudinary.com/regulus/image/upload/v1545221846/Github/templete_bachelor_zhongqi_1.jpg)
![本科毕业设计中期封面内容页](https://res.cloudinary.com/regulus/image/upload/v1545221849/Github/templete_bachelor_zhongqi_2.jpg)
![硕士开题封面](https://res.cloudinary.com/regulus/image/upload/v1545221838/Github/templete_master_kaiti_0.jpg)
![硕士开题目录页](https://res.cloudinary.com/regulus/image/upload/v1545221847/Github/templete_master_kaiti_1.jpg)
![硕士开题封面内容页](https://res.cloudinary.com/regulus/image/upload/v1545221849/Github/templete_master_kaiti_2.jpg)

## 使用说明
- 首先基本使用方法与原来hithesis一致
先执行```latex hithesis.ins```(macOS/Linux) ```lualatex hithesis.ins```(Windows，未测试)，然后在主文档中正常选择学位类型 ```type=doctor/master/bachelor```
- 选择```stage=kaiti,zhongqi```
如需使用开题/中期报告时选填(需放在type项前)，去掉该项缺省为false，即为原来hithesisd的本硕博毕业论文格式。
- 选择```noheader=true```,
添加全局“没有页眉”选项，某些老师可能要求开题、中期报告没有页眉，去掉该项缺省为false，页眉正常显示，如果在bachelor下使用，优先级高于bsheadrule。

## 修改说明
#### 选项
- 添加选项 ```stage=kaiti,zhongqi```
使用开题/中期报告时选填(需放在type项前)，去掉该项缺省为false，即为原来hithesisd的本硕博毕业论文格式。
- 添加选项 ```noheader=true,false```
添加全局“没有页眉”选项，某些老师可能要求开题、中期报告没有页眉，去掉该项缺省为false，页眉正常显示，如果在bachelor下使用，优先级高于bsheadrule。
- 新建插入自定义宏包/命令文档custom_definition
有些专业需用到特殊的宏包，以及自己码文时自定义一些方便的快捷命令，可以统一放在./front/custom_definition.tex中

#### 样式code
主要修改添加 hithesis.dtx文件的部分代码。
- 添加hit@stage项，用于区分kaiti、zhongqi
- 添加noheader项，用于手动去掉页眉
- \fancypagestyle{hit@headings}添加开题/中期的显示设置
- 添加stageheader、stagestatus等字段定义，用于添加字符“开题/中期报告”字符
- 新定义开题/中期报告封面样式\hit@report@titlepage
- 分别添加 研究生/本科生 开题/中期报告封面
代码参考自[PlutoThesisProposal](https://github.com/dustincys/PlutoThesisProposal)，膜拜Dustincys大神。

\* *所有修改、添加的位置均注明了 "_added by t"，方便查找纠错。*


## 问题及变通
### 存在的bug问题
- **本科生开题/中期的封面与学校样例存在差别**
开题报告等字符/行间距不符合；封面底部“哈尔滨工业大学教务处”未能更改隶书字体(这里我也没搞明白，理论上原来已经定义了\lishu命令，但使用无效)。
- **“题目”行居中方式与学校样例存在差别**
目前和标准模板还有些许区别，“题目”两个字与题目的内容是一同居中的，而研究生院、教务处模板可能是题目两个字位置固定，题目内容文字单独居中。
- **开题/中期报告封面部分代码风格老旧**
因为封面是由[PlutoThesisProposal](https://github.com/dustincys/PlutoThesisProposal) 项目中修改而来，代码风格仍是PlutoThesis时代，本人水平、精力有限，只能修改到让其运行起来，暂无力优化。

### 变通方法
目前bug问题主要存在于封面页面，如果自动生成封面无法满足需要，可以自行下载填写学校word模板封面页面，生成pdf文件，放入front文件夹，命名为report_cover.pdf，使用```\includepdfmerge{front/report_cover.pdf}	``` 命令手动插入该pdf封面，并注释掉下面```\input{front/reportcover}```  及 ```\makecover``` 两行。
附：
[窝工博士生培养过程相关下载](http://hitgs.hit.edu.cn/e0/a8/c3416a123048/page.psp)
[窝工硕士生培养过程相关下载](http://hitgs.hit.edu.cn/e0/b2/c3359a123058/page.psp)
[窝工本科毕业设计相关下载](http://jwc.hit.edu.cn/2566/list.htm)

## 致谢及声明
首先感谢Dustincys大神编写的[Hithesis](https://github.com/dustincys/hithesis)模板及[PlutoThesisProposal](https://github.com/dustincys/PlutoThesisProposal)模板，膜拜。

本人也是才疏学浅，对LaTex的了解也是“一知半解”，只是自己用到，一时兴起，想着分享出来。暂时只为满足自己使用需要，无精力进行完整测试及进一步优化，有交流需要请加入 hithesis 交流QQ群：259959600，大神超多。

再次对[Dustincys](https://github.com/dustincys)等窝工LaTeX各路大神表示感谢。



---
 ***hithesis原说明文档 请查看 [README_hithesis.md](https://github.com/dustincys/hithesis) 。***

