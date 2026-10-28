# LearnHub — read, run, master

One environment to **learn programming languages and databases by reading and practicing in the same place**.
Every track is a complete curriculum (explanation → runnable example → checked exercise → interview Q&A),
and the `content/` folder is the single source of truth for all of it.

## Tracks

| Kind | Tracks | Engine in the browser |
|---|---|---|
| Languages | Python, JavaScript, TypeScript, Java | Pyodide · Web Worker · Sucrase + Worker · local JDK via `/api/execute` |
| Java frameworks | Spring Boot, Hibernate & JPA, JSP & Servlets | plain-Java mechanisms + PostgreSQL cells; real apps in `workbench/spring-lab` |
| Databases | PostgreSQL, MySQL, MongoDB, Redis | PGlite (real Postgres) · sql.js (SQLite engine, MySQL dialect notes) · mingo-backed mongosh emulator · redis-cli emulator |

## The LearnHub app (nothing to install)

Download **LearnHub Setup** and run it. The installer contains everything: the app, its server, a JDK 21, Maven
and every Maven package the Java lessons and the Spring workbench need. You install nothing else.

- **Opens like any app.** First launch copies the parts it writes to (workbench, Maven cache) into your user-data
  folder, then shows LearnHub.
- **What sets itself up on first use:** Python packages such as NumPy, pandas and FastAPI download the first time a
  lesson imports them, and Gradle downloads the first time a Gradle cell runs. Both need an internet connection
  that one time.
- **Menus:** View (Home, Roadmap, Sandbox, My notes), Tools (Start Spring workbench; Allow phone access), and
  Help (Open data folder).
- **Docker and Kubernetes:** on first launch LearnHub checks what is already installed and only fetches what is
  missing. kubectl and kind are downloaded into the data folder (no admin rights). If Docker is missing it asks,
  then installs Docker Desktop (winget on Windows, Homebrew on macOS; Linux gets the install guide). Docker
  Desktop needs administrator rights and is free for personal use, education and small businesses. Once Docker
  is running it offers to create a local `learnhub` cluster with kind. Run it again any time from
  **Tools → Set up Docker & Kubernetes**. Until then, Dockerfile cells say Docker is missing and Kubernetes YAML
  is checked offline.
- **Your data** (notes, logs, workbench copy) is in `%APPDATA%\LearnHub` on Windows,
  `~/Library/Application Support/LearnHub` on macOS and `~/.config/LearnHub` on Linux.

### On your phone

In the app choose **Tools → Allow phone access (same Wi-Fi)**. It shows an address; open it on your phone and use
**Add to Home Screen** (Safari: Share → Add to Home Screen; Chrome: ⋮ → Add to Home screen). LearnHub then opens
full screen with its own icon. Lessons, notes and the in-browser runtimes work; Java, shell, Docker and kubectl
cells stay off while phone access is on, so other devices cannot run commands on your computer. Phones treat a
plain `http://` address on your Wi-Fi as not secure, so there is no offline mode on the phone.

## Highlights and notes

Select any text in a lesson to highlight it (four colours or underline) or attach a note. Click a highlight
to edit or delete it; the **Notes** button in a lesson lists that lesson's notes, and the **Notes** page in the
top menu lists all of them with search, a colour filter and Markdown export.

Notes are saved in `notes/notes.json` through the app's `/api/notes` route, so every browser on this computer
sees the same notes and they are committed with the repo. A highlight is stored as its text plus a little
surrounding context; if a lesson is later reworded so that text no longer exists, the note is kept and listed
under "Not found in the current text".
