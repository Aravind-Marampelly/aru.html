<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interest Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

        .container {
            width: 50%;
            margin: 50px auto;
            padding: 20px;
            background-color: white;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
        }

        h1 {
            text-align: center;
            color: #333;
        }

        label {
            font-size: 16px;
            display: block;
            margin: 10px 0 5px;
        }

        input[type="number"], input[type="button"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #f0f0f0;
            border-radius: 5px;
            font-size: 18px;
        }

        .button-container {
            display: flex;
            justify-content: space-between;
        }

        input[type="button"] {
            width: 48%;
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
            border: none;
        }

        input[type="button"]:hover {
            background-color: #45a049;
        }

        .reset-btn {
            background-color: #f44336;
        }

        .reset-btn:hover {
            background-color: #da190b;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Interest Calculator</h1>
    
    <!-- Input Form -->
    <label for="principal">Principal Amount (P):</label>
    <input type="number" id="principal" placeholder="Enter principal amount" required>

    <label for="rate">Interest Rate (R %):</label>
    <input type="number" id="rate" placeholder="Enter interest rate" required>

    <label for="time">Time Period (T in years):</label>
    <input type="number" id="time" placeholder="Enter time period in years" required>
    
    <!-- Buttons for calculation and reset -->
    <div class="button-container">
        <input type="button" value="Calculate Interest" onclick="calculateInterest()">
        <input type="button" class="reset-btn" value="Reset" onclick="resetFields()">
    </div>

    <!-- Result Section -->
    <div id="result" class="result"></div>
</div>

<script>
    // Function to calculate Simple Interest and Compound Interest
    function calculateInterest() {
        // Get the user input values
        const principal = parseFloat(document.getElementById('principal').value);
        const rate = parseFloat(document.getElementById('rate').value);
        const time = parseFloat(document.getElementById('time').value);

        if (isNaN(principal) || isNaN(rate) || isNaN(time)) {
            document.getElementById('result').innerHTML = "Please enter valid numbers for all fields.";
            return;
        }

        // Calculate Simple Interest (SI) and Compound Interest (CI)
        const simpleInterest = (principal * rate * time) / 100;
        const compoundInterest = principal * (Math.pow((1 + rate / 100), time)) - principal;

        // Display the results
        document.getElementById('result').innerHTML = `
            <strong>Simple Interest:</strong> ₹${simpleInterest.toFixed(2)}<br>
            <strong>Compound Interest:</strong> ₹${compoundInterest.toFixed(2)}
        `;
    }

    // Function to reset input fields
    function resetFields() {
        document.getElementById('principal').value = '';
        document.getElementById('rate').value = '';
        document.getElementById('time').value = '';
        document.getElementById('result').innerHTML = '';
    }
</script>

</body>
</html>
