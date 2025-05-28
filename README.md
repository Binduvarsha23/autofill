
```
# 🔍 Autofill Search Input with LRU Cache

This is a React application built using Vite that implements an intelligent autofill (autocomplete) input. It filters suggestions based on user input, optimizes performance with an LRU cache, and highlights matched text.

## 🚀 Live Demo

🌐 [Live Project](https://binduvarsha23.github.io/autofill/)

## ✨ Features

- 🔎 **Real-time filtering** based on user input
- ⌛ **Debounced input** (300ms delay) to reduce unnecessary processing
- 💾 **LRU Cache** that stores up to 10 recent queries for performance
- ✨ **Matched substring highlighting** in bold
- ✅ **Accessible and responsive UI** with Bootstrap 5

## 📁 Project Structure

```

src/
│
├── components/
│   └── AutoComplete.jsx      # Main autocomplete component
│
├── utils/
│   └── LRUCache.js           # LRU cache class implementation
│
├── dummy.json                # Static dummy data for suggestions
└── App.jsx / main.jsx        # Root component and entry point

````

## 🔧 Getting Started

### Prerequisites

- Node.js (v20.6)
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/Binduvarsha23/autofill.git
cd autofill

# Install dependencies
npm install

# Start the development server
npm run dev
````

## 🧠 How It Works

### LRU Cache

The LRU Cache stores up to 10 recent query results using JavaScript’s `Map` to maintain insertion order.

```js
const cache = new LRUCache(10);
const cachedResults = cache.get(query);
if (!cachedResults) {
  const results = filterData(query);
  cache.set(query, results);
}
```

### Debounced Filtering

A `setTimeout` is used in `useEffect` to debounce user input, waiting 300ms before filtering.

### Match Highlighting

The matched portion of each suggestion is rendered in `<strong>` tags to emphasize the match.

```js
const highlightMatch = (text, query) => {
  const regex = new RegExp(`(${query})`, 'gi');
  return text.split(regex).map((part, index) =>
    regex.test(part) ? <strong key={index}>{part}</strong> : part
  );
};
```

## 📊 Example Data (`dummy.json`)

```json
[
  { "id": 1, "name": "React Tutorials" },
  { "id": 2, "name": "React Query" },
  { "id": 3, "name": "React Redux" }
]
```
