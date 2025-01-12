<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplicativo de Bebidas</title>
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
        #qr-code {
            margin-top: 20px;
            text-align: center;
        }
    </style>
    <script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script>
</head>
<body>
    <header>
        <h1>Aplicativo de Bebidas</h1>
        <p>Compre e retire bebidas de forma rápida e prática no seu evento!</p>
    </header>
    <div class="container">
        <div class="card">
            <h2>Compre Bebidas</h2>
            <div class="menu-item">
                <span>Cerveja - R$5</span>
                <button class="btn" onclick="addToCart('Cerveja - R$5')">Adicionar ao Carrinho</button>
            </div>
            <div class="menu-item">
                <span>Vinho - R$8</span>
                <button class="btn" onclick="addToCart('Vinho - R$8')">Adicionar ao Carrinho</button>
            </div>
            <div class="menu-item">
                <span>Refrigerante - R$3</span>
                <button class="btn" onclick="addToCart('Refrigerante - R$3')">Adicionar ao Carrinho</button>
            </div>
        </div>

        <div class="card">
            <h2>Seu Carrinho</h2>
            <ul id="cart"></ul>
            <button class="btn" onclick="finalizePurchase()">Finalizar Compra</button>
        </div>

        <div class="card" id="qr-code">
            <!-- O QR Code será gerado aqui -->
        </div>

        <div class="card">
            <h2>Como Funciona</h2>
            <ol>
                <li>Selecione as bebidas e adicione ao carrinho.</li>
                <li>Complete o pagamento.</li>
                <li>Receba um QR Code para retirada.</li>
                <li>Apresente o QR Code no evento para retirar suas bebidas!</li>
            </ol>
        </div>
    </div>

    <script>
        const cartItems = [];

        function addToCart(item) {
            cartItems.push(item);
            updateCartView();
        }

        function updateCartView() {
            const cart = document.getElementById('cart');
            cart.innerHTML = '';
            cartItems.forEach((item, index) => {
                const li = document.createElement('li');
                li.textContent = item;
                cart.appendChild(li);
            });
        }

        function finalizePurchase() {
            if (cartItems.length === 0) {
                alert('Seu carrinho está vazio!');
                return;
            }

            const itemsList = cartItems.join(', ');
            const qrCodeContainer = document.getElementById('qr-code');
            qrCodeContainer.innerHTML = '<h2>Seu QR Code</h2>';

            QRCode.toCanvas(
                qrCodeContainer,
                `data:text/plain;charset=utf-8,Itens escolhidos: ${itemsList}`,
                function (error) {
                    if (error) console.error(error);
                }
            );

            alert('Compra finalizada! Escaneie o QR Code para ver os itens.');
        }
    </script>
</body>
</html>
