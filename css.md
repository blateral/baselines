# CSS

## Struktur
Unser CSS in folgender Verzeichnisstruktur abgebildet:

```
|---css
    |---base
    |---layout
    |---modules
    |---components
    |---utils
```

### base
Im `base`-Verzeichnis ist Platz für Konfiguration, grundlegende Element-Styles z.B. `body` oder `html`

## Konventionen
Um skalierbare und vor allem wartbare Stylesheets zu schreiben, müssen folgende Konventionen eingehalten werden.

### Klassenbasierte Styles

```css
/* 👍 */
.my-element {
    prop: value,
    another-prop: value
}

/* 💩 */
#my-element {
    prop: value,
    another-prop: value
}

/* 💩 (Ausnahme: elements.scss) */
element {
    prop: value,
    another-prop: value
}
```

### Klassen im HTML
Um eine bessere Lesbarkeit im Markup zu gewährleisten, nutzen wir **zwei Leerzeichen** zwischen den Klassen:

```html
<div class="my-module  h-spacer  h-border"> ... </div>
```

Die Notation der Klassen erfolgt in der Reihenfolge, so wie diese im CSS spezifiziert sind. Dadurch kann die Verwendung der `!important`-Anweisung vermieden werden.

```html
<div class="module-a  module-b  ComponentA  h-helper-1  h-helper-2"> ... </div>
```

### Kein `!important`
Wenn es sich vermeiden lässt, benutzen wir keine `!important`-Anweisungen in Modulen und Komponenten.

**Ausnahme**: Helper und Utility-Klassen können `!important` einsetzen (sparsam, wenn's geht).

### Bennenung
Bei der Bennenung der Module, Komponenten und Helper gilt, so kurz wie möglich, dennoch so aussagekräftig wie möglich.

#### Layout
Layouts verwenden einen `.l-` Prefix.
```css
.l-header {}

.l-main {}

.l-footer {}
```

#### Module
Module werden klein geschrieben, Worte werden mit Trennstrichen getrennt:

```css
/* 👍 */
.module {}

/* 👍 */
.my-module {}

/* 💩 */
.Module {}

/* 💩 */
.My-Module {}

/* 💩 */
.MyModule {}
```

#### Komponenten
Komponenten werden groß geschrieben, Worte werden mit der camelCase-Schreibweise getrennt

```css
/* 👍 */
.Component {}

/* 👍 */
.AnotherComponent {}

/* 💩 */
.component {}

/* 💩 */
.Another-component {}
```

#### Helper und Utilities
Helper und Utilities verwenden einen `.h-`-Prefix.
```css
.h-visual-hidden {}

.h-border {}
```

#### Suffixe zur Kennzeichnung von Breakpoints
Ggf. können Helper oder Module nur ab bestimmten Breakpoints auftreten. Um die Benennung der Klassen eindeutig zu halten, nutzen wir `@`-Suffixe.
```css
.h-spacer {
    padding: 10px;
}

.h-spacer\@large {
    @media all and (min-width: 64em) {
        padding: 20px;
    }
}
```

```html
<div class="h-spacer"> ... </div>
<div class="h-spacer@large"> ... </div>
```

## BEM

## Sortierung von CSS-Properties

```css
.my-element {
    /* 1. Box Model */
    width: 200px;
    height: 200px;
    margin: 0;
    padding: 0;
    border: none;
    display: block;
    overflow: auto;
    box-sizing: border-box;

    /* 2. Position */
    position: relative;
    top: auto;
    left: auto;
    right: auto;
    bottom: auto;
    z-index: auto;
    transform: auto;
    vertical-align: middle;

    /* 3. Kosmetik */
    color: #333;
    background: #543efa;
    box-shadow: none;
    transition: all;
    animation: anim-name;

    /* 4. Typographie */
    font-family: sans-serif;
    font-size: 1em;
    font-weight: normal;
    font-style: normal;
    letter-spacing: normal;
    line-height: normal;
    text-align: left;
    text-transform: none;
    text-shadow: none;

    /* 5. Misc */
    will-change: transform;

}
```
