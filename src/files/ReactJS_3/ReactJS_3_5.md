import React, { useRef } from 'react';

function FocusInput() {
  // Membuat ref dengan useRef yang akan di-attach ke input
  const inputRef = useRef(null);

  // Fungsi untuk memfokuskan input ketika tombol ditekan
  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      {/* Menghubungkan ref dengan input */}
      <input ref={inputRef} type="text" />
      {/* Menambahkan onClick event handler untuk fokus pada input */}
      <button onClick={focusInput}>Fokuskan Input</button>
    </div>
  );
}

export default FocusInput;