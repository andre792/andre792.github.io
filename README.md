<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galeria de Produtos - Yuan para Euro</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --bg-primary: #0f0f23;
            --bg-secondary: #1a1a2e;
            --bg-card: #16213e;
            --text-primary: #e2e2e2;
            --text-secondary: #a0a0a0;
            --accent-primary: #6a11cb;
            --accent-secondary: #2575fc;
            --price-yuan: #ff6b6b;
            --price-euro: #4ecdc4;
            --border-color: #2d2d4d;
            --shadow: rgba(0, 0, 0, 0.3);
        }
        
        body {
            background: linear-gradient(135deg, var(--bg-primary) 0%, var(--bg-secondary) 100%);
            min-height: 100vh;
            padding: 20px;
            color: var(--text-primary);
        }
        
        .container {
            background-color: var(--bg-card);
            border-radius: 15px;
            box-shadow: 0 10px 30px var(--shadow);
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 30px;
            text-align: center;
            border: 1px solid var(--border-color);
        }
        
        h1 {
            color: var(--text-primary);
            margin-bottom: 20px;
            font-weight: 600;
            background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .tabs {
            display: flex;
            margin-bottom: 30px;
            border-bottom: 1px solid var(--border-color);
        }
        
        .tab {
            padding: 12px 25px;
            background: none;
            border: none;
            font-size: 16px;
            font-weight: 500;
            cursor: pointer;
            color: var(--text-secondary);
            transition: all 0.3s;
            border-bottom: 3px solid transparent;
        }
        
        .tab.active {
            color: var(--accent-primary);
            border-bottom: 3px solid var(--accent-primary);
        }
        
        .tab:hover {
            color: var(--text-primary);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        .form-group {
            margin-bottom: 20px;
            text-align: left;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--text-primary);
        }
        
        input[type="text"], input[type="url"], input[type="number"] {
            width: 100%;
            padding: 12px 15px;
            background-color: var(--bg-secondary);
            border: 2px solid var(--border-color);
            border-radius: 8px;
            font-size: 16px;
            transition: all 0.3s;
            color: var(--text-primary);
        }
        
        input[type="text"]:focus, input[type="url"]:focus, input[type="number"]:focus {
            border-color: var(--accent-primary);
            outline: none;
            box-shadow: 0 0 0 2px rgba(106, 17, 203, 0.2);
        }
        
        input::placeholder {
            color: var(--text-secondary);
        }
        
        .preview-container {
            margin: 30px 0;
            padding: 20px;
            border: 2px dashed var(--border-color);
            border-radius: 10px;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            transition: border-color 0.3s;
            background-color: var(--bg-secondary);
        }
        
        .preview-container:hover {
            border-color: var(--accent-primary);
        }
        
        #imagePreview {
            max-width: 100%;
            max-height: 300px;
            border-radius: 8px;
            box-shadow: 0 4px 10px var(--shadow);
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        #imagePreview:hover {
            transform: scale(1.02);
            box-shadow: 0 6px 15px var(--shadow);
        }
        
        .placeholder-text {
            color: var(--text-secondary);
            font-style: italic;
        }
        
        .buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        
        button {
            flex: 1;
            padding: 12px 20px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        #addBtn {
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            color: white;
        }
        
        #addBtn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(106, 17, 203, 0.4);
        }
        
        #resetBtn {
            background-color: var(--bg-secondary);
            color: var(--text-primary);
            border: 1px solid var(--border-color);
        }
        
        #resetBtn:hover {
            background-color: var(--border-color);
        }
        
        .instructions {
            margin-top: 25px;
            padding: 15px;
            background-color: var(--bg-secondary);
            border-radius: 8px;
            text-align: left;
            font-size: 14px;
            color: var(--text-secondary);
            border: 1px solid var(--border-color);
        }
        
        .instructions h3 {
            margin-bottom: 10px;
            color: var(--text-primary);
        }
        
        .instructions ul {
            padding-left: 20px;
        }
        
        .instructions li {
            margin-bottom: 8px;
        }
        
        /* Estilos para a galeria */
        .gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .gallery-item {
            background-color: var(--bg-card);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 10px var(--shadow);
            transition: transform 0.3s, box-shadow 0.3s;
            display: flex;
            flex-direction: column;
            border: 1px solid var(--border-color);
        }
        
        .gallery-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px var(--shadow);
            border-color: var(--accent-primary);
        }
        
        .gallery-image {
            width: 100%;
            height: 180px;
            object-fit: cover;
            cursor: pointer;
        }
        
        .gallery-info {
            padding: 15px;
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }
        
        .gallery-title {
            font-weight: 500;
            color: var(--text-primary);
            margin-bottom: 12px;
            font-size: 16px;
            min-height: 40px;
        }
        
        .gallery-price {
            font-size: 18px;
            font-weight: 600;
            color: var(--price-yuan);
            margin-bottom: 5px;
        }
        
        .gallery-conversion {
            font-size: 14px;
            color: var(--price-euro);
            margin-bottom: 15px;
            font-weight: 500;
        }
        
        .empty-gallery {
            grid-column: 1 / -1;
            padding: 40px;
            text-align: center;
            color: var(--text-secondary);
            font-style: italic;
        }
        
        .delete-btn {
            background-color: #ff4757;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 8px 12px;
            cursor: pointer;
            margin-top: auto;
            font-size: 14px;
            transition: background-color 0.3s;
        }
        
        .delete-btn:hover {
            background-color: #ff3742;
        }
        
        .price-input-container {
            position: relative;
        }
        
        .currency-symbol {
            position: absolute;
            left: 12px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-secondary);
            font-weight: 500;
            font-size: 18px;
        }
        
        #priceInput {
            padding-left: 40px;
            font-size: 16px;
        }
        
        .gallery-actions {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
        }
        
        .buy-btn {
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            color: white;
            border: none;
            border-radius: 5px;
            padding: 8px 12px;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.3s;
            flex: 1;
            margin-right: 5px;
        }
        
        .buy-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 3px 10px rgba(106, 17, 203, 0.3);
        }
        
        .exchange-info {
            background-color: rgba(37, 117, 252, 0.1);
            padding: 12px;
            border-radius: 8px;
            margin-top: 15px;
            font-size: 14px;
            color: var(--price-euro);
            text-align: center;
            border: 1px solid rgba(37, 117, 252, 0.2);
        }
        
        .conversion-preview {
            background-color: var(--bg-secondary);
            padding: 15px;
            border-radius: 8px;
            margin-top: 10px;
            border: 1px solid var(--border-color);
            display: none;
        }
        
        .conversion-preview.active {
            display: block;
        }
        
        .conversion-result {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
            font-size: 16px;
        }
        
        .yuan-result {
            color: var(--price-yuan);
            font-weight: 600;
        }
        
        .euro-result {
            color: var(--price-euro);
            font-weight: 600;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Galeria de Produtos - Yuan para Euro</h1>
        
        <div class="tabs">
            <button class="tab active" data-tab="add">Adicionar Produto</button>
            <button class="tab" data-tab="gallery">Galeria de Produtos</button>
        </div>
        
        <div class="tab-content active" id="add-tab">
            <div class="form-group">
                <label for="imageTitle">Nome do Produto:</label>
                <input type="text" id="imageTitle" placeholder="Digite o nome do produto">
            </div>
            
            <div class="form-group">
                <label for="priceInput">Preço em Yuan (¥):</label>
                <div class="price-input-container">
                    <span class="currency-symbol">¥</span>
                    <input type="number" id="priceInput" placeholder="0.00" step="0.01" min="0">
                </div>
            </div>
            
            <div class="conversion-preview" id="conversionPreview">
                <div class="conversion-result">
                    <span>Preço em Yuan:</span>
                    <span class="yuan-result" id="yuanResult">¥ 0.00</span>
                </div>
                <div class="conversion-result">
                    <span>Preço em Euro:</span>
                    <span class="euro-result" id="euroResult">€ 0.00</span>
                </div>
            </div>
            
            <div class="exchange-info">
                <strong>Taxa de câmbio aproximada:</strong> 1€ ≈ 7.8¥
            </div>
            
            <div class="form-group">
                <label for="imageUrl">URL da Imagem:</label>
                <input type="url" id="imageUrl" placeholder="Cole a URL da imagem aqui">
            </div>
            
            <div class="form-group">
                <label for="linkUrl">URL do Link:</label>
                <input type="url" id="linkUrl" placeholder="Cole o link de destino aqui">
            </div>
            
            <div class="preview-container">
                <img id="imagePreview" src="" alt="Prévia da imagem" style="display: none;">
                <p id="placeholder" class="placeholder-text">Sua imagem aparecerá aqui</p>
            </div>
            
            <div class="buttons">
                <button id="addBtn">Adicionar à Galeria</button>
                <button id="resetBtn">Limpar Campos</button>
            </div>
            
            <div class="instructions">
                <h3>Como usar:</h3>
                <ul>
                    <li>Digite o nome do produto</li>
                    <li>Informe o preço em Yuan (¥) - a conversão para Euro é automática</li>
                    <li>Cole a URL de uma imagem no campo correspondente</li>
                    <li>Cole o link de destino (ex: link de compra)</li>
                    <li>Clique em "Adicionar à Galeria"</li>
                    <li>Vá para a aba "Galeria de Produtos" para ver todos os produtos</li>
                    <li>Clique em "Comprar" para abrir o link ou na imagem para visualizar</li>
                </ul>
            </div>
        </div>
        
        <div class="tab-content" id="gallery-tab">
            <h2>Minha Galeria de Produtos</h2>
            <p>Clique em "Comprar" para abrir o link de compra ou na imagem para visualizar</p>
            
            <div class="gallery" id="imageGallery">
                <!-- As imagens serão adicionadas aqui dinamicamente -->
            </div>
            
            <div class="instructions">
                <h3>Dica:</h3>
                <p>Use a aba "Adicionar Produto" para incluir mais produtos na sua galeria. Todos os produtos são salvos automaticamente no seu navegador.</p>
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Elementos da interface
            const tabs = document.querySelectorAll('.tab');
            const tabContents = document.querySelectorAll('.tab-content');
            const imageTitleInput = document.getElementById('imageTitle');
            const priceInput = document.getElementById('priceInput');
            const imageUrlInput = document.getElementById('imageUrl');
            const linkUrlInput = document.getElementById('linkUrl');
            const imagePreview = document.getElementById('imagePreview');
            const placeholder = document.getElementById('placeholder');
            const addBtn = document.getElementById('addBtn');
            const resetBtn = document.getElementById('resetBtn');
            const imageGallery = document.getElementById('imageGallery');
            const conversionPreview = document.getElementById('conversionPreview');
            const yuanResult = document.getElementById('yuanResult');
            const euroResult = document.getElementById('euroResult');
            
            // Taxa de câmbio Yuan para Euro (aproximada)
            const yuanToEuroRate = 0.128; // 1¥ = 0.128€ (aproximadamente 7.8¥ = 1€)
            
            // Sistema de abas
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    const tabId = tab.getAttribute('data-tab');
                    
                    // Ativar aba clicada
                    tabs.forEach(t => t.classList.remove('active'));
                    tab.classList.add('active');
                    
                    // Mostrar conteúdo da aba
                    tabContents.forEach(content => content.classList.remove('active'));
                    document.getElementById(`${tabId}-tab`).classList.add('active');
                    
                    // Se for a galeria, atualizar a exibição
                    if (tabId === 'gallery') {
                        renderGallery();
                    }
                });
            });
            
            // Carregar galeria salva
            let galleryItems = JSON.parse(localStorage.getItem('imageGallery')) || [];
            
            // Atualizar prévia da imagem quando a URL for alterada
            imageUrlInput.addEventListener('input', function() {
                updateImagePreview(this.value);
            });
            
            // Atualizar conversão automaticamente quando o preço for digitado
            priceInput.addEventListener('input', function() {
                updateConversionPreview(this.value);
            });
            
            // Adicionar produto à galeria
            addBtn.addEventListener('click', function() {
                const title = imageTitleInput.value.trim();
                const priceYuan = parseFloat(priceInput.value);
                const imageUrl = imageUrlInput.value.trim();
                const linkUrl = linkUrlInput.value.trim();
                
                if (!title) {
                    alert('Por favor, digite um nome para o produto.');
                    return;
                }
                
                if (isNaN(priceYuan) || priceYuan <= 0) {
                    alert('Por favor, insira um preço válido em Yuan.');
                    return;
                }
                
                if (!imageUrl) {
                    alert('Por favor, insira uma URL de imagem válida.');
                    return;
                }
                
                if (!linkUrl) {
                    alert('Por favor, insira uma URL de destino válida.');
                    return;
                }
                
                // Calcular preço em Euro
                const priceEuro = priceYuan * yuanToEuroRate;
                
                // Adicionar à galeria
                galleryItems.push({
                    id: Date.now(),
                    title: title,
                    priceYuan: priceYuan,
                    priceEuro: priceEuro,
                    imageUrl: imageUrl,
                    linkUrl: linkUrl
                });
                
                // Salvar no localStorage
                localStorage.setItem('imageGallery', JSON.stringify(galleryItems));
                
                // Limpar campos
                resetForm();
                
                alert('Produto adicionado à galeria com sucesso!');
                
                // Ir para a galeria
                tabs[1].click();
            });
            
            // Limpar campos
            resetBtn.addEventListener('click', resetForm);
            
            // Função para atualizar a prévia da imagem
            function updateImagePreview(url) {
                if (url) {
                    imagePreview.src = url;
                    imagePreview.style.display = 'block';
                    placeholder.style.display = 'none';
                } else {
                    imagePreview.style.display = 'none';
                    placeholder.style.display = 'block';
                }
            }
            
            // Função para atualizar a prévia da conversão
            function updateConversionPreview(yuanValue) {
                const yuan = parseFloat(yuanValue);
                
                if (!isNaN(yuan) && yuan > 0) {
                    const euro = yuan * yuanToEuroRate;
                    yuanResult.textContent = `¥ ${yuan.toFixed(2)}`;
                    euroResult.textContent = `€ ${euro.toFixed(2)}`;
                    conversionPreview.classList.add('active');
                } else {
                    conversionPreview.classList.remove('active');
                }
            }
            
            // Função para limpar o formulário
            function resetForm() {
                imageTitleInput.value = '';
                priceInput.value = '';
                imageUrlInput.value = '';
                linkUrlInput.value = '';
                imagePreview.style.display = 'none';
                placeholder.style.display = 'block';
                conversionPreview.classList.remove('active');
            }
            
            // Função para renderizar a galeria
            function renderGallery() {
                imageGallery.innerHTML = '';
                
                if (galleryItems.length === 0) {
                    imageGallery.innerHTML = '<div class="empty-gallery">Nenhum produto na galeria. Adicione alguns produtos na aba "Adicionar Produto".</div>';
                    return;
                }
                
                galleryItems.forEach(item => {
                    const galleryItem = document.createElement('div');
                    galleryItem.className = 'gallery-item';
                    
                    galleryItem.innerHTML = `
                        <img src="${item.imageUrl}" alt="${item.title}" class="gallery-image">
                        <div class="gallery-info">
                            <div class="gallery-title">${item.title}</div>
                            
                            <div class="gallery-price">¥ ${item.priceYuan.toFixed(2)}</div>
                            
                            <div class="gallery-conversion">≈ € ${item.priceEuro.toFixed(2)}</div>
                            
                            <div class="gallery-actions">
                                <button class="buy-btn">Comprar</button>
                                <button class="delete-btn" data-id="${item.id}">Remover</button>
                            </div>
                        </div>
                    `;
                    
                    // Adicionar evento de clique para visualizar a imagem
                    const image = galleryItem.querySelector('.gallery-image');
                    image.addEventListener('click', () => {
                        // Abre a imagem em uma nova aba para visualização
                        window.open(item.imageUrl, '_blank');
                    });
                    
                    // Adicionar evento para comprar (abrir link)
                    const buyBtn = galleryItem.querySelector('.buy-btn');
                    buyBtn.addEventListener('click', () => {
                        window.open(item.linkUrl, '_blank');
                    });
                    
                    // Adicionar evento para remover item
                    const deleteBtn = galleryItem.querySelector('.delete-btn');
                    deleteBtn.addEventListener('click', (e) => {
                        e.stopPropagation(); // Impedir que o clique propague para a imagem
                        if (confirm('Tem certeza que deseja remover este produto da galeria?')) {
                            removeFromGallery(item.id);
                        }
                    });
                    
                    imageGallery.appendChild(galleryItem);
                });
            }
            
            // Função para remover item da galeria
            function removeFromGallery(id) {
                galleryItems = galleryItems.filter(item => item.id !== id);
                localStorage.setItem('imageGallery', JSON.stringify(galleryItems));
                renderGallery();
            }
            
            // Inicializar a prévia com um exemplo, se disponível
            if (galleryItems.length > 0) {
                imageUrlInput.value = galleryItems[0].imageUrl;
                updateImagePreview(galleryItems[0].imageUrl);
            }
        });
    </script>
</body>
</html>
