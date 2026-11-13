# EXP 15 – Fetch Student Details Using Axios in React

**NAME:** Nithya T  
**REG NO:** 2305001023

## Aim

To develop a React application using Axios to send a GET request to a REST API, retrieve student information in JSON format, and display the details when the user clicks the View Details button.

## Objectives

1. To understand Axios and its usage in React applications.
2. To install and configure the Axios library.
3. To perform GET requests using Axios.
4. To retrieve and display API data using React state.
5. To handle loading and error messages during API requests.

## Program

### Step 1: Create a React Project

```bash
npm create vite@latest student-axios
cd student-axios
npm install
npm install axios
npm run dev
```

### Step 2: App.jsx

```jsx
import { useState } from "react";
import axios from "axios";
import "./App.css";

function App() {
  const [student, setStudent] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  async function getStudentDetails() {
    setLoading(true);
    setError("");
    setStudent(null);

    try {
      const response = await axios.get(
        "https://jsonplaceholder.typicode.com/users/1"
      );

      setStudent({
        id: response.data.id,
        name: "Nithya T",
        email: "nithya@gmail.com",
        city: response.data.address.city
      });

    } catch (err) {
      setError("Unable to fetch student details. Try again.");
    } finally {
      setLoading(false);
    }
  }

  return (
    <div className="container">
      <h1>Nithya's Student Management System</h1>

      <p>Click below to view student details.</p>

      <button onClick={getStudentDetails} disabled={loading}>
        {loading ? "Loading..." : "View Details"}
      </button>

      {loading && <p>Fetching student data...</p>}

      {error && <p className="error">{error}</p>}

      {student && (
        <div className="student-card">
          <h2>Student Details</h2>
          <p><strong>ID:</strong> {student.id}</p>
          <p><strong>Name:</strong> {student.name}</p>
          <p><strong>Email:</strong> {student.email}</p>
          <p><strong>City:</strong> {student.city}</p>
        </div>
      )}
    </div>
  );
}

export default App;
```

### Step 3: App.css

```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f1f5f9;
}

.container {
  max-width: 600px;
  margin: 60px auto;
  padding: 25px;
  text-align: center;
  background: white;
  border-radius: 12px;
}

h1 {
  color: #1d4ed8;
}

button {
  padding: 12px 22px;
  background: #2563eb;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
}

button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

.student-card {
  margin-top: 25px;
  padding: 20px;
  text-align: left;
  background: #dbeafe;
  border-radius: 8px;
}

.error {
  color: red;
}
```

## Output

<img width="483" height="326" alt="image" src="https://github.com/user-attachments/assets/58a4b76c-e6d7-406e-a125-8fa12d28e7d5" />


## Result

Thus, a React application was successfully developed using Axios to send a GET request to a REST API and retrieve and display student information dynamically.
