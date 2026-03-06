# 🚀 APEX OS Live Webinar — AI-Powered CV Builder

> **Build a production-ready, AI-enhanced CV Builder in 1.5 hours**
> Live coding session powered by the APEX OS agent swarm

[![Next.js](https://img.shields.io/badge/Next.js-14-black?style=flat-square&logo=nextdotjs)](https://nextjs.org)
[![Supabase](https://img.shields.io/badge/Supabase-Database-3ECF8E?style=flat-square&logo=supabase)](https://supabase.com)
[![Claude AI](https://img.shields.io/badge/Claude-AI-CC785C?style=flat-square)](https://anthropic.com)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript)](https://typescriptlang.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](https://opensource.org/licenses/MIT)

**Live repo:** https://github.com/fratilanico/webinar
**Code repo:** https://github.com/fratilanico/cv-builder

---

## 🏗️ APEX OS Agent Swarm Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                    APEX OS — AGENT SWARM                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │              GATEWAY / ORCHESTRATOR LAYER                   │   │
│  │                                                             │   │
│  │   ┌──────────────┐    ┌──────────────┐    ┌─────────────┐  │   │
│  │   │  Task Router │    │  Dispatcher  │    │  Scheduler  │  │   │
│  │   │  & Planner   │───▶│  & Priority  │───▶│  & Queue    │  │   │
│  │   └──────────────┘    └──────────────┘    └─────────────┘  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                              │                                      │
│                              ▼                                      │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                  WORKER AGENTS LAYER                        │   │
│  │                                                             │   │
│  │   ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐  │   │
│  │   │ Worker-1 │  │ Worker-2 │  │ Worker-3 │  │ Worker-N │  │   │
│  │   │  (Dev)   │  │  (Dev)   │  │  (Dev)   │  │  (Dev)   │  │   │
│  │   └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘  │   │
│  └────────┼─────────────┼─────────────┼──────────────┼────────┘   │
│           │             │             │              │             │
│           └─────────────┴──────┬──────┴──────────────┘             │
│                                ▼                                    │
│  ┌─────────────────────────────────────────────────────────────┐   │
│  │                      TOOLS LAYER                            │   │
│  │                                                             │   │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐  │   │
│  │  │   Bash   │ │   Git    │ │  File    │ │    GitHub    │  │   │
│  │  │ Executor │ │  Tools   │ │   R/W    │ │     CLI      │  │   │
│  │  └──────────┘ └──────────┘ └──────────┘ └──────────────┘  │   │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐  │   │
│  │  │  Search  │ │  Claude  │ │ Supabase │ │   Vercel     │  │   │
│  │  │   Web    │ │   API    │ │   SDK    │ │    Deploy    │  │   │
│  │  └──────────┘ └──────────┘ └──────────┘ └──────────────┘  │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 📋 Prerequisites

Before joining the webinar, make sure you have:

```
┌─────────────────────────────────────────────────────┐
│                   PREREQUISITES                     │
├──────────────────┬──────────────────────────────────┤
│  Tool / Account  │  Notes                           │
├──────────────────┼──────────────────────────────────┤
│  Node.js 18+     │  https://nodejs.org              │
│  npm / pnpm      │  pnpm recommended                │
│  Git             │  Any recent version              │
│  Supabase Acct   │  Free tier is sufficient         │
│  Anthropic Key   │  console.anthropic.com           │
│  Vercel Acct     │  Free tier for deploy            │
│  VS Code         │  Or your preferred editor        │
└──────────────────┴──────────────────────────────────┘
```

---

## ⏱️ Webinar Agenda

### [00:00–05:00] Welcome + Architecture Overview

**What we're building:** A full-stack, AI-powered CV Builder with real-time preview,
dark/light mode, and intelligent per-section AI suggestions — deployed to production.

**Tech stack at a glance:**

```
┌─────────────────────────────────────────────────────┐
│                    TECH STACK                       │
├───────────────────┬─────────────────────────────────┤
│  Layer            │  Technology                     │
├───────────────────┼─────────────────────────────────┤
│  Frontend         │  Next.js 14 App Router          │
│  UI Components    │  shadcn/ui + Tailwind CSS        │
│  Database         │  Supabase (Postgres)             │
│  Auth             │  Supabase Auth                   │
│  AI               │  Claude API (Anthropic)          │
│  Language         │  TypeScript 5                   │
│  Deployment       │  Vercel                          │
└───────────────────┴─────────────────────────────────┘
```

**Design philosophy:**
- Supabase-style neon green (`#3ECF8E`) aesthetic
- Clean, professional, minimal UI
- Dark/light mode from day one
- Mobile-first responsive layout

---

### [05:00–15:00] Project Setup

#### 1. Bootstrap the app

```bash
npx create-next-app@latest cv-builder \
  --typescript \
  --tailwind \
  --eslint \
  --app \
  --src-dir \
  --import-alias "@/*"

cd cv-builder
```

#### 2. Install dependencies

```bash
# shadcn/ui
npx shadcn-ui@latest init

# Core UI components
npx shadcn-ui@latest add button input label textarea card badge separator tabs

# Supabase
npm install @supabase/supabase-js @supabase/ssr

# AI
npm install @anthropic-ai/sdk

# Utilities
npm install zod react-hook-form @hookform/resolvers clsx tailwind-merge
```

#### 3. Supabase project setup

```bash
# Install Supabase CLI
npm install -g supabase

# Init local dev
supabase init
supabase start
```

#### 4. Environment variables

```bash
# .env.local  — NEVER commit this file
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
ANTHROPIC_API_KEY=your_anthropic_api_key
```

#### 5. Database schema

```sql
-- Run in Supabase SQL Editor
create table cv_profiles (
  id uuid default gen_random_uuid() primary key,
  user_id uuid references auth.users not null,
  title text not null default 'My CV',
  personal_info jsonb default '{}',
  experience jsonb default '[]',
  education jsonb default '[]',
  skills jsonb default '[]',
  created_at timestamptz default now(),
  updated_at timestamptz default now()
);

alter table cv_profiles enable row level security;

create policy "Users own their CVs"
  on cv_profiles for all
  using (auth.uid() = user_id);
```

---

### [15:00–30:00] Core CV Builder UI

#### Component architecture

```
src/
├── app/
│   ├── layout.tsx              # Root layout + theme provider
│   ├── page.tsx                # Landing page
│   └── cv/
│       ├── page.tsx            # CV editor page
│       └── [id]/
│           └── page.tsx        # Shared CV view
├── components/
│   ├── cv/
│   │   ├── CVEditor.tsx        # Main editor container
│   │   ├── CVPreview.tsx       # Real-time preview pane
│   │   ├── sections/
│   │   │   ├── PersonalInfo.tsx
│   │   │   ├── Experience.tsx
│   │   │   ├── Education.tsx
│   │   │   └── Skills.tsx
│   │   └── AIAssistButton.tsx  # Per-section AI enhancement
│   ├── ui/                     # shadcn components
│   └── ThemeToggle.tsx
├── lib/
│   ├── supabase/
│   │   ├── client.ts
│   │   └── server.ts
│   ├── ai/
│   │   └── claude.ts
│   └── types.ts
└── styles/
    └── globals.css
```

#### Design tokens — Neon green aesthetic

```css
/* globals.css */
:root {
  --accent: #3ECF8E;          /* Supabase neon green */
  --accent-hover: #2EB87B;
  --background: #FFFFFF;
  --surface: #F8F9FA;
  --border: #E5E7EB;
  --text-primary: #111827;
  --text-secondary: #6B7280;
}

.dark {
  --background: #0A0A0A;
  --surface: #111111;
  --border: #1F1F1F;
  --text-primary: #F9FAFB;
  --text-secondary: #9CA3AF;
}
```

#### Real-time split-pane layout

```tsx
// app/cv/page.tsx
export default function CVPage() {
  return (
    <div className="flex h-screen overflow-hidden">
      {/* Editor — left pane */}
      <div className="w-1/2 overflow-y-auto border-r border-border">
        <CVEditor />
      </div>

      {/* Preview — right pane */}
      <div className="w-1/2 overflow-y-auto bg-surface">
        <CVPreview />
      </div>
    </div>
  )
}
```

#### Form sections covered

```
┌─────────────────────────────────────────────────────┐
│                   CV SECTIONS                       │
├──────────────────┬──────────────────────────────────┤
│  Section         │  Fields                         │
├──────────────────┼──────────────────────────────────┤
│  Personal Info   │  Name, title, email, phone,     │
│                  │  location, LinkedIn, GitHub      │
├──────────────────┼──────────────────────────────────┤
│  Experience      │  Company, role, dates, bullet   │
│                  │  points (dynamic list)           │
├──────────────────┼──────────────────────────────────┤
│  Education       │  Institution, degree, field,    │
│                  │  dates, achievements             │
├──────────────────┼──────────────────────────────────┤
│  Skills          │  Categories + skill tags,       │
│                  │  proficiency levels              │
└──────────────────┴──────────────────────────────────┘
```

---

### [30:00–50:00] AI Integration — Claude API

#### Server action for AI enhancement

```typescript
// lib/ai/claude.ts
import Anthropic from '@anthropic-ai/sdk'

const client = new Anthropic()

export async function enhanceSection(
  section: string,
  content: string
): Promise<string> {
  const message = await client.messages.create({
    model: 'claude-opus-4-6',
    max_tokens: 1024,
    messages: [
      {
        role: 'user',
        content: `You are a professional CV writer.
Enhance the following ${section} section of a CV.
Make it more impactful, use strong action verbs,
quantify achievements where possible.
Return only the enhanced text, no explanations.

Original:
${content}`
      }
    ]
  })

  return (message.content[0] as { type: 'text'; text: string }).text
}
```

#### API route

```typescript
// app/api/ai/enhance/route.ts
import { enhanceSection } from '@/lib/ai/claude'
import { NextRequest, NextResponse } from 'next/server'

export async function POST(request: NextRequest) {
  const { section, content } = await request.json()

  if (!section || !content) {
    return NextResponse.json({ error: 'Missing fields' }, { status: 400 })
  }

  const enhanced = await enhanceSection(section, content)
  return NextResponse.json({ enhanced })
}
```

#### AI features we'll build

```
┌───────────────────────────────────────────────────────────────┐
│                      AI FEATURES                              │
├──────────────────────┬────────────────────────────────────────┤
│  Feature             │  Description                          │
├──────────────────────┼────────────────────────────────────────┤
│  Section Enhance     │  One-click rewrite per section        │
│  Bullet Improve      │  Make each bullet point stronger      │
│  Skills Suggest      │  Auto-suggest skills from experience  │
│  Summary Generate    │  Write a compelling professional      │
│                      │  summary from the full CV content     │
│  ATS Optimization    │  Suggest keywords for job matching    │
└──────────────────────┴────────────────────────────────────────┘
```

#### AI Assist Button component

```tsx
// components/cv/AIAssistButton.tsx
'use client'

import { useState } from 'react'
import { Button } from '@/components/ui/button'
import { Sparkles, Loader2 } from 'lucide-react'

interface Props {
  section: string
  content: string
  onEnhanced: (text: string) => void
}

export function AIAssistButton({ section, content, onEnhanced }: Props) {
  const [loading, setLoading] = useState(false)

  const handleEnhance = async () => {
    setLoading(true)
    try {
      const res = await fetch('/api/ai/enhance', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ section, content })
      })
      const { enhanced } = await res.json()
      onEnhanced(enhanced)
    } finally {
      setLoading(false)
    }
  }

  return (
    <Button
      variant="outline"
      size="sm"
      onClick={handleEnhance}
      disabled={loading}
      className="border-[#3ECF8E] text-[#3ECF8E] hover:bg-[#3ECF8E]/10"
    >
      {loading
        ? <Loader2 className="h-4 w-4 animate-spin mr-2" />
        : <Sparkles className="h-4 w-4 mr-2" />
      }
      {loading ? 'Enhancing...' : 'AI Enhance'}
    </Button>
  )
}
```

---

### [50:00–60:00] Testing, Bug Fixing & Deploy

#### Pre-deploy checklist

```
┌─────────────────────────────────────────────────────┐
│               PRE-DEPLOY CHECKLIST                  │
├─────────────────────────────────────────────────────┤
│  ☐  All env vars set in Vercel dashboard            │
│  ☐  Supabase RLS policies verified                 │
│  ☐  API routes return proper error codes           │
│  ☐  Dark mode toggle works                         │
│  ☐  Mobile responsive layout checked               │
│  ☐  CV preview renders correctly                   │
│  ☐  AI enhancement endpoint tested                 │
│  ☐  .env.local NOT committed to git                │
└─────────────────────────────────────────────────────┘
```

#### Deploy to Vercel

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel --prod

# Set environment variables
vercel env add NEXT_PUBLIC_SUPABASE_URL
vercel env add NEXT_PUBLIC_SUPABASE_ANON_KEY
vercel env add ANTHROPIC_API_KEY
```

---

### [60:00–90:00] Q&A, Architecture Deep-Dive & Audience Questions

**Topics we'll cover:**

- How the APEX OS agent swarm orchestrates autonomous dev workers
- Scaling multi-agent systems: task queuing, priority, parallelism
- Claude API best practices: system prompts, streaming, tool use
- Supabase Row Level Security patterns for multi-tenant apps
- Next.js 14 App Router patterns: server components, server actions, streaming
- Production considerations: rate limiting, caching, cost optimization

---

## 📁 Resources

### Workspace Scan Results (2026-03-06)

Verified filesystem scan — no personal CV or career documents found on this machine.

```
┌─────────────────────────────────────────────────────────────────────┐
│                  WORKSPACE SCAN (VERIFIED)                          │
├──────────────────────────────────┬──────────────────────────────────┤
│  Location                        │  Result                         │
├──────────────────────────────────┼──────────────────────────────────┤
│  ~/apex-workspace/               │  Does not exist                 │
│  ~/Documents/                    │  Does not exist                 │
│  ~/repos/                        │  Does not exist                 │
│  ~/repos/nico-archive/           │  Does not exist                 │
└──────────────────────────────────┴──────────────────────────────────┘
```

No personal CV, EU brief, or resume documents are present on this machine.
The webinar builds the CV Builder entirely from scratch using the stack below.

### Reference Links

```
┌─────────────────────────────────────────────────────────────────┐
│                      REFERENCE LINKS                            │
├────────────────────────────────────┬────────────────────────────┤
│  Resource                          │  URL                       │
├────────────────────────────────────┼────────────────────────────┤
│  CV Builder repo (live code)       │  github.com/fratilanico/   │
│                                    │  cv-builder                │
│  Vibe Coder Academy                │  APEX OS curriculum system │
│  Next.js 14 docs                   │  nextjs.org/docs           │
│  Supabase docs                     │  supabase.com/docs         │
│  shadcn/ui                         │  ui.shadcn.com             │
│  Anthropic docs                    │  docs.anthropic.com        │
│  Claude API reference              │  docs.anthropic.com/en/api │
│  Vercel deployment                 │  vercel.com/docs           │
└────────────────────────────────────┴────────────────────────────┘
```

---

## 🛠️ Quick Start (Post-Webinar)

```bash
git clone https://github.com/fratilanico/cv-builder.git
cd cv-builder
cp .env.example .env.local
# Fill in your Supabase + Anthropic keys
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 📄 License

MIT © [Nico Fratila](https://github.com/fratilanico)

---

*Built live with the APEX OS agent swarm*
