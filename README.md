<h1 align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=30&duration=3200&pause=900&color=58A6FF&center=true&vCenter=true&width=760&lines=Greetings%2C+I%27m+Albert+Adamyan;System+Software+Engineer+%7C+C%2FC%2B%2B;Linux+%C2%B7+Infrastructure+%C2%B7+CI%2FCD;High-performance+Linux+systems" alt="Typing SVG" />
</h1>

<p align="center">
  <a href="https://github.com/CreatorShyMoon"><img src="https://img.shields.io/badge/GitHub-CreatorShyMoon-181717?style=flat-square&logo=github" alt="GitHub"></a>
  <a href="https://gitlab.com/CreatorShyMoon"><img src="https://img.shields.io/badge/GitLab-CreatorShyMoon-FC6D26?style=flat-square&logo=gitlab" alt="GitLab"></a>
  <a href="mailto:albertadaman70@gmail.com"><img src="https://img.shields.io/badge/Email-albertadaman70%40gmail.com-EA4335?style=flat-square&logo=gmail" alt="Email"></a>
  <a href="https://t.me/moon_dsdsdsss"><img src="https://img.shields.io/badge/Telegram-%40moon__dsdsdsss-26A5E4?style=flat-square&logo=telegram" alt="Telegram"></a>
  <img src="https://hits.sh/github.com/CreatorShyMoon.svg?style=flat-square&label=Profile%20views&color=58A6FF" alt="Profile views">
</p>

---

## 🇷🇺 Русская версия

### 👨‍💻 Обо мне

Пишу системный софт на **C/C++** под Linux и строю **инфраструктуру** вокруг него:
контейнеры, CI/CD и воспроизводимые окружения. Люблю разбираться, как всё устроено
под капотом — сисколлы, ядро, сборка — а потом автоматизировать так, чтобы ничего
не делалось руками.

**Что я делаю:**

- ⚙️ **Низкоуровневая разработка на C/C++**: сокеты, `epoll`, обработка сигналов, namespaces, cgroups
- 📦 Написал **свой контейнерный рантайм**, чтобы понять, что Docker делает на уровне сисколлов
- 🔁 Любой проект оборачиваю в **полный CI/CD**: линтеры, матрица сборки (gcc/clang), статический анализ, покрытие, санитайзеры, фаззинг, упаковка
- 🐳 **Docker** для воспроизводимых dev-окружений (Linux-тулчейн на macOS)
- 🐧 **Linux** как системный администратор: процессы, systemd, сеть, LVM, права, логи, SSH, харденинг
- 📐 Документирую всё, что изучаю — архитектурные решения, README и личную базу знаний

**Ещё интересно:** PostgreSQL, Ansible, AWS, мониторинг на VictoriaMetrics + Grafana, бэкенд на Spring Boot.

### 📌 Избранные проекты

#### ⚡ [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — высокопроизводительный TCP-сервер

Однопоточный TCP-сервер на **reactor-паттерне** поверх `epoll(7)` с текстовым протоколом
(`PING`/`ECHO`/`UPPER`/`QUIT`). Неблокирующий I/O с буферизацией на каждое соединение,
`eventfd` для остановки цикла и `signalfd` для graceful shutdown. Логика протокола — чистая
функция, поэтому она покрыта unit-тестами и фаззингом без сети. Вокруг — полный GitLab CI:
линтеры, матрица gcc/clang с `-Werror`, clang-tidy + cppcheck, покрытие через gcovr,
ASan/UBSan/TSan, libFuzzer и упаковка.

`C++20` `epoll` `eventfd` `signalfd` `CMake` `GoogleTest` `libFuzzer` `Docker` `GitLab CI`

#### 📦 [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — контейнерный рантайм

Мини-рантайм контейнеров — ядро Docker примерно в 1000 строк на C++. Изоляция через
**namespaces** на `clone(2)` (PID/MNT/UTS/IPC, опционально NET), файловая система через
`pivot_root` со свежими `/proc`, `/dev` (devtmpfs) и `/sys` только для чтения, лимиты через
**cgroups v2** (`memory.max`, `pids.max`, `cpu.max`) и полный сброс **capabilities** с
`PR_SET_NO_NEW_PRIVS`. Плюс честный **PID 1**: собирает зомби и форвардит сигналы в
process-group контейнера.

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `CMake` `GoogleTest` `Docker`

#### 🖥️ [TUIOpenMath](https://github.com/CreatorShyMoon/TUIOpenMath) — менеджер открытой математической среды

Терминальный TUI на **C11** и **ncurses**, разворачивающий чистый Linux в готовую среду для
вычислений: **7 встроенных профилей**, изолированные Python-venv, Julia LTS/Stable, JupyterLab
в отдельном runtime и зарегистрированные Jupyter-ядра Python, Julia, Bash, Octave и Scilab.

Установки идут асинхронно через `fork` / `pipe` / `waitpid` и построчно стримятся в живую
log-панель; диагностика проверяет только компоненты активного профиля. Управление — полностью
с клавиатуры, без графики, работает по SSH.

`C11` `ncurses` `JupyterLab` `Julia` `Python venv` `Jupyter kernels` `cJSON` `MIT`

#### 🔢 [machine-translation](https://github.com/CreatorShyMoon/machine-translation) — генератор заданий

Приложение на **C**, которое генерирует индивидуальные задания по теме машинного
представления вещественных чисел — упражнение на IEEE 754, битовые операции и аккуратный ввод-вывод.

`C` `IEEE 754`

#### 🧮 [MatrixLibMultiply3](https://github.com/CreatorShyMoon/MatrixLibMultiply3) — быстрое умножение матриц

Библиотека на **C++** для быстрого умножения матриц любого размера: алгоритмы с учётом
кэша вместо наивного тройного цикла.

`C++` `алгоритмы` `производительность`

#### ♟️ [GameTurn-BasedCombat](https://github.com/CreatorShyMoon/GameTurn-BasedCombat) — пошаговая RPG

Консольная пошаговая RPG на карте 15×15 на **C++**, построенная на паттернах
**«Стратегия»** и **«Фабрика»** для действий персонажа (атака, огненный шар, блок).

`C++` `ООП` `паттерны проектирования`

#### ☕ [todo-api](https://github.com/CreatorShyMoon/todo-api) — REST API для задач

REST API на **Java 21** и **Spring Boot 3.4**: **Spring Security + JWT**, Spring Data JPA /
Hibernate, PostgreSQL в проде и in-memory H2 в dev-профиле — запускается без инфраструктуры
одной командой. Покрыт тестами на **JUnit 5 + Mockito**, поднимается через Docker Compose
и отдаёт собственный статический веб-клиент прямо со Spring.

`Java 21` `Spring Boot` `Spring Security` `JWT` `JPA/Hibernate` `PostgreSQL` `H2` `JUnit 5` `Docker Compose`

### 🤝 Контакты

- 📧 **Почта**: [albertadaman70@gmail.com](mailto:albertadaman70@gmail.com)
- 💬 **Telegram**: [@moon_dsdsdsss](https://t.me/moon_dsdsdsss)
- 🐙 **GitHub**: [CreatorShyMoon](https://github.com/CreatorShyMoon)
- 🦊 **GitLab**: [CreatorShyMoon](https://gitlab.com/CreatorShyMoon)

---

## 🛠️ Tech Stack

### Languages

![C](https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

### Linux & Systems

![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![POSIX](https://img.shields.io/badge/POSIX%20syscalls-333333?style=flat-square&logo=linux&logoColor=white)
![epoll](https://img.shields.io/badge/epoll%20%2F%20reactor-4B8BBE?style=flat-square&logo=linux&logoColor=white)
![Namespaces](https://img.shields.io/badge/namespaces%20%2B%20cgroups-2496ED?style=flat-square&logo=linux&logoColor=white)
![CMake](https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white)
![Ninja](https://img.shields.io/badge/Ninja-000000?style=flat-square&logo=ninja&logoColor=white)
![GCC](https://img.shields.io/badge/GCC%20%2F%20Clang-A42E2B?style=flat-square&logo=llvm&logoColor=white)

### DevOps & Infrastructure

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitLab CI](https://img.shields.io/badge/GitLab%20CI-FC6D26?style=flat-square&logo=gitlab&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat-square&logo=ansible&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana%20%2F%20VictoriaMetrics-F46800?style=flat-square&logo=grafana&logoColor=white)

### Testing & Quality

![GoogleTest](https://img.shields.io/badge/GoogleTest-4285F4?style=flat-square&logo=google&logoColor=white)
![Sanitizers](https://img.shields.io/badge/ASan%20%2F%20UBSan%20%2F%20TSan-CC342D?style=flat-square&logo=llvm&logoColor=white)
![libFuzzer](https://img.shields.io/badge/libFuzzer-8A2BE2?style=flat-square&logo=llvm&logoColor=white)
![gcovr](https://img.shields.io/badge/gcovr%20coverage-2F9E44?style=flat-square&logo=gnu&logoColor=white)
![clang-tidy](https://img.shields.io/badge/clang--tidy%20%2F%20cppcheck-1F6FEB?style=flat-square&logo=llvm&logoColor=white)

---

## 🇬🇧 English version

### 👨‍💻 About Me

I write systems software in **C/C++** for Linux and build the **infrastructure** around it:
containers, CI/CD pipelines and reproducible environments. I like understanding how things
work under the hood — syscalls, the kernel, the build system — and then automating them
so nothing depends on manual steps.

**What I do:**

- ⚙️ Build **low-level Linux software** in C/C++ — sockets, `epoll`, signal handling, namespaces, cgroups
- 📦 Write my own **container runtime** to understand what Docker actually does at the syscall level
- 🔁 Wrap every project in a **full CI/CD pipeline** — lint, build matrix (gcc/clang), static analysis, coverage, sanitizers, fuzzing, packaging
- 🐳 Use **Docker** for reproducible dev environments (Linux toolchain on a macOS host)
- 🐧 Administer **Linux** as a sysadmin: processes, systemd, networking, LVM, permissions, logs, SSH, hardening
- 📐 Document what I learn — architecture decisions, READMEs and a personal knowledge base

**Also interested in:** PostgreSQL, Ansible, AWS, monitoring with VictoriaMetrics + Grafana, backend services on Spring Boot.

### 📌 Featured Projects

#### ⚡ [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — high-performance TCP server

Single-threaded TCP server built on the **reactor pattern** over `epoll(7)` with a text
protocol (`PING`/`ECHO`/`UPPER`/`QUIT`). Non-blocking I/O with per-connection buffering,
`eventfd` for loop wakeup and `signalfd` for graceful shutdown. Protocol logic is a pure
function, so it is unit-tested and fuzzed without touching the network. Wrapped in a full
GitLab CI pipeline: linting, gcc/clang matrix with `-Werror`, clang-tidy + cppcheck, gcovr
coverage, ASan/UBSan/TSan, libFuzzer and packaging.

`C++20` `epoll` `eventfd` `signalfd` `CMake` `GoogleTest` `libFuzzer` `Docker` `GitLab CI`

#### 📦 [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — container runtime

A tiny container runtime — the core of Docker in about 1k lines of C++. Isolation via
`clone(2)` **namespaces** (PID/MNT/UTS/IPC, optional NET), filesystem view via `pivot_root`
with a fresh `/proc`, `/dev` (devtmpfs) and read-only `/sys`, resource limits via
**cgroups v2** (`memory.max`, `pids.max`, `cpu.max`) and full **capability** dropping with
`PR_SET_NO_NEW_PRIVS`. Plus it behaves as a proper **PID 1**: it reaps zombies and forwards
signals to the container's process group.

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `CMake` `GoogleTest` `Docker`

#### 🖥️ [TUIOpenMath](https://github.com/CreatorShyMoon/TUIOpenMath) — open math environment manager

A terminal TUI in **C11** + **ncurses** that turns a bare Linux machine into a ready-to-use
computational environment: **7 built-in profiles**, isolated Python venvs, Julia LTS/Stable,
JupyterLab in a dedicated runtime, and registered Jupyter kernels for Python, Julia, Bash,
Octave and Scilab.

Long installs run asynchronously via `fork` / `pipe` / `waitpid` and stream line by line into a
live log panel; diagnostics check only the active profile's components. Everything is driven
from the keyboard — no GUI, works over SSH.

`C11` `ncurses` `JupyterLab` `Julia` `Python venv` `Jupyter kernels` `cJSON` `MIT`

#### 🔢 [machine-translation](https://github.com/CreatorShyMoon/machine-translation) — floating-point task generator

A **C** application generating individual assignments on machine representation of
floating-point numbers — an exercise in IEEE 754, bit tricks and correct I/O.

`C` `IEEE 754`

#### 🧮 [MatrixLibMultiply3](https://github.com/CreatorShyMoon/MatrixLibMultiply3) — fast matrix multiplication

A **C++** library for fast multiplication of matrices of any size, using cache-aware
algorithms instead of a naive triple loop.

`C++` `algorithms` `performance`

#### ♟️ [GameTurn-BasedCombat](https://github.com/CreatorShyMoon/GameTurn-BasedCombat) — turn-based RPG

Console turn-based RPG on a 15×15 map in **C++**, built around the **Strategy** and
**Factory** design patterns for character actions (attack, fireball, block).

`C++` `OOP` `design patterns`

#### ☕ [todo-api](https://github.com/CreatorShyMoon/todo-api) — task REST API

REST API on **Java 21** and **Spring Boot 3.4**: **Spring Security + JWT**, Spring Data JPA /
Hibernate, PostgreSQL in production and in-memory H2 behind a dev profile — boots with zero
infrastructure in a single command. Covered by **JUnit 5 + Mockito** tests, starts via Docker
Compose, and ships its own static web client served straight by Spring.

`Java 21` `Spring Boot` `Spring Security` `JWT` `JPA/Hibernate` `PostgreSQL` `H2` `JUnit 5` `Docker Compose`

### 🤝 Let's Connect

Open to collaboration, freelance and full-time opportunities around **Linux systems,
C/C++ development and DevOps/CI-CD engineering**. I write documented code and ship
complete, reproducible projects.

- 📧 **Email**: [albertadaman70@gmail.com](mailto:albertadaman70@gmail.com)
- 💬 **Telegram**: [@moon_dsdsdsss](https://t.me/moon_dsdsdsss)
- 🐙 **GitHub**: You're already here!

---

## 📊 GitHub Stats

<p align="center">
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=CreatorShyMoon&show_icons=true&theme=github_dark&hide_border=true&count_private=true&include_all_commits=true" alt="GitHub stats">
  <img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=CreatorShyMoon&layout=compact&theme=github_dark&hide_border=true&langs_count=8&exclude_repo=CreatorShyMoon" alt="Top languages">
</p>

---

*«Getting code from AI doesn't mean you understand it.»*
