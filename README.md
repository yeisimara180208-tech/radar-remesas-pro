# radar-remesas-pro
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Radar Remesas PRO</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 100%);
            min-height: 100vh;
            color: #ffffff;
            padding: 20px;
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
            padding-bottom: 20px;
            border-bottom: 2px solid #00e676;
        }

        h1 {
            font-size: 2.5rem;
            font-weight: 700;
            color: #00e676;
            text-shadow: 0 2px 10px rgba(0, 230, 118, 0.3);
            margin-bottom: 10px;
            letter-spacing: 1px;
        }

        .subtitle {
            color: #a0a0a0;
            font-size: 0.95rem;
            letter-spacing: 0.5px;
        }

        .content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }

        @media (max-width: 900px) {
            .content {
                grid-template-columns: 1fr;
            }
        }

        .panel {
            background: rgba(26, 26, 46, 0.8);
            border: 1px solid rgba(0, 230, 118, 0.2);
            border-radius: 12px;
            padding: 25px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .panel h2 {
            font-size: 1.3rem;
            color: #00e676;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .panel h2::before {
            content: '';
            display: inline-block;
            width: 4px;
            height: 20px;
            background: #00e676;
            border-radius: 2px;
        }

        .form-group {
            margin-bottom: 18px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #b0b0b0;
            font-size: 0.85rem;
            font-weight: 500;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        input[type="number"],
        input[type="text"] {
            width: 100%;
            padding: 12px 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(0, 230, 118, 0.3);
            border-radius: 8px;
            color: #ffffff;
            font-size: 1rem;
            transition: all 0.3s ease;
        }

        input[type="number"]:focus,
        input[type="text"]:focus {
            outline: none;
            border-color: #00e676;
            background: rgba(0, 230, 118, 0.05);
            box-shadow: 0 0 10px rgba(0, 230, 118, 0.2);
        }

        input[type="number"]::placeholder {
            color: rgba(255, 255, 255, 0.3);
        }

        .input-hint {
            font-size: 0.75rem;
            color: #808080;
            margin-top: 5px;
        }

        .button-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-top: 25px;
        }

        button {
            padding: 14px 24px;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .btn-calculate {
            grid-column: 1 / -1;
            background: linear-gradient(135deg, #00e676 0%, #00b853 100%);
            color: #000000;
            box-shadow: 0 4px 15px rgba(0, 230, 118, 0.3);
        }

        .btn-calculate:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 230, 118, 0.4);
        }

        .btn-calculate:active {
            transform: translateY(0);
        }

        .btn-copy {
            background: rgba(0, 230, 118, 0.2);
            color: #00e676;
            border: 1px solid #00e676;
        }

        .btn-copy:hover {
            background: rgba(0, 230, 118, 0.3);
            transform: translateY(-1px);
        }

        .btn-clear {
            background: rgba(255, 107, 107, 0.2);
            color: #ff6b6b;
            border: 1px solid #ff6b6b;
        }

        .btn-clear:hover {
            background: rgba(255, 107, 107, 0.3);
            transform: translateY(-1px);
        }

        .results {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 20px;
        }

        .result-item {
            background: rgba(0, 230, 118, 0.05);
            border: 1px solid rgba(0, 230, 118, 0.2);
            border-radius: 8px;
            padding: 15px;
            text-align: center;
        }

        .result-label {
            font-size: 0.8rem;
            color: #a0a0a0;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            margin-bottom: 8px;
        }

        .result-value {
            font-size: 1.6rem;
            color: #00e676;
            font-weight: 700;
        }

        .result-unit {
            font-size: 0.85rem;
            color: #808080;
            margin-left: 5px;
        }

        .result-full-width {
            grid-column: 1 / -1;
        }

        .history-panel {
            background: rgba(26, 26, 46, 0.8);
            border: 1px solid rgba(0, 230, 118, 0.2);
            border-radius: 12px;
            padding: 25px;
            backdrop-filter: blur(10px);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .history-panel h2 {
            font-size: 1.3rem;
            color: #00e676;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .history-panel h2::before {
            content: '';
            display: inline-block;
            width: 4px;
            height: 20px;
            background: #00e676;
            border-radius: 2px;
        }

        .history-list {
            max-height: 400px;
            overflow-y: auto;
        }

        .history-item {
            background: rgba(0, 230, 118, 0.05);
            border-left: 3px solid #00e676;
            padding: 12px;
            margin-bottom: 10px;
            border-radius: 4px;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            font-size: 0.9rem;
        }

        .history-item:last-child {
            margin-bottom: 0;
        }

        .history-time {
            color: #808080;
            font-size: 0.8rem;
            grid-column: 1 / -1;
        }

        .history-stat {
            display: flex;
            justify-content: space-between;
        }

        .history-stat-label {
            color: #a0a0a0;
        }

        .history-stat-value {
            color: #00e676;
            font-weight: 600;
        }

        .history-empty {
            text-align: center;
            color: #808080;
            padding: 30px 20px;
            font-style: italic;
        }

        .history-controls {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .btn-delete-history {
            flex: 1;
            background: rgba(255, 107, 107, 0.2);
            color: #ff6b6b;
            border: 1px solid #ff6b6b;
            padding: 10px;
            font-size: 0.9rem;
        }

        .btn-delete-history:hover {
            background: rgba(255, 107, 107, 0.3);
        }

        .success-message {
            display: none;
            position: fixed;
            top: 20px;
            right: 20px;
            background: #00e676;
            color: #000000;
            padding: 14px 20px;
            border-radius: 8px;
            font-weight: 600;
            box-shadow: 0 4px 15px rgba(0, 230, 118, 0.3);
            animation: slideIn 0.3s ease;
            z-index: 1000;
        }

        @keyframes slideIn {
            from {
                transform: translateX(400px);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }

        .success-message.show {
            display: block;
        }

        ::-webkit-scrollbar {
            width: 6px;
        }

        ::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
        }

        ::-webkit-scrollbar-thumb {
            background: rgba(0, 230, 118, 0.3);
            border-radius: 10px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: rgba(0, 230, 118, 0.5);
        }

        .row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }

        @media (max-width: 600px) {
            h1 {
                font-size: 1.8rem;
            }

            .content {
                gap: 20px;
            }

            .row {
                grid-template-columns: 1fr;
            }

            .result-value {
                font-size: 1.3rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>💱 Radar Remesas PRO</h1>
            <p class="subtitle">Calculadora de Remesas PEN ↔ VES | Comercio P2P</p>
        </header>

        <div class="content">
            <!-- Panel de Entrada -->
            <div class="panel">
                <h2>Parámetros</h2>
                
                <div class="form-group">
                    <label for="monto-pen">Monto en PEN</label>
                    <input type="number" id="monto-pen" placeholder="Ej: 100" step="0.01" min="0">
                    <div class="input-hint">Cantidad a convertir</div>
                </div>

                <div class="row">
                    <div class="form-group">
                        <label for="tc-usd-pen">TC USD/PEN</label>
                        <input type="number" id="tc-usd-pen" placeholder="Ej: 3.80" step="0.01" min="0" value="3.80">
                        <div class="input-hint">Tipo de cambio</div>
                    </div>
                    <div class="form-group">
                        <label for="tc-usd-ves">TC USD/VES</label>
                        <input type="number" id="tc-usd-ves" placeholder="Ej: 2500" step="0.01" min="0" value="2500">
                        <div class="input-hint">Tipo de cambio</div>
                    </div>
                </div>

                <div class="row">
                    <div class="form-group">
                        <label for="comision-peru">Comisión Perú (%)</label>
                        <input type="number" id="comision-peru" placeholder="Ej: 1.5" step="0.01" min="0" max="100" value="1.5">
                        <div class="input-hint">% de comisión</div>
                    </div>
                    <div class="form-group">
                        <label for="comision-venezuela">Comisión Venezuela (%)</label>
                        <input type="number" id="comision-venezuela" placeholder="Ej: 2.0" step="0.01" min="0" max="100" value="2.0">
                        <div class="input-hint">% de comisión</div>
                    </div>
                </div>

                <div class="form-group">
                    <label for="margen-ganancia">Margen de Ganancia (%)</label>
                    <input type="number" id="margen-ganancia" placeholder="Ej: 3.0" step="0.01" min="0" max="100" value="3.0">
                    <div class="input-hint">Tu ganancia esperada</div>
                </div>

                <div class="button-group">
                    <button class="btn-calculate" onclick="calcular()">📊 CALCULAR</button>
                    <button class="btn-copy" onclick="copiarResultado()">📋 COPIAR</button>
                    <button class="btn-clear" onclick="limpiar()">🔄 LIMPIAR</button>
                </div>
            </div>

            <!-- Panel de Resultados -->
            <div class="panel">
                <h2>Resultados</h2>
                
                <div class="results">
                    <div class="result-item">
                        <div class="result-label">Total VES</div>
                        <div class="result-value">
                            <span id="resultado-ves">0</span><span class="result-unit">VES</span>
                        </div>
                    </div>

                    <div class="result-item">
                        <div class="result-label">Ganancia USD</div>
                        <div class="result-value">
                            <span id="resultado-ganancia">0</span><span class="result-unit">USD</span>
                        </div>
                    </div>

                    <div class="result-item result-full-width">
                        <div class="result-label">Precio Recomendado por PEN</div>
                        <div class="result-value">
                            <span id="precio-recomendado">0</span><span class="result-unit">VES/PEN</span>
                        </div>
                    </div>

                    <div class="result-item result-full-width">
                        <div class="result-label">Costo Real (PEN → USD → VES)</div>
                        <div class="result-value">
                            <span id="costo-real">0</span><span class="result-unit">VES</span>
                        </div>
                    </div>
                </div>

                <div style="margin-top: 20px; padding: 15px; background: rgba(0, 230, 118, 0.1); border-radius: 8px; border-left: 3px solid #00e676;">
                    <div style="font-size: 0.85rem; color: #a0a0a0; margin-bottom: 8px;">📝 RESUMEN</div>
                    <div style="font-size: 1rem;">
                        <span style="color: #b0b0b0;">Entregas: </span>
                        <span id="resumen-entregas" style="color: #00e676; font-weight: 600;">0 VES</span>
                    </div>
                    <div style="font-size: 1rem; margin-top: 5px;">
                        <span style="color: #b0b0b0;">ROI: </span>
                        <span id="resumen-roi" style="color: #00e676; font-weight: 600;">0%</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Panel de Historial -->
        <div class="history-panel">
            <h2>Historial de Operaciones</h2>
            
            <div class="history-list" id="history-list">
                <div class="history-empty">📭 Sin operaciones registradas</div>
            </div>

            <div class="history-controls">
                <button class="btn-delete-history" onclick="limpiarHistorial()">🗑️ Limpiar Historial</button>
            </div>
        </div>
    </div>

    <div class="success-message" id="success-message"></div>

    <script>
        // Cargar historial al abrir la página
        cargarHistorial();

        function calcular() {
            // Obtener valores
            const montoPEN = parseFloat(document.getElementById('monto-pen').value) || 0;
            const tcUsdPen = parseFloat(document.getElementById('tc-usd-pen').value) || 1;
            const tcUsdVes = parseFloat(document.getElementById('tc-usd-ves').value) || 1;
            const comisionPeru = parseFloat(document.getElementById('comision-peru').value) || 0;
            const comisionVenezuela = parseFloat(document.getElementById('comision-venezuela').value) || 0;
            const margenGanancia = parseFloat(document.getElementById('margen-ganancia').value) || 0;

            if (montoPEN <= 0) {
                mostrarMensaje('❌ Ingresa un monto válido en PEN');
                return;
            }

            // CÁLCULOS
            // 1. Convertir PEN a USD
            let usd = montoPEN / tcUsdPen;

            // 2. Restar comisión Perú
            const comisionPeru_usd = usd * (comisionPeru / 100);
            usd = usd - comisionPeru_usd;

            // 3. Convertir USD a VES
            let ves = usd * tcUsdVes;

            // 4. Restar comisión Venezuela
            const comisionVenezuela_ves = ves * (comisionVenezuela / 100);
            ves = ves - comisionVenezuela_ves;

            // 5. Guardar VES antes de aplicar margen
            const vesAnteriorAlMargen = ves;

            // 6. Aplicar margen de ganancia (sobre el USD)
            const gananciaBruta = usd * (margenGanancia / 100);

            // VES final para entregar
            const vesFinal = ves + (gananciaBruta * tcUsdVes);

            // Costo real (PEN → USD → VES sin margen)
            const costoReal = vesAnteriorAlMargen;

            // Precio recomendado por PEN
            const precioRecomendado = vesFinal / montoPEN;

            // ROI en %
            const roi = (gananciaBruta / (montoPEN / tcUsdPen)) * 100;

            // MOSTRAR RESULTADOS
            document.getElementById('resultado-ves').textContent = formatoNumero(vesFinal);
            document.getElementById('resultado-ganancia').textContent = formatoNumero(gananciaBruta, 2);
            document.getElementById('precio-recomendado').textContent = formatoNumero(precioRecomendado, 2);
            document.getElementById('costo-real').textContent = formatoNumero(costoReal);
            document.getElementById('resumen-entregas').textContent = formatoNumero(vesFinal) + ' VES';
            document.getElementById('resumen-roi').textContent = formatoNumero(roi, 2) + '%';

            // GUARDAR EN HISTORIAL
            guardarOperacion(montoPEN, vesFinal, gananciaBruta);

            mostrarMensaje('✅ Cálculo completado');
        }

        function formatoNumero(num, decimales = 0) {
            return new Intl.NumberFormat('es-ES', {
                minimumFractionDigits: decimales,
                maximumFractionDigits: decimales
            }).format(num);
        }

        function copiarResultado() {
            const ves = document.getElementById('resultado-ves').textContent;
            const ganancia = document.getElementById('resultado-ganancia').textContent;
            const precio = document.getElementById('precio-recomendado').textContent;

            const texto = `🎯 Radar Remesas PRO\n\nVES a entregar: ${ves}\nGanancia: ${ganancia} USD\nPrecio/PEN: ${precio} VES`;

            navigator.clipboard.writeText(texto).then(() => {
                mostrarMensaje('📋 Resultado copiado');
            });
        }

        function limpiar() {
            document.getElementById('monto-pen').value = '';
            document.getElementById('resultado-ves').textContent = '0';
            document.getElementById('resultado-ganancia').textContent = '0';
            document.getElementById('precio-recomendado').textContent = '0';
            document.getElementById('costo-real').textContent = '0';
            document.getElementById('resumen-entregas').textContent = '0 VES';
            document.getElementById('resumen-roi').textContent = '0%';
            mostrarMensaje('🔄 Campos limpios');
        }

        function guardarOperacion(pen, ves, ganancia) {
            let historial = JSON.parse(localStorage.getItem('radarHistorial')) || [];

            const operacion = {
                fecha: new Date().toLocaleString('es-ES'),
                pen: pen,
                ves: ves,
                ganancia: ganancia,
                timestamp: Date.now()
            };

          
