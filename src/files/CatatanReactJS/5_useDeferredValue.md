import { useState, useDeferredValue } from "react";

// Membuat daftar item dengan jumlah 10.000
const largeItemList = Array.from(
{ length: 99 },
(\_, index) => `Product ${index + 1}`
);

function ItemSearch() {
const [query, setQuery] = useState("");
const deferredQuery = useDeferredValue(query);

// Memfilter item berdasarkan input yang tertunda (deferredQuery)
const matchingItems = largeItemList.filter((product) =>
product.toLowerCase().includes(deferredQuery.toLowerCase())
);

return (
<div>
<input
type="text"
value={query}
onChange={(e) => setQuery(e.target.value)}
placeholder="Search items..."
/>
<ul>
{matchingItems.map((product) => (
<li key={product}>{product}</li>
))}
</ul>
</div>
);
}

export default ItemSearch;
