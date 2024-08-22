import React, { useState, useMemo } from 'react';

function ExpensiveComputation({ num }) {
  // Fungsi simulasi untuk menghitung nilai yang memakan waktu
  const compute = (num) => {
    console.log('Menghitung nilai...');
    return num * 2;
  };

  // Menggunakan useMemo untuk meng-cache hasil perhitungan
  const result = useMemo(() => compute(num), [num]);

  return (
    <div>
      <h1>Hasil: {result}</h1>
    </div>
  );
}

function App() {
  const [num, setNum] = useState(1);

  return (
    <div>
      <input
        type="number"
        value={num}
        onChange={(e) => setNum(parseInt(e.target.value))}
      />
      {/* Mengirim nilai num sebagai props ke ExpensiveComputation */}
      <ExpensiveComputation num={num} />
    </div>
  );
}

export default App;