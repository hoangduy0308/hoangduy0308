# Execution Plan: GitHub Profile Portfolio

Epic: GitHub Profile Portfolio Website
Generated: 2026-01-14
Updated: 2026-01-14 (v3 - final review)
Username: hoangduy0308

## Overview

Build a React + Vite portfolio website that displays GitHub profile data with clean, minimal design.

## Beads (Work Items)

### Phase 1: Setup & Infrastructure

| ID | Title | Type | Priority | Dependencies |
|----|-------|------|----------|--------------|
| bd-1 | Initialize Vite + React project | task | P0 | - |
| bd-2 | Setup project structure & config | task | P0 | bd-1 |
| bd-3 | Create siteConfig with user data | task | P1 | bd-2 |
| bd-4 | Setup global CSS & design tokens | task | P0 | bd-2 |

### Phase 2: Core Services & Hooks

| ID | Title | Type | Priority | Dependencies |
|----|-------|------|----------|--------------|
| bd-5 | Create githubApi service | task | P0 | bd-2 |
| bd-6 | Create useGithubProfile hook | task | P0 | bd-5 |
| bd-7 | Add localStorage caching | task | P1 | bd-6 |

### Phase 3: Components

| ID | Title | Type | Priority | Dependencies |
|----|-------|------|----------|--------------|
| bd-8 | Create UI atoms (Avatar, StatBadge, SkillPill, IconLink) | task | P1 | bd-4 |
| bd-9 | Create Section wrapper component | task | P1 | bd-4 |
| bd-10 | Create RepoCard component | task | P1 | bd-4 |

### Phase 4: Sections

| ID | Title | Type | Priority | Dependencies |
|----|-------|------|----------|--------------|
| bd-11 | Create HeroSection | task | P0 | bd-3, bd-6, bd-8 |
| bd-12 | Create AboutSection | task | P1 | bd-6, bd-9 |
| bd-13 | Create SkillsSection | task | P1 | bd-3, bd-6, bd-8, bd-9 |
| bd-14 | Create ProjectsSection | task | P0 | bd-6, bd-9, bd-10 |
| bd-15 | Create ContactSection | task | P1 | bd-3, bd-8, bd-9 |

### Phase 5: Integration & Polish

| ID | Title | Type | Priority | Dependencies |
|----|-------|------|----------|--------------|
| bd-16 | Integrate all sections in App.jsx | task | P0 | bd-11, bd-12, bd-13, bd-14, bd-15 |
| bd-17 | Add loading & error states | task | P0 | bd-16 |
| bd-18 | Add responsive styles | task | P1 | bd-16 |
| bd-19 | Add SEO meta tags | task | P2 | bd-16 |
| bd-20 | Add basic accessibility | task | P2 | bd-16 |

### Phase 6: Deployment

| ID | Title | Type | Priority | Dependencies |
|----|-------|------|----------|--------------|
| bd-21 | Configure vite for GitHub Pages | task | P0 | bd-2 |
| bd-22 | Setup GitHub Actions deploy | task | P1 | bd-21 |

## Tracks (Parallel Execution)

| Track | Agent | Beads (in order) | File Scope |
|-------|-------|------------------|------------|
| 1 | BlueLake | bd-1 → bd-2 → bd-3 → bd-4 | `src/config/**`, `src/styles/**`, `package.json` |
| 2 | GreenCastle | bd-5 → bd-6 → bd-7 | `src/services/**`, `src/hooks/**` |
| 3 | RedStone | bd-8 → bd-9 → bd-10 | `src/components/**` |
| 4 | PurpleBear | bd-11 → bd-12 → bd-13 → bd-14 → bd-15 | `src/sections/**` |
| 5 | SilverFox | bd-21 → bd-22 | `vite.config.js`, `.github/workflows/**` |
| 6 | GoldEagle | bd-16 → bd-17 → bd-18 → bd-19 → bd-20 | `src/App.jsx`, `src/main.jsx`, `index.html` |

**Cross-Track Dependencies:**
- Track 2 starts after bd-2 (Track 1)
- Track 3 starts after bd-4 (Track 1)
- Track 4 starts after bd-3, bd-6 (Track 1+2) and bd-8, bd-9 (Track 3)
- Track 5 starts after bd-2 (Track 1) - can run early in parallel
- Track 6 starts after all sections complete (bd-11..15 from Track 4)

## Dependency Graph

```
bd-1
  │
  ▼
bd-2 ───────────────┬─────────────┬─────────────────────────┐
  │                 │             │                         │
  ▼                 ▼             ▼                         ▼
bd-3              bd-4          bd-5                      bd-21
  │                 │             │                         │
  │                 │             ▼                         ▼
  │                 │           bd-6 ──────────┐          bd-22
  │                 │             │            │
  │                 │             ▼            │
  │                 │           bd-7           │
  │                 │                          │
  │                 ├────────┬────────┐        │
  │                 │        │        │        │
  │                 ▼        ▼        ▼        │
  │               bd-8     bd-9    bd-10       │
  │                 │        │        │        │
  ├─────────────────┼────────┼────────┼────────┤
  │                 │        │        │        │
  ▼                 ▼        ▼        ▼        ▼
bd-11            bd-12    bd-13    bd-14    bd-15
  │                │        │        │        │
  └────────────────┴────────┴────────┴────────┘
                            │
                            ▼
                          bd-16
                            │
               ┌────────────┼────────────┬────────────┐
               │            │            │            │
               ▼            ▼            ▼            ▼
             bd-17        bd-18        bd-19        bd-20
```

## Summary

| Metric | Value |
|--------|-------|
| Total Beads | 22 |
| P0 (Critical) | 10 (bd-1,2,4,5,6,11,14,16,17,21) |
| P1 (High) | 10 (bd-3,7,8,9,10,12,13,15,18,22) |
| P2 (Medium) | 2 (bd-19,20) |
| Parallel Tracks | 6 |
| Estimated Time | ~2 hours |

## Changes from v2

- ✅ Added bd-6 and bd-3 as dependencies for bd-13 (SkillsSection)
- ✅ Added Track 6 (GoldEagle) for integration beads bd-16..20
- ✅ Clarified file scope: Track 5 owns vite.config.js, Track 1 owns package.json
- ✅ Fixed Summary metrics (P0=10, P2=2)

## Ready to Execute

Run `bd ready` to start with highest priority unblocked beads.
