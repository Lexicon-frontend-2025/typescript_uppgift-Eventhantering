# 💻 Övning: Eventhantering i TS

## 🧩 Uppgifter

---

### 1. Enkel Knapp

**Uppgift:**  
Skapa en HTML-knapp:

```html
<button id="my-btn">Klicka mig!</button>
````

**I TypeScript:**

* Hämta knappen via `document.getElementById`
* Lägg till en `click`-händelselyssnare
* När knappen klickas, skriv ut:
  `"Knappen klickades!"` i konsolen

<details>
<summary>💡 Lösningsförslag</summary>

```ts
const button = document.getElementById("my-btn") as HTMLButtonElement;

button.addEventListener("click", () => {
  console.log("Knappen klickades!");
});
```

</details>

---

### 2. Växla Klass

**HTML:**

```html
<div id="toggle-box" class="box"></div>
<button id="toggle-btn">Växla färg</button>
```

**CSS:**

```css
.box {
  width: 100px;
  height: 100px;
  background-color: lightblue;
}

.highlight {
  background-color: lightgreen;
}
```

**I TypeScript:**

* När knappen klickas:

  * Använd `classList.toggle("highlight")` på `<div>` med id `toggle-box`

<details>
<summary>💡 Lösningsförslag</summary>

```ts
const toggleBox = document.getElementById("toggle-box") as HTMLDivElement;
const toggleBtn = document.getElementById("toggle-btn") as HTMLButtonElement;

toggleBtn.addEventListener("click", () => {
  toggleBox.classList.toggle("highlight");
});
```

</details>

---

### 3. Textfält med Uppdatering

**HTML:**

```html
<input type="text" id="text-input" placeholder="Skriv något...">
<p id="display-text">Här visas texten...</p>
```

**I TypeScript:**

* Lägg till en `input`-lyssnare på textfältet
* När användaren skriver, uppdatera `textContent` i `<p>` med `event.target.value`

<details>
<summary>💡 Lösningsförslag</summary>

```ts
const input = document.getElementById("text-input") as HTMLInputElement;
const display = document.getElementById("display-text") as HTMLParagraphElement;

input.addEventListener("input", (event) => {
  const target = event.target as HTMLInputElement;
  display.textContent = target.value;
});
```

</details>

---

### 4. Dynamisk Lista med Knapp

**Förutsättning:**
Du har en array av studentobjekt, t.ex.:

```ts
type Student = {
  name: string;
  age: number;
};

let students: Student[] = [
  { name: "Alice", age: 20 },
  { name: "Bob", age: 22 }
];
```

**HTML:**

```html
<ul id="student-list"></ul>
<button id="add-student-btn">Lägg till ny student</button>
```

**I TypeScript:**

* När knappen klickas:

  * Lägg till ett nytt (hårdkodat) studentobjekt i arrayen
  * Rensa och rendera listan på nytt i DOM med t.ex. `map()`

<details>
<summary>💡 Lösningsförslag</summary>

```ts
const list = document.getElementById("student-list") as HTMLUListElement;
const addBtn = document.getElementById("add-student-btn") as HTMLButtonElement;

function renderList() {
  list.innerHTML = "";
  students.forEach((student) => {
    const li = document.createElement("li");
    li.textContent = `${student.name}, ${student.age} år`;
    list.appendChild(li);
  });
}

addBtn.addEventListener("click", () => {
  const newStudent: Student = { name: "Charlie", age: 23 };
  students.push(newStudent);
  renderList();
});

renderList();
```

</details>
