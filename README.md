<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Beverage App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f8f9fa;
        }
        header {
            background-color: #007bff;
            color: white;
            padding: 20px;
            text-align: center;
        }
        .container {
            padding: 20px;
        }
        .card {
            background: white;
            margin: 10px 0;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        .btn {
            display: inline-block;
            padding: 10px 15px;
            color: white;
            background-color: #007bff;
            border: none;
            border-radius: 5px;
            text-decoration: none;
            text-align: center;
            cursor: pointer;
        }
        .btn:hover {
            background-color: #0056b3;
        }
        .menu-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Event Beverage App</h1>
        <p>Purchase and pick up beverages seamlessly at your event!</p>
    </header>
    <div class="container">
        <div class="card">
            <h2>Purchase Beverages</h2>
            <div class="menu-item">
                <span>Beer - $5</span>
                <button class="btn">Add to Cart</button>
            </div>
            <div class="menu-item">
                <span>Wine - $8</span>
                <button class="btn">Add to Cart</button>
            </div>
            <div class="menu-item">
                <span>Soda - $3</span>
                <button class="btn">Add to Cart</button>
            </div>
        </div>

        <div class="card">
            <h2>Your Cart</h2>
            <p>No items in the cart yet.</p>
            <button class="btn">Checkout</button>
        </div>

        <div class="card">
            <h2>How It Works</h2>
            <ol>
                <li>Select beverages and add them to your cart.</li>
                <li>Complete your payment.</li>
                <li>Receive a QR Code for pickup.</li>
                <li>Present the QR Code at the event to get your drinks!</li>
            </ol>
        </div>
    </div>
</body>
</html>
