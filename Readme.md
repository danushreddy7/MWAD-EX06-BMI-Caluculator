# Ex06 BMI Calculator
## Date:27-10-2025

## AIM:
To create a BMI calculator using React Router 

## ALGORITHM:
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM:

## App.jsx:
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const [height, setHeight] = useState("");
  const [weight, setWeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [message, setMessage] = useState("");
  const [unit, setUnit] = useState("metric");

  const calculateBMI = () => {
    if (!height || !weight || height <= 0 || weight <= 0) {
      setMessage("⚠️ Please enter valid height and weight values.");
      setBmi(null);
      return;
    }

    let bmiValue;
    if (unit === "metric") {
      const heightInMeters = height / 100;
      bmiValue = weight / (heightInMeters * heightInMeters);
    } else {
      bmiValue = (weight / (height * height)) * 703;
    }

    setBmi(bmiValue.toFixed(1));

    if (bmiValue < 18.5) setMessage("🟡 Underweight");
    else if (bmiValue < 24.9) setMessage("🟢 Normal weight");
    else if (bmiValue < 29.9) setMessage("🟠 Overweight");
    else setMessage("🔴 Obese");
  };

  const resetForm = () => {
    setHeight("");
    setWeight("");
    setBmi(null);
    setMessage("");
  };

  return (
    <div className="container">
      <h1 className="title">💪 BMI Calculator</h1>

      <div className="unit-toggle">
        <label>
          <input
            type="radio"
            value="metric"
            checked={unit === "metric"}
            onChange={() => setUnit("metric")}
          />{" "}
          Metric (kg/cm)
        </label>
        <label>
          <input
            type="radio"
            value="imperial"
            checked={unit === "imperial"}
            onChange={() => setUnit("imperial")}
          />{" "}
          Imperial (lbs/in)
        </label>
      </div>

      <div className="input-group">
        <label>Height ({unit === "metric" ? "cm" : "inches"})</label>
        <input
          type="number"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
          placeholder={`Enter height in ${unit === "metric" ? "cm" : "inches"}`}
        />

        <label>Weight ({unit === "metric" ? "kg" : "lbs"})</label>
        <input
          type="number"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
          placeholder={`Enter weight in ${unit === "metric" ? "kg" : "lbs"}`}
        />
      </div>

      <div className="button-group">
        <button onClick={calculateBMI} className="calculate-btn">
          Calculate
        </button>
        <button onClick={resetForm} className="reset-btn">
          Reset
        </button>
      </div>

      {bmi && (
        <div className="result-card">
          <h2>Your BMI: <span>{bmi}</span></h2>
          <p>{message}</p>
        </div>
      )}
    </div>
  );
}

export default App;
```
## App.css:
```
body {
  background: linear-gradient(135deg, #a8edea, #fed6e3);
  font-family: "Poppins", sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

.container {
  background: #ffffff;
  border-radius: 16px;
  box-shadow: 0 6px 30px rgba(0, 0, 0, 0.1);
  padding: 35px 25px;
  width: 360px;
  text-align: center;
  transition: 0.3s;
}

.title {
  color: #1f2937;
  margin-bottom: 20px;
  font-size: 28px;
  font-weight: 600;
}

.unit-toggle {
  display: flex;
  justify-content: center;
  gap: 15px;
  margin-bottom: 20px;
}

.unit-toggle label {
  font-size: 14px;
  color: #555;
  cursor: pointer;
}

.input-group {
  display: flex;
  flex-direction: column;
  text-align: left;
  margin-bottom: 20px;
}

.input-group label {
  margin-top: 10px;
  font-size: 14px;
  color: #333;
}

.input-group input {
  margin-top: 5px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 16px;
  transition: 0.2s;
}

.input-group input:focus {
  border-color: #4f46e5;
  outline: none;
}

.button-group {
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  font-size: 16px;
  transition: 0.3s ease;
  color: white;
}

.calculate-btn {
  background: #4f46e5;
}

.calculate-btn:hover {
  background: #4338ca;
  transform: scale(1.05);
}

.reset-btn {
  background: #ef4444;
}

.reset-btn:hover {
  background: #dc2626;
  transform: scale(1.05);
}

.result-card {
  background: #f9fafb;
  border-radius: 12px;
  padding: 20px;
  margin-top: 30px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.result-card h2 {
  margin: 0;
  color: #111827;
}

.result-card span {
  color: #2563eb;
  font-weight: 600;
}

.result-card p {
  margin-top: 10px;
  color: #444;
  font-weight: 500;
}
```
## OUTPUT:

<img width="1536" height="911" alt="image" src="https://github.com/user-attachments/assets/70f8713b-8541-4fd4-8a4c-2b6e8e9bc349" />


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
