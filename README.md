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
  <<< Author notes: Step 4 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-4-notes.
-->

## ステップ 4: プルリクエストで脆弱性を防ぐ

_よくできました！ステップ 3: セキュリティ脆弱性の修正 を完了しました！ :partying_face:_

よくやりました！ここまで来れました。もうすぐ完了です！最後のステップは、CodeQLとプルリクエストの統合をテストすることです。このステップでは、`routes.py` ファイルに脆弱性を再び追加して、SQLインジェクション脆弱性のアラートをトリガーします。これは最初に見たのと同じ問題になります。

目標は、開発者が新しい脆弱性を見つけたときの体験を理解することです。

このステップでは以下を行います：
- `routes.py` ファイルを編集します
- SQL文を安全でないものに変更します
- これらの変更をコミットし、安全でないコードをメインブランチにマージします
- プルリクエスト内でアラートを体験します

始めましょう 👍

**プルリクエストとは**: プルリクエストは、ユーザーが提出し、リポジトリの協力者によって承認または拒否される、リポジトリへの変更提案です。これにより複数の人が同じコードを同時に作業できます。詳細については、GitHub Skills コース「[Introduction to GitHub](https://github.com/skills/introduction-to-github)」またはGitHubドキュメントの「[プルリクエストについて](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)」を参照してください。

**ブランチとは**: ブランチはリポジトリの並行バージョンです。デフォルトでは、リポジトリには main という名前の1つのブランチがあり、これが決定的なブランチとされています。追加のブランチを作成することで、リポジトリのメインブランチをコピーし、メインプロジェクトを中断することなく安全に変更を行うことができます。詳細については、GitHubドキュメントの「[ブランチについて](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches#)」を参照してください。

### :keyboard: アクティビティ 1: `routes.py` を編集して新しいプルリクエストを作成する

この最初のアクティビティでは、以前と同じ安全でないSQL文を `routes.py` ファイルに導入します。ファイルを更新したら、新しいブランチにコミットして、プルリクエストを作成します。

  1. リポジトリの **Code** タブをクリックします。
  2. `server` フォルダを選択します。
  3. `routes.py` ファイルを選択します。
  4. 右側の **Edit** ボタンをクリックします。

![edit-button.png](/images/edit-button.png)
  
  5. 16行目のSQL文をハイライトして、このテキストに置き換えます：`"SELECT * FROM books WHERE name LIKE '%" + name + "%'"`
  6. 右上の **Commit changes...** をクリックします。「変更を提案」ウィンドウがポップアップします。
  7. 今回は **Create a new branch** の横のラジオボタンを選択します。このブランチの新しい名前を作成するか、デフォルトの提案をそのまま使用できます。
  8. **Propose changes** をクリックします。これで新しいプルリクエストが開きます。
  9. 「プルリクエストを開く」ウィンドウで **Create pull request** をクリックします。
  

### :keyboard: アクティビティ 2: プルリクエストをレビューする

この時点で、脆弱なコードを追加するために `routes.py` ファイルを編集し、新しいブランチにこれらの変更をコミットし、新しいブランチを `main` ブランチにマージするプルリクエストを作成しました。これらは開発者が新しい脆弱なコードをリポジトリに導入するときに取る同じ手順です。

では、プルリクエストを見て、どのような体験になるかを確認しましょう。

1. 前のアクティビティで、プルリクエストを作成しました。プルリクエストを作成した後、プルリクエストページに直接移動しました。プルリクエストの下部に、「Code scanning/CodeQL」というチェックが表示されます。これは、プルリクエストで導入されたコードをスキャンするCodeQL分析ジョブです。

![pr-panel](/images/pr-panel.png)

2. チェックが完了すると、CodeQLからプルリクエストに新しいセキュリティ脆弱性を示す新しいコメントが表示されます。これは、ユーザー制御データから構築されたSQLクエリです。これが私たちのSQLインジェクション脆弱性です。

<img width="1180" alt="image" src="https://github.com/leftrightleft/enable-code-scanning/assets/4910518/378bd766-ef61-4619-ab3c-bf2c8d9618d7">

3. **Show paths** をクリックして、データフローパスを確認します。

4. 必要に応じて、コメントを追加し、GitHubハンドルを使用して友人をタグ付けできます（例：`@username`）。これにより、あなたがその問題にコメントし、問題の解決に協力が必要であることが通知されます。😄

実際の状況では、開発者はブランチ内のSQL文を修正します。修正されると、脆弱性は自動的にクローズされます。

コードスキャンのプルリクエスト統合についてもっと学びたい場合は、「[プルリクエストでのコードスキャンアラートのトリアージ](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/triaging-code-scanning-alerts-in-pull-requests)」を参照してください。

5. 約20秒待ってから、このページ（指示に従っているページ）を更新してください。[GitHub Actions](https://docs.github.com/en/actions) が自動的に次のステップに更新します。

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

ヘルプを取得: [ディスカッションボードに投稿](https://github.com/orgs/skills/discussions/categories/introduction-to-codeql) &bull; [GitHubステータスページを確認](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [行動規範](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
