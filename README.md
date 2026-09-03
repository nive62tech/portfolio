# Niveditha S Nair — Portfolio Website

Personal portfolio website for **Niveditha S Nair**, B.Tech AI & ML student at Chinmaya Vishwavidyapeeth.  
Live at → **[nive62tech.github.io](https://nive62tech.github.io)**

---

## Tech Stack

| Layer | Tech |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 (custom, no frameworks) |
| Logic | Vanilla JavaScript (no build tools) |
| Hosting | GitHub Pages |
| Fonts | Outfit · JetBrains Mono (Google Fonts) |

No React. No Node. No dependencies. Just two files — `index.html` and `style.css`.

---

## File Structure

```
nive62tech.github.io/
│
├── index.html              ← entire site — all content, sections, JS
├── style.css               ← all styling
├── README.md               ← this file
│
├── images/
│   ├── profile.jpg         ← hero portrait (half-body, PNG with transparent bg recommended)
│   ├── hero-poster.jpg     ← video fallback image
│   │
│   ├── vizora.jpg          ← project card + modal main image
│   ├── vizora-1.jpg        ← project gallery image 1
│   ├── vizora-2.jpg        ← project gallery image 2
│   ├── promptlens.jpg
│   ├── neuronote.jpg
│   ├── airwriter.jpg
│   ├── projectpilot.jpg
│   ├── emojitranslator.jpg
│   │
│   ├── exp/
│   │   ├── sauvc.jpg       ← SAUVC experience card image
│   │   ├── sauvc-1.jpg     ← SAUVC gallery image
│   │   ├── sauvc-2.jpg
│   │   ├── ieee.jpg
│   │   ├── ieee-1.jpg
│   │   ├── backend.jpg
│   │   └── debate.jpg
│   │
│   └── research/
│       ├── paddy-1.jpg     ← presentation/poster photos
│       ├── paddy-poster.jpg
│       ├── skin-tone-1.jpg
│       ├── skin-tone-pres.jpg
│       ├── coral-poster.jpg
│       ├── coral-1.jpg
│       └── emotional-pres.jpg
│
└── videos/
    └── hero-bg.mp4         ← hero background video (dark ambient loop)
```

---

## Sections

| Section | Description |
|---|---|
| **Hero** | Full-screen video background, name, typewriter role, portrait, CTA buttons |
| **About** | Bio, education card, 4 stat cards, skills by category |
| **Projects** | Bento grid with category filters + load more. Click → in-page modal with gallery, highlights, clone command |
| **Experience** | Clickable cards for internships + roles. Click → modal with image gallery |
| **Research** | Papers list with Paper/IEEE links. Click → modal with presentation photos |
| **Achievements** | Competition wins and awards |
| **Contact** | Direct links + contact form |

---

## Features

- **Video hero background** — fullscreen looping video with dark overlay
- **In-page project modal** — no page redirects; click a card → modal slides up with image gallery, highlights, GitHub link, clone command with copy button
- **Experience galleries** — internship and role cards open the same modal with photos
- **Research galleries** — papers open with presentation photos + direct paper link button
- **Category filter** — filter projects by AI/ML, Computer Vision, Mobile, NLP, Tools, Open Source
- **Load More** — shows 6 projects at a time; expands on click
- **Typewriter effect** — cycling role descriptions in the hero
- **Scroll reveal animations** — sections animate in as you scroll
- **Responsive** — works on mobile, tablet, desktop
- **No external dependencies** — loads fast, works offline after first load

---

## How to Run Locally

No build step needed. Just open the file:

```bash
git clone https://github.com/nive62tech/nive62tech.github.io.git
cd nive62tech.github.io

# Open directly in browser
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

Or use VS Code Live Server extension for hot reload.

---

## How to Deploy Changes

```bash
git add .
git commit -m "describe your change"
git push origin main
```

Live site updates within **1–3 minutes**. Hard refresh with `Ctrl + Shift + R` if changes don't show.

---

## How to Add a New Project

### Step 1 — Add data entry in `index.html`

Find `const DATA = {` → `project: {` and add:

```javascript
your_project_id: {
  title: 'Project Title',
  tagline: 'One-line description for the modal header.',
  tags: ['Tag1', 'Tag2', 'Tag3'],
  links: [
    { label: 'GitHub', url: 'https://github.com/nive62tech/repo', icon: 'github' },
    { label: 'Clone', clone: 'git clone https://github.com/nive62tech/repo.git' }
  ],
  meta: { Role: 'Solo Builder', Stack: 'Python · FastAPI', Status: 'Active' },
  overview: 'Longer description of what the project does and why.',
  highlights: [
    'Key feature one',
    'Key feature two',
    'Key feature three'
  ],
  images: ['images/your_project_id.jpg', 'images/your_project_id-1.jpg']
},
```

> ⚠️ The key name (`your_project_id`) must exactly match what you use in the card's `onclick` and in the image filenames.

### Step 2 — Add the card HTML

Find `<div class="proj-grid" id="projGrid">` and add:

```html
<div class="pcard" data-category="ai-ml tools" onclick="openModal('project','your_project_id')">
  <div class="pcard-img">
    <img src="images/your_project_id.jpg" alt="Title" onerror="this.style.display='none'">
    <div class="pcard-img-fallback"><!-- SVG icon --></div>
  </div>
  <div class="pcard-body">
    <div class="pcard-tags"><span>Tag1</span><span>Tag2</span></div>
    <h3>Project Title</h3>
    <p>Short description for the card (1–2 lines).</p>
    <div class="pcard-hint">Click to explore →</div>
  </div>
</div>
```

**Available category values for `data-category`:**
`ai-ml` · `computer-vision` · `mobile` · `open-source` · `nlp` · `tools`  
You can combine: `data-category="ai-ml computer-vision"`

### Step 3 — Add images

```
images/your_project_id.jpg      ← main image (card + modal hero)
images/your_project_id-1.jpg    ← gallery image 1
images/your_project_id-2.jpg    ← gallery image 2
```

---

## How to Add a Research Paper

### Step 1 — Add data in `const DATA.research`

```javascript
paper_key: {
  title: 'Full Paper Title',
  tagline: 'Short description of contribution.',
  tags: ['Badge Type', 'Keyword 1', 'Keyword 2'],
  links: [
    { label: 'View Paper', url: 'https://doi.org/xxxxx', icon: 'paper' },
    { label: 'IEEE Xplore', url: 'https://ieeexplore.ieee.org/...', icon: 'external' }
  ],
  meta: { Published: 'Month Year', Journal: 'Journal Name', Conference: 'Conf Name', Venue: 'Location' },
  overview: 'Abstract or description of the work.',
  highlights: ['Key contribution 1', 'Key contribution 2'],
  images: ['images/research/paper-key-1.jpg', 'images/research/paper-key-pres.jpg']
},
```

### Step 2 — Add the row HTML

Find `<div class="research-list reveal">` and add:

```html
<div class="research-item" onclick="openModal('research','paper_key')">
  <div class="ri-left">
    <span class="ri-badge pub">Published</span>
    <span class="ri-date">Month Year</span>
    <a href="https://doi.org/xxxxx" class="ri-paper-link" onclick="event.stopPropagation()" title="View Paper">
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/><polyline points="15 3 21 3 21 9"/><line x1="10" y1="14" x2="21" y2="3"/></svg>
      Paper
    </a>
  </div>
  <div class="ri-body">
    <h4>Full Paper Title Here</h4>
    <p>Conference/Journal · Venue</p>
    <div class="ri-tags"><span>Keyword 1</span><span>Keyword 2</span></div>
    <div class="ri-gallery-hint">📷 Click to view presentation photos</div>
  </div>
</div>
```

**Badge classes:** `ri-badge pub` · `ri-badge ieee` · `ri-badge acc` · `ri-badge pres`

---

## How to Update Paper Links

Find the research entry in `DATA.research` and update the `url` field:

```javascript
links: [
  { label: 'View Paper', url: 'https://actual-doi-or-journal-link.com', icon: 'paper' }
],
```

Also update the `href` in the HTML row's `<a class="ri-paper-link">` tag.

---

## How to Change the Profile Photo

1. Replace `images/profile.jpg` with your new photo
2. If filename changed, update in `index.html`:
   ```html
   src="images/profile.jpg"
   ```
3. For best results — use a PNG with transparent background. Go to **[remove.bg](https://remove.bg)**, upload, download PNG, rename to `profile.png`, and update the `src` accordingly.

---

## How to Change the Background Video

1. Download a dark ambient tech loop video (MP4) from **Pexels**, **Mixkit**, or **Coverr**
   - Good search terms: `neural network dark`, `particle network`, `dark data stream`, `abstract tech dark`
2. Rename to `hero-bg.mp4`
3. Place in `videos/` folder
4. Also add `images/hero-poster.jpg` as a fallback image shown before video loads
5. Keep file size under **10MB** for fast loading

---

## How to Change Colors

Open `style.css` and edit the CSS variables at the top:

```css
:root {
  --bg:      #000000;   /* main background */
  --bg2:     #080808;   /* dark section bg */
  --bg3:     #111111;   /* card surfaces */
  --white:   #ffffff;   /* primary text + buttons */
  --muted:   rgba(255,255,255,0.52);  /* secondary text */
  --dim:     rgba(255,255,255,0.28);  /* label text */
  --border:  rgba(255,255,255,0.14);  /* hover borders */
  --border2: rgba(255,255,255,0.07);  /* default borders */
}
```

---

## How to Edit Personal Info

| What | Where in index.html |
|---|---|
| Name | Search `Niveditha S Nair` — appears in hero, footer, meta |
| Email | Search `nivtecho@gmail.com` |
| LinkedIn | Search `niveditha-s-nair` |
| GitHub | Search `nive62tech` |
| CGPA | Search `9.44` |
| Availability | Search `Open to AI/ML Internships` and `Currently Available` |
| Typewriter phrases | Find `const ph = [` inside `<script>` |

---

## Current Content

### Projects (6)
| ID | Title | Status |
|---|---|---|
| `vizora` | Vizora — AI Data Visualization | Active · Open Source |
| `promptlens` | PromptLens — LLM Evaluation | Active |
| `neuronote` | Neuro_Note — Voice Task App | In Progress |
| `airwriter` | AI Air Writer — Gesture Drawing | Complete |
| `projectpilot` | ProjectPilot — Student Mentor | Active · Open Source |
| `emojitranslator` | Emoji Translator — NLP | In Progress |

### Research (5)
| ID | Title | Status |
|---|---|---|
| `paddy_drones` | Paddy Farming & Drones | Published · Harvest Journal |
| `skin_tone` | Skin Tone Bug Bite Classification | IEEE Xplore · Accepted |
| `rl_reward` | Reward Shaping DQN/DDQN | Accepted · ICDRLDS-26 |
| `emotional_ai` | AI & Emotional Intelligence | Presented · ICDTEBM 2026 |
| `coral_reef` | Coral Reef Habitat Mapping | Poster + Flash Talk · IIOSC-2025 |

### Experience (4)
| ID | Role |
|---|---|
| `sauvc_lead` | SAUVC Technical Lead — Nautical Navigators |
| `backend_intern` | Backend Development Intern — Navigators |
| `ieee_chair` | IEEE Student Branch Chair |
| `debate_treasurer` | Creative Debate Society — Treasurer |

---

## Contact

**Niveditha S Nair**  
📧 nivtecho@gmail.com  
nivedithasathishnair@gmail.com
💼 [linkedin.com/in/niveditha-s-nair](https://linkedin.com/in/niveditha-s-nair)  
🐙 [github.com/nive62tech](https://github.com/nive62tech)