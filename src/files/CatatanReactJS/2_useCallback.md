import { useState, useCallback } from 'react';

// Komponen Button dengan properti onClick dan children
function Button({ handleClick, label }) {
console.log('Button is rendered');
return <button onClick={handleClick}>{label}</button>;
}

function Counter() {
const [count, setCount] = useState(0);

// Menggunakan useCallback untuk menyimpan fungsi yang sama kecuali nilai count berubah
const increment = useCallback(() => {
setCount(prevCount => prevCount + 1);
}, []);

return (

<div>
<p>Current Count: {count}</p>
{/\*_ Menggunakan Button dengan fungsi increment _/}
<Button handleClick={increment} label="Increase" />
</div>
);
}

export default Counter;
