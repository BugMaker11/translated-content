---
title: Sintaxis
slug: Web/CSS/CSS_syntax/Syntax
original_slug: Web/CSS/Syntax
---

La meta básica del lenguaje Cascading Stylesheet (CSS) es permitir al motor del navegador pintar elementos de la página con características específicas, como colores, posición o decoración. La sintaxis CSS refleja estas metas y estos son los bloques básicos de construcción.

- La **propiedad** que es un identificador, un _nombre_ leíble por humanos, que define qué característica es considerada.
- El **valor** que describe como las características deben ser manejadas por el motor. Cada propiedad tiene un conjunto de valores válidos, definido por una gramática formal, así como un significado semántico, implementados por el motor del navegador.

## Declaraciones de CSS

Configurando propiedades CSS a valores específicos es la función principal del lenguaje del CSS. Una propiedad y su valor son llamados una d**eclaración**, y cualquier motor de CSS calcula qué declaraciones aplican a cada uno de los elementos de una página para mostralos apropiadamente y estilizarlos.

Ambos propiedades y valores son sensibles a mayúculas y minúsculas en CSS. El par se separa por dos puntos, '`:`' (`U+003A COLON`), y los espacios en blanco antes, entre ellos y después, pero no necesariamente dentro de ellos, son ignorados.

![css syntax - declaration.png](css_syntax_-_declaration.png)

Hay más de [100 propiedades diferentes](/es/docs/Web/CSS/Reference) en CSS y cerca de un número infinito de diferentes valores. No todos los pares de propiedades y valores son permitidos cada propiedad define que valores son válidos. Cuando un valor no es válido para una propiedad específica, la declaración es considerada _inválida_ y es completamente ignorada por el motor del CSS.

## Bloques de declaraciones en CSS

Las declaraciones son agrupadas en **bloques**, que es una estructura delimitada por una llave de apertura, '`{`' (`U+007B LEFT CURLY BRACKET`), y una de cierre, '`}`' (`U+007D RIGHT CURLY BRACKET`). Los bloques en ocasiones pueden anidarse, por lo que las llaves de apertura y cierre deben de coindidir.

![css syntax - block.png](css_syntax_-_block.png)

Esos bloques son naturalmente llamados **bloques de declaraciones** y las declaraciones dentro de ellos están separadas por un punto y coma, '`;`' (`U+003B SEMICOLON`). Un bloque de declaración puede estar vacío, que es contener una declaración nula. Los espacios en blanco alrededor de las declaraciones son ignorados. En cuanto a la última declaración de un bloque, esta no necesita terminar en un punto y coma, aunque es usualmente considerado una _buena práctica_ porque previene el olvidar agregarlo cuando se extienda el bloque con otra declaración.

![css syntax - declarations block.png](css_syntax_-_declarations_block.png)

> [!NOTE]
> El contenido de un bloque de declaración CSS, que es una lista de declaraciones separadas por un punto y coma, sin las llaves de apertura y cierre, pueden ser colocadas dentro del atributo `style de HTML`.

## Sets de reglas CSS

Si cada hoja de estilos pudiera aplicar una sola declaración a cada elemento de una página web, sería algo inútil. El verdadero objetivo es aplicar varias declaraciones a distintas partes del documento.

CSS permite esto asociando condiciones con bloques de declaraciones. Cada declaración (válida) es precedida por un _selector_, es decir, una condición que selecciona algunos elementos de la página. El bloque que forma el par selector-declaraciones recibe el nombre de **set de reglas**, o simplemente una **regla**.

![css syntax - ruleset.png](css_syntax_-_ruleset.png)

Debido a que un elemento de la página puede ser seleccionado por varios selectores, y, por lo tanto, por varias reglas que pueden contener la misma propiedad más de una vez, con diferentes valores, el estandar CSS define cuál regla tiene precedencia por sobre las otras y debe ser aplicada: esto se conoce como el algoritmo [cascada](/es/docs/Learn_web_development/Core/Styling_basics/Handling_conflicts).

> [!NOTE]
> Es importante resaltar que si un set de reglas formado por un grupo de selectores es un atajo que reemplaza varios sets de reglas con un solo selector cada una, esto no aplica a la validez del set de reglas en sí.
>
> Esto tiene una consecuencia importante: si algún selector básico es inválido, como cuando se usa un pseudo-elemento o pseudo-clase inválida, el _selector_ entero es inválido y, por lo tanto, el set de reglas completo es ignorado (por ser inválido también).

## Declaraciones CSS

Los sets de reglas son los bloques principales de una hoja de estilos, que generalmente consiste en una larga lista de ellos. Pero existe otro tipo de información que el autor web puede transmitir en la hoja de estilos, como el set de caracteres, otra hoja de estilos a importar, font face o listar descripciones de contador, entre otros. Se usarán tipos de declaracionnes específicas para esto mismo.

Una **declaración** es un bloque que empieza con un caracter (no espacio) y termina con la primer llave de cierre o punto y coma (fuera de una cadena, sin escape y no incluñido dentro de otro par de {}. () o \[]).

![css syntax - statements Venn diag.png](css_syntax_-_statements_venn_diag.png)

Existen dos tipos de declaraciones:

- **Sets de reglas** (o _reglas_) que, como lo visto, asocian una colección de declaraciones CSS a una condición descrita como selector.
- **Reglas At** que inician con un símbolo '`@`' (`U+0040 COMMERCIAL AT`), seguido de un identificador y luego el resto de la declaración que finaliza con un punto y coma (;) por fuera de un bloque o al inicio del próximo bloque. Cada tipo de [reglas at](/es/docs/Web/CSS/CSS_syntax/At-rule), definidas por un identificador, tienen su propia sintaxis interna, y semántica por supuesto. Se utilizan para establecer información de meta datos (como {{ cssxref("@charset") }} o {{ cssxref("@import") }}), información condicional (como {{ cssxref("@media") }} o {{ cssxref("@document") }}), o información descrciptiva (como {{ cssxref("@font-face") }}).

Toda declaración que no es un set de reglas ni una regla at es considerada inválida e ignorada.

Existe otro grupo de declaraciones: las **declaraciones anidadas**. Estas son declaraciones que pueden ser usadas en un subset específico de reglas at (las _reglas de grupo condicionales_). Estas declaraciones sólo aplican si una condición específica se cumple: el contenido de la regla at `@media` se aplica sólo si el dispositivo en el que el navegador se encuentra corriendo cumple dadas condiciones; el contenido de la regla at `@document` se aplica sólo si la página actual cumple dadas condiciones, y así. En CSS1 y CSS2.1, sólo los sets de reglas pueden ser usados dentro de reglas de grupo condicionales. Esto era muy restrictivo y se dejó de aplicar en [_CSS Conditionals Level 3_](/es/docs/Web/CSS/CSS_conditional_rules). Actualmente, aunque sigue siendo experimental y no es soportado por todos los navegadores, las reglas de grupo condicional pueden contener varios sets de reglas, e incluso, aunque no todas, reglas at.

## Ver también

- CSS Key Concepts: [CSS syntax](/es/docs/Web/CSS/CSS_syntax/Syntax), [at-rule](/es/docs/Web/CSS/CSS_syntax/At-rule), [comments](/es/docs/Web/CSS/CSS_syntax/Comments), [specificity](/es/docs/Web/CSS/CSS_cascade/Specificity) and [inheritance](/es/docs/Web/CSS/CSS_cascade/Inheritance), the [box](/es/docs/Web/CSS/CSS_box_model/Introduction_to_the_CSS_box_model), [layout modes](/es/docs/Glossary/Layout_mode) and [visual formatting models](/es/docs/Web/CSS/Visual_formatting_model), and [margin collapsing](/es/docs/Web/CSS/CSS_box_model/Mastering_margin_collapsing), or the [initial](/es/docs/Web/CSS/CSS_cascade/Value_processing), [computed](/es/docs/conflicting/Web/CSS/CSS_cascade/Value_processing_e3410028f0a698ddd9f74225ea8d122c0a582707d683fdd173e681e62003518d), [resolved](/es/docs/conflicting/Web/CSS/CSS_cascade/Value_processing_a47f4c6da6bce4fc52f8ed2ce27dc58e53fa5bd72bfef0bb04a61adbc5249cc4), [specified](/es/docs/conflicting/Web/CSS/CSS_cascade/Value_processing_8a702f25e61d14d8bd6ee6f7e88ca236512427b92b01a92c1d11f9edbb8f5fe1), [used](/es/docs/Web/CSS/used_value), and [actual](/es/docs/conflicting/Web/CSS/CSS_cascade/Value_processing) values. Definitions of [value syntax](/es/docs/Web/CSS/CSS_Values_and_Units/Value_definition_syntax), [shorthand properties](/es/docs/Web/CSS/CSS_cascade/Shorthand_properties) and [replaced elements](/es/docs/Web/CSS/CSS_images/Replaced_element_properties).
