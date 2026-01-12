# Formspree 設定完了ガイド

## ✅ 修正完了項目

以下のファイルを修正しました：
1. `contact.html` - フォームにFormspree連携を追加
2. `js/main.js` - Formspree送信用にJavaScriptを最適化

---

## 📋 **設定手順（あと3ステップ！）**

### **STEP 1: Formspreeアカウント作成**

1. **Formspree公式サイトにアクセス**
   ```
   https://formspree.io/
   ```

2. **「Get Started」または「Sign Up」をクリック**

3. **アカウント登録**
   - メールアドレスとパスワードを入力
   - または、Googleアカウントでサインアップ（推奨）

4. **メール認証**
   - 登録したメールアドレスに確認メールが届きます
   - メール内のリンクをクリックして認証完了

---

### **STEP 2: フォーム作成**

1. **ダッシュボードにログイン後、「+ New Form」をクリック**

2. **フォーム情報を入力**
   - **Form Name（フォーム名）**: `Kotae CS お問い合わせフォーム`
   - **Email（通知先）**: あなたのメールアドレス（問い合わせ通知を受け取るアドレス）

3. **「Create Form」をクリック**

4. **フォームIDを確認**
   - 画面に表示されるエンドポイントURL:
     ```
     https://formspree.io/f/YOUR_FORM_ID
     ```
   - 例: `https://formspree.io/f/mwpklzqr`
   - **YOUR_FORM_ID** の部分（例: `mwpklzqr`）をメモしてください

---

### **STEP 3: contact.htmlを更新**

1. **`contact.html` ファイルを開く**

2. **48行目付近を探す**
   ```html
   <form id="contactForm" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```

3. **YOUR_FORM_IDを実際のIDに置き換え**
   - 修正前: `https://formspree.io/f/YOUR_FORM_ID`
   - 修正後: `https://formspree.io/f/mwpklzqr` （あなたのID）

4. **103行目付近を探す（オプション）**
   ```html
   <input type="hidden" name="_next" value="https://your-domain.com/contact.html?success=true">
   ```
   - `your-domain.com` を実際のドメインに置き換え
   - ローカルテスト時は削除してもOK（Formspreeのデフォルト完了ページが表示されます）

5. **ファイルを保存**

---

## 🎉 **設定完了！**

### **テスト方法**

1. **contact.htmlをブラウザで開く**

2. **フォームに情報を入力して送信**

3. **以下を確認**
   - ✅ Formspreeのダッシュボードにデータが届く
   - ✅ 設定したメールアドレスに通知メールが届く
   - ✅ 送信者に自動返信メール（設定した場合）

---

## ⚙️ **Formspree追加設定（オプション）**

### **1. 自動返信メールの設定**

Formspreeダッシュボード → あなたのフォーム → 「Settings」 → 「Autoresponse」

```
Subject: お問い合わせありがとうございます - Kotae CS

Body:
{name}様

この度はKotae CSにお問い合わせいただき、誠にありがとうございます。

お問い合わせ内容を確認いたしました。
担当者より24時間以内にご返信させていただきます。

今しばらくお待ちくださいませ。

━━━━━━━━━━━━━━━━━━
Kotae CS
代表者：趙早紀（チョウ サキ）
所在地：대한민국 경기도 분당구
事業者登録番号：173-16-02670
━━━━━━━━━━━━━━━━━━
```

---

### **2. スパム対策の設定**

Formspreeダッシュボード → あなたのフォーム → 「Settings」 → 「Spam Prevention」

- ✅ **reCAPTCHA** を有効化（推奨）
- ✅ **Honeypot** は既に設定済み（`_gotcha`フィールド）

---

### **3. 通知メールのカスタマイズ**

Formspreeダッシュボード → あなたのフォーム → 「Settings」 → 「Notifications」

**メール件名のカスタマイズ:**
- `_subject` フィールドで既に設定済み: 「【Kotae CS】新規お問い合わせ」

**メールフォーマットの例:**
```
新規お問い合わせがありました

会社名: {company}
お名前: {name}
メールアドレス: {email}
電話番号: {phone}
業種: {industry}
希望プラン: {plan}
月間問い合わせ件数: {volume}

相談内容:
{message}
```

---

## 📊 **Formspree無料プランの制限**

| 項目 | 制限 |
|------|------|
| 月間送信数 | 50件まで |
| フォーム数 | 無制限 |
| ファイル添付 | 10MB/月 |
| スパム対策 | ✅ |
| 自動返信 | ✅ |

**💡 アップグレードが必要な場合:**
- 月50件を超える場合: $10/月（250件まで）
- 詳細: https://formspree.io/plans

---

## 🔧 **トラブルシューティング**

### **問題1: フォーム送信後、エラーが出る**

**原因:** フォームIDが間違っている

**解決策:**
1. Formspreeダッシュボードで正しいフォームIDを確認
2. `contact.html` の `action="https://formspree.io/f/YOUR_FORM_ID"` を修正

---

### **問題2: メール通知が届かない**

**原因:** 迷惑メールフォルダに入っている

**解決策:**
1. 迷惑メールフォルダを確認
2. `noreply@formspree.io` を連絡先に追加
3. Formspreeダッシュボード → Settings → Notifications で通知先メールアドレスを確認

---

### **問題3: 送信完了メッセージが表示されない**

**原因:** `_next` のURLが間違っている

**解決策:**
1. `contact.html` の103行目付近を確認
2. `https://your-domain.com/contact.html?success=true` のドメインを実際のドメインに変更
3. ローカルテスト時は `file:///C:/your-path/contact.html?success=true` のようなフルパスに変更

---

## 📞 **Formspreeサポート**

- 公式ドキュメント: https://help.formspree.io/
- コミュニティフォーラム: https://community.formspree.io/

---

## ✅ **最終チェックリスト**

送信前に以下を確認してください：

- [ ] Formspreeアカウントを作成した
- [ ] 新しいフォームを作成し、フォームIDを取得した
- [ ] `contact.html` の `YOUR_FORM_ID` を実際のIDに置き換えた
- [ ] `contact.html` の `your-domain.com` を実際のドメインに置き換えた（本番環境のみ）
- [ ] ファイルを保存した
- [ ] ブラウザでテスト送信した
- [ ] Formspreeダッシュボードでデータを確認した
- [ ] 通知メールが届いたことを確認した

すべてチェックが完了したら、設定完了です！🎉

---

**ご不明な点がございましたら、お気軽にお問い合わせください。**
