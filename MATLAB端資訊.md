雖然AI可以幫忙直接從論文之幫忙抓參數、直接建檔，但是如果要做一些調整，或是要做檢查，還是必須知道背後運作得邏輯和原理。
我想把一些MATLAB上常用的資訊放到這邊，學習的同時也做個紀錄。
一樣先以EMI shielding leadless package solution for automotive這篇著手，我在這之前從沒有碰過MATLAB、COMSOL所以會非常基礎。

下方是AI(Claude)給我的程式碼的開頭:
%% build_qfn_comsol.m
% 重建 Fig.5(a) Normal QFN 的 3D 幾何（含引腳陣列、打線）、材料與基本 EMW 設定
% 需求：COMSOL Multiphysics + LiveLink for MATLAB（RF 模組）
% 使用前先在終端機執行：comsol mphserver，或 MATLAB 內用 "COMSOL with MATLAB" 啟動
% 注意：論文只給本體 8x8 mm、晶片 4x2 mm、兩顆晶片、5 GHz、雜訊源位置；
%       其餘尺寸（標示「假設」）都是我自己設的，請依實際封裝修改。

clear; close all;
import com.comsol.model.*
import com.comsol.model.util.*

第一段學習到的資訊:
1. % 是 MATLAB 的註解符號。<br>
MATLAB 遇到 % 後，該行後面的文字不會被執行。
像是Python中的#
2. %% 像是這一段的標題、目標，像是我第一段扣掉註解的部分就只剩最下3行
3.
