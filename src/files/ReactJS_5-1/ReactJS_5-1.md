import React, { createContext, useState, useContext, useReducer } from 'react';

// 1. Membuat Tema Global: Context API untuk mengelola tema terang/gelap
const ThemeContext = createContext();

function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');

  const toggleTheme = () => {
    setTheme(theme === 'light' ? 'dark' : 'light');
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

function ThemedComponent() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  const style = {
    backgroundColor: theme === 'light' ? '#f4f4f4' : '#1e1e1e',
    color: theme === 'light' ? '#333' : '#f4f4f4',
    padding: '20px',
    textAlign: 'center',
    borderRadius: '8px',
    boxShadow: '0 4px 8px rgba(0, 0, 0, 0.1)',
    marginBottom: '20px',
  };

  return (
    <div style={style}>
      <h1>Tema Saat Ini: {theme}</h1>
      <button 
        onClick={toggleTheme}
        style={{
          padding: '10px 20px',
          fontSize: '16px',
          border: 'none',
          borderRadius: '4px',
          cursor: 'pointer',
          backgroundColor: theme === 'light' ? '#007bff' : '#4CAF50',
          color: '#fff',
        }}
      >
        Ganti Tema
      </button>
    </div>
  );
}

// 2. State Global Pengguna: Context API untuk mengelola state pengguna yang login
const UserContext = createContext();

function UserProvider({ children }) {
  const [user, setUser] = useState(null);

  const loginUser = (userData) => {
    setUser(userData);
  };

  const logoutUser = () => {
    setUser(null);
  };

  return (
    <UserContext.Provider value={{ user, loginUser, logoutUser }}>
      {children}
    </UserContext.Provider>
  );
}

function UserComponent() {
  const { user, loginUser, logoutUser } = useContext(UserContext);

  return (
    <div 
      style={{
        padding: '20px',
        textAlign: 'center',
        borderRadius: '8px',
        boxShadow: '0 4px 8px rgba(0, 0, 0, 0.1)',
        marginBottom: '20px',
        backgroundColor: '#f4f4f4',
        color: '#333'
      }}
    >
      {user ? (
        <>
          <h2>Selamat datang, {user.name}!</h2>
          <button 
            onClick={logoutUser}
            style={{
              padding: '10px 20px',
              fontSize: '16px',
              border: 'none',
              borderRadius: '4px',
              cursor: 'pointer',
              backgroundColor: '#dc3545',
              color: '#fff',
            }}
          >
            Logout
          </button>
        </>
      ) : (
        <button 
          onClick={() => loginUser({ name: 'Rifai' })}
          style={{
            padding: '10px 20px',
            fontSize: '16px',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer',
            backgroundColor: '#007bff',
            color: '#fff',
          }}
        >
          Login
        </button>
      )}
    </div>
  );
}

// 3. Counter dengan Context dan Reducer
const CounterContext = createContext();

function counterReducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    case 'reset':
      return { count: 0 };
    default:
      throw new Error(`Unhandled action type: ${action.type}`);
  }
}

function CounterProvider({ children }) {
  const [state, dispatch] = useReducer(counterReducer, { count: 0 });

  return (
    <CounterContext.Provider value={{ state, dispatch }}>
      {children}
    </CounterContext.Provider>
  );
}

function CounterComponent() {
  const { state, dispatch } = useContext(CounterContext);

  return (
    <div 
      style={{
        padding: '20px',
        textAlign: 'center',
        borderRadius: '8px',
        boxShadow: '0 4px 8px rgba(0, 0, 0, 0.1)',
        marginBottom: '20px',
        backgroundColor: '#f4f4f4',
        color: '#333'
      }}
    >
      <h1>Counter: {state.count}</h1>
      <div>
        <button 
          onClick={() => dispatch({ type: 'increment' })}
          style={{
            padding: '10px 20px',
            fontSize: '16px',
            margin: '5px',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer',
            backgroundColor: '#007bff',
            color: '#fff',
          }}
        >
          Increment
        </button>
        <button 
          onClick={() => dispatch({ type: 'decrement' })}
          style={{
            padding: '10px 20px',
            fontSize: '16px',
            margin: '5px',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer',
            backgroundColor: '#28a745',
            color: '#fff',
          }}
        >
          Decrement
        </button>
        <button 
          onClick={() => dispatch({ type: 'reset' })}
          style={{
            padding: '10px 20px',
            fontSize: '16px',
            margin: '5px',
            border: 'none',
            borderRadius: '4px',
            cursor: 'pointer',
            backgroundColor: '#dc3545',
            color: '#fff',
          }}
        >
          Reset
        </button>
      </div>
    </div>
  );
}

// Gabungkan semua fitur dalam satu App component
function App() {
  return (
    <ThemeProvider>
      <UserProvider>
        <CounterProvider>
          <ThemedComponent />
          <UserComponent />
          <CounterComponent />
        </CounterProvider>
      </UserProvider>
    </ThemeProvider>
  );
}

export default App;
