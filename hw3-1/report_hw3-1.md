# 資料分析 HW3-1

----

## How did you preprocess this dataset 

在最開始時，我將所有資料直接餵進去 logistic regression 的 model，發現結果很糟，全部都是猜上升

猜測說，有沒有可能股票的起始價格不重要，
重要的是當中的漲跌，
因此將 `Close Price`、`High Price`、 `Low Price` 減去 `Open Price`，
看一天內的數值變化，分佈圖如下
- **High - Open** 與 **Close - Open**
    當天的 High 與 Open 之間的差距越大，越有可能是上漲
    ![](https://i.imgur.com/zkShk9j.png)
- **Open - Low** 與 **Close - Open**
    當 Low  與 Open 之間的差距越大，越有可能是下跌
    ![](https://i.imgur.com/4ODOnDS.png)

因此將資料拆成
- **High - Open**
    High Price 與 Open Price 之間的差值
- **Open - Low**
    Low Price 與 Open Price 之間的差值
- **Close - Open**
    Close Price 與 Open Price 之間的差值
    
----

## Which classifier reaches the highest classification accuracy in this dataset ?

在這次的作業中我使用的 classfier 有
- Logistic Regression
- Desicition Tree / Random Forest
- Neural Network

分別的正確率為

**Validation Set**:
- Logistic Regression: 0.93
- Desicition Tree: 0.93
- Random Forest: 0.93
- Neural Network: 0.89~0.92

**Test Set**:
- Logistic Regression: 0.82
- Desicition Tree: 0.82
- Random Forest: 0.82
- Neural Network: 0.83

我覺得 **Neural Network** 表現的應該比較好一點

### Why ?

觀察了一下每個 model 的 confusion matrix，
其實表現的都算平均
![](https://i.imgur.com/6JOJWDX.jpg)

但是若把預測結果給畫出來，會發現 decision tree / random forest / logistic regression 都會大致以 'Close - Open' = 0 為分界預測
(綠色為正確, 紅色為 FP, 藍色為 FN)

![](https://i.imgur.com/zCnmoAD.png)

但是 Neural Network 很明顯會抓到一些其他 feature
![](https://i.imgur.com/6Ucys54.png)

### Can this result remain if the dataset is different ?
我覺得若是不同區段的資料，Neural Network 或許可以，
因為他有抓到不同的 feature ，或許這就是在不同天中，判斷是否是上漲或下跌的部分

----

## How did you improve your classifiers ?
