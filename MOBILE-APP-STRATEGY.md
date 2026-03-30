# Trochai Mobile App — Research & Strategy

> **Date:** 2026-03-27
> **Status:** Research / Proposal
> **Author:** Claude (AI-assisted research)

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Framework Comparison](#framework-comparison)
3. [Recommendation: React Native + Expo](#recommendation-react-native--expo)
4. [MVP Scope Definition](#mvp-scope-definition)
5. [Existing API Surface](#existing-api-surface)
6. [Real-Time Architecture](#real-time-architecture)
7. [Push Notifications Strategy](#push-notifications-strategy)
8. [Authentication on Mobile](#authentication-on-mobile)
9. [Code Sharing Strategy](#code-sharing-strategy)
10. [Technical Architecture](#technical-architecture)
11. [Phased Roadmap](#phased-roadmap)
12. [Risks & Mitigations](#risks--mitigations)

---

## Executive Summary

The goal is to bring Trochai Inbox to mobile — specifically, the **messaging experience**. Agents need to see incoming WhatsApp messages, reply to contacts, and toggle the AI bot from their phone. Full features like property management, analytics, and project configuration remain desktop-only.

**Recommendation:** React Native with Expo (using Expo Router) is the clear winner for this project. The primary reasons:

- **40-60% code reuse** with the existing Next.js web app (TypeScript types, Supabase client, Zod schemas, business logic, TanStack Query patterns)
- **Near-zero learning curve** — same React + TypeScript + hooks paradigm the codebase already uses
- **Chat app performance is excellent** — FlashList for message lists, react-native-keyboard-controller for keyboard handling, Supabase Realtime for live updates
- **AI-assisted development** — Claude writes high-quality React Native + TypeScript code, and the shared paradigm means patterns are consistent across web and mobile
- **Expo handles the hard stuff** — EAS Build for CI/CD, EAS Submit for App Store/Play Store, expo-notifications for push, OTA updates for quick patches

---

## Framework Comparison

### React Native + Expo

| Aspect | Details |
|---|---|
| **Language** | TypeScript (same as web app) |
| **Rendering** | New Architecture (Fabric + TurboModules) — stable and default since RN 0.76+ |
| **Chat list perf** | Excellent — FlashList (Shopify) with item recycling, comparable to native UICollectionView/RecyclerView |
| **Keyboard handling** | Excellent — `react-native-keyboard-controller` provides native-driven keyboard animations |
| **Supabase support** | `@supabase/supabase-js` works identically — same API, same types, Auth + Realtime + Storage |
| **Push notifications** | `expo-notifications` — unified FCM (Android) + APNs (iOS) API |
| **Code sharing** | Direct reuse of TS types, Zod schemas, TanStack Query hooks, business logic |
| **Routing** | Expo Router v4+ — file-based routing like Next.js App Router |
| **Build/deploy** | EAS Build + Submit + Update — no local Xcode/Android Studio needed |
| **AI code quality** | Best — largest React/TS training corpus |

### Flutter

| Aspect | Details |
|---|---|
| **Language** | Dart (completely different from our stack) |
| **Rendering** | Impeller engine — excellent, direct canvas rendering |
| **Chat list perf** | Excellent — `ListView.builder` with recycling |
| **Keyboard handling** | Very good |
| **Supabase support** | `supabase_flutter` — works but separate Dart API, types must be rewritten |
| **Push notifications** | `firebase_messaging` — mature |
| **Code sharing** | **Zero** — different language, all types/logic/validation must be rewritten in Dart |
| **AI code quality** | Good, but smaller training corpus than React/TS |

### Native (Swift + Kotlin)

| Aspect | Details |
|---|---|
| **Language** | Swift (iOS) + Kotlin (Android) — two separate codebases |
| **Rendering** | Best possible — SwiftUI + Jetpack Compose |
| **Chat list perf** | Best possible |
| **Keyboard handling** | Best possible |
| **Supabase support** | Separate clients per platform (`supabase-swift`, `supabase-kt`) |
| **Push notifications** | Platform-native APIs — most flexible |
| **Code sharing** | **Zero** — two separate codebases, zero sharing with web |
| **Development effort** | 2-3x compared to cross-platform for equivalent features |

### Comparison Matrix

| Criteria | React Native + Expo | Flutter | Native |
|---|---|---|---|
| Code sharing with web | **40-60%** | 0% | 0% |
| Team learning curve | **Low** | High | Very High |
| Chat app readiness | Excellent | Excellent | Best |
| Supabase integration | **Native JS client** | Dart client | Per-platform |
| Single codebase | Yes | Yes | No (2 codebases) |
| Time to MVP | **Fastest** | Moderate | Slowest |
| AI code generation | **Best** | Good | Good (per platform) |
| App Store OTA updates | Yes (EAS Update) | Limited | No |
| Long-term maintenance | Low | Moderate | High (2x) |

### Why Not Flutter?

Flutter is a great framework, but the **zero code sharing** with our existing TypeScript/React/Supabase stack is a dealbreaker. We would need to:
- Rewrite all Supabase types in Dart
- Rewrite all Zod validation schemas
- Rewrite all business logic (date formatting, price formatting, phone validation)
- Learn Dart and Flutter's widget system from scratch
- Maintain two completely disconnected codebases with duplicated logic

### Why Not Native?

Native development makes sense for companies with dedicated platform teams and billions of users (WhatsApp, Telegram). For a SaaS startup:
- Two completely separate codebases (Swift + Kotlin)
- Zero shared code with the web app
- 2-3x development time for feature parity
- Ongoing cost of maintaining two platforms
- The performance difference vs React Native New Architecture is negligible for a chat app

---

## Recommendation: React Native + Expo

React Native with Expo is the right choice. Here's the specific stack:

| Layer | Technology |
|---|---|
| **Framework** | React Native 0.76+ (New Architecture) |
| **Platform** | Expo SDK 52+ (managed workflow) |
| **Routing** | Expo Router v4 (file-based, like Next.js) |
| **UI Components** | React Native Paper or Tamagui (for shared design system) |
| **Lists** | FlashList (Shopify) — high-perf recycling list |
| **Keyboard** | react-native-keyboard-controller |
| **Animations** | Reanimated 3 |
| **State/Data** | TanStack Query (same as web) |
| **Database/Auth** | Supabase JS client (same as web) |
| **Real-time** | Supabase Realtime Broadcast + polling fallback |
| **Push** | expo-notifications (FCM + APNs) |
| **Storage** | expo-secure-store (auth tokens) |
| **Media** | expo-image-picker, expo-document-picker |
| **Build/CI** | EAS Build + EAS Submit |
| **OTA Updates** | EAS Update |

---

## MVP Scope Definition

Based on analysis of the full trochai-inbox codebase (83 API routes, 13 inbox components, 18 DB tables), here's the MVP scope prioritized for mobile agents.

### Phase 1 — Core Messaging (MVP)

The absolute minimum for a useful mobile app. An agent can view and reply to conversations from their phone.

| Feature | Description | Priority |
|---|---|---|
| **Login** | Email/password + Google OAuth via Supabase Auth | Must |
| **Conversation list** | Paginated list with search, unread counts, last message preview | Must |
| **Conversation filters** | Filter by status (open/in_progress/closed), unread only | Must |
| **Message thread** | Full message history with cursor pagination (scroll up to load more) | Must |
| **Send text message** | Compose and send text messages | Must |
| **Send media** | Send photos from camera/gallery | Must |
| **Bot toggle** | Enable/disable AI bot per conversation | Must |
| **Real-time messages** | Live incoming message updates via Supabase Broadcast | Must |
| **Real-time conversation list** | Live conversation list updates (new messages, status changes) | Must |
| **Push notifications** | Notify agent when new message arrives (even when app is closed) | Must |
| **Unread badge** | App icon badge count for unread messages | Must |
| **24-hour window indicator** | Show whether WhatsApp window is open or expired | Must |
| **Message status** | Show sent/delivered/read checkmarks | Must |
| **Agent availability toggle** | Set yourself as available/unavailable | Should |

### Phase 2 — Enhanced Messaging

Features that make the mobile experience more complete and reduce the need to switch to desktop.

| Feature | Description | Priority |
|---|---|---|
| **Send templates** | Select and send approved WhatsApp templates (critical for outside 24-hour window) | High |
| **Send documents/files** | Send PDFs and other documents | High |
| **Conversation assignment** | Assign/reassign conversation to another agent | High |
| **Conversation status** | Change status (open/in_progress/closed) | High |
| **Contact info panel** | View contact details, tags, notes | High |
| **Internal notes** | Read and add internal team notes on a conversation | High |
| **Conversation tags** | View and manage tags | Medium |
| **Notification preferences** | Configure which notifications to receive | Medium |
| **Multi-channel indicator** | Show which WhatsApp channel a conversation belongs to | Medium |
| **Media viewer** | Full-screen image/video viewer for received media | Medium |
| **Audio messages** | Play received audio, record and send voice messages | Medium |

### Phase 3 — Extended Features

Features that bring more desktop functionality to mobile. Only build after Phase 1 + 2 are solid.

| Feature | Description | Priority |
|---|---|---|
| **Schedule followups** | Schedule template messages for future delivery | Medium |
| **Contact list** | Browse and search all contacts | Medium |
| **Quick property lookup** | Search properties to share with contacts (link or card) | Medium |
| **Escalation handling** | See and resolve bot escalations | Medium |
| **Basic analytics** | Today's conversation count, unread count, bot stats | Low |
| **Settings** | Bot settings, profile, notification preferences | Low |
| **Offline support** | Cache recent conversations for viewing without connection | Low |

### Explicitly NOT in Mobile Scope

These features stay desktop-only:

- Property CRUD (create/edit/delete listings)
- Project management
- CSV import wizard
- Template creation/editing (Meta approval workflow)
- WhatsApp channel configuration
- User/team management
- Assignment rule configuration
- Billing/subscription management
- Full analytics dashboard
- Embedding/AI configuration
- Tag management (CRUD — only tag assignment on mobile)

---

## Existing API Surface

The mobile app does **not** need a new backend. All required endpoints already exist in the Next.js API routes. Here's what the mobile app will consume:

### Authentication

| Method | Endpoint | Purpose |
|---|---|---|
| `POST` | Supabase Auth (SDK) | Email/password login, Google OAuth |
| `GET` | `/api/identity` | Fetch user profile + org + subscription (app startup) |
| `GET` | `/api/users/me` | Get user profile |
| `PATCH` | `/api/users/me` | Update availability, profile |

### Conversations (core)

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/conversations` | List conversations (paginated, filterable) |
| `GET` | `/api/conversations/[id]` | Get single conversation details |
| `PATCH` | `/api/conversations/[id]/bot` | Toggle bot on/off |
| `PATCH` | `/api/conversations/[id]/claim` | Agent claims conversation |
| `PATCH` | `/api/conversations/[id]/reassign` | Reassign to another agent |
| `PATCH` | `/api/conversations/[id]/human-needed` | Resolve escalation |

### Messages (core)

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/messages/[conversationId]` | Fetch message history (cursor pagination) |
| `POST` | `/api/messages/send` | Send text/media message (FormData) |
| `POST` | `/api/messages/interactive` | Send interactive buttons/lists |
| `POST` | `/api/templates/send` | Send approved template message |

### Contacts

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/contacts` | List contacts (paginated, searchable) |
| `GET` | `/api/contacts/[id]` | Get contact details |
| `PATCH` | `/api/contacts/[id]` | Update contact info |

### Notifications

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/notifications` | Fetch in-app notifications |
| `PATCH` | `/api/notifications` | Mark as read |

### Templates

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/templates` | List approved templates (for sending) |

### Followups

| Method | Endpoint | Purpose |
|---|---|---|
| `POST` | `/api/followups` | Schedule a follow-up message |
| `PATCH` | `/api/followups/[id]` | Cancel/update followup |

### Notes

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/conversations/[id]/notes` | Get internal notes |
| `POST` | `/api/conversations/[id]/notes` | Add internal note |

### Rate Limits (already enforced by backend)

| Tier | Limit |
|---|---|
| `auth` | 10/min per IP |
| `api` (general) | 100/min per user |
| `messaging` | 30/min per user |

The mobile app inherits all rate limiting, input validation (Zod), tenant isolation (RLS), and security from the existing backend. No new API work is needed for MVP.

---

## Real-Time Architecture

The web app already uses a **dual strategy** (Supabase Broadcast + polling fallback) that translates directly to mobile.

### How It Works Today (Web)

```
Meta Webhook → /api/webhooks/whatsapp → Store message in DB
                                       → Broadcast via Supabase Realtime

Browser:
  1. Supabase Broadcast subscription (instant, <100ms)
  2. Polling fallback every 3s (resilience)
  3. Deduplication via Set<messageId>
```

### Channels

| Channel | Event | Purpose |
|---|---|---|
| `inbox:messages:{orgId}` | `new_message` | New message in any conversation |
| `inbox:conversations:{orgId}` | `conversation_updated` | Conversation list change |

### Mobile Implementation

The Supabase JS client works identically in React Native. The same subscription pattern from the web hooks (`useRealtimeMessages`, `useRealtimeConversations`) can be adapted:

```typescript
// React Native — same Supabase Realtime API
const channel = supabase
  .channel(`inbox:messages:${organizationId}`)
  .on('broadcast', { event: 'new_message' }, (payload) => {
    // Update local state / TanStack Query cache
    queryClient.setQueryData(['messages', conversationId], (old) => {
      return [...old, payload.payload];
    });
  })
  .subscribe();
```

### Mobile-Specific Considerations

| Concern | Solution |
|---|---|
| **App in background** | Supabase WebSocket disconnects → push notifications take over |
| **App foregrounded** | Re-establish Realtime subscription, poll for missed messages |
| **Poor connectivity** | Polling fallback (same pattern as web, 3-5s interval) |
| **Message dedup** | Same `Set<messageId>` approach as web |
| **Reconnection** | Supabase client handles automatic reconnection |

---

## Push Notifications Strategy

The web app currently has **no push notification infrastructure** — notifications are in-app only (Supabase Realtime + 60s polling). Mobile is the opportunity to build this properly.

### Architecture

```
Inbound WhatsApp message
  → Webhook processor stores message
  → Webhook processor broadcasts via Realtime (existing)
  → NEW: Webhook processor sends push notification
    → Look up assigned agent's push token
    → Send via expo-notifications server SDK (or FCM/APNs directly)
    → Notification payload includes conversation_id for deep linking
```

### Implementation Plan

1. **New DB table: `push_tokens`**
   ```sql
   CREATE TABLE push_tokens (
     id          uuid PRIMARY KEY DEFAULT gen_random_uuid(),
     user_id     uuid NOT NULL REFERENCES users(id) ON DELETE CASCADE,
     token       text NOT NULL,
     platform    text NOT NULL CHECK (platform IN ('ios', 'android')),
     created_at  timestamptz NOT NULL DEFAULT now(),
     UNIQUE (user_id, token)
   );
   ```

2. **New API endpoints:**
   - `POST /api/push-tokens` — Register device token on login
   - `DELETE /api/push-tokens` — Remove token on logout

3. **Modify webhook processor** to send push notifications after storing a message:
   - Look up the conversation's `assigned_agent_id`
   - Fetch their push token(s)
   - Send notification with `{ title: contactName, body: messagePreview, data: { conversationId } }`
   - Only send if agent is not currently viewing that conversation (check presence or a simple flag)

4. **Deep linking** — Tapping a notification opens the app directly to that conversation:
   ```
   trochai://inbox/[conversationId]
   ```
   Expo Router handles this automatically based on file structure.

### Notification Types

| Type | Trigger | Mobile Push? |
|---|---|---|
| New message (assigned) | Inbound message to agent's conversation | Yes |
| New message (unassigned) | Inbound message to unassigned conversation | Optional (configurable) |
| Conversation assigned | Admin assigns conversation to agent | Yes |
| Bot escalation | Bot escalates to human | Yes |
| SLA warning | Response time approaching SLA limit | Yes |
| Followup sent/failed | Scheduled followup status change | Optional |

---

## Authentication on Mobile

### Flow

```
1. App opens → check for stored session in expo-secure-store
2. If valid session → GET /api/identity → show inbox
3. If no session → show login screen
4. Login options:
   a. Email + password → Supabase Auth signInWithPassword()
   b. Google OAuth → Supabase Auth signInWithIdToken()
      (using expo-auth-session for the OAuth flow)
5. On success → store session in expo-secure-store
6. Session refresh handled automatically by Supabase client
```

### Key Differences from Web

| Concern | Web | Mobile |
|---|---|---|
| **Token storage** | Cookies (`.trochai.com` domain) | expo-secure-store (encrypted Keychain/Keystore) |
| **Google OAuth** | Browser redirect flow | expo-auth-session (in-app browser or native Google Sign-In) |
| **Session refresh** | Supabase middleware on every request | Supabase client auto-refresh on token expiry |
| **Multi-org** | Subdomain routing (`{org}.trochai.com`) | Single app, org selected at login or via `/api/identity` |

### Security

- JWT tokens stored in **expo-secure-store** (iOS Keychain, Android Keystore) — encrypted at rest
- No subdomain routing needed — the mobile app always hits the main API domain
- Same RBAC enforcement on all API endpoints (admin/agent/viewer roles)
- Same RLS policies ensure tenant isolation

---

## Code Sharing Strategy

### What Can Be Shared Directly

These files/modules from `trochai-inbox/web/src/` can be reused with zero or minimal changes:

| Module | Path | Sharing Level |
|---|---|---|
| **Supabase types** | `types/database.ts` | 100% — auto-generated, identical |
| **Zod schemas** | Various API route files | 100% — extract to shared package |
| **Business logic** | `lib/utils.ts` (formatters, helpers) | 90% — strip DOM-specific bits |
| **API response types** | Various | 100% — TypeScript interfaces |
| **WhatsApp types** | `types/whatsapp.ts` | 100% |
| **Billing constants** | `lib/billing/plans.ts` | 100% |
| **Amenity constants** | `lib/constants/amenities.ts` | 100% |
| **i18n strings** | `messages/es.json`, `messages/en.json` | 80% — subset for mobile screens |

### What Must Be Rewritten (Mobile-Specific)

| Concern | Web | Mobile |
|---|---|---|
| **UI Components** | React DOM (`div`, `span`, `input`) | React Native (`View`, `Text`, `TextInput`) |
| **Navigation** | Next.js App Router + `next-intl` | Expo Router |
| **Supabase client** | Cookie-based auth (`createBrowserClient`) | Token-based auth (`createClient` with `AsyncStorage`) |
| **File uploads** | `FormData` with `File` | `FormData` with `expo-image-picker` URI |
| **Styling** | Tailwind CSS classes | StyleSheet / NativeWind (Tailwind for RN) or Tamagui |
| **Real-time hooks** | `useRealtimeMessages` (DOM-specific) | Rewrite with same logic, RN lifecycle |

### Monorepo Structure (Future)

When the mobile app matures, extract shared code into a monorepo:

```
trochai/
├── packages/
│   └── shared/
│       ├── types/           ← database.ts, whatsapp.ts
│       ├── validation/      ← extracted Zod schemas
│       ├── utils/           ← formatters, helpers
│       ├── constants/       ← amenities, plans, limits
│       └── i18n/            ← shared translation strings
├── trochai-inbox/
│   └── web/                 ← imports from @trochai/shared
└── trochai-mobile/
    └── app/                 ← imports from @trochai/shared
```

For MVP, start with a standalone project and **copy** shared types. Extract to monorepo when it becomes painful.

---

## Technical Architecture

### Project Structure

```
trochai-mobile/
├── app/                          ← Expo Router (file-based routes)
│   ├── _layout.tsx               ← Root layout (auth provider, query client)
│   ├── (auth)/                   ← Auth screens (no tab bar)
│   │   ├── login.tsx
│   │   └── signup.tsx
│   ├── (tabs)/                   ← Main app (tab navigator)
│   │   ├── _layout.tsx           ← Tab bar config
│   │   ├── inbox/
│   │   │   ├── index.tsx         ← Conversation list
│   │   │   └── [id].tsx          ← Message thread
│   │   ├── contacts/
│   │   │   └── index.tsx         ← Contact list
│   │   └── settings/
│   │       └── index.tsx         ← Profile, availability, preferences
│   └── +not-found.tsx
├── components/
│   ├── inbox/
│   │   ├── ConversationItem.tsx
│   │   ├── MessageBubble.tsx
│   │   ├── MessageComposer.tsx
│   │   ├── BotToggle.tsx
│   │   └── WindowIndicator.tsx
│   ├── ui/                       ← Base UI components
│   └── providers/
│       ├── AuthProvider.tsx
│       └── QueryProvider.tsx
├── hooks/
│   ├── useIdentity.ts            ← User + org context
│   ├── useConversations.ts       ← Conversation list query
│   ├── useMessages.ts            ← Message history query
│   ├── useRealtimeMessages.ts    ← Realtime subscription
│   └── usePushNotifications.ts   ← Push registration
├── lib/
│   ├── supabase.ts               ← Supabase client (token-based)
│   ├── api.ts                    ← API client helpers
│   └── notifications.ts          ← Push notification helpers
├── types/
│   └── database.ts               ← Copied from web (or shared package)
├── assets/                       ← App icon, splash screen
├── app.json                      ← Expo config
└── package.json
```

### Key Dependencies

```json
{
  "dependencies": {
    "expo": "~52.0.0",
    "expo-router": "~4.0.0",
    "expo-secure-store": "~13.0.0",
    "expo-notifications": "~0.28.0",
    "expo-image-picker": "~15.0.0",
    "expo-document-picker": "~12.0.0",
    "expo-auth-session": "~6.0.0",
    "react-native": "0.76+",
    "@shopify/flash-list": "~1.7.0",
    "react-native-keyboard-controller": "~1.14.0",
    "react-native-reanimated": "~3.16.0",
    "@supabase/supabase-js": "^2.45.0",
    "@tanstack/react-query": "^5.60.0",
    "react-native-mmkv": "~3.0.0",
    "zod": "^3.23.0",
    "date-fns": "^3.0.0"
  }
}
```

### Screens Wireframe (MVP)

```
┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────────┐
│ ┌─────────────────┐ │  │ ← Back    Juan P.   │  │ Settings            │
│ │ 🔍 Search...    │ │  │ Bot: ON  Window: 22h│  │                     │
│ ├─────────────────┤ │  ├─────────────────────┤  │ ┌─────────────────┐ │
│ │ ● Juan Pérez    │ │  │                     │  │ │ 👤 Lee Reed     │ │
│ │   Hola, busco.. │ │  │  [Contact bubble]   │  │ │ Agent • Online  │ │
│ │   2 min ago   3 │ │  │  Hola, busco un     │  │ └─────────────────┘ │
│ ├─────────────────┤ │  │  apartamento en...   │  │                     │
│ │   María López   │ │  │                     │  │ ☐ Available         │
│ │   Gracias por.. │ │  │     [Bot bubble]    │  │                     │
│ │   1 hour ago    │ │  │     ¡Hola Juan!     │  │ Notifications       │
│ ├─────────────────┤ │  │     Tenemos varias  │  │ ☑ New messages      │
│ │   Carlos Ruiz   │ │  │     opciones...     │  │ ☑ Assignments       │
│ │   Me interesa.. │ │  │                     │  │ ☐ Bot escalations   │
│ │   3 hours ago   │ │  │     [Agent bubble]  │  │                     │
│ ├─────────────────┤ │  │     Te mando las    │  │ Language            │
│ │   Ana Torres    │ │  │     fotos ahora     │  │ [Español ▼]         │
│ │   Cuánto cue... │ │  │                     │  │                     │
│ │   Yesterday     │ │  │                     │  │ About               │
│ └─────────────────┘ │  ├─────────────────────┤  │ Version 1.0.0       │
│                     │  │ [📎] [Message...]  →│  │                     │
│ [Inbox] [Settings]  │  │                     │  │ [Sign Out]          │
└─────────────────────┘  └─────────────────────┘  └─────────────────────┘
   Conversation List        Message Thread            Settings
```

---

## Phased Roadmap

### Phase 1: Core Messaging MVP

**Goal:** Agent can view conversations, read messages, and reply from their phone.

**Scope:**
- Login (email/password + Google OAuth)
- Conversation list with search, filters, unread counts
- Message thread with full history (text, images, documents, audio)
- Send text messages
- Send photos (camera + gallery)
- Bot toggle per conversation
- Real-time message updates (Supabase Broadcast + polling)
- Push notifications for new messages
- 24-hour window indicator
- Message status (sent/delivered/read)
- App icon unread badge

**Backend changes needed:**
- New `push_tokens` table + migration
- `POST /api/push-tokens` and `DELETE /api/push-tokens` endpoints
- Modify webhook processor to send push notifications
- (Optional) New Supabase Edge Function for push delivery

**New infrastructure:**
- Expo project setup with EAS
- Apple Developer account ($99/year) — for App Store + APNs
- Google Play Developer account ($25 one-time) — for Play Store + FCM
- EAS Build plan (free tier may suffice for MVP)

### Phase 2: Enhanced Messaging

**Goal:** Reduce need to switch to desktop for common actions.

**Scope:**
- Send WhatsApp templates (critical for outside 24-hour window)
- Send documents/files
- Conversation assignment and status changes
- Contact info panel
- Internal notes (read + write)
- Conversation tags
- Audio message playback and recording
- Full-screen media viewer
- Notification preferences

### Phase 3: Extended Features

**Goal:** Bring select desktop features to mobile for power users.

**Scope:**
- Schedule follow-up messages
- Contact list and search
- Quick property lookup (share property links with contacts)
- Escalation handling
- Basic daily stats
- Offline caching for recent conversations

---

## Risks & Mitigations

### Technical Risks

| Risk | Impact | Mitigation |
|---|---|---|
| **React Native upgrade friction** | Dependency breakage on major versions | Expo managed workflow handles native deps; pin Expo SDK version |
| **Supabase Realtime on mobile** | WebSocket drops on poor connectivity | Polling fallback (same pattern as web), reconnection handling |
| **Push notification delivery** | FCM/APNs can be unreliable | In-app polling fallback, notification status tracking |
| **iOS App Store review** | Rejection for missing features or guidelines | Follow Apple HIG, minimal first submission, iterate |
| **Auth token management** | Token expiry while app in background | Supabase client auto-refresh, re-auth flow on 401 |
| **Large message history** | Memory issues with long conversations | FlashList recycling, cursor pagination, virtualization |

### Product Risks

| Risk | Impact | Mitigation |
|---|---|---|
| **Agents prefer mobile browser** | Low adoption of native app | Push notifications are the killer feature — no web equivalent |
| **Scope creep** | MVP delayed by feature requests | Strict MVP scope — messaging only, everything else stays desktop |
| **Two surfaces to maintain** | Bug fixes needed in both web + mobile | Shared types and validation reduce duplication; API-first means fixes often only touch backend |

### Operational Risks

| Risk | Impact | Mitigation |
|---|---|---|
| **App Store submission process** | Delays in initial publishing | Start the process early; Apple review takes 1-3 days |
| **Push notification certificates** | Expired certs = no notifications | Use Expo push service (handles cert rotation) |
| **Monitoring** | Mobile-specific crashes hard to debug | Sentry React Native SDK for crash reporting |

---

## Appendix: Database Tables Relevant to Mobile

The mobile app interacts with these tables (through the existing API — no direct DB access):

| Table | Mobile Usage |
|---|---|
| `conversations` | List, filter, update status, toggle bot |
| `messages` | Read history, send new |
| `contacts` | View contact info, update |
| `channels` | Display channel indicator |
| `users` | Auth, profile, availability |
| `organizations` | Org context (name, settings) |
| `tags` | Display/assign tags |
| `internal_notes` | Read/write notes |
| `scheduled_followups` | Schedule/cancel (Phase 2+) |
| `notifications` | Read/mark as read |
| `subscriptions` | Check plan limits |
| `push_tokens` (NEW) | Register/unregister device tokens |

### Key Enums

```
conversation_status:  "open" | "in_progress" | "closed"
message_direction:    "inbound" | "outbound"
message_type:         "text" | "image" | "video" | "audio" | "document" | "sticker" | "template" | "interactive" | "reaction" | "location"
message_status:       "sent" | "delivered" | "read" | "failed"
sender_type:          "contact" | "agent" | "bot" | "system"
user_role:            "admin" | "agent" | "viewer"
```
