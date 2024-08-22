import React, { useContext } from 'react';

// Membuat konteks untuk tema dengan default 'light'
const ThemeContext = React.createContext('light');

function ThemedBox() {
// Menggunakan useContext untuk mendapatkan nilai dari ThemeContext
const currentTheme = useContext(ThemeContext);

// Menentukan gaya berdasarkan nilai tema dari context
const boxStyle = {
backgroundColor: currentTheme === 'light' ? '#ffffff' : '#222222',
color: currentTheme === 'light' ? '#000000' : '#eeeeee',
padding: '15px',
textAlign: 'center',
borderRadius: '5px'
};

return (
<div style={boxStyle}>
Active Theme: {currentTheme}
</div>
);
}

function App() {
return (
// Menyediakan nilai 'dark' untuk ThemeContext
<ThemeContext.Provider value="dark">
<ThemedBox />
</ThemeContext.Provider>
);
}

export default App;
