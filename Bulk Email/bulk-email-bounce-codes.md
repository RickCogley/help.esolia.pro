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
| HardBounce | 1 | ハードバウンス — The server was unable to deliver your message (ex: unknown user, mailbox not found). |
| Transient | 2 | 送信遅れ — The server could not temporarily deliver your message (ex: Message is delayed due to network troubles). |
| Unsubscribe | 16 | 送信停止依頼 — Unsubscribe or Remove request. |
| Subscribe | 32 | サブスク依頼 — Subscribe request from someone wanting to get added to the mailing list. |
| AutoResponder | 64 | 自動応対 — Automatic email responder (ex: "Out of Office" or "On Vacation"). |
| AddressChange | 128 | アドレス変更依頼 — The recipient has requested an address change. |
| DnsError | 256 | DNSエラー — A temporary DNS error. |
| SpamNotification | 512 | スパム通知 — The message was delivered, but was either blocked by the user, or classified as spam, bulk mail, or had rejected content. |
| OpenRelayTest | 1024 | オープンリレー調査 — The NDR is actually a test email message to see if the mail server is an open relay. |
| Unknown | 2048 | 区別不可 — Unable to classify the NDR. |
| SoftBounce | 4096 | ソフトバウンス — Unable to temporarily deliver message (i.e. mailbox full, account disabled, exceeds quota, out of disk space). |
| VirusNotification | 8192 | ウイルス通知 — The bounce is actually a virus notification warning about a virus/code infected message. |
| ChallengeVerification | 16384 | スパム確認 — The bounce is a challenge asking for verification you actually sent the email. Typcial challenges are made by Spam Arrest, or MailFrontier Matador. |
| BadEmailAddress | 100000 | 無効なメールアドレス — The address is not a valid email address. |
| SpamComplaint | 100001 | スパム苦情 — The subscriber explicitly marked this message as spam. |
| ManuallyDeactivated | 100002 | 手動無効化 — The email was manually deactivated. |
| Unconfirmed | 100003 | 一覧登録未確認 — The subscriber has not clicked on the confirmation link upon registration or import. |
| Blocked | 100006 | ISPブロック — Blocked from this ISP due to content or blacklisting. |
| SMTPApiError | 100007 | SMTP API エラー — An error occurred while accepting an email through the SMTP API. |
| InboundError | 100008 | 処理失敗 — Unable to deliver inbound message to destination inbound hook. |
| DMARCPolicy | 100009 | DMARC規定 — Email rejected due DMARC Policy. |
| TemplateRenderingFailed | 100010 | テンプレート利用失敗 — An error occurred while attempting to render your template. |