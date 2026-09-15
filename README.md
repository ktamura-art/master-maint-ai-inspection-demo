# マスタメンテ依頼　AI検査・例外管理デモ

マスタメンテナンス依頼の受付〜登録業務について、**「全件を人が確認する運用」から「AIとルールが全件を自動検査し、要確認案件だけを人が判断する例外管理型」への転換**が Power Platform で実現可能かを検討した、報告用のデモ画面です。

## 収録内容

| # | 画面 | 内容 |
|---|---|---|
| 01 | 結論 | できること／条件付き／AIでは解けないことの切り分け |
| 02 | 現状と目指す姿 | AS-IS / TO-BE と設計上の最重要ポイント |
| 03 | 実現アーキテクチャ | 全体構成図（4段の検査）、受付システムからの取り出し方式比較 |
| 04 | 動くデモ | 依頼書1件が「AI読解 → ルール検査 → 判定」を通る様子（3パターン） |
| 05 | 例外管理キュー | 要確認案件の一覧と理由コード体系 |
| 06 | 判定マトリクス | Power Automate でできること／できないこと（◎○△×） |
| 07 | 役割分担 | AIとルールベースの境界線。判定表の初版をAIで作るアプローチ |
| 08 | 懸念点・技術制約 | 公式ドキュメント確認済みの制約、AI利用コスト試算 |
| 09 | PoCの進め方 | 8週間のスケジュール、評価指標、必要データ |

## 注意

- 画面・数値はすべて**検討用のサンプル**であり、実測値・実装済み機能ではありません。
- デモの判定結果はサンプルデータによる固定応答で、実際のAI出力ではありません。
- 特定の企業・システムを指す固有名詞は含めていません（システムA/B/C 等の汎用表記）。

## 技術制約の出典（2026年9月時点）

- [SQL Server コネクタ](https://learn.microsoft.com/ja-jp/connectors/sql/) — 「SQLクエリの実行(V2)」はオンプレミス／ゲートウェイ接続では非対応、110秒タイムアウト、要求2MB／応答8MB
- [クラウドフローの制限事項](https://learn.microsoft.com/ja-jp/power-automate/limits-and-config) — 1フロー500アクション、ネスト8階層、実行保持30日
- [Power Automate ライセンスの種類](https://learn.microsoft.com/ja-jp/power-platform/admin/power-automate-licensing/types) — Premium 1ユーザー40,000アクション/日、Process 25万/日
- [ライセンスとAI Builder クレジット](https://learn.microsoft.com/ja-jp/ai-builder/credit-management) — シードクレジットは2026年11月1日に廃止、Copilot クレジットへ移行
- [ライセンスとCopilot クレジット](https://learn.microsoft.com/ja-jp/ai-builder/message-management) — 消費レート（基本 0.1CC/1Kトークン ほか）

---
静的HTML1枚（外部依存なし）。ローカルでは `index.html` をブラウザで開くだけで動作します。
