# Link
- [はじめに](#はじめに)
- [概要](#概要)
- [はじめに](#はじめに)
- [動作環境](#動作環境)
- [使用ライブラリ](#使用ライブラリ)
- [留意点](#留意点)

# はじめに
 
本プログラムは、トロンボーンのスライド菅の伸縮を画像処理によって検出できるようになることを目的として作成しています。
現時点では未完成であり、根本的な手法自体に見直しが必要と感じる箇所がいくつかあります。
また、もともとはPythonで書いていましたが、御社へ提出するにあたりKotolinで書き直すことを目標に準備いたしました。
よろしくお願いいたします。
 
# 概要
 
単眼深度推定ネットワークを用いて、スライド菅の先端からベルの前面までの距離を計測する。
使用時には以下の図のように、スマホの画面が見えるようにスライド菅の先端に取り付け、アプリを動作させる。
![トロンボーン](https://user-images.githubusercontent.com/58971155/173251115-979d5cfe-8034-477f-9355-83fd655ca599.png)
取り付けには結束バンドや紐などを用いることを想定している。
 
# 動作環境
 
以下の環境で動作確認を行なった。
 
* デバイス：Android 11
* 言語：Kotolin 17.0
* 開発環境：Android Studio 2021.2.15 for windows
* 開発PCのOS：Windows10 
 
# 使用ライブラリ
 
* TensorflowLite
モバイル版として実装するため、Tendorflowの軽量版であるtendorflowLite(TFLite)を利用する。

* MiDASモデル
単眼深度推定をするにあたり、Pythonで使用していたMannequiChallengeがTensorflowLiteでは利用できないため、MiDASモデルを使用して深度推定を行う。
なお、プログラムは以下のものを使用している。
[MiDAS github](https://github.com/shubham0204/Realtime_MiDaS_Depth_Estimation_Android)

* OpenCV4.5.5
深層学習による深度推定では挙動が不安定であったため、色・円・エッジなどでの検出も併用することを目的に導入した。
しかし、OpenCVの関数を使用しようとするとアプリがクラッシュしてしまうため、現在は使用していない。
OpenCVの処理が重いのか、ライフサイクルの都合なのか、理解不足の点が多いため今後勉強していく予定である。
OpenCVは以下からインストールした。
[OpenCV URL](https://opencv.org/releases/)
 
# 使い方

1. Android端末からアクセスして、apkファイルをダウンロードし、実行する。
2. <p>起動画面上にある2つのボタンのうち<img src="https://user-images.githubusercontent.com/58971155/173270557-0488390c-b811-4749-8fc5-3d0b2fde547e.PNG" width="10px">はカメラの向きを変更、<img src="https://user-images.githubusercontent.com/58971155/173270652-dfdcd4f3-3a7d-47e2-8ebe-255af4b36c9f.PNG" width="30px">は深度推定用のボタンである。</p>
3. <p><img src="https://user-images.githubusercontent.com/58971155/173270652-dfdcd4f3-3a7d-47e2-8ebe-255af4b36c9f.PNG" width="30px">をタップすると深度マップと数字が表示される。</p>
4. 画像中の物体に対して距離が変化すると、画面上部の数字も変化する（未実装）。
 
# 留意点

* コンセプトがスライド菅の先端に取り付けるというものなので、構造上の都合から画面の向きは横向き固定としている。
* [はじめに](#はじめに)で説明したように、肝心の計測した距離の出力がまだ実装できていない。

# 作成者
 
* 氏名：山林央樹
* 所属：豊橋技術科学大学大学院 情報・知能工学専攻 修士2年
* E-mail：yamabayashi.hiroki.zp@tut.jp
"# Trombone-Application-fuller-" 
