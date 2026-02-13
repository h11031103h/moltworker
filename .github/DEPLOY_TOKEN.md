# GitHub Actions デプロイ用 Cloudflare API トークン

デプロイが失敗する場合、API トークンの権限不足の可能性があります。

## 推奨: カスタムトークンを作成

1. https://dash.cloudflare.com/profile/api-tokens を開く
2. **Create Token** → **Create Custom Token**
3. 権限を次のように設定:
   - **Account** → **Account Settings** → Read
   - **Account** → **Workers Scripts** → Edit
   - **Account** → **Workers KV Storage** → Edit
   - **Account** → **Workers R2 Storage** → Edit
   - **Account** → **Durable Objects** → Edit
   - **Account** → **Containers** または **Cloudflare Sandbox** があれば → Edit
4. **Account Resources** で対象のアカウントを指定
5. **Continue to summary** → **Create Token**
6. 表示されたトークンをコピーし、GitHub の Secrets の `CLOUDFLARE_API_TOKEN` を**この新しいトークンに差し替え**

## テンプレート「Edit Cloudflare Workers」の場合

そのままで動くこともありますが、Containers（Sandbox）の権限が含まれていないとデプロイで失敗することがあります。上記のカスタムトークンに切り替えてください。
