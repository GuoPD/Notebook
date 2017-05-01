## DiversifyDecayGenerator

&emsp;&emsp;用于生成个性化的Decay系数，featureTypeDecayMap和featureNameDecayMap
根据大类featureType和featureName分别进行折扣，防止同名特征衰减被二次计算
将两个Decay系数相乘得到最终的衰减系数

----------


## FastDiversifyProcessor
同user2video FastDiversifyProcessor

----------

## FastWindowDiversifyProcessor
设置windowSize，当筛出的Candidates数目超过windowSize时，对过度折扣的分数值进行恢复

----------

## FastPersonalizedWindowDiversifyProcessor
逻辑如FastWindowDiversifyProcessor，使用个性化的衰退参数对分数进行折扣

----------

## FastPinnedFromIdDiversifyProcessor

根据mashType(RetrieveKey)筛选fromid

