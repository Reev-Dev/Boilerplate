import React, { useState, useEffect } from 'react';

// Custom Hook untuk fetch data
function useFetch(url) {
  // State untuk menyimpan data yang di-fetch dan status loading
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch(url)
      .then(response => response.json())
      .then(data => {
        setData(data);
        setLoading(false); // Set loading ke false setelah data berhasil di-fetch
      });
  }, [url]); // Array dependency berisi url agar fetch dijalankan setiap kali url berubah

  return { data, loading };
}

function App() {
  // Menggunakan custom hook useFetch untuk fetch data dari API
  const { data, loading } = useFetch('https://api.example.com/data');

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

export default App;