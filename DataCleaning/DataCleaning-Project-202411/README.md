Step 1: Handling missing values
Step 2: Scaling and normalization
Step 3: Parsing dates
Step 4: Character encodings
Step 5: Inconsistent Data Entry


Step 1: Handling missing values(dataset：NFL)

    1.Calculate missing value
        isnull().sum()
    
    2.Figure missing value
       (1)drop all null
            dropna()
            dropna(axis=1)  #axis=0 delete column、axis=1 delete row
            
       (2)fill in
            fillna(0)
            fillna(method ='bfill', axis=0),fillna(0)  #bfill = backward fill 填入後面一個有效值

Step 2: Scaling and normalization(dataset：KS)

    Scaling 標準化
        
        ● scale the range, not distribution shape 不改變分布形狀，改變縮放比例
            EX：original data, $0 to $10000000 ->  0-1
        ● the extreme values could lead to  model instablility 具極端值可能導致model不穩定

        method
        ●Min-Max Scaling
            將數據縮放到固定範圍（如 0 到 1）。

    normalization 正規化

        ●Change the distribution, when important than absulte size 改變比例，當筆絕對數值重要時
           like distance, unit. 不同單位
           EX:   
                    price  g
                A   300    500
                B   450    600
 
                1.sum
                    A = 300 + 500 = 800
                    B = 450 + 600 = 1050
                
                2.normalization
                    A = price: 300/800 = 0.375   
                          g:   500/800 = 0.625

                    B = price: 450/1050 ≈ 0.428
                          g:   600/1050 ≈ 0.571  
                
                => A has lower price, higer g. 
        method
        ● Box-Cox Transformation.
            change to normal disibution, only use for positive values.  轉變為常態分佈，只適用於正值