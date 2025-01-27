# Another One Of Statbars
趣味に走りまくったステータスバーを表示します。  

## 表示  
![1](https://user-images.githubusercontent.com/50558182/71636975-472e3980-2c7c-11ea-82be-5089f5b56578.png)  
![4](https://user-images.githubusercontent.com/50558182/71637005-e5220400-2c7c-11ea-82fa-0db3c8d2c194.png)  

水色はSP  
緑色はHP  
紫色は装備耐久値  
黄色はスタミナ  
中央下のゲージはレリックポイント（レリック未装着時は表示されません）
画面中央の水色ダイヤはセット装備スキルのクールダウンもしくはバフの残り時間です（ダイヤモンド表示のカスタマイズ参照）  
(現在水色ダイア表示は機能停止中)
です。

* アーケインエナジー有効化中は以下の画像のように２段表示になり、SP回復量がわかります。  
![2](https://user-images.githubusercontent.com/50558182/71636976-472e3980-2c7c-11ea-9caf-bae39c39d0f6.png)
* ヒーリングファクター有効化中は以下の画像のように２段表示になり、HP回復可能閾値がわかります。  
![3](https://user-images.githubusercontent.com/50558182/71636977-472e3980-2c7c-11ea-8616-a6d0bb8ed6a7.png)

## 使い方
バー中央のアイコンをつかむとドラッグできます。  
画面中央上か下に配置するようデザインしています。  
バーは最大値に応じて結構長く伸びます。  (HPは100000、SPは10000まで伸びます) MHのオマージュです。  

幅やスタイルなどの設定はアイコンをLSHIFT+RCLICKで行えます。  

元のステータスバーは  
weizlogy氏のCompact Heads Up Display 及び MizukiBelhi氏のExtendedUI をご使用いただいて片づけておくと便利です。  
__セット装備スキルのクールダウンはディスナイ・レゲンダ系列にはまだ対応していません。__

## ダイヤモンド表示のカスタマイズ
中央の水色ダイヤの表示内容は`anotheroneofstatbars\settings.json`を弄ることでカスタマイズできます。  
デフォルトではセット装備スキルのクールダウンを表示するようになっています。  
以下の場所においてあるサンプルファイルを使用すると、クールダウンの代わりにセット装備スキルの持続時間が表示されるようになります。  

サンプル設定ファイル→ [example_settings.json](https://github.com/ebisuke/TosAddons/blob/master/anotheroneofstatbars/example_settings.json)  
  
設定ファイルの変更は、マップ切り替えかキャラクターチェンジで反映されます。  
__(ただしそれまでの間にバーを動かすと設定が上書きされますのでご注意ください)__
### 共通
```json
{
    "diamond": {
        "shownumber":true,
        "buffs": {
            "S4271": {
                "name": "Korup"
            },
            "nouse":true,
        },
        "skills": {
            "S100001":{"skill":"Velcoffer_Sumazinti"},
            "nouse":false,
        }
    }
}
```
`diamond.buffs` `diamond.skills`には、どちらにも`nouse`という記述ができます。  
これを`true`にすると、その設定を使用しなくなります。反対に`false`と書くか記述を消すと、その設定を使用します。  
`diamond.shownumber`を`true`にすると、残り時間を数字で表示します。  
![image](https://user-images.githubusercontent.com/50558182/73176448-cd408180-414f-11ea-8af4-c823d1a00f0a.png)


### バフ
`diamond.buffs`には、バフの設定を記述できます。`S1234`のように、Sを書いたのちバフのClsidを書きます。  
`name`は現在使用していませんが、何か書いておいてください。 
```json
{
    "diamond": {
        "buffs": {
            "S4271": {
                "name": "Korup"
            },
            "S2104": {
                "name": "Fanaticism"
            },
        }
    }
}
```
記載されている複数のバフが同時に発動した場合は、表示は不定です。
### スキルのクールダウン
`diamond.skills`には、クールダウンを表示するスキルの設定を記述できます。`S1234`のように、Sを書いたのちスキルのClsidを書きます。  
`skill`は現在使用していませんが、何か書いておいてください。   
サンプルにはほかに記述がありますが、無視してください。(autoswapforsetskillsからコピーしただけです)

```json
{
    "diamond": {
        "skills": {
            "S100001":{"skill":"Velcoffer_Sumazinti"},
        }
    }
}
```
記載されている複数のスキルが同時にクールダウンとなった場合は、表示は不定です。   
また、バフと重複している場合は、バフの設定が優先されます。

## 注意点
* Lv300以上のキャラを想定して作成していますので、それ未満のキャラだと表示がいまいちかもしれません。


# リリースノート
## v0.2.1
* 中央ダイヤを別の形で復活
* ディスナイ系セットスキルに対応（適用するには設定ファイルを削除してください）
## v0.2.0

* EP13対応
## v0.1.6
* statが取得できないときにエラーを吐くのを修正
* パラメータが最小長さより短いときに正常に表示されないのを修正
## v0.1.5
* 起動直後にウインドウ座標が再現されないのを修正
## v0.1.4
* STYLE Bでシールドの位置がおかしいのを修正
* レイヤーレベルの変更機能追加
## v0.1.3
* カスタマイズ機能追加
* STYLE B追加
## v0.1.2
* クラス変更時にアイコンのエラーが出る問題を修正
## v0.1.1
* 右クリックで拠点移動のメニューを表示するように
## v0.1.0
* 中央ダイヤのカスタマイズを可能にした（バフ時間orクールダウン）
* ティクラスのプレフィクスが間違っていたのを修正
## v0.0.5
* アクロバ・アタガル・リリス・プロバースに対応

## v0.0.4
* ファナティシズム有効時はHPバーを赤みがかった黄色にするようにした。
* ~~アクロバ・アタガル・リリス・プロバースに対応~~

## v0.0.3
* 表示の微調整
  今回のアップデートにより表示位置が少し右にずれます。  
  画面をドラッグできなくなった場合は、`addons/anotheroneofstatbars/`フォルダ内の`settings.json`を削除してください。
* バーを常時レンダリングに変更（今まではステータス変化時にレンダリング）  
* ステータスが30%以下になった時に該当するバーの背景を点滅するように
  (装備耐久値については、0になったら点滅をやめます)

## v0.0.2
* HP・SPの最大値がバーの上限に達しているとき、バー減少エフェクトの色がおかしいのを修正
* 装備耐久値の色を明るくした
* 表示の微調整

## v0.0.1
* 初回試験公開
