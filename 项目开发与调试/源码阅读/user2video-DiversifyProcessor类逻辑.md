## FastDiversifyProcessor

### 私有类
1. ItemWithScore
存放预测项目、分值，以及其对应的多样化特征项。

2. DiversityFeatureTerm
多样化涉及的特征项目

----------


### 运行逻辑：
1. 构建堆heap与索引表termInvertedTable。初始视频分值设为$\frac{1}{1+e^{-x}}$。
2. 从堆中推出一个得分最高项bestChoice
3. 根据DiversityFeatureType将堆中具有相同DiversityFeature的Candidates打分乘以衰退系数
4. 从termInvertedTable中将bestChoice项目移除
5. 重新调整堆，回到2，直到堆中所有元素全部推出

----------

## FastDiversifyV2Processor

与FastDiversifyProcessor运行逻辑类似，在buildInvertedTableAndHeap时，考虑到的DiversityFeature为Category, Subcategory, tag和Duration
DurationTime按照时间划分为4类：$du1[0,60],du2[60,240],du3[240,360],du4[360,+\infty)
