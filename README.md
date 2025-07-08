<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Produkt-Rechner</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }
        
        .container {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            backdrop-filter: blur(10px);
        }
        
        h1 {
            text-align: center;
            color: #4a5568;
            margin-bottom: 30px;
            font-size: 2.5em;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }
        
        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .product-item {
            background: white;
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }
        
        .product-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.15);
            border-color: #667eea;
        }
        
        .product-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .product-name {
            font-weight: bold;
            color: #2d3748;
            font-size: 1.1em;
        }
        
        .product-price {
            color: #667eea;
            font-weight: bold;
            font-size: 1.2em;
        }
        
        .quantity-controls {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .quantity-btn {
            background: #667eea;
            color: white;
            border: none;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .quantity-btn:hover {
            background: #5a67d8;
            transform: scale(1.1);
        }
        
        .quantity-input {
            width: 60px;
            text-align: center;
            padding: 8px;
            border: 2px solid #e2e8f0;
            border-radius: 8px;
            font-size: 16px;
            font-weight: bold;
            color: #2d3748;
        }
        
        .quantity-input:focus {
            outline: none;
            border-color: #667eea;
        }
        
        .subtotal {
            text-align: right;
            margin-top: 10px;
            font-weight: bold;
            color: #2d3748;
            font-size: 1.1em;
        }
        
        .total-section {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            margin-top: 30px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }
        
        .total-amount {
            font-size: 2.5em;
            font-weight: bold;
            margin: 10px 0;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }
        
        .reset-btn {
            background: #e53e3e;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            margin-top: 20px;
            transition: all 0.3s ease;
        }
        
        .reset-btn:hover {
            background: #c53030;
            transform: scale(1.05);
        }
        
        .category-header {
            background: linear-gradient(135deg, #48bb78, #38a169);
            color: white;
            padding: 15px;
            border-radius: 10px;
            margin: 30px 0 20px 0;
            text-align: center;
            font-weight: bold;
            font-size: 1.2em;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🍹 Produkt-Rechner 🍹</h1>
        
        <div class="category-header">🍸 Cocktails & Drinks</div>
        <div class="product-grid">
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Bloody Mary</span>
                    <span class="product-price">25$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('bloody-mary', -1)">−</button>
                    <input type="number" class="quantity-input" id="bloody-mary" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('bloody-mary', 1)">+</button>
                </div>
                <div class="subtotal" id="bloody-mary-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Young Boy</span>
                    <span class="product-price">25$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('young-boy', -1)">−</button>
                    <input type="number" class="quantity-input" id="young-boy" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('young-boy', 1)">+</button>
                </div>
                <div class="subtotal" id="young-boy-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Sweating Girl</span>
                    <span class="product-price">25$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('sweating-girl', -1)">−</button>
                    <input type="number" class="quantity-input" id="sweating-girl" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('sweating-girl', 1)">+</button>
                </div>
                <div class="subtotal" id="sweating-girl-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Sex on the Beach</span>
                    <span class="product-price">25$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('sex-beach', -1)">−</button>
                    <input type="number" class="quantity-input" id="sex-beach" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('sex-beach', 1)">+</button>
                </div>
                <div class="subtotal" id="sex-beach-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Aperoli Spritz</span>
                    <span class="product-price">25$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('aperoli-spritz', -1)">−</button>
                    <input type="number" class="quantity-input" id="aperoli-spritz" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('aperoli-spritz', 1)">+</button>
                </div>
                <div class="subtotal" id="aperoli-spritz-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Fruity Baby</span>
                    <span class="product-price">25$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('fruity-baby', -1)">−</button>
                    <input type="number" class="quantity-input" id="fruity-baby" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('fruity-baby', 1)">+</button>
                </div>
                <div class="subtotal" id="fruity-baby-subtotal">0$</div>
            </div>
        </div>
        
        <div class="category-header">🥃 Spirituosen</div>
        <div class="product-grid">
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Vodka/Tequila/Gin</span>
                    <span class="product-price">15$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('vodka-tequila-gin', -1)">−</button>
                    <input type="number" class="quantity-input" id="vodka-tequila-gin" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('vodka-tequila-gin', 1)">+</button>
                </div>
                <div class="subtotal" id="vodka-tequila-gin-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Whisky/Likör/Cognac</span>
                    <span class="product-price">20$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('whisky-liquor-cognac', -1)">−</button>
                    <input type="number" class="quantity-input" id="whisky-liquor-cognac" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('whisky-liquor-cognac', 1)">+</button>
                </div>
                <div class="subtotal" id="whisky-liquor-cognac-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Bier</span>
                    <span class="product-price">10$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('bier', -1)">−</button>
                    <input type="number" class="quantity-input" id="bier" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('bier', 1)">+</button>
                </div>
                <div class="subtotal" id="bier-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Champagner</span>
                    <span class="product-price">500$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('champagner', -1)">−</button>
                    <input type="number" class="quantity-input" id="champagner" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('champagner', 1)">+</button>
                </div>
                <div class="subtotal" id="champagner-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Kiste Champagner</span>
                    <span class="product-price">2500$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('kiste-champagner', -1)">−</button>
                    <input type="number" class="quantity-input" id="kiste-champagner" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('kiste-champagner', 1)">+</button>
                </div>
                <div class="subtotal" id="kiste-champagner-subtotal">0$</div>
            </div>
        </div>
        
        <div class="category-header">🍽️ Essen</div>
        <div class="product-grid">
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Sportlunch</span>
                    <span class="product-price">20$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('sportlunch', -1)">−</button>
                    <input type="number" class="quantity-input" id="sportlunch" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('sportlunch', 1)">+</button>
                </div>
                <div class="subtotal" id="sportlunch-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Vegane Burger</span>
                    <span class="product-price">30$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('vegane-burger', -1)">−</button>
                    <input type="number" class="quantity-input" id="vegane-burger" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('vegane-burger', 1)">+</button>
                </div>
                <div class="subtotal" id="vegane-burger-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Gemüsepfanne</span>
                    <span class="product-price">40$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('gemuese-pfanne', -1)">−</button>
                    <input type="number" class="quantity-input" id="gemuese-pfanne" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('gemuese-pfanne', 1)">+</button>
                </div>
                <div class="subtotal" id="gemuese-pfanne-subtotal">0$</div>
            </div>
        </div>
        
        <div class="category-header">🥤 Getränke</div>
        <div class="product-grid">
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Biomilch</span>
                    <span class="product-price">17$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('biomilch', -1)">−</button>
                    <input type="number" class="quantity-input" id="biomilch" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('biomilch', 1)">+</button>
                </div>
                <div class="subtotal" id="biomilch-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Vita Iso Drink</span>
                    <span class="product-price">25$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('vita-iso-drink', -1)">−</button>
                    <input type="number" class="quantity-input" id="vita-iso-drink" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('vita-iso-drink', 1)">+</button>
                </div>
                <div class="subtotal" id="vita-iso-drink-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Vita Wasser</span>
                    <span class="product-price">15$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('vita-wasser', -1)">−</button>
                    <input type="number" class="quantity-input" id="vita-wasser" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('vita-wasser', 1)">+</button>
                </div>
                <div class="subtotal" id="vita-wasser-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Fruchtsaft</span>
                    <span class="product-price">17$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('fruchtsaft', -1)">−</button>
                    <input type="number" class="quantity-input" id="fruchtsaft" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('fruchtsaft', 1)">+</button>
                </div>
                <div class="subtotal" id="fruchtsaft-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Smoothie</span>
                    <span class="product-price">20$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('smoothie', -1)">−</button>
                    <input type="number" class="quantity-input" id="smoothie" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('smoothie', 1)">+</button>
                </div>
                <div class="subtotal" id="smoothie-subtotal">0$</div>
            </div>
            
            <div class="product-item">
                <div class="product-header">
                    <span class="product-name">Protein Shake</span>
                    <span class="product-price">20$</span>
                </div>
                <div class="quantity-controls">
                    <button class="quantity-btn" onclick="changeQuantity('protein-shake', -1)">−</button>
                    <input type="number" class="quantity-input" id="protein-shake" value="0" min="0" onchange="updateTotal()">
                    <button class="quantity-btn" onclick="changeQuantity('protein-shake', 1)">+</button>
                </div>
                <div class="subtotal" id="protein-shake-subtotal">0$</div>
            </div>
        </div>
        
        <div class="total-section">
            <h2>Gesamtsumme</h2>
            <div class="total-amount" id="total-amount">0$</div>
            <button class="reset-btn" onclick="resetAll()">Alles zurücksetzen</button>
        </div>
    </div>

    <script>
        const products = {
            'bloody-mary': 25,
            'young-boy': 25,
            'sweating-girl': 25,
            'sex-beach': 25,
            'aperoli-spritz': 25,
            'fruity-baby': 25,
            'vodka-tequila-gin': 15,
            'whisky-liquor-cognac': 20,
            'bier': 10,
            'champagner': 500,
            'kiste-champagner': 2500,
            'sportlunch': 20,
            'vegane-burger': 30,
            'gemuese-pfanne': 40,
            'biomilch': 17,
            'vita-iso-drink': 25,
            'vita-wasser': 15,
            'fruchtsaft': 17,
            'smoothie': 20,
            'protein-shake': 20
        };

        function changeQuantity(productId, change) {
            const input = document.getElementById(productId);
            const currentValue = parseInt(input.value) || 0;
            const newValue = Math.max(0, currentValue + change);
            input.value = newValue;
            updateTotal();
        }

        function updateTotal() {
            let total = 0;
            
            for (const [productId, price] of Object.entries(products)) {
                const quantity = parseInt(document.getElementById(productId).value) || 0;
                const subtotal = quantity * price;
                total += subtotal;
                
                document.getElementById(productId + '-subtotal').textContent = subtotal + '$';
            }
            
            document.getElementById('total-amount').textContent = total + '$';
        }

        function resetAll() {
            for (const productId of Object.keys(products)) {
                document.getElementById(productId).value = 0;
            }
            updateTotal();
        }

        // Initial update
        updateTotal();
    </script>
</body>
</html>
