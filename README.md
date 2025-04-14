---

## ✅ 洗練済み：README用「構造宣言」テンプレート（日本語）

md
## 🧱 アーキテクチャ構成（v3）

このテンプレートは、単なるNext.jsの雛形ではなく、  
**生成AIを組み込んだ本番想定のSaaS構築に耐える設計思想を体現した「拡張型アーキテクチャテンプレート」です。**

アプリケーションは以下のように責務ごとにディレクトリが分離されており、  
**テスト可能性・保守性・スケーラビリティを重視した構成**となっています。

```
src/
├── domain/              # 💡 ビジネスルール（エンティティ・値オブジェクトなど）
│   └── Document.ts
│
├── usecases/            # 🧠 アプリケーションロジック（ユースケース単位で振る舞いを定義）
│   └── createDocument.ts
│
├── repositories/        # 🧱 外部サービスとの接続層（Supabase, OpenAI, pgvector等）
│   ├── documentRepository.ts
│   ├── embeddingRepository.ts
│   └── openaiRepository.ts
│
├── interfaces/          # 🌐 入出力インターフェース層（APIルートやReact UI）
│   ├── api/
│   │   └── document/create.ts
│   └── ui/
│       ├── components/
│       ├── hooks/
│       ├── pages/ (任意)
│       └── contexts/
│
├── lib/                 # ⚙️ 技術固有の処理（Supabase / OpenAIクライアントなど）
│   ├── supabase/client.ts
│   └── openai/client.ts
│
├── schema/              # 📏 バリデーションスキーマ（zod）と型推論の中心
│   └── documentSchema.ts
│
├── types/               # 🧩 補助的な型定義（Supabaseの型や共通型など）
│   └── supabase.ts
│
└── tests/               # 🧪 各レイヤーに対するユニットテスト
    ├── usecases/createDocument.test.ts
    └── repositories/documentRepository.test.ts

---

### 🎯 この構成の特徴

- **責務に応じた明確なレイヤー分離**：ビジネスロジック、データ永続化、入出力処理を明確に区別  
- **副作用を排除した純粋なドメインロジック**：テストしやすく、拡張にも強い  
- **AIとの連携を構造の中に組み込む設計**：OpenAI APIや埋め込み生成を専用のリポジトリ層に隔離  
- **CI・RLS・型定義の整合性を前提とした開発体験**：壊れない構造を目指す

---

### 🧪 想定ユースケース

- 生成AIを活用したドキュメント自動生成サービス  
- pgvectorによる意味検索を備えたナレッジベースアプリ  
- Supabase＋Next.jsによるスケーラブルなSaaS開発  
- Clean Architectureの導入学習・実践

---

### 🔧 セットアップ

```bash
git clone https://github.com/YOUR_NAME/next-supabase-starter.git
cd next-supabase-starter
npm install
cp .env.example .env.local
npm run dev


### ✅ デプロイ
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/import/project?template=https://github.com/wktk1187/next-supabase-starter)

