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

- **Data Preprocess**
將非數值資料轉化為數值
    - Month: ['Jan', 'Feb' ... , 'Dec'] -> 1 ~ 12 
    - Weekend: True: 1, False: 0
    - VisitorType: New: 0, Return: 1, Other: 2

- **Input** (全部資料都放進去)
    - Month
    - Weekend
    - VisitorType
    - OperatingSystems
    - Browser
    - Region 
    - TrafficType
    - SpecialDay
    - Administrative
    - Administrative_Duration
    - Informational
    - Informational_Duration 
    - ProductRelated 
    - ProductRelated_Duration
    - BounceRates
    - ExitRates
    - PageValues
- **Result**
    - LogisticRegression
        - train accuracy: 0.880575
        - test  accuracy: acc: 0.8844282
        - confusion matrix:
        ![](https://i.imgur.com/86rzmft.png)
    - RandomForest
        - train accuracy: 1.0
        - test  accuracy: acc: 0.903487
        - confusion matrix:
        ![](https://i.imgur.com/u8Mkymw.png)

----

## Explain how you improved your results step-by-step

#### Origin Result:
- LogisticRegression
    - train accuracy: 0.880575
    - test  accuracy: acc: 0.8844282
    - confusion matrix:
    ![](https://i.imgur.com/86rzmft.png)
- RandomForest
    - train accuracy: 1.0
    - test  accuracy: acc: 0.903487
    - confusion matrix:
    ![](https://i.imgur.com/u8Mkymw.png)

----

## imporvement 1
- **reason**
最開始我把所有資料都直接丟進 model ，當中可能有 noise
- **approaches**
嘗試著減少丟進去的資料，只丟影響較大的
- **imporvement**
    可以看到 Logistic Regression 的部分有變好一點
    - input:
        - Month
        - Weekend
        - VisitorType
        - BounceRates
        - ExitRates
        - PageValues
    - result
    ![](https://i.imgur.com/nQkq0hP.png)
    
----

### imporvement 2

- **reason**
random forest overfitting
- **approaches**
改變 model 的參數
    - max_leaf_nodes: 限制 leaf 的數量，不要使其分得太細
    - min_samples_split: 超過一定數量才能夠分 leaf，原因同上
- **imporvement**
可以看到 RandomForest 的 accuracy 增加了
    - input:
        - Month
        - Weekend
        - VisitorType
        - BounceRates
        - ExitRates
        - PageValues
    - result
    ![](https://i.imgur.com/dShnia0.png)

