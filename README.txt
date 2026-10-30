CASIOアラームと時間計算（MTG-B1000専用）

設置：ZIPを展開し、中の index.html / sw.js / manifest.webmanifest / icon-192.png / icon-512.png をGitリポジトリの公開フォルダへ置き、GitHub Pagesで公開してください。README.txt は配布不要です。

初回はオンラインで公開URLをAndroid Chromeで開き、PWAをインストールします。時計への転送はBluetoothが必要です。

基本操作：
1. 時刻を入力
2. 「B1000へ転送」を押す
3. B1000のBluetooth接続用ボタンを約4秒長押し
4. 書き込み後、アプリが読み戻して時刻とONを確認

アラームOFF：
1. 「アラームOFF」を押す
2. B1000のBluetooth接続用ボタンを約4秒長押し
3. 現在のアラーム時刻を維持したままOFFを書き込み、読み戻して確認

Bluetooth：初回だけ機器一覧から「CASIO MTG-B1000」を選択します。以後は同じ公開URLへの機器許可がChromeに残っていれば navigator.bluetooth.getDevices() からB1000を再利用し、通常は機器選択画面を出しません。サイトデータ削除、Bluetooth許可の解除、シークレットモード等では再選択が必要になる場合があります。名前フィルターは使用せず、acceptAllDevices:true のままです。

入力：645 と 0645 はどちらも 06:45。24時間表示、時・分です。転送するアラームは常にONです。

安全：書き込み後は読み戻し一致で成功表示します。結果不明時の自動再送はしません。

更新：sw.js のCACHE名は v8。Ver.ボタンでService Workerを更新して再起動します。

Ver.0.1.8：B600を削除してB1000専用化。許可済みB1000の再利用を明確化。現在時刻を維持したままアラームをOFFにするボタンを追加。操作順「時刻入力→送信→時計を約4秒長押し」を維持。
