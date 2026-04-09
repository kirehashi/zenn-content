---
title: "Claudeの2026年3月が凄すぎたので全部まとめる — 14以上のローンチ、Mythos流出事件"
emoji: "⚡"
type: "tech"
topics: ["Claude", "Anthropic", "AI", "LLM", "ClaudeCode"]
published: false
---

## はじめに

2026年3月のAnthropicは、控えめに言って異常だった。

新モデル、PC遠隔操作、音声入力、ビジュアライゼーション、メモリ機能の無料化 — 主要アップデートだけで14件以上。Claude Codeに至っては2週間で7バージョンをリリースする狂気のペース。そして月末には、未発表の次世代モデル「Claude Mythos」の存在が情報漏洩で発覚するという事件まで起きた。

正直、追いきれなかった。なので自分の学習も兼ねて、3月に起きたことを時系列で全部まとめる。

---

## 前提：2月のモデルリリースが土台

3月のアップデートを理解するには、2月のモデルリリースを押さえておく必要がある。

| モデル | リリース日 | 特徴 |
|--------|-----------|------|
| **Claude Opus 4.6** | 2月5日 | 最上位モデル。SWE-bench 80.8%。100万トークンコンテキスト。法務・金融・コーディングで他社を上回るベンチマーク |
| **Claude Sonnet 4.6** | 2月17日 | Opusの1/5の価格でほぼ同等の性能。SWE-bench 79.6%。Computer Use 72.5%（Opus 72.7%とほぼ同等） |

Sonnet 4.6はOpusとほぼ同じ性能を$3/$15（Opusは$15/$75）で提供するという衝撃的なコスパで、開発者コミュニティに大きなインパクトを与えた。Sonnet 4.5からの乗り換えで70%のユーザーが4.6を好んだという調査結果もある。

この2つの新モデルの上に、3月の機能群が次々と載っていく。

---

## 3月のアップデート時系列

### 3月2日 — メモリ機能が全ユーザーに無料開放

これまで有料プラン限定だったメモリ機能（過去の会話を記憶し、セッションをまたいで文脈を引き継ぐ機能）が、無料ユーザーを含む全ユーザーに開放された。

さらに、他社AIチャットボット（ChatGPT等）からのコンテキストインポートツールも同時公開。競合からの乗り換えを明確に狙った動き。

### 3月11日 — Excel/PowerPoint アドイン強化

Claude for ExcelとClaude for PowerPointのアドインがアップデート。

- 会話の完全なコンテキストを共有可能に
- Skills（定型処理機能）のサポート追加
- Amazon Bedrock、Google Vertex AI、Microsoft FoundryからLLMゲートウェイ経由で接続可能に

エンタープライズ向けの統合がかなり進んだ印象。日常業務のExcel/PowerPoint内でClaude を使えるようになるのは、非エンジニア層への普及において大きい。

### 3月12日 — インタラクティブ・ビジュアライゼーション

Claudeが会話内でチャート、ダイアグラム、その他のインタラクティブな可視化をインラインで生成できるようになった。全プラン（無料含む）でベータ提供。

技術的には、ClaudeがHTML/CSS/JavaScriptを書き、Chart.js、D3.js、Plotly.js等のライブラリを呼び出してブラウザ内でレンダリングする仕組み。データポイントにホバーして詳細を表示したり、カテゴリのトグルも可能。

単にテキストで回答を返す時代から、**データを視覚的に操作できるインターフェース**へのシフトが始まった。

### 3月17日 — Cowork 永続エージェントスレッド

Pro/Maxプラン向けに、Coworkで永続的なエージェントスレッドがリリース。モバイルとデスクトップの両方からタスク管理が可能に。

### 3月23日 — Computer Use（PCの自動操作）

**3月最大のアップデート。** Claude がユーザーのデスクトップを「見て」「操作する」Computer Use機能がリサーチプレビューとしてリリースされた。

- ボタンのクリック、アプリの起動、スプレッドシートの操作、マルチステップのワークフローを人間の介入なしに実行
- 適切なAPI連携（Google Calendar、Slack等）がない場合、**人間と同じように画面を見てマウスとキーボードで操作**するフォールバック動作
- Cowork と Claude Code の両方で利用可能
- **現時点ではMacのみ対応**（Windows/Linuxは未対応）

同時にDispatch機能も公開。スマートフォンからタスクを指示すると、離席中にClaudeがPCを操作してタスクを完了する — 文字通り「AIに仕事を任せて出かける」が可能になった。

Anthropicは安全性について「Claudeはミスをする可能性があり、新しいアプリにアクセスする前に必ず許可を求める」と注意喚起している。

### 3月25日 — モバイルアプリでインタラクティブビジュアル

iOS/Androidアプリでもインタラクティブなチャート・ダイアグラムが利用可能に。

---

## Claude Code: 2週間で7バージョンの狂騒

3月のClaude Codeは異常なリリース速度だった。v2.1.80（3/20）からv2.1.88（3/31）まで、ほぼ毎日のようにアップデートが投下された。

### 主要な新機能

| 機能 | 日付 | 概要 |
|------|------|------|
| **Voice Mode** | 3月初旬 | `/voice`コマンドで音声入力。スペースバー長押しのPush-to-Talk方式。20言語対応 |
| **Channels** | 3月20日 | Telegram/Discord/iMessageからClaude Codeセッションを遠隔操作。MCP準拠の公式プラグイン |
| **Remote Control** | 2月〜（3月最適化） | QRコード/URLでスマホからローカルセッションに接続。ソースコードはクラウドに上がらない設計。3月にポーリング頻度を300倍効率化 |
| **PowerShellプレビュー** | 3月26日 | Windows向けPowerShellツールをオプトインプレビューで提供 |
| **Computer Use** | 3月23日 | Claude CodeからもMacアプリの直接操作が可能に |
| **/loop** | 3月 | 定期実行コマンド。`/loop 5m /foo`で5分ごとにコマンド実行 |

### 品質改善・バグ修正の嵐

- 長時間セッションのメモリリーク修正
- Windows CRLF改行の二重化問題修正
- alt-screenのフリッカーフリーレンダリング
- 起動速度30ms短縮、大規模リポジトリでメモリ使用量80MB削減
- MCP環境変数、条件付きフックフィルタリング等のエコシステム強化

全体として、Claude Codeは「ターミナルに張り付くAIツール」から**「どこからでも使える自律エージェント」**へと明確に進化した。

---

## 月末の衝撃：Claude Mythos 流出事件

### 何が起きたか

3月26日、AnthropicのCMS（コンテンツ管理システム）の設定ミスにより、約3,000件の未公開ドキュメントが一般に検索可能な状態になっていたことが発覚。その中に、未発表の次世代モデル**「Claude Mythos」**（社内コードネーム: Capybara）のドラフトブログ記事が含まれていた。

### Mythosとは何か

- Opusよりもさらに上位の新しいモデル層
- コーディング、学術推論、サイバーセキュリティ等でOpus 4.6を大幅に上回るスコア
- Anthropic自身が「これまでに構築した中で最も強力なモデル」と記述
- 早期アクセスの顧客によるトライアル中

### 安全性への懸念

流出ドキュメントによると、Anthropicは政府高官に対して**「Mythosは大規模サイバー攻撃の可能性を著しく高める」**と非公式に警告していた。このレベルの能力を持つエージェントは、最小限の人間の関与で複雑な作戦を計画・実行できるとされる。

### さらに追い打ち

3月31日には、Claude Codeのソースコードが別の経路で漏洩するという二重のセキュリティインシデントが発生。3月はAnthropicにとって、プロダクト面での躍進とセキュリティ面での失態が同居する月となった。

---

## 需要過多：ピーク時間帯の利用制限

これだけのアップデートにユーザーが殺到した結果、3月後半にはGPU容量が逼迫。

- **平日8:00〜14:00（米国東部時間）** にPro/Maxプランの利用制限を強化
- 代わりにオフピーク時の利用量を2倍にする期間限定プロモーション（3/13〜3/28）を実施
- Free/Pro/Max/Teamプラン全てが対象

需要に供給が追いつかない状況は、Anthropicの急成長とインフラ課題を如実に示している。

---

## 旧モデルの引退予告

Anthropicは以下の発表も行った：

- **Claude Sonnet 4.5 / Sonnet 4 の100万トークンベータを2026年4月30日で終了**
- Sonnet 4.6 / Opus 4.6への移行を推奨（こちらは標準価格で100万トークン対応、ベータヘッダ不要）

---

## 3月を俯瞰して：何が変わったのか

3月のアップデートを並べて見ると、Anthropicの戦略が見える。

**1. 「チャットボット」から「自律エージェント」への転換**

Computer Use + Dispatch + Cowork永続スレッド + Claude Code Remote Control。これらを組み合わせると「スマホからタスクを指示→Claudeが自分のPCを操作して完了→結果をスマホで確認」という完全なエージェントループが成立する。3月はその構成要素が全て揃った月だった。

**2. 非エンジニアへの間口拡大**

メモリ無料化、Excel/PowerPointアドイン、インタラクティブ可視化。エンジニア以外がClaude を日常業務で使えるようにするピースが次々と追加された。

**3. 開発者ツールとしての成熟**

Claude Codeの音声入力、Channels、/loop、PowerShell対応。開発者がClaude Codeを本番ワークフローに組み込むための機能が急速に整備された。

---

## 所感

正直に言って、この1ヶ月の動きを追いきれていなかった。まとめてみて改めて思うのは、Claudeは「賢いチャットボット」のフェーズをとっくに通り過ぎていて、**「自分のPCを操作して仕事をしてくれるエージェント」**になりつつあるということだ。

個人的に最もインパクトが大きいと感じたのは、Computer Use + Dispatchの組み合わせ。「AIに仕事を任せて出かける」が文字通り可能になった。まだMac限定のリサーチプレビューではあるが、これが安定してWindows/Linuxに広がったとき、働き方が根本的に変わる可能性がある。

一方で、Mythos流出とClaude Codeソースコード漏洩という2つのセキュリティインシデントは見逃せない。「最も強力なAI」を作る会社が、基本的な情報管理でミスをする — この矛盾は、AI企業の成長速度とガバナンス体制のギャップを浮き彫りにしている。

AIの進化速度はもはや月単位ではなく週単位。「追いかける」のではなく「触って理解する」方が効率的なフェーズに入ったと感じる。

---

## 参考情報

### 公式

- [Anthropic: Introducing Claude Sonnet 4.6](https://www.anthropic.com/news/claude-sonnet-4-6)
- [Anthropic: Introducing Claude Opus 4.6](https://www.anthropic.com/news/claude-opus-4-6)
- [Claude Platform Release Notes](https://platform.claude.com/docs/en/release-notes/overview)
- [Claude Code Changelog](https://code.claude.com/docs/en/changelog)

### 報道・解説

- [The New Stack: Anthropic's Madcap March](https://thenewstack.io/anthropic-march-2026-roundup/)
- [Fortune: Anthropic Mythos AI Model Revealed in Data Leak](https://fortune.com/2026/03/26/anthropic-says-testing-mythos-powerful-new-ai-model-after-data-leak-reveals-its-existence-step-change-in-capabilities/)
- [Fortune: Anthropic Leaks Claude Code Source Code](https://fortune.com/2026/03/31/anthropic-source-code-claude-code-data-leak-second-security-lapse-days-after-accidentally-revealing-mythos/)
- [CNBC: Claude Can Now Use Your Computer](https://www.cnbc.com/2026/03/24/anthropic-claude-ai-agent-use-computer-finish-tasks.html)
- [MacRumors: Claude Memory Free for All Users](https://www.macrumors.com/2026/03/02/anthropic-memory-import-tool/)
- [VentureBeat: Sonnet 4.6 Matches Flagship Performance at 1/5 Cost](https://venturebeat.com/technology/anthropics-sonnet-4-6-matches-flagship-ai-performance-at-one-fifth-the-cost/)

### Claude Code

- [Claude Code Docs: Remote Control](https://code.claude.com/docs/ja/remote-control)
- [NxCode: Claude Code Remote Control Guide](https://www.nxcode.io/resources/news/claude-code-remote-control-mobile-terminal-handoff-guide-2026)
- [Claude Code Channels vs Remote Control](https://docs.bswen.com/blog/2026-03-21-claude-channels-vs-remote-control/)

---

*この記事はAI（Claude）による調査・下書きをベースに、筆者が編集・加筆したものです。*
