# Family Schedule Hub

A personal web app that **aggregates multiple Google Calendars into one unified view** — with color-coded activities and automatic **conflict detection** for overlapping events. Built to solve a real family scheduling problem: coordinating swimming, art class, and skating lessons across different calendars.

> **Note**: This app is deployed as a private instance. The repository includes full setup instructions so you can run your own.

## ✨ Features

- Aggregates multiple Google Calendars in a single view
- **Conflict detection**: warns when two events overlap at the same time
- Color-coded categories (Swimming, Art Class, Skating, etc.)
- Week / next-week view toggle
- OAuth 2.0 authentication with Google
- Deployed on Vercel (private, invite-only)

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | Next.js 14 (App Router) |
| Language | TypeScript |
| API | Google Calendar API v3 |
| Auth | OAuth 2.0 (Google) |
| Styling | Tailwind CSS |
| Deployment | Vercel |

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- A Google Cloud project with **Calendar API** enabled
- OAuth 2.0 credentials (Client ID + Client Secret)

### Installation

```bash
git clone https://github.com/YOSHl/family-schedule-hub.git
cd family-schedule-hub
npm install
cp .env.example .env.local
```

### Configure Google OAuth

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a project → Enable **Google Calendar API**
3. Create OAuth 2.0 credentials (Web application)
4. Add `http://localhost:3000/api/auth/callback/google` as an authorized redirect URI

```env
GOOGLE_CLIENT_ID=...
GOOGLE_CLIENT_SECRET=...
NEXTAUTH_SECRET=...          # Generate with: openssl rand -base64 32
NEXTAUTH_URL=http://localhost:3000

# Calendar IDs to aggregate (comma-separated)
CALENDAR_IDS=primary,family@group.calendar.google.com
```

```bash
npm run dev
```

## 📁 Project Structure

```
family-schedule-hub/
├── app/
│   ├── page.tsx              # Main calendar view
│   ├── api/
│   │   ├── auth/             # NextAuth OAuth handler
│   │   └── events/           # Google Calendar API proxy
├── components/
│   ├── CalendarView.tsx      # Week grid
│   ├── EventCard.tsx         # Individual event display
│   └── ConflictAlert.tsx     # Overlap warning
├── lib/
│   ├── google-calendar.ts    # Calendar API client
│   └── conflict-detector.ts  # Overlap detection logic
└── .env.example
```

## 🔑 Keywords

`React` · `TypeScript` · `Next.js` · `Google Calendar API` · `OAuth 2.0` · `REST API` · `Tailwind CSS` · `Vercel`

## 👨‍💻 Story Behind This Project

Managing kids' activities — swimming on Tuesday, art class Wednesday, skating Saturday — across multiple Google Calendars was causing double-bookings. I built this to see the whole week at a glance and get warned the moment two things overlapped. It solved a real problem in the first week of use.

This project was developed with **Claude Code** (Anthropic). AI-assisted development was used throughout, from OAuth setup to the conflict detection algorithm.

---

## 日本語

複数のGoogleカレンダー（自分・家族）を一画面に集約し、予定の重複を検出してくれる家族スケジュール統合ビューアです。

### このプロジェクトについて

子どもの水泳・Artクラス・Skatingの予定を平日にやりくりするのが複雑になってきたため、自分の家族のために作りました。TypeScript・React・Google Calendar APIを「自分ごと」の問題を解く形で実装しています。

「これは自分の家族のために作った」と面接で言える一枚は、技術力以上に面接官の記憶に残ります。

### 機能

- 複数のGoogleカレンダーを同一画面に表示
- **重複検出**：同じ時間帯の予定が重なると警告表示
- 子ども活動（水泳・Art・Skating）をカテゴリ別に色分け
- 今週/来週のビュー切り替え
- OAuth 2.0でGoogleと連携

### Google OAuth設定手順

1. [Google Cloud Console](https://console.cloud.google.com/) でプロジェクトを作成
2. **Google Calendar API** を有効化
3. OAuth 2.0認証情報を作成（Webアプリケーション）
4. リダイレクトURIに `http://localhost:3000/api/auth/callback/google` を追加

```bash
git clone https://github.com/YOSHl/family-schedule-hub.git
cd family-schedule-hub
npm install
cp .env.example .env.local
# .env.local にGoogleのAPIキーを設定
npm run dev
```

### 開発について

このプロジェクトは **Claude Code**（Anthropic）を活用して開発しました。OAuth設定から重複検出アルゴリズムまで、AIアシスト開発を全面的に採用しています。
