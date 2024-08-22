import React, { useState } from 'react';

function Counter() {
// Menggunakan useState untuk mendefinisikan state 'count' dengan nilai awal 0
const [count, setCount] = useState(0);

// Fungsi untuk menambah nilai count ketika tombol ditekan
const increment = () => {
setCount(count + 1);
};

return (

<div>
<h1>Hitungan: {count}</h1>
{/_ Menambahkan onClick event handler yang memanggil fungsi increment _/}
<button onClick={increment}>Tambah</button>
</div>
);
}

export default Counter;
