# A Template for IEE thesis

経営工学系学位論文に使用できるテンプレート. 

## 特徴

- Docker コンテナを使用して, ローカル環境に Latex の環境を構築しなくても Latex のビルドが可能
- textlint による校正機能
  - GitHub Actions を用いた reviewdog により, pull-request 時に自動でコメントを review log に表示
  - Docker コンテナを用いて環境構築せずローカル環境での校正も実施可能. 

## 環境構築

マシンの環境
- macOS 10.14 or later では動作確認. 
- Windows, Ubuntu では動作未確認.


Docker 環境
- Docker Desktop for Mac 2.1 or later
- Docker 18.06 or later




VS Code
- Latex Workshop をインスト―ル
- VS Code の `settig.json` に以下を追記
  ```
  “latex-workshop.latex.recipe.default”: “latexmk (latexmkrc)”,
  “latex-workshop.docker.enabled”: true,
  “latex-workshop.docker.image.latex”: “texlive/texlive”,
  “latex-workshop.latex.autoBuild.run”: “onFileChange”,
  “latex-workshop.view.pdf.viewer”: “tab”
  ```

## ローカル環境での操作方法

Docker コンテナを用いて, Latex や textlint の環境を構築せずに PDF のビルドや校正を行うことができます.


1. GitHub からクローンする
   > git clone https://github.com/tokyotech-nakatalab/latex-template_iee-thesis.git
1. ディレクトリに入る
   > cd latex-template_iee-thesis
1. make コマンドで Latex のコンパイルを実行したり, 中間ファイルを削除したり, textlint による校正もできる. 
   > make pdf # コンパイルを実行, PDF ファイルが生成される    
   > make clean # 中間ファイルを消す   
   > make lint # textlint による校正を行う. 

VS Code を用いて tex の編集を行う場合, tex ソースを保存するたびにコンパイルが実行される. 

## GitHub Actions による自動校正

GitHub Actions を用いて, pull-request 時に textlint による校正結果を review log に表示することができます. 

1. 適当にブランチを切って, 原稿のファイルを編集する.
2. 編集したファイルをブランチにプッシュする. 
3. 作業中のブランチから main ブランチへの pull request を出す.
4. pull request をした段階で GitHub Actions が走って textlint が実行される.
     - textlint による検出結果は, pull-request における reviewlog にコメントとして出力される.
          - ただし, review log に出力されるコメントは pull-request 時における差分の部分だけであることに注意. 
     - pull-request 画面における Action の実行結果から `Details` に飛ぶと, textlint での検出結果全てを見れる.


## ライセンス

MIT ライセンス (だが当面は研究室内部での公開)


## 謝辞

本リポジトリ作成にあたっては, Shoma Kokuryo さんのリポジトリとブログを参考にした:
- https://github.com/being24/latex-template-ja,
- https://poyo.hatenablog.jp/entry/2020/12/05/110000.


## Contributer 


小林健