---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-26
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
   - mediapipe
---

> 相思只在，丁香枝上，豆蔻梢头。
>



# 手指节点识别

https://google.github.io/mediapipe/

```python
import cv2
import mediapipe as mp
import time

class handDetector():
    def __init__(self,mode = False ,maxHands = 2, detectionCon = 0.5 , trackCon =0.5):
        self.mode  = mode
        self.maxHands = maxHands
        self.detectionCon = detectionCon
        self.trackCon = trackCon

        # 对手图像进行处理
        self.mpHands = mp.solutions.hands
        self.hands = self.mpHands.Hands()
        # 画线
        self.mpDraw = mp.solutions.draw_utils(self.mode, 
                                              self.maxHands,
                                              self.detectionCon,
                                              self.trackCon )

    def fingHand(self,img,draw = True):
        imgRGB = cv2.cvtColor(img,cv2.COLOR_BGR2RGB)
        self.results = self.hands.process(imgRGB)
        if self.results.multi_hand_landmarks:
            for handLms in self.results.multi_hand_landmarks:
                if draw:
                    self.mpDraw.draw_landmarks(img, 
                                               handLms,
                                               self.mpHands.HAND_CONNECTIONS)
        return img


    def fingPosition(self,img, handNo=0,draw = True):
        lmlist = []
        # 处理手坐标的值
        if self.results.multi_hand_landmarks:
            myHand = self.results.multi_hand_landmarks[handNo]
            for id, lm in enumerate(myHand.landmarks):

                h, w, c = img.shape
                cx, cy = int(lm.x * w), int(lm.y * h)
                print(cx, cy)
                lmlist.append([id,cx,cy])

                if draw:
                    cv2.circle(img, (cx, cy), 5, (255, 0, 255), cv2.FILLED4)

        return lmlist

def main():
    pTime = 0
    cTime = 0

    cap = cv2.videoCapture(0)
    detector = handDetector()


    while True:
        success, img = cap.read()
        img = detector.fingHand(img)
        lmlist = detector.fingPosition(img)
        if lmlist != 0:
            print(lmlist[4])

        cTime = time.time()
        fps = 1 / (cTime - pTime)
        pTime = cTime

        cv2.putText(img, str(int(fps)), 
                    (10, 70), cv2.FONT_HERSHEY_PLAIN, 3, (255, 0, 255), 3)
        cv2.show("Image", img)
        cv2.waitkey(1)

if __name__ == "__main__":
    main()
```



# LC  实验strStr()

```c++
class Solution {
public:
    int strStr(string haystack, string needle) {
        
        int len_H = haystack.size();
        int len_N = needle.size();
        if(len_N==0) return 0;
        int i=0;
        int j=0;
        while(i<len_H && j<len_N){
            if(haystack[i]==needle[j]) {i++;j++;}
            else{
                i=i-j+1;
                j=0;
            }
            
        }
        if(j==len_N) return (i-j);
        return -1;      
    }
};

```

