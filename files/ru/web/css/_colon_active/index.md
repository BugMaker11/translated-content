---
title: :active
slug: Web/CSS/:active
---

{{CSSRef}}

[Псевдокласс](/ru/docs/Web/CSS/Pseudo-classes) **`:active`** соответствует элементу в момент, когда он активируется пользователем. Он позволяет странице среагировать, когда элемент активируется. Взаимодействие элемента с мышью - это, как правило, время между нажатием и отпусканием пользователем кнопки мыши.

```css
/*  Любой элемент <a>, который будет активирован */
a:active {
  color: red;
}
```

Псевдокласс `:active` чаще используется с элементами {{HTMLElement("a")}} и {{HTMLElement("button")}}, но может применяться и к другим элементам – например элементам форм.

Это свойство может быть переопределено любыми другими псевдоклассами, относящимся к ссылке, такими как {{cssxref(":link")}}, {{cssxref(":hover")}} и {{cssxref(":visited")}}, описанными в последующих правилах. Чтобы стилизировать нужные ссылки, вам нужно ставить правило `:active` после всех других правил, относящихся к ссылке, как определено правилом _LVHA-порядком_: `:link` — `:visited` — `:hover` — `:active`.

> [!NOTE]
> В системах с много-кнопочными мышами, CSS 3 указывает, что псевдокласс `:active` должен применяться только к первой кнопке; для праворуких мышей - это обычно самая левая кнопка.

## Синтаксис

{{csssyntax}}

## Пример

### Активные ссылки

#### HTML

```html
<p>
  Этот абзац содержит ссылку:
  <a href="#">Эта ссылка будет окрашена в красный, когда вы нажмёте на неё.</a>
  У абзаца фон станет серым при нажатии на него или на ссылку.
</p>
```

#### CSS

```css
/* Непосещённые ссылки */
a:link {
  color: blue;
}
/* Посещённые ссылки */
a:visited {
  color: purple;
}
/* Ссылки при наведении */
a:hover {
  background: yellow;
}
/* Активные ссылки */
a:active {
  color: red;
}

/* Активные абзацы */
p:active {
  background: #eee;
}
```

#### Результат

{{EmbedLiveSample('Активные_ссылки')}}

### Активные элементы формы

#### HTML

```html
<form>
  <label for="my-button">Моя кнопка: </label>
  <button id="my-button" type="button">
    Попробуй Нажать Меня или Мою подсказку!
  </button>
</form>
```

#### CSS

```css
form :active {
  color: red;
}

form button {
  background: white;
}
```

#### Result

{{EmbedLiveSample('Активные_элементы_формы')}}

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- Псевдоклассы, связанные с ссылками: {{cssxref(":link")}}, {{cssxref(":visited")}} и {{cssxref(":hover")}}.
