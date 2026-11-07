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
контейнеры, автономные (Air-Gapped) репозитории, CI/CD и воспроизводимые окружения[span_0](start_span)[span_0](end_span)[span_1](start_span)[span_1](end_span)[span_2](start_span)[span_2](end_span). Люблю разбираться, как всё устроено под капотом — сисколлы, ядро, сборка — а потом автоматизировать так, чтобы ничего не делалось руками.

**Что я делаю:**

- ⚙️ **Низкоуровневая разработка на C/C++**: сокеты, `epoll`, обработка сигналов (`signalfd`), IPC (`fork`/`exec`/`pipe`), `ioctl`, namespaces, cgroups v2[span_3](start_span)[span_3](end_span)[span_4](start_span)[span_4](end_span)[span_5](start_span)[span_5](end_span)
- 📦 Написал **свой контейнерный рантайм**, чтобы понять, что Docker делает на уровне сисколлов[span_6](start_span)[span_6](end_span)
- 🌐 Проектирую **автономную (Air-Gapped) инфраструктуру**: собственный PEP 503 PyPI-сервер, зеркалирование бинарных артефактов и упаковка офлайн-монолитов[span_7](start_span)[span_7](end_span)
- 🔁 Любой проект оборачиваю в **полный CI/CD**: линтеры, матрица сборки (gcc/clang), статический анализ, покрытие, санитайзеры, фаззинг, упаковка[span_8](start_span)[span_8](end_span)
- 🐳 **Docker** для воспроизводимых dev-окружений (Linux-тулчейн на macOS)[span_9](start_span)[span_9](end_span)
- 🐧 **Linux** как системный администратор: процессы, systemd, сеть, LVM, права, логи, SSH, харденинг[span_10](start_span)[span_10](end_span)[span_11](start_span)[span_11](end_span)
- 📐 Документирую всё, что изучаю — архитектурные решения, README и личную базу знаний

**Ещё интересно:** PostgreSQL, Ansible, AWS, мониторинг на VictoriaMetrics + Grafana, скриптинг игровой и сетевой логики (SQF / Arma 3), бэкенд на Spring Boot[span_12](start_span)[span_12](end_span).

### 📌 Избранные проекты

#### ⚡ [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — высокопроизводительный TCP-сервер

TCP-сервер в одном потоке на `epoll(7)`: тысячи соединений, текстовый протокол
`PING`/`ECHO`/`UPPER`/`QUIT`[span_13](start_span)[span_13](end_span). Реализация — reactor-паттерн и неблокирующий I/O (`eventfd`,
`signalfd`), логика протокола вынесена в чистую функцию и покрыта тестами и фаззингом[span_14](start_span)[span_14](end_span).
GitLab CI: линтеры, матрица gcc/clang, санитайзеры, покрытие, libFuzzer[span_15](start_span)[span_15](end_span)[span_16](start_span)[span_16](end_span).

`C++20` `epoll` `eventfd` `signalfd` `CMake` `GoogleTest` `libFuzzer` `Docker` `GitLab CI`[span_17](start_span)[span_17](end_span)[span_18](start_span)[span_18](end_span)

#### 📦 [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — контейнерный рантайм

Запускает процесс в изолированном окружении — как Docker, но в миниатюре (~1000 строк C++)[span_19](start_span)[span_19](end_span).
Изоляция — namespaces через `clone(2)` и `pivot_root`, лимиты — cgroups v2, плюс сброс
capabilities и PID 1, который собирает зомби и пробрасывает сигналы[span_20](start_span)[span_20](end_span).

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `CMake` `GoogleTest` `Docker`[span_21](start_span)[span_21](end_span)[span_22](start_span)[span_22](end_span)

#### 🖥️ [TUIOpenMath_Server (SysOpenMath)](https://github.com/CreatorShyMoon/TUIOpenMath_Server) — автономная (Air-Gapped) платформа научных сред

Клиент-серверная система развёртывания вычислительных окружений (Python, Julia LTS, JupyterLab, Octave, Scilab) на машинах без интернета[span_23](start_span)[span_23](end_span).
- **TUI-клиент на C11/ncursesw**: асинхронный раннер процессов (`fork`/`exec`/`pipe`), защита от шторма `KEY_RESIZE` через `ioctl(TIOCGWINSZ)`, атомарные инсталляторы на `mkstemp` с `trap EXIT`[span_24](start_span)[span_24](end_span).
- **Локальный сервер на FastAPI**: собственный **PEP 503 PyPI-индекс** (`/simple/`), раздача 120+ `.whl` и портативных сборок со встроенной JRE, двухфазная загрузка с проверкой `SHA-256`, сборка единого офлайн-бандла (`make bundle`)[span_25](start_span)[span_25](end_span).

`C11` `POSIX` `ncursesw` `ioctl` `FastAPI` `PEP 503 PyPI` `Air-Gapped` `JupyterLab` `Julia` `cJSON`[span_26](start_span)[span_26](end_span)[span_27](start_span)[span_27](end_span)

#### ☕ [todo-api](https://github.com/CreatorShyMoon/todo-api) — REST API для задач

REST API для задач с JWT-аутентификацией[span_28](start_span)[span_28](end_span). Spring Security + JPA/Hibernate, PostgreSQL в
проде и H2 в dev (старт одной командой), тесты JUnit 5 + Mockito, запуск через Docker Compose[span_29](start_span)[span_29](end_span).

`Java 21` `Spring Boot` `Spring Security` `JWT` `JPA/Hibernate` `PostgreSQL` `H2` `JUnit 5` `Docker Compose`[span_30](start_span)[span_30](end_span)

### 🤝 Контакты

- 📧 **Почта**: [albertadaman70@gmail.com](mailto:albertadaman70@gmail.com)[span_31](start_span)[span_31](end_span)
- 💬 **Telegram**: [@moon_dsdsdsss](https://t.me/moon_dsdsdsss)[span_32](start_span)[span_32](end_span)
- 🐙 **GitHub**: [CreatorShyMoon](https://github.com/CreatorShyMoon)[span_33](start_span)[span_33](end_span)
- 🦊 **GitLab**: [CreatorShyMoon](https://gitlab.com/CreatorShyMoon)[span_34](start_span)[span_34](end_span)

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
containers, air-gapped artifact repositories, CI/CD pipelines and reproducible environments[span_35](start_span)[span_35](end_span)[span_36](start_span)[span_36](end_span)[span_37](start_span)[span_37](end_span). I like understanding how things work under the hood — syscalls, the kernel, the build system — and then automating them so nothing depends on manual steps.

**What I do:**

- ⚙️ Build **low-level Linux software** in C/C++ — sockets, `epoll`, signal handling (`signalfd`), IPC (`fork`/`exec`/`pipe`), `ioctl`, namespaces, cgroups v2[span_38](start_span)[span_38](end_span)[span_39](start_span)[span_39](end_span)[span_40](start_span)[span_40](end_span)
- 📦 Write my own **container runtime** to understand what Docker actually does at the syscall level[span_41](start_span)[span_41](end_span)
- 🌐 Design **Air-Gapped infrastructure** — self-hosted PEP 503 PyPI index, binary artifact mirroring and offline monolith bundling[span_42](start_span)[span_42](end_span)
- 🔁 Wrap every project in a **full CI/CD pipeline** — lint, build matrix (gcc/clang), static analysis, coverage, sanitizers, fuzzing, packaging[span_43](start_span)[span_43](end_span)
- 🐳 Use **Docker** for reproducible dev environments (Linux toolchain on a macOS host)[span_44](start_span)[span_44](end_span)
- 🐧 Administer **Linux** as a sysadmin: processes, systemd, networking, LVM, permissions, logs, SSH, hardening[span_45](start_span)[span_45](end_span)[span_46](start_span)[span_46](end_span)
- 📐 Document what I learn — architecture decisions, READMEs and a personal knowledge base

**Also interested in:** PostgreSQL, Ansible, AWS, monitoring with VictoriaMetrics + Grafana, game/network scripting (SQF / Arma 3), backend services on Spring Boot[span_47](start_span)[span_47](end_span).

### 📌 Featured Projects

#### ⚡ [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — high-performance TCP server

Single-threaded TCP server on `epoll(7)`: thousands of connections over the text protocol
`PING`/`ECHO`/`UPPER`/`QUIT`[span_48](start_span)[span_48](end_span). Reactor pattern with non-blocking I/O (`eventfd`, `signalfd`);
protocol logic is a pure function covered by unit tests and fuzzing[span_49](start_span)[span_49](end_span). GitLab CI: lint,
gcc/clang matrix, sanitizers, coverage, libFuzzer[span_50](start_span)[span_50](end_span)[span_51](start_span)[span_51](end_span).

`C++20` `epoll` `eventfd` `signalfd` `CMake` `GoogleTest` `libFuzzer` `Docker` `GitLab CI`[span_52](start_span)[span_52](end_span)[span_53](start_span)[span_53](end_span)

#### 📦 [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — container runtime

Runs a process in an isolated environment — what Docker does, in miniature (~1k lines of
C++)[span_54](start_span)[span_54](end_span). Namespaces via `clone(2)` and `pivot_root` for the filesystem, cgroups v2 limits,
capability dropping, plus PID 1 semantics: zombie reaping and signal forwarding[span_55](start_span)[span_55](end_span).

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `CMake` `GoogleTest` `Docker`[span_56](start_span)[span_56](end_span)[span_57](start_span)[span_57](end_span)

#### 🖥️ [TUIOpenMath_Server (SysOpenMath)](https://github.com/CreatorShyMoon/TUIOpenMath_Server) — air-gapped math environment platform

Client-server provisioning platform that deploys scientific environments (Python, Julia LTS, JupyterLab, Octave, Scilab) on completely offline (air-gapped) Linux machines[span_58](start_span)[span_58](end_span):
- **System TUI Client (`C11` / `ncursesw`)**: async process runner (`fork`/`exec`/`pipe`), flicker-free resize handling via `ioctl(TIOCGWINSZ)`, and atomic script execution using `mkstemp` + `trap EXIT`[span_59](start_span)[span_59](end_span).
- **Self-Hosted Artifact Server (`FastAPI`)**: local **PEP 503 PyPI repository** (`/simple/`) serving 120+ wheels and portable toolchains with `SHA-256` verification, Read-Only REST API isolation, and single-archive offline bundling (`make bundle`)[span_60](start_span)[span_60](end_span).

`C11` `POSIX` `ncursesw` `ioctl` `FastAPI` `PEP 503 PyPI` `Air-Gapped` `JupyterLab` `Julia` `cJSON`[span_61](start_span)[span_61](end_span)[span_62](start_span)[span_62](end_span)

#### ☕ [todo-api](https://github.com/CreatorShyMoon/todo-api) — task REST API

Task REST API with JWT auth[span_63](start_span)[span_63](end_span). Spring Security + JPA/Hibernate, PostgreSQL in prod, H2 in dev
(single-command start), JUnit 5 + Mockito tests, Docker Compose[span_64](start_span)[span_64](end_span).

`Java 21` `Spring Boot` `Spring Security` `JWT` `JPA/Hibernate` `PostgreSQL` `H2` `JUnit 5` `Docker Compose`[span_65](start_span)[span_65](end_span)

### 🤝 Let's Connect

- 📧 **Email**: [albertadaman70@gmail.com](mailto:albertadaman70@gmail.com)[span_66](start_span)[span_66](end_span)
- 💬 **Telegram**: [@moon_dsdsdsss](https://t.me/moon_dsdsdsss)[span_67](start_span)[span_67](end_span)
- 🐙 **GitHub**: You're already here!
