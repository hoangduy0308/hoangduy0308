# Approach: GitHub Profile Portfolio

## Gap Analysis Summary

| Component | Have | Need | Gap |
|-----------|------|------|-----|
| Data fetching | Basic fetch concept | Loading/error states, caching | Error handling UX, rate limit handling |
| Hero | Planned | Fallbacks for missing data | Handle null bio/name |
| Skills | Auto-derive idea | Clear extraction logic | Hardcode + merge from repos |
| Projects | Top 6 concept | Sorting/filter rules | Exclude forks, sort by stars |
| Accessibility | - | Semantic HTML, ARIA | Full a11y implementation |
| SEO | - | Meta tags, OG cards | Add metadata |
| Deployment | GitHub Pages | Correct base config | Configure vite.config |

## Recommended Approach

### Architecture
```
src/
├── main.jsx                 # Entry point
├── App.jsx                  # Root component
├── config/
│   └── siteConfig.js        # Username, social links, skills
├── services/
│   └── githubApi.js         # API functions
├── hooks/
│   └── useGithubProfile.js  # Data fetching hook
├── components/
│   ├── Avatar.jsx
│   ├── Section.jsx
│   ├── StatBadge.jsx
│   ├── RepoCard.jsx
│   ├── SkillPill.jsx
│   └── IconLink.jsx
├── sections/
│   ├── HeroSection.jsx
│   ├── AboutSection.jsx
│   ├── SkillsSection.jsx
│   ├── ProjectsSection.jsx
│   └── ContactSection.jsx
└── styles/
    └── globals.css
```

### Data Flow
```
App.jsx
  └── useGithubProfile(username)
        ├── fetchUser() ──┐
        └── fetchRepos() ─┴── Promise.all
              │
              ▼
        { user, repos, loading, error }
              │
              ▼
        Pass to sections
```

### Key Decisions
1. **JavaScript** (not TypeScript) - simple project, faster to build
2. **CSS Variables** for theming - easy to customize
3. **Lucide-react** for icons - tree-shakeable, clean design
4. **No routing** - single page, no need for react-router
5. **localStorage caching** - reduce API calls

## Risk Map

| Component | Risk | Reason | Verification |
|-----------|------|--------|--------------|
| GitHub API | MEDIUM | Rate limits, network errors | Test error states |
| Hero Section | LOW | Simple rendering | Handle null fields |
| About Section | LOW | Static text | Conditional render |
| Skills Section | MEDIUM | Logic complexity | Hardcode + derive hybrid |
| Projects Section | MEDIUM | Sorting/filtering | Clear rules, test edge cases |
| Contact Section | LOW | Simple links | Validate URLs |
| Deployment | MEDIUM | Config issues | Test after deploy |
| Accessibility | MEDIUM | Often overlooked | Manual + automated checks |

## Tech Stack Final

```json
{
  "dependencies": {
    "react": "^18.x",
    "react-dom": "^18.x",
    "lucide-react": "latest"
  },
  "devDependencies": {
    "vite": "^5.x",
    "@vitejs/plugin-react": "^4.x"
  }
}
```
