# COMSOL Learning Journey
[一、背景知識](#bg)<br>
[二、COMSOL建模基礎步驟](#step)<br>
[三、COMSOL LiveLink for MATLAB](#livelink)<br>
[四、使用文獻資料練習模擬](#practice)<br>
[五、小功能(建議先看)](#errors)


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
9. Others:顏色和動畫
    
<a id="livelink"></a>
**三、COMSOL LiveLink for MATLAB** (MATLAB使用前可以確認所屬學校或機構有沒有買)<br>
&emsp;&emsp;COMSOL除了連MATLAB也可以連其他軟體，依需求而定。<br>
&emsp;&emsp;方法一:<br>
1. 先打開命令提示字元<br>
2. 輸入 cd/d"你的COMSOL安裝路徑\Multiphysics\bin\win64"<br>
3. 再輸入 comsolmphserver.exe<br>
*第一次啟動可能會要你設定使用者名稱和密碼，隨便設一組並記住。
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
&emsp;&emsp;方法二(推薦):<br>
&emsp;&emsp;直接在Windows的「開始」選單搜尋 COMSOL Multiphysics 6.4 with MATLAB，加捷徑到桌面就不用每次都連線。<br>
<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/00e303cb-a66c-463a-808d-99332097615e" width="450">
</p><br>
<p align="center">



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
<br>
<br>

<a id="errors"></a>
**五、小功能**<br>
&emsp;很基礎的小功能，但可以節省一點時間<br>
1. 如果是小Block外面有一個Block罩住，要選取小Block就滾動滑鼠滾輪，不是用點擊的，會點到天荒地老都選不到。這有點愚蠢但困擾我半小時。 <br>
2. 滑鼠長按左鍵轉視角、長按右鍵平移<br>
3. 透明<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/9490a2b2-1b6a-4254-9304-c7b18e56caf4" width="500">
</p> <br>
<p align="center">
  現在圖片中顯示的是設置的空氣域，呈現一整個實心方塊，按透明(按紅色圈圈處)之後就可以看見裡面的東西<br>
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/485507c5-b33e-48c2-8764-f90b39d7fa7f" width="500">
</p> <br>
<p align="center">
  像這樣
</p><br>

4. 重複<br>
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/726664ca-7c1d-47f0-a145-402dc7499b46" width="500">
</p> <br>
<p align="center">
  我拿blk22做示範，我想在它的右邊多加一個焊料小塊，用重複的方式只需要改一個，其他參數都一樣不用再打一次
</p><br>
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/137069b8-c8d9-4d73-a841-7a4ce7f1bd88" width="500">
</p> <br>
<p align="center">
  點完會出現新的blk23，這時候我們把x軸的座標加上間距(0.5)，調成-0.25<br>
  p.s.我在建模基礎步驟表示以中心作為起點比較好算座標，但在這邊從角落作為起點會簡單不少(小塊是從角落開始排)
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/b48b443c-c703-4d97-81bc-de78eb0f546f" width="500">
</p> <br>
<p align="center">
  調完座標按"建立選定的"，就完成了<br>
  建議把名稱改成小塊4，比較不會搞混
</p><br>

5. 群組<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/5d07ff58-07e6-45e1-bf57-acbe5174a474" width="500">
</p> <br>
<p align="center">
  一堆小塊看了很雜，可以把它們整理到一個群組裡面<br>
  Geometry 1 上點右鍵找"節點群組"
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/6f915330-b40c-4298-b3ce-bbcc16ffa5ed" width="500">
</p> <br>
<p align="center">
  長按Ctrl點選想抓的東西，再點右鍵把它們移到群組，這樣就有乾淨介面了<br>
</p><br>

6. 鏡射<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/ab92520a-0d02-4635-acb1-e12fb3fbc94e" width="500">
</p> <br>
<p align="center">
  接下來我想要die pad y軸方向兩側都有小塊，所以使用鏡射功能，同樣的事不用做兩遍
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/7f18e014-78c7-478f-98a5-281c1a85650f" width="500">
</p> <br>
<p align="center">
  在圖形處把要參加鏡射的小塊點一點，記得調鏡射的法線向量，調完按"建立選定的"<br>
  重要!要勾"保留輸入文件"，不然只是整排被移到對面而已
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/ad51aa96-eda9-408a-92c6-8fb8ac8821da" width="500">
</p> <br>
<p align="center">
  完成圖
</p><br>

7. 資料庫Application libraries<br>
&emsp;可以從資料庫中學習各種功能，並做建模參考
<p align="center">
  <img src="https://github.com/user-attachments/assets/e4c8383d-d98b-46b6-aa95-ca6cad0318e4" width="500">
</p> <br>
<p align="center">
  在"檔案"處找到"應用資料庫"
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/f5a3a3d2-edbd-4849-8b9a-808f6c72540e" height="400">
</p> <br>
<p align="center">
  會出現各類型已經建好的模型，可以直接選或是搜尋
</p><br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/80e45004-68f3-4efc-855f-894963c989e2" width="500">
</p> <br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/07653803-d628-469e-853a-8dd3043ea715" width="500">
</p> <br>
<p align="center">
  可以從左邊的資訊欄學到很多
</p><br>

8. 剖面圖<br>
<p align="center">
  <img src="https://github.com/user-attachments/assets/9180eead-2752-43a2-85d5-8707d74fddb1" height="300" />
  <img src="https://github.com/user-attachments/assets/5bfddd50-19ec-439e-8b47-f0bbc16232ef" height="300" />
</p>
<p align="center">
  原本是像左圖這樣，希望變成像右圖一樣顯示剖面電場影響範圍
</p><br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/89a9413d-9177-49f2-9b9f-69c5dd911752" width="500">
</p> <br>

<p align="center">
  需要做以下幾件事:<br>
  結果→資料集點右鍵→研究 1/解 1(Solution)<br>
  結果→資料集點右鍵→切面(Cut Plane)。在切面的設定要切哪裡。<br>
  結果點右鍵→3D繪圖群組→設定中的資料集要選"切面"<br>
  3D繪圖群組點右鍵→表面→設定中的資料集選"來自上階"就行<br>
  上述是基本要選的部分，至於"表面"的色彩範圍和參數可以自行決定。
</p><br>
