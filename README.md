[index.html](https://github.com/user-attachments/files/32909176/index.html)
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Gmail Slack連携</title>
  <meta name="description" content="Gmail Slack連携は Google Apps Script で作成した業務自動化ツールです。">
  <style>
    :root {
      --bg: #f7f7f5;
      --card: #ffffff;
      --text: #1f2328;
      --muted: #5c636e;
      --line: #e3e3df;
      --accent: #1a6b54;
      --accent-soft: #e8f2ee;
    }
    @media (prefers-color-scheme: dark) {
      :root {
        --bg: #16181b;
        --card: #1e2125;
        --text: #e6e8eb;
        --muted: #a0a7b1;
        --line: #33373d;
        --accent: #6cc4a4;
        --accent-soft: #1f3029;
      }
    }
    * { box-sizing: border-box; }
    body {
      margin: 0;
      background: var(--bg);
      color: var(--text);
      font-family: -apple-system, BlinkMacSystemFont, "Hiragino Sans", "Hiragino Kaku Gothic ProN", "Noto Sans JP", "Yu Gothic UI", Meiryo, sans-serif;
      line-height: 1.85;
      font-size: 16px;
    }
    .wrap {
      max-width: 760px;
      margin: 0 auto;
      padding: 48px 16px 64px;
    }
    header { margin-bottom: 32px; }
    .tag {
      display: inline-block;
      font-size: 12px;
      letter-spacing: 0.08em;
      color: var(--accent);
      background: var(--accent-soft);
      padding: 2px 10px;
      border-radius: 999px;
      margin-bottom: 12px;
    }
    h1 {
      font-size: clamp(26px, 5vw, 34px);
      line-height: 1.35;
      margin: 0 0 8px;
    }
    .lead { color: var(--muted); margin: 0; }
    section {
      background: var(--card);
      border: 1px solid var(--line);
      border-radius: 12px;
      padding: 28px 24px;
      margin-bottom: 24px;
    }
    h2 {
      font-size: 20px;
      margin: 0 0 16px;
      padding-bottom: 10px;
      border-bottom: 1px solid var(--line);
    }
    h3 {
      font-size: 16px;
      margin: 28px 0 6px;
    }
    h3:first-of-type { margin-top: 8px; }
    p { margin: 0 0 12px; }
    ul { margin: 0 0 12px; padding-left: 1.4em; }
    a { color: var(--accent); }
    .date { color: var(--muted); font-size: 14px; }
    .cta {
      display: inline-block;
      margin-top: 8px;
      padding: 8px 16px;
      border: 1px solid var(--accent);
      border-radius: 8px;
      text-decoration: none;
      font-weight: 600;
    }
    footer {
      color: var(--muted);
      font-size: 13px;
      text-align: center;
      margin-top: 40px;
    }
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <span class="tag">Google Apps Script</span>
      <h1>Gmail Slack連携</h1>
      <p class="lead">Google Apps Script で作成した業務自動化ツール</p>
    </header>

    <section id="about">
      <h2>このアプリについて</h2>
      <p>Gmail Slack連携は、Google Apps Script（GAS）で作成した、業務を自動化するためのツールです。あらかじめ設定した時間に、利用者本人が承認した Google のサービス（Gmail など）から情報を取得・整理し、Google スプレッドシートへの記録や Slack への通知を行うことで、手作業の負担を減らすことを目的としています。</p>
      <p>主な機能は次のとおりです。</p>
      <ul>
        <li>設定した時間での自動実行（時間主導型トリガー）</li>
        <li>Google のサービスからの情報の取得・整理</li>
        <li>処理結果の Google スプレッドシート等への記録</li>
        <li>利用者が指定した Slack ワークスペースへの通知</li>
      </ul>
      <p>本アプリは開発者本人と、開発者が許可した限られた利用者のみが使用するもので、一般公開や販売はしていません。</p>
      <a class="cta" href="#privacy">プライバシーポリシーを見る</a>
    </section>

    <section id="privacy">
      <h2>プライバシーポリシー</h2>
      <p class="date">制定日：2026年10月1日</p>

      <h3>1. 取得する情報</h3>
      <p>本アプリは、利用者が Google アカウントの承認画面で許可した範囲（Google スプレッドシート、Gmail、Google ドライブなど、承認画面に表示されたもの）に限り、Google のユーザーデータにアクセスします。許可されていないデータにはアクセスしません。</p>

      <h3>2. 利用目的</h3>
      <p>取得した情報は、本アプリの自動化処理（情報の取得・整理・記録・通知）を行うためだけに使用します。広告、販売、プロファイリング、機械学習モデルの学習など、その他の目的には使用しません。</p>

      <h3>3. 情報の保存</h3>
      <p>処理結果は、利用者自身の Google アカウント内（スプレッドシートなど）に保存されるほか、通知として利用者が指定した Slack ワークスペースに送信されます。開発者が管理する独自のサーバーに Google のユーザーデータを保存することはありません。</p>

      <h3>4. 第三者への提供</h3>
      <p>取得した情報は、上記の Slack への通知を除き、第三者に販売・提供・共有することはありません。Slack に送信された情報の取り扱いは、Slack のプライバシーポリシーに従います。ただし、法令に基づき開示を求められた場合を除きます。</p>

      <h3>5. Google API サービスのユーザーデータに関するポリシーへの準拠</h3>
      <p>本アプリによる Google API から受け取った情報の使用および他のアプリへの転送は、限定使用（Limited Use）の要件を含む <a href="https://developers.google.com/terms/api-services-user-data-policy" target="_blank" rel="noopener">Google API サービスのユーザーデータに関するポリシー</a>に準拠します。</p>

      <h3>6. アクセス権の取り消し</h3>
      <p>利用者は、いつでも <a href="https://myaccount.google.com/permissions" target="_blank" rel="noopener">Google アカウントの「サードパーティ製のアプリとサービス」</a>から、本アプリへのアクセス権を取り消すことができます。</p>

      <h3>7. お問い合わせ</h3>
      <p>本ポリシーに関するお問い合わせは、以下までご連絡ください。<br><a href="mailto:ryotatabu6376@gmail.com">ryotatabu6376@gmail.com</a></p>

      <h3>8. 改定</h3>
      <p>本ポリシーは必要に応じて改定することがあります。改定した場合は、このページでお知らせします。</p>
    </section>

    <footer>&copy; 2026 Gmail Slack連携</footer>
  </div>
</body>
</html>
