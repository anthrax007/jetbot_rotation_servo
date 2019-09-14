# jetbot_rotation_servo
for PCA9685,GWS S35

サーボは個体差があり、デフォルトの値だと停止しない場合がある。その場合は値の調整を行う。

１.動作確認
　jupyter notebookのbasic motionでrobot.stop()を実行

２. 停止しない場合はnotebookの値を変更
/home/jetbot/jetbot/jetbot/motor.pyの以下の値を変える。

PWM_STOP_CH0 = 306
PWM_STOP_CH1 = 306
→ 最初は5程度づつ変えてみる。 

CHx→PCA9685ボードのCHxに繋いだサーボ
S35 STDと書いてあるラベルを正面にする。

値を増やすと時計回りに加速。
値を減らすと反時計回りに加速。
サーボは左右逆向きについているのでよく確認する。

３.実際に動作させるソースを上書きする。
sudo cp /home/jetbot/jetbot/jetbot/motor.py /usr/local/lib/python3.6/dist-packages/jetbot-0.3.0-py3.6.egg/jetbot/.

４.再スタート
   メニューのkernel→restart kernelでbasic motionを終了する。再度１.から実施し、更新したプログラムを再度読み込ませる。STOPでタイヤが停止するようになるまで調整する。
