# Discovery Report: GitHub Profile Portfolio

## Project Overview
- **User**: hoangduy0308
- **Goal**: Personal portfolio website displaying GitHub profile
- **Style**: Simple, clean, minimal
- **Stack**: React + Vite

## GitHub API Research

### REST API Endpoints (No Auth Required)
```
GET https://api.github.com/users/{username}           → User info (avatar, bio, name, location, followers, following)
GET https://api.github.com/users/{username}/repos     → Public repositories
```

### User Data Structure
```json
{
  "login": "hoangduy0308",
  "avatar_url": "...",
  "html_url": "https://github.com/hoangduy0308",
  "name": "...",
  "bio": "...",
  "location": "...",
  "blog": "...",
  "public_repos": 10,
  "followers": 50,
  "following": 30,
  "created_at": "..."
}
```

### Repository Data Structure
```json
{
  "name": "repo-name",
  "description": "...",
  "html_url": "...",
  "language": "JavaScript",
  "stargazers_count": 5,
  "forks_count": 2,
  "topics": ["react", "nodejs"],
  "updated_at": "..."
}
```

## Technical Constraints

### Dependencies Needed
- React 18+
- Vite 5+
- react-router-dom (optional, single page có thể không cần)
- Lucide-react hoặc react-icons (icons)

### Deployment Target
- GitHub Pages (static hosting)
- Build output: `dist/` folder

## UI Sections Planned

1. **Hero Section**
   - Avatar (circular)
   - Name + Username
   - Bio
   - Social links (GitHub, LinkedIn, Email)
   - Stats (repos, followers, following)

2. **About Section**
   - Introduction text
   - Location

3. **Skills Section**
   - Tech stack badges/pills
   - Có thể hardcode hoặc extract từ repo languages

4. **Projects Section**
   - Top 6 repos (sorted by stars/updated)
   - Card layout: name, description, language, stars, forks
   - Link to repo

5. **Contact Section**
   - Email link
   - Social links

## Design Direction

### Style: Clean Minimal
- Light theme với accent color nhẹ (blue/teal)
- Typography: System fonts hoặc clean sans-serif
- Whitespace generous
- Subtle shadows, no heavy effects
- Responsive: mobile-first

### Avoid (AI Slop)
- Gradient text
- Glassmorphism
- Neon accents
- Cards nested in cards
- Centered everything

## External References
- GitHub REST API: https://docs.github.com/en/rest
- Vite React template: `npm create vite@latest -- --template react`
