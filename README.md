# CSS Flexbox

## Introduzione

CSS3 Flexbox è una modalità di layout che prevede la disposizione degli elementi in una pagina in modo **flessibile**. Introdotto nel 2015, Flexbox è ora supportato dal 97% dei browser.

### Perché Flexbox?

Prima di Flexbox, gli strumenti disponibili per creare layout erano:
- `display`
- `float`
- `position`
- `table` (alle origini del web)

Flexbox è stato progettato per sostituire tutti questi "hack" complicati con un sistema semplice, facile da usare e completo.

---

## Concetti Fondamentali

### Flex Container e Flex Item

Gli elementi che vogliamo disporre in modo flessibile devono essere contenuti in un **Flex-Container** (genitore).

```css
.container-flex {
    display: flex;
}
```

- I **figli diretti** del container diventano automaticamente **Flex-Item**
- ⚠️ Solo i figli diretti! Non i nipoti o altri discendenti
- Si possono annidare flex-container quando necessario

---

## Terminologia: Assi e Dimensioni

Flexbox utilizza un sistema di assi diverso dal modello tradizionale:

### Main Axis (Asse Principale)
L'asse lungo cui vengono disposti i Flex-Item. Può essere:
- Orizzontale (`flex-direction: row`)
- Verticale (`flex-direction: column`)

### Cross Axis (Asse Trasversale)
Perpendicolare al Main Axis.

### Dimensioni
- **Main Size**: dimensione lungo il Main Axis
- **Cross Size**: dimensione lungo il Cross Axis

```
flex-direction: row          flex-direction: column
┌─────────────────────┐      ┌──────────┐
│  MAIN AXIS →        │      │    ↓     │
│ ┌───┐ ┌───┐ ┌───┐   │      │  MAIN    │
│ │ 1 │ │ 2 │ │ 3 │   │      │  AXIS    │
│ └───┘ └───┘ └───┘   │      │          │
│         ↓           │      │ ← CROSS  │
│    CROSS AXIS       │      │   AXIS   │
└─────────────────────┘      └──────────┘
```

---

## Proprietà del Flex-Container

### 1. flex-direction

Definisce la direzione del Main Axis:

```css
flex-direction: row;            /* default - orizzontale da sinistra a destra */
flex-direction: row-reverse;    /* orizzontale da destra a sinistra */
flex-direction: column;         /* verticale dall'alto al basso */
flex-direction: column-reverse; /* verticale dal basso all'alto */
```

---

### 2. justify-content

Definisce come i Flex-Item sono disposti lungo il **Main Axis**.

```css
justify-content: flex-start;    /* all'inizio (default) */
justify-content: flex-end;      /* alla fine */
justify-content: center;        /* al centro */
justify-content: space-between; /* spazio tra gli elementi */
justify-content: space-around;  /* spazio attorno agli elementi */
```

**Esempio visivo (flex-direction: row):**

```
flex-start:       [1][2][3]___________
flex-end:         ___________[1][2][3]
center:           _____[1][2][3]______
space-between:    [1]_______[2]______[3]
space-around:     __[1]___[2]___[3]__
```

---

### 3. align-items

Definisce come i Flex-Item sono disposti lungo il **Cross Axis**.

```css
align-items: flex-start;  /* all'inizio del cross axis */
align-items: flex-end;    /* alla fine del cross axis */
align-items: center;      /* al centro del cross axis */
align-items: stretch;     /* si estende per riempire (default) */
align-items: baseline;    /* allineati alla baseline del testo */
```

**Esempio visivo (flex-direction: row):**

```
flex-start:    [1][2][3]
               ─────────

center:
               [1][2][3]

flex-end:      ─────────
               [1][2][3]

stretch:       ┌───┬───┬───┐
               │ 1 │ 2 │ 3 │
               └───┴───┴───┘
```

---

### 4. flex-wrap

Specifica se i Flex-Items devono disporsi su un'unica riga o su più righe quando eccedono lo spazio del container.

```css
flex-wrap: nowrap;        /* default - unica riga, no wrapping */
flex-wrap: wrap;          /* va a capo su più righe */
flex-wrap: wrap-reverse;  /* va a capo in ordine inverso */
```

---

## Comportamento Dinamico

### Cambio di Direzione

Quando si cambia `flex-direction`, tutto si adatta automaticamente:

- `justify-content` continua ad agire sul **Main Axis** (che ora è cambiato)
- `align-items` continua ad agire sul **Cross Axis** (che ora è cambiato)

**Esempio:**
```css
/* Orizzontale */
flex-direction: row;
justify-content: flex-end;  /* allinea a destra */

/* Verticale */
flex-direction: column;
justify-content: flex-end;  /* allinea in basso */
```

---

## Le 3 Novità Rivoluzionarie di Flexbox

1. **Disposizione flessibile**: Gli elementi possono essere disposti orizzontalmente o verticalmente
2. **Controllo della distribuzione**: La distribuzione può essere gestita sia orizzontalmente che verticalmente
3. **Dimensioni flessibili**: Gli elementi possono avere dimensioni che si adattano allo spazio disponibile

---

## Uso Pratico

Flexbox può essere utilizzato:
- Solo in alcune parti della pagina
- Dove serve davvero
- Continuando ad usare altri metodi CSS per il resto

Non è necessario convertire tutto il layout a Flexbox!

---

## Risorse Utili

📖 **Cheat sheet completo:**
[https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

---

## Schema Riassuntivo

```
FLEX-CONTAINER (genitore)
├── display: flex
├── flex-direction: row | column | row-reverse | column-reverse
├── justify-content: flex-start | flex-end | center | space-between | space-around
├── align-items: flex-start | flex-end | center | stretch | baseline
└── flex-wrap: nowrap | wrap | wrap-reverse

FLEX-ITEMS (figli diretti)
└── Diventano automaticamente flex-item
```

---

## Esempio Base

```html
<div class="container-flex">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
</div>
```

```css
.container-flex {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}
```

**Risultato:** Tre box centrati orizzontalmente e verticalmente nel container.

---

*Siamo arrivata alla pagine 26 delle slide*