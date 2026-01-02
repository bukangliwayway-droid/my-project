<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Food Costing Calculator</title>
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Ubuntu:wght@500&display=swap" rel="stylesheet">
<style>
    body {
        font-family: 'Roboto', sans-serif;
        background: #f5f7fa;
        margin: 0;
        padding: 20px;
        color: #333;
    }

    h1 {
        font-family: 'Ubuntu', sans-serif;
        text-align: center;
        color: #2c3e50;
        margin-bottom: 20px;
    }

    .container {
        max-width: 800px;
        margin: auto;
        background: #fff;
        padding: 25px;
        border-radius: 15px;
        box-shadow: 0 6px 10px rgba(0,0,0,0.1);
    }

    table {
        width: 100%;
        border-collapse: collapse;
        margin-bottom: 15px;
    }

    th, td {
        padding: 12px;
        text-align: center;
        border-bottom: 1px solid #ccc;
    }

    th {
        background-color: #3498db;
        color: #fff;
        font-weight: 600;
    }

    tr:nth-child(even) {
        background-color: #f2f2f2;
    }

    tr:hover {
        background-color: #d6eaf8;
    }

    input[type="text"], input[type="number"] {
        width: 90%;
        padding: 6px;
        border-radius: 5px;
        border: 1px solid #ccc;
        text-align: center;
    }

    button {
        padding: 10px 20px;
        margin: 5px;
        border: none;
        border-radius: 8px;
        cursor: pointer;
        font-weight: bold;
        transition: 0.3s;
    }

    button:hover {
        transform: translateY(-2px);
        box-shadow: 0 4px 6px rgba(0,0,0,0.2);
    }

    #addBtn { background-color: #2ecc71; color: white; }
    #resetBtn { background-color: #e74c3c; color: white; }

    label { display: block; margin: 15px 0; font-weight: 500; }
    #percentage { width: 100px; padding: 6px; border-radius: 5px; border: 1px solid #ccc; text-align: center; }

    p { font-size: 18px; font-weight: 500; }
    span { color: #e67e22; font-weight: 700; }
</style>
</head>
<body>

<div class="container">
    <h1>🍲 Food Costing Calculator</h1>

    <table id="costTable">
        <thead>
            <tr>
                <th>Ingredient</th>
                <th>Quantity</th>
                <th>Unit Cost</th>
                <th>Total</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td><input type="text" placeholder="Rice"></td>
                <td><input type="number" value="0" oninput="calculate()"></td>
                <td><input type="number" value="0" oninput="calculate()"></td>
                <td class="rowTotal">0.00</td>
            </tr>
        </tbody>
    </table>

    <button id="addBtn" onclick="addRow()">➕ Add Ingredient</button>

    <label>
        Percentage (+ / -):
        <input type="number" id="percentage" value="0" oninput="calculate()">
    </label>

    <p><strong>Total Cost:</strong> ₱ <span id="grandTotal">0.00</span></p>
    <p><strong>Adjusted Cost:</strong> ₱ <span id="adjustedTotal">0.00</span></p>

    <button id="resetBtn" onclick="resetCalculator()">♻ Reset</button>
</div>

<script>
function addRow() {
    const tbody = document.querySelector("#costTable tbody");
    const row = document.createElement("tr");
    row.innerHTML = `
        <td><input type="text" placeholder="Ingredient"></td>
        <td><input type="number" value="0" oninput="calculate()"></td>
        <td><input type="number" value="0" oninput="calculate()"></td>
        <td class="rowTotal">0.00</td>
    `;
    tbody.appendChild(row);
}

function calculate() {
    const rows = document.querySelectorAll("#costTable tbody tr");
    let grandTotal = 0;
    rows.forEach(row => {
        const qty = parseFloat(row.cells[1].querySelector("input").value) || 0;
        const unitCost = parseFloat(row.cells[2].querySelector("input").value) || 0;
        const rowTotal = qty * unitCost;
        row.cells[3].textContent = rowTotal.toFixed(2);
        grandTotal += rowTotal;
    });

    document.getElementById("grandTotal").textContent = grandTotal.toFixed(2);

    const percentage = parseFloat(document.getElementById("percentage").value) || 0;
    const adjustedTotal = grandTotal * (1 + percentage / 100);
    document.getElementById("adjustedTotal").textContent = adjustedTotal.toFixed(2);
}

function resetCalculator() {
    const rows = document.querySelectorAll("#costTable tbody tr");
    rows.forEach(row => {
        row.cells[0].querySelector("input").value = "";
        row.cells[1].querySelector("input").value = "0";
        row.cells[2].querySelector("input").value = "0";
        row.cells[3].textContent = "0.00";
    });
    document.getElementById("percentage").value = "0";
    document.getElementById("grandTotal").textContent = "0.00";
    document.getElementById("adjustedTotal").textContent = "0.00";
}
</script>

</body>
</html>
