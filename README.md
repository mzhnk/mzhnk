<h1 align="center">
  <img src="https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=28&pause=1000&color=00AFC2&center=true&vCenter=true&width=750&lines=Hi%2C+I'm+mzhnk+%F0%9F%91%8B;Student+Developer+from+Indonesia;Building+AI%2C+Web+%26+Embedded+Projects;Currently+building%3A+AI+Pet+Robot" alt="Hi, I'm mzhnk" />
</h1>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=mzhnk&color=0F6675&style=flat-square&label=PROFILE+VIEWS" alt="Profile views" />
  <img src="https://img.shields.io/github/followers/mzhnk?style=flat-square&label=Followers&color=0F6675" alt="GitHub followers" />
  <img src="https://img.shields.io/github/stars/mzhnk?style=flat-square&label=Total+Stars&color=0F6675" alt="Total stars" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Location-Indonesia-0F6675?style=flat-square&logo=googlemaps&logoColor=white" alt="Location: Indonesia" />
  <img src="https://img.shields.io/badge/Status-Building_in_public-0F6675?style=flat-square" alt="Status: building in public" />
  <img src="https://img.shields.io/badge/Focus-AI_%7C_Web_%7C_Embedded_%7C_Robotics-0F6675?style=flat-square" alt="Focus: AI, web, embedded, robotics" />
</p>

---

## 👋 About Me

I'm a student developer from Indonesia. Most of what I know comes from building real projects, not just from following tutorials. My interests span AI, web development, embedded systems, and robotics, usually at the point where software has to behave predictably in real time.

Right now, that means two projects: an AI pet robot and a 3D periodic table in the browser. Beyond making things work, I care about the architecture underneath: how state is shared, how failures are handled, and what makes a system reliable enough to trust.

---

## 🚀 Featured Projects

### AI Pet Robot · V2 "Make It Aware"

A desktop pet robot built from an ESP32 "body" and a Flask-based "Local AI" brain that talk to each other over WebSocket. It's my way of learning embedded systems and sensor fusion by building something physical that has to keep working, not just something that compiles.

<!-- Add project screenshot here: a real photo or demo GIF of the robot, uploaded to the repo -->

**What makes it technically interesting:**

- **Perception:** an ESP32-CAM detects people and buckets their position (left, center, right), an HC-SR04 measures distance to obstacles, and an MPU-6050 catches falls and tilts.
- **Fusion:** all three sensor streams feed into one shared `WorldState`.
- **Decision:** a 13-state behavior FSM (curious → follow → interact → avoid → recover) turns that state into behavior.
- **Safety first:** obstacle avoidance and fall recovery are resolved deterministically on the ESP32 itself, so the AI layer can't override safety-critical decisions.
- **Offline by design:** the robot keeps its base behaviors even if the WiFi link or the AI backend drops.

```
Sensors                        Fusion              Decision                 Output
────────                       ───────             ─────────                ──────
ESP32-CAM   (person zoning) ┐
HC-SR04     (distance)      ├──▶  WorldState ──▶  13-state FSM  ──▶  motors · LEDs · sound
MPU-6050    (fall / tilt)   ┘                          ▲
                                                       │
                              Flask "Local AI" (WebSocket, offline-capable)
```

> **V1 → V2:** *Make It Alive* (move, turn, react to touch) → *Make It Aware* (see, sense distance, detect falls, decide)

**Status:** Actively developed · additive V2 protocol · verified by 206 automated tests (134 native, 51 pytest, 21 E2E) · September 2026<br>
**Stack:** `C++` `ESP32` `WebSocket` `Flask`<br>
**Repo:** [github.com/mzhnk/ai-pet-robot](https://github.com/mzhnk/ai-pet-robot)

<br>

### 3D Periodic Table

An interactive 3D visualization of all 118 chemical elements with four swappable layouts (Table, Sphere, Helix, Grid), smooth Anime.js transitions, and mouse, touch, and long-press interaction, in English and Indonesian.

The current version is the result of an architectural refactor: a single 690-line `index.html` split into 20 modular ES Module files, with zero behavior change and a much cleaner structure to build on.

<!-- Add project screenshot here: a real screenshot of one of the four layouts, uploaded to the repo -->

**What makes it technically interesting:**

- Pure CSS 3D transforms driving four distinct layout modes
- Modular ES Module architecture, no bundler and no framework
- Bilingual UI (EN/ID) built into the component structure, not bolted on

**Status:** Refactor shipped · September 2026<br>
**Stack:** `JavaScript` `ES Modules` `CSS3` `Anime.js`<br>
**Repo:** [github.com/mzhnk/periodic-table](https://github.com/mzhnk/periodic-table)

---

## 🛠️ Tech Stack

**Languages**

<p>
  <img src="https://skillicons.dev/icons?i=py,js,cpp,html,css&theme=dark" alt="Python, JavaScript, C++, HTML, CSS" />
</p>

**Currently Exploring**

<p>
  <img src="https://skillicons.dev/icons?i=ts,react,nextjs,tailwind,postgres,prisma&theme=dark" alt="TypeScript, React, Next.js, Tailwind CSS, PostgreSQL, Prisma" />
  <br>
  <img src="https://img.shields.io/badge/shadcn%2Fui-0F6675?style=flat-square" alt="shadcn/ui" />
  <img src="https://img.shields.io/badge/Zod-0F6675?style=flat-square" alt="Zod" />
</p>

**Backend & Data**

<p>
  <img src="https://skillicons.dev/icons?i=flask,sqlite&theme=dark" alt="Flask, SQLite" />
</p>

**Embedded & Hardware**

<p>
  <img src="https://skillicons.dev/icons?i=arduino&theme=dark" alt="Arduino" />
  <img src="https://img.shields.io/badge/ESP32-0F6675?style=flat-square&logo=espressif&logoColor=white" alt="ESP32" />
</p>

**Testing & Tooling**

<p>
  <img src="https://skillicons.dev/icons?i=git,github,vitest&theme=dark" alt="Git, GitHub, Vitest" />
  <img src="https://img.shields.io/badge/Playwright-0F6675?style=flat-square&logo=playwright&logoColor=white" alt="Playwright" />
</p>

---

## 🌱 Currently Exploring

- **Modern web development:** TypeScript, React, Next.js App Router, server actions, and type-safe application patterns
- **Embedded systems & robotics:** state machines, sensor integration, motor control, and reliable real-time systems
- **JavaScript & software architecture:** ES Modules, design patterns, and how the pieces fit together beneath the framework layer

---

## 📊 GitHub Activity

<p align="center">
  <img height="170" src="https://github-stats-extended.vercel.app/api?username=mzhnk&show_icons=true&theme=dark&hide_border=false&include_all_commits=true&count_private=false&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10" alt="GitHub stats" />
  <picture>
    <source media="(max-width: 480px)" srcset="https://github-readme-stats.shion.dev/api/top-langs/?username=mzhnk&layout=compact&theme=dark&hide_border=false&langs_count=5&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10" />
    <img height="170" src="https://github-readme-stats.shion.dev/api/top-langs/?username=mzhnk&layout=compact&theme=dark&hide_border=false&langs_count=8&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10" alt="Most used programming languages" />
  </picture>
</p>

<p align="center">
  <img height="170" src="https://streak-stats.demolab.com?user=mzhnk&theme=dark&hide_border=false&background=0D1117&border=164A55&stroke=164A55&ring=00AFC2&fire=00AFC2&currStreakLabel=00AFC2&sideLabels=8B949E&currStreakNum=DDE3F0&sideNums=DDE3F0&dates=6E7890&border_radius=10" alt="GitHub contribution streak" />
</p>

---

## 📫 Connect

<p align="center">
  <a href="https://github.com/mzhnk"><img src="https://img.shields.io/badge/GitHub-0F6675?style=for-the-badge&logo=github&logoColor=E6F7FA" alt="GitHub profile" /></a>
  <a href="mailto:zihankholidi@gmail.com"><img src="https://img.shields.io/badge/Email-0F6675?style=for-the-badge&logo=gmail&logoColor=E6F7FA" alt="Email" /></a>
  <a href="https://www.linkedin.com/in/mzhnk"><img src="https://img.shields.io/badge/LinkedIn-0F6675?style=for-the-badge&logo=linkedin&logoColor=E6F7FA" alt="LinkedIn profile" /></a>
  <a href="https://instagram.com/mzkx2201"><img src="https://img.shields.io/badge/Instagram-0F6675?style=for-the-badge&logo=instagram&logoColor=E6F7FA" alt="Instagram profile" /></a>
</p>

---

## 🎮 Just for Fun

The serious part of this profile ends above this line. Down here, it's all just for fun.

<!-- Snake animation: requires the GitHub Actions workflow (snake.yml) in .github/workflows/. The image appears after the first workflow run. -->
<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/mzhnk/mzhnk/output/github-contribution-grid-snake-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/mzhnk/mzhnk/output/github-contribution-grid-snake.svg" />
    <img alt="Snake animation eating my contribution graph" src="https://raw.githubusercontent.com/mzhnk/mzhnk/output/github-contribution-grid-snake.svg" />
  </picture>
</p>

<p align="center">
  <img src="https://ghchart.rshah.org/00AFC2/mzhnk" alt="My contribution chart for the last year" />
</p>

<!-- Milestone badges: plain shields.io images, no workflow and no token needed. Update the numbers as the projects grow. -->
<p align="center">
  <img src="https://img.shields.io/badge/Automated_Tests-206_Passing-0F6675?style=for-the-badge&logo=githubactions&logoColor=E6F7FA" alt="206 automated tests passing" />
  <img src="https://img.shields.io/badge/Pet_Robot_FSM-13_States-0F6675?style=for-the-badge&logo=arduino&logoColor=E6F7FA" alt="13-state behavior FSM on the pet robot" />
  <img src="https://img.shields.io/badge/3D_Periodic_Table-118_Elements-0F6675?style=for-the-badge&logo=electron&logoColor=E6F7FA" alt="3D periodic table with all 118 elements" />
</p>

<p align="center">
  <img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=tokyonight" alt="Random programming quote" />
</p>

<p align="center">
  <img src="https://readme-jokes.vercel.app/api?bgColor=%230D1117&borderColor=%23164A55&codeColor=%2300AFC2" alt="Random dev joke" />
</p>


---

<p align="center">
  <i>Consistency over talent, building in public, one commit at a time.</i><br>
  <sub>재능보다 꾸준함, 한 번에 한 커밋씩.</sub>
</p>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0F6675&height=80&section=footer" alt="" />
