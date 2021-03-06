# Patronus
## 製品概要
### テレオペ Tech

### 背景（製品開発のきっかけ、課題等）

#### アイデアの背景

自分が機械音痴の母親にリモートで何かを教えないといけないときに，厄介に思うことがあり，それを解決できるようなアプリケーションを作れないかと思ったため．

#### 技術的背景

最近，Electronを触る機会が多く，Webの技術でドコまでPCの作業をハックできるかを試してみたかった．

### 製品説明（具体的な製品の説明）

Patronus(守護霊)はリモートで会話をしながらの指示出し(テレオペ)を支援するアプリケーションです．
PC上での操作をリモートで指示するとき，指導者には作業者の画面を見せることで，作業者が正しい操作をしているかを確認できます．
作業者の画面には指導者のWebカメラの映像をうっすら透過して映すことで，作業者は指導者の顔をみて会話をしながら安心して指示を受けられます．
指導者はWebカメラの映像を使って自分の指で画面上の位置を相手に示すことができます．

### 特長
####1. ビデオ通話と画面共有のいいとこどり
####2. 顔を見ながら安心して指示を受けられる
####3. 共有したい情報をすぐに見せられる

### 解決出来ること

Patronusは従来の電話やSkypeでのオペレーティングの問題点を解決します．  

従来の電話やskypeでのオペレーティングでは
* 指導者が作業者の画面を確認できない．
* 指導者が作業者の画面上の特定の位置を作業者に伝えられない．
* 作業者は指導者の顔を確認できないため不安．
* 作業者の画面を共有すると，指導者は自分の画面上にある情報を作業者に見せられない．
と言った両者にとっての問題点があります．

Patronusではこれらの問題点を **同時に** 解決します．

Patronusでは，
* 指導者の画面には作業者の画面とその全面に自分のWebカメラ映像を表示します．
* 作業者の画面には指導者のWebカメラ映像が透過して表示されるため，相手の顔，画面上で指を指した位置を確認しながら作業できます．
* 簡単な操作でに共有のウィンドウを両者の画面上に表示し，同一のWebコンテンツを共有します．またウィンドウの位置も両者で同期します．


### 今後の展望
今後は1対1だけではなく，**1対多**の作業画面・Webカメラ映像の共有を行えるようにすることで以下のような利用に展開できる．

#### 在宅勤務者の会議参加やリモート指導
在宅勤務者の業務にはリモートでの作業内容の共有は必要．Patronusでは，在宅であっても相手の顔を確認しながらの指導を実現できる．  
テキストベースのコミュニケーションツールでは指示者が見てほしいページのリンクを渡すだけどこが重要か見てほしいかわからないため，Patronusの共有ウィンドウ機能は有効

#### プログラミング学習の低年齢化
指導者は一度に多くの相手に指導する必要があります．学習経験の浅い相手に対しては指導者が直接指導できることが好まれるため，Webカメラ映像のオーバーレイ技術によるオペレーションが応用が効く．

#### 企業の採用面接やリモートの説明会などへの応用
企業の採用面接では説明者の表情を確認できることは重要であり，Patronusではそれに加えて共有したい情報(採用ページ，プロダクト)などを相手に見せることができる．

### 注力したこと（こだわり等）
* Patronusのインタフェースは基本的に指示者が操作することを意識しています。非支持者は基本的に機械音痴を想定しているので操作をなるべくしないように工夫しています．
* ビデオカメラの映像を画面の一部に出すのではなく，全画面に透過して映すことで，視覚的な指示や作業領域の確保などを実現している．

## 開発技術
### 活用した外部技術

#### フレームワーク・ライブラリ・モジュール
##### skyway
Webカメラ映像，作業画面をWebRTCで通信した．．Electronで表示したhtmlでskywayを使用のために様々な手法を試し，なんとかペアリングなどをできるようにし，機能の実現を行った．
##### Electron
Electronでは画面の表示レイヤーや背景やマウスイベントの透過をできるため，それらの機能を最大限に活かしたWebカメラ映像の表示を行った．
##### socket.io
WebRTCで通信しないシステム上の情報を各ユーザごとで通信するために利用した．socket.ioのRoomを利用したペアリングや，共有ウィンドウの管理に利用した．

#### デバイス
* Webカメラ付きのPC(指導者)
* PC(作業者)

### 独自技術
#### 期間中に開発した独自機能・技術
* Webカメラ映像とデスクトップのスクリーン映像をオーバーレイして表示するインタフェース(Electron, skywayの協調利用)
* Webカメラ映像を画面の最前面で表示し，マウスイベントを透過することで通常のPC作業を可能にする(Electronの利用工夫)
* 共有Webコンテンツとそのウィンドウ位置のリアルタイムな同期(socket.ioによる即時的な双方向情報共有)
