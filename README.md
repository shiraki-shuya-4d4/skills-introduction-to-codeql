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
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
  TBD-step-2-notes.
-->

## ステップ2: CodeQLアラートのレビューとトリアージ

_素晴らしい！CodeQLが動作しています！ :tada:_

この演習では、CodeQLスキャンの結果をレビューし、アラートをトリアージし、アラートを追跡するためのGitHub Issueを作成します。

**GitHub Actionsとは**: GitHub ActionsはGitHub内の自動化およびCI/CDプラットフォームです。私たちはGitHub Actionsを使用して、コードスキャンでセキュリティスキャンを統括・実行します。GitHub Actionsは継続的インテグレーション・継続的デリバリー（CI/CD）プラットフォームで、ビルド、テスト、デプロイメントパイプラインを自動化できます。GitHub Actionsの詳細については、「[GitHub Actionsを理解する](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)」を参照してください。

**CWEとは**: Common Weakness Enumeration（CWE）は、ハードウェアおよびソフトウェアの弱点と脆弱性のカテゴリシステムです。これは、アプリケーションのソースコードにおけるセキュリティ問題を説明・分類する方法と考えてください。CWEの詳細については、Wikipedia記事「[Common Weakness Enumeration](https://en.wikipedia.org/wiki/Common_Weakness_Enumeration)」を参照してください。

### :keyboard: アクティビティ1: CodeQLスキャンのステータス確認

このアクティビティでは、GitHub Actionsを使用してCodeQLスキャンのステータスを確認します。
1. 新しいリポジトリで、トップナビゲーションバーから**Actions**を選択してActionsページに移動します。CodeQL Actionの実行がまだ実行中の場合、スキャンがまだ進行中であることを示す黄色のスピナーが表示されます。通常、完了まで約4分かかります。
2. **CodeQL Setup**をクリックして実行を選択します。

![codeql-setup](/images/codeql-setup.png)

Actionsの実行内でより多くの情報が利用できることに注意してください。このセクションを自由に探索して、CodeQLログ、実行時間、ステータス、CodeQLによって生成されたアーティファクトなどの情報を確認してください。

スキャンが完了すると、実行の横に緑のチェックが表示されます。  
  
### :keyboard: アクティビティ2: すべてのCodeQLアラートの確認

このアクティビティでは、リポジトリのセキュリティページでCodeQLの発見事項を確認します。セキュリティページは、すべてのセキュリティ関連情報が表示される場所です。

1. リポジトリのトップナビゲーションバーで**Security**タブに移動します。
2. 左側のナビゲーションバーの「Vulnerability alerts」の見出しの下にある**Code scanning**を選択します。

この画面には、このリポジトリのコードベース内でCodeQLによって特定されたすべての脆弱性が表示されます。このページのさまざまなフィルターと検索機能を調べてください。これらのフィルタリング機能は、多くの発見事項を扱う際に非常に役立ちます！


### :keyboard: アクティビティ3: アラートのレビュー

このアクティビティでは、アラートUIを探索します。脆弱性のデータフローをレビューし、アラートがコードのどの部分に影響するかを特定し、アラートに関する詳細情報を取得します。

**アラートステータス:** このセクションでは、現在のアラートステータス（オープンまたはクローズ）を表示し、スキャンがアラートを検出したブランチを特定し、アラートのタイムスタンプを表示します。

![alert-status](/images/alert-status.png)

**位置情報:** このセクションでは、コードのどの部分が脆弱であるかを説明します。

![location-information](/images/location-information.png)

**パス:** 「Show paths」をクリックすると、アラートのデータフローに関する追加の洞察が得られます。モーダルでは、ユーザー入力（これを「ソース」と呼びます）がアプリケーションを流れ、処理される（これを「シンク」と呼びます）までの流れを示します。これにより、アプリケーション内のデータの流れを可視化できます。

**推奨事項:** このセクションでは、ツール（この場合はCodeQL）、ルールID、さらにはこの脆弱性を見つけるために使用されたCodeQLクエリを表示できます。**View source**をクリックしてクエリを表示できます。さらに、このペインには、この脆弱性を修正するための推奨事項が含まれています。**Show more**をクリックして、完全な推奨事項を表示します。

![recommendations](/images/recommendations.png)

**監査証跡:** 監査証跡は、アラートの履歴を示します。この証跡は、ユーザーがアラートをクローズとしてマークしたり、コード内のアラートを修正したりする際のステータスを表示します。

![audit-trail](/images/audit-trail.png)

**アラートトリアージ:** アラートの右上にあるボタンを使用して、アラートをトリアージしたり、アラートに対して新しいイシューを作成したりします。まだ何もしないでください。すぐにこれらのボタンについて説明します。😄

**追加情報:** 最後に、右側のパネルには、タグ、CWE情報、アラートの重要度などの情報が含まれています。
  ![additional-information.png](/images/additiona-information.png)


### :keyboard: アクティビティ4: アラートを閉じる
アラートのレイアウトに慣れたところで、アラートをクローズするプロセスを実行してみましょう。

1. この同じアラート内で、**Dismiss alert**をクリックし、却下する理由を選択し、短いメモを追加します。
2. **Dismiss alert**をクリックします。
3. この時点で、アラートのステータスが「Dismissed」に変わります。アラートの下部にある監査証跡で、自分が行った変更を確認できます。
4. **Security** > **Code scanning alerts**に戻ります。1つのアラートのみがリストされていることがわかります。
5. **1 Closed**をクリックします。これにより、閉じたアラートが表示され、今閉じたアラートを確認できます。
   ![one-closed-alert.png](/images/one-closed-alert.png)

7. （オプション）アラートを開いて**Reopen alert**を選択することで、アラートを再度開くこともできます。

### :keyboard: アクティビティ5: アラートに対するGitHub Issueの作成
この最後のステップでは、脆弱性の解決に向けた作業を追跡するためのGitHub Issueを作成する方法を示します。Issueは、セキュリティ問題に対するコラボレーションのスペースを提供し、個人やチームに割り当てることができます。

1. スキャンでCodeQLが特定したオープンアラートの1つを開きます。
2. アラートの右上にある緑色の**Create issue**ボタンをクリックします。このボタンが表示されない場合は、アラートのステータスを確認して、オープンアラートであることを確認してください。
3. 新しいイシューフォームに含めたい詳細を追加します。
4. **Submit new issue**をクリックします。
5. イシューを表示するには、リポジトリのトップナビゲーションバーで**Issues**をクリックします。
6. 約20秒待ってから、このページ（手順を説明しているページ）を更新します。[GitHub Actions](https://docs.github.com/en/actions)が自動的に次のステップに更新されます。

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

ヘルプを取得: [ディスカッションボードに投稿](https://github.com/orgs/skills/discussions/categories/introduction-to-codeql) &bull; [GitHubステータスページを確認](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [行動規範](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
