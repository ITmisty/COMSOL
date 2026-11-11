# COMSOL Learning Journey
一、背景知識<br>
二、COMSOL建模<br>
三、如何連結MATLAB和COMSOL<br>
四、使用文獻資料練習模擬<br>
五、 錯誤紀錄&解決方法


**一、背景知識<br>**
1.Electromagnetics:Maxwell's Equations<br>
2.Electromagnetic Waves:Frequency、Wavelength、Propagation<br>
3.Material Properties:Permittivity、Permeability、Conductivity<br>
4.RF Fundamentals:Resonance、Impedance、RF Loss<br>
5.S-Parameters:S11、S21、Reflection、Transmission<br>
6.EMI:Electromagnetic Interference、Shielding Effectiveness<br>

**二、COMSOL建模<br>**
1.Model Wizard：建立模型<br>
2.Global Definitions：設定全域參數<br>
3.Geometry：建立幾何結構<br>
4.Materials：設定材料<br>
5.Physics：設定物理場<br>
6.Mesh：建立網格<br>
7.Study：設定求解方式<br>
8.Results：分析模擬結果<br>

**三、如何連結MATLAB和COMSOL**  (MATLAB使用前可以確認所屬學校或機構有沒有買)<br>
1.先打開命令提示字元<br>
2.輸入 cd /d "~~C:\Program Files\COMSOL\COMSOL56\Multiphysics\bin\win64~~"，畫線的地方請自行輸入你COMSOL的路徑，要選最原始的路徑(可在本機處搜尋COMSOL找)，不是桌面捷徑的路徑<br>

% Add COMSOL LiveLink path
addpath('你的COMSOL安裝路徑\Multiphysics\mli');

% Connect MATLAB to COMSOL Server
mphstart

3.再輸入comsolmphserver.exe<br>
4.在MATLAB中的Command Window中輸入 addpath('~~C:\Program Files\COMSOL\COMSOL56\Multiphysics~~\mli'); mphstart。<br>
完成後就會這樣
<p align="center">
  <img src="https://github.com/user-attachments/assets/107ae9ad-ff96-4e94-9bdc-06f74307df12" width="600">
</p>
<p align="center">
  <img src="https://github.com/user-attachments/assets/6564f543-81e1-470d-8146-af2d61e1e26e" width="600">
</p>

提醒:完成連接後命令提示字元視窗不要關，這樣萬一斷掉不用再重開

**四、使用文獻資料練習模擬<br>**
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
都找完之後就可以打開COMSOL，步驟如下:<br>
1.

自己動手製作發現非常費時，就算是簡單構造的封裝建模，假設有32支lead frame就夠痛苦了，要先建好一支、複製一排、使用鏡射到對面，其中還要確認座標正確、材料對的上。  
也有可能我接觸時間不到半天，對操作不熟悉，也許有更快的方式。  
附圖是我的成果，少的可憐。  
<p align="center">
  <img src="https://github.com/user-attachments/assets/d849a8a0-6c35-4e5a-b885-ce01eb19b6d6" width="600">
</p>

為了節省時間，使用AI+MATLAB，先把參數和其他設定給AI，請他做出適合的MATLAB程式碼，再將MATLAB和COMSOL連結。

文獻二:Wide-range soft anisotropic thermistor with a direct wireless radio frequency interface - Nature communication, 2024  
  
**五、錯誤紀錄&解決方法**


