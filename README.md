# MZ-80B_RAM-checker

MZ-80BのRAMが壊れてしまったので、作成しました。
自分のマシンの壊れ方は、IPL起動するものの、テープ読み込み後にRAMモードでリセットするとバグるという状態です。
ですので、IPLからの起動とキャラクターディスプレイの表示は正常であることが条件です。

ipl.romを2716などのEPROMに焼いて、IPLのROMと交換して起動します。
はじめに$0000〜$7FFFまでをチェックします。
チェック方法は、各ビットを順番に1にしたデータの書き込み、読み込みを行って比較します。
アドレスと書き込みを行ったデータは常に表示されます。

エラーがあった場合は、読み込んだデータとERという表示で動作が一時停止します。
スペースバーを押すと次のアドレスに進みます。

上記アドレスが正常で合った場合は、NSTリセットを行い、$8000〜$FFFFまでを同様の方法でチェックします。
$FFFFまでのチェックが終わるとHaltします。
