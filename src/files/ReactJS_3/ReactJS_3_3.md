import React, { useState, useEffect } from 'react';

function DataFetcher() {
  // State untuk menyimpan data yang di-fetch dan status loading
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  // Menggunakan useEffect untuk fetch data ketika komponen dimounting
  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => {
        setData(data);
        setLoading(false); // Set loading ke false setelah data berhasil di-fetch
      });
  }, []); // Array kosong [] sebagai dependency array agar effect hanya berjalan sekali

  if (loading) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      <h1>Data yang di-fetch:</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

export default DataFetcher;