# Project7： A/B Test
优达学城数据分析师 纳米学位

<script type="text/javascript"
   src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>


# 试验设计
## 试验概述：免费试学筛选器
### 试验进行之前
在进行此试验时，优达学城当前的主页上有两个选项：“开始免费试学”和“访问课程资料”。 如果学生点击“开始免费试学”，系统将要求他们输入信用卡信息，然后他们将进入付费课 程版本的免费试学。14 天后，将对他们自动收费，除非他们在此期限结束前取消试用。若 学生点击“访问课程材料”，他们将能够观看视频和免费进行小测试，但是他们不会获得导 师指导支持或验证证书，无法提交最终项目来获取反馈。 

### 试验内容
在此试验中，优达学城测试了一项变化，如果学生点击“开始免费试学”，系统会问他们有 多少时间投入到这个课程中。如果学生表示每周 5 小时或更多，将按常规程序进行登录。 如果他们表示一周不到 5 小时，将出现一条消息说明优达学城的课程通常需要更多的时间 投入才能成功完成，并建议学生可免费访问课程资料。在这里，学生可选择继续进行免费试 学，或免费访问课程资料。这张截图展示了试验概况。

### 试验解读
从上述说明可以看出，试试验验改变了学生点击“开始免费试学”到“登录并进入试用课程”之间的流程，增加了每周投入时间筛选的流程。

### 试验期望
1. 减少因为没有足够的时间而离开免费试学，并因此受挫的学生数量；
2. 不会在很大程度上减少继续通过免费试学和最终完成课程的学生数量。


### 转移单位
转移单位为 cookie，尽管学生参加的是免费试学，但在登录后他们的用户 id 便被跟踪。同 一个用户 id 不能两次参加免费试学。对于不参加免费试学的用户，他们的用户 id 不会在 试验中被跟踪，即使他们在访问课程概述页面时登录了网站。

## 度量选择
### 选择不变度量
可以选择的不变量指标如下：

1. **Cookie 的数量**：即查看课程概述页面的唯一 cookie 的数量
2. **点击次数**：即点击“开始免费试用”按钮（在免费试用屏幕触犯前发生）的唯一 cookie 的数量。

**选择这两个度量的原因如下：**

根据试验内容，我们可以得知，试验改变的是学生点击“开始免费试学”到“登录“之间的流程，增加了每周投入时间筛选的流程。
而Cookie的数量，以及点击次数的计算，都是在该新增的流程之前统计的，不会收到更改的流程影响。
故选择 cookie数量和点击次数作为不变度量。

实际上，**点进概率**也可以作为不变量指标来选择，但是由于点进概率计算的是计算的是点击“开始免费试学”的按钮的唯一 cookie 的数量除以查看课程概述 页的唯一 cookie 的数量所得的比率，与前两个不变量指标Cookie 的数量和点击次数有重复的地方，故这里不选择点进概率作为不变量指标。

**不选择其他度量的原因如下：**

*  **用户id的数量**：用户id计算的是参加免费试学的用户数量，而试验更改了进入的方式，增加了筛选器，故这个变量会受到影响
*  **点进概率**：点进概率计算的是点击“开始免费试学”的按钮的唯一 cookie 的数量除以查看课程概述 页的唯一 cookie 的数量所得的比率，虽然这个指标也是不变的，但与cookie数量和点击次数这两个指标有重合，故不选择
*   **总转化率**： 计算的是完成登录并参加免费试学的用户 id 的数量除以点击“开始免费试学” 按钮的唯一 cookie 的数量所得的比率。由于完成登录并参加试学的用户有可能会改变，故不选择
*   **留存率**：计算的是在 14 天的期限过后仍参加课程（因此至少进行了一次付费）的用户 id 数量除以完成登录的用户 id 的数量。由于这个指标的计算方式是在试验更改之后的流程，故有可能会发生变化
*   **净转换率**：即在 14 天的期限后仍参与课程的用户 id 的数量（因此至少进行了一 次付费）除以点击了“开始免费试学”按钮的唯一 cookie 的数量所得的比率，由于14后参与课程的用户id数量有可能会变化，故不选择。

### 选择评估度量
选择如下：

1. 总转化率
2. 净转换率
3. 留存率

选择理由如下：

$$ 总转化率 = \dfrac{完成登录并参加免费试学的用户 id 的数量}{点击“开始免费试学” 按钮的唯一 cookie 的数量} $$    

试验更改流程后，直接影响的就是“完成登录并参加免费试学的用户 id 的数量”，
故用总转化率可以评估试验是否改变了完成登录并参加免费试学的用户数量。

$$ 净转化率 = \dfrac{14天试学结束后仍参加课程的用户 id 的数量}{点击“开始免费试学” 按钮的唯一 cookie 的数量} $$ 

用净转化率可以评估试验是否在很大程度上减少继续通过免费试学和最终完成课程的学生数量。

$$ 留存率 = \dfrac{14天试学结束后仍参加课程的用户 id 的数量}{完成登录的用户 id 的数量} $$ 

$留存率=\dfrac{净转化率}{总转化率}$ ， 用此度量也可以评估试验是否有效果，即减少了登录并参加试学的人数，但是付费人数不变。   

**不选择其他度量的原因如下：**
1. **Cookie 的数量**、**点击次数**、**点进概率**：这三个指标在试验组和对照组记录的均是更改流程之前的数据，是不变量，试验引起的数据变化无法识别到，故不能选择评估度量；
2. **用户id的数量**：用户id的计算也是发生在实验更改的步骤后面，能够对实验的影响作出反应。但是没有选择这个指标是因为：没有归一化，由于实验组和对照组的cookie数量不一定相同，也就是说两组中用户ID数量不同 可能是由于实验的影响，也可能是由于两组cookie的不同。所以使用用户ID数量的区别不能够很好的评估试验的效果。在一个比例化的评估度量（总转化率）存在的情况下，我们可以不选择用户ID的数量。   

### 期望从评估度量中得到的结果
本试验的目标是，减少学习时间不足的用户参与免费试学，同时提高服务质量。我们预计学习时间不足的用户原本就不会付费。若该实验起到效果，则总转化率会显著减少，留存率会显著增加，净转化率应该变化不大或增长。
故期望结果有两个：
1. 总转化率，有负的显著性变化；
2. 净转化率变化不大，置信区间可以包含0或者大于0，但是不可以小于0。
3. 留存率，有正的显著性变化。

## 测量标准偏差
**1. 计算所有评估度量的标准偏差**

评估度量 | 基准值 | 标准偏差
--------- | ------------- | -------------
总转化率 | 0.20625 | 0.0202
净转化率 | 0.1093 | 0.0156
留存率 | 0.53 | 0.0549

以总转化率为例，计算过程如下：
1）由于 $N = 5000*0.08 = 400$，可以假设点击量为正态分布
2）标准偏差: $SE = \sqrt{\dfrac{0.20525*(1-0.20625)}{400}}$   =0.0202

同样的方法，计算净转化率的标准偏差为0.0156，留存率的标准偏差为0.0549.

**2. 说明分析变异性是否可能匹配经验变异性**   
由于分析变异性和经验变异性匹配的条件是unit of analysis = unit of diversion。分析3个评估指标如下：
1）总转化率的分析单位是cookie，转移单位也是cookie，故总转化率的分析变异性和经验变异性匹配；
2）净转化率的分析单位是cookie，转移单位也是cookie，故净转化率的分析变异性和经验变异性也匹配；
3）留存率的分析单位是user-id，转移单位是cookie，故留存率的分析变异性和经验变异性不匹配，根据经验计算的变异性可能会远大于分析变异性。在这种情况下，应该为留存率收集变异的经验估计。如果有足够的时间，应该为留存率收集变异的经验估计。


## 规模
### 样本数量和支持
1. 是否会使用Bonferroni校正？   
	答案：不会。
	因为两个评估度量指标总转化率和净转化率是相关的，不是独立的。使用Bonferroni校正法，会使得α值太小，结果太过于保守。
2. 根据试验要求，可知，α=0.05，β=0.2，总转化率的d_min=0.01，净转化率的d_min=0.0075，留存率的d_min=0.01；
3. 用在线计算器计算得出总转化率的sample size=25835，转化成pageview=25835*2/0.08=645875
4. 用在线计算器算出净转化率的 sample size=27413，则转化成pageview = 27413*2/0.08=685325
5. 用在线计算器算出留存率的 sample size=39115，则转化成pageview =39115*2/0.0165=4741200
6. 由于留存率需要的页面量太大，会导致实验实际太久，故舍弃掉留存率这个指标。由于要确保剩下的两个度量都具有足够的数据支持，故取两个pageview中较大的值，即 685325

故样本数量应该为685325.

### 持续时间和风险暴露
1. 说明你会将哪一部分流量转入该试验？需要多少天运行试验？   
	答：对于该试验，将投入每天的全部流量进行试验。鉴于此条件，需要试验的天数为 685325/40000=17.1≈18天。   
	
2. 说明选择所转移流量部分的原因。    
	答：选择使用全部流量是因为同一时间并没有其他试验需要同步实施，且该试验的风险很低，如果只使用部分流量，会导致试验持续的时间太久，故选择转移全部流量。    
	
3. 说明试验的风险    
答：该试验的风险很低。
	**从身体、情感、心理方面来说：**
	1）本试验在用户点击“开始试学”到登录并进入试学页面之间，加入了一个筛选器，对于每周学不到5小时的用户，会建议去免费访问课程资料，对于超过5小时的用户，没有影响。
对于每周时间少于5小时的用户，如果他们还想参加这个课程，仍然可以进入免费试学、登录并可能完成继续课程，不会因此影响用户使用网站的习惯。
2）页面展示上没有过大的改动，不会对用户产生情感上的影响，用户也不需要花很长时间来适应页面的改变。
故而，对身体、情感、心理方面的影响。

	**从道德伦理方面来说：**
	1）该试验并没有做涉及到道德层面的更改，所以并不会增加道德上的风险

	**数据库安全方面**
	1）	该试验没有关于数据库及后台的改变，不用担心数据的丢失及由于后台的失误导致网页奔溃用户无法访问网页等大问题。
	
	**数据敏感性方面**
	1）	此试验也不会对用户的个人信息安全造成风险，因为不论网页是否增加了提醒，用户在确认参加免费试学时都得输入信用卡信息，而很明显系统一定会保护用户的个人信息。
    
	根据上面的说明，可以得出结论，本试验的风险很低。

# 试验分析
## 合理性检查
不变量为 cookie数量，点击次数。
其完整性检验如下：

/      | 置信区间下限 | 上限 | 观察值 | 是否通过检验
--------- | ------- | ------- | ------- | -------
cookie数量 | 0.4988 | 0.5012 | 0.5006 | 通过检验
“开始免费试学”的点击次数 | 0.4959 | 0.5041 | 0.5005 | 通过检验

从上述表格可以看出，合理性检查成功，可以进行下一步分析了。  

**计算过程如下：**
观察试验组和对照组的值，计算总的cookie数量和总的点击次数如下，

    /  | 总cookie数量 | 总点击次数 
--------- | ------- | ------- 
试验组 | 344660 | 28325
对照组 | 345543 | 28378

合理性分析的方法是：选择不变量，看它在试验组和对照组内是否具有合理的相似性。

总cookie数量的不变性计算如下：

1. 由于每条cookie都是以0.5的概率随意分配到对照组和试验组的，即分到对照组的次数遵循二项分布定理，所以可以构建一个二项式置信区间；
2. 由于总体有接近7万的数据，已经足够假设一个正态分布了   
	1）计算二项分布的标准差为 $SE=\sqrt{\dfrac{0.5*(1-0.5)}{344660+345543}}$ = 0.0006   
	2) 由于 $α=0.05$ ，可知 $z=1.96$，得到误差范围 $m=SE*z$ = 0.0012    
	3) 则置信区间为 $(0.4988, 0.5012)$    
	4) 观察对照组的 $p= \dfrac{345543}{345543+344660}$ = 0.5006   
3. 从上面的计算可知，观察到对照组的p值为0.5006，落在置信区间$(0.4988, 0.5012)$ 之间，故总的cookie数量可信，即cookie数量通过了完整性检验

总点击次数的不变性计算方法类似，不详细列出计算过程了。

## 效应大小检验
从上述试验说明，可知，本试验选择了两个评估度量，分别是总转化率和净转化率。
计算这两个评估度量试验组和对照组之间差异的置信区间，列表如下：   

    /  | 差异的置信区间下限 | 上限 | 统计显著性 | 实际显著性
--------- | ------- | ------- | ------- | -------
总转化率 | -0.0291 | -0.0120 | ✔️ | ✔️
净转化率 | -0.0116 | 0.0019 | ✘ | ✘

计算过程在此省略。
从上面的表格可以看出，

1. 对于总转化率   
1）置信区间不包含0，可以确信它会变化，即这个指标具有统计显著性；   
2）又由于置信区间不包含实际显著性边界 （-0.01，0.01），故该指标具有实际显著性；   
3）由于置信区间的上下限均为负值，故总转化率具有负的统计显著性和负的实际显著性

2. 对于净转化率   
1）置信区间包含0，说明不具备统计显著性；    
2）置信区间包含实际显著性边界0.0075，说明不具备实际显著性。

## 符号检验
符号检验的过程及结果见表格

    /  | 总天数 | 对照组概率大于试验组概率天数 | P-value | 统计显著性
--------- | ------- | ------- | ------- | -------
总转化率 | 23 | 19 | 0.0026 | ✔️
净转化率 | 23 | 13 | 0.6776 | ✘

通过表格可以看出，
1. 总转化率的P-value=0.0026 <0.05，说明该指标具有统计显著性；
2. 净转化率的P-value=0.6776 > 0.05，说明该指标不具有统计显著性。

## 结果汇总
1. 是否使用Bonferroni 校正，并解释原因。    
答：没有使用Bonferroni 校正，原因是两个评估指标之间具有相关性，并不是独立的指标，如果使用Bonferroni 校正，会导致结果太过于保守。

2. 效应大小检验和符号检验之间是否存在差异，并说明差异原因。   
答： 从上述的介绍可知，效应大小检验和符号检验之间不存在差异。可以得出 总转化率具有负的统计显著性，净转化率不具有统计显著性的结果。

# 建议
根据上面的分析，我不建议开展此试验。理由如下：

本试验的预期是：
1. 减少因为没有足够的时间而离开免费试学，并因此受挫的学生数量；
2. 不会在很大程度上减少继续通过免费试学和最终完成课程的学生数量。

转化成评估指标后，对应的预期是：
1. 总转化率，有负的显著性变化；
2. 净转化率变化不大，置信区间可以包含0或者大于0，但是不可以小于0。

从上述结果汇总可知，总转化率确实具有负的统计显著性和实际显著性，是我们希望看到的结果。
但是，净转化率的置信区间为（-0.0116 , 0.0019），包含负数，这说明在投入人力和时间成本之后，进行该实验之后净转化率可能会减少。这是我们不希望看到的。

故不建议实施该试验。

对于上述试验，最终结果虽然总转化率达到了想要的效果，净转化率可能会减少，也就是说，付费用户很可能会减少，这个举措会减少公司的收入，已经最终通过课程的人数，与公司的目标相悖。所以这个试验弊大于利，不值得花费后续试验的成本。应该舍弃。

我们可以试验一些新的，并与公司目标相符合的A/B test。


# 根进试验
通过上述结论，我们已经否定了该实验的有效性。
因此，我们需要进行一个新的A/B test。
我们将目标定位，增加继续通过免费试学和最终完成课程的学生数量。

## 实验设计
### 实验概述
对于首次在Udacity进行学习的用户，给参加免费试学的学生发放200元优惠券，并在首次支付时，抵扣200元现金。
### 实验进行之前 
在进行此试验时，优达学城当前的主页上有两个选项：“开始免费试学”和“访问课程资料”。 如果学生点击“开始免费试学”，系统将要求他们输入信用卡信息，然后他们将进入付费课 程版本的免费试学。进入试学页面后，用户点击“开始学习”就可以开始学习。14 天后，将对他们自动收费，除非他们在此期限结束前取消试用。
### 试验内容
在此试验中，将测试了一项变化，如果学生点击“开始免费试学”，按常规程序进行登录，并开始试学。对于首次在Udacity进行学习的用户，进入试学页面后，在“开始学习”的下方增加一个领取红包的按钮，用户点击按钮，弹框提示“可领取200元红包，将在首次付费时，抵扣200元费用，不限课程。”点击按钮“领取”，可获得200元红包，点击完“领取”后，按钮显示“已领取”。点击弹框的“x”可以关闭弹框。用户领取成功后，“领取红包”的按钮将消失。用户点击“开始学习”，可以开始学习该课程。当用户付费时，增加抵扣200元的说明，总价格减少200元。其他步骤不变。详细见图解：
[领取红包](picture/receive_a_red_envelope.jpeg)
[弹框](picture/receive_a_red_envelope_bounced.jpeg)
[领取以后](picture/WechatIMG24.jpeg)
[付费页面](picture/WechatIMG25.jpeg)

### 实验期望
增加继续通过免费试学和最终完成课程的学生数量，留住更多用户。

## 度量选择
### 不变量度量
1. **Cookie 的数量**：即查看课程概述页面的唯一 cookie 的数量
2. **点击次数**：即点击“开始免费试用”按钮（在免费试用屏幕触犯前发生）的唯一 cookie 的数量。
3. **总转化率**： 计算的是完成登录并参加免费试学的用户 id 的数量除以点击“开始免费试学” 按钮的唯一 cookie 的数量所得的比率。
4. **点进概率**：点进概率计算的是点击“开始免费试学”的按钮的唯一 cookie 的数量除以查看课程概述 页的唯一 cookie 的数量所得的比率。   

**选择这四个度量的原因如下：**

根据试验内容，我们可以得知，试验进入试学页面之后的流程，增加了领取红包的步骤以及付费时直接抵扣现金的步骤。
而这几个指标的数据，都是在该新增的流程之前统计的，不会受到更改的流程影响。
故选择 cookie数量、点击次数、总转化率、点进概率作为不变度量。


### 评估度量
选择如下：
1. 留存率

$$ 留存率 = \dfrac{14天试学结束后仍参加课程的用户 id 的数量}{完成登录的用户 id 的数量} $$ 

用留存率可以评估继续学习并完成课程的用户数量是否显著性增长，如果显著性增长，留存率应该可以显著性提高。 

### 试验期望
留存率有显著性增长。

## 转移单位
选择user-id作为转移单位。
本试验的目标是增加继续通过免费试学和最终完成课程的学生数量，留住更多用户。
从实验设置来看，用户领取红包之后，可以抵扣首次付费200元现金，这个条件应该可以跨平台使用，即该更改应该在各个设备之间具有一致性。故选择user-id作为转移单位。

