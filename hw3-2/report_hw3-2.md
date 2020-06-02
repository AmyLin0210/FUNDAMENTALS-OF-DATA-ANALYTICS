# FDA HW3-2
 
----
 
## Choose a dataset
我選擇了 **Online Shoppers Purchasing Intention Dataset**

----

## Analyze the data 
**觀察各個類別的數量**
![](https://i.imgur.com/MjA0k3P.png)
![](https://i.imgur.com/ymBKVJh.png)

**比較不同類別的購買成功率**
(y軸 = 該類別購買數/該類別全部人數)
![](https://i.imgur.com/OxoCkeR.png)
![](https://i.imgur.com/ugTQ1Yo.png)

從由於每個資料欄位的 category 數量相差很大，所以以下分析指針對數量較多的，數量少的先暫時視為 outlayer

- **OperationSystem** 
    編號 3 的購買成功率明顯較低，故 operation system 有可能有影響
- **Browser**、**Region** 
    感覺影響較小
- **TrafficType**、**Month**、**SpecialDay**
    可以明顯地看出每個 category 成功率有很大的區別
- **VisitorType**
    Returing Visitor 有比較高的購買成功率
       
**觀察各個數值的數量**
y 軸為累計的比例，
`藍色`：累計成功率
`黃色`：累計失敗率
`綠色`：累計數量比例
![](https://i.imgur.com/cSvJI9Z.png)
![](https://i.imgur.com/QPwGzqo.png)

----

## Define a reasonable problem and predict the results

**Reasonable problem**
由各種數據去判斷使用者是否會購買

**predict the result**
使用 **LogisticRegression** 
- **Input** 
    - OperatingSystems
    - Browser
    - Region 
    - TrafficType
    - SpecialDay
    - Administrative_Duration
    - Informational_Duration 
    - ProductRelated 
    - ProductRelated_Duration
    - BounceRates
    - ExitRates
    - PageValues
- **Result**
    - accuracy: 0.88
    - confusion matrix:
        ![](https://i.imgur.com/Q9rZWek.png)


----









