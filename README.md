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
  <<< Author notes: Step 1 >>>
  Choose 3-5 steps for your course.
  The first step is always the hardest, so pick something easy!
  Link to docs.github.com for further explanations.
  Encourage users to open new tabs for steps!
  TBD-step-1-notes.
-->

## ステップ1: CodeQLを有効にする

👋 こんにちは！GitHub Skillsコース「コードスキャンを有効にする」へようこそ！

始めましょう！

この最初のステップでは、CodeQLについて詳しく学び、それを使用してソースコードを保護する方法を学びます。

**GitHubコードスキャンとは**: _[コードスキャン](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning)_ は、開発チームがソフトウェア開発プロセスにセキュリティテストツールを統合できる機能です。これはGitHub Actionsを使用して行われます。コードスキャンを使用すると、SAST、コンテナ、インフラストラクチャ・アズ・コードセキュリティツールなど、多くの異なるタイプのツールを統合できます。

**CodeQLとは**: _[CodeQL](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning-with-codeql)_ は、SQLインジェクション、クロスサイトスクリプティング、コードインジェクションの問題などのセキュリティ脆弱性を特定するのに役立つ静的解析テストツールです。

### :keyboard: アクティビティ: CodeQLでコードスキャンを有効にする
  
まず、リポジトリでCodeQLを使用したコードスキャンを有効にします。

1. 新しいブラウザタブを開き、このタブで手順を読みながら、2番目のタブでステップを実行します。
2. 新しく作成されたリポジトリの上部にある **Settings** タブに移動します。
3. 左側の **Security** セクションで、**Advanced Security** を選択します。
4. **Code scanning** というタイトルのセクションまでスクロールダウンします。このコースでは、CodeQL分析に焦点を当てます。
5. **Set up** ドロップダウンメニューをクリックして、**Default** を選択します。
![enable-code-scanning-default.png](/images/enable-code-scanning-default.png)

モーダルの設定オプションを見てみましょう：
  
  - **Languages to analyze:** これらは、CodeQLによってスキャンされる言語です。この場合、`Python`でスキャンします。
  - **Query suites:** CodeQL [クエリ](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning-with-codeql#about-codeql-queries)は「スイート」と呼ばれるバンドルにパッケージされています。このセクションでは、使用するクエリスイートを選択できます。この演習では、**Default** に設定したままにします。詳細については、「[CodeQLクエリについて](https://docs.github.com/en/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/about-code-scanning-with-codeql#about-codeql-queries)」を参照してください。
  - **Events:** このセクションは、CodeQLがいつスキャンするかを指定します。この場合、`main`ブランチへのプルリクエストでスキャンするように設定されています。
    
![codeql-default-configuration-box.png](/images/codeql-default-configuration-box.png)

6. **Enable CodeQL** をクリックします
7. 約20秒待ってから、このページ（手順を読んでいるページ）を更新します。[GitHub Actions](https://docs.github.com/en/actions)が自動的に次のステップに更新されます。

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

ヘルプを取得: [ディスカッションボードに投稿](https://github.com/orgs/skills/discussions/categories/introduction-to-codeql) &bull; [GitHubステータスページを確認](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [行動規範](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
