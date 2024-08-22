import React, { useState, useEffect } from 'react';
import { useSyncExternalStore } from 'react';

// Fungsi untuk meng-subscribe perubahan dari store eksternal
function subscribeToStore(callback) {
  // Misalnya store eksternal adalah objek sederhana
  const store = { value: 42 };

  // Callback akan dipanggil ketika store berubah
  const unsubscribe = () => {
    // Logika untuk berhenti mendengarkan perubahan
  };

  return unsubscribe;
}

// Fungsi untuk mendapatkan nilai terbaru dari store
function getStoreSnapshot() {
  return store.value; // Misalnya store adalah objek global
}

function MyComponent() {
  // Menggunakan useSyncExternalStore untuk mendapatkan nilai sinkron dari store
  const storeValue = useSyncExternalStore(subscribeToStore, getStoreSnapshot);

  return (
    <div>
      <p>Store Value: {storeValue}</p>
    </div>
  );
}

export default MyComponent;