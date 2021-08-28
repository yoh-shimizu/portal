# ヤフオクの初回入札情報を自動取得+slack通知するシステムを作ってみた

## 概要

両親がヤフオクをしていた際に
「初回入札の情報がメールとかで通知されれば商品の準備ができて楽なんだよね〜」
ということを話していた。

現状、初回入札情報は「新着情報ページ」でしか通知されず、
メールでの通知設定が不可である。

## 解決策

定期的に「新着情報ページ」の初回入札情報を取得し、
Slackで通知するようにする。

## 主な使用環境

- Raspberry Pi3
- Docker
- Python

## 実装

### ソースコード

- `https://github.com/yoh-shimizu/yahoo_auction`

上記リンクのファイルをダウンロードして展開する。
以下情報については割愛。

- Raspberry PiでのDocker環境構築について
- SlackのWebhook機能について

### 定期実行

cronを使用。

```crontab
# 例：2時間毎に実行する場合
0 */2 * * * docker exec python python /app/yahoo_auction/main.py
```
