# zen-connect デザインガイドライン

## プロジェクト概要
**zen-connect**は瞑想版「サウナイキタイ」として、瞑想体験の共有とコミュニティ形成に特化したWebアプリケーションです。

## デザインコンセプト
「静寂の中の繋がり」- 瞑想の静けさと深さを保ちながら、ユーザー同士の温かなコミュニティを形成するデザイン

## 参考デザイン
**メインリファレンス**: [Simple Habit](https://www.simplehabit.com/) (80%)
- ダークモードベースの洗練されたデザイン
- クリーンで読みやすいタイポグラフィ
- ミニマルで機能的なレイアウト

**サブリファレンス**: 
- [Waking Up](https://wakingup.com/) - 自然要素のアニメーション
- [サウナイキタイ](https://sauna-ikitai.com/) - 体験記録の定型フォーマット
- 日本の伝統色・禅の美学

## カラーパレット

### プライマリーカラー
```css
/* ベースカラー */
--primary-dark: #1c222e;     /* ダークネイビー（メイン背景） */
--primary-light: #ffffff;    /* ホワイト（テキスト） */

/* アクセントカラー */
--accent-teal: #3fc0c7;      /* ティール（CTA、リンク） */
--accent-coral: #fd9074;     /* ソフトコーラル（重要な要素） */

/* 日本の伝統色（サブアクセント） */
--zen-indigo: #4c6cb3;       /* 藍色 */
--zen-charcoal: #36454f;     /* 墨色 */
--zen-sage: #9caf88;         /* 抹茶色 */
```

### セカンダリーカラー
```css
/* グレースケール */
--gray-50: #f8fafc;
--gray-100: #f1f5f9;
--gray-200: #e2e8f0;
--gray-300: #cbd5e1;
--gray-400: #94a3b8;
--gray-500: #64748b;
--gray-600: #475569;
--gray-700: #334155;
--gray-800: #1e293b;
--gray-900: #0f172a;
```

## タイポグラフィ

### フォントファミリー
```css
/* プライマリーフォント */
--font-primary: 'Avenir', 'Helvetica', 'Arial', 'Hiragino Kaku Gothic ProN', 'Hiragino Sans', 'Meiryo', sans-serif;

/* セカンダリーフォント（和文強調時） */
--font-secondary: 'Noto Sans JP', 'Hiragino Kaku Gothic ProN', sans-serif;
```

### フォントサイズ
```css
--text-xs: 0.75rem;    /* 12px */
--text-sm: 0.875rem;   /* 14px */
--text-base: 1rem;     /* 16px */
--text-lg: 1.125rem;   /* 18px */
--text-xl: 1.25rem;    /* 20px */
--text-2xl: 1.5rem;    /* 24px */
--text-3xl: 1.875rem;  /* 30px */
--text-4xl: 2.25rem;   /* 36px */
--text-5xl: 3rem;      /* 48px */
```

### フォントウェイト
```css
--font-light: 300;
--font-normal: 400;
--font-medium: 500;
--font-semibold: 600;
--font-bold: 700;
```

## レイアウト

### デザインシステム
- **レスポンシブデザイン**: モバイルファースト
- **グリッドシステム**: Flexbox + CSS Grid
- **ブレークポイント**: 
  - モバイル: 〜767px
  - タブレット: 768px〜1023px
  - デスクトップ: 1024px〜

### スペーシング
```css
--space-1: 0.25rem;   /* 4px */
--space-2: 0.5rem;    /* 8px */
--space-3: 0.75rem;   /* 12px */
--space-4: 1rem;      /* 16px */
--space-5: 1.25rem;   /* 20px */
--space-6: 1.5rem;    /* 24px */
--space-8: 2rem;      /* 32px */
--space-10: 2.5rem;   /* 40px */
--space-12: 3rem;     /* 48px */
--space-16: 4rem;     /* 64px */
--space-20: 5rem;     /* 80px */
```

### 余白の原則
- **大胆な余白**: コンテンツ周りに十分なスペース
- **垂直リズム**: 一貫した行間・要素間隔
- **ネガティブスペース**: 視覚的な静寂を重視

## UIコンポーネント

### ボタン
```css
/* プライマリーボタン */
.btn-primary {
  background: var(--accent-teal);
  color: var(--primary-light);
  border-radius: 8px;
  padding: 12px 24px;
  font-weight: var(--font-medium);
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* セカンダリーボタン */
.btn-secondary {
  background: transparent;
  color: var(--accent-teal);
  border: 2px solid var(--accent-teal);
  border-radius: 8px;
  padding: 10px 22px;
}
```

### カード
```css
.card {
  background: var(--gray-800);
  border-radius: 12px;
  padding: var(--space-6);
  border: 1px solid var(--gray-700);
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
}
```

### フォーム
```css
.form-input {
  background: var(--gray-700);
  border: 1px solid var(--gray-600);
  border-radius: 8px;
  padding: 12px 16px;
  color: var(--primary-light);
  font-size: var(--text-base);
}

.form-input:focus {
  border-color: var(--accent-teal);
  outline: none;
  box-shadow: 0 0 0 3px rgba(63, 192, 199, 0.1);
}
```

## アニメーション・インタラクション

### アニメーション原則
- **微細なアニメーション**: 300ms以下の短い時間
- **イージング**: ease-in-out
- **自然な動き**: 瞑想の呼吸をイメージした緩やかな動き

### ホバー効果
```css
.interactive:hover {
  transform: translateY(-2px);
  transition: transform 0.2s ease-in-out;
}
```

## アイコン・イラスト

### アイコンスタイル
- **ミニマルライン**: 細線のアウトラインアイコン
- **自然モチーフ**: 木、雲、鳥、山などの自然要素
- **サイズ**: 16px、24px、32px、48px

### イラスト要素
- **抽象的な自然**: 雲、波、山のシルエット
- **グラデーション**: 微細なグラデーション効果
- **アニメーション**: 浮遊、回転などの緩やかな動き

## 体験記録UI

### 記録フォーマット
```
場所: [テキスト入力] (例：自宅の和室、公園のベンチ)
時間: [時間選択] (例：朝5:00-5:20)
瞑想法: [選択式] (例：マインドフルネス、ヴィパッサナー)
心の状態: [タグ選択] (例：落ち着いた、集中、穏やか)
気づき: [フリーテキスト] (例：鳥の鳴き声が心地よかった)
公開設定: [公開/非公開/フォロワーのみ]
```

### 記録表示
- **カード形式**: 各記録を独立したカードで表示
- **タイムライン**: 時系列での記録表示
- **フィルター**: 場所、時間、瞑想法での絞り込み

## レスポンシブデザイン

### モバイル（〜767px）
- **単一カラム**レイアウト
- **大きなタップエリア**（44px以上）
- **シンプルなナビゲーション**（ハンバーガーメニュー）

### タブレット（768px〜1023px）
- **2カラム**レイアウト
- **タブナビゲーション**
- **カード表示**の最適化

### デスクトップ（1024px〜）
- **3カラム**レイアウト
- **サイドバーナビゲーション**
- **詳細情報**の表示

## Tailwind CSS設定

### カスタムコンフィグ
```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: {
          dark: '#1c222e',
          light: '#ffffff',
        },
        accent: {
          teal: '#3fc0c7',
          coral: '#fd9074',
        },
        zen: {
          indigo: '#4c6cb3',
          charcoal: '#36454f',
          sage: '#9caf88',
        }
      },
      fontFamily: {
        primary: ['Avenir', 'Helvetica', 'Arial', 'Hiragino Kaku Gothic ProN', 'sans-serif'],
        secondary: ['Noto Sans JP', 'Hiragino Kaku Gothic ProN', 'sans-serif'],
      },
      animation: {
        'float': 'float 3s ease-in-out infinite',
        'fade-in': 'fadeIn 0.3s ease-in-out',
      }
    }
  }
}
```

## アクセシビリティ

### 基本原則
- **高コントラスト**: 4.5:1以上の色彩コントラスト
- **キーボード操作**: 全機能のキーボードアクセス
- **スクリーンリーダー**: 適切なaria-label、alt属性
- **フォーカス表示**: 明確なフォーカス状態

### ダークモード対応
```css
/* ライトモード用の代替カラー */
@media (prefers-color-scheme: light) {
  :root {
    --primary-dark: #ffffff;
    --primary-light: #1c222e;
    --gray-800: #f1f5f9;
    --gray-700: #e2e8f0;
  }
}
```

## 実装フェーズ

### Phase 1: 基盤UI（MVP）
- [ ] 認証画面（ログイン・新規登録）
- [ ] プロフィール画面
- [ ] 体験記録作成・編集フォーム
- [ ] 体験記録一覧表示

### Phase 2: コミュニティ機能
- [ ] ユーザー検索・フォロー
- [ ] タイムライン表示
- [ ] いいね・コメント機能
- [ ] 通知機能

### Phase 3: 拡張機能
- [ ] 瞑想統計・分析
- [ ] イベント機能
- [ ] 検索・フィルター強化
- [ ] PWA対応

## 参考資料

### デザインリファレンス
- [Simple Habit](https://www.simplehabit.com/) - メインリファレンス
- [Waking Up](https://wakingup.com/) - 自然要素・アニメーション
- [サウナイキタイ](https://sauna-ikitai.com/) - 体験記録フォーマット

### 技術リファレンス
- [Tailwind CSS](https://tailwindcss.com/)
- [Next.js](https://nextjs.org/)
- [React](https://react.dev/)

---

**作成日**: 2025年1月5日  
**ステータス**: 設計完了・実装準備中  
**次のステップ**: Next.jsプロジェクトセットアップとコンポーネント作成