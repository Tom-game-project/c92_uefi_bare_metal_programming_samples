# "フルスクラッチで作る!UEFIベアメタルプログラミング"サンプルプログラム
同人誌"フルスクラッチで作る!UEFIベアメタルプログラミング"のサンプルプログラムです。

サンプル毎にディレクトリが分かれています。
同人誌本文でサンプルコードを紹介する際、ディレクトリ名を書いていますので、
各サンプルの内容については同人誌を参照してください。

なお、同人誌のPDF版は、新刊として頒布するコミックマーケット92のイベント日(8/11(金))以降、
以下のページで公開しています。

* http://yuma.ohgami.jp/


## USBにEFIを書き込む手順

アプリケーションの`Disks`を使うとUSBのmount先がわかる

ディレクトリが作成できていなければ適宜作る

```bash
sudo umount /dev/sda1
sudo mount /dev/sda1 /mnt/usbmem
sudo cp <作成したEFIファイル> /mnt/usbmem/EFI/BOOT
sudo umount /mnt/usbmem
```

UEFIファームウェアのバイナリを配置する
```
./third_party/ovmf/RELEASEX64_OVMF.fd
```

