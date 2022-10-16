---
title: Quasi-static image-based immersed boundary-finite element model of left ventricle under diastolic loading
author: 马鹏飞
category: translation
layout: post
mathjax: yes
Status: waiting
tags: 论文翻译
date: 2022-10-16 10:21
---



心脏的[[有限应力应变分析]]可使我们深入了解[[心肌功能和功能障碍]]的生物力学原理。
在此，我们使用结合了[[有限元结构力学模型]]的[[浸没边界法]]，建立了针对特定患者的左心室动态模型。我们使用了[[基于结构体的超弹性应变能函数]]描述左心室心肌的被动力学响应，使用了根据健康人体心脏的临床核磁共振图像重建的解剖几何形状，使用了基于规则生成的纤维结构。将[[浸没有限元方法]]得到的数值结果与商业有限元求解器得到的结果进行比较，发现在[[舒张负荷条件]]下，两者的计算结果能够吻合，与过去研究者计算或者实验得到的结果都是一致的。因此，我们可以说[[浸没有限元方法]]对左心室的力学模拟是可靠的。

心脏疾病和心脏衰竭的生物力学机理尚未完全明晰，我们知道心肌[[应力应变分布]]的改变可能会导致[[心室肥厚]]等疾病[^1][^2]，但是我们无法直接测量患者的心肌的[[应力应变分布]]。[[心脏的计算模型]]可以很便利地提供三维的应力应变分布，这样的模型可以帮助医生确定患者的风险等级，并帮助医生临床决策[^3]。提高对心室生物力学的理解对于优化旨在恢复正常心脏功能的医疗和手术程序也很重要[^4]。

开发一个真实的[[心脏计算模型]]是非常复杂的。心脏是一个[[多物理系统]]，心肌收缩是由[[心脏电生理学]]来刺激和协调的。主动和






[^1]: Costa KD, Holmes JW, McCulloch AD. Modelling cardiac mechanical properties in three dimensions. Philosophical Transactions of the Royal Society of London. Series A: Mathematical, Physical and Engineering Science 2001; 359(1783):1233–1250.
[^2]: Zile MR, Baicu CF, Gaasch WH. Diastolic heart failure abnormalities in active relaxation and passive stiffness of the left ventricle. New England Journal of Medicine 2004; 350(19):1953–1959.
[^3]: Smith N, de Vecchi A, McCormick M, Nordsletten D, Camara O, Frangi AF, Delingette H, Sermesant M, Relan J, Ayache N, Krueger MW, Schulze WHW, Hose R, Valverde I, Beerbaum P, Staicu C, Siebes M, Spaan J, Hunter P, Weese J, Lehmann H, Chapelle D, Rezavi R. euHeart: personalized and integrated cardiac care using patient-specific cardiovascular modelling. Interface Focus 2011; 1(3):349–364.
[^4]: Niederer SA, Shetty AK, Plank G, Bostock J, Razavi R, Smith N, Rinaldi CA. Biophysical modeling to simulate the response to multisite left ventricular stimulation using a quadripolar pacing lead. Pacing and Clinical Electrophysiology 2012; 35(2):204–214.