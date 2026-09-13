<h1 align="center">
  <img src="https://readme-typing-svg.demolab.com/?font=Fira+Code&weight=600&size=28&pause=1000&color=00E0FF&center=true&vCenter=true&width=750&lines=Hi%2C+I'm+mzhnk+%F0%9F%91%8B;Student+Developer+from+Indonesia;Building+AI%2C+Web+%26+Embedded+Projects;Currently+building%3A+AI+Pet+Robot" alt="Typing SVG" />
</h1>

<p align="center">
  Student developer from Indonesia, building AI-powered applications while exploring web development, embedded systems, and robotics.
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=mzhnk&color=0F6675&style=flat-square&label=PROFILE+VIEWS" alt="Profile Views" />
  <img src="https://img.shields.io/github/followers/mzhnk?style=flat-square&label=Followers&color=0F6675" alt="GitHub Followers" />
  <img src="https://img.shields.io/github/stars/mzhnk?style=flat-square&label=Total+Stars&color=0F6675" alt="Total GitHub Stars" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Location-Indonesia-0F6675?style=flat-square&logo=googlemaps&logoColor=white" alt="Location: Indonesia" />
  <img src="https://img.shields.io/badge/Status-Building_in_public-0F6675?style=flat-square" alt="Status: Building in public" />
  <img src="https://img.shields.io/badge/Focus-AI_%7C_Web_%7C_Embedded_%7C_Robotics-0F6675?style=flat-square" alt="Focus: AI, Web, Embedded Systems, Robotics" />
</p>



---

## About Me

I'm a student developer from Indonesia, learning by building practical software and embedded systems across AI, web development, and robotics. Most of what I build is hands-on and systems-oriented: connecting a web or API layer to something that has to behave predictably in real time, whether that's a WebSocket protocol, a local AI backend, or an ESP32 that keeps its core behavior running even when the network doesn't.

Right now, I'm splitting my time between a 3D data visualization on the web and a desktop robot whose on-board behavior has to stay safe and "alive" even when its AI brain is offline. I'm especially interested in understanding not just how technologies work individually, but how the architecture underneath them makes the whole system reliable.

---

## 🚀 Featured Projects

### 🐾 AI Pet Robot — V2, "Make It Aware"

A desktop pet robot built from an ESP32 "body" and a Flask-based "Local AI" brain that talk to each other over WebSocket. It's my way of learning embedded systems and sensor fusion by building something physical that has to keep working, not just something that compiles.

**What makes it technically interesting:**
- **Perception:** an ESP32-CAM detects people and buckets their position (left / center / right), an HC-SR04 senses distance to obstacles, and an MPU-6050 catches falls and tilts.
- **Fusion:** all three sensor streams feed into a single shared `WorldState`.
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

**Status:** Actively developed · additive V2 protocol · verified by 206 automated tests (134 native · 51 pytest · 21 E2E) · Sept 2026
**Stack:** `C++` `ESP32` `WebSocket` `Flask`
**Repo:** [github.com/mzhnk/ai-pet-robot](https://github.com/mzhnk/ai-pet-robot)

<br>

### ⚛️ 3D Periodic Table

An interactive 3D visualization of all 118 chemical elements with four swappable layouts (Table, Sphere, Helix, Grid), smooth Anime.js transitions, and full mouse, touch, and long-press interaction, in English and Indonesian.

The current version is the result of an architectural refactor: a single 690-line `index.html` file split into 20 modular ES Module files, with zero behavior change but a much cleaner structure to build on.

**What makes it technically interesting:**
- Pure CSS 3D transforms driving four distinct layout modes
- Modular ES Module architecture (no bundler, no framework)
- Bilingual UI (EN/ID) built into the component structure, not bolted on

**Status:** Refactor shipped, Sept 2026
**Stack:** `JavaScript` `ES Modules` `CSS3` `Anime.js`
**Repo:** [github.com/mzhnk/periodic-table](https://github.com/mzhnk/periodic-table)

---

## 🛠️ Tech Stack

<details open>
<summary><b>Click to expand</b></summary>

**Languages**

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" />
  <img src="https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white" />
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white" />
</p>

**Currently Exploring**

<p>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=next.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind_CSS-38BDF8?style=flat-square&logo=tailwind-css&logoColor=white" />
  <img src="https://img.shields.io/badge/shadcn/ui-000000?style=flat-square" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma&logoColor=white" />
  <img src="https://img.shields.io/badge/Zod-3E67B1?style=flat-square" />
</p>

**Backend & Data**

<p>
  <img src="https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white" />
  <img src="https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white" />
</p>

**Embedded & Hardware**

<p>
  <img src="https://img.shields.io/badge/Arduino-00878F?style=flat-square&logo=arduino&logoColor=white" />
  <img src="https://img.shields.io/badge/ESP32-E7352F?style=flat-square&logo=espressif&logoColor=white" />
</p>

**Testing & Tooling**

<p>
  <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white" />
  <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" />
  <img src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white" />
</p>

</details>

---

## 🌱 Currently Exploring

* **Modern web development:** TypeScript, React, Next.js App Router, server actions, and type-safe application patterns
* **Embedded systems & robotics:** state machines, sensor integration, motor control, and building reliable real-time systems
* **JavaScript & software architecture:** ES Modules, design patterns, modular architecture, and understanding how the pieces work beneath the framework layer

---

## 📊 GitHub Activity

<div align="center">

  <p>
    <img
      width="480"
      src="https://github-stats-extended.vercel.app/api?username=mzhnk&show_icons=true&theme=dark&hide_border=false&include_all_commits=true&count_private=false&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10"
      alt="GitHub activity statistics"
    />
    <img
      width="350"
      src="https://github-readme-stats.shion.dev/api/top-langs/?username=mzhnk&layout=compact&theme=dark&hide_border=false&langs_count=8&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10"
      alt="Most used programming languages"
    />
  </p>

  <p>
    <img
      width="650"
      src="https://streak-stats.demolab.com?user=mzhnk&theme=dark&hide_border=false&background=0D1117&border=164A55&stroke=164A55&ring=00AFC2&fire=00AFC2&currStreakLabel=00AFC2&sideLabels=8B949E&currStreakNum=DDE3F0&sideNums=DDE3F0&dates=6E7890&border_radius=10"
      alt="GitHub contribution streak"
    />
  </p>

</div>

---

## 📫 Connect

<p align="center">
  <a href="https://github.com/mzhnk"><img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /></a>
  <a href="mailto:zihankholidi@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" /></a>
  <a href="https://www.linkedin.com/in/mzhnk"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="https://instagram.com/mzkx2201"><img src="https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white" /></a>
</p>

---

<p align="center">
  <i>Consistency over talent — building in public, one commit at a time.</i>
</p>
