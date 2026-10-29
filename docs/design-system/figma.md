# Figma

## Файл и страницы

- [Aleks — Website Design System](https://www.figma.com/design/JDdwr6tCTr1LlcFIypbrcj) — основная Design-библиотека.
- [FigJam-карта связей](https://www.figma.com/board/aD8A7V1A8gdlErnokiHgBC) — визуальная карта основ, компонентов, CSS и Figma.

Design-файл содержит страницы `00 — Start here`, `01 — Foundations` и `02 — Components`. На странице компонентов находятся варианты Action и Tag, а также Project Card, Shot Card и Case Study.

## Foundations

Файл содержит коллекции переменных `Primitives`, `Color`, `Spacing & Shape` и `Motion`, а также стили текста Golos Text. Названия semantic variables соответствуют CSS-переменным. Например, Figma `color/text/secondary` соотносится с `--color-text-secondary`.

| Коллекция | Содержимое |
| --- | --- |
| `Primitives` | Базовая палитра. |
| `Color` | Семантические цвета и aliases на primitives. |
| `Spacing & Shape` | Шкала отступов, радиусы и ширины. |
| `Motion` | Длительности и кривые переходов. |

Библиотека соответствует светлой теме сайта. Вторичные текстовые роли для новых экранов контрастнее legacy muted и синего акцента.

В первой версии foundation-токены и компоненты заведены как отдельные ресурсы; заливки компонентов пока не привязаны к variables. При изменении токенов обновляйте экземпляры компонентов и CSS одновременно.

## Связь с кодом

| Figma | Код |
| --- | --- |
| Variables | CSS custom properties в `assets/design-system.css`. |
| `Action` | `.ds-action` |
| `Tag` | `.ds-tag` |
| `Project Card` | `.ds-card` |
| `Shot Card` | `.ds-shot-card` |
| `Case Study` | `.ds-case` и `.ds-case__*` |

Code Connect на Starter недоступен, поэтому соответствия компонентов документированы здесь и в [`DESIGN_SYSTEM.md`](../../DESIGN_SYSTEM.md). При использовании компонентов сверяйтесь с CSS-классами и именами переменных вручную.
