# 給我一隻手，還你一張圖
### Give Me a Hand, Get a Picture

> 手勢互動遊戲｜Python 以 OpenCV 結合 cvzone 手勢辨識與影像處理技術

用手隔空擊中畫面上的目標，每命中一次，神秘人物照片的干擾就減少一些，**60 秒內揭開真正的圖吧**還能看到新年驚喜！

---

## ✨ 特色

-  **免接觸操作**：透過攝影機追蹤手部，肢體互動遊戲
-  **距離偵測**：由手掌關鍵點推算手與鏡頭的距離，夠近才算命中
-  **握拳暫停**：握拳即暫停，張手繼續，暫停時間不計入倒數
-  **漸進式揭圖**：照片被漩渦、馬賽克、胡椒鹽雜訊、高斯模糊層層遮蔽，隨得分逐一解除
-  **過關動畫**：完成揭圖後出現粒子愛心動畫與「Happy New Year!」

##  技術

| 項目 | 使用技術 |
|------|----------|
| 語言 | Python 3 |
| 影像擷取與繪製 | OpenCV |
| 手勢辨識 | cvzone HandTrackingModule（MediaPipe） |
| 距離估算 | NumPy 二次多項式擬合（polyfit） |
| 影像處理 | 漩渦變形、馬賽克、胡椒鹽雜訊、高斯模糊 |
| 動畫 | 心形參數方程式粒子動畫 |

##  執行方式

```bash
# 1. 安裝套件
pip install opencv-python cvzone mediapipe numpy

# 2. 修改 main.py 中的圖片路徑為你自己的照片
photo = cv2.imread(r"你的路徑/queen1.jpg", cv2.IMREAD_UNCHANGED)

# 3. 執行
python main.py
```

> 需要可用的攝影機。

## 🎮 操作

| 動作 | 功能 |
|------|------|
| 手靠近鏡頭（< 40 cm）並覆蓋目標圓圈 | 命中得分 |
| 握拳 ✊ | 暫停遊戲 |
| 張開手 🖐️ | 繼續遊戲 |
| `R` | 重新開始 |
| `Q` | 離開遊戲 |

##  揭曉圖片的流程

###遊戲規則說明
1.用手調整與螢幕的距離，讓視窗中的點消失
2.目標是在時間內還原出遊戲中圖片
###每命中一次得 1 分，照片依序解除干擾：

| 階段 | 得分 | 變化 |
|------|------|------|
| 0 → 1 | 1–9 | 馬賽克逐漸變細直到消失 |
| 1 → 2 | 10–15 | 高斯模糊逐漸減弱直到消失 |
| 2 → 3 | 16–22 | 胡椒鹽雜訊逐漸減少直到消失 |
| 3 | 23–30 | 漩渦逐漸解開，照片恢復清晰 |
| 🎉 過關 | > 30 | 愛心動畫 + Happy New Year! |

60 秒內未過關則顯示 Game Over、得分與完成階段。

##  遊戲畫面
## 遊戲畫面
<p align="center">
  <img width="49%" alt="遊戲中介面" src="https://github.com/user-attachments/assets/7f696727-0fa5-40bc-94ca-eee713478a86" />
  <img width="49%" alt="遊戲結束" src="https://github.com/user-attachments/assets/304c2f28-f3d4-415e-bf9d-d34d86369141" />
</p>
示範及解說影片連結：https://youtu.be/7qfffHcIes8?si=hSeGWEbxoibGFCMx

## 📁 檔案結構

```
├── main.py      # 遊戲主程式
├── queen1.jpg   # 神秘人物照片（可自行替換）
└── README.md
```
