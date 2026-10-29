# DataLife Engine (DLE) Documentation — AI Agent Skill

[![Antigravity Skill](https://img.shields.io/badge/Antigravity-Skill-4285F4?style=flat-square&logo=google)](https://antigravity.google)
[![Documentation Source](https://img.shields.io/badge/Source-dle--news.ru-007ACC?style=flat-square)](https://dle-news.ru/extras/online/)
[![Status](https://img.shields.io/badge/Status-Up--to--date%20(Oct%202026)-success?style=flat-square)](#)

Официальная документация CMS **DataLife Engine (DLE)**, структурированная и оптимизированная под формат **AI Agent Skill** с поддержкой **Progressive Disclosure** (прогрессивного раскрытия контекста).

Предназначена для работы с AI-ассистентами и кодинг-агентами: **Google Antigravity**, **Cursor**, **Claude Code**, **Windsurf**, **Cline** и LLM с поддержкой RAG или длинного контекста.

---

## ⚖️ Авторские права и актуальность

> [!IMPORTANT]
> - **Правообладатель:** Все авторские, имущественные и исключительные права на документацию, товарный знак и CMS DataLife Engine принадлежат компании **Softnews Media Group** ([https://dle-news.ru](https://dle-news.ru)).
> - **Назначение:** Данный репозиторий создан в справочных и образовательных целях для обеспечения качественной интеграции и работы AI-ассистентов с движком DLE.
> - **Актуальность данных:** Документация в репозитории получена с официального раздела [https://dle-news.ru/extras/online/](https://dle-news.ru/extras/online/) и полностью актуальна на **29 октября 2026 года**.

---

## 📁 Структура репозитория

```text
.
├── SKILL.md                  # Главный файл навыка: frontmatter + интерактивное оглавление
├── references/               # 70 подробных разделов документации в Markdown
│   ├── topic_02_kratko_o_cms.md
│   ├── topic_08_nachalo_raboty_i_shablony.md
│   ├── topic_09_glavnye_i_globalnye_tegi_dlya_shablonov.md
│   ├── topic_21_sistema_plaginov.md
│   ├── topic_38_glavnyy_shablon_sayta.md
│   ├── topic_40_kratkoe_soderzhanie.md
│   ├── topic_41_statya_tselikom.md
│   ├── topic_72_razrabotka_i_podklyuchenie_moduley.md
│   ├── topic_74_api_dlya_razrabotki_moduley.md
│   └── ... (всего 70 файлов)
└── README.md
```

### Разделы документации

1. **Кратко о CMS**: Возможности, установка, обновление, системные требования.
2. **Начало работы и шаблоны**: Главные и глобальные теги шаблонов, теги новостей, ЧПУ, избранное, мобильная версия.
3. **Управление и контент**: Добавление/редактирование публикаций, доп. поля (xfields), категории, группы пользователей, фильтры, реклама, плагины.
4. **Шаблоны оформления**: Полный синтаксис всех `.tpl` файлов (`main.tpl`, `login.tpl`, `shortstory.tpl`, `fullstory.tpl`, `comments.tpl`, `userinfo.tpl`, `search.tpl` и др.).
5. **Разработка и API**: Создание плагинов, интеграция в админпанель, официальный PHP API DLE, крон (cron), RSS экспорт/импорт.

---

## 🚀 Установка и использование

### 1. В Google Antigravity

#### Глобально для всех проектов:
Склонируйте репозиторий в каталог пользовательских скиллов Antigravity:
```bash
git clone https://github.com/shlyahten/dle-docs-skill.git ~/.gemini/config/skills/dle-docs
```

#### Для конкретного проекта (локально):
Склонируйте репозиторий в папку `.agents/skills/` вашего DLE-проекта:
```bash
git clone https://github.com/shlyahten/dle-docs-skill.git .agents/skills/dle-docs
```

*После этого Antigravity будет автоматически обращаться к скиллу всякий раз, когда вы задаете вопросы о верстке, тегах шаблонов, создании плагинов или настройках DLE.*

---

### 2. В Cursor / Windsurf / Claude Code

Добавьте ссылку на данный репозиторий или файл `SKILL.md` в ваш `.cursorrules`, `CLAUDE.md` или промпт:
```markdown
При работе с шаблонами или кодом DataLife Engine обращайся к локальной документации в папке `dle-docs/references/` или файлу `dle-docs/SKILL.md`.
```

---

## 💡 Особенности форматирования под AI

- **Защита тегов шаблонизатора**: Теги вида `{custom ...}`, `{THEME}`, `[group=1]...[/group]` обёрнуты в кодовые блоки, предотвращая их повреждение или ложную интерпретацию LLM как Markdown-ссылок.
- **Таблицы параметров**: Все параметры модификаторов и тегов сведены в структурированные Markdown-таблицы для точного извлечения сущностей моделью.
- **Progressive Disclosure**: Агент загружает только нужную статью, не засоряя окно контекста лишними данными.
