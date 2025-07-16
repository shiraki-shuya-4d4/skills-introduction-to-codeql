<header>

<!--
  <<< Author notes: Course header >>>
  Read <https://skills.github.com/quickstart> for more information about how to build courses using this template.
  Include a 1280×640 image, course name in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Next to "About", add description & tags; disable releases, packages, & environments.
  Add your open source license, GitHub uses the MIT license.
-->

# CodeQLを有効にしてソースコードを保護する

_アプリケーションソースコードのセキュリティを確保することは、現代のソフトウェア開発において重要なステップです。このGitHub Skillsコースでは、GitHubコードスキャンを使用して、安全でないコーディングパターンを特定、解決、および防止する方法を学びます。_

</header>

<!--
  <<< Author notes: Step 3 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-3-notes.
-->

## Step 3: セキュリティ脆弱性を修正する

_Step 2: CodeQLアラートのレビューとトリアージが完了しました。お疲れ様でした :sparkles:_
  
このステップでは、CodeQLによって既に特定された既存のセキュリティ脆弱性を修正します。この時点で、私たちはリポジトリにCodeQLを導入し、既存のコードをスキャンしました。発見された脆弱性は実世界の問題であり、修正する必要があります！`/server/routes.py`ファイルを編集してこの問題を修正します。

### :keyboard: Activity 1: アラートをレビューする
まず、これらのアラートを修正する前に、アラートがまだ開いていることを確認する必要があります。また、どのファイルを修正し、どのように修正するのが最適かについての情報を収集する必要があります。

1. コードスキャンアラートページに移動します：**Security** > **Code scanning**
1. 「**Open**」としてリストされた2つのアラートが表示されるはずです。いずれかのアラートが「**Closed**」としてリストされている場合は、アラートページを開いて「**Reopen alert**」を選択してください。

これで両方のアラートが開いているので、修正しましょう。アラートを確認すると、どちらも問題を含む特定のファイルを指しています：`server/routes.py`。問題はデータベースのSQLクエリの作成にあります。これらのクエリはSQLインジェクション攻撃に対して脆弱です。これらのSQL文をより安全に書き直す必要があります。
  
アラートの下部にある**More info**セクションを展開すると、このクエリを修正するための明確な提案があります。次のアクティビティでこれらの提案を実装します。

### :keyboard: Activity 2: routes.pyを編集する
問題がどこにあり、どのように修正するかがわかったので、`routes.py`ファイルの修正を開始します。次のステップは、別のブラウザウィンドウまたはタブで行うことをお勧めします。
  
1. リポジトリの**Code**タブをクリックします。
2. `server`フォルダを選択します。
3. `routes.py`ファイルを選択します。
4. 右側の**Edit**ボタンをクリックします。
  
  ![edit-button.png](/images/edit-button.png)
  
5. 16行目を編集し、SQL文をハイライトしてこのテキストに置き換えます：`"SELECT * FROM books WHERE name LIKE %s", name`
  
6. 22行目を編集し、SQL文をこのテキストに置き換えます：`"SELECT * FROM books WHERE author LIKE %s", author`
  
7. 右上の**Commit changes...**をクリックします。「Propose changes」ウィンドウがポップアップします。デフォルトの設定のままにして、再度**Commit changes**をクリックします。
8. CodeQLが新しいスキャンを開始します。**Actions**に移動し、**CodeQL**アクションを選択してそのスキャンのステータスを確認します。スキャンジョブが完了すると、ActionsはGitHubページの最後の実行の横に緑色のチェックマークを表示します。
9. そのCodeQLスキャンが完了したら、**Security** > **Code scanning**に移動してアラートをレビューします。開いているアラートはゼロ、閉じられたアラートは2つになっているはずです🎉。閉じられたアラート、特に監査証跡を自由にレビューしてください。
10. 約20秒待ってから、このページ（指示に従っているページ）を更新してください。[GitHub Actions](https://docs.github.com/en/actions)が自動的に次のステップに更新されます。

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

ヘルプを取得: [ディスカッションボードに投稿](https://github.com/orgs/skills/discussions/categories/introduction-to-codeql) &bull; [GitHubステータスページを確認](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [行動規範](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
