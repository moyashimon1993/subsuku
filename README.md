# SubSplit MVP (Next.js 14 + Tailwind)

**目的**: サブスクを“規約内で”管理・割り勘・リマインド。ID/パスワードは保存しません。

## セットアップ（ローカル）
```bash
# pnpm推奨（無ければ npm / yarn でOK）
pnpm i
pnpm dev  # http://localhost:3000
```

## 必須環境変数（.env.local）
```
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
STRIPE_SECRET_KEY=
STRIPE_WEBHOOK_SECRET=
```

## Vercelデプロイ
1. このリポジトリをGitHubにプッシュ → Vercelで **Import**  
2. `NEXT_PUBLIC_*` と `STRIPE_*` を **Project Settings → Environment Variables** に設定  
3. **Deploy**。動作確認 → `/api/health` がOKを返せば成功です。

## Stripe Webhook（任意）
- デプロイ後、Stripe CLIで：
```bash
stripe listen --forward-to https://YOUR_DOMAIN/api/webhooks/stripe
```
- 本番は `STRIPE_WEBHOOK_SECRET` を設定し、署名検証を実装してください。

## Supabase
- 認証/DBは未接続のプレースホルダです。DBスキーマは `supabase/schema.sql` を参照し、
  SupabaseのSQLエディタに貼り付けて実行してください。

## 免責
- 各サービスの利用規約（TOS）順守を前提とします。
