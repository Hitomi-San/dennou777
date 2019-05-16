# 地球流体電脳倶楽部 LaTeX2e 用マクロ集 version 7 Nicole (dennou777.cls)

## 概要

これは、「LaTeX を用いた、マニュアル、論文等の作成に便利な、マクロ定義スタイル集である」
[Dennou6.sty](http://www.gfd-dennou.org/library/cc-env/TeXmacro/dennou/) 
の、古くなった部分は更新し、さらに新しく便利な機能を追加したものである。

**現在開発中である**。特に、__Nicole バージョンは、開発中途であり、安定版ではない__。
この README は、パッケージの使い方や、仕様を記したものではなく、
dennou777.cls を開発する上での覚書である。パッケージのドキュメントは dennou777.pdf
を参照。**現在開発中であるが、デバグのために、より多くの人に利用してもらいたい**。

## インストール方法

### ファイル群

d6stys ディレクトリに含まれるファイル群は、オリジナルの電脳スタイル version 6 のファイルである
（Dennou6.sty は D6.sty と、version 6 のドキュメントは、D6.pdf とリネームした）。
これらファイルは、オリジナルのままであるので、（リネーム以外の）一切の変更は行っていない。

version 7 におけるファイル群は、dennou777 から始まるファイル、d777 から始まるファイル、
そしてこの README である。

### インストール

dennou777.cls, d777helper.sty, d6styles 配下にある Dennnou6.sty の付属ファイル
一式（とこのドキュメント）を「TeX から見える位置」に配置することで、インストールは完了する。
なお、使用している TeX ライブラリが古い場合、必要なファイルが見つからないと言われる可能性がある。
その場合は TeX ライブラリのアップデート（TeX Live 2018 以降を推奨）すること。

Dennou6.sty 利用者は、dennou777.cls と d777helper.sty のみインストールすれば
使えるようになる。

### 使用方法

dennou777 はクラスファイルの形で提供されている。`\documentclass{dennou777}` とする
ことによって、dennou777 を利用することができる。

dennou777.cls は内部で jlreq.cls を読み込んでいるので、jlreq が受け付けるオプションは
すべて受け付ける。他のオプションについては、dennou777.pdf を参照。

## 開発方針

Version 6 と同様な機能を提供しつつ、outdated な記述を削除し、推奨されている
記述に改める。また、version 6 が提供しようとしている機能自体が outdated なものである
場合、*その機能自体を削除することも辞さない*。
Version 6 と同様な機能—版面構成は、d6styles 配下にある D6.pdf を参照。

Version 6 の機能を改めると同時に、Version 7 で新しい機能を提供することも考えている。

また、日本語で LaTeX をする方法に、pLaTeX + dvipdfmx 以外の方法、例えば upLaTeX + dvipdfmx
や、XeLaTeX、LuaLaTeX-ja といった方法が増えてきたのを鑑みて、pLaTeX、upLaTeX、
LuaLaTeX のいずれにも対応するパッケージとすることを目指す。

### Version 6 から更新された機能

+ **dennou777 はクラスファイルとして提供することにした。**
	- ベースとするのは jlreq.cls。
	- jlreq.cls には、エンジンの自動判定機能があるので、fontspec や okumacro といった
		特定のエンジンに依存するパッケージを使わない限り、LuaLaTeX でも、pLaTeX でも、
		upLaTeX でも動く。
		* XeLaTeX はサポート外とする。
		* upLaTeX + dvipdfmx ができるかちょっと怪しい。
	- D6style 相当の機能は、ほとんど jlreq の機能を用いて再現した。
+ (u)pLaTeX で処理されたときに、自動で dvipdfmx のオプションを付加して graphicx と
	xcolor を読み込むようにした。
	- BXdvidriver を利用。
+ D6graphicx は削除した。
	- 今どき PostScript を埋め込まなければならないなんて、ありえないでしょ（）。
	- 同等の機能は欲しい場合は、graphicx の機能を使うか、TikZ を利用してください。

### 更新する予定の機能

#### Version 6 の機能のうち、改修する予定のもの

+ `\bf` が使われているので、それを排除する。
+ D6math.sty が提供するコマンドの、スペース関連のもの。

#### Version 6 の機能のうち、削除したいと考えているもの

+ D6prog.sty（高機能な listing パッケージが存在しているため、そちらを使うべきなのでは;
	削除するかは未定）

#### Version 7 で新しく追加したい機能

+ lmodern パッケージや、amsmath パッケージのように、毎回読み込むパッケージを
	一括して読み込む機能。
+ このパッケージを使う人の層を考えると、LaTeX 初学者が触れる機会が多いので、
	LaTeX の使い方もパッケージのドキュメントに含めるべきか。
+ 微積分の d を、立体か斜体かを選択する機能。

#### 既知の不具合

+ Version 6 のページスタイルを模倣したが、罫線がないので、そこを直す。
+ 柱に chapter が表示されない。

## FAQ

<dl>
	<dt>どうして、dennou7.cls じゃなくて、dennou777.cls なのですか。</dt>
	<dd>
		とあるゲームに由来してます。
	</dd>
	<dt>「地球流体電脳倶楽部 LaTeX2e 用マクロ集 version 7.0.0 (Nicole)」の Nicole って何ですか。</dt>
	<dd>
		コードネームです。「777」の元ネタに登場するキャラクターに由来しています。
		ver. 7.1.x では “Haru”、7.2.x では “Musubi” というふうに続く予定です。
	</dd>
	<dt>どうして、全面的に作り変えようとしたのですか?</dt>
	<dd>
		dennou6.sty が 2001 年以降手を加えられていなさそうだからです。
		さすがに 2001 年以前とは環境が違いすぎるのでやばい。
	</dd>
</dl>

## ライセンス (License)

修正 BSD ライセンスの元配布を行う。

This package is distributed under the Revised BSD License.

## 開発状況（主な更新箇所）

- [2019-05-16] Version 7.0.3
- [2019-05-15] ライセンスを明記。
- [2019-05-14] Version 7.0.2 （Version 7.1.0 は誤りです）
- [2019-05-09] ドキュメントを充実させた。
- [2019-04-18] README.md にインストール方法と使用方法を記載。
- [2019-04-16] 簡易にドキュメントを作成。
- [2019-04-16] Dmyheading と DAheading ページスタイルを簡易に実装。
- [2019-04-15] クラスファイルとして提供する方針を決めた。
- [2019-04-15] Version 6 のファイル群をディレクトリにまとめた。
- [2019-04-14] 開発を開始するため、開発方針について、本文書に記載。
