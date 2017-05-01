ture   | weight |
|   :-:     |   :-:  |
| ch_score:gbdt | 0.1 |
| cos(rf_rel,rf_rel) | 1.5 |
|vd_qlt:up | 0.005 |
|vd_qlt:fav | 0.01 |
|vd_qlt:cmt | 1.00E-04 |
|cos(tkw,tkw) | 5 |
|vd_qlt:play | 5.00E-07 |
|avg(vd_sct,vd_sct) | 0.5 |
|cos(fromid,fromid) | 1 |
|cos(vd_ytags,vd_ytags) | 5 |
|cos(vd_ytags,tkw) | 2 |

在video2video中docid为**V_00pFn4tU**的推荐结果中只包含
**[ch_score:gbdt]**一项，且分值普遍偏小，不到**0.1**

其他测试用例中出现**[cos(tkw,tkw)]**，约为**0.8-0.9**，因此分值较大



通过模型追踪，只有cos(tkw,tkw)以及ch_score:gbdt在featurelist里面出现并使用
接下来的计划：
1、追踪一日数据，查看featurelist情况（调用API时间可能较长，数据量会较大）
2、看user2video中postprocesser里面的FastDiversify代码
