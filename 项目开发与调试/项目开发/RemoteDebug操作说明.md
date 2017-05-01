IntelliJ配置，以开发机为10.101.2.67为例：
> **run** - **edit configuration** - **添加remote** - 设置host为**10.101.2.67**

port为8809，运行即可

ssh services@10.101.2.67

/home/services/video2video/bin

user2video测试用例：

>http://10.101.2.67:8600/user2video/recommend?userid=119368279&num=100&history_rpc_address=10.101.1.170:9888&batch=44&src=homepage&bucket=u2vusercf-uc&debug=1

video2video测试用例:

>http://10.101.2.67:8100/video2video/recommend?docid=V_00d1uw9N&num=30&debug=true

video2video线上版本(可通过Jekins查看)

>http://10.103.17.18:8100/video2video/recommend?docid=V_00d1uw9N&num=30&debug=true
