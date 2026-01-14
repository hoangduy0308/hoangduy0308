# Discovery Report: GitHub Profile README with Animations

## Overview

GitHub Profile README là file README.md đặc biệt trong repo có cùng tên với username, hiển thị trên trang profile.

## Animation Components Available

### 1. Header Animation - capsule-render
- **Repo**: [kyechan99/capsule-render](https://github.com/kyechan99/capsule-render)
- **Purpose**: Dynamic SVG headers với animations (fadeIn, scaleIn, blink, etc.)
- **Usage**: 
```markdown
![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&height=200&section=header&text=Your%20Name&fontSize=50&animation=fadeIn)
```

### 2. Typing Effect - readme-typing-svg
- **Repo**: [DenverCoder1/readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg)
- **Purpose**: Animated typing text effect
- **Usage**:
```markdown
[![Typing SVG](https://readme-typing-svg.demolab.com/?lines=Full+Stack+Developer;Open+Source+Contributor)](https://git.io/typing-svg)
```

### 3. Snake Animation - snk
- **Repo**: [Platane/snk](https://github.com/Platane/snk)
- **Purpose**: Snake game ăn contribution graph
- **Requirements**: GitHub Actions workflow
- **Usage**:
```yaml
# .github/workflows/snake.yml
name: Generate Snake
on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark
      - uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
```

### 4. GitHub Stats - github-readme-stats
- **Repo**: [anuraghazra/github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
- **Purpose**: Stats cards (commits, PRs, issues, stars)
- **Usage**:
```markdown
![GitHub Stats](https://github-readme-stats.vercel.app/api?username=YOUR_USERNAME&show_icons=true&theme=radical)
```

### 5. Streak Stats - github-readme-streak-stats  
- **Repo**: [DenverCoder1/github-readme-streak-stats](https://github.com/DenverCoder1/github-readme-streak-stats)
- **Purpose**: Current streak, longest streak, total contributions
- **Usage**:
```markdown
[![GitHub Streak](https://streak-stats.demolab.com/?user=YOUR_USERNAME&theme=dark)](https://git.io/streak-stats)
```

### 6. Top Languages
- **Source**: github-readme-stats
- **Usage**:
```markdown
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_USERNAME&layout=compact&theme=radical)
```

### 7. 3D Contribution Graph
- **Repo**: [yoshi389111/github-profile-3d-contrib](https://github.com/yoshi389111/github-profile-3d-contrib)
- **Requirements**: GitHub Actions
- **Purpose**: 3D isometric view của contribution graph

### 8. Activity Graph
- **Repo**: [Ashutosh00710/github-readme-activity-graph](https://github.com/Ashutosh00710/github-readme-activity-graph)
- **Purpose**: Visual graph của activity timeline

### 9. Profile Views Counter
- **Source**: komarev.com
- **Usage**:
```markdown
![Profile Views](https://komarev.com/ghpvc/?username=YOUR_USERNAME&color=blue)
```

### 10. Tech Stack Badges
- **Source**: shields.io + simple-icons
- **Usage**:
```markdown
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
```

## Technical Constraints

- **Max file size**: README should be reasonable size
- **Rate limits**: Some APIs have rate limits (github-readme-stats)
- **GitHub Actions**: Required for snake animation và 3D contrib
- **Dark/Light mode**: Use `<picture>` element for responsive themes

## Dark/Light Mode Support

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="dark-image.svg" />
  <source media="(prefers-color-scheme: light)" srcset="light-image.svg" />
  <img alt="description" src="light-image.svg" />
</picture>
```

## Recommended Structure

```
├── README.md                    # Main profile
├── .github/
│   └── workflows/
│       └── snake.yml           # Snake animation workflow
└── assets/                     # Static assets (optional)
```
