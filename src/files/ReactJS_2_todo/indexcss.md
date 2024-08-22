.todo-container {
  width: 300px;
  margin: 50px auto;
  padding: 20px;
  border-radius: 8px;
  background-color: #f4f4f4;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 1.5em;
  margin-bottom: 20px;
  text-align: center;
  color: #333;
}

.input-container {
  display: flex;
  justify-content: space-between;
}

input[type="text"] {
  width: 70%;
  padding: 8px;
  font-size: 1em;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 8px 12px;
  font-size: 1em;
  color: white;
  background-color: #007bff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

ul {
  list-style-type: none;
  padding: 0;
  margin-top: 20px;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  border-bottom: 1px solid #ddd;
}

.todo-text {
  cursor: pointer;
}

.todo-text.completed {
  text-decoration: line-through;
  color: #aaa;
}

.delete-button {
  background: none;
  border: none;
  color: #d9534f;
  font-size: 1.2em;
  cursor: pointer;
}

.delete-button:hover {
  color: #c9302c;
}
