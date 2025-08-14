# SRI-MSCN
Esta pagina es una simulación del Sri en linea del ECUADOR, los datos registrados son ficción. 
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SRI en Línea - Servicios</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js CDN -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* Estilos personalizados */
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        .shadow-sri { box-shadow: 0 4px 24px 0 rgba(0,84,143,0.10), 0 1.5px 4px 0 rgba(76,175,80,0.10);}
        .bg-login { background: linear-gradient(135deg, #00548F 60%, #4CAF50 100%);}
        .menu-item-active { background-color: #0069B3; color: #fff !important;}
        .icon-circle {
            background: linear-gradient(135deg, #4CAF50 60%, #00548F 100%);
            color: #fff; border-radius: 50%; width: 56px; height: 56px;
            display: flex; align-items: center; justify-content: center;
            font-size: 2rem; margin: 0 auto 1rem auto;
            box-shadow: 0 2px 8px rgba(0,84,143,0.10);
        }
        .card-efecto { transition: transform 0.2s, box-shadow 0.2s;}
        .card-efecto:hover { transform: translateY(-6px) scale(1.03); box-shadow: 0 8px 32px 0 rgba(0,84,143,0.18), 0 3px 12px 0 rgba(76,175,80,0.15);}
    </style>
</head>
<body class="min-h-screen bg-gradient-to-br from-sri-blue via-sri-green to-sri-green-light">

    <!-- Cabecera -->
    <header class="bg-sri-blue shadow">
        <div class="container mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center">
                <img src="https://seeklogo.com/images/S/sri-ecuador-logo-2B7B2B7B2D-seeklogo.com.png" alt="Logo SRI" class="h-14 mr-4 bg-white rounded p-1 shadow">
                <div>
                    <h1 class="text-white text-2xl font-bold tracking-wide">SRI en Línea</h1>
                    <p class="text-sri-green-light text-xs">Servicio de Rentas Internas del Ecuador</p>
                </div>
            </div>
            <button id="logoutBtn" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded hidden">Cerrar Sesión</button>
        </div>
    </header>

    <!-- Login/Registro -->
    <div class="bg-login min-h-[calc(100vh-80px)] flex items-center justify-center py-12" id="loginBg">
        <div class="w-full max-w-md mx-auto bg-white rounded-lg shadow-sri p-8 card-efecto">
            <div class="flex flex-col items-center mb-6">
                <div class="icon-circle mb-2">
                    <svg class="w-10 h-10" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24">
                        <circle cx="12" cy="8" r="4" stroke="currentColor" stroke-width="2"/>
                        <path stroke="currentColor" stroke-width="2" d="M4 20c0-4 4-7 8-7s8 3 8 7"/>
                    </svg>
                </div>
                <h2 class="text-2xl font-bold text-sri-blue mb-1">Acceso a SRI en Línea</h2>
                <p class="text-gray-500 text-sm text-center">Ingrese con su usuario y contraseña o regístrese</p>
            </div>
            <form id="loginForm" class="flex flex-col gap-4">
                <div>
                    <label for="usuario" class="block text-sri-blue font-medium mb-1">Usuario</label>
                    <input type="text" id="usuario" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                </div>
                <div>
                    <label for="contrasena" class="block text-sri-blue font-medium mb-1">Contraseña</label>
                    <input type="password" id="contrasena" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                </div>
                <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white font-semibold py-2 rounded transition shadow">Ingresar</button>
                <p id="loginError" class="text-red-500 text-sm hidden">Usuario o contraseña incorrectos</p>
            </form>
            <div class="flex justify-between mt-4 text-xs">
                <span class="text-sri-blue">¿No tienes cuenta?</span>
                <a href="#" id="showRegister" class="text-sri-blue hover:underline cursor-pointer">Registrarse</a>
            </div>
            <form id="registerForm" class="flex flex-col gap-4 mt-6 hidden bg-gray-100 p-4 rounded shadow">
                <h3 class="text-lg font-bold text-sri-blue mb-2">Registro de nuevo usuario</h3>
                <div>
                    <label for="nuevoUsuario" class="block text-sri-blue font-medium mb-1">Usuario</label>
                    <input type="text" id="nuevoUsuario" class="border border-gray-300 rounded px-3 py-2 w-full" required placeholder="Ej: usuario123">
                </div>
                <div>
                    <label for="nuevaContrasena" class="block text-sri-blue font-medium mb-1">Contraseña</label>
                    <input type="password" id="nuevaContrasena" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                </div>
                <div>
                    <label for="nuevoCorreo" class="block text-sri-blue font-medium mb-1">Correo electrónico</label>
                    <input type="email" id="nuevoCorreo" class="border border-gray-300 rounded px-3 py-2 w-full" required placeholder="Ej: correo@ejemplo.com">
                </div>
                <div>
                    <label for="nombreCompleto" class="block text-sri-blue font-medium mb-1">Nombre Completo</label>
                    <input type="text" id="nombreCompleto" class="border border-gray-300 rounded px-3 py-2 w-full" required placeholder="Ej: Juan Pérez García">
                </div>
                <div>
                    <label for="nuevaCedula" class="block text-sri-blue font-medium mb-1">Cédula</label>
                    <input type="text" id="nuevaCedula" class="border border-gray-300 rounded px-3 py-2 w-full" required maxlength="10" placeholder="Ej: 0102030405">
                </div>
                <div>
                    <label for="nuevoRuc" class="block text-sri-blue font-medium mb-1">RUC</label>
                    <input type="text" id="nuevoRuc" class="border border-gray-300 rounded px-3 py-2 w-full" required maxlength="13" placeholder="Ej: 0102030405001">
                </div>
                <div>
                    <label for="nuevaPlaca" class="block text-sri-blue font-medium mb-1">Placa de vehículo</label>
                    <input type="text" id="nuevaPlaca" class="border border-gray-300 rounded px-3 py-2 w-full" required maxlength="7" placeholder="Ej: ABC1234">
                </div>
                <div>
                    <label for="direccion" class="block text-sri-blue font-medium mb-1">Dirección</label>
                    <input type="text" id="direccion" class="border border-gray-300 rounded px-3 py-2 w-full" required placeholder="Ej: Av. Principal 123 y Calle Secundaria">
                </div>
                <div>
                    <label for="telefono" class="block text-sri-blue font-medium mb-1">Teléfono</label>
                    <input type="text" id="telefono" class="border border-gray-300 rounded px-3 py-2 w-full" required maxlength="10" placeholder="Ej: 0991234567">
                </div>
                <div>
                    <label for="estadoCivil" class="block text-sri-blue font-medium mb-1">Estado Civil</label>
                    <select id="estadoCivil" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                        <option value="">Seleccione</option>
                        <option value="Soltero/a">Soltero/a</option>
                        <option value="Casado/a">Casado/a</option>
                        <option value="Divorciado/a">Divorciado/a</option>
                        <option value="Viudo/a">Viudo/a</option>
                        <option value="Unión Libre">Unión Libre</option>
                    </select>
                </div>
                <div>
                    <label for="fechaNacimiento" class="block text-sri-blue font-medium mb-1">Fecha de Nacimiento</label>
                    <input type="date" id="fechaNacimiento" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                </div>
                <div>
                    <label for="nacionalidad" class="block text-sri-blue font-medium mb-1">Nacionalidad</label>
                    <input type="text" id="nacionalidad" class="border border-gray-300 rounded px-3 py-2 w-full" required placeholder="Ej: Ecuatoriana">
                </div>
                <div>
                    <label for="actividadEconomica" class="block text-sri-blue font-medium mb-1">Actividad Económica Principal</label>
                    <input type="text" id="actividadEconomica" class="border border-gray-300 rounded px-3 py-2 w-full" required placeholder="Ej: Comercio al por menor">
                </div>
                <div>
                    <label for="tipoContribuyente" class="block text-sri-blue font-medium mb-1">Tipo de Contribuyente</label>
                    <select id="tipoContribuyente" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                        <option value="">Seleccione</option>
                        <option value="PERSONA NATURAL">Persona Natural</option>
                        <option value="SOCIEDAD PRIVADA">Sociedad Privada</option>
                        <option value="SOCIEDAD PÚBLICA">Sociedad Pública</option>
                    </select>
                </div>
                <div>
                    <label for="regimenTributario" class="block text-sri-blue font-medium mb-1">Régimen Tributario</label>
                    <select id="regimenTributario" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                        <option value="">Seleccione</option>
                        <option value="RIMPE">RIMPE</option>
                        <option value="GENERAL">General</option>
                        <option value="ESPECIAL">Especial</option>
                    </select>
                </div>
                <div>
                    <label for="categoriaTributaria" class="block text-sri-blue font-medium mb-1">Categoría Tributaria</label>
                    <select id="categoriaTributaria" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                        <option value="">Seleccione</option>
                        <option value="EMPRENDEDOR">Emprendedor</option>
                        <option value="NEGOCIO POPULAR">Negocio Popular</option>
                        <option value="CONTRIBUYENTE">Contribuyente</option>
                    </select>
                </div>
                <div>
                    <label for="fechaInicioActividades" class="block text-sri-blue font-medium mb-1">Fecha de Inicio de Actividades</label>
                    <input type="date" id="fechaInicioActividades" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                </div>
                <div>
                    <label for="obligadoContabilidad" class="block text-sri-blue font-medium mb-1">Obligado a llevar Contabilidad</label>
                    <select id="obligadoContabilidad" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                        <option value="NO">NO</option>
                        <option value="SI">SI</option>
                    </select>
                </div>
                <div>
                    <label for="agenteRetencion" class="block text-sri-blue font-medium mb-1">Agente de Retención</label>
                    <select id="agenteRetencion" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                        <option value="NO">NO</option>
                        <option value="SI">SI</option>
                    </select>
                </div>
                <div>
                    <label for="contribuyenteEspecial" class="block text-sri-blue font-medium mb-1">Contribuyente Especial</label>
                    <select id="contribuyenteEspecial" class="border border-gray-300 rounded px-3 py-2 w-full" required>
                        <option value="NO">NO</option>
                        <option value="SI">SI</option>
                    </select>
                </div>

                <button type="submit" class="bg-sri-blue hover:bg-sri-blue-light text-white font-semibold py-2 rounded transition">Registrar</button>
                <p id="registerSuccess" class="text-green-600 text-sm hidden">¡Registro exitoso! Ahora puede iniciar sesión.</p>
            </form>
        </div>
    </div>

    <!-- Banner visual con azul y verde y un gráfico SVG decorativo -->
    <div class="bg-gradient-to-r from-sri-blue to-sri-green-light py-10 px-4 flex flex-col md:flex-row items-center justify-between shadow-lg">
        <div class="text-white md:w-2/3">
            <h2 class="text-3xl md:text-4xl font-bold mb-2 drop-shadow">Bienvenido al Portal SRI en Línea</h2>
            <p class="text-lg md:text-xl mb-4 drop-shadow">Accede a todos tus servicios tributarios de forma segura y moderna.</p>
            <div class="flex gap-4 mt-4">
                <div class="icon-circle bg-white text-sri-blue shadow"><span>🔍</span></div>
                <div class="icon-circle bg-white text-sri-blue shadow"><span>🧾</span></div>
                <div class="icon-circle bg-white text-sri-blue shadow"><span>📄</span></div>
                <div class="icon-circle bg-white text-sri-blue shadow"><span>🚗</span></div>
            </div>
        </div>
        <div class="md:w-1/3 flex justify-center mt-8 md:mt-0">
            <!-- SVG decorativo tipo gráfico de barras -->
            <svg width="180" height="120" viewBox="0 0 180 120" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect x="20" y="60" width="20" height="40" rx="4" fill="#00548F"/>
                <rect x="50" y="40" width="20" height="60" rx="4" fill="#4CAF50"/>
                <rect x="80" y="20" width="20" height="80" rx="4" fill="#0069B3"/>
                <rect x="110" y="50" width="20" height="50" rx="4" fill="#81C784"/>
                <rect x="140" y="70" width="20" height="30" rx="4" fill="#00548F"/>
            </svg>
        </div>
    </div>

    <!-- Menú de servicios -->
    <div id="mainContent" class="hidden bg-gray-100 min-h-screen">
        <nav class="bg-sri-blue shadow sticky top-0 z-20">
            <div class="container mx-auto px-4">
                <div class="flex flex-wrap gap-2 py-2" id="menuNav">
                    <button data-section="consulta" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>🔍</span>Consulta</button>
                    <button data-section="facturacion" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>🧾</span>Facturación Electrónica</button>
                    <button data-section="ruc" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>📄</span>RUC</button>
                    <button data-section="declaraciones" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>📑</span>Declaraciones</button>
                    <button data-section="anexos" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>📂</span>Anexos</button>
                    <button data-section="pagos" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>💳</span>Pagos</button>
                    <button data-section="deudas" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>💰</span>Deudas</button>
                    <button data-section="reintegro" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>🔄</span>Reintegro de Valores</button>
                    <button data-section="tramites" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>📝</span>Trámites</button>
                    <button data-section="vehiculos" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>🚗</span>Vehículos</button>
                    <button data-section="reportes" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>📊</span>Reportes de Pago Vehicular</button>
                    <button data-section="claves" class="menu-btn bg-white text-sri-blue px-3 py-2 rounded shadow flex items-center gap-2"><span>🔑</span>Claves</button>
                </div>
            </div>
        </nav>
        <main class="container mx-auto px-4 py-8">
            <!-- Secciones de servicios -->
            <div id="section-consulta" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">🔍 Consulta por Cédula o RUC</h3>
                    <form id="formConsulta" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">Cédula o RUC</label>
                            <input type="text" id="consultaDocumento" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="13" required placeholder="Ej: 0102030405 o 0102030405001">
                            <span id="errorConsultaDocumento" class="text-red-500 text-xs hidden">Documento inválido</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Consultar</button>
                    </form>
                    <div id="resultadoConsulta" class="mt-6"></div>
                </div>
            </div>
            <div id="section-facturacion" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">🧾 Facturación Electrónica</h3>
                    <form id="formFacturacion" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">Clave de Acceso (49 dígitos)</label>
                            <input type="text" id="facturaClave" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="49" required placeholder="Ej: 1234567890123456789012345678901234567890123456789">
                            <span id="errorFacturaClave" class="text-red-500 text-xs hidden">Clave inválida</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Validar Factura</button>
                    </form>
                    <div id="resultadoFacturacion" class="mt-6"></div>
                </div>
            </div>
            <div id="section-ruc" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">📄 Consulta de RUC</h3>
                    <form id="formRuc" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">RUC</label>
                            <input type="text" id="rucConsulta" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="13" required placeholder="Ej: 0102030405001">
                            <span id="errorRucConsulta" class="text-red-500 text-xs hidden">RUC inválido</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Consultar RUC</button>
                    </form>
                    <div id="resultadoRuc" class="mt-6"></div>
                </div>
            </div>
            <div id="section-declaraciones" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">📑 Declaraciones</h3>
                    <form id="formDeclaracion" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">RUC</label>
                            <input type="text" id="declaracionRuc" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="13" required placeholder="Ej: 0102030405001">
                            <span id="errorDeclaracionRuc" class="text-red-500 text-xs hidden">RUC inválido</span>
                        </div>
                        <div>
                            <label class="text-sri-blue font-medium">Año fiscal</label>
                            <input type="number" id="declaracionAnio" class="border border-gray-300 rounded px-2 py-1 w-full" min="2000" max="2100" required placeholder="Ej: 2024">
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Enviar declaración</button>
                    </form>
                    <div id="resultadoDeclaracion" class="mt-6"></div>
                </div>
            </div>
            <div id="section-anexos" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">📂 Anexos</h3>
                    <form id="formAnexo" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">RUC</label>
                            <input type="text" id="anexoRuc" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="13" required placeholder="Ej: 0102030405001">
                            <span id="errorAnexoRuc" class="text-red-500 text-xs hidden">RUC inválido</span>
                        </div>
                        <div>
                            <label class="text-sri-blue font-medium">Periodo</label>
                            <input type="month" id="anexoPeriodo" class="border border-gray-300 rounded px-2 py-1 w-full" required>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Enviar anexo</button>
                    </form>
                    <div id="resultadoAnexo" class="mt-6"></div>
                </div>
            </div>
            <div id="section-pagos" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">💳 Pagos</h3>
                    <form id="formPagos" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">RUC o Cédula</label>
                            <input type="text" id="pagosDocumento" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="13" required placeholder="Ej: 0102030405 o 0102030405001">
                            <span id="errorPagosDocumento" class="text-red-500 text-xs hidden">Documento inválido</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Consultar Pagos</button>
                    </form>
                    <div id="resultadoPagos" class="mt-6"></div>
                </div>
            </div>
            <div id="section-deudas" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">💰 Deudas</h3>
                    <form id="formDeudas" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">RUC o Cédula</label>
                            <input type="text" id="deudasDocumento" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="13" required placeholder="Ej: 0102030405 o 0102030405001">
                            <span id="errorDeudasDocumento" class="text-red-500 text-xs hidden">Documento inválido</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Consultar Deudas</button>
                    </form>
                    <div id="resultadoDeudas" class="mt-6"></div>
                </div>
            </div>
            <div id="section-reintegro" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">🔄 Reintegro de Valores</h3>
                    <form id="formReintegro" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">RUC</label>
                            <input type="text" id="reintegroRuc" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="13" required placeholder="Ej: 0102030405001">
                            <span id="errorReintegroRuc" class="text-red-500 text-xs hidden">RUC inválido</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Solicitar Reintegro</button>
                    </form>
                    <div id="resultadoReintegro" class="mt-6"></div>
                </div>
            </div>
            <div id="section-tramites" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">📝 Trámites</h3>
                    <form id="formTramites" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">RUC o Cédula</label>
                            <input type="text" id="tramitesDocumento" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="13" required placeholder="Ej: 0102030405 o 0102030405001">
                            <span id="errorTramitesDocumento" class="text-red-500 text-xs hidden">Documento inválido</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Consultar Trámite</button>
                    </form>
                    <div id="resultadoTramites" class="mt-6"></div>
                </div>
            </div>
            <div id="section-vehiculos" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">🚗 Vehículos</h3>
                    <form id="formVehiculos" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">Placa</label>
                            <input type="text" id="vehiculoPlaca" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="7" required placeholder="Ej: ABC1234">
                            <span id="errorVehiculoPlaca" class="text-red-500 text-xs hidden">Placa inválida</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Consultar Vehículo</button>
                    </form>
                    <div id="resultadoVehiculos" class="mt-6"></div>
                </div>
            </div>
            <div id="section-reportes" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">📊 Reporte de Pago Vehicular</h3>
                    <form id="formReporte" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">Placa</label>
                            <input type="text" id="reportePlaca" class="border border-gray-300 rounded px-2 py-1 w-full" maxlength="7" required placeholder="Ej: ABC1234">
                            <span id="errorReportePlaca" class="text-red-500 text-xs hidden">Placa inválida</span>
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Generar Reporte</button>
                    </form>
                    <div id="resultadoReporte" class="mt-6"></div>
                </div>
            </div>
            <div id="section-claves" class="service-section hidden">
                <div class="bg-white rounded-lg shadow-sri p-8 max-w-lg mx-auto card-efecto">
                    <h3 class="text-xl font-bold text-sri-blue mb-4 flex items-center gap-2">🔑 Gestión de Claves</h3>
                    <form id="formClaves" class="flex flex-col gap-4">
                        <div>
                            <label class="text-sri-blue font-medium">Usuario</label>
                            <input type="text" id="clavesUsuario" class="border border-gray-300 rounded px-2 py-1 w-full" required placeholder="Ej: usuario123">
                        </div>
                        <button type="submit" class="bg-sri-green hover:bg-sri-green-light text-white px-3 py-2 rounded shadow">Recuperar Clave</button>
                    </form>
                    <div id="resultadoClaves" class="mt-6"></div>
                </div>
            </div>
        </main>
        <!-- Menú de servicios visual -->
        <main class="container mx-auto px-4 py-8 grid grid-cols-1 md:grid-cols-3 gap-8" id="mainMenu" style="display:none;">
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('consulta')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-green-400 to-blue-600"><span>🔍</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Consulta</h3>
                <p class="text-gray-600 mb-2">Consulta tu RUC, cédula, vehículos y más.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('facturacion')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-yellow-400 to-red-500"><span>🧾</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Facturación Electrónica</h3>
                <p class="text-gray-600 mb-2">Valida comprobantes electrónicos.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('vehiculos')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-purple-400 to-pink-500"><span>🚗</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Vehículos</h3>
                <p class="text-gray-600 mb-2">Consulta y reporta pagos por placa.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('declaraciones')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-blue-400 to-green-500"><span>📑</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Declaraciones</h3>
                <p class="text-gray-600 mb-2">Envía tus declaraciones tributarias.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('anexos')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-red-400 to-purple-500"><span>📂</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Anexos</h3>
                <p class="text-gray-600 mb-2">Gestiona tus anexos.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('pagos')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-orange-400 to-yellow-500"><span>💳</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Pagos</h3>
                <p class="text-gray-600 mb-2">Consulta y realiza tus pagos.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('deudas')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-teal-400 to-cyan-500"><span>💰</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Deudas</h3>
                <p class="text-gray-600 mb-2">Revisa tu estado de deudas.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('reintegro')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-lime-400 to-emerald-500"><span>🔄</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Reintegro de Valores</h3>
                <p class="text-gray-600 mb-2">Solicita reintegros.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('tramites')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-rose-400 to-fuchsia-500"><span>📝</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Trámites</h3>
                <p class="text-gray-600 mb-2">Gestiona tus trámites en línea.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('reportes')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-indigo-400 to-violet-500"><span>📊</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Reportes de Pago Vehicular</h3>
                <p class="text-gray-600 mb-2">Genera reportes de pagos de vehículos.</p>
            </div>
            <div class="bg-white rounded-lg shadow-sri p-8 text-center card-efecto cursor-pointer" onclick="showSection('claves')">
                <div class="icon-circle mb-2 bg-gradient-to-br from-gray-400 to-zinc-500"><span>🔑</span></div>
                <h3 class="text-lg font-bold text-sri-blue mb-2">Gestión de Claves</h3>
                <p class="text-gray-600 mb-2">Recupera o cambia tu clave.</p>
            </div>
        </main>
    </div>

    <script>
        // Configuración de Tailwind CSS (debe ir antes de usar las clases personalizadas)
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'sri-blue': '#00548F',
                        'sri-green': '#4CAF50',
                        'sri-green-light': '#81C784'
                    }
                }
            }
        }

        // Cargar usuarios desde localStorage o usar el admin por defecto
        let usuariosRegistrados = JSON.parse(localStorage.getItem('usuariosSRI')) || [
            {
                usuario: 'admin',
                contrasena: '1234',
                correo: 'admin@sri.com',
                cedula: '0102030405',
                ruc: '0102030405001',
                placas: ['ABC1234'],
                nombreCompleto: 'Administrador Principal',
                direccion: 'Av. Amazonas N34-123 y La Pinta',
                telefono: '022555123',
                estadoCivil: 'Soltero/a',
                fechaNacimiento: '1980-01-15',
                nacionalidad: 'Ecuatoriana',
                actividadEconomica: 'SERVICIOS DE REPARACIÓN Y MANTENIMIENTO DE MAQUINARIA Y TRACTORES DE USO AGROPECUARIO',
                tipoContribuyente: 'PERSONA NATURAL',
                regimenTributario: 'RIMPE',
                categoriaTributaria: 'EMPRENDEDOR',
                fechaInicioActividades: '2018-08-01',
                estadoRuc: 'ACTIVO',
                obligadoContabilidad: 'NO',
                agenteRetencion: 'NO',
                contribuyenteEspecial: 'NO',
                contribuyenteFantasma: 'NO',
                transaccionesInexistentes: 'NO'
            }
        ];

        let usuarioActivo = null;

        // Función para guardar usuarios en localStorage
        function guardarUsuarios() {
            localStorage.setItem('usuariosSRI', JSON.stringify(usuariosRegistrados));
        }

        // Función para iniciar sesión
        function loginUser(usuario, contrasena) {
            const encontrado = usuariosRegistrados.find(u => u.usuario === usuario && u.contrasena === contrasena);
            if(encontrado) {
                usuarioActivo = encontrado;
                localStorage.setItem('usuarioActivoSRI', JSON.stringify(usuarioActivo)); // Guardar sesión activa
                document.body.classList.remove('bg-login');
                document.getElementById('mainContent').classList.remove('hidden');
                document.getElementById('loginBg').classList.add('hidden');
                document.getElementById('mainMenu').style.display = 'grid'; // Asegura que el menú visual se muestre como grid
                document.getElementById('logoutBtn').classList.remove('hidden');
                document.getElementById('loginError').classList.add('hidden'); // Ocultar error si estaba visible
            } else {
                document.getElementById('loginError').classList.remove('hidden');
            }
        }

        // Función para cerrar sesión
        function logoutUser() {
            usuarioActivo = null;
            localStorage.removeItem('usuarioActivoSRI'); // Eliminar sesión activa
            document.body.classList.add('bg-login');
            document.getElementById('mainContent').classList.add('hidden');
            document.getElementById('loginBg').classList.remove('hidden');
            document.getElementById('mainMenu').style.display = 'none';
            document.getElementById('logoutBtn').classList.add('hidden');
            // Limpiar formularios y resultados al cerrar sesión
            document.querySelectorAll('form').forEach(form => form.reset());
            document.querySelectorAll('[id^="resultado"]').forEach(div => div.innerHTML = '');
            document.querySelectorAll('.service-section').forEach(sec => sec.classList.add('hidden'));
            document.querySelectorAll('.menu-btn').forEach(b => b.classList.remove('menu-item-active'));
        }

        // Verificar sesión al cargar la página
        document.addEventListener('DOMContentLoaded', function() {
            const storedUser = localStorage.getItem('usuarioActivoSRI');
            if (storedUser) {
                usuarioActivo = JSON.parse(storedUser);
                document.body.classList.remove('bg-login');
                document.getElementById('mainContent').classList.remove('hidden');
                document.getElementById('loginBg').classList.add('hidden');
                document.getElementById('mainMenu').style.display = 'grid'; // Asegura que el menú visual se muestre como grid
                document.getElementById('logoutBtn').classList.remove('hidden');
            }
        });

        // Event Listener para el botón de cerrar sesión
        document.getElementById('logoutBtn').addEventListener('click', logoutUser);

        // Login
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const usuario = document.getElementById('usuario').value;
            const contrasena = document.getElementById('contrasena').value;
            loginUser(usuario, contrasena);
        });

        // Mostrar formulario de registro
        document.getElementById('showRegister').addEventListener('click', function(e) {
            e.preventDefault(); // Prevenir el comportamiento por defecto del enlace
            document.getElementById('registerForm').classList.toggle('hidden');
            document.getElementById('loginError').classList.add('hidden'); // Ocultar error de login al mostrar registro
            document.getElementById('registerSuccess').classList.add('hidden'); // Ocultar mensaje de éxito/error de registro
            document.getElementById('registerSuccess').classList.remove('text-red-600', 'text-green-600'); // Limpiar clases de color
        });

        // Registro de nuevo usuario
        document.getElementById('registerForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const nuevoUsuario = document.getElementById('nuevoUsuario').value.trim();
            const nuevaContrasena = document.getElementById('nuevaContrasena').value;
            const nuevoCorreo = document.getElementById('nuevoCorreo').value.trim();
            const nombreCompleto = document.getElementById('nombreCompleto').value.trim();
            const nuevaCedula = document.getElementById('nuevaCedula').value.trim();
            const nuevoRuc = document.getElementById('nuevoRuc').value.trim();
            const nuevaPlaca = document.getElementById('nuevaPlaca').value.trim().toUpperCase();
            const direccion = document.getElementById('direccion').value.trim();
            const telefono = document.getElementById('telefono').value.trim();
            const estadoCivil = document.getElementById('estadoCivil').value;
            const fechaNacimiento = document.getElementById('fechaNacimiento').value;
            const nacionalidad = document.getElementById('nacionalidad').value.trim();
            const actividadEconomica = document.getElementById('actividadEconomica').value.trim();
            const tipoContribuyente = document.getElementById('tipoContribuyente').value;
            const regimenTributario = document.getElementById('regimenTributario').value;
            const categoriaTributaria = document.getElementById('categoriaTributaria').value;
            const fechaInicioActividades = document.getElementById('fechaInicioActividades').value;
            const obligadoContabilidad = document.getElementById('obligadoContabilidad').value;
            const agenteRetencion = document.getElementById('agenteRetencion').value;
            const contribuyenteEspecial = document.getElementById('contribuyenteEspecial').value;

            const successMsg = document.getElementById('registerSuccess');
            successMsg.classList.remove('text-red-600', 'text-green-600'); // Limpiar clases de color antes de establecer una nueva

            // Validaciones básicas de campos vacíos
            const requiredFields = [
                nuevoUsuario, nuevaContrasena, nuevoCorreo, nombreCompleto, nuevaCedula, nuevoRuc, nuevaPlaca,
                direccion, telefono, estadoCivil, fechaNacimiento, nacionalidad, actividadEconomica,
                tipoContribuyente, regimenTributario, categoriaTributaria, fechaInicioActividades,
                obligadoContabilidad, agenteRetencion, contribuyenteEspecial
            ];
            if (requiredFields.some(field => !field)) {
                successMsg.textContent = 'Todos los campos son obligatorios.';
                successMsg.classList.remove('hidden');
                successMsg.classList.add('text-red-600');
                return;
            }

            // Validaciones de unicidad contra TODOS los usuarios registrados
            if (usuariosRegistrados.find(u => u.usuario === nuevoUsuario)) {
                successMsg.textContent = 'El usuario ya existe.';
                successMsg.classList.remove('hidden');
                successMsg.classList.add('text-red-600');
                return;
            }
            if (usuariosRegistrados.find(u => u.cedula === nuevaCedula)) {
                successMsg.textContent = 'La cédula ya está registrada.';
                successMsg.classList.remove('hidden');
                successMsg.classList.add('text-red-600');
                return;
            }
            if (usuariosRegistrados.find(u => u.ruc === nuevoRuc)) {
                successMsg.textContent = 'El RUC ya está registrado.';
                successMsg.classList.remove('hidden');
                successMsg.classList.add('text-red-600');
                return;
            }
            if (usuariosRegistrados.find(u => u.placas.includes(nuevaPlaca))) {
                successMsg.textContent = 'La placa ya está registrada.';
                successMsg.classList.remove('hidden');
                successMsg.classList.add('text-red-600');
                return;
            }

            // Validaciones de formato
            if (!validarCedula(nuevaCedula)) {
                successMsg.textContent = 'Cédula inválida.';
                successMsg.classList.remove('hidden');
                successMsg.classList.add('text-red-600');
                return;
            }
            if (!validarRuc(nuevoRuc)) {
                successMsg.textContent = 'RUC inválido.';
                successMsg.classList.remove('hidden');
                successMsg.classList.add('text-red-600');
                return;
            }
            if (!validarPlaca(nuevaPlaca)) {
                successMsg.textContent = 'Placa inválida.';
                successMsg.classList.remove('hidden');
                successMsg.classList.add('text-red-600');
                return;
            }

            usuariosRegistrados.push({
                usuario: nuevoUsuario,
                contrasena: nuevaContrasena,
                correo: nuevoCorreo,
                cedula: nuevaCedula,
                ruc: nuevoRuc,
                placas: [nuevaPlaca],
                nombreCompleto: nombreCompleto,
                direccion: direccion,
                telefono: telefono,
                estadoCivil: estadoCivil,
                fechaNacimiento: fechaNacimiento,
                nacionalidad: nacionalidad,
                actividadEconomica: actividadEconomica,
                tipoContribuyente: tipoContribuyente,
                regimenTributario: regimenTributario,
                categoriaTributaria: categoriaTributaria,
                fechaInicioActividades: fechaInicioActividades,
                estadoRuc: 'ACTIVO', // Por defecto al registrar
                obligadoContabilidad: obligadoContabilidad,
                agenteRetencion: agenteRetencion,
                contribuyenteEspecial: contribuyenteEspecial,
                contribuyenteFantasma: 'NO', // Por defecto
                transaccionesInexistentes: 'NO' // Por defecto
            });

            guardarUsuarios(); // Guardar en localStorage
            successMsg.textContent = '¡Registro exitoso! Ahora puede iniciar sesión.';
            successMsg.classList.remove('hidden');
            successMsg.classList.add('text-green-600');
            document.getElementById('registerForm').reset();
        });

        // Menú de servicios
        document.querySelectorAll('.menu-btn').forEach(btn => {
            btn.addEventListener('click', function() {
                document.querySelectorAll('.service-section').forEach(sec => sec.classList.add('hidden'));
                document.querySelectorAll('.menu-btn').forEach(b => b.classList.remove('menu-item-active'));
                this.classList.add('menu-item-active');
                const section = this.getAttribute('data-section');
                document.getElementById('section-' + section).classList.remove('hidden');
                // Limpiar resultados anteriores al cambiar de sección
                document.querySelectorAll('[id^="resultado"]').forEach(div => div.innerHTML = '');
            });
        });

        // Mostrar sección por clic en menú visual
        function showSection(section) {
            document.querySelectorAll('.service-section').forEach(sec => sec.classList.add('hidden'));
            document.querySelectorAll('.menu-btn').forEach(b => b.classList.remove('menu-item-active'));
            document.getElementById('section-' + section).classList.remove('hidden');
            const correspondingMenuBtn = document.querySelector(`.menu-btn[data-section="${section}"]`);
            if (correspondingMenuBtn) {
                correspondingMenuBtn.classList.add('menu-item-active');
            }
            // Limpiar resultados anteriores al cambiar de sección
            document.querySelectorAll('[id^="resultado"]').forEach(div => div.innerHTML = '');
        }

        // Validaciones Ecuador
        function validarCedula(cedula) {
            if (!/^\d{10}$/.test(cedula)) return false;
            const provincia = parseInt(cedula.substring(0, 2), 10);
            if (provincia < 1 || provincia > 24) return false;
            const digitos = cedula.split('').map(Number);
            let suma = 0;
            for (let i = 0; i < 9; i++) {
                let val = digitos[i];
                if (i % 2 === 0) {
                    val *= 2;
                    if (val > 9) val -= 9;
                }
                suma += val;
            }
            const verificador = (10 - (suma % 10)) % 10;
            return verificador === digitos[9];
        }
        function validarRuc(ruc) {
            if (!/^\d{13}$/.test(ruc)) return false;
            const cedula = ruc.substring(0, 10);
            // Validar los primeros 10 dígitos como cédula si es RUC de persona natural
            if (ruc.substring(10, 13) === '001') {
                if (!validarCedula(cedula)) return false;
            }
            // Para RUC de sociedades o entidades públicas, la validación es más compleja
            // Aquí solo se hace una validación básica de longitud y que sea numérico
            return true;
        }
        function validarPlaca(placa) {
            return /^[A-Z]{3}\d{4}$/.test(placa.toUpperCase());
        }

        // Generador de nombre ficticio (para cuando no hay usuario logueado o el documento no le pertenece)
        function generarNombreFicticio(doc) {
            const nombres = ["Carlos", "María", "Pedro", "Luisa", "Andrea", "Jorge", "Sofía", "Miguel", "Daniel", "Elena"];
            const apellidos = ["García", "Torres", "Pérez", "Mendoza", "Ramírez", "Vera", "Cedeño", "Salazar", "Castro", "Ruiz"];
            const n = doc.split('').reduce((a, b) => a + parseInt(b || 0), 0);
            const nombre = nombres[n % nombres.length];
            const apellido = apellidos[n % apellidos.length];
            return `${nombre} ${apellido}`;
        }

        function generarFichaRucFicticia(ruc) {
            const nombre = generarNombreFicticio(ruc);
            const estados = ["ACTIVO", "SUSPENDIDO", "CANCELADO"];
            const actividades = [
                "SERVICIOS DE CONSULTORÍA EMPRESARIAL",
                "COMERCIO AL POR MAYOR DE ALIMENTOS",
                "DESARROLLO DE SOFTWARE",
                "SERVICIOS DE CONTABILIDAD",
                "ACTIVIDADES DE RESTAURANTES"
            ];
            const tipos = ["PERSONA NATURAL", "SOCIEDAD PRIVADA"];
            const regimenes = ["RIMPE", "GENERAL"];
            const categorias = ["EMPRENDEDOR", "NEGOCIO POPULAR", "CONTRIBUYENTE"];
            const fecha = `201${ruc[0] || 8}-0${(parseInt(ruc[1]) % 9) + 1}-0${(parseInt(ruc[2]) % 9) + 1}`;
            const obligadoContabilidad = (parseInt(ruc[3]) % 2 === 0) ? 'SI' : 'NO';
            const agenteRetencion = (parseInt(ruc[4]) % 3 === 0) ? 'SI' : 'NO';
            const contribuyenteEspecial = (parseInt(ruc[5]) % 4 === 0) ? 'SI' : 'NO';

            return {
                nombreCompleto: nombre,
                ruc: ruc,
                estadoRuc: estados[parseInt(ruc[3] || 0) % estados.length],
                actividadEconomica: actividades[parseInt(ruc[4] || 0) % actividades.length],
                tipoContribuyente: tipos[parseInt(ruc[5] || 0) % tipos.length],
                regimenTributario: regimenes[parseInt(ruc[6] || 0) % regimenes.length],
                categoriaTributaria: categorias[parseInt(ruc[7] || 0) % categorias.length],
                fechaInicioActividades: fecha,
                obligadoContabilidad: obligadoContabilidad,
                agenteRetencion: agenteRetencion,
                contribuyenteEspecial: contribuyenteEspecial,
                contribuyenteFantasma: 'NO',
                transaccionesInexistentes: 'NO',
                direccion: `Calle Ficticia ${ruc.substring(0,3)} y Avenida Imaginaria`,
                telefono: `09${ruc.substring(3,10)}`,
                estadoCivil: (parseInt(ruc[8]) % 2 === 0) ? 'Casado/a' : 'Soltero/a',
                fechaNacimiento: `19${ruc.substring(0,2)}-${(parseInt(ruc[3]) % 12) + 1}-${(parseInt(ruc[4]) % 28) + 1}`,
                nacionalidad: 'Ecuatoriana',
                correo: `ficticio_${ruc.substring(0,5)}@ejemplo.com`
            };
        }

        // Funciones de visualización de fichas (MODIFICADAS para validar usuario activo)
        function mostrarFichaRuc(doc) {
            const resultadoDiv = document.getElementById('resultadoRuc');
            let data = null;

            if (usuarioActivo && usuarioActivo.ruc === doc) {
                data = usuarioActivo;
            } else if (!usuarioActivo) {
                data = generarFichaRucFicticia(doc);
            } else {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Este RUC no corresponde a su cuenta.</span>
                    </div>
                `;
                return;
            }

            resultadoDiv.innerHTML = `
            <div class="bg-white rounded shadow p-6 mb-4">
                <h4 class="text-xl font-bold text-sri-blue mb-2">Consulta de RUC</h4>
                <div class="mb-2"><b>RUC:</b> ${data.ruc}</div>
                <div class="mb-2"><b>Razón social:</b> ${data.nombreCompleto}</div>
                <div class="mb-2"><b>Estado contribuyente en el RUC:</b> <span class="text-green-600 font-bold">${data.estadoRuc}</span></div>
                <div class="mb-2"><b>Actividad económica principal:</b> <span class="bg-sri-blue text-white px-2 py-1 rounded">${data.actividadEconomica}</span></div>
                <div class="mb-2"><b>Tipo contribuyente:</b> ${data.tipoContribuyente}</div>
                <div class="mb-2"><b>Régimen:</b> ${data.regimenTributario}</div>
                <div class="mb-2"><b>Categoría:</b> ${data.categoriaTributaria}</div>
                <div class="mb-2"><b>Fecha inicio actividades:</b> ${data.fechaInicioActividades}</div>
                <div class="grid grid-cols-2 gap-2 mt-4">
                    <div><b>Contribuyente fantasma:</b> ${data.contribuyenteFantasma}</div>
                    <div><b>Contribuyente con transacciones inexistentes:</b> ${data.transaccionesInexistentes}</div>
                    <div><b>Obligado a llevar contabilidad:</b> ${data.obligadoContabilidad}</div>
                    <div><b>Agente de retención:</b> ${data.agenteRetencion}</div>
                    <div><b>Contribuyente especial:</b> ${data.contribuyenteEspecial}</div>
                </div>
                <div class="mt-4">
                    <h5 class="text-lg font-bold text-sri-blue mb-2">Datos Adicionales</h5>
                    <div class="mb-2"><b>Dirección:</b> ${data.direccion}</div>
                    <div class="mb-2"><b>Teléfono:</b> ${data.telefono}</div>
                    <div class="mb-2"><b>Estado Civil:</b> ${data.estadoCivil}</div>
                    <div class="mb-2"><b>Fecha de Nacimiento:</b> ${data.fechaNacimiento}</div>
                    <div class="mb-2"><b>Nacionalidad:</b> ${data.nacionalidad}</div>
                    <div class="mb-2"><b>Correo:</b> ${data.correo}</div>
                </div>
            </div>
            `;
        }

        function mostrarFichaConsulta(doc) {
            const resultadoDiv = document.getElementById('resultadoConsulta');
            let data = null;

            if (usuarioActivo && (usuarioActivo.cedula === doc || usuarioActivo.ruc === doc)) {
                data = usuarioActivo;
            } else if (!usuarioActivo) {
                data = generarFichaRucFicticia(doc); // Reutilizamos la generación de RUC ficticio para datos personales
                data.estado = 'ACTIVO'; // Estado general para consulta
                data.tipo = data.tipoContribuyente; // Usar el tipo de contribuyente como tipo general
            } else {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Este documento no corresponde a su cuenta.</span>
                    </div>
                `;
                return;
            }

            resultadoDiv.innerHTML = `
            <div class="bg-white rounded shadow p-6 mb-4">
                <h4 class="text-xl font-bold text-sri-blue mb-2">Consulta por Cédula o RUC</h4>
                <div class="mb-2"><b>Documento:</b> ${doc}</div>
                <div class="mb-2"><b>Nombre Completo:</b> ${data.nombreCompleto}</div>
                <div class="mb-2"><b>Estado:</b> <span class="text-green-600 font-bold">${data.estadoRuc || data.estado}</span></div>
                <div class="mb-2"><b>Tipo:</b> ${data.tipoContribuyente || data.tipo}</div>
                <div class="mb-2"><b>Correo:</b> ${data.correo}</div>
                <div class="mt-4">
                    <h5 class="text-lg font-bold text-sri-blue mb-2">Información Personal</h5>
                    <div class="mb-2"><b>Dirección:</b> ${data.direccion}</div>
                    <div class="mb-2"><b>Teléfono:</b> ${data.telefono}</div>
                    <div class="mb-2"><b>Estado Civil:</b> ${data.estadoCivil}</div>
                    <div class="mb-2"><b>Fecha de Nacimiento:</b> ${data.fechaNacimiento}</div>
                    <div class="mb-2"><b>Nacionalidad:</b> ${data.nacionalidad}</div>
                </div>
            </div>
            `;
        }

        function mostrarFichaPagos(doc) {
            const resultadoDiv = document.getElementById('resultadoPagos');
            let nombreMostrar;

            if (usuarioActivo && (usuarioActivo.cedula === doc || usuarioActivo.ruc === doc)) {
                nombreMostrar = usuarioActivo.nombreCompleto;
            } else if (!usuarioActivo) {
                nombreMostrar = generarNombreFicticio(doc);
            } else {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Este documento no corresponde a su cuenta para consultar pagos.</span>
                    </div>
                `;
                return;
            }

            resultadoDiv.innerHTML = `
            <div class="bg-white rounded shadow p-6 mb-4">
                <h4 class="text-xl font-bold text-sri-blue mb-2">Pagos</h4>
                <div class="mb-2"><b>Documento:</b> ${doc}</div>
                <div class="mb-2"><b>Nombre:</b> ${nombreMostrar}</div>
                <div class="mb-2"><b>Estado de pagos:</b> <span class="text-green-600 font-bold">Pagos al día</span></div>
                <div class="mt-4">
                    <h5 class="text-lg font-bold text-sri-blue mb-2">Detalle de Pagos Recientes</h5>
                    <ul>
                        <li>Impuesto a la Renta 2023: Pagado el 2024-03-20</li>
                        <li>IVA Febrero 2024: Pagado el 2024-03-10</li>
                        <li>Impuesto Predial 2024: Pagado el 2024-01-05</li>
                    </ul>
                </div>
            </div>
            `;
        }

        function mostrarFichaDeudas(doc) {
            const resultadoDiv = document.getElementById('resultadoDeudas');
            let nombreMostrar;

            if (usuarioActivo && (usuarioActivo.cedula === doc || usuarioActivo.ruc === doc)) {
                nombreMostrar = usuarioActivo.nombreCompleto;
            } else if (!usuarioActivo) {
                nombreMostrar = generarNombreFicticio(doc);
            } else {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Este documento no corresponde a su cuenta para consultar deudas.</span>
                    </div>
                `;
                return;
            }

            resultadoDiv.innerHTML = `
            <div class="bg-white rounded shadow p-6 mb-4">
                <h4 class="text-xl font-bold text-sri-blue mb-2">Deudas</h4>
                <div class="mb-2"><b>Documento:</b> ${doc}</div>
                <div class="mb-2"><b>Nombre:</b> ${nombreMostrar}</div>
                <div class="mb-2"><b>Estado de deudas:</b> <span class="text-green-600 font-bold">Sin deudas pendientes</span></div>
                <div class="mt-4">
                    <h5 class="text-lg font-bold text-sri-blue mb-2">Historial de Deudas</h5>
                    <p>No se registran deudas tributarias pendientes a la fecha.</p>
                </div>
            </div>
            `;
        }

        function mostrarFichaTramites(doc) {
            const resultadoDiv = document.getElementById('resultadoTramites');
            let nombreMostrar;

            if (usuarioActivo && (usuarioActivo.cedula === doc || usuarioActivo.ruc === doc)) {
                nombreMostrar = usuarioActivo.nombreCompleto;
            } else if (!usuarioActivo) {
                nombreMostrar = generarNombreFicticio(doc);
            } else {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Este documento no corresponde a su cuenta para consultar trámites.</span>
                    </div>
                `;
                return;
            }

            resultadoDiv.innerHTML = `
            <div class="bg-white rounded shadow p-6 mb-4">
                <h4 class="text-xl font-bold text-sri-blue mb-2">Trámites</h4>
                <div class="mb-2"><b>Documento:</b> ${doc}</div>
                <div class="mb-2"><b>Nombre:</b> ${nombreMostrar}</div>
                <div class="mb-2"><b>Estado de trámite:</b> <span class="text-green-600 font-bold">Trámite de actualización de RUC completado (2024-02-15)</span></div>
                <div class="mt-4">
                    <h5 class="text-lg font-bold text-sri-blue mb-2">Trámites Recientes</h5>
                    <ul>
                        <li>Solicitud de Certificado de Cumplimiento Tributario: Aprobado (2024-03-01)</li>
                        <li>Actualización de Dirección Domiciliaria: Completado (2024-02-20)</li>
                    </ul>
                </div>
            </div>
            `;
        }

        function mostrarFichaVehiculos(placa) {
            const resultadoDiv = document.getElementById('resultadoVehiculos');
            let nombreMostrar;

            if (usuarioActivo && usuarioActivo.placas.includes(placa.toUpperCase())) {
                nombreMostrar = usuarioActivo.nombreCompleto;
            } else if (!usuarioActivo) {
                nombreMostrar = generarNombreFicticio(placa);
            } else {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Esta placa no está asociada a su cuenta.</span>
                    </div>
                `;
                return;
            }

            const modelo = (parseInt(placa[3]) % 2 === 0) ? 'Toyota Corolla' : 'Chevrolet Sail';
            const anio = `20${(parseInt(placa[4]) % 2) + 20}`; // 2020 o 2021
            const color = (parseInt(placa[5]) % 2 === 0) ? 'Blanco' : 'Gris';

            resultadoDiv.innerHTML = `
            <div class="bg-white rounded shadow p-6 mb-4">
                <h4 class="text-xl font-bold text-sri-blue mb-2">Vehículo</h4>
                <div class="mb-2"><b>Placa:</b> ${placa}</div>
                <div class="mb-2"><b>Propietario:</b> ${nombreMostrar}</div>
                <div class="mb-2"><b>Marca y Modelo:</b> ${modelo}</div>
                <div class="mb-2"><b>Año de Fabricación:</b> ${anio}</div>
                <div class="mb-2"><b>Color:</b> ${color}</div>
                <div class="mb-2"><b>Estado:</b> <span class="text-green-600 font-bold">Sin multas pendientes</span></div>
                <div class="mt-4">
                    <h5 class="text-lg font-bold text-sri-blue mb-2">Historial de Matriculación</h5>
                    <ul>
                        <li>Matriculación 2024: Pagada y al día</li>
                        <li>Revisión Técnica Vehicular: Aprobada (2024-01-10)</li>
                    </ul>
                </div>
            </div>
            `;
        }

        function mostrarFichaReporte(placa) {
            const resultadoDiv = document.getElementById('resultadoReporte');
            let nombreMostrar;

            if (usuarioActivo && usuarioActivo.placas.includes(placa.toUpperCase())) {
                nombreMostrar = usuarioActivo.nombreCompleto;
            } else if (!usuarioActivo) {
                nombreMostrar = generarNombreFicticio(placa);
            } else {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Esta placa no está asociada a su cuenta para generar reportes.</span>
                    </div>
                `;
                return;
            }

            const valorMatricula = (parseInt(placa[3]) * 10 + parseInt(placa[4])) * 5 + 50; // Valor ficticio
            const valorRodaje = 15;
            const valorTotal = valorMatricula + valorRodaje;

            resultadoDiv.innerHTML = `
            <div class="bg-white rounded shadow p-6 mb-4">
                <h4 class="text-xl font-bold text-sri-blue mb-2">Reporte de Pago Vehicular</h4>
                <div class="mb-2"><b>Placa:</b> ${placa}</div>
                <div class="mb-2"><b>Propietario:</b> ${nombreMostrar}</div>
                <div class="mb-2"><b>Estado de pagos:</b> <span class="text-green-600 font-bold">Pagos al día</span></div>
                <div class="mt-4">
                    <h5 class="text-lg font-bold text-sri-blue mb-2">Detalle de Valores a Pagar (Año Actual)</h5>
                    <ul>
                        <li>Valor de Matriculación: \$${valorMatricula.toFixed(2)}</li>
                        <li>Impuesto al Rodaje: \$${valorRodaje.toFixed(2)}</li>
                        <li>Multas y Recargos: \$0.00</li>
                    </ul>
                    <p class="text-lg font-bold mt-2">Total a Pagar: \$${valorTotal.toFixed(2)}</p>
                    <p class="text-sm text-gray-500 mt-2">Último pago registrado: 2024-01-15</p>
                </div>
            </div>
            `;
        }

        // Event Listeners para los formularios de consulta
        document.getElementById('formConsulta').addEventListener('submit', function(e) {
            e.preventDefault();
            const documento = document.getElementById('consultaDocumento').value.trim();
            const error = document.getElementById('errorConsultaDocumento');

            if (documento.length === 10 && !validarCedula(documento)) {
                error.classList.remove('hidden');
                error.textContent = 'Cédula inválida';
                return;
            }
            if (documento.length === 13 && !validarRuc(documento)) {
                error.classList.remove('hidden');
                error.textContent = 'RUC inválido';
                return;
            }
            if (documento.length !== 10 && documento.length !== 13) {
                error.classList.remove('hidden');
                error.textContent = 'Documento debe ser Cédula (10 dígitos) o RUC (13 dígitos)';
                return;
            }

            error.classList.add('hidden');
            mostrarFichaConsulta(documento);
            this.reset();
        });

        document.getElementById('formRuc').addEventListener('submit', function(e) {
            e.preventDefault();
            const ruc = document.getElementById('rucConsulta').value.trim();
            const error = document.getElementById('errorRucConsulta');
            if (!validarRuc(ruc)) {
                error.classList.remove('hidden');
                error.textContent = 'RUC inválido';
                return;
            }
            error.classList.add('hidden');

            mostrarFichaRuc(ruc);
            this.reset();
        });

        document.getElementById('formPagos').addEventListener('submit', function(e) {
            e.preventDefault();
            const documento = document.getElementById('pagosDocumento').value.trim();
            const error = document.getElementById('errorPagosDocumento');

            if (documento.length === 10 && !validarCedula(documento)) {
                error.classList.remove('hidden');
                error.textContent = 'Cédula inválida';
                return;
            }
            if (documento.length === 13 && !validarRuc(documento)) {
                error.classList.remove('hidden');
                error.textContent = 'RUC inválido';
                return;
            }
            if (documento.length !== 10 && documento.length !== 13) {
                error.classList.remove('hidden');
                error.textContent = 'Documento debe ser Cédula (10 dígitos) o RUC (13 dígitos)';
                return;
            }

            error.classList.add('hidden');
            mostrarFichaPagos(documento);
            this.reset();
        });

        document.getElementById('formDeudas').addEventListener('submit', function(e) {
            e.preventDefault();
            const documento = document.getElementById('deudasDocumento').value.trim();
            const error = document.getElementById('errorDeudasDocumento');

            if (documento.length === 10 && !validarCedula(documento)) {
                error.classList.remove('hidden');
                error.textContent = 'Cédula inválida';
                return;
            }
            if (documento.length === 13 && !validarRuc(documento)) {
                error.classList.remove('hidden');
                error.textContent = 'RUC inválido';
                return;
            }
            if (documento.length !== 10 && documento.length !== 13) {
                error.classList.remove('hidden');
                error.textContent = 'Documento debe ser Cédula (10 dígitos) o RUC (13 dígitos)';
                return;
            }

            error.classList.add('hidden');
            mostrarFichaDeudas(documento);
            this.reset();
        });

        document.getElementById('formTramites').addEventListener('submit', function(e) {
            e.preventDefault();
            const documento = document.getElementById('tramitesDocumento').value.trim();
            const error = document.getElementById('errorTramitesDocumento');

            if (documento.length === 10 && !validarCedula(documento)) {
                error.classList.remove('hidden');
                error.textContent = 'Cédula inválida';
                return;
            }
            if (documento.length === 13 && !validarRuc(documento)) {
                error.classList.remove('hidden');
                error.textContent = 'RUC inválido';
                return;
            }
            if (documento.length !== 10 && documento.length !== 13) {
                error.classList.remove('hidden');
                error.textContent = 'Documento debe ser Cédula (10 dígitos) o RUC (13 dígitos)';
                return;
            }

            error.classList.add('hidden');
            mostrarFichaTramites(documento);
            this.reset();
        });

        document.getElementById('formVehiculos').addEventListener('submit', function(e) {
            e.preventDefault();
            const placa = document.getElementById('vehiculoPlaca').value.trim().toUpperCase();
            const error = document.getElementById('errorVehiculoPlaca');

            if (!validarPlaca(placa)) {
                error.classList.remove('hidden');
                error.textContent = 'Placa inválida (Ej: ABC1234)';
                return;
            }
            error.classList.add('hidden');
            mostrarFichaVehiculos(placa);
            this.reset();
        });

        document.getElementById('formReporte').addEventListener('submit', function(e) {
            e.preventDefault();
            const placa = document.getElementById('reportePlaca').value.trim().toUpperCase();
            const error = document.getElementById('errorReportePlaca');

            if (!validarPlaca(placa)) {
                error.classList.remove('hidden');
                error.textContent = 'Placa inválida (Ej: ABC1234)';
                return;
            }
            error.classList.add('hidden');
            mostrarFichaReporte(placa);
            this.reset();
        });

        // Funciones para Facturación Electrónica, Anexos y Claves (simuladas con mensajes)
        document.getElementById('formFacturacion').addEventListener('submit', function(e) {
            e.preventDefault();
            const clave = document.getElementById('facturaClave').value.trim();
            const error = document.getElementById('errorFacturaClave');
            const resultadoDiv = document.getElementById('resultadoFacturacion');

            if (clave.length !== 49 || !/^\d{49}$/.test(clave)) {
                error.classList.remove('hidden');
                error.textContent = 'Clave de acceso inválida (debe tener 49 dígitos numéricos).';
                resultadoDiv.innerHTML = ''; // Limpiar resultado anterior
                return;
            }
            error.classList.add('hidden');

            if (!usuarioActivo) {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Debe iniciar sesión para validar facturas.</span>
                    </div>
                `;
                return;
            }

            // Simulación de validación de factura
            const emisorRuc = clave.substring(10, 23);
            const fechaEmision = `${clave.substring(4, 6)}/${clave.substring(2, 4)}/20${clave.substring(0, 2)}`;
            const valorTotal = (Math.random() * 1000 + 10).toFixed(2);

            resultadoDiv.innerHTML = `
                <div class="bg-white rounded shadow p-6 mt-4">
                    <h4 class="text-xl font-bold text-sri-blue mb-2">Resultado Validación Factura</h4>
                    <div class="mb-2"><b>Clave de Acceso:</b> ${clave}</div>
                    <div class="mb-2"><b>Estado:</b> <span class="text-green-600 font-bold">Válida y Autorizada</span></div>
                    <div class="mb-2"><b>Emisor RUC:</b> ${emisorRuc}</div>
                    <div class="mb-2"><b>Fecha Emisión:</b> ${fechaEmision}</div>
                    <div class="mb-2"><b>Valor Total:</b> \$${valorTotal}</div>
                    <p class="text-sm text-gray-500 mt-2">Esta factura ha sido verificada con éxito en el sistema del SRI.</p>
                </div>
            `;
            this.reset();
        });

        document.getElementById('formDeclaracion').addEventListener('submit', function(e) {
            e.preventDefault();
            const ruc = document.getElementById('declaracionRuc').value.trim();
            const anio = document.getElementById('declaracionAnio').value.trim();
            const error = document.getElementById('errorDeclaracionRuc');
            const resultadoDiv = document.getElementById('resultadoDeclaracion');

            if (!validarRuc(ruc)) {
                error.classList.remove('hidden');
                error.textContent = 'RUC inválido';
                resultadoDiv.innerHTML = '';
                return;
            }
            error.classList.add('hidden');

            if (!usuarioActivo || usuarioActivo.ruc !== ruc) {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Solo puede enviar declaraciones para su propio RUC.</span>
                    </div>
                `;
                return;
            }

            resultadoDiv.innerHTML = `
                <div class="bg-white rounded shadow p-6 mt-4">
                    <h4 class="text-xl font-bold text-sri-blue mb-2">Resultado Declaración</h4>
                    <div class="mb-2"><b>RUC:</b> ${ruc}</div>
                    <div class="mb-2"><b>Año Fiscal:</b> ${anio}</div>
                    <div class="mb-2"><b>Estado:</b> <span class="text-green-600 font-bold">Declaración enviada con éxito</span></div>
                    <p class="text-sm text-gray-500 mt-2">Su declaración ha sido recibida y procesada por el SRI.</p>
                </div>
            `;
            this.reset();
        });

        document.getElementById('formAnexo').addEventListener('submit', function(e) {
            e.preventDefault();
            const ruc = document.getElementById('anexoRuc').value.trim();
            const periodo = document.getElementById('anexoPeriodo').value.trim();
            const error = document.getElementById('errorAnexoRuc');
            const resultadoDiv = document.getElementById('resultadoAnexo');

            if (!validarRuc(ruc)) {
                error.classList.remove('hidden');
                error.textContent = 'RUC inválido';
                resultadoDiv.innerHTML = '';
                return;
            }
            error.classList.add('hidden');

            if (!usuarioActivo || usuarioActivo.ruc !== ruc) {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Solo puede enviar anexos para su propio RUC.</span>
                    </div>
                `;
                return;
            }

            resultadoDiv.innerHTML = `
                <div class="bg-white rounded shadow p-6 mt-4">
                    <h4 class="text-xl font-bold text-sri-blue mb-2">Resultado Envío Anexo</h4>
                    <div class="mb-2"><b>RUC:</b> ${ruc}</div>
                    <div class="mb-2"><b>Período:</b> ${periodo}</div>
                    <div class="mb-2"><b>Estado:</b> <span class="text-green-600 font-bold">Anexo enviado y validado</span></div>
                    <p class="text-sm text-gray-500 mt-2">El anexo correspondiente al período ha sido recibido por el SRI.</p>
                </div>
            `;
            this.reset();
        });

        document.getElementById('formReintegro').addEventListener('submit', function(e) {
            e.preventDefault();
            const ruc = document.getElementById('reintegroRuc').value.trim();
            const error = document.getElementById('errorReintegroRuc');
            const resultadoDiv = document.getElementById('resultadoReintegro');

            if (!validarRuc(ruc)) {
                error.classList.remove('hidden');
                error.textContent = 'RUC inválido';
                resultadoDiv.innerHTML = '';
                return;
            }
            error.classList.add('hidden');

            if (!usuarioActivo || usuarioActivo.ruc !== ruc) {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Solo puede solicitar reintegros para su propio RUC.</span>
                    </div>
                `;
                return;
            }

            resultadoDiv.innerHTML = `
                <div class="bg-white rounded shadow p-6 mt-4">
                    <h4 class="text-xl font-bold text-sri-blue mb-2">Resultado Solicitud de Reintegro</h4>
                    <div class="mb-2"><b>RUC:</b> ${ruc}</div>
                    <div class="mb-2"><b>Estado:</b> <span class="text-green-600 font-bold">Solicitud de reintegro recibida</span></div>
                    <p class="text-sm text-gray-500 mt-2">Su solicitud de reintegro de valores está en proceso de revisión.</p>
                </div>
            `;
            this.reset();
        });

        document.getElementById('formClaves').addEventListener('submit', function(e) {
            e.preventDefault();
            const usuario = document.getElementById('clavesUsuario').value.trim();
            const resultadoDiv = document.getElementById('resultadoClaves');

            if (!usuarioActivo || usuarioActivo.usuario !== usuario) {
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Acceso Denegado:</strong>
                        <span class="block sm:inline">Solo puede gestionar la clave de su propio usuario.</span>
                    </div>
                `;
                return;
            }

            const userFound = usuariosRegistrados.find(u => u.usuario === usuario);
            if (userFound) {
                resultadoDiv.innerHTML = `
                    <div class="bg-white rounded shadow p-6 mt-4">
                        <h4 class="text-xl font-bold text-sri-blue mb-2">Recuperación de Clave</h4>
                        <div class="mb-2"><b>Usuario:</b> ${usuario}</div>
                        <div class="mb-2"><b>Estado:</b> <span class="text-green-600 font-bold">Instrucciones enviadas</span></div>
                        <p class="text-sm text-gray-500 mt-2">Se han enviado instrucciones para recuperar su clave al correo electrónico registrado: ${userFound.correo}.</p>
                    </div>
                `;
            } else {
                // Este caso no debería ocurrir si ya se validó que usuario === usuarioActivo.usuario
                // Pero se mantiene como fallback.
                resultadoDiv.innerHTML = `
                    <div class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative" role="alert">
                        <strong class="font-bold">Error:</strong>
                        <span class="block sm:inline">El usuario ingresado no se encuentra registrado en nuestro sistema.</span>
                    </div>
                `;
            }
            this.reset();
        });


        // Chart.js gráfico barras institucional (se mantiene sin cambios)
        document.addEventListener('DOMContentLoaded', function() {
            const graficoElement = document.getElementById('graficoSRI');
            if (graficoElement) {
                const ctx = graficoElement.getContext('2d');
                new Chart(ctx, {
                    type: 'bar',
                    data: {
                        labels: ['Consultas', 'Facturación', 'Vehículos', 'Pagos', 'Deudas'],
                        datasets: [{
                            label: 'Servicios usados',
                            data: [12, 19, 7, 14, 9],
                            backgroundColor: [
                                '#00548F',
                                '#4CAF50',
                                '#0069B3',
                                '#81C784',
                                '#00548F'
                            ],
                            borderRadius: 8
                        }]
                    },
                    options: {
                        plugins: {
                            legend: { display: false }
                        },
                        scales: {
                            y: { beginAtZero: true, ticks: { color: '#00548F' } },
                            x: { ticks: { color: '#00548F' } }
                        }
                    }
                });
            }
        });
    </script>
</body>
</html>
