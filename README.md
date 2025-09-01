Here’s the **README.md** as proper Markdown, Syam 👇

---

````markdown
# Looper 🚀  
A **lightweight JSON-driven JavaScript template engine** for building dynamic web pages with **no dependencies**.  

Looper is designed to be **fast**, **secure**, and **easy-to-use**. It lets you define your UI in JSON, preload variables, render instantly, and re-render only the parts that change.  

---

## ✨ Features
- **JSON-driven templates**: Define HTML structure in JSON.  
- **Preload / Render / Re-render** lifecycle:
  - **Preload** prepares templates and variables.  
  - **Render** inserts templates into the DOM.  
  - **Re-render** updates only changed variables/components.  
- **Nested Loops**: Repeat blocks for arrays (`$.items[...]`).  
- **Conditionals**: `{{if $.var}}...{{else}}...{{end}}`.  
- **Components**: Insert templates inside other templates with `{{componentName}}`.  
- **Auto Event Binding**: Use `data-onclick="eventName"`.  
- **Two-Way Data Binding**: Inputs sync directly with variables (`data-bind="varName"`).  
- **Live JSON Reload**: Fetches JSON periodically and updates the page automatically.  
- **Animations**: Smooth fade and collapse transitions on updates.  

---

## 📦 Installation
Simply include `index.html` and `site.json` in your project.  
No npm, no build system required — Looper runs in **plain JavaScript**.  

```html
<script src="looper.js"></script>
````

---

## 🛠 Usage

### **1. Create a JSON file**

Define templates and variables in `site.json`:

```json
{
  "templates": {
    "header": "<h1>$.title</h1><h3>$.tagline</h3>",
    "body": "<p>Edit tagline:</p><input type='text' data-bind='tagline'>",
    "footer": "<button data-onclick='toggle'>Toggle</button>"
  },
  "vars": {
    "title": "Coming Soon",
    "tagline": "Fast. Secure. Dynamic."
  }
}
```

---

### **2. Load JSON and Render**

```js
Looper.loadFromJSON("site.json", 5000); // reload every 5s
```

---

### **3. Handle Events**

```js
Looper.events = {
  toggle: () => {
    Looper.rerender({ tagline: "Toggled!" });
  }
};
```

---

### **4. Loops Example**

```json
"menu": "<ul>$.menuItems[<li><a href='$.url'>$.label</a></li>]</ul>"
```

```json
"vars": {
  "menuItems": [
    { "label": "Home", "url": "/" },
    { "label": "About", "url": "/about" }
  ]
}
```

---

### **5. Conditionals Example**

```json
"body": "{{if $.loggedIn}}<p>Welcome!</p>{{else}}<p>Please login</p>{{end}}"
```

---

### **6. Components Example**

```json
"body": "<div>{{header}}</div>"
```

---

## 🎨 Animations

* **Fade updates** when content changes.
* **Collapsible sections** (like Features) slide open/closed smoothly.

---

## 🔒 Security

* Variables are **escaped by default**.
* Use `__HTML__<raw>` if you want safe HTML injection.

---

## 🚀 Roadmap

* [x] JSON-driven rendering
* [x] Nested loops
* [x] Conditionals & components
* [x] Auto event binding
* [x] Two-way data binding
* [x] Live JSON reload
* [x] Collapse animations
* [ ] WebSocket real-time sync
* [ ] State persistence across reloads
* [ ] Plugin system

---

## 📜 License

MIT License – Free to use, modify, and distribute.

```
