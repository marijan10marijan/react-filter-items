# How to build a search bar in React

### A search bar is a great way to make content on your website discoverable. In this tutorial, we’ll be building an accessible search bar component using React.

### In this project, I write all the code in one component because the project is for learning purposes.

## Code:

```javascript
import { useRef, useState } from "react";

function App() {
  const [items, setItems] = useState([]);
  const [query, setQuery] = useState("");
  const input = useRef();

  const addItem = (e) => {
    e.preventDefault();
    const inputValue = input.current.value;
    setItems((prev) => {
      return [...prev, inputValue];
    });
    input.current.value = "";
  };

  const filteredItems = items.filter((item) => {
    return item.toLowerCase().includes(query.toLowerCase());
  });

  return (
    <div className="App">
      <h1>My Application</h1>
      <input
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        type="text"
        placeholder="search items"
      />
      <form onSubmit={addItem}>
        <input ref={input} type="text" placeholder="your item" />
        <button type="submit">Add Item</button>
      </form>
      <h1 className="items">Items: </h1>
      <div className="items-list">
        {filteredItems.map((item, index) => (
          <h2 key={index}>{item}</h2>
        ))}
      </div>
    </div>
  );
}

export default App;
```
