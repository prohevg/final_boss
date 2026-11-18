# SportSphere — архитектурное решение финальной работы

**SportSphere** — глобальное социальное фитнес-приложение транснациональной компании
производителя спортивных товаров (одежда, обувь, инвентарь). Приложение объединяет
социальные группы по интересам, трекинг и анализ тренировок, совместные тренировки,
геймификацию, умные подсказки по инвентарю и интеграцию с существующими приложениями
компании для продаж.

## Как читать решение

Рекомендуемый порядок для первого ознакомления:

1. [Бизнес-цели](docs/stage1-concept/01-business-goals.md) →
   [Функциональные требования](docs/stage1-concept/02-functional-requirements.md) →
   [Стейкхолдеры](docs/stage1-concept/03-stakeholders.md) — *что и для кого строим*;
2. [Концептуальная архитектура](docs/stage1-concept/04-conceptual-architecture.md) —
   *главная схема, от неё расходятся все остальные документы*;
3. [Атрибуты качества](docs/stage1-concept/08-quality-attributes.md) и
   [НФТ](docs/stage1-concept/09-nonfunctional-requirements.md) — *по каким правилам оцениваем*;
4. [Анализ опций](docs/stage1-concept/10-architecture-options.md) — *почему выбрано то, а не другое*;
5. [ADR](docs/stage2-plan/adr/README.md) → [Базовая архитектура](docs/stage2-plan/13-base-architecture.md) →
   [Представления](docs/stage2-plan/views/) — *как решение устроено и почему именно так*;
6. [Пересмотр рисков](docs/stage3-risk-cost/15-architecture-risks.md) →
   [Стоимость владения](docs/stage3-risk-cost/16-tco.md) — *что подтвердилось через год,
   во что обходится система и почему не дешевле*;
7. [Презентация защиты](presentation/SportSphere_презентация_для_инвестора.pptx)
   ([пояснительная записка](presentation/README.md)) — *вся защита за 6 минут*.

Схематические обозначения перекрёстных ссылок: каждый документ ссылается на
номера артефактов (`А-04` = артефакт 4), ADR (`ADR-003`) и на работы практик
курса (`9.6` … `15.6`), наработки которых используются в решении.

---

## Этап 1. Утверждение концепта (артефакты 1–10)

| № | Артефакт | Документ |
|---|----------|----------|
| 1 | Детализация бизнес-целей (не более 4) | [01-business-goals.md](docs/stage1-concept/01-business-goals.md) |
| 2 | Анализ и список функциональных требований | [02-functional-requirements.md](docs/stage1-concept/02-functional-requirements.md) |
| 3 | Анализ стейкхолдеров и их интересов | [03-stakeholders.md](docs/stage1-concept/03-stakeholders.md) |
| 4 | Концептуальная архитектура | [04-conceptual-architecture.md](docs/stage1-concept/04-conceptual-architecture.md) |
| 5 | Описание рисков реализации (бизнес и технические) | [05-risks.md](docs/stage1-concept/05-risks.md) |
| 6 | План поэтапной разработки и расширения, критически важные компоненты | [06-roadmap.md](docs/stage1-concept/06-roadmap.md) |
| 7 | Критические бизнес-сценарии | [07-critical-scenarios.md](docs/stage1-concept/07-critical-scenarios.md) |
| 8 | Основные атрибуты качества (не более 3) | [08-quality-attributes.md](docs/stage1-concept/08-quality-attributes.md) |
| 9 | Анализ и список нефункциональных требований | [09-nonfunctional-requirements.md](docs/stage1-concept/09-nonfunctional-requirements.md) |
| 10 | Анализ архитектурных опций и обоснование выбора | [10-architecture-options.md](docs/stage1-concept/10-architecture-options.md) |

## Этап 2. Защита плана реализации (артефакты 11–14)

| № | Артефакт | Документ |
|---|----------|----------|
| 11 | Список ADR (12 записей) | [adr/README.md](docs/stage2-plan/adr/README.md) |
| 12 | Сценарии использования приложения | [12-use-cases.md](docs/stage2-plan/12-use-cases.md) |
| 13 | Базовая архитектура (с учётом ограничений, НФТ, выбора, атрибутов качества) | [13-base-architecture.md](docs/stage2-plan/13-base-architecture.md) |
| 14 | Основные представления: a. функциональное · b. информационное · c. многозадачность · d. инфраструктурное · e. безопасность | [views/](docs/stage2-plan/views/) |

### ADR (артефакт 11)

| ADR | Решение |
|-----|---------|
| [001](docs/stage2-plan/adr/ADR-001-microservices.md) | Микросервисная архитектура по доменам |
| [002](docs/stage2-plan/adr/ADR-002-multicloud.md) | Мультиоблачность и портируемое ядро |
| [003](docs/stage2-plan/adr/ADR-003-data-residency.md) | Data residency и изоляция PII |
| [004](docs/stage2-plan/adr/ADR-004-event-driven.md) | Событийная интеграция через Kafka |
| [005](docs/stage2-plan/adr/ADR-005-gateway-bff.md) | API-шлюз и BFF как единая точка входа |
| [006](docs/stage2-plan/adr/ADR-006-offline-first.md) | Offline-first захват тренировок |
| [007](docs/stage2-plan/adr/ADR-007-geo-search.md) | Гео-поиск людей и маршрутов на OpenSearch |
| [008](docs/stage2-plan/adr/ADR-008-leaderboards.md) | Live-лидерборды в Redis, история в ClickHouse |
| [009](docs/stage2-plan/adr/ADR-009-identity-sso.md) | Единая идентичность: OIDC/SSO с приложениями компании |
| [010](docs/stage2-plan/adr/ADR-010-commerce-bridge.md) | Commerce Bridge: контракт с приложениями компании |
| [011](docs/stage2-plan/adr/ADR-011-datastores.md) | Хранилища: управляемое по умолчанию, self-managed точечно |
| [012](docs/stage2-plan/adr/ADR-012-observability.md) | Единая наблюдаемость: OpenTelemetry → метрики/логи/трассы |

### Представления (артефакт 14)

| Файл | Представление | Что показывает |
|------|---------------|----------------|
| [functional.md](docs/stage2-plan/views/functional.md) | А-14a, функциональное | Capability-группы сервисов и их связи |
| [information.md](docs/stage2-plan/views/information.md) | А-14b, информационное | Модель данных, потоки событий, объёмы хранения |
| [concurrency.md](docs/stage2-plan/views/concurrency.md) | А-14c, многозадачность | Офлайн-синхронизация и конкурентный доступ |
| [infrastructure.md](docs/stage2-plan/views/infrastructure.md) | А-14d, инфраструктурное | Мультиоблачность, регионы, DR-контур |
| [security.md](docs/stage2-plan/views/security.md) | А-14e, безопасность | Зоны доверия и потоки авторизации |

## Этап 3. Защита итогов (артефакты 15–16 + презентация)

| № | Артефакт | Документ |
|---|----------|----------|
| 15 | Пересмотр архитектурных рисков и компромиссов: вероятность, важность, трудозатраты, последствия | [15-architecture-risks.md](docs/stage3-risk-cost/15-architecture-risks.md) |
| 16 | Стоимость владения (TCO): годы 1 / 2 / 5, рост данных и пользователей | [16-tco.md](docs/stage3-risk-cost/16-tco.md) |
| — | Презентация защиты (9 слайдов, 5–7 мин) и пояснительная записка | [presentation/](presentation/) |

Что внутри:

- **А-15** — продолжение [А-05](docs/stage1-concept/05-risks.md): таблица пересмотра
  всех 19 рисков (что закрыто архитектурой, что подтвердилось и управляется, что
  осталось продуктовым), 8 осознанно принятых компромиссов и приоритеты на будущее.
- **А-16** — расчёт стоимости владения с точки зрения компьютерных ресурсов:
  допущения по MAU, нагрузке и данным, статьи затрат по годам, `$/пользователь`,
  сценарии альтернатив и механизм контроля стоимости.

## Презентация защиты

[SportSphere_презентация_для_инвестора.pptx](presentation/SportSphere_презентация_для_инвестора.pptx) —
9 слайдов, 16:9, 5–7 минут, заметки докладчика встроены в каждый слайд. Логика
«продающая», а не техническая: цели и метрики → риски на языке денег → одно решение
и одна схема → план волнами → TCO и альтернативы → три причины и конкретная просьба.

[Пояснительная записка](presentation/README.md) — назначение и аудитория, хронометраж
по слайдам, полный текст выступления, таблица ключевых чисел с источниками,
8 вопросов-ответов для защиты и инструкция по пересборке.

## Диаграммы

Отрендеренные схемы (PNG) лежат в [diagrams/](diagrams/):

| Файл | Назначение | Где используется |
|------|------------|------------------|
| `d1_conceptual.png` | Концептуальная архитектура | А-04, [презентация](presentation/README.md) |
| `d2_scenario_competition.png` | Критичный сценарий: массовое соревнование | А-07 |
| `d3_functional.png` | Функциональное представление | [А-14a](docs/stage2-plan/views/functional.md) |
| `d4_information.png` | Информационное представление (ER) | [А-14b](docs/stage2-plan/views/information.md) |
| `d5_concurrency.png` | Многозадачность: синхронизация и конкурентный доступ | [А-14c](docs/stage2-plan/views/concurrency.md) |
| `d6_infrastructure.png` | Инфраструктурное представление (мультиоблачность) | [А-14d](docs/stage2-plan/views/infrastructure.md) |
| `d7_security.png` | Зоны доверия и потоки авторизации | [А-14e](docs/stage2-plan/views/security.md) |

## Связи с работами практик курса

Решение опирается на наработки предыдущих работ: события и агрегаты (`9.6`),
интеграции и устойчивость к ошибкам (`10.5`), фиче-флаги (`11.5`),
безопасность и модели угроз внешних интеграций (`12.5`), API-шлюзы (`13.5`),
отказоустойчивая мультиоблачная инфраструктура и DRP (`14.5`),
наблюдаемость: метрики, логи, хранение (`15.6`).
