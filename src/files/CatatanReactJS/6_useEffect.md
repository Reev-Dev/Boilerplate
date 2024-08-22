import { useState, useEffect } from "react";

function FetchDataComponent() {
// State untuk menyimpan hasil fetch dan status pemuatan
const [fetchedData, setFetchedData] = useState(null);
const [isLoading, setIsLoading] = useState(true);

// Menggunakan useEffect untuk mengambil data ketika komponen dipasang (mounted)
useEffect(() => {
async function fetchData() {
try {
const response = await fetch(
"https://api.myquran.com/v2/sholat/kota/semua"
);
const result = await response.json();
setFetchedData(result); // Menyimpan data hasil fetch ke state
} catch (error) {
console.error("Error fetching data:", error);
} finally {
setIsLoading(false); // Set isLoading ke false setelah proses selesai
}
}

    fetchData(); // Memanggil fungsi fetchData

}, []); // Dependency array kosong [] agar useEffect hanya berjalan sekali

if (isLoading) {
return <p>Loading data, please wait...</p>;
}

return (
<div>
<h2>Fetched Data:</h2>
<pre>{JSON.stringify(fetchedData, null, 2)}</pre>
</div>
);
}

export default FetchDataComponent;
