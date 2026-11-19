<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0F6675&height=120&section=header&reversal=true&animation=fadeIn" alt="" />

<p align="center">
  <a href="https://github.com/mzhnk">
    <img src="https://wsrv.nl/?url=https://github.com/mzhnk.png&w=280&h=280&fit=cover&mask=circle" width="130" alt="mzhnk profile photo" />
  </a>
</p>

<h2 align="center">mzhnk</h2>

<p align="center">
  <sub><b>Software that has to keep working in the real world</b></sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Student_Developer-Indonesia-0F6675?style=flat-square" alt="Student developer, Indonesia" />
  <img src="https://img.shields.io/badge/Focus-AI_·_Web_·_Embedded_·_Robotics-0F6675?style=flat-square" alt="Focus: AI, web, embedded, robotics" />
  <img src="https://img.shields.io/badge/Mode-Building_in_public-0F6675?style=flat-square" alt="Building in public" />
  <img src="https://img.shields.io/github/followers/mzhnk?style=flat-square&label=Followers&color=0F6675" alt="GitHub followers" />
  <img src="https://komarev.com/ghpvc/?username=mzhnk&color=0F6675&style=flat-square&label=Views" alt="Profile views" />
</p>

<p align="center">
  <a href="#about">About</a> ·
  <a href="#projects">Projects</a> ·
  <a href="#stack">Stack</a> ·
  <a href="#exploring">Exploring</a> ·
  <a href="#activity">Activity</a> ·
  <a href="#connect">Connect</a>
</p>

---

<a id="about"></a>
## About

I'm a student developer from Indonesia. Most of what I know comes from building real projects rather than following tutorials, usually at the point where software meets hardware and has to behave predictably in real time.

What I care about beyond "it works": how state is shared, how failures are handled, and what makes a system reliable enough to trust. I document the process as I go, because the failures teach more than the wins.

> [!NOTE]
> **Building in public.** Everything below is work in progress. I write down what broke as well as what worked.

```yaml
whoami:
  handle: mzhnk
  from: Indonesia
  role: student developer
  interests: [AI, web, embedded systems, robotics]
  building_now:
    - AI Pet Robot (V2, "Make It Aware")
    - 3D Periodic Table
  learning: [TypeScript, React, Next.js, Tailwind, PostgreSQL, Prisma, shadcn/ui, Zod]
  principle: "Failures teach more than wins. Document both."
```

---

<a id="projects"></a>
## Projects

### 🤖 AI Pet Robot · V2 "Make It Aware"

A desktop pet robot: an **ESP32 body** and a **Flask "Local AI" brain** talking over WebSocket. It's my way of learning embedded systems and sensor fusion by building something physical that has to keep working, not just something that compiles.

```mermaid
flowchart LR
    subgraph S["Perception"]
        CAM["ESP32-CAM<br/>person zoning L / C / R"]
        US["HC-SR04<br/>obstacle distance"]
        IMU["MPU-6050<br/>fall / tilt"]
    end

    CAM --> WS
    US --> WS
    IMU --> WS
    WS(["WorldState<br/>shared fusion"]) --> FSM{{"13-state<br/>behavior FSM"}}
    FSM --> OUT["Motors · LEDs · Sound"]

    AI["Flask Local AI<br/>WebSocket, offline-capable"] <-.-> FSM

    SAFE["Deterministic safety on ESP32<br/>avoidance · fall recovery"] -. overrides .-> FSM

    classDef core fill:#0F6675,stroke:#00AFC2,color:#E6F7FA;
    classDef safe fill:#7a2e2e,stroke:#e06c6c,color:#fff;
    class WS,FSM core;
    class SAFE safe;
```

> [!IMPORTANT]
> **Safety is never delegated to the AI.** Obstacle avoidance and fall recovery are resolved deterministically on the ESP32. The Flask brain can suggest behavior, but it cannot override these decisions.

| Layer | What it does |
|:--|:--|
| **Perception** | Camera buckets people into left / center / right, ultrasonic measures obstacle distance, IMU catches falls and tilts |
| **Fusion** | All three sensor streams feed one shared `WorldState` |
| **Decision** | A 13-state FSM (curious → follow → interact → avoid → recover …) turns state into behavior |
| **Safety** | Obstacle avoidance and fall recovery are resolved deterministically **on the ESP32**, so the AI layer can never override them |
| **Resilience** | Base behaviors keep running if WiFi or the AI backend drops |

> [!WARNING]
> **Actively developed.** The V2 protocol is additive and still evolving, so expect changes between commits.

<details>
<summary><b>Version history: V1 → V2</b></summary>
<br>

| Version | Theme | Capabilities |
|:--|:--|:--|
| V1 | *Make It Alive* | Move, turn, react to touch |
| V2 | *Make It Aware* | See, sense distance, detect falls, decide |

</details>

<table>
  <tr>
    <td><b>Status</b></td>
    <td>Actively developed · additive V2 protocol · September 2026</td>
  </tr>
  <tr>
    <td><b>Verification</b></td>
    <td>
      <img src="https://img.shields.io/badge/Total-206_tests-0F6675?style=flat-square" alt="206 tests" />
      <img src="https://img.shields.io/badge/Native-134-164A55?style=flat-square" alt="134 native tests" />
      <img src="https://img.shields.io/badge/pytest-51-164A55?style=flat-square" alt="51 pytest tests" />
      <img src="https://img.shields.io/badge/E2E-21-164A55?style=flat-square" alt="21 end-to-end tests" />
    </td>
  </tr>
  <tr>
    <td><b>Stack</b></td>
    <td><code>C++</code> <code>ESP32</code> <code>WebSocket</code> <code>Flask</code></td>
  </tr>
  <tr>
    <td><b>Repo</b></td>
    <td><a href="https://github.com/mzhnk/ai-pet-robot">github.com/mzhnk/ai-pet-robot</a></td>
  </tr>
</table>

<p align="center">
  <a href="https://github.com/mzhnk/ai-pet-robot">
    <img src="https://github-stats-extended.vercel.app/api/pin/?username=mzhnk&repo=ai-pet-robot&theme=dark&hide_border=false&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10" alt="ai-pet-robot repository card" />
  </a>
  <br>
  <img src="https://img.shields.io/github/last-commit/mzhnk/ai-pet-robot?style=flat-square&label=Last+commit&color=0F6675" alt="ai-pet-robot last commit" />
  <img src="https://img.shields.io/github/languages/top/mzhnk/ai-pet-robot?style=flat-square&color=0F6675" alt="ai-pet-robot top language" />
</p>

<br>

### 🧪 3D Periodic Table

An interactive 3D visualization of all **118 elements** with four swappable layouts, smooth Anime.js transitions, and mouse, touch and long-press interaction, in English and Indonesian.

| Layouts | Interaction | Languages |
|:--:|:--:|:--:|
| Table · Sphere · Helix · Grid | Mouse · Touch · Long-press | EN · ID |

> [!NOTE]
> **Zero behavior change.** The refactor from a single 690-line `index.html` to 20 ES Modules was structural only.

**The refactor:** one 690-line `index.html` became 20 ES Module files, with zero behavior change.

```text
Before                          After
──────                          ─────
index.html  (690 lines)   ──▶   20 ES Modules
                                no bundler · no framework
                                i18n built into the component structure
```

- Pure CSS 3D transforms drive all four layout modes
- Modular ES Module architecture, nothing between the code and the browser
- Bilingual UI designed in from the start, not bolted on

<table>
  <tr>
    <td><b>Status</b></td>
    <td>Refactor shipped · September 2026</td>
  </tr>
  <tr>
    <td><b>Stack</b></td>
    <td><code>JavaScript</code> <code>ES Modules</code> <code>CSS3</code> <code>Anime.js</code></td>
  </tr>
  <tr>
    <td><b>Repo</b></td>
    <td><a href="https://github.com/mzhnk/periodic-table">github.com/mzhnk/periodic-table</a></td>
  </tr>
</table>

<p align="center">
  <a href="https://github.com/mzhnk/periodic-table">
    <img src="https://github-stats-extended.vercel.app/api/pin/?username=mzhnk&repo=periodic-table&theme=dark&hide_border=false&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10" alt="periodic-table repository card" />
  </a>
  <br>
  <img src="https://img.shields.io/github/last-commit/mzhnk/periodic-table?style=flat-square&label=Last+commit&color=0F6675" alt="periodic-table last commit" />
  <img src="https://img.shields.io/github/languages/top/mzhnk/periodic-table?style=flat-square&color=0F6675" alt="periodic-table top language" />
</p>

---

<a id="stack"></a>
## Stack

> [!TIP]
> The left column is what I have **shipped** in real projects. The right column is what I am **still learning**.

<table>
  <tr>
    <th align="left" width="160">Domain</th>
    <th align="left">Shipped in real projects</th>
    <th align="left">Learning</th>
  </tr>
  <tr>
    <td><b>Languages</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=py,js,cpp,html,css&theme=dark" alt="Python, JavaScript, C++, HTML, CSS" />
    </td>
    <td>
      <img src="https://skillicons.dev/icons?i=ts&theme=dark" alt="TypeScript" />
    </td>
  </tr>
  <tr>
    <td><b>Frontend</b></td>
    <td>
      <img src="https://img.shields.io/badge/Anime.js-0D1117?style=flat-square" alt="Anime.js" />
      <img src="https://img.shields.io/badge/ES_Modules-F7DF1E?style=flat-square&logo=javascript&logoColor=black" alt="ES Modules" />
    </td>
    <td>
      <img src="https://skillicons.dev/icons?i=react,nextjs,tailwind&theme=dark" alt="React, Next.js, Tailwind CSS" />
      <img src="https://img.shields.io/badge/shadcn%2Fui-000000?style=flat-square&logo=shadcnui&logoColor=white" alt="shadcn/ui" />
      <img src="https://img.shields.io/badge/Zod-3E67B1?style=flat-square&logo=zod&logoColor=white" alt="Zod" />
    </td>
  </tr>
  <tr>
    <td><b>Backend &amp; Data</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=flask,sqlite&theme=dark" alt="Flask, SQLite" />
      <img src="https://img.shields.io/badge/WebSocket-0D1117?style=flat-square" alt="WebSocket" />
    </td>
    <td>
      <img src="https://skillicons.dev/icons?i=postgres,prisma&theme=dark" alt="PostgreSQL, Prisma" />
    </td>
  </tr>
  <tr>
    <td><b>Embedded</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=arduino&theme=dark" alt="Arduino" />
      <img src="https://img.shields.io/badge/ESP32-E7352C?style=flat-square&logo=espressif&logoColor=white" alt="ESP32" />
      <br>
      <sub>ESP32-CAM · HC-SR04 · MPU-6050</sub>
    </td>
    <td><sub>Motor control, deeper sensor fusion</sub></td>
  </tr>
  <tr>
    <td><b>Testing &amp; Tooling</b></td>
    <td>
      <img src="https://skillicons.dev/icons?i=git,github,githubactions,vitest,playwright&theme=dark" alt="Git, GitHub, GitHub Actions, Vitest, Playwright" />
      <img src="https://img.shields.io/badge/pytest-0A101F?style=flat-square&logo=pytest&logoColor=white" alt="pytest" />
    </td>
    <td><sub>Type-safe application patterns</sub></td>
  </tr>
</table>

---

<a id="exploring"></a>
## Currently Exploring

> [!IMPORTANT]
> **Current priority:** moving from plain JavaScript toward the TypeScript and Next.js ecosystem, while keeping the embedded work going in parallel.

| Track | Focus | Why it matters to me |
|:--|:--|:--|
| **Modern web** | TypeScript, React, Next.js App Router, server actions, type-safe patterns | Moving from "it runs" to "the compiler catches my mistakes" |
| **Embedded & robotics** | State machines, sensor integration, motor control, real-time reliability | Physical systems punish sloppy assumptions |
| **Architecture** | ES Modules, design patterns, how the pieces fit beneath the framework | Frameworks change; structure carries over |

---

<a id="activity"></a>
## Activity

<p align="center">
  <img height="170" src="https://github-stats-extended.vercel.app/api?username=mzhnk&show_icons=true&theme=dark&hide_border=false&include_all_commits=true&count_private=false&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10" alt="GitHub stats" />
  <picture>
    <source media="(max-width: 480px)" srcset="https://github-readme-stats.shion.dev/api/top-langs/?username=mzhnk&layout=compact&theme=dark&hide_border=false&langs_count=5&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10" />
    <img height="170" src="https://github-readme-stats.shion.dev/api/top-langs/?username=mzhnk&layout=compact&theme=dark&hide_border=false&langs_count=8&title_color=00AFC2&text_color=8B949E&icon_color=00AFC2&bg_color=0D1117&border_color=164A55&border_radius=10" alt="Most used languages" />
  </picture>
</p>

<p align="center">
  <img src="https://streak-stats.demolab.com?user=mzhnk&theme=dark&hide_border=false&background=0D1117&border=164A55&stroke=164A55&ring=00AFC2&fire=00AFC2&currStreakLabel=00AFC2&sideLabels=8B949E&currStreakNum=DDE3F0&sideNums=DDE3F0&dates=6E7890&border_radius=10" alt="Contribution streak" />
</p>

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=mzhnk&bg_color=0D1117&color=8B949E&line=00AFC2&point=E6F7FA&area=true&area_color=0F6675&hide_border=true&radius=10" alt="Contribution activity graph" />
</p>

---

<a id="connect"></a>
## Connect

> [!TIP]
> Happy to talk about embedded systems, robotics, or web architecture. Email is the best way to reach me.

<p align="center">
  <a href="https://github.com/mzhnk"><img src="https://img.shields.io/badge/GitHub-mzhnk-0F6675?style=for-the-badge&logo=github&logoColor=E6F7FA" alt="GitHub" /></a>
  <a href="mailto:zihankholidi@gmail.com"><img src="https://img.shields.io/badge/Email-Say_hello-0F6675?style=for-the-badge&logo=gmail&logoColor=E6F7FA" alt="Email" /></a>
  <a href="https://www.linkedin.com/in/mzhnk"><img src="https://img.shields.io/badge/LinkedIn-mzhnk-0F6675?style=for-the-badge" alt="LinkedIn" /></a>
  <a href="https://instagram.com/mzkx2201"><img src="https://img.shields.io/badge/Instagram-mzkx2201-0F6675?style=for-the-badge&logo=instagram&logoColor=E6F7FA" alt="Instagram" /></a>
</p>

---

<p align="center">
  <i>Consistency over talent, building in public, one commit at a time.</i><br>
  <sub>재능보다 꾸준함, 한 번에 한 커밋씩.</sub>
</p>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0F6675&height=120&section=footer&animation=fadeIn" alt="" />
