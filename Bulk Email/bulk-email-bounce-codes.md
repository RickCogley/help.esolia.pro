---
title: バルクメールのエラーコード
date: 2022-04-19T09:55
description: バルクメールシステムで利用しているエラーコード
order: 1000
category: サービス詳細
tags:
  - バルクメール
  - エラーコード
---

バルクメール送信で利用しているシステムのエラーコード。

### Postmark バウンスエラー

| タイプ | コード | 説明 |
| ---- | ---- | ------------------ |
| HardBounce | 1 | ハードバウンス — サーバーは送信したメールを届けることが出来ませんでした。 (例: ユーザーが無い、メールボックスが無い). |
| Transient | 2 | 送信遅れ — The server could not temporarily deliver your message (例: Message is delayed due to network troubles). |
| Unsubscribe | 16 | 送信停止依頼 — Unsubscribe or Remove request. |
| Subscribe | 32 | サブスク依頼 — Subscribe request from someone wanting to get added to the mailing list. |
| AutoResponder | 64 | 自動応対 — 自動レスポンスメッセージが戻って来た (例: "手が離さない" 又は "休み中"). |
| AddressChange | 128 | アドレス変更依頼 — The recipient has requested an address change. |
| DnsError | 256 | DNSエラー — 一時的DNSエラーが発生した. |
| SpamNotification | 512 | スパム通知 — メッセージ届けたが、ユーザーがブロックを掛けたか、スパムやバルクメールとしてフラグを立てた。 |
| OpenRelayTest | 1024 | オープンリレー調査 — The NDR is actually a test email message to see if the mail server is an open relay. |
| Unknown | 2048 | 区別不可 — 区別が出来ないNDR. |
| SoftBounce | 4096 | ソフトバウンス — 一時的に送信したメールを届けることが出来ませんでした。 (例: メールボックスがいっぱい、アカウントが無効になっている、保存クォータをオーバしている、ハードディスク保存領域がもう無い). |
| VirusNotification | 8192 | ウイルス通知 — 受信メッセージにウイルスを検知したと言う通知。|
| ChallengeVerification | 16384 | スパム確認 — The bounce is a challenge asking for verification you actually sent the email. Typcial challenges are made by Spam Arrest, or MailFrontier Matador. |
| BadEmailAddress | 100000 | 無効なメールアドレス — メールアドレス事態が無効です。 |
| SpamComplaint | 100001 | スパム苦情 — 受信者が本メールを明示的にスパムとしてフラグを立てた。 |
| ManuallyDeactivated | 100002 | 手動無効化 — The email was manually deactivated. |
| Unconfirmed | 100003 | 一覧登録未確認 — The subscriber has not clicked on the confirmation link upon registration or import. |
| Blocked | 100006 | ISPブロック — コンテントやブラックリストによる、処理しているISPがブロックを掛けた。 |
| SMTPApiError | 100007 | SMTP API エラー — An error occurred while accepting an email through the SMTP API. |
| InboundError | 100008 | 処理失敗 — Unable to deliver inbound message to destination inbound hook. |
| DMARCPolicy | 100009 | DMARC規定 — Email rejected due DMARC Policy. |
| TemplateRenderingFailed | 100010 | テンプレート利用失敗 — メール送信をしようとした時、メールのコンテンツを作成することが出来なかった。 |