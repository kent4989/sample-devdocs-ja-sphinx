.. include:: definition.txt
==============================
ドキュメント更新のガイドライン
==============================

本ドキュメントは、オープンソースで提供されているPython製のドキュメント生成ツール Sphinxを利用して作成されています。本項では本ドキュメントを更新するための最低限の情報を示します。より詳細な情報が必要な場合は、末尾に記載の参考サイトや各種技術書籍を確認してください。

.. index:: Sphinxのインストール

Sphinxのインストール(Windows向け)
=================================
本ドキュメントを閲覧するだけであればSphinxのインストールは不要です。更新・追加を行う場合のみ、以下のサイトを参考にインストールを行なって下さい。

- http://sphinx-users.jp/gettingstarted/install_windows.html

文書のビルド
============
本ドキュメントの各パーツは、拡張子rstのテキストファイルになります。文書をビルドすることで、これらのテキストファイルは統合されHTMLや各種のフォーマットで出力されます。

文書全体をビルドする
--------------------
文書全体をビルドする場合は、予め用意されたMake.batコマンドを利用します。コマンドラインで以下のコマンドを実行して下さい。

::

  Make HTML

結果はデフォルトでは_buildフォルダに出力されます。

特定の文書だけをビルドする
--------------------------
文書の追加や修正をおこなう際には、特定のファイルだけをビルドして出力結果を確認することができます。コマンドラインで以下のコマンドを実行して下さい。

.. TODO::
  要調査。上記のように書いたけれども、Sphinxは1ファイルだけのビルドは出来ないように見える。
  ちょっと修正するだけでもMakeしたほうが良いのかも(差分rstファイルだけを更新しているようだ)。

文書の追加
==========
新たに文書を追加する場合は、拡張子rstのテキストファイルを追加します。追加するファイルは文字コードUTF-8で保存してください。また、追加したテキストファイルを目次に追加する必要があります。目次ファイルは各フォルダにあるindex.rstです。

各フォルダにあるindex.rstに書かれたtoctreeにファイル名(拡張子は不要です)を追加すれば、ビルド時に自動的に目次に記述内容が組み込まれます。文法の説明は :ref:`about_rst` を参照してください。

文書の修正
==========
既存の文書を修正する場合はテキストエディタで修正を行なって下さい。文法の説明は :ref:`about_rst` を参照してください。

文書の構成について
==================
このドキュメントは、ドキュメントの用途種類別にフォルダを分けて管理しています。それぞれのフォルダにはindex.rstという目次ファイルがあります。文書を新たに追加した場合は、目次ファイルの修正も必要です。

=========== ================
本ドキュメントの構成
----------------------------
フォルダ    フォルダの役割・位置付け
=========== ================
inception   |inception| 
project     |project| 
design      |design| 
development |development| 
test        |test| 
release     |release| 
maintenance |maintenance| 
records     |records| 
=========== ================

上記のフォルダに含まれないものは :doc:`全体の目次<index>` 、 :doc:`intro` 、 :doc:`using_sphinx` の3つです。

.. index:: reStructredText
.. _about_rst:

最低限の文法説明
================
Sphinxでは、reStructredTextという、Wikiに似た簡易テキストマークアップを利用してドキュメントを作っていきます。ここではよく利用する基本的なテンプレートで説明を行います。

::

  ==============
  ページタイトル
  ==============
  
  大項目
  ======
  
  ・・・・・本文・・・・・
  
  中項目
  ------
  
  - リスト1
  - リスト2
  
   - リスト2-1 (上下に空行を入れる点に注意して下さい)
  
  - リスト3
  
  小項目
  ------
  **太字**
  
  *斜体*
  
  ``リテラル``
  
  `リンク付きテキスト <http://python.org>`_

さらに詳細なreStructredTextの文法は文末の :ref:`reference` を参照してください。

本ドキュメントのローカルルール
==============================

画像・添付ファイルの取り扱い
----------------------------
文書内に表示する画像や、各種の添付ファイルについては_staticフォルダに、文書のファイルと同名のフォルダを作成した上で格納してください。

用語集の使用
------------
用語集ファイルを使用することで、用語名の統一を図ることができます。例えばシステム名称は開発段階では無かったり、仮称であったりします。用語集ファイルに書き出して活用することで、常に一貫した擁護を使うことができます。

用語を登録する
^^^^^^^^^^^^^^
用語集ファイル(definition.txt)に用語を登録してください。

::
  
  .. |hello| replace:: (^o^)／

用語を使用する
^^^^^^^^^^^^^^
ファイルの冒頭に以下のinclude定義を行なって下さい。文中では、\|用語\|で記述すれば、文書のビルド時に一括して置換されます。

::

  .. include:: ../definition.txt
  ・
  ・
  ・
  定義された名前を呼び出します。|hello|

.. _reference:

INDEXを使用する
^^^^^^^^^^^^^^^
任意のキーワードで索引(INDEX)を作ることができます。ここで言う索引とは、目次ではなく技術書の末尾にあるようなものです。文章に関連したキーワードを設定しておけば文章の閲覧性が高まります。特に細かいルールはありませんが、以下の場合にはINDEXを記述するようにして下さい。

- 文章内でユニークな事柄や特記事項を記載する場合
- システムの特定の機能に関する記述

INDEXエントリーはカンマ区切りで複数指定することもできます。またセミコロンで区切った場合、サブエントリーとなります。

::
  
  .. index: keyword1,keyword2,keyword3;sub-keyword3.1
  ・
  ・

Sphinxに関する参考情報
======================
- http://sphinx-users.jp/
