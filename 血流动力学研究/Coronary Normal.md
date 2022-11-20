---
title: Coronary Normal
author: 马鹏飞
date: 2022-10-31 00:22
project:
category: 
tags: 名词定义
description: "来源：[SimVascular Clinical Test Cases](http://simvascular.github.io/clinicalCase3.html)"
---
# Coronary Normal

冠状动脉疾病(coronary artery disease)是
心血管疾病(cardiovascular disease)中致死率最高的一类，大约占死亡比例的25%。冠状动脉狭窄(coronary artery stenosis)和
冠状动脉堵塞(coronary artery occlusion)通常是因为脂肪物质导致动脉粥样硬化(atherosclerosis)，形成斑块，阻碍动脉向心肌供血，导致心肌缺血(ischemia)。严重的冠状动脉疾病可以通过冠状动脉旁路移植手术(coronary artery bypass graft surgery, CABG)治疗，取病人自身的一些组织移植在冠状动脉阻塞处(blockages)，重新引导血液流通。仅在美国一年就要进行大约40万次冠状动脉旁路移植手术。中文里，冠状动脉旁路移植手术也称为冠状动脉搭桥手术。另一种非手术治疗方案是经皮冠状动脉介入治疗(percutaneous coronary intervention, PCI)，将球囊导管( balloon catheter)插入冠状动脉病变并充气以打开动脉。PCI每年执行约50万次。血流动力学可以帮助了解冠状动脉疾病进展和考虑个体患者最佳治疗方案的基础。

冠状动脉血流的一个关键特征是流量和压力的“异相(out-of-phase)”特征。与收缩期血流量最高的全身循环不同，冠状动脉中的大部分流量发生在舒张期。这是因为心脏收缩时冠状动脉床(coronary vascular beds)收缩，血管阻力增加。当心脏在舒张期(diastole)间放松时，阻力降低，冠状动脉流量达到最大值。SimVascular具有专门的边界条件，可以对这种行为进行建模。左冠状动脉波形(left coronary waveform)的特征通常是收缩期低流量，然后是舒张期高流量。右冠状动脉波形(right coronary waveform)的特征通常是收缩期和舒张期的流量峰值大致相等。图1中显示了两种波形的示例，其中主动脉压(aortic pressure)按比例缩放以显示其异相行为。

![图1](../attatchments/Pasted%20image%2020221031005338.png)
<center>图1：动脉的波形特征</center>
下面介绍动脉模型及其模拟，包括构建冠状动脉模型并运行仿真。建议新用户首先阅读一般文档，以了解SimVascular中的工作流程，因为本教程将重点介绍针对冠状动脉建模的技巧，希望用户已经对SimVascural有了大致的了解。在介绍过程中，我们会给出相关参考文档的出处。

## 冠状动脉解剖
主动脉(aorta)分出冠状动脉主干(main coronary artery)，它们通常被称为左主冠状动脉(left main coronary artery, LCA)和右主冠状动脉(right main coronary artery, RCA)。左冠状动脉进一步分支为左前降支(left anterior descending artery, LAD)和左回旋支(left circumflex, LCX)。左冠状动脉主要灌注心脏的左侧（即左心室和左心房），右冠状动脉主要灌流心脏的右侧。在高分辨率CT图像数据中可以看出，这些主要血管又分出许多小血管。

## 图像数据

冠状动脉成像(Coronary imaging)通常通过CT完成，也有一些通过MRI完成。冠状动脉的医学图像可能包括也可能不包括主动脉弓(aortic arch)。在这里给出的示例中，图像数据在主动脉根部被切断，因此相应的模型仅包含主动脉根部和冠状动脉。解剖模型中通常不包括心腔(心室和心房)，因此流入条件仅应用于主动脉瓣(aortic valve)远端。

## 冠状动脉模型构建

通常，构建冠状动脉模型的第一步是构建主动脉，因为它是图像数据中最大的血管。左主冠状动脉和右主冠状动脉直接从主动脉分支，因此它提供了一个很好的锚定点。主动脉的起始位置在左心室，我们可以看见这一部分管腔。如下图所示，可以在轴向切片139的轴向视图中看到它。

![](../attatchments/Pasted%20image%2020221031012127.png)

<center>图2：CT图像中的主动脉根</center>




