# HTMLTestRunnerScreenshot
 HTMLTestRunner with Screenshot（url or base64）
 
 说明
 =======
在HTMLTestRunnerCN基础上添加截图显示功能，截图可以使用url链接方式或base64编码模式直接加载到html文件中（会导致html文件变大，但是单html文件就可已显示图片，不会因为图片路径改变导致图片无法显示）<br>
获取图片原理使用为根据控制台中的print输出的内容判断截图路径及文件名，其中“../screenshots/”为截图所在路径需替换成自己的截图路径；“截图：”为提取关键字，需调整为截图函数中print内的内容；截图函数的print内需加入“ end='' ”不然输出路径将带有'/n'--换行符导致报错<br>
HTMLTestRunnerCN作者地址：https://github.com/findyou/HTMLTestRunnerCN/tree/dev<br>
HTMLTestRunne作者地址：http://tungwaiyip.info/software/HTMLTestRunner.html<br>

###### 如何使用
```python
首先进行设置调整
1.首先在截图函数中添加print，print内容为“关键字+截图路径及文件名” 结尾需增加“,end=''”参数，不然输出路径将带有'/n'换行符，导致程序报错    
    例如：print('截图:'+'%s %s.png' % (module, now_time), end='')
          
2.在“def _generate_report_test(self, rows, cid, tid, n, t, o, e):”函数中查找base64_status变量并赋bool值，默认为True。     
    True 为启用base64模式 
    False 为启用url模式
    注意：启用base64模式后图片将由base64编码保存至html文件中，如果测试用例较多可能导致测试报告变得比较大，但是html文件脱离截图文件夹后依然可以正常查看图片
          
3.调整image_url变量中关键字起始字符数；例如：“截图：”字符数为3，那么为'unum + 3'，如关键字为'screenshot'字符数为10，那么3就需要改成10

4.截图图片需为png格式

5.其它使用方法同HTMLTestRunnerCN与HTMLtestRrunner
```



        
###### 更新历史
```python
Version 0.8.4 -CaptainJi 20200429
* 报告页面增加截图
* 可选使用url方式添加图片或base64方式添加图片
                  
Version 0.8.3 -Findyou 20171206
* BUG fixed :错误的测试用例没有统计与显示
* BUG fixed :当PASS的测试用例有print内容时，通过按钮显示为红色
* 表格背景颜色根据用例结果显示颜色，优先级： 错误(黄色)>失败(红色)>通过(绿色)
* 合并文为HTMLTestRunner*N.py 同时支持python2,python3

Version 0.8.2.2 -Findyou
* HTMLTestRunnerEN.py 支持 python3.x
* HTMLTestRunnerEN.py 支持 python2.x

Version 0.8.2.1 -Findyou
* 支持中文，汉化
* 调整样式，美化（需要连入网络，使用的百度的Bootstrap.js）
* 增加 通过分类显示、测试人员、通过率的展示
* 优化“详细”与“收起”状态的变换
* 增加返回顶部的锚点

Version 0.8.2
* Show output inline instead of popup window (Viorel Lupu).

Version in 0.8.1
* Validated XHTML (Wolfgang Borgert).
* Added description of test classes and test cases.

Version in 0.8.0
* Define Template_mixin class for customization.
* Workaround a IE 6 bug that it does not treat <script> block as CDATA.

Version in 0.7.1
* Back port to Python 2.3 (Frank Horowitz).
* Fix missing scroll bars in detail log (Podi).
```
