# ai-service-watch (crawler information)

このリポジトリは、下記の User-Agent を名乗るクローラの**説明ページ**です。
アクセスログでこの名前を見つけて来られた方向けの情報をまとめています。

*This repository is the information page for the crawler identified by the User-Agent below.
If you found this URL in your access logs, this page explains what it is.*

---

## User-Agent

```
Mozilla/5.0 (compatible; ai-service-watch/0.1; +https://github.com/kairyu33/ai-service-watch-bot)
```

## 目的 / Purpose

公開されている料金ページ・利用規約ページから、**価格や上限値などの事実データ**を取得し、
その変化を時系列で記録しています。個人が運営する小規模なプロジェクトです。

*Collects factual data — prices, plan names, usage limits — from publicly available
pricing and terms pages, and records how they change over time.
This is a small project operated by an individual in Japan.*

## アクセスの頻度と作法 / Crawl behavior

| | |
| --- | --- |
| 頻度 | 1サイトあたり **1日1回まで**（ページの取得に失敗した場合のみ最大3回まで再試行） |
| 間隔 | 同一ドメインへの連続アクセスは**5秒以上**空けます |
| robots.txt | **毎回の実行時に取得して確認**し、`Disallow` されている URL は取得しません |
| 対象 | 公開ページのみ。ログインが必要なページや非公開ページにはアクセスしません |
| 認証 | 一切行いません。フォーム送信もしません |

*One page fetch per site per day at most. At least 5 seconds between requests to the
same domain. robots.txt is fetched and evaluated on every run, and `Disallow` rules are
honored. Only publicly accessible pages are visited — never login-protected or
non-public pages. No authentication, no form submission.*

## 取得しているもの / What is collected

**取得するもの**

- プラン名、金額、通貨、税込/税抜の別
- 無料枠の有無とその上限
- 利用上限（例: 月◯分、◯クレジット）
- 特定条項の有無

**取得しないもの / 行わないこと**

- 個人情報は一切取得しません
- ページ本文・説明文・キャッチコピーの**転載や再配信は行いません**
- 取得したページテキストは、抽出処理をやり直すために内部保存するのみで、外部へ公開しません
- 画像・動画・添付ファイルの収集は行いません

*Only factual values are extracted. No personal data is collected. Page copy is never
republished or redistributed — raw text is retained internally solely so that extraction
can be re-run without re-crawling your site.*

## 停止・除外のご依頼 / How to stop it

**方法1: robots.txt に記載する（即座に有効・確実）**

```
User-agent: ai-service-watch
Disallow: /
```

毎回の実行時に robots.txt を確認しているため、この記述だけでアクセスは止まります。
こちらへのご連絡は不要です。

**方法2: このリポジトリの [Issues](https://github.com/kairyu33/ai-service-watch-bot/issues) に投稿する**

ドメインをお知らせいただければ、監視対象から削除します。理由の説明は不要です。

*Either add the robots.txt rule above (takes effect on the next run, no need to contact
us), or open an Issue here with your domain. We will remove it. No explanation needed.*

## 不具合・過剰なアクセスを見つけた場合 / Reporting problems

意図しない挙動で負荷をかけてしまっていた場合は、[Issues](https://github.com/kairyu33/ai-service-watch-bot/issues)
でお知らせください。速やかに停止して原因を確認します。

*If this crawler is causing load or behaving unexpectedly, please open an Issue.
It will be stopped promptly while the cause is investigated.*

---

<sub>最終更新: 2026-08-02</sub>
