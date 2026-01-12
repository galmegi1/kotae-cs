# Formspree トラブルシューティング

## ❌ 問題: "Form Not Found" エラー

### 確認事項チェックリスト

#### 1. フォームIDの確認
- [ ] Formspreeダッシュボードでフォームが作成されている
- [ ] フォームのステータスが「Active」になっている
- [ ] FORM ENDPOINTのURLが `https://formspree.io/f/xnnjaqok` で正しい

#### 2. HTMLの確認
- [ ] `contact.html` のフォームタグに `action="https://formspree.io/f/xnnjaqok"` がある
- [ ] `method="POST"` が設定されている
- [ ] スペルミス（xnnjaqok）がない

#### 3. Formspreeアカウントの確認
- [ ] メール認証が完了している
- [ ] ログインできている
- [ ] ダッシュボードでフォームが表示されている

---

## 🔧 解決方法

### 方法1: 新しいフォームを作成

1. Formspreeダッシュボードで「+ New Form」
2. フォーム名: `Kotae CS Test`
3. 通知先メール: あなたのメールアドレス
4. 新しいフォームID（例: `mvgodrlw`）を取得
5. `test-form.html` のフォームIDを更新してテスト

### 方法2: 直接メールアドレスを使用

Formspreeでは、フォームIDの代わりに直接メールアドレスを使う方法もあります：

```html
<form action="https://formspree.io/your-email@example.com" method="POST">
```

初回送信時に、Formspreeから確認メールが届きます。
メール内のリンクをクリックして有効化すれば使えるようになります。

### 方法3: Netlify Formsに切り替え

1. Webサイトを Netlify で公開
2. フォームに `data-netlify="true"` を追加
3. Formspree不要で、無料で自動的にフォーム機能が使える

---

## 📝 次のアクション

1. **test-form.htmlでテスト送信してみる**
2. それでもエラーが出る場合:
   - Formspreeダッシュボードのスクリーンショットを共有
   - エラーメッセージの詳細を教えてください

3. または、**Netlify Formsに切り替える**（推奨）

---

どの方法を試してみますか？
