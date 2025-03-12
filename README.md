<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PetShop</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #de65f6 0%, #8587fd 100%);
            color: #333;
            text-align: center;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 800px;
            margin: auto;
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        .product {
            border: 1px solid #ddd;
            padding: 15px;
            margin: 10px;
            background: white;
            border-radius: 10px;
        }
        .cart {
            margin-top: 20px;
            padding: 10px;
            border-top: 2px solid #000;
            background: white;
            border-radius: 10px;
        }
        button {
            background: #ff7e5f;
            color: white;
            border: none;
            padding: 10px 15px;
            cursor: pointer;
            border-radius: 5px;
        }
        button:hover {
            background: #e943c0;
        }
        input, select {
            display: block;
            width: 90%;
            margin: 10px auto;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ddd;
        }
    </style>
</head>
<body>


    <div class="container">
        <h2>Paw PetShop</h2>
        <div id="products">
            <div class="product" data-name="Makanan Kucing" data-price="50000">
                <h3>Makanan Kucing Premium</h3>
                <p>Harga: Rp50.000</p>
                <button onclick="addToCart(this)">Beli</button>
            </div>
            <div class="product" data-name="Pasir Kucing" data-price="30000">
                <h3>Pasir Kucing Wangi</h3>
                <p>Harga: Rp30.000</p>
                <button onclick="addToCart(this)">Beli</button>
            </div>
            <div class="product" data-name="Mainan Kucing" data-price="25000">
                <h3>Mainan Kucing Bola</h3>
                <p>Harga: Rp25.000</p>
                <button onclick="addToCart(this)">Beli</button>
            </div>
            <div class="product" data-name="Shampoo Kucing" data-price="40000">
                <h3>Shampoo Kucing Herbal</h3>
                <p>Harga: Rp40.000</p>
                <button onclick="addToCart(this)">Beli</button>
            </div>
            <div class="product" data-name="Obat kutu" data-price="20000">
                <h3>Obat kutu</h3>
                <p>Harga: Rp20.000</p>
                <button onclick="addToCart(this)">Beli</button>
            </div>
            <div class="product" data-name="baju Kucing" data-price="38000">
                <h3>baju Kucing</h3>
                <p>Harga: Rp38.000</p>
                <button onclick="addToCart(this)">Beli</button>
            </div>
            <div class="product" data-name="Obat Jamur" data-price="28000">
                <h3>Obat Jamur</h3>
                <p>Harga: Rp28.000</p>
                <button onclick="addToCart(this)">Beli</button>
            </div>
            <div class="product" data-name="sisir bulu" data-price="18000">
                <h3>sisir bulu</h3>
                <p>Harga: Rp18.000</p>
                <button onclick="addToCart(this)">Beli</button>
            </div>
        </div>
        
        <div class="cart">
            <h3>Keranjang Belanja</h3>
            <ul id="cart-list"></ul>
            <p>Total: Rp<span id="total-price">0</span></p>
            <h3>Data Pelanggan</h3>
            <form id="checkout-form">
                <input type="text" id="customer-name" placeholder="Nama" required>
                <input type="text" id="customer-address" placeholder="Alamat" required>
                <input type="tel" id="customer-phone" placeholder="Nomor Telepon" required>
                <input type="email" id="customer-email" placeholder="Alamat Email" required>
                <select id="payment-method" required>
                    <option value="">Pilih Metode Pembayaran</option>
                    <option value="transfer">Transfer Bank</option>
                    <option value="cod">Cash on Delivery (COD)</option>
                    <option value="ewallet">E-Wallet</option>
                </select>
                <button type="submit">Checkout</button>
            </form>
        </div>
    </div>

    <script>
        let cart = [];
        
        function addToCart(button) {
            let product = button.parentElement;
            let name = product.getAttribute('data-name');
            let price = parseInt(product.getAttribute('data-price'));
            cart.push({ name, price });
            updateCart();
        }
        
        function updateCart() {
            let cartList = document.getElementById("cart-list");
            let totalPrice = document.getElementById("total-price");
            cartList.innerHTML = "";
            let total = 0;
            cart.forEach(item => {
                let li = document.createElement("li");
                li.textContent = `${item.name} - Rp${item.price}`;
                cartList.appendChild(li);
                total += item.price;
            });
            totalPrice.textContent = total;
        }
        
        document.getElementById("checkout-form").addEventListener("submit", function(event) {
            event.preventDefault();
            let name = document.getElementById("customer-name").value;
            let address = document.getElementById("customer-address").value;
            let phone = document.getElementById("customer-phone").value;
            let email = document.getElementById("customer-email").value;
            let paymentMethod = document.getElementById("payment-method").value;
            
            if (!paymentMethod) {
                alert("Silakan pilih metode pembayaran.");
                return;
            }
            
            alert(`Pesanan atas nama ${name} akan dikirim ke ${address}.\nNomor Telepon: ${phone}\nEmail: ${email}\nMetode Pembayaran: ${paymentMethod}`);
            cart = [];
            updateCart();
        });
    </script>
</body>
</html>
