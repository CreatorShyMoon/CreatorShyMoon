# Albert Adamyan

```text
albert@linux:~$ whoami
Albert Adamyan

albert@linux:~$ cat /etc/focus
Linux internals · C/C++ · Air-Gapped infra · containers · CI/CD

albert@linux:~$ uptime
building reliable systems since 2024
```

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
контейнеры, автономные (Air-Gapped) репозитории, CI/CD и воспроизводимые окружения. Люблю разбираться, как всё устроено под капотом — сисколлы, ядро, сборка — а потом автоматизировать так, чтобы ничего не делалось руками.

**Что я делаю:**

- ⚙️ **Низкоуровневая разработка на C/C++**: сокеты, `epoll`, обработка сигналов (`signalfd`), IPC (`fork`/`exec`/`pipe`), `ioctl`, namespaces, cgroups v2
- 📦 Написал **свой контейнерный рантайм**, чтобы понять, что Docker делает на уровне сисколлов
- 🌐 Проектирую **автономную (Air-Gapped) инфраструктуру**: собственный PEP 503 PyPI-сервер, зеркалирование бинарных артефактов и упаковка офлайн-монолитов
- 🔁 Любой проект оборачиваю в **полный CI/CD**: линтеры, матрица сборки (gcc/clang), статический анализ, покрытие, санитайзеры, фаззинг, упаковка
- 🐳 **Docker** для воспроизводимых dev-окружений (Linux-тулчейн на macOS)
- 🐧 **Linux** как системный администратор: процессы, systemd, сеть, LVM, права, логи, SSH, харденинг
- 📐 Документирую всё, что изучаю — архитектурные решения, README и личную базу знаний

**Ещё интересно:** PostgreSQL, Ansible, AWS, мониторинг на VictoriaMetrics + Grafana, скриптинг игровой и сетевой логики (SQF / Arma 3), бэкенд на Spring Boot.

### 📌 Избранные проекты

#### ⚡ [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — высокопроизводительный TCP-сервер

TCP-сервер в одном потоке на `epoll(7)`: тысячи соединений, текстовый протокол
`PING`/`ECHO`/`UPPER`/`QUIT`. Реализация — reactor-паттерн и неблокирующий I/O (`eventfd`,
`signalfd`), логика протокола вынесена в чистую функцию и покрыта тестами и фаззингом.
GitLab CI: линтеры, матрица gcc/clang, санитайзеры, покрытие, libFuzzer.

`C++20` `epoll` `eventfd` `signalfd` `CMake` `GoogleTest` `libFuzzer` `Docker` `GitLab CI`

#### 📦 [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — контейнерный рантайм

Запускает процесс в изолированном окружении — как Docker, но в миниатюре (~1000 строк C++).
Изоляция — namespaces через `clone(2)` и `pivot_root`, лимиты — cgroups v2, плюс сброс
capabilities и PID 1, который собирает зомби и пробрасывает сигналы.

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `CMake` `GoogleTest` `Docker`

#### 🖥️ [TUIOpenMath_Server (SysOpenMath)](https://github.com/CreatorShyMoon/TUIOpenMath_Server) — автономная (Air-Gapped) платформа научных сред

Клиент-серверная система развёртывания вычислительных окружений (Python, Julia LTS, JupyterLab, Octave, Scilab) на машинах без интернета.
- **TUI-клиент на C11/ncursesw**: асинхронный раннер процессов (`fork`/`exec`/`pipe`), защита от шторма `KEY_RESIZE` через `ioctl(TIOCGWINSZ)`, атомарные инсталляторы на `mkstemp` с `trap EXIT`.
- **Локальный сервер на FastAPI**: собственный **PEP 503 PyPI-индекс** (`/simple/`), раздача 120+ `.whl` и портативных сборок со встроенной JRE, двухфазная загрузка с проверкой `SHA-256`, сборка единого офлайн-бандла (`make bundle`).

`C11` `POSIX` `ncursesw` `ioctl` `FastAPI` `PEP 503 PyPI` `Air-Gapped` `JupyterLab` `Julia` `cJSON`

#### ☕ [todo-api](https://github.com/CreatorShyMoon/todo-api) — REST API для задач

REST API для задач с JWT-аутентификацией. Spring Security + JPA/Hibernate, PostgreSQL в
проде и H2 в dev (старт одной командой), тесты JUnit 5 + Mockito, запуск через Docker Compose.

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
![ncurses](https://img.shields.io/badge/ncursesw%20TUI-2E3440?style=flat-square&logo=gnu-bash&logoColor=white)
![CMake](https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white)
![Ninja](https://img.shields.io/badge/Ninja-000000?style=flat-square&logo=ninja&logoColor=white)
![GCC](https://img.shields.io/badge/GCC%20%2F%20Clang-A42E2B?style=flat-square&logo=llvm&logoColor=white)

### DevOps & Infrastructure

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitLab CI](https://img.shields.io/badge/GitLab%20CI-FC6D26?style=flat-square&logo=gitlab&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI%20%2F%20PEP%20503-009688?style=flat-square&logo=fastapi&logoColor=white)
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
containers, air-gapped artifact repositories, CI/CD pipelines and reproducible environments. I like understanding how things work under the hood — syscalls, the kernel, the build system — and then automating them so nothing depends on manual steps.

**What I do:**

- ⚙️ Build **low-level Linux software** in C/C++ — sockets, `epoll`, signal handling (`signalfd`), IPC (`fork`/`exec`/`pipe`), `ioctl`, namespaces, cgroups v2
- 📦 Write my own **container runtime** to understand what Docker actually does at the syscall level
- 🌐 Design **Air-Gapped infrastructure** — self-hosted PEP 503 PyPI index, binary artifact mirroring and offline monolith bundling
- 🔁 Wrap every project in a **full CI/CD pipeline** — lint, build matrix (gcc/clang), static analysis, coverage, sanitizers, fuzzing, packaging
- 🐳 Use **Docker** for reproducible dev environments (Linux toolchain on a macOS host)
- 🐧 Administer **Linux** as a sysadmin: processes, systemd, networking, LVM, permissions, logs, SSH, hardening
- 📐 Document what I learn — architecture decisions, READMEs and a personal knowledge base

**Also interested in:** PostgreSQL, Ansible, AWS, monitoring with VictoriaMetrics + Grafana, game/network scripting (SQF / Arma 3), backend services on Spring Boot.

### 📌 Featured Projects

#### ⚡ [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — high-performance TCP server

Single-threaded TCP server on `epoll(7)`: thousands of connections over the text protocol
`PING`/`ECHO`/`UPPER`/`QUIT`. Reactor pattern with non-blocking I/O (`eventfd`, `signalfd`);
protocol logic is a pure function covered by unit tests and fuzzing. GitLab CI: lint,
gcc/clang matrix, sanitizers, coverage, libFuzzer.

`C++20` `epoll` `eventfd` `signalfd` `CMake` `GoogleTest` `libFuzzer` `Docker` `GitLab CI`

#### 📦 [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — container runtime

Runs a process in an isolated environment — what Docker does, in miniature (~1k lines of
C++). Namespaces via `clone(2)` and `pivot_root` for the filesystem, cgroups v2 limits,
capability dropping, plus PID 1 semantics: zombie reaping and signal forwarding.

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `CMake` `GoogleTest` `Docker`

#### 🖥️ [TUIOpenMath_Server (SysOpenMath)](https://github.com/CreatorShyMoon/TUIOpenMath_Server) — air-gapped math environment platform

Client-server provisioning platform that deploys scientific environments (Python, Julia LTS, JupyterLab, Octave, Scilab) on completely offline (air-gapped) Linux machines:
- **System TUI Client (`C11` / `ncursesw`)**: async process runner (`fork`/`exec`/`pipe`), flicker-free resize handling via `ioctl(TIOCGWINSZ)`, and atomic script execution using `mkstemp` + `trap EXIT`.
- **Self-Hosted Artifact Server (`FastAPI`)**: local **PEP 503 PyPI repository** (`/simple/`) serving 120+ wheels and portable toolchains with `SHA-256` verification, Read-Only REST API isolation, and single-archive offline bundling (`make bundle`).

`C11` `POSIX` `ncursesw` `ioctl` `FastAPI` `PEP 503 PyPI` `Air-Gapped` `JupyterLab` `Julia` `cJSON`

#### ☕ [todo-api](https://github.com/CreatorShyMoon/todo-api) — task REST API

Task REST API with JWT auth. Spring Security + JPA/Hibernate, PostgreSQL in prod, H2 in dev
(single-command start), JUnit 5 + Mockito tests, Docker Compose.

`Java 21` `Spring Boot` `Spring Security` `JWT` `JPA/Hibernate` `PostgreSQL` `H2` `JUnit 5` `Docker Compose`

### 🤝 Let's Connect

- 📧 **Email**: [albertadaman70@gmail.com](mailto:albertadaman70@gmail.com)
- 💬 **Telegram**: [@moon_dsdsdsss](https://t.me/moon_dsdsdsss)
- 🐙 **GitHub**: You're already here!
