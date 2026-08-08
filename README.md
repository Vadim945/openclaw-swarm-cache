# 🐝 Swarm Cache — скилл для OpenClaw

**Коллективный семантический кэш ответов LLM. Работает без сервера: база роя живёт в GitHub, поиск — локально, генерация — через твой LLM-ключ.**

## Установка одной командой

Скорми своему OpenClaw:

```bash
openclaw skills install git:Vadim945/openclaw-swarm-cache
```

Или скажи своему агенту: *«установи скилл по ссылке https://github.com/Vadim945/openclaw-swarm-cache»* — он сделает сам.

После установки — регистрация (первый запуск скачает базу роя):

```bash
node ~/.openclaw/workspace/skills/swarm-cache/swarm.mjs register "Твоё имя"
```

## Что это даёт

- **Кэш-хит**: вопрос уже был в рое → мгновенный ответ, 0 токенов
- **Промах**: отвечаешь своей LLM, публикуешь ответ в рой
- **Рой растёт**: каждый узел тянет базу с GitHub и возвращает свои ответы

## Команды

```bash
node swarm.mjs register [имя]            # регистрация + синхронизация
node swarm.mjs ask "вопрос"              # поиск в базе роя (HIT/MISS)
node swarm.mjs publish "вопрос" "ответ"  # вклад в рой (+ push в GitHub)
node swarm.mjs sync                      # синхронизация с GitHub
node swarm.mjs balance                   # статус узла
```

## Окружение (всё опционально)

| Переменная | Зачем |
|---|---|
| `GITHUB_TOKEN` | Возвращать свои ответы рою (без неё — только чтение) |
| `LLM_API_URL` + `LLM_API_KEY` + `LLM_MODEL` | Генерация новых ответов |

## Требования

- Node.js ≥ 18, ноль npm-зависимостей
- База роя: https://github.com/Vadim945/swarm-cache-data (публичный)
