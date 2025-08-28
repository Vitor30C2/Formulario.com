# Formulario.com
formulario
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Solicitação de Materiais</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            animation: slideIn 0.8s ease-out;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .header {
            background: linear-gradient(135deg, #2196F3, #21CBF3);
            color: white;
            padding: 40px 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            font-weight: 300;
        }

        .header p {
            opacity: 0.9;
            font-size: 1.1em;
        }

        .form-container {
            padding: 40px 30px;
        }

        .form-group {
            margin-bottom: 25px;
            position: relative;
        }

        .form-row {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
        }

        .form-row .form-group {
            flex: 1;
            min-width: 250px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #333;
            font-size: 14px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        input, select, textarea {
            width: 100%;
            padding: 15px;
            border: 2px solid #e1e1e1;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
            background: #f9f9f9;
        }

        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: #2196F3;
            background: white;
            box-shadow: 0 0 0 3px rgba(33, 150, 243, 0.1);
            transform: translateY(-2px);
        }

        textarea {
            resize: vertical;
            min-height: 100px;
        }

        .materials-section {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 25px;
            margin: 30px 0;
            border-left: 4px solid #2196F3;
        }

        .materials-section h3 {
            color: #2196F3;
            margin-bottom: 20px;
            font-size: 1.3em;
        }

        .material-item {
            display: flex;
            gap: 15px;
            align-items: end;
            margin-bottom: 15px;
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            transition: transform 0.2s ease;
        }

        .material-item:hover {
            transform: translateY(-2px);
        }

        .material-item input[type="text"] {
            flex: 2;
        }

        .material-item input[type="number"] {
            flex: 1;
            min-width: 100px;
        }

        .remove-btn {
            background: #ff4757;
            color: white;
            border: none;
            padding: 15px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            min-width: 80px;
            transition: all 0.2s ease;
        }

        .remove-btn:hover {
            background: #ff3838;
            transform: scale(1.05);
        }

        .add-btn {
            background: #2ed573;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            margin-top: 15px;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .add-btn:hover {
            background: #26d46c;
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(46, 213, 115, 0.3);
        }

        .submit-btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 18px 40px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 18px;
            font-weight: 600;
            width: 100%;
            margin-top: 30px;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(102, 126, 234, 0.4);
        }

        .submit-btn:active {
            transform: translateY(0);
        }

        .success-message {
            display: none;
            background: #2ed573;
            color: white;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
            text-align: center;
            font-weight: 600;
        }

        .priority-high { border-left-color: #ff4757; }
        .priority-medium { border-left-color: #ffa726; }
        .priority-low { border-left-color: #2ed573; }

        @media (max-width: 768px) {
            .container {
                margin: 10px;
                border-radius: 15px;
            }
            
            .form-row {
                flex-direction: column;
            }
            
            .form-row .form-group {
                min-width: auto;
            }
            
            .material-item {
                flex-direction: column;
                gap: 10px;
            }
            
            .header h1 {
                font-size: 2em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>📋 Solicitação de Materiais</h1>
            <p>Preencha o formulário abaixo para solicitar materiais</p>
        </div>
        
        <div class="form-container">
            <form id="materialForm">
                <div class="form-row">
                    <div class="form-group">
                        <label for="solicitante">Nome do Solicitante *</label>
                        <input type="text" id="solicitante" name="solicitante" required>
                    </div>
                    <div class="form-group">
                        <label for="departamento">Departamento *</label>
                        <select id="departamento" name="departamento" required>
                            <option value="">Selecione o departamento</option>
                            <option value="TI">Tecnologia da Informação</option>
                            <option value="RH">Recursos Humanos</option>
                            <option value="Financeiro">Financeiro</option>
                            <option value="Marketing">Marketing</option>
                            <option value="Vendas">Vendas</option>
                            <option value="Produção">Produção</option>
                            <option value="Logística">Logística</option>
                            <option value="Administrativo">Administrativo</option>
                            <option value="Outro">Outro</option>
                        </select>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="email">E-mail *</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="telefone">Telefone</label>
                        <input type="tel" id="telefone" name="telefone" placeholder="(00) 00000-0000">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="prioridade">Prioridade *</label>
                        <select id="prioridade" name="prioridade" required>
                            <option value="">Selecione a prioridade</option>
                            <option value="alta">🔴 Alta</option>
                            <option value="media">🟡 Média</option>
                            <option value="baixa">🟢 Baixa</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="dataLimite">Data Limite</label>
                        <input type="date" id="dataLimite" name="dataLimite">
                    </div>
                </div>

                <div class="materials-section" id="materialsSection">
                    <h3>📦 Lista de Materiais</h3>
                    <div id="materialsList">
                        <div class="material-item">
                            <div style="flex: 2;">
                                <label>Descrição do Material *</label>
                                <input type="text" name="material[]" placeholder="Ex: Papel A4, Canetas, Computador..." required>
                            </div>
                            <div style="flex: 1;">
                                <label>Quantidade *</label>
                                <input type="number" name="quantidade[]" min="1" placeholder="Ex: 10" required>
                            </div>
                            <div>
                                <label>Unidade</label>
                                <select name="unidade[]">
                                    <option value="un">Unidade</option>
                                    <option value="cx">Caixa</option>
                                    <option value="pct">Pacote</option>
                                    <option value="kg">Quilograma</option>
                                    <option value="m">Metro</option>
                                    <option value="l">Litro</option>
                                </select>
                            </div>
                        </div>
                    </div>
                    <button type="button" class="add-btn" onclick="addMaterial()">
                        ➕ Adicionar Material
                    </button>
                </div>

                <div class="form-group">
                    <label for="justificativa">Justificativa *</label>
                    <textarea id="justificativa" name="justificativa" placeholder="Descreva o motivo da solicitação e como os materiais serão utilizados..." required></textarea>
                </div>

                <div class="form-group">
                    <label for="observacoes">Observações Adicionais</label>
                    <textarea id="observacoes" name="observacoes" placeholder="Informações complementares, especificações técnicas, etc."></textarea>
                </div>

                <button type="submit" class="submit-btn">
                    📨 Enviar Solicitação
                </button>

                <div id="successMessage" class="success-message">
                    ✅ Solicitação enviada com sucesso! Você receberá uma cópia por e-mail.
                </div>
            </form>
        </div>
    </div>

    <script>
        let materialCount = 1;

        function addMaterial() {
            materialCount++;
            const materialsList = document.getElementById('materialsList');
            const materialItem = document.createElement('div');
            materialItem.className = 'material-item';
            materialItem.innerHTML = `
                <div style="flex: 2;">
                    <label>Descrição do Material *</label>
                    <input type="text" name="material[]" placeholder="Ex: Papel A4, Canetas, Computador..." required>
                </div>
                <div style="flex: 1;">
                    <label>Quantidade *</label>
                    <input type="number" name="quantidade[]" min="1" placeholder="Ex: 10" required>
                </div>
                <div>
                    <label>Unidade</label>
                    <select name="unidade[]">
                        <option value="un">Unidade</option>
                        <option value="cx">Caixa</option>
                        <option value="pct">Pacote</option>
                        <option value="kg">Quilograma</option>
                        <option value="m">Metro</option>
                        <option value="l">Litro</option>
                    </select>
                </div>
                <button type="button" class="remove-btn" onclick="removeMaterial(this)">
                    🗑️ Remover
                </button>
            `;
            materialsList.appendChild(materialItem);
        }

        function removeMaterial(button) {
            if (materialCount > 1) {
                button.parentElement.remove();
                materialCount--;
            }
        }

        document.getElementById('prioridade').addEventListener('change', function() {
            const section = document.getElementById('materialsSection');
            section.className = 'materials-section priority-' + this.value;
        });

        document.getElementById('materialForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Coleta os dados do formulário
            const formData = new FormData(this);
            const materials = [];
            
            // Processa os materiais
            const materialInputs = document.getElementsByName('material[]');
            const quantidadeInputs = document.getElementsByName('quantidade[]');
            const unidadeInputs = document.getElementsByName('unidade[]');
            
            for (let i = 0; i < materialInputs.length; i++) {
                if (materialInputs[i].value.trim()) {
                    materials.push({
                        material: materialInputs[i].value,
                        quantidade: quantidadeInputs[i].value,
                        unidade: unidadeInputs[i].value
                    });
                }
            }
            
            // Monta o corpo do email
            let emailBody = `Solicitação de Materiais\n\n`;
            emailBody += `Solicitante: ${formData.get('solicitante')}\n`;
            emailBody += `Departamento: ${formData.get('departamento')}\n`;
            emailBody += `E-mail: ${formData.get('email')}\n`;
            emailBody += `Telefone: ${formData.get('telefone') || 'Não informado'}\n`;
            emailBody += `Prioridade: ${formData.get('prioridade')}\n`;
            emailBody += `Data Limite: ${formData.get('dataLimite') || 'Não informada'}\n\n`;
            
            emailBody += `MATERIAIS SOLICITADOS:\n`;
            materials.forEach((item, index) => {
                emailBody += `${index + 1}. ${item.material} - ${item.quantidade} ${item.unidade}\n`;
            });
            
            emailBody += `\nJUSTIFICATIVA:\n${formData.get('justificativa')}\n\n`;
            
            if (formData.get('observacoes')) {
                emailBody += `OBSERVAÇÕES:\n${formData.get('observacoes')}\n\n`;
            }
            
            emailBody += `Data da Solicitação: ${new Date().toLocaleDateString('pt-BR')}`;
            
            // Cria o link mailto
            const subject = `Solicitação de Materiais - ${formData.get('solicitante')} - ${formData.get('departamento')}`;
            const mailtoLink = `mailto:administrativo@qfrotas.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(emailBody)}`;
            
            // Abre o cliente de email
            window.location.href = mailtoLink;
            
            // Mostra mensagem de sucesso
            document.getElementById('successMessage').style.display = 'block';
            
            // Rola até a mensagem de sucesso
            document.getElementById('successMessage').scrollIntoView({ 
                behavior: 'smooth' 
            });
            
            // Opcional: limpa o formulário após alguns segundos
            setTimeout(() => {
                this.reset();
                document.getElementById('successMessage').style.display = 'none';
                // Restaura apenas um material na lista
                document.getElementById('materialsList').innerHTML = `
                    <div class="material-item">
                        <div style="flex: 2;">
                            <label>Descrição do Material *</label>
                            <input type="text" name="material[]" placeholder="Ex: Papel A4, Canetas, Computador..." required>
                        </div>
                        <div style="flex: 1;">
                            <label>Quantidade *</label>
                            <input type="number" name="quantidade[]" min="1" placeholder="Ex: 10" required>
                        </div>
                        <div>
                            <label>Unidade</label>
                            <select name="unidade[]">
                                <option value="un">Unidade</option>
                                <option value="cx">Caixa</option>
                                <option value="pct">Pacote</option>
                                <option value="kg">Quilograma</option>
                                <option value="m">Metro</option>
                                <option value="l">Litro</option>
                            </select>
                        </div>
                    </div>
                `;
                materialCount = 1;
                document.getElementById('materialsSection').className = 'materials-section';
            }, 5000);
        });

        // Formatação do telefone
        document.getElementById('telefone').addEventListener('input', function(e) {
            let value = e.target.value.replace(/\D/g, '');
            if (value.length >= 11) {
                value = value.replace(/(\d{2})(\d{5})(\d{4})/, '($1) $2-$3');
            } else if (value.length >= 7) {
                value = value.replace(/(\d{2})(\d{4})(\d{0,4})/, '($1) $2-$3');
            } else if (value.length >= 3) {
                value = value.replace(/(\d{2})(\d{0,5})/, '($1) $2');
            } else if (value.length >= 1) {
                value = value.replace(/(\d{0,2})/, '($1');
            }
            e.target.value = value;
        });

        // Define data mínima como hoje
        document.getElementById('dataLimite').min = new Date().toISOString().split('T')[0];
    </script>
</body>
</html>
