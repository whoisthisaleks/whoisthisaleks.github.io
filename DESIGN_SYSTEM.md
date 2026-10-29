# Дизайн-система портфолио

Система описывает визуальную основу сайта и повторно используемые стили для новых экранов. Исходный сайт остаётся статическим HTML/CSS; сборщик и UI-фреймворк не нужны. Документация разделена по темам: [карта и навигация](docs/design-system/index.md), [паттерны](docs/design-system/patterns.md), [токены](docs/design-system/tokens.md), [playbook](docs/design-system/playbook.md) и [Figma](docs/design-system/figma.md).

## Страница-пример

Откройте `/design-system/` локально или на GitHub Pages после публикации ветки. Существующие `index.html` и `en/index.html` не подключают новый файл автоматически и не менялись в этой задаче.

Для новой страницы подключите шрифт Golos Text и общий CSS:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Golos+Text:wght@400;500;600&display=swap" rel="stylesheet">
<link rel="stylesheet" href="/assets/design-system.css">
```

У страницы должны быть `lang`, viewport и семантическая структура; используйте классы из префикса `ds-`, чтобы локальные правила не пересекались с прежними стилями.

## Цвета

| CSS-токен | Значение | Назначение |
| --- | --- | --- |
| `--color-page-bg` | `#FFFFFF` | Основной фон |
| `--color-text` | `#19191A` | Основной текст |
| `--color-card-bg` | `#F4F4F4` | Поверхности карточек |
| `--color-tag-bg` | `#E8E8E8` | Фон меток |
| `--color-text-secondary` | `#696969` | Вторичный текст новых экранов |
| `--color-link` | `#0068D7` | Интерактивный текст с контрастом AA |
| `--color-hover` | `#0079FF` | Фирменный синий акцент и фокус-контур |
| `--color-hover-bg` | `rgba(0, 121, 255, 0.08)` | Фон hover-состояния |
| `--color-muted` | `#8B8B8B` | Исходное значение сайта; не применять для мелкого текста новых экранов |

Примитивы объявлены в начале `:root`; семантические цвета ссылаются на них, а не дублируют значения:

| CSS-токен | Значение |
| --- | --- |
| `--palette-white` | `#FFFFFF` |
| `--palette-gray-50` / `--palette-gray-100` | `#F4F4F4` / `#E8E8E8` |
| `--palette-gray-400` / `--palette-gray-700` / `--palette-gray-900` | `#8B8B8B` / `#696969` / `#19191A` |
| `--palette-blue-500` / `--palette-blue-700` | `#0079FF` / `#0068D7` |
| `--palette-blue-500-08` | `rgba(0, 121, 255, 0.08)` |

Исходный `--color-muted` даёт контраст около 3.4:1 на белом, а синий `--color-hover` — около 4.1:1 для текста. Новые текстовые роли используют `--color-text-secondary` (около 5.5:1 на белом) и `--color-link` (около 5.3:1); оригинальная главная страница при этом остаётся без изменений.

## Типографика

Используйте `Golos Text` с весами 400, 500 и 600. Набор стилей уже подключён классами `.ds-intro`, `.ds-case__title`, `.ds-body-small` и `.ds-caption`.

| Роль | Размер | Межстрочный интервал |
| --- | --- | --- |
| Intro | `clamp(27px, 3vw, 33px)` | `1.32` |
| Заголовок кейса | `34px` | `1.55` |
| Основной текст | `16px` | `1.56` |
| Вторичный текст | `14px` | `1.56` |
| Подпись | `12px` | `1.4` |

## Отступы, радиусы и движение

`--space-1`…`--space-11` — шаги 4, 8, 12, 16, 24, 32, 40, 48, 62, 80 и 120 px. Применяйте их вместо новых разрозненных значений там, где это подходит композиции.

Основные радиусы: `--radius-control: 9999px`, `--radius-card: 24px`, `--radius-media: 16px`; на узком экране карточки используют `18px`, медиа — `12px`. Точки адаптации сохраняют текущие значения сайта: 900px, 640px и 390px.

Для переходов используйте `--motion-duration-*` и `--motion-ease-*`. При `prefers-reduced-motion: reduce` трансформации отключаются, а переходы сводятся к минимуму.

## Компоненты

- `.ds-action` — действие в форме ссылки или кнопки; hover и фокус показывают интерактивность. Для кнопки используйте нативный `disabled`; для ссылки с `aria-disabled="true"` также отключите активацию в обработчике.
- `.ds-tag` — короткая метка периода или категории.
- `.ds-card` — карточка проекта с заголовком, превью и описанием; интерактивный вариант использует `.ds-card--interactive`.
- `.ds-shot-card` — карточка отдельной работы или экрана. Подпись раскрывается при наведении и остаётся видимой на узких экранах.
- `.ds-case` и `.ds-case__*` — ширина и текстовые роли страницы кейса: заголовок, описание, факты, обложка и секции.
- `.ds-container` и `.ds-stack` — основные строительные блоки ширины и вертикального ритма.

Компоненты используют семантический HTML и видимый `:focus-visible`. Изображениям задавайте полезный `alt`; декоративным — пустой `alt` и `aria-hidden="true"`.

## Карта токенов Figma

Файл: [Aleks — Website Design System](https://www.figma.com/design/JDdwr6tCTr1LlcFIypbrcj).

| Имя Figma | CSS code syntax |
| --- | --- |
| `palette/white` | `var(--palette-white)` |
| `palette/gray/50` | `var(--palette-gray-50)` |
| `palette/gray/100` | `var(--palette-gray-100)` |
| `palette/gray/400` | `var(--palette-gray-400)` |
| `palette/gray/700` | `var(--palette-gray-700)` |
| `palette/gray/900` | `var(--palette-gray-900)` |
| `palette/blue/500` | `var(--palette-blue-500)` |
| `palette/blue/700` | `var(--palette-blue-700)` |
| `palette/blue/500-08` | `var(--palette-blue-500-08)` |
| `color/bg/page` | `var(--color-page-bg)` |
| `color/bg/card` | `var(--color-card-bg)` |
| `color/bg/tag` | `var(--color-tag-bg)` |
| `color/text/primary` | `var(--color-text)` |
| `color/text/secondary` | `var(--color-text-secondary)` |
| `color/text/muted-legacy` | `var(--color-muted)` |
| `color/interactive/accent` | `var(--color-hover)` |
| `color/interactive/text` | `var(--color-link)` |
| `color/interactive/hover-bg` | `var(--color-hover-bg)` |

Figma-файл содержит только светлую тему, как и сайт. Primitives скрыты из property pickers, semantic variables ссылаются на primitives, а spacing/radius и motion имеют WEB code syntax.

## Ограничения первой версии

- Главная страница и текущие кейсы не мигрированы на новые классы.
- Система рассчитана на статические HTML-экраны; интеграции с React/Storybook нет.
- Стили фокусируются на повторяемых паттернах портфолио, а не на форме или дашборде.
