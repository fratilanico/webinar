# 🎬 APEX OS Live Webinar — CV Builder with AI

> **Building a production-grade AI-powered CV Builder in 90 minutes**
> Powered by Next.js 14 · Supabase · Claude AI · shadcn/ui · TypeScript

```
┌─────────────────────────────────────────────────────────────────┐
│              APEX OS AGENT SWARM — LIVE WEBINAR                │
│                   CV Builder with AI 🤖                        │
│                                                                 │
│  📅 Live Session  │  ⏱  90 minutes  │  🔓 Open Source         │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🗺️ Architecture Overview

```
┌──────────────────────────────────────────────────────────────────┐
│                    APEX OS AGENT SWARM                          │
│                                                                  │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │          GATEWAY / ORCHESTRATOR LAYER                   │    │
│  │                                                         │    │
│  │   ┌─────────────┐    ┌─────────────┐    ┌──────────┐   │    │
│  │   │  API Gateway│    │Orchestrator │    │  Router  │   │    │
│  │   │  (Next.js)  │───▶│   Agent     │───▶│  Logic   │   │    │
│  │   └─────────────┘    └─────────────┘    └──────────┘   │    │
│  └─────────────────────────────────────────────────────────┘    │
│                            │                                     │
│                            ▼                                     │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │              WORKER AGENTS LAYER                        │    │
│  │                                                         │    │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐  │    │
│  │  │  CV-     │ │  AI      │ │  Export  │ │  Auth    │  │    │
│  │  │  Builder │ │Enhancer  │ │  Agent   │ │  Agent   │  │    │
│  │  │  Agent   │ │  Agent   │ │ (PDF/MD) │ │(Supabase)│  │    │
│  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘  │    │
│  └─────────────────────────────────────────────────────────┘    │
│                            │                                     │
│                            ▼                                     │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │                   TOOLS LAYER                           │    │
│  │                                                         │    │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐  │    │
│  │  │ Supabase │ │  Claude  │ │  Vercel  │ │  shadcn  │  │    │
│  │  │    DB    │ │  API     │ │  Deploy  │ │    UI    │  │    │
│  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘  │    │
│  └─────────────────────────────────────────────────────────┘    │
└──────────────────────────────────────────────────────────────────┘
```

---

## 📋 Prerequisites

Before joining the webinar, make sure you have:

```
┌─────────────────────────────────────────────────────────────────┐
│                      PREREQUISITES                              │
├────────────────────┬────────────────────────────────────────────┤
│  Tool              │  Requirement                               │
├────────────────────┼────────────────────────────────────────────┤
│  Node.js           │  v18+ (LTS recommended)                    │
│  npm / pnpm        │  Latest stable                             │
│  Git               │  Any recent version                        │
│  Supabase Account  │  Free tier at supabase.com                 │
│  Anthropic API Key │  Get one at console.anthropic.com          │
│  Vercel Account    │  Free tier at vercel.com                   │
│  VS Code           │  Recommended editor                        │
└────────────────────┴────────────────────────────────────────────┘
```

---

## ⏱️ Webinar Schedule

### `[00:00 – 05:00]` 🚀 Welcome + Architecture Overview

- Introductions and goals for the session
- What we're building: a full-stack AI-powered CV Builder
- Architecture walkthrough: Next.js 14 App Router + Supabase + Claude AI
- APEX OS agent swarm design pattern explained
- Live demo of the finished product

---

### `[05:00 – 15:00]` 🛠️ Project Setup

**Stack:**

```
┌─────────────────────────────────────────────────────────────────┐
│                       TECH STACK                               │
├─────────────────────┬───────────────────────────────────────────┤
│  Layer              │  Technology                               │
├─────────────────────┼───────────────────────────────────────────┤
│  Framework          │  Next.js 14 (App Router)                  │
│  Language           │  TypeScript                               │
│  Database           │  Supabase (PostgreSQL)                    │
│  Auth               │  Supabase Auth                            │
│  UI Components      │  shadcn/ui + Radix UI                     │
│  Styling            │  Tailwind CSS                             │
│  AI                 │  Anthropic Claude API                     │
│  Deployment         │  Vercel                                   │
└─────────────────────┴───────────────────────────────────────────┘
```

**Step-by-step setup:**

```bash
# 1. Bootstrap Next.js 14 with TypeScript + Tailwind
npx create-next-app@latest cv-builder \
  --typescript \
  --tailwind \
  --eslint \
  --app \
  --src-dir

cd cv-builder

# 2. Install shadcn/ui
npx shadcn-ui@latest init

# 3. Add core components
npx shadcn-ui@latest add button input label card tabs badge

# 4. Install Supabase client
npm install @supabase/supabase-js @supabase/ssr

# 5. Install Anthropic SDK
npm install @anthropic-ai/sdk

# 6. Install additional utilities
npm install react-hook-form zod @hookform/resolvers
```

**Environment setup:**

```bash
# .env.local  — NEVER commit this file to git
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
ANTHROPIC_API_KEY=your_anthropic_api_key
```

**Supabase schema:**

```sql
-- Run in Supabase SQL editor
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

create policy "Users can manage own CVs"
  on cv_profiles for all
  using (auth.uid() = user_id);
```

---

### `[15:00 – 30:00]` 🎨 Core CV Builder UI

**Design System — Supabase-style Neon Green Aesthetic:**

```
┌─────────────────────────────────────────────────────────────────┐
│                      DESIGN TOKENS                             │
├──────────────────┬──────────────────────────────────────────────┤
│  Token           │  Value                                       │
├──────────────────┼──────────────────────────────────────────────┤
│  Primary         │  #3ECF8E  (Neon green)                       │
│  Background      │  #1C1C1C  (Dark)                             │
│  Surface         │  #2A2A2A  (Card background)                  │
│  Border          │  #3A3A3A  (Subtle border)                    │
│  Text Primary    │  #FFFFFF                                      │
│  Text Muted      │  #A1A1AA                                      │
│  Accent          │  #3ECF8E  (Same as primary)                  │
└──────────────────┴──────────────────────────────────────────────┘
```

**CV Builder Layout:**

```
┌─────────────────────────────────────────────────────────────────┐
│  Header: CV Builder  ●  [Save]  [Export PDF]  [AI Enhance]     │
├────────────────────────┬────────────────────────────────────────┤
│  FORM PANEL (left)     │  LIVE PREVIEW (right)                  │
│                        │                                        │
│  [Personal Info]       │  ┌──────────────────────────────────┐  │
│  [Experience]          │  │  John Doe                        │  │
│  [Education]           │  │  Senior Software Engineer        │  │
│  [Skills]              │  │  john@email.com · github.com/... │  │
│                        │  ├──────────────────────────────────┤  │
│  ──────────────────    │  │  EXPERIENCE                      │  │
│                        │  │  ● Senior Engineer @ Acme Corp   │  │
│  Dark/Light Toggle ☀️  │  │  ● Engineer @ StartupXYZ        │  │
│                        │  ├──────────────────────────────────┤  │
│                        │  │  EDUCATION & SKILLS              │  │
│                        │  └──────────────────────────────────┘  │
└────────────────────────┴────────────────────────────────────────┘
```

**Form sections to build:**

1. **Personal Info** — name, title, email, phone, LinkedIn, GitHub, summary
2. **Experience** — company, role, dates, description, achievements (dynamic list)
3. **Education** — institution, degree, dates, GPA (optional)
4. **Skills** — categorized tags (languages, frameworks, tools)

**Key component: `CVForm.tsx`:**

```tsx
// src/components/CVForm.tsx
'use client'
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs'
import PersonalInfoSection from './sections/PersonalInfoSection'
import ExperienceSection from './sections/ExperienceSection'
import EducationSection from './sections/EducationSection'
import SkillsSection from './sections/SkillsSection'

export default function CVForm({ data, onChange }) {
  return (
    <Tabs defaultValue="personal">
      <TabsList className="grid grid-cols-4 w-full">
        <TabsTrigger value="personal">Personal</TabsTrigger>
        <TabsTrigger value="experience">Experience</TabsTrigger>
        <TabsTrigger value="education">Education</TabsTrigger>
        <TabsTrigger value="skills">Skills</TabsTrigger>
      </TabsList>
      <TabsContent value="personal">
        <PersonalInfoSection data={data.personalInfo} onChange={onChange} />
      </TabsContent>
      {/* ... other tab contents */}
    </Tabs>
  )
}
```

---

### `[30:00 – 50:00]` 🤖 AI Integration with Claude

**How AI enhancement works:**

```
┌─────────────────────────────────────────────────────────────────┐
│                   AI ENHANCEMENT FLOW                          │
│                                                                 │
│  User clicks "✨ Enhance"                                       │
│         │                                                       │
│         ▼                                                       │
│  Next.js API Route (/api/enhance)                              │
│         │                                                       │
│         ▼                                                       │
│  Claude API (claude-sonnet-4-6)                                │
│    ● System: "You are a professional CV writer..."              │
│    ● User: section content + context                           │
│         │                                                       │
│         ▼                                                       │
│  Stream response back to UI                                    │
│         │                                                       │
│         ▼                                                       │
│  User reviews + accepts / rejects                              │
└─────────────────────────────────────────────────────────────────┘
```

**API route implementation:**

```typescript
// src/app/api/enhance/route.ts
import Anthropic from '@anthropic-ai/sdk'
import { NextRequest } from 'next/server'

const client = new Anthropic()

export async function POST(req: NextRequest) {
  const { section, content, jobTitle } = await req.json()

  const systemPrompt = `You are an expert CV writer and career coach.
Your task is to enhance CV content to be more impactful, professional, and ATS-friendly.
Use strong action verbs, quantify achievements where possible, and maintain authenticity.
Return only the enhanced content without explanation.`

  const userPrompt = `Enhance this ${section} section for a ${jobTitle} role:

${JSON.stringify(content, null, 2)}

Requirements:
- Use strong action verbs
- Quantify achievements where possible
- Keep it concise and impactful
- Maintain a professional tone`

  const stream = await client.messages.stream({
    model: 'claude-sonnet-4-6',
    max_tokens: 1024,
    system: systemPrompt,
    messages: [{ role: 'user', content: userPrompt }],
  })

  return new Response(stream.toReadableStream())
}
```

**AI features overview:**

```
┌─────────────────────────────────────────────────────────────────┐
│                      AI FEATURES                               │
├──────────────────────┬──────────────────────────────────────────┤
│  Feature             │  Description                             │
├──────────────────────┼──────────────────────────────────────────┤
│  Smart Suggestions   │  Per-section enhancement tips            │
│  One-click Rewrite   │  Full section AI rewrite                 │
│  ATS Optimization    │  Keyword analysis for job descriptions   │
│  Tone Analysis       │  Professional tone scoring               │
│  Achievement Boost   │  Convert duties to achievements          │
└──────────────────────┴──────────────────────────────────────────┘
```

**Smart suggestions component:**

```tsx
// src/components/AISuggestions.tsx
'use client'
import { useState } from 'react'
import { Button } from '@/components/ui/button'
import { Sparkles } from 'lucide-react'

export default function AISuggestions({ section, content, onApply }) {
  const [suggestion, setSuggestion] = useState('')
  const [loading, setLoading] = useState(false)

  async function enhance() {
    setLoading(true)
    const res = await fetch('/api/enhance', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ section, content }),
    })
    setSuggestion(await res.text())
    setLoading(false)
  }

  return (
    <div className="mt-4 p-4 border border-[#3ECF8E]/30 rounded-lg bg-[#3ECF8E]/5">
      <Button
        onClick={enhance}
        disabled={loading}
        className="bg-[#3ECF8E] text-black hover:bg-[#3ECF8E]/90"
      >
        <Sparkles className="mr-2 h-4 w-4" />
        {loading ? 'Enhancing...' : 'AI Enhance'}
      </Button>
      {suggestion && (
        <div className="mt-3">
          <p className="text-sm text-muted-foreground mb-2">AI Suggestion:</p>
          <p className="text-sm">{suggestion}</p>
          <Button size="sm" onClick={() => onApply(suggestion)} className="mt-2">
            Apply
          </Button>
        </div>
      )}
    </div>
  )
}
```

---

### `[50:00 – 60:00]` 🧪 Testing, Bug Fixing & Deploy

**QA checklist:**

```
┌─────────────────────────────────────────────────────────────────┐
│                    QA CHECKLIST                                │
├─────────────────────────────────────────────────────────────────┤
│  ✓  Form validation works for all sections                     │
│  ✓  Real-time preview updates as user types                    │
│  ✓  Dark / light mode toggle persists on refresh               │
│  ✓  AI enhancement handles API errors gracefully               │
│  ✓  CV saves to Supabase and loads correctly                   │
│  ✓  Authentication flow (login, signup, logout)                │
│  ✓  Export produces readable PDF / Markdown                    │
│  ✓  Mobile responsive layout works on phone                    │
│  ✓  All RLS policies secure user data properly                 │
└─────────────────────────────────────────────────────────────────┘
```

**Vercel deployment:**

```bash
# Deploy to Vercel
npm install -g vercel
vercel

# Set these environment variables in your Vercel dashboard:
#   NEXT_PUBLIC_SUPABASE_URL
#   NEXT_PUBLIC_SUPABASE_ANON_KEY
#   ANTHROPIC_API_KEY
```

---

### `[60:00 – 90:00]` 🎤 Q&A + Architecture Deep-Dive

**Topics to cover:**

```
┌─────────────────────────────────────────────────────────────────┐
│                    Q&A TOPICS                                  │
├──────────────────────┬──────────────────────────────────────────┤
│  Topic               │  Details                                 │
├──────────────────────┼──────────────────────────────────────────┤
│  Scaling with APEX   │  How the swarm handles concurrent users  │
│  AI Prompt Eng.      │  Crafting effective CV prompts           │
│  Supabase RLS        │  Row-level security deep dive            │
│  Next.js App Router  │  Server vs client components strategy    │
│  PDF Export          │  Puppeteer vs react-pdf vs html-to-pdf   │
│  Custom Themes       │  Building your own design system         │
│  Production Tips     │  Rate limiting, caching, monitoring      │
│  Open Source         │  How to contribute to cv-builder         │
└──────────────────────┴──────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
cv-builder/
├── src/
│   ├── app/
│   │   ├── (auth)/
│   │   │   ├── login/page.tsx
│   │   │   └── signup/page.tsx
│   │   ├── (dashboard)/
│   │   │   └── builder/page.tsx
│   │   ├── api/
│   │   │   ├── enhance/route.ts       ← Claude AI endpoint
│   │   │   └── export/route.ts        ← PDF / MD export
│   │   └── layout.tsx
│   ├── components/
│   │   ├── ui/                        ← shadcn/ui components
│   │   ├── CVForm.tsx
│   │   ├── CVPreview.tsx
│   │   ├── AISuggestions.tsx
│   │   └── sections/
│   │       ├── PersonalInfoSection.tsx
│   │       ├── ExperienceSection.tsx
│   │       ├── EducationSection.tsx
│   │       └── SkillsSection.tsx
│   ├── lib/
│   │   ├── supabase/
│   │   │   ├── client.ts
│   │   │   └── server.ts
│   │   └── types.ts
│   └── styles/
│       └── globals.css
├── .env.local                         ← NEVER commit
├── .gitignore
├── package.json
└── README.md
```

---

## 🔗 Resources

```
┌─────────────────────────────────────────────────────────────────┐
│                     USEFUL LINKS                               │
├──────────────────────┬──────────────────────────────────────────┤
│  Resource            │  URL                                     │
├──────────────────────┼──────────────────────────────────────────┤
│  CV Builder Repo     │  github.com/fratilanico/cv-builder       │
│  Next.js Docs        │  nextjs.org/docs                         │
│  Supabase Docs       │  supabase.com/docs                       │
│  Claude API Docs     │  docs.anthropic.com                      │
│  shadcn/ui           │  ui.shadcn.com                           │
│  Vercel Deploy       │  vercel.com/docs                         │
│  Tailwind CSS        │  tailwindcss.com                         │
└──────────────────────┴──────────────────────────────────────────┘
```

> No existing CV/resume materials were found in the workspace at scan time.
> Add your materials to a `resources/` directory in this repo and reference them here.

---

## 🤖 Built with APEX OS

This webinar is part of the **APEX OS** open-source agent swarm platform — an autonomous multi-agent development system.

```
┌─────────────────────────────────────────────────────────────────┐
│  APEX OS  ·  Autonomous Development Platform                   │
│  Every feature demo'd in this webinar was built by AI agents   │
│  working in parallel — just like you'll build in production.   │
└─────────────────────────────────────────────────────────────────┘
```

---

*Made with ❤️ by Nico Fratila · APEX OS Webinar Series*
