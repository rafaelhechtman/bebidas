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
        #cart ul {
            list-style-type: none;
            padding: 0;
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
                <button class="btn" onclick="addToCart('Cerveja')">Adicionar ao Carrinho</button>
            </div>
            <div class="menu-item">
                <span>Vinho - R$8</span>
                <button class="btn" onclick="addToCart('Vinho')">Adicionar ao Carrinho</button>
            </div>
            <div class="menu-item">
                <span>Refrigerante - R$3</span>
                <button class="btn" onclick="addToCart('Refrigerante')">Adicionar ao Carrinho</button>
            </div>
        </div>

        <div class="card">
            <h2>Seu Carrinho</h2>
            <div id="cart">
                <ul></ul>
            </div>
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
        const cartItems = {};

        function addToCart(item) {
            if (cartItems[item]) {
                cartItems[item]++;
            } else {
                cartItems[item] = 1;
            }
            updateCartView();
        }

        function updateCartView() {
            const cart = document.getElementById('cart').querySelector('ul');
            cart.innerHTML = '';
            Object.keys(cartItems).forEach(item => {
                const li = document.createElement('li');
                li.textContent = `${item} (${cartItems[item]})`;
                cart.appendChild(li);
            });
        }

        function finalizePurchase() {
    const qrCodeContainer = document.getElementById('qr-code');
    qrCodeContainer.innerHTML = '<h2>Seu QR Code</h2>';
    
    QRCode.toCanvas(
        qrCodeContainer,
        "Teste de QR Code",
        function (error, canvas) {
            if (error) {
                console.error(error);
                alert('Erro ao gerar o QR Code.');
                return;
            }
            qrCodeContainer.appendChild(canvas);
        }
    );
}

    );
            }

            const itemsList = Object.entries(cartItems)
                .map(([item, qty]) => `${item} (${qty})`)
                .join(', ');

            const qrCodeContainer = document.getElementById('qr-code');
            qrCodeContainer.innerHTML = '<h2>Seu QR Code</h2>';

            QRCode.toCanvas(
                qrCodeContainer,
                JSON.stringify({ itens: cartItems }),
                function (error, canvas) {
                    if (error) {
                        console.error(error);
                        alert('Erro ao gerar o QR Code.');
                        return;
                    }
                    qrCodeContainer.appendChild(canvas);
                }
            );

            alert('Compra finalizada! Escaneie o QR Code para ver os itens.');
        }
    </script>
</body>
</html>
