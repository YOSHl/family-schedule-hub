# family-schedule-hub

Pulls multiple Google Calendars into one view and flags any time two events overlap. I built this because managing my kids' activities — swimming, art class, skating — across different shared calendars kept causing double-bookings.

This is deployed as a private instance. The repo has everything you need to run your own.

## Features

- Aggregates multiple Google Calendars in a single week view
- Highlights overlapping events with a warning
- Color-coded by category (configurable)
- Toggle between this week and next week
- OAuth 2.0 login with Google

## Stack

- Next.js 14, TypeScript, App Router
- Google Calendar API v3
- NextAuth.js (OAuth 2.0)
- Tailwind CSS
- Vercel (hosting)

## Setup

You'll need a Google Cloud project with the Calendar API enabled.

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a project → enable **Google Calendar API**
3. Create OAuth 2.0 credentials (Web application type)
4. Add `http://localhost:3000/api/auth/callback/google` as an authorized redirect URI

```bash
git clone https://github.com/YOSHl/family-schedule-hub.git
cd family-schedule-hub
npm install
cp .env.example .env.local
```

```env
GOOGLE_CLIENT_ID=...
GOOGLE_CLIENT_SECRET=...
NEXTAUTH_SECRET=...          # openssl rand -base64 32
NEXTAUTH_URL=http://localhost:3000
CALENDAR_IDS=primary,family@group.calendar.google.com
```

```bash
npm run dev
```

## Project structure

```
app/
  page.tsx                  # main calendar view
  api/
    auth/                   # NextAuth OAuth handler
    events/                 # Calendar API proxy
components/
  CalendarView.tsx
  EventCard.tsx
  ConflictAlert.tsx
lib/
  google-calendar.ts
  conflict-detector.ts      # overlap detection
.env.example
```

---

## 日本語

複数のGoogleカレンダーを1画面にまとめて表示し、予定が重なった時に警告を出すカレンダーアプリです。

子どもの習い事（水泳・Artクラス・スケート）を複数の共有カレンダーで管理していて、ダブルブッキングが続いたので作りました。今はプライベートでデプロイして使っています。

### セットアップ

Google Cloud ConsoleでCalendar APIを有効にしたプロジェクトが必要です。

1. [Google Cloud Console](https://console.cloud.google.com/) でプロジェクト作成
2. **Google Calendar API** を有効化
3. OAuth 2.0認証情報を作成（Webアプリケーション）
4. リダイレクトURIに `http://localhost:3000/api/auth/callback/google` を追加

```bash
git clone https://github.com/YOSHl/family-schedule-hub.git
cd family-schedule-hub
npm install
cp .env.example .env.local
# .env.local に各キーを設定
npm run dev
```

`CALENDAR_IDS` にカンマ区切りでカレンダーIDを指定すると、複数カレンダーをまとめて表示します。
