2018/06/20
baxter_handの使い方を学んだ
hand_controlにstring型の'{"command":"activate-deactivate"or"move","hand":"r-l","angle":"[９個の配列]"}'のデータを送るとstring型のデータが返ってくる
今後腕の動かし方を学んでようやく動かせるようになる
カメラ(kinect)は３次元的に見ることができるが扱いが難しいらしい

2018/06/21
* baxter_handのプログラムをみた
  hand_control_client,serverとhand_sys
* エラー？でcontrol_serverが動かなかった
  retry to connect /dev/ttyUSB0 ID:1がいっぱい
  **実行手順
　  共有PC:baxter.sh
  　      sudo startup.sh
          source catkin_ws/devel/setup.bash
          rosrun baxrer_hand hand_control_server
        上のエラー
  ** /dev/上にttyUSB0とttyUSB1はあった
    ls -l /dev/ttyUSB*
    crw-rw---- 1 root dialout 188, 0 Jun 21 19:54 /dev/ttyUSB0
    crw-rw---- 1 root dialout 188, 1 Jun 21 19:52 /dev/ttyUSB0
  ** chmod 777 をttyUSB0とUSB1をしても結果は同じだった
** 戸田PC上では実行ファイル(serverとclient)が見つからなかった(多分上戸は違う設定ミス)
  toda@LT15-L09:~/catkin_ws/src/baxter_hand/scripts$ rosrun baxter_hand hand_control_server.py
  [rosrun] Couldn't find executable named hand_control_server.py below /home/toda/catkin_ws/src/baxter_hand
  [rosrun] Found the following, but they're either not files,
  [rosrun] or not executable:
  [rosrun]   /home/toda/catkin_ws/src/baxter_hand/scripts/hand_control_server.py
**baxter_toolのtuck_armは普通に動いた

2018/06/22
* ハンドの電源を入れましょう

2018/06/26
* 動かす手順
　* hand_control_clientとhand_control_serverを実行する何方ともbaxter.shの実行が必要
  * baxter.sh後にもう一度source catkin_ws/devel/setup.bash  の必要あり
* json で文字列を扱うとき？{}で囲う必要あり
* 横にしないと紙をうまくつかめない
* メモgitで管理したい
