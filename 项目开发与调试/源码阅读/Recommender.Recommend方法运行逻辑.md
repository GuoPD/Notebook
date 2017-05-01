1. 由RetrieveKeyBuilder构建不同的RetrieveKeys
2. 构建keyBasedRetriever，输入retrieveKeys和retrieveValidator返回retrieveKeyQueueMap，存放召回的内容Item数据
3. 由RetrievePostProcessor处理检索结果
4. 由Blender进行了blend，生成Candidates
5. Merge candidates: 将KeysItem集合转换为ID->KeysItem的Map
6. FeaturesDumper产生随机needDump
7. preProcessor
8. Predict调用算法（本地，远程）进行打分预测
9. Postprecess多样化
