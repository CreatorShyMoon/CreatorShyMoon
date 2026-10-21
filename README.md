# Albert Adamyan

```text
albert@linux:~$ whoami
Albert Adamyan

albert@linux:~$ cat /etc/focus
Linux internals · C/C++ · containers · CI/CD · observability

albert@linux:~$ uptime
building reliable systems since 2024
```

Пишу системный софт на **C/C++** под Linux и строю инфраструктуру вокруг него: контейнеры, CI/CD и воспроизводимые окружения.

---

## Обо мне

Мне интересно, как всё устроено под капотом — сисколлы, ядро, сборка, сеть. Поэтому я не останавливаюсь на использовании инструмента: разбираю его до уровня, на котором могу собрать что-то своё.

Люблю проекты, где можно пройти путь до конца: от архитектуры и кода до тестов, CI, Docker-образа и документации.

**Принципы:** понять уровень ниже · автоматизировать повторяющееся · доказывать тестами · оставлять след.

---

## Избранные проекты

### [epoll-server](https://github.com/CreatorShyMoon/epoll-server) — высокопроизводительный TCP-сервер

Однопоточный сервер на reactor-паттерне поверх `epoll(7)`: неблокирующий I/O, буферизация на каждое соединение, `eventfd` для остановки цикла и `signalfd` для graceful shutdown.

Логика протокола вынесена в чистую функцию и покрыта unit-тестами и фаззингом. Вокруг — GitLab CI: линтеры, матрица gcc/clang, ASan/UBSan/TSan, `clang-tidy`, `cppcheck` и `libFuzzer`.

`C++20` `epoll` `eventfd` `signalfd` `CMake` `GoogleTest` `libFuzzer`

---

### [mini-runtime](https://github.com/CreatorShyMoon/mini-runtime) — контейнерный рантайм

Мини-рантайм контейнеров на C++20 — попытка понять, как устроен Docker, и собрать его ядро самостоятельно.

Изоляция через `clone(2)` и namespaces, файловая система через `pivot_root`, лимиты через cgroups v2, сброс capabilities и честный PID 1: сбор зомби и forwarding сигналов в process group контейнера. Покрыт тестами, включая интеграционные с реальной изоляцией.

`C++20` `namespaces` `cgroups v2` `pivot_root` `capabilities` `CMake` `GoogleTest`

---

### [TUIOpenMath](https://github.com/CreatorShyMoon/TUIOpenMath) — среда для вычислений в терминале

Терминальный TUI на **C11** и **ncurses**, который превращает чистый Linux в готовую среду для вычислений: 7 профилей, изолированные Python venv, Julia LTS/Stable и JupyterLab.

Установки идут асинхронно через `fork` / `pipe` / `waitpid` и стримятся в живую лог-панель. Управление полностью с клавиатуры, без графики — работает по SSH.

`C11` `ncurses` `JupyterLab` `Julia` `Python venv` `cJSON`

---

### [todo-api](https://github.com/CreatorShyMoon/todo-api) — REST API для задач

Spring Boot-приложение с **Spring Security + JWT**, Spring Data JPA / Hibernate и PostgreSQL в production-профиле. Поднимается через Docker Compose, покрыто тестами на JUnit 5 + Mockito и отдаёт собственный статический веб-клиент.

`Java 21` `Spring Boot` `Spring Security` `JWT` `PostgreSQL` `Docker Compose`

---

### [machine-translation](https://github.com/CreatorShyMoon/machine-translation) — генератор заданий

Приложение на **C**, которое генерирует индивидуальные задания по теме машинного представления вещественных чисел: IEEE 754, битовые операции и аккуратный ввод-вывод.

`C` `IEEE 754`

---

### [MatrixLibMultiply3](https://github.com/CreatorShyMoon/MatrixLibMultiply3) — умножение матриц

Библиотека на **C++** для быстрого умножения матриц любого размера: алгоритмы с учётом кэша вместо наивного тройного цикла.

`C++` `алгоритмы` `производительность`

---

### [GameTurn-BasedCombat](https://github.com/CreatorShyMoon/GameTurn-BasedCombat) — пошаговая RPG

Консольная пошаговая RPG на карте 15×15 на **C++**, построенная на паттернах «Стратегия» и «Фабрика» для действий персонажа.

`C++` `ООП` `паттерны проектирования`

---

## Стек

<p>
  <img src="https://img.shields.io/badge/C-00599C?style=flat-square&logo=c&logoColor=white" alt="C">
  <img src="https://img.shields.io/badge/C%2B%2B-00599C?style=flat-square&logo=cplusplus&logoColor=white" alt="C++">
  <img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white" alt="Bash">
  <img src="https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white" alt="CMake">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker">
  <img src="https://img.shields.io/badge/GitLab%20CI-FC6D26?style=flat-square&logo=gitlab&logoColor=white" alt="GitLab CI">
  <img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" alt="GitHub Actions">
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white" alt="Java">
</p>

**Systems:** C, C++20, POSIX, Linux, epoll, namespaces, cgroups, pivot_root, capabilities, signals, pthread

**Infrastructure:** Docker, Docker Compose, GitLab CI, GitHub Actions, Nginx, systemd, Bash, PostgreSQL

**Quality:** CMake, Make, GCC/Clang, gdb, GoogleTest, ASan/UBSan/TSan, libFuzzer, clang-tidy, cppcheck, gcovr

**Backend:** Java 21, Spring Boot, Spring Security, JWT, JPA/Hibernate, JUnit 5, Mockito

**Изучаю:** Ansible, Prometheus/Grafana, Loki, k3s, Terraform

---

<details>
<summary>English</summary>

### About

I write systems software in **C/C++** for Linux and build the infrastructure around it: containers, CI/CD and reproducible environments. I like understanding how things work under the hood — syscalls, the kernel, the build system — and then automating them so nothing depends on manual steps.

I enjoy projects where I can go all the way: architecture, code, tests, CI, Docker image and documentation.

### Selected work

- **[epoll-server](https://github.com/CreatorShyMoon/epoll-server)** — single-threaded TCP server on the reactor pattern over `epoll(7)`. Non-blocking I/O, `eventfd`, `signalfd`, unit tests, sanitizers, fuzzing and GitLab CI.
- **[mini-runtime](https://github.com/CreatorShyMoon/mini-runtime)** — container runtime in C++20. Linux namespaces, `cgroups v2`, `pivot_root`, capability dropping and PID 1 semantics.
- **[TUIOpenMath](https://github.com/CreatorShyMoon/TUIOpenMath)** — terminal TUI in C11 and ncurses for setting up a reproducible math environment.
- **[todo-api](https://github.com/CreatorShyMoon/todo-api)** — Spring Boot REST API with JWT, PostgreSQL and Docker Compose.

### Stack

C/C++20, Linux, POSIX, epoll, namespaces, cgroups, Docker, GitLab CI, GitHub Actions, Nginx, systemd, Bash, PostgreSQL, Java/Spring Boot, CMake, GoogleTest, ASan/UBSan/TSan, libFuzzer.

</details>

---

## Контакты

[Email](mailto:albertadaman70@gmail.com) · [Telegram](https://t.me/moon_dsdsdsss) · [GitLab](https://gitlab.com/CreatorShyMoon) · [Все репозитории](https://github.com/CreatorShyMoon?tab=repositories)
