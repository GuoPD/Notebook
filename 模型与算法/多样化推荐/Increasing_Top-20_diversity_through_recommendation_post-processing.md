计算前20推荐选项的ILD值，具体方法为：
在计算时，每次去除一个选项，计算其余19项的ILD。
如此得到20个ILD@19，重新排序

## Method  1

&emsp;&emsp;从后20个Candidates分别替换前20个，计算ILD值，得到400个ILD的分值。最后，选择最高ILD值的前20推荐给用户5

## Method 2

&emsp;&emsp;使用$a*avgPR+b*nILD$替换掉ILD，均衡准确率与多样性

## ILD计算方式
&emsp;&emsp;
1. 将词项目数\词频总和
2. 关键词项目数\关键词词频总和
3. 关键词加权

