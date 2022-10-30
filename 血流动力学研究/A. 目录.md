---
title: A. 目录
author: 马鹏飞
date: 2022-10-29 10:11
project:
category: 
tags: 目录
description: "描述"
# layout: post
# mathjax: yes
# status: # prepared or working or finished or abandoned
# version: 0.0
# researchers:
# doi:}}
---
# A. 血流动力学

>来源：Impacts of Internal Carotid Artery Revascularization on Flow in Anterior Communicating Artery Aneurysm: A Preliminary Multiscale Numerical Investigation

[[血运重建|血运重建 (Revascularization)]]：血运重建是指通过药物或手术的方式，使狭窄、闭塞的动脉血管重新恢复血流灌注，以恢复相应缺血器官的供血，达到治疗目的的手段。

前交通动脉瘤血管(anterior communicating artery aneurysm, ACoAA)：

颈内动脉(internal carotid artery, ICA):

单侧颈内动脉血运重建(unilateral ICA revascularization)：

脑血管系统(cerebral vascular system)：

血流动力学参数(hemodynamic parameter)：

壁面剪切应力(wall shear stress, WSS)：动脉壁上施加在血流上的摩擦力，
$$
\tau_w=\mu\left(\frac{\partial u}{\partial y}\right)_{y=0}
$$
其中，$\tau_w$为WSS，$\mu$为血液的动态粘性，$u$为血流速度，$y$为与壁面的距离。在IB方法中，可以先将流体的速度插值到固体上，然后再在固体表面计算WSS。

时均壁面剪切应力(Time-averaged WSS, TAWSS)：通过对整个心动周期的WSS进行积分来计算TAWSS
$$
T A W S S=\frac{1}{T} \int_0^T\left|\overrightarrow{\tau_w}\right| d t
$$
其中，$T$为一个心动周期。

相对停留时间(relative residence time, RRT)：RRT表示血液在壁附近的停留时间
$$
R R T=\frac{1}{(1-2 * O S I) \times T A W S S}
$$


振荡剪切指数(oscillating shear index, OSI)：OSI表示心动周期内WSS的方向变化程度
$$
O S I=\frac{1}{2}\left(1-\frac{\left|\int_0^T \overrightarrow{\tau_w} d t\right|}{\int_0^T\left|\overrightarrow{\tau_w}\right| d t}\right)
$$


狭窄程度(stenosis degree)：根据北美症状性颈动脉内膜切除术试验(North American Symptomatic Carotid Endarterectomy Trial, NASCET)，狭窄程度的定义为
$$
S=\left(1-\frac{d_s}{d_n}\right) \times 100 \%
$$
其中 $\mathrm{S}$ 为狭窄参数，$d_s$为ICA狭窄段的管腔直径，$d_n$为ICA正常段的管腔直径。$d_n$的计算方式：首先在MIMICS软件(Materialise Inc., Leuven, Belgium)中计算狭窄模型和特定患者模型的末端关节的横截面积，然后可以根据圆形面积的方程计算$d_n$。(原文是这样的，我没理解，我认为算$d_n$只需知道正常段的横截面积)

瞬态计算流体力学模拟(transient CFD simulations)：

未破裂颅内动脉瘤(unruptured intracranial aneurysms, UIA)：

颈动脉狭窄(carotid artery stenosis)：

脑血流量(cerebral blood flow, CBF)：

计算机断层摄影血管造影(computed tomography angiography, CTA)：CT血管造影

>来源：

主动脉狭窄(Aortic stenosis, AS)
