import React, { useState, useTransition } from 'react';

const itemList = Array.from({ length: 10000 }, (_, i) => `Item ${i + 1}`);

function SearchComponent() {
  const [input, setInput] = useState('');
  const [items, setItems] = useState(itemList);
  const [isPending, startTransition] = useTransition();

  const handleChange = (event) => {
    const value = event.target.value;
    setInput(value);

    // Membungkus pembaruan state dalam startTransition
    startTransition(() => {
      const filteredItems = itemList.filter(item =>
        item.toLowerCase().includes(value.toLowerCase())
      );
      setItems(filteredItems);
    });
  };

  return (
    <div>
      <input
        type="text"
        value={input}
        onChange={handleChange}
        placeholder="Search..."
      />
      {isPending ? <p>Loading...</p> : null}
      <ul>
        {items.map(item => (
          <li key={item}>{item}</li>
        ))}
      </ul>
    </div>
  );
}

export default SearchComponent;