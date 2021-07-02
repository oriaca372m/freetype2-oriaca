# Qtのフォントの描画が太すぎるのをどうにかするFreeType2のパッチ
Qtのフォントの描画が、GTKと比べて明らかに太くてかっこ悪いのを、強引に治すFreeType2のパッチとArch Linux用のPKGBUILD

# スクリーンショット
ビフォー
![ビフォー](./img/before.png)

アフター
![アフター](./img/after.png)

# ビルドとインストール
``` bash
$ makepkg -Csfi --skippgpcheck --check
```
