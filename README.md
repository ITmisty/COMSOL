# COMSOL
大致規劃<br> 
一.先了解一些背景知識<br>
二.熟悉操作(像是調整參數、製作模型)<br>
三.使用文獻資料練習模擬

**一、背景知識<br>**
1.電磁學與波動基礎<br>

**二、熟悉操作、常見問題<br>**

**三、使用文獻資料練習模擬<br>**
文獻一:EMI shielding leadless package solution for automotive - Journal of Advanced Joining Processes, 2022<br>
這篇是在說改良一種QFN，Microleadframe®(MLF®)，名為routable MLF (rtMLF®)，可以更有效減少EMI<br>


想要使用COMSOL模擬出圖二的Normal QFN，該如何下手呢?<br>
目前已知參數:<br>
往下找到 Material Contents，填入下列三項（EMC 的假設值）：<br>
Relative permittivity（相對介電常數）：3.7<br>
Relative permeability（相對導磁率）：1<br>
Electrical conductivity（導電率）：0 S/m<br>
Body size : 8 × 8 mm<br>
Die size: 4 × 2 mm <br>
A noise source was placed 0.3 mm away from the package top and 3.0 mm from a package side with an operation frequency of 5 GHz.<br>
Gold (Au) wires are used<br>
Conformal shield layer consists of SUS (Steel Use Stainless, SUS, an acronym from Japanese Industrial Standards (JIS))-Cu-SUS<br>
自己手搓了
