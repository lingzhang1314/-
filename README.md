# 基于循环神经网络的股票价格预测系统研究

本项目致力于构建基于循环神经网络的股票价格预测系统，深入探究LSTM与CNN + LSTM模型在股票价格预测中的适用性及参数优化。

### 数据处理
收集沪深300指数高频数据，涵盖开盘价、收盘价、成交量等6项关键特征。对数据进行缺失值填充、min - max标准化处理，并合理划分数据集，确保数据质量与可用性。数据集预览如下：
<html xmlns:v="urn:schemas-microsoft-com:vml" xmlns:o="urn:schemas-microsoft-com:office:office" xmlns:x="urn:schemas-microsoft-com:office:excel" xmlns="http://www.w3.org/TR/REC-html40">
<head>

<meta name=Generator content="Microsoft Excel">
<!--[if !mso]>
<style>
v\:* {behavior:url(#default#VML);}
o\:* {behavior:url(#default#VML);}
x\:* {behavior:url(#default#VML);}
.shape {behavior:url(#default#VML);}
</style>
<![endif]-->
<style>
<!--.font0
	{color:#000000;
	font-size:11.0pt;
	font-family:宋体;
	font-weight:400;
	font-style:normal;
	text-decoration:none;}
br
	{mso-data-placement:same-cell;}
td
	{padding-top:1px;
	padding-left:1px;
	padding-right:1px;
	mso-ignore:padding;
	color:#000000;
	font-size:11.0pt;
	font-weight:400;
	font-style:normal;
	text-decoration:none;
	font-family:宋体;
	mso-generic-font-family:auto;
	mso-font-charset:134;
	mso-number-format:General;
	border:none;
	mso-background-source:auto;
	mso-pattern:auto;
	text-align:general;
	vertical-align:middle;
	white-space:nowrap;
	mso-rotate:0;
	mso-protection:locked visible;}
.et2
	{mso-generic-font-family:auto;
	mso-font-charset:134;
	mso-number-format:"yyyy/m/d";}
-->
</style>
</head>
<body>
<!--StartFragment-->

日期 | 收盘 | 开盘 | 高 | 低 | 交易量 | 涨跌幅
-- | -- | -- | -- | -- | -- | --
2025/1/20 | 3829 | 3832 | 3862.2 | 3819.6 | 30.75K | 0
2025/1/17 | 3818.6 | 3786.8 | 3830 | 3777.6 | 18.04K | 0.01
2025/1/16 | 3795 | 3806.2 | 3849.6 | 3774.2 | 35.19K | 0
2025/1/15 | 3795.2 | 3816.4 | 3817.2 | 3788.4 | 37.98K | -0.01
2025/1/14 | 3819.6 | 3725 | 3833.8 | 3721.8 | 60.82K | 0.03


<!--EndFragment-->
</body>

</html>



### 模型评估
- **模型搭建**：本研究搭建了LSTM、GRU、BiLSTM、CNN+LSTM模型，并且针对LSTM的滑动窗口大小、隐藏层单元数、学习率及CNN+LSTM模型中的CNN卷积核大小进行参数调优，获得最优模型来进行预测。
LSTM模型结构如下图：



![LSTM结构图](https://img.picui.cn/free/2025/03/27/67e50c986e41e.png)

- **量化指标**：运用均方根误差、平均绝对误差和平均绝对百分比误差等指标，精准量化模型性能。
- **金融指标**：引入夏普比率和累计收益率等金融指标，评估模型在市场周期下的稳定性，更贴合金融投资实际需求。

### 研究成果
研究发现，CNN + LSTM模型表现卓越，单位风险下超额收益获取能力最优，（通过预测未来五天的股票价格与实际股票价格进行比较得出）夏普比率高达3.93，显著优于其他模型。在算力允许的情况下，多模态特征融合的复合架构能更有效地提升策略表现。
具体结果如下：

![](https://img.picui.cn/free/2025/03/27/67e50d167981e.png)

![最终模型预测与实际预览图](https://img.picui.cn/free/2025/03/27/67e50d9f0c900.png)

训练过程截图如下：
![LSTM训练过程](https://img.picui.cn/free/2025/03/27/67e50e66c82e4.png)

### 项目价值
本研究为投资者提供了科学的决策依据，具有实用性和指导价值。

### 未来展望
未来研究将进一步探索模型的泛化能力以及在不同市场条件下的适用性，以提升系统的全面性和鲁棒性。 

### 最终预测展示
![预测结果展示](https://img.picui.cn/free/2025/03/27/67e50ef583ce1.png)
本地可视化页面通过Flask。Flask 是一个轻量级的 Python Web 框架，用于构建 Web 应用程序。在这段代码中，Flask 负责处理 HTTP 请求和响应，创建 Web 服务器，提供用户界面，并将预测结果展示给用户。

![本地可视化页面1](https://img.picui.cn/free/2025/03/27/67e50f7b836ea.png)
![本地可视化页面2](https://img.picui.cn/free/2025/03/27/67e50f7baa35d.png)
![本地可视化页面3](https://img.picui.cn/free/2025/03/27/67e50f7bb9c21.png)
![本地可视化页面4](https://img.picui.cn/free/2025/03/27/67e50f7baa4c1.png)

# 免责声明

本博客所呈现的股票价格预测研究及相关内容，仅供知识分享和学术探讨之目的，不构成任何形式的投资建议。在进行任何股票投资决策时，请务必审慎考量。

## 1. 预测结果的不确定性
股票市场是一个复杂且动态的系统，受到众多因素的综合影响，包括但不限于宏观经济状况、政治局势、公司财务状况、行业竞争态势、突发事件等。尽管本研究运用了先进的数据分析和机器学习技术进行股票价格预测，但这些预测结果仅基于历史数据和特定的模型假设，不能保证与未来的实际股票价格走势完全相符。实际股价可能会受到各种不可预见的因素影响，与预测结果产生较大偏差。

## 2. 不构成投资建议
本博客中的内容并非针对特定个人或群体的投资建议。每个人的财务状况、投资目标、风险承受能力和投资经验都有所不同，因此在做出任何投资决策之前，您应该根据自己的实际情况，充分考虑各种因素，并咨询专业的金融顾问或投资专家。任何基于本博客内容所做出的投资决策，均由您自行承担相应的风险和后果。

## 3. 信息来源与准确性
本博客中的信息主要来源于公开渠道和已有的研究成果。尽管我们尽力确保所引用信息的准确性和可靠性，但无法保证所有信息的绝对准确和完整。信息可能存在更新不及时、数据误差或其他问题。因此，在使用这些信息时，请自行进行核实和判断。

## 4. 责任限制
对于因使用本博客内容而导致的任何直接或间接损失、损害或其他不利后果，我们不承担任何法律责任。无论这种损失是由于预测结果不准确、信息错误、技术故障还是其他原因造成的，我们均不承担赔偿责任。

请始终牢记，投资股票具有较高的风险，可能导致您的本金损失。在进行投资之前，请务必充分了解相关的风险，并根据自己的实际情况做出明智的决策。 

如果您在相关技术方面（如结课大作业🛴，毕业设计🏳‍🌈）需要本研究免费支持，欢迎免费交流。若您还有其他想法或需求，不妨看看我的其他博客，说不定能找到您想要的内容。 
                                                                                                            
***
嘉利顿大学大三学长 
### email:4132790751@qq.com
### QQ:3142790751
### 欢迎您的咨询！🚀
***
