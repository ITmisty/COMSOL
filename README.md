# COMSOL Learning Journey
[一、背景知識](#bg)<br>
[二、COMSOL建模基礎步驟](#step)<br>
[三、COMSOL LiveLink for MATLAB](#livelink)<br>
[四、使用文獻資料練習模擬](#practice)<br>
[五、錯誤紀錄&解決方法&功能](#errors)


<a id="bg"></a>
**一、背景知識**
1. Electromagnetics:Maxwell's Equations<br>
2. Electromagnetic Waves:Frequency、Wavelength、Propagation<br>
3. Material Properties:Permittivity、Permeability、Conductivity<br>
4. RF Fundamentals:Resonance、Impedance、RF Loss<br>
5. S-Parameters:S11、S21、Reflection、Transmission<br>
6. EMI:Electromagnetic Interference、Shielding Effectiveness<br>

<a id="step"></a>
**二、COMSOL建模基礎步驟**
1. Model Wizard：建立模型<br>
2. Global Definitions：設定全域參數<br>
3. Geometry：建立幾何結構<br>
4. Materials：設定材料<br>
5. Physics：設定物理場<br>
6. Mesh：建立網格<br>
7. Study：設定求解方式<br>
8. Results：分析模擬結果<br>
9. 顏色和動畫
    
<a id="livelink"></a>
**三、COMSOL LiveLink for MATLAB** (MATLAB使用前可以確認所屬學校或機構有沒有買)<br>
1. 先打開命令提示字元<br>
2. 輸入 cd/d"你的COMSOL安裝路徑\Multiphysics\bin\win64"<br>
*第一次啟動可能會要你設定使用者名稱和密碼，隨便設一組並記住。
3. 再輸入 comsolmphserver.exe<br>
4. 在MATLAB中的Command Window中輸入 addpath('你的COMSOL安裝路徑\Multiphysics\mli');mphstart<br>
*如果前面有設密碼，連線時會問你，輸入同一組。接著輸入 mphversion，有顯示 COMSOL 版本就成功，之後就能 Run 腳本。<br>

&emsp;&emsp;大概會長這樣
<p align="center">
  <img src="https://github.com/user-attachments/assets/c62883d7-98a3-498c-864d-3ae17bbe3a07" width="600">
</p><br>
<p align="center">
  先開命令提示字元輸入，看到started listening on port... 代表成功<br>
  提醒:完成連接後命令提示字元視窗不要關，不然會終止 Server，使 MATLAB 無法繼續連線。
</p><br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/d376f9fa-669b-401e-be1a-6a110360bb3a" width="600">
</p><br>
<p align="center">
  到MATLAB輸入該輸的部分
</p><br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/677116e7-f8c0-4937-9af2-d942cfd68833" width="600">
</p><br>
<p align="center">
  把AI整理的參數大禮包用MATLAB打開，確認沒問題按Run
</p><br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/b4b9d0a7-5bd9-47d6-8f63-09f3091e2225" width="600">
</p><br>
<p align="center">
  跑完之後會出現在你存檔的地方，如果一開始就想改檔名可以拉到最下面改紅圈圈的地方
</p><br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/6a9e2548-8571-4321-b34a-9a6e73a558ea" width="600">
</p><br>
<p align="center">
  點開檔案後按透明就可以看到暖心的一幕
</p><br>

<a id="practice"></a>
**四、使用文獻資料練習模擬**<br>
文獻一:EMI shielding leadless package solution for automotive - Journal of Advanced Joining Processes, 2022<br>
&emsp;&emsp;這篇是在說改良一種QFN，Microleadframe®(MLF®)，名為routable MLF (rtMLF®)，可以更有效減少EMI<br>


&emsp;&emsp;想要使用COMSOL模擬出圖二的Normal QFN，該如何下手呢?<br>
&emsp;&emsp;列出部分參數(更完整的參數可以直接請AI抓再檢查就好):<br>
&emsp;&emsp;1. Geometry Parameters<br>
&emsp;&emsp;&emsp;&emsp;Package Body Size:8 × 8 mm	<br>
&emsp;&emsp;&emsp;&emsp;Die Size:4 × 2 mm<br>
&emsp;&emsp;&emsp;&emsp;Bond Wire Material:Gold (Au)<br>	
&emsp;&emsp;2. Material Properties<br>
&emsp;&emsp;&emsp;&emsp;EMC (Epoxy Molding Compound)<br>
&emsp;&emsp;&emsp;&emsp;以下數值為模擬時採用的假設值，並非已確認的論文原始數據。<br>
&emsp;&emsp;&emsp;&emsp;Relative Permittivity:3.7<br>
&emsp;&emsp;&emsp;&emsp;Relative Permeability:1	<br>
&emsp;&emsp;&emsp;&emsp;Electrical Conductivity:0 S/m<br>

&emsp;&emsp;3. Conformal Shielding Layer<br>
&emsp;&emsp;&emsp;&emsp;Material Structure: SUS–Cu–SUS<br>
&emsp;&emsp;&emsp;&emsp;SUS: Stainless Steel（不鏽鋼）<br>
&emsp;&emsp;&emsp;&emsp;Cu: Copper（銅）<br>
&emsp;&emsp;&emsp;&emsp;屏蔽層由三層材料組成，依序為不鏽鋼、銅、不鏽鋼。<br>

&emsp;&emsp;4. Simulation Conditions<br>
&emsp;&emsp;&emsp;&emsp;Parameter Value<br>
&emsp;&emsp;&emsp;&emsp;Operating Frequency	5 GHz<br>
&emsp;&emsp;&emsp;&emsp;Noise Source Distance from Package Top	0.3 mm<br>
&emsp;&emsp;&emsp;&emsp;Noise Source Distance from Package Side	3.0 mm<br>

&emsp;&emsp;都找完之後就可以打開COMSOL:<br>
&emsp;&emsp;自己動手製作發現非常費時，就算是簡單構造的封裝建模，假設有32支lead frame就夠痛苦，要先建好一支、複製一排、使用鏡射到對面，再確認座標正確、材料對的上。可能我接觸時間少對操作不熟悉，也許有更快的方式。  附圖是製作成果(未完成)，少的可憐。  
<p align="center">
  <img src="https://github.com/user-attachments/assets/ad6946ef-aadf-4a42-bf78-defd8ad1ba62" width="600">
</p> <br>
&emsp;&emsp;如何做出來的放在 COMSOL基礎建模步驟<br>
<br>
<br>
文獻二:Wide-range soft anisotropic thermistor with a direct wireless radio frequency interface - Nature communication, 2024  <br>
&emsp;&emsp;這篇試著直接用MATLAB，然後學習在MATLAB端做調整 <br>


<a id="errors"></a>
**五、錯誤紀錄&解決方法&功能**

