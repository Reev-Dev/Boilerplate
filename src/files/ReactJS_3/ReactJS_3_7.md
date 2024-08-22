import React, { useState, useCallback } from 'react';

function Button({ onClick, children }) {
  console.log('Button dirender');
  return <button onClick={onClick}>{children}</button>;
}

function Counter() {
  const [count, setCount] = useState(0);

  // Menggunakan useCallback untuk menghindari pembuatan ulang fungsi increment kecuali nilai count berubah
  const increment = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return (
    <div>
      <h1>Hitungan: {count}</h1>
      {/* Menggunakan Button dengan fungsi increment */}
      <Button onClick={increment}>Tambah</Button>
    </div>
  );
}

export default Counter;