# COMSOL Learning Journey
[一、背景知識](#一背景知識)<br>
二、COMSOL建模基礎步驟<br>
三、COMSOL LiveLink for MATLAB<br>
四、使用文獻資料練習模擬<br>
[五、錯誤紀錄&解決方法&功能](##五、錯誤紀錄&解決方法&功能)


**一、背景知識<br>**
1. Electromagnetics:Maxwell's Equations<br>
2. Electromagnetic Waves:Frequency、Wavelength、Propagation<br>
3. Material Properties:Permittivity、Permeability、Conductivity<br>
4. RF Fundamentals:Resonance、Impedance、RF Loss<br>
5. S-Parameters:S11、S21、Reflection、Transmission<br>
6. EMI:Electromagnetic Interference、Shielding Effectiveness<br>

**二、COMSOL建模基礎步驟<br>**
1. Model Wizard：建立模型<br>
2. Global Definitions：設定全域參數<br>
3. Geometry：建立幾何結構<br>
4. Materials：設定材料<br>
5. Physics：設定物理場<br>
6. Mesh：建立網格<br>
7. Study：設定求解方式<br>
8. Results：分析模擬結果<br>
9. 顏色和動畫

**三、COMSOL LiveLink for MATLAB**  (MATLAB使用前可以確認所屬學校或機構有沒有買)<br>
1. 先打開命令提示字元<br>
2. 輸入 cd/d"你的COMSOL安裝路徑\Multiphysics\bin\win64"，要選最原始的路徑，不是桌面捷徑的路徑<br>
*第一次啟動可能會要你設定使用者名稱和密碼，隨便設一組並記住。
3. 再輸入 comsolmphserver.exe<br>
4. 在MATLAB中的Command Window中輸入 addpath('你的COMSOL安裝路徑\Multiphysics\mli');mphstart<br>
*如果前面有設密碼，連線時會問你，輸入同一組。接著輸入 mphversion，有顯示 COMSOL 版本就成功，之後就能 Run 腳本。<br>

完成後大概會長這樣
<p align="center">
  <img src="https://github.com/user-attachments/assets/4605fa92-5730-4c91-8389-4cf4a89ed634" width="600">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/515ac975-295a-4065-a419-15ec0191af14" width="600">
</p>


提醒:完成連接後命令提示字元視窗不要關，不然會終止 Server，使 MATLAB 無法繼續連線。

**四、使用文獻資料練習模擬<br>**
文獻一:EMI shielding leadless package solution for automotive - Journal of Advanced Joining Processes, 2022<br>
這篇是在說改良一種QFN，Microleadframe®(MLF®)，名為routable MLF (rtMLF®)，可以更有效減少EMI<br>


想要使用COMSOL模擬出圖二的Normal QFN，該如何下手呢?<br>
列出部分參數(更完整的參數可以直接請AI抓再檢查就好):<br>
1. Geometry Parameters<br>
Package Body Size:8 × 8 mm	<br>
Die Size:4 × 2 mm<br>
Bond Wire Material:Gold (Au)<br>	
2. Material Properties<br>
EMC (Epoxy Molding Compound)<br>
以下數值為模擬時採用的假設值，並非已確認的論文原始數據。<br>
Relative Permittivity:3.7<br>
Relative Permeability:1	<br>
Electrical Conductivity:0 S/m<br>

3. Conformal Shielding Layer<br>
Material Structure: SUS–Cu–SUS<br>
SUS: Stainless Steel（不鏽鋼）<br>
Cu: Copper（銅）<br>
屏蔽層由三層材料組成，依序為不鏽鋼、銅、不鏽鋼。<br>

4. Simulation Conditions<br>
Parameter	Value<br>
Operating Frequency	5 GHz<br>
Noise Source Distance from Package Top	0.3 mm<br>
Noise Source Distance from Package Side	3.0 mm<br>

都找完之後就可以打開COMSOL，結果如下:<br>
自己動手製作發現非常費時，就算是簡單構造的封裝建模，假設有32支lead frame就夠痛苦了，要先建好一支、複製一排、使用鏡射到對面，其中還要確認座標正確、材料對的上。  
可能我接觸時間少對操作不熟悉，也許有更快的方式。  
附圖是我改用AI+MATLAB前的成果，少的可憐。  
<p align="center">
  <img src="https://github.com/user-attachments/assets/ad6946ef-aadf-4a42-bf78-defd8ad1ba62" width="600">
</p>


文獻二:Wide-range soft anisotropic thermistor with a direct wireless radio frequency interface - Nature communication, 2024  <br>
這篇試著直接用MATLAB，然後學習在MATLAB端做調整

  
**五、錯誤紀錄&解決方法&功能**
1. 鏡射
2. 複製

