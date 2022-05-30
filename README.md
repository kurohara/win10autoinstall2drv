# Auto Answer File for Windows 10 installation.

Windows10の新規インストール時に、以下のような環境を構築したい人向けのアンサーファイルを作成。

* 新規インストール
* ２台以上の物理ディスク。
* Usersフォルダを別ドライブ（２台目）に置きたい。
* ２台目のディスクのドライブレターは E。
* ロケールは日本語

※　もし使用する際は自己責任で。（末尾の「問題点など」を参照ください）

## 関連情報

非公式のアンサーファイル自動作成サイト  
https://www.windowsafg.com/win10x86_x64_uefi.html  

アンサーファイルを編集するのにシステムイメージマネージャがあると便利なのでダウンロードする。  
Windows10のアンサーファイル作成でも、Windows11用が使える。  
（というか古いものではエラーになる）  
https://docs.microsoft.com/ja-JP/windows-hardware/get-started/adk-install  

この辺りの情報も参照  
https://docs.microsoft.com/ja-jp/windows-hardware/customize/desktop/unattend/

isoファイルからbootable USBメモリ作成  

## 使用方法

1. autounattend.xml の [作成ユーザ名] と [プロダクトキー] をエディタで編集して修正する(自前のものに置き換える)。
2. Windows10インストール用のUSBメモリのルートディレクトリにautounattend.xml を置く。
3. 対象機にてUSBメディアからブートしてインストールする。

(DVD等でインストールする場合はautounattend.xmlだけを書き込んだUSBメモリをインストールメディアと一緒に装着する)

## 問題点など

* これを使用して、Usersフォルダを別ドライブにすることは公式には推奨されておらず、OSアップデートで問題が出る可能性があると言われている。
* 最初、"FolderLocation"だけを変更し、UsersフォルダとProgramDataフォルダをEドライブに変えてみたら、スタートメニューが表示されないという問題が起きた。  
  原因はExplorerを含め多数のプログラムのインストール時に、 "C:\Users" や "C:\ProgramData" などの文字列が決め打ちでレジストリに書かれていたためだった。  
  Usersフォルダに関してだけはインストール直後のカスタムコマンドで対処できたが（多分）、ProgramDataに関してはあまりに多岐に渡っていたのでEドライブへの移動は断念した。  

