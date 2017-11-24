

http://github.com
## eval suspend功能使用文档

### 启动任务
`pinoctl eval --force --suspend --group=ads-model-pinocloud ./demos/mnist.SR`
注意：
1 加入--suspend参数
2 将eval用data放入project指定位置，或者只需保证tty进入环境后PinoAI指定目录有eval用data即可
### tty
执行pinoctl eval后，执行pinoctl list，会刚才启动的eval任务，tty登录，会看到eval_client.sh脚本
![enter description here][1]
### 进行eval
  执行命令eval_client.sh 后加modelid参数
  `./eval_client.sh c51b3f8abaed11e7bfd840f2e9cf3a82`
   ![enter description here][2]
  正常情况下，会如图提示Run Eval in Background.Please check the eval log，表示启动eval成功，eval任务后台运行。可以在/export/App/training_platform/PinoModel/==real_log #800023==目录下看到每次eval的日志和结果目录，改目录的命名规则为`eval_log_${model_id}_时间`
![enter description here][3]


  [1]: ./images/1511507560818.jpg
  [2]: ./images/1511508184519.jpg
  [3]: ./images/1511508431875.jpg
  ### 回收eval
  多次eval完成后，请自行使用scp拷贝eval结果和日志，不要使用pinoctl release操作，release不会持久化real_log下的文件。