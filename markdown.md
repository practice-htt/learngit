## <span id = "目录">目录</span>

+ 最近邻搜索基础
    1. [最近邻搜索简介和算法](#一)
    2. [数据表示和距离衡量标准的重要性](#二)
+ 快速最近邻搜索
    4. [KD-树：中低维和近似最近邻](#KD-tree)
    5. [LSH：高维上的近似最近邻](#LSH)
+ 在Wikipedia上的数值实验
    3. [Programming Assignment1：不同的数据表示和距离标准](#Assignment1)
    6. [Programming Assignment2：LSH](#Assignment2)
    
## <span id = "一">一、最近邻搜索简介和算法</span>

***
** 1-最近邻算法 (1-NN algorithm) **
***
** 输入：** 当前阅读的文章：$X_q$
            文集：$X_1,X_2,\cdots,X_N$   
** 输出：** 最相似的文章：$X^{NN}$  
其中，$X^{NN}$ = arg$\min\limits_{i}$ distance$(X_i,X_q)$  
初始化 ** Dist2NN = $\infty, X^{NN}$ = $\varnothing$ **  
For $i=1,2,\cdots,N$  
　　计算：$\delta = distance(X_i,X_q)$  
    if $\delta<$**Dist2NN**  
    　　令 $X^{NN}=X_i$  
          　　令** Dist2NN**=$\delta$  
Return 最相似文章：$X^{NN}$
***
***
** K-最近邻算法 (K-NN algorithm) **
***  
** 输入：** 当前阅读的文章：$X_q$
             文集：$X_1,X_2,\cdots,X_N$   
** 输出：** 最相似的文章列表(list)：$X^{NN}$  
其中，$X^{NN}$ = $\{X^{NN_1},\cdots,X^{NN_k}\}$，对所有不在$X^{NN}$中的$X_i$，都有$distance(X_i,X_q)\ge\max\limits_{X^{NN_j},j=1,\cdots,k}distance(X^{NN_j},X_q)$  
初始化 ** Dist2KNN ** = sort$(\delta_1,\cdots,\delta_k)$，$X^{NN}=sort(X_1,\cdots,X_k)$     
For $i=k+1,\cdots,N$  
　　计算：$\delta = distance(X_i,X_q)$  
    if $\delta<$**Dist2KNN**[K]  
    　　找到**j**使得**Dist2KNN**[j]>$\delta>$**Dist2KNN**[j-1]  
    　　删除最远的元素并且移动列表：  
        　　　　$X^{NN}[j+1:K]=X^{NN}[j:K-1]$  
            　　**Dist2KNN**[j+1:K]=Dist2KNN[j:K-1]  
        　　   令 **Dist2KNN**[j]=$\delta$，$X^{NN}$[j]=$X_i$    
Return K篇最相似的文章：$X^{NN}$  
***
## <span id = "二">二、数据表示和距离衡量标准的重要性</span>
