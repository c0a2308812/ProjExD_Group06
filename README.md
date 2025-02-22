# こうかとんストライク

## 実行環境の必要条件
* python >= 3.10
* pygame >= 2.1

## ゲームの概要
モンスターストライクを参考に作ったゲームで、こうかとんを引っ張ってショットするゲーム

## ゲームの遊び方
* 敵が出現し、手番のキャラクターを引っ張って動かして直接ダメージを与える  
* 味方にあたることで1回だけ出る友情コンボでダメージを与える
* HPが0になったら，ゲームオーバーとなる
* 敵を3体倒せばクリアになる
* 弱点を殴るとダメージは2倍になる

## ゲームの実装
### 共通基本機能
* 背景画像
* 4体のキャラクター
* ゲームデザイン
* BGM
* メニュー画面(キャラ詳細・リセット)

### 担当追加機能
* 友情コンボ　全属性エナジーサークル（担当：一石）：五つの円を５つキャラクターの周りに出す友情コンボを描画する
* 友情コンボ　十字レーザー（担当：小野寺）：キャラクターから十字にレーザーが出る友情コンボを描画する
* 友情コンボ　反射拡散弾（担当：矢田）：キャラクターから全方向に壁で3回反射する拡散弾を出す友情コンボを描画する
* 友情コンボ　ハイエナジーサークル（担当：原口）：キャラクターから一瞬で円形に広がるサークルを出す友情コンボを描画する
* 敵+ゲーム全般（担当：瀬戸山）：敵を描画する+ゲーム全般を作る  
敵を生成し、手番のキャラクターと衝突判定を行って、衝突したら敵のHPを減らす  
弱点と衝突したら2倍のダメージを与える  
敵を倒したら次の敵が出てきて、3体すべて倒すとゲームクリアになる  
友情コンボと敵の衝突判定もコメントアウトで作成  
rotate_pos関数を定義して原点、半径、回転角度を入れるだけで、簡単に座標を得られるようにした


### ToDo
- 反射
- ギミック
- 他の友情コンボ
- ステージの移動
- ゲージ

### メモ
* 敵と友情コンボの衝突判定はコメントアウトで用意してある
* それぞれの友情コンボのクラスはSpriteを継承して作成し、Groupに追加することで衝突判定を行う
* 友情コンボクラスでは、attack(ダメージ量)を設定して欲しい
* GameManagerクラスのインスタンスgameのnow_characterメソッドを使うことで、引数無しなら手番のキャラクター、引数有りなら入れた番号のBirdクラスインスタンスが返ってくるようにしてあるので、衝突判定などに利用するとよい
* ゲームの状態はGameManagerクラスのインスタンスgameのstateに保存されている

![](fig/game.png)