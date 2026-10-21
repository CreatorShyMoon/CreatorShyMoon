# Albert Adamyan

```text
albert@linux:~$ whoami
Albert Adamyan

albert@linux:~$ cat /etc/focus
Linux internals · C/C++ · containers · CI/CD · observability

albert@linux:~$ uptime
building reliable systems since 2024
```

**Systems Software Engineer** из Краснодара. Пишу низкоуровневый софт под Linux и собираю инфраструктуру вокруг него: контейнеры, CI/CD, воспроизводимые окружения. Сейчас двигаюсь в сторону DevOps — Linux, systemd, Nginx, мониторинг, логи и Kubernetes.

Не коллекционирую технологии. Собираю системы, которые можно понять, проверить и воспроизвести.

---

## Сейчас

- Собираю **DevOps-лабораторию** по собственной дорожной карте: Linux VM, SSH, systemd, Nginx, CI/CD, Prometheus/Grafana, Loki, k3s.
- Довожу **mini-runtime** — контейнерный рантайм на C++20, который показывает, что Docker делает на уровне сисколлов.
- Развиваю **epoll-server** — однопоточный TCP-сервер на reactor-паттерне с полным CI.
- Веду инженерные заметки: архитектурные решения, диагностика, разборы ошибок и документация к проектам.

---

## Как я работаю

1. **Спускаюсь на уровень ниже.** Мне важно понимать не только `docker run`, но и `namespaces`, `cgroups`, `pivot_root` и `capabilities`.
2. **Автоматизирую повторяющееся.** Если действие делается второй раз руками — оно должно стать скриптом, pipeline или конфигурацией.
3. **Доказываю качество.** Тесты, санитайзеры, статический анализ, фаззинг и CI для меня не галочка, а способ не врать самому себе.
4. **Оставляю след.** README, схемы, runbook и заметки должны позволить другому человеку повторить результат без меня.

---

## Лаборатория

| Проект | Что это | Стек |
|---|---|---|
| [epoll-server](https://github.com/CreatorShyMoon/epoll-server) | Высокопроизводительный TCP-сервер на reactor-паттерне | C++20, epoll, eventfd, signalfd, CMake |
| [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) | Контейнерный рантайм: namespaces, cgroups v2, pivot_root, capabilities | C++20, Linux, CMake |
| [TUIOpenMath](https://github.com/CreatorShyMoon/TUIOpenMath) | Терминальный менеджер математической среды | C11, ncurses, JupyterLab, Julia |
| [todo-api](https://github.com/CreatorShyMoon/todo-api) | REST API с JWT, PostgreSQL и Docker Compose | Java 21, Spring Boot, JPA, JUnit |

---

## Избранные проекты

### [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — высокопроизводительный TCP-сервер

Однопоточный сервер на reactor-паттерне поверх `epoll(7)`. Обслуживает множество соединений без создания отдельного потока под каждого клиента.

**Что внутри:**
- неблокирующий I/O и буферизация на каждое соединение;
- `eventfd` для остановки event loop и `signalfd` для graceful shutdown;
- текстовый протокол `PING` / `ECHO` / `UPPER` / `QUIT`;
- логика протокола вынесена в чистую функцию и тестируется без сети.

**Проверка:** 13 тестов, ASan/UBSan/TSan, `clang-tidy`, `cppcheck`, `libFuzzer`, матрица gcc/clang, GitHub Actions.

`C++20` `epoll` `eventfd` `signalfd` `CMake` `GoogleTest` `libFuzzer`

---

### [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — контейнерный рантайм

Мини-рантайм контейнеров на C++20 — попытка понять, как устроен Docker, и собрать его ядро самостоятельно.

**Что внутри:**
- изоляция через `clone(2)` и Linux namespaces: PID, MNT, UTS, IPC, опционально NET;
- файловая система через `pivot_root`, свежие `/proc`, `/dev` и read-only `/sys`;
- лимиты через `cgroups v2`: `memory.max`, `pids.max`, `cpu.max`;
- сброс capabilities и `PR_SET_NO_NEW_PRIVS`;
- поведение PID 1: сбор зомби и forwarding сигналов в process group контейнера.

**Проверка:** 19 тестов, включая интеграционные с реальной изоляцией, ASan/UBSan, сборка gcc/clang, GitHub Actions.

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `CMake` `GoogleTest`

---

### [TUIOpenMath](https://github.com/CreatorShyMoon/TUIOpenMath) — менеджер открытой математической среды

Терминальный TUI на C11 и ncurses, который превращает чистый Linux в готовую среду для вычислений.

**Что внутри:**
- 7 встроенных профилей;
- изолированные Python venv, Julia LTS/Stable, JupyterLab;
- Jupyter-ядра для Python, Julia, Bash, Octave и Scilab;
- асинхронные установки через `fork` / `pipe` / `waitpid` и живая лог-панель;
- полностью клавиатурное управление, работает по SSH.

**Проверка:** сборка gcc/clang, `cppcheck`, GitHub Actions.

`C11` `ncurses` `JupyterLab` `Julia` `Python venv` `cJSON`

---

### [todo-api](https://github.com/CreatorShyMoon/todo-api) — REST API для задач

Spring Boot-приложение с аутентификацией, базой данных и Docker Compose.

**Что внутри:**
- Spring Security + JWT;
- Spring Data JPA / Hibernate;
- PostgreSQL в production-профиле и H2 в dev;
- JUnit 5 + Mockito;
- статический веб-клиент, который отдаёт сам Spring.

`Java 21` `Spring Boot` `Spring Security` `JWT` `PostgreSQL` `Docker Compose`

---

## Стек

**Systems:** C, C++20, POSIX, Linux, epoll, namespaces, cgroups, pivot_root, capabilities, signals, pthread

**Infrastructure:** Docker, Docker Compose, GitLab CI, GitHub Actions, Nginx, systemd, Bash, PostgreSQL

**Quality:** CMake, Make, GCC/Clang, gdb, GoogleTest, ASan/UBSan/TSan, libFuzzer, clang-tidy, cppcheck, gcovr

**Backend:** Java 21, Spring Boot, Spring Security, JWT, JPA/Hibernate, JUnit 5, Mockito

**Сейчас изучаю:** Ansible, Prometheus/Grafana, Loki, k3s, Terraform

---

## CI

[epoll-server](https://github.com/CreatorShyMoon/epoll-server/actions) · [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime/actions) · [TUIOpenMath](https://github.com/CreatorShyMoon/TUIOpenMath/actions)

Все три системных проекта собираются и проверяются автоматически.

---

<details>
<summary>English</summary>

### About

**Systems Software Engineer** based in Krasnodar, Russia. I build low-level Linux software in C/C++ and the infrastructure around it: containers, CI/CD and reproducible environments. Currently expanding into DevOps: Linux administration, systemd, Nginx, observability and Kubernetes.

I do not collect technologies. I build systems that can be understood, verified and reproduced.

### Selected work

- **[epoll-server](https://github.com/CreatorShyMoon/epoll-server)** — single-threaded TCP server built on the reactor pattern over `epoll(7)`. Non-blocking I/O, `eventfd`, `signalfd`, 13 tests, sanitizers, fuzzing and CI.
- **[mini-runtime](https://github.com/CreatorShyMoon/mini-runtime)** — container runtime in C++20. Linux namespaces, `cgroups v2`, `pivot_root`, capability dropping, PID 1 semantics and 19 tests.
- **[TUIOpenMath](https://github.com/CreatorShyMoon/TUIOpenMath)** — terminal TUI in C11 and ncurses for setting up a reproducible math environment.
- **[todo-api](https://github.com/CreatorShyMoon/todo-api)** — Spring Boot REST API with JWT, PostgreSQL and Docker Compose.

### Stack

C/C++20, Linux, POSIX, epoll, namespaces, cgroups, Docker, GitLab CI, GitHub Actions, Nginx, systemd, Bash, PostgreSQL, Java/Spring Boot, CMake, GoogleTest, ASan/UBSan/TSan, libFuzzer.

Open to full-time and freelance opportunities around Linux, C/C++ and DevOps.

</details>

---

## Контакты

[Email](mailto:albertadaman70@gmail.com) · [Telegram](https://t.me/moon_dsdsdsss) · [GitLab](https://gitlab.com/CreatorShyMoon) · [Все репозитории](https://github.com/CreatorShyMoon?tab=repositories)

Краснодар · удалённо / гибрид · русский (родной), английский (B1)
