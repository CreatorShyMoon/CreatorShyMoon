# Albert Adamyan

```text
albert@linux:~$ whoami
Albert Adamyan

albert@linux:~$ cat /etc/focus
Linux Kernel & Internals · C/C++ · Network Security · Containers · Air-Gapped Infra · CI/CD

albert@linux:~$ uptime
building reliable systems since 2023
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

### 👨💻 Обо мне

Пишу системный софт на **C/C++** под Linux (от прикладных демонов до модулей ядра) и строю **инфраструктуру** вокруг него: контейнеры, изолированные (Air-Gapped) среды, CI/CD, выделенные игровые серверы и воспроизводимые окружения. 

Мне нравится докапываться до самой сути: не просто использовать готовые инструменты, а разбираться, как они устроены «под капотом» ядра Linux — системные вызовы, прерывания, сетевые буферы, управление памятью и изоляция.

**Чем я занимаюсь:**

- 🛡️ **Разработка под ядро Linux (Kernel Space)**: пишу модули ядра (LKM), работаю с сетевой фильтрацией Netfilter, перехватом пакетов `sk_buff` и потокобезопасностью в прерываниях (`softirq`).
- ⚙️ **Низкоуровневые сетевые сервисы на C/C++**: сокеты, неблокирующий ввод-вывод (`epoll`), сигналы (`signalfd`), IPC (`fork`/`exec`/`pipe`).
- 📦 **Изучение контейнеризации изнутри**: написал свой аналог Docker, чтобы на практике понять, как ядро изолирует процессы и ресурсы.
- 🎮 **Игровые серверы и сетевой код (Arma 3)**: разрабатываю серверную архитектуру и сложную логику на SQF для проекта **FINAL SECTOR** на выделенных Linux-серверах (RPC, синхронизация сотен игроков, оптимизация FPS).
- 🌐 **Автономная (Air-Gapped) инфраструктура**: сборка систем, работающих полностью без интернета (собственные серверы пакетов, зеркала и офлайн-бандлы).
- 🔁 **Культура CI/CD и тестов**: любой проект автоматически собирается под несколькими компиляторами (GCC/Clang), проверяется статическим анализом, санитайзерами памяти и стресс-тестами (фаззингом).
- 🐧 **Администрирование Linux**: настройка безопасности, демоны systemd, сети, фаерволы, диски (LVM), права доступа и диагностика сбоев.

---

### 📌 Избранные проекты (на пальцах)

#### 🛡️ [mini-firewall](https://github.com/CreatorShyMoon/mini-firewall) — сетевой файрвол внутри ядра Linux
> **Простыми словами:** Программа-щит, которая встраивается прямо в ядро Linux и мгновенно блокирует нежелательный сетевой трафик ещё до того, как он дойдёт до обычных программ.

* **Что делает:** Перехватывает сетевые пакеты на лету, блокирует опасные IP-адреса и порты, переводит сервер в «режим невидимки» (игнорирует пинги) и защищает от скрытого сканирования хакерами (Xmas/NULL-сканы).
* **Управление:** В комплекте идет собственная консольная утилита `fwctl` для добавления правил и просмотра статистики отброшенных пакетов в реальном времени.

`C99` `Linux Kernel Module (LKM)` `Netfilter` `sk_buff` `spin_lock_bh` `procfs` `fwctl CLI`

---

#### 📦 [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — легковесный аналог Docker с нуля
> **Простыми словами:** Собственный мини-Docker, написанный на C++, чтобы понять, как работает изоляция контейнеров на уровне операционной системы.

* **Что делает:** Запирает запускаемое приложение в изолированной среде: программа видит только свою отдельную папку (не имея доступа к файлам сервера), получает собственное имя и отдельный список процессов.
* **Безопасность:** Задает жесткие лимиты по памяти (RAM) и процессору (CPU), сбрасывает опасные права root и корректно передает сигналы остановки (Ctrl+C).

`C++20` `Linux namespaces` `cgroups v2` `pivot_root` `capabilities` `PID 1 init` `GitLab CI`

---

#### ⚡ [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — скоростной сетевой TCP-сервер
> **Простыми словами:** Высоконагруженный сервер, способный держать тысячи клиентов одновременно на одном ядре процессора (по архитектуре похож на Nginx или Redis).

* **Что делает:** Вместо тяжелого выделения отдельного потока на каждого пользователя, сервер мгновенно переключается между активными соединениями, экономя оперативную память.
* **Надежность:** Корректно завершает работу без обрыва соединений (Graceful Shutdown). Протестирован миллионами случайных запросов (фаззинг libFuzzer).

`C++20` `epoll` `reactor pattern` `non-blocking I/O` `signalfd` `libFuzzer` `GoogleTest` `GitLab CI`

---

#### 🎮 [FINAL SECTOR (Arma 3 Script Engine)](https://github.com/CreatorShyMoon/FinalSectorScript-s) — сетевой движок игрового проекта *(Private)*
> **Простыми словами:** Собственная серверная кодовая база и скриптовый движок для мультиплеерного проекта **FINAL SECTOR** в тактическом симуляторе Arma 3.

* **Сетевая синхронизация (RPC):** Написание распределенной клиент-серверной логики (`remoteExec`), синхронизация состояний игроков, объектов и окружения без рассинхронов.
* **Оптимизация производительности:** Асинхронное распределение задач (`spawn`, планировщик движка), обеспечивающее высокий и стабильный серверный FPS при большом онлайне.
* **Серверная инфраструктура:** Эксплуатация и тюнинг выделенных серверов (Arma 3 Dedicated Server) под Linux, автоматизация перезапусков и мониторинг логов.
* **Ссылки проекта:** [Discord сообщество](https://discord.gg/4qrpCGP8F) · [TikTok @finalsectorarma3](https://www.tiktok.com/@finalsectorarma3)

`SQF` `Arma 3` `Linux Dedicated Server` `Networking RPC` `remoteExec` `Multiplayer State Sync`

---

#### 🖥️ [TUIOpenMath_Server (SysOpenMath)](https://github.com/CreatorShyMoon/TUIOpenMath_Server) — развертывание сред на машинах без интернета
> **Простыми словами:** Комплекс для быстрой установки рабочих и научных сред (Python, Julia, JupyterLab) на изолированные компьютеры, полностью отрезанные от сети (Air-Gapped).

* Текстовое меню в терминале на C11 (`ncursesw`) + локальный сервер пакетов (FastAPI / PEP 503 PyPI), раздающий 120+ пакетов с проверкой контрольных сумм SHA-256.

`C11` `POSIX` `ncursesw` `ioctl` `FastAPI` `PEP 503 PyPI` `Air-Gapped` `SHA-256`

---

#### ☕ [todo-api](https://github.com/CreatorShyMoon/todo-api) — классический REST API бэкенд
> **Простыми словами:** Готовый серверный сервис для работы с задачами по современным стандартам бэкенд-разработки.

* Безопасная авторизация по JWT-токенам (Spring Security), база данных PostgreSQL, тесты (JUnit 5 + Mockito) и запуск одной командой через Docker Compose.

`Java 21` `Spring Boot` `Spring Security` `JWT` `PostgreSQL` `Docker Compose`

---

### 🤝 Контакты

- 📧 **Почта**: [albertadaman70@gmail.com](mailto:albertadaman70@gmail.com)
- 💬 **Telegram**: [@moon_dsdsdsss](https://t.me/moon_dsdsdsss)
- 🐙 **GitHub**: [CreatorShyMoon](https://github.com/CreatorShyMoon)
- 🦊 **GitLab**: [CreatorShyMoon](https://gitlab.com/CreatorShyMoon)

---

## 🛠️ Стек технологий (Tech Stack)

### Языки программирования
![C](https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![SQF](https://img.shields.io/badge/SQF%20(Arma%203)-2E3440?style=flat-square&logo=cplusplus&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

### Ядро Linux и системная разработка
![Linux Kernel](https://img.shields.io/badge/Linux%20Kernel%20(LKM)-FCC624?style=flat-square&logo=linux&logoColor=black)
![Netfilter](https://img.shields.io/badge/Netfilter%20Hooks-brightgreen?style=flat-square&logo=linux&logoColor=white)
![POSIX](https://img.shields.io/badge/POSIX%20syscalls-333333?style=flat-square&logo=linux&logoColor=white)
![epoll](https://img.shields.io/badge/epoll%20%2F%20reactor-4B8BBE?style=flat-square&logo=linux&logoColor=white)
![Namespaces](https://img.shields.io/badge/namespaces%20%2B%20cgroups%20v2-2496ED?style=flat-square&logo=linux&logoColor=white)
![Dedicated Server](https://img.shields.io/badge/Dedicated%20Server%20Admin-107C41?style=flat-square&logo=linux&logoColor=white)
![CMake](https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white)
![GCC](https://img.shields.io/badge/GCC%20%2F%20Clang-A42E2B?style=flat-square&logo=llvm&logoColor=white)

### Инфраструктура и DevOps
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitLab CI](https://img.shields.io/badge/GitLab%20CI-FC6D26?style=flat-square&logo=gitlab&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat-square&logo=ansible&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![VictoriaMetrics](https://img.shields.io/badge/VictoriaMetrics%20%2B%20Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

---

## 🇬🇧 English version

### 👨💻 About Me

I develop low-level systems software in **C/C++** for Linux (ranging from user-space network daemons to kernel modules), design game server network backends, and maintain reliable **infrastructure** supporting it: container runtimes, air-gapped repositories, CI/CD pipelines, and dedicated Linux servers.

Rather than just using abstraction layers, I focus on how things operate under the hood: Linux system calls, interrupt contexts, network socket buffers (`sk_buff`), memory protection, and process isolation.

---

### 📌 Featured Projects (In Plain English)

#### 🛡️ [mini-firewall](https://github.com/CreatorShyMoon/mini-firewall) — Linux Kernel Packet Filter (LKM)
> **In Plain English:** A kernel-level network shield that drops malicious traffic in real time before it ever reaches user applications.

* Intercepts incoming network packets using Netfilter hooks (`NF_INET_PRE_ROUTING`), inspects raw `sk_buff` headers, drops blacklisted IPs/ports, and blocks stealth reconnaissance scans (Xmas/NULL scans).
* Includes a custom, clean CLI management utility (`fwctl`) with real-time drop counters.

`C99` `Linux Kernel Module (LKM)` `Netfilter` `sk_buff` `spin_lock_bh` `fwctl CLI`

---

#### 📦 [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — Lightweight Container Runtime
> **In Plain English:** A custom, from-scratch replica of Docker written in C++ to master Linux process isolation.

* Runs commands in isolated namespaces (`clone`), mounts a jailed root filesystem (`pivot_root`), enforces strict RAM/CPU quotas via `cgroups v2`, drops root capabilities, and implements PID 1 zombie reaping and signal forwarding.

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `PID 1 init`

---

#### ⚡ [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — High-Performance TCP Server
> **In Plain English:** An ultra-fast network server handling thousands of concurrent client connections on a single CPU core without lags (similar to Nginx / Redis).

* Single-threaded event loop on `epoll(7)` with non-blocking sockets. Does not spawn expensive threads per user.
* Clean separation of protocol logic from I/O; fuzzed with millions of malformed payloads via `libFuzzer`.

`C++20` `epoll` `reactor pattern` `non-blocking I/O` `signalfd` `libFuzzer`

---

#### 🎮 [FINAL SECTOR (Arma 3 Script Engine)](https://github.com/CreatorShyMoon/FinalSectorScript-s) — Game Network Engine *(Private)*
> **In Plain English:** Custom server-side codebase and network engine for the **FINAL SECTOR** multiplayer project in Arma 3 tactical simulator.

* **Multiplayer Replication:** Distributed client-server synchronization (`remoteExec` RPC), state sync for players and environment without desyncs.
* **Server Performance:** Asynchronous task scheduling ensuring stable and high server FPS under heavy player counts.
* **Linux Dedicated Server:** Deploying, configuring, and monitoring Arma 3 Dedicated Servers on Linux.
* **Links:** [Discord Server](https://discord.gg/4qrpCGP8F) · [TikTok @finalsectorarma3](https://www.tiktok.com/@finalsectorarma3)

`SQF` `Arma 3` `Linux Dedicated Server` `Networking RPC` `remoteExec` `Multiplayer Sync`

---

#### 🖥️ [TUIOpenMath_Server (SysOpenMath)](https://github.com/CreatorShyMoon/TUIOpenMath_Server) — Air-Gapped Platform
> **In Plain English:** A complete offline deployment system for scientific environments (Python, Julia, JupyterLab) on air-gapped Linux workstations without internet access.

* Responsive terminal client in C11 (`ncursesw`) + local PEP 503 PyPI server (FastAPI) distributing 120+ pre-cached packages with SHA-256 integrity validation.

`C11` `POSIX` `ncursesw` `FastAPI` `PEP 503 PyPI` `Air-Gapped`

---

#### ☕ [todo-api](https://github.com/CreatorShyMoon/todo-api) — Task REST API
> **In Plain English:** A production-style backend REST API for task management built with modern engineering practices.

* JWT authentication, Spring Security, PostgreSQL, JUnit 5 + Mockito tests, containerized with Docker Compose.

`Java 21` `Spring Boot` `Spring Security` `JWT` `PostgreSQL` `Docker Compose`

---

### 🤝 Let's Connect

- 📧 **Email**: [albertadaman70@gmail.com](mailto:albertadaman70@gmail.com)
- 💬 **Telegram**: [@moon_dsdsdsss](https://t.me/moon_dsdsdsss)
- 🐙 **GitHub**: You are already here!
