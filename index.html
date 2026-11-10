<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cartografía Cimática — Datos en Arena</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Exclusivamente Montserrat -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@200;300;400;500;600;700&display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Montserrat', 'sans-serif'],
                    },
                    colors: {
                        signal: '#EAB308',
                        signalSoft: '#FDE047',
                        plate: '#121110',
                        sandLight: '#FAF6EE'
                    }
                }
            }
        }
    </script>

    <style>
        * {
            box-sizing: border-box;
            user-select: none;
            font-family: 'Montserrat', sans-serif;
        }
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            background-color: #121110;
            color: #EAB308;
            -webkit-font-smoothing: antialiased;
        }

        /* Lienzo de simulación de arena de cuarzo */
        #sandCanvas {
            position: absolute;
            inset: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        /* Textura sutil de placa negra mate como el póster de referencia */
        .plate-vignette {
            position: absolute;
            inset: 0;
            z-index: 2;
            pointer-events: none;
            background: radial-gradient(
                circle at 50% 50%,
                rgba(255, 250, 240, 0.01) 0%,
                rgba(16, 15, 14, 0.35) 75%,
                rgba(8, 7, 7, 0.78) 100%
            );
        }

        /* Sombra editorial limpia para máxima legibilidad sobre los granos de arena */
        .poster-text {
            text-shadow:
                0 2px 18px rgba(10, 9, 8, 0.96),
                0 1px 4px rgba(0, 0, 0, 0.98);
        }

        .ui-corner {
            position: fixed;
            z-index: 20;
            pointer-events: none;
        }
        .interactive {
            pointer-events: auto;
        }

        /* Botones de pictograma minimalistas sin cajas pesadas */
        .picto-btn {
            display: inline-flex;
            align-items: center;
            gap: 0.55rem;
            padding: 0.45rem 0.8rem;
            border-radius: 9999px;
            border: 1px solid rgba(234, 179, 8, 0.28);
            background: rgba(18, 17, 16, 0.72);
            backdrop-filter: blur(6px);
            color: rgba(234, 179, 8, 0.85);
            font-size: 11px;
            font-weight: 500;
            letter-spacing: 0.08em;
            transition: all 0.22s ease;
        }
        .picto-btn:hover {
            border-color: #EAB308;
            color: #FAF6EE;
            transform: translateY(-1px);
        }
        .picto-btn.active {
            background: #EAB308;
            border-color: #EAB308;
            color: #121110;
            font-weight: 600;
        }

        /* Chips de los 5 círculos del instrumento */
        .ring-pill {
            padding: 0.3rem 0.65rem;
            border-radius: 9999px;
            border: 1px solid rgba(234, 179, 8, 0.24);
            background: rgba(18, 17, 16, 0.68);
            color: rgba(234, 179, 8, 0.78);
            font-size: 10px;
            font-weight: 500;
            letter-spacing: 0.1em;
            transition: all 0.2s ease;
        }
        .ring-pill:hover {
            border-color: #EAB308;
            color: #FAF6EE;
        }
        .ring-pill.active {
            border-color: #EAB308;
            background: rgba(234, 179, 8, 0.22);
            color: #FDE047;
            font-weight: 600;
        }

        /* Pulso sutil del llamado a la acción en la portada */
        @keyframes subtlePulse {
            0%, 100% { opacity: 0.95; transform: translateX(0); }
            50% { opacity: 0.6; transform: translateX(3px); }
        }
        .cta-pulse {
            animation: subtlePulse 2.8s infinite ease-in-out;
        }
    </style>
</head>
<body class="w-screen h-screen overflow-hidden select-none">

    <!-- LIENZO DE ARENA DE CUARZO -->
    <canvas id="sandCanvas"></canvas>
    <div class="plate-vignette"></div>

    <!-- ==========================================================================
         ESQUINA SUPERIOR IZQUIERDA (top: 44px, left: 52px)
         Emblema geométrico amarillo de polígonos superpuestos (exacto al afiche)
         ========================================================================== -->
    <div class="ui-corner top-8 left-8 sm:top-12 sm:left-14 flex items-center gap-6">
        <button onclick="handleTopEmblemClick()" class="interactive group text-left focus:outline-none" title="Cambiar etapa / Volver">
            <svg id="harmonicEmblem" width="82" height="82" viewBox="-52 -52 104 104" class="overflow-visible transition-transform duration-500 group-hover:scale-105">
                <!-- Polígonos amarillos superpuestos generados dinámicamente -->
            </svg>
        </button>

        <!-- Botón minimalista de retorno cuando se está en Etapa 1 o Etapa 2 -->
        <div id="topNavActions" class="interactive hidden items-center gap-3 poster-text">
            <button id="backBtn" onclick="stepBack()" class="px-3.5 py-1.5 rounded-full border border-[#EAB308]/40 bg-[#121110]/75 text-[#EAB308] text-[10px] font-medium tracking-[0.16em] uppercase hover:border-[#EAB308] hover:text-[#FAF6EE] transition-all">
                ← Volver
            </button>
        </div>
    </div>

    <!-- ==========================================================================
         ESQUINA SUPERIOR DERECHA (top: 44px, right: 52px)
         Solo visible en Etapa 2 (Desglose de Lugar) para filtrar por Pictograma y Círculo
         ========================================================================== -->
    <div id="detailFiltersCorner" class="ui-corner top-8 right-8 sm:top-12 sm:right-14 hidden flex-col items-end gap-3.5 max-w-xl">
        <!-- Fila 1: Los 4 Pictogramas de Onda + Total -->
        <div class="interactive flex flex-wrap justify-end gap-2">
            <button onclick="setWaveFilter('todas')" id="wf-todas" class="picto-btn active">
                <span>Total</span>
                <span class="opacity-75" id="wfCount-todas">24</span>
            </button>

            <!-- 1. Naturaleza (Envolvente) -->
            <button onclick="setWaveFilter('envolvente')" id="wf-envolvente" class="picto-btn">
                <svg class="w-3.5 h-3.5 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
                    <path d="M2 13c2.5-3 5.5-3 8 0s5.5 3 8 0 3.5-2 4-1"/>
                    <path d="M12 3c-3.5 2-5 5.5-2 8 3-2.5 1.5-6-2-8z"/>
                </svg>
                <span>Naturaleza</span>
                <span class="opacity-75" id="wfCount-envolvente">11</span>
            </button>

            <!-- 2. Tráfico y Motores (Intensa) -->
            <button onclick="setWaveFilter('intensa')" id="wf-intensa" class="picto-btn">
                <svg class="w-3.5 h-3.5 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                    <polyline points="2 12 6 12 9 4 13 20 16 9 19 15 22 12"/>
                </svg>
                <span>Tráfico</span>
                <span class="opacity-75" id="wfCount-intensa">7</span>
            </button>

            <!-- 3. Murmullo Humano (Abierta) -->
            <button onclick="setWaveFilter('abierta')" id="wf-abierta" class="picto-btn">
                <svg class="w-3.5 h-3.5 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
                    <circle cx="9" cy="10" r="3"/>
                    <path d="M16 6a6 6 0 0 1 0 9"/>
                    <path d="M19.5 3.5a10 10 0 0 1 0 14"/>
                </svg>
                <span>Voces</span>
                <span class="opacity-75" id="wfCount-abierta">4</span>
            </button>

            <!-- 4. Puerto y Señales (Fugaz) -->
            <button onclick="setWaveFilter('fugaz')" id="wf-fugaz" class="picto-btn">
                <svg class="w-3.5 h-3.5 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round">
                    <circle cx="12" cy="12" r="2.2"/>
                    <path d="M12 2v4M12 18v4M2 12h4M18 12h4M5 5l3 3M16 16l3 3M19 5l-3 3M8 16l-3 3"/>
                </svg>
                <span>Puerto</span>
                <span class="opacity-75" id="wfCount-fugaz">2</span>
            </button>
        </div>

        <!-- Fila 2: Los 5 Círculos del Instrumento (C1 a C5) -->
        <div class="interactive flex flex-wrap justify-end items-center gap-1.5">
            <span class="text-[9px] font-medium tracking-[0.18em] uppercase text-[#EAB308]/65 mr-1 poster-text">Círculos:</span>
            <button onclick="setRingFilter(0)" id="rf-0" class="ring-pill active">C1–C5</button>
            <button onclick="setRingFilter(1)" id="rf-1" class="ring-pill">C1 (<span id="rfCount-1">2</span>)</button>
            <button onclick="setRingFilter(2)" id="rf-2" class="ring-pill">C2 (<span id="rfCount-2">4</span>)</button>
            <button onclick="setRingFilter(3)" id="rf-3" class="ring-pill">C3 (<span id="rfCount-3">6</span>)</button>
            <button onclick="setRingFilter(4)" id="rf-4" class="ring-pill">C4 (<span id="rfCount-4">7</span>)</button>
            <button onclick="setRingFilter(5)" id="rf-5" class="ring-pill">C5 (<span id="rfCount-5">5</span>)</button>
        </div>

        <!-- Etiqueta cuando se aísla a 1 persona -->
        <button id="clearPersonBtn" onclick="clearIsolatedPerson()" class="interactive hidden px-3 py-1 rounded-full bg-[#EAB308] text-[#121110] text-[10px] font-semibold tracking-[0.12em] uppercase">
            Restaurar grupo ✕
        </button>
    </div>

    <!-- ==========================================================================
         ESQUINA INFERIOR IZQUIERDA (bottom: 48px, left: 52px)
         Diagramación idéntica al bloque izquierdo de "Sound Image Handel"
         ========================================================================== -->
    <div class="ui-corner bottom-9 left-8 sm:bottom-13 sm:left-14 max-w-md poster-text">

        <!-- Bloque principal de 5 líneas con la jerarquía del afiche de referencia -->
        <div class="space-y-0.5 text-[#EAB308] leading-[1.32] tracking-[-0.01em]">
            <div id="posterLine1" class="text-xl sm:text-[26px] font-semibold">
                Cartografía Cimática
            </div>
            <div id="posterLine2" class="text-lg sm:text-[22px] font-normal">
                Percepción en ondas de arena
            </div>
            <div id="posterLine3" class="text-base sm:text-[20px] font-light opacity-95">
                62 registros en tres territorios
            </div>
            <div id="posterLine4" class="text-base sm:text-[20px] font-light opacity-95">
                Sotomayor, Muelle Prat,
            </div>
            <div id="posterLine5" class="text-base sm:text-[20px] font-light opacity-95">
                Buenos Aires
            </div>
        </div>

        <!-- Leyenda compacta de los 4 Pictogramas + Pie de acción (como el pie pequeño del afiche) -->
        <div class="mt-6 space-y-3">
            <!-- Mini-fila de los 4 pictogramas siempre comprensibles -->
            <div class="flex flex-wrap items-center gap-x-4 gap-y-1.5 text-[10px] font-normal tracking-[0.06em] text-[#EAB308]/85">
                <span class="inline-flex items-center gap-1.5">
                    <svg class="w-3 h-3" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M2 13c2.5-3 5.5-3 8 0s5.5 3 8 0"/><path d="M12 3c-3 2-4 5-2 7 2-2 1-5-2-7z"/></svg>
                    Naturaleza
                </span>
                <span class="inline-flex items-center gap-1.5">
                    <svg class="w-3 h-3" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="2 12 6 12 9 4 14 20 18 10 22 12"/></svg>
                    Tráfico
                </span>
                <span class="inline-flex items-center gap-1.5">
                    <svg class="w-3 h-3" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="8" cy="10" r="3"/><path d="M15 6a6 6 0 0 1 0 9"/></svg>
                    Voces
                </span>
                <span class="inline-flex items-center gap-1.5">
                    <svg class="w-3 h-3" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="2"/><path d="M12 2v4M12 18v4M2 12h4M18 12h4"/></svg>
                    Puerto
                </span>
            </div>

            <!-- Pie de dos líneas al estilo "All concerts of the new season..." -->
            <div class="interactive pt-1">
                <button id="posterSmallCta" onclick="handlePrimaryAction()" class="text-left group focus:outline-none">
                    <div id="smallCaption1" class="text-[11px] sm:text-xs font-normal tracking-[0.02em] text-[#EAB308] cta-pulse group-hover:underline">
                        Click en la placa para ingresar al total →
                    </div>
                    <div id="smallCaption2" class="text-[11px] sm:text-xs font-light tracking-[0.02em] text-[#EAB308]/80">
                        4 pictogramas de onda · 5 círculos de intensidad
                    </div>
                </button>
            </div>
        </div>
    </div>

    <!-- ==========================================================================
         ESQUINA INFERIOR DERECHA (bottom: 48px, right: 52px)
         Firma limpia en dos líneas idéntica a "Berliner Philharmoniker"
         ========================================================================== -->
    <div class="ui-corner bottom-9 right-8 sm:bottom-13 sm:right-14 flex flex-col items-end gap-4 poster-text">

        <!-- Navegación rápida y limpia entre lugares -->
        <nav id="QuickPlaceNav" class="interactive hidden sm:flex items-center gap-5 text-[11px] font-medium tracking-[0.08em] text-[#EAB308]/75">
            <button onclick="goToStage('overview')" id="nav-overview" class="hover:text-[#FAF6EE] transition-colors">
                Total (62)
            </button>
            <button onclick="enterPlaceDetail('sotomayor')" id="nav-sotomayor" class="hover:text-[#FAF6EE] transition-colors">
                Sotomayor (24)
            </button>
            <button onclick="enterPlaceDetail('muelle')" id="nav-muelle" class="hover:text-[#FAF6EE] transition-colors">
                Muelle Prat (20)
            </button>
            <button onclick="enterPlaceDetail('buenosaires')" id="nav-buenosaires" class="hover:text-[#FAF6EE] transition-colors">
                Buenos Aires (18)
            </button>
        </nav>

        <!-- Firma editorial de dos líneas en amarillo -->
        <div onclick="handlePrimaryAction()" class="interactive cursor-pointer text-right leading-[1.18] tracking-[-0.01em] text-[#EAB308]">
            <div id="brandRightLine1" class="text-lg sm:text-[23px] font-semibold">
                Visualización
            </div>
            <div id="brandRightLine2" class="text-lg sm:text-[23px] font-semibold">
                Datos en Arena
            </div>
        </div>
    </div>

    <script>
        /**
         * ============================================================================
         * 1. DEFINICIÓN DE LOS 4 PICTOGRAMAS Y DATOS FIJOS DETERMINISTAS (N = 62)
         * ============================================================================
         */
        const WAVE_TYPES = {
            envolvente: {
                key: 'envolvente',
                pictogramName: 'Naturaleza',
                waveQuality: 'Onda Envolvente',
                lobes: 4,          // Cuadrilobular armónica como el afiche de Handel
                kRadial: 2.22,
                lobeAmp: 0.46,
                innerRing: 0.24,
                emblemSides: 4
            },
            intensa: {
                key: 'intensa',
                pictogramName: 'Tráfico',
                waveQuality: 'Onda Intensa',
                lobes: 6,          // Estrella hexagonal de alta frecuencia
                kRadial: 3.12,
                lobeAmp: 0.52,
                innerRing: 0.16,
                emblemSides: 6
            },
            abierta: {
                key: 'abierta',
                pictogramName: 'Voces',
                waveQuality: 'Onda Abierta',
                lobes: 2,          // Bipolar abierta hacia el horizonte
                kRadial: 1.72,
                lobeAmp: 0.48,
                innerRing: 0.20,
                emblemSides: 3
            },
            fugaz: {
                key: 'fugaz',
                pictogramName: 'Puerto',
                waveQuality: 'Onda Fugaz',
                lobes: 8,          // Octogonal de pulsos breves
                kRadial: 2.75,
                lobeAmp: 0.55,
                innerRing: 0.14,
                emblemSides: 8
            }
        };

        const INTENSITY_RINGS = [
            { level: 1, short: 'C1', label: 'Intensidad 1 · Muy Baja', radiusNorm: 0.22 },
            { level: 2, short: 'C2', label: 'Intensidad 2 · Baja',     radiusNorm: 0.38 },
            { level: 3, short: 'C3', label: 'Intensidad 3 · Media',    radiusNorm: 0.54 },
            { level: 4, short: 'C4', label: 'Intensidad 4 · Alta',     radiusNorm: 0.71 },
            { level: 5, short: 'C5', label: 'Intensidad 5 · Máxima',   radiusNorm: 0.88 }
        ];

        // DATOS FIJOS CERRADOS (Sotomayor = 24, Muelle Prat = 20, Buenos Aires = 18 -> Total = 62)
        const PLACES_DATA = {
            sotomayor: {
                id: 'sotomayor',
                name: 'Plaza Sotomayor',
                subtitle: 'Confluencia urbana y eco patrimonial',
                // Posición asimétrica en Etapa 1: Mayor tamaño (N=24), arriba-izquierda
                layoutRatio: { x: 0.28, y: 0.37, sizeScale: 1.18 },
                people: [
                    { id: 'S-01', ring: 1, wave: 'envolvente', angle: 0.45, freqMod: 1.00, note: 'Brisa húmeda contenida en el centro.' },
                    { id: 'S-02', ring: 1, wave: 'fugaz',      angle: 3.60, freqMod: 0.95, note: 'Eco lejano de buque desde la dársena.' },
                    { id: 'S-03', ring: 2, wave: 'envolvente', angle: 0.95, freqMod: 1.02, note: 'Aire costero envolvente entre fachadas.' },
                    { id: 'S-04', ring: 2, wave: 'abierta',    angle: 2.35, freqMod: 0.98, note: 'Voces tranquilas hacia el muelle.' },
                    { id: 'S-05', ring: 2, wave: 'envolvente', angle: 4.10, freqMod: 1.04, note: 'Sensación envolvente en la explanada.' },
                    { id: 'S-06', ring: 2, wave: 'fugaz',      angle: 5.50, freqMod: 0.92, note: 'Señal breve sobre adoquines.' },
                    { id: 'S-07', ring: 3, wave: 'envolvente', angle: 0.30, freqMod: 1.00, note: 'Viento que rebota en las cuatro esquinas.' },
                    { id: 'S-08', ring: 3, wave: 'intensa',    angle: 1.35, freqMod: 1.06, note: 'Flujo constante por calle Serrano.' },
                    { id: 'S-09', ring: 3, wave: 'envolvente', angle: 2.40, freqMod: 0.97, note: 'Resonancia natural como anfiteatro.' },
                    { id: 'S-10', ring: 3, wave: 'abierta',    angle: 3.45, freqMod: 1.01, note: 'Murmullo peatonal hacia el puerto.' },
                    { id: 'S-11', ring: 3, wave: 'envolvente', angle: 4.55, freqMod: 1.03, note: 'Corriente marina que abraza la plaza.' },
                    { id: 'S-12', ring: 3, wave: 'intensa',    angle: 5.65, freqMod: 1.08, note: 'Pulso de buses en el eje arterial.' },
                    { id: 'S-13', ring: 4, wave: 'envolvente', angle: 0.15, freqMod: 1.05, note: 'Envolvimiento total desde los muros.' },
                    { id: 'S-14', ring: 4, wave: 'intensa',    angle: 1.05, freqMod: 1.10, note: 'Vibración intensa de tráfico.' },
                    { id: 'S-15', ring: 4, wave: 'envolvente', angle: 1.95, freqMod: 0.99, note: 'Reverberación profunda en piedra.' },
                    { id: 'S-16', ring: 4, wave: 'intensa',    angle: 2.85, freqMod: 1.07, note: 'Motores acelerando en el perímetro sur.' },
                    { id: 'S-17', ring: 4, wave: 'abierta',    angle: 3.75, freqMod: 0.96, note: 'Voces de grupos hacia la costanera.' },
                    { id: 'S-18', ring: 4, wave: 'envolvente', angle: 4.65, freqMod: 1.02, note: 'Cúpula sonora por la simetría urbana.' },
                    { id: 'S-19', ring: 4, wave: 'intensa',    angle: 5.55, freqMod: 1.11, note: 'Tráfico pesado reflejado en fachadas.' },
                    { id: 'S-20', ring: 5, wave: 'intensa',    angle: 0.65, freqMod: 1.14, note: 'Pico vehicular en el borde arterial.' },
                    { id: 'S-21', ring: 5, wave: 'envolvente', angle: 1.90, freqMod: 1.06, note: 'Máxima sensación envolvente central.' },
                    { id: 'S-22', ring: 5, wave: 'intensa',    angle: 3.15, freqMod: 1.12, note: 'Saturación de motores en acera oriente.' },
                    { id: 'S-23', ring: 5, wave: 'envolvente', angle: 4.40, freqMod: 1.04, note: 'Resonancia envolvente de gran amplitud.' },
                    { id: 'S-24', ring: 5, wave: 'abierta',    angle: 5.60, freqMod: 1.00, note: 'Gran apertura de voces hacia el mar.' }
                ]
            },

            muelle: {
                id: 'muelle',
                name: 'Muelle Prat',
                subtitle: 'Horizonte marítimo y voces abiertas',
                // Posición asimétrica en Etapa 1: Tamaño mediano (N=20), derecha-media/baja
                layoutRatio: { x: 0.73, y: 0.44, sizeScale: 1.02 },
                people: [
                    { id: 'M-01', ring: 1, wave: 'abierta',    angle: 0.80, freqMod: 0.96, note: 'Voces frente al agua hacia la bahía.' },
                    { id: 'M-02', ring: 1, wave: 'envolvente', angle: 2.90, freqMod: 0.94, note: 'Brisa marina suave al borde del muelle.' },
                    { id: 'M-03', ring: 1, wave: 'fugaz',      angle: 5.00, freqMod: 0.98, note: 'Gaviotas planeando sobre el agua.' },
                    { id: 'M-04', ring: 2, wave: 'abierta',    angle: 0.40, freqMod: 1.00, note: 'Murmullo abierto mirando los barcos.' },
                    { id: 'M-05', ring: 2, wave: 'envolvente', angle: 1.65, freqMod: 0.99, note: 'Vaivén envolvente del oleaje.' },
                    { id: 'M-06', ring: 2, wave: 'abierta',    angle: 2.90, freqMod: 0.97, note: 'Conversaciones que se abren al océano.' },
                    { id: 'M-07', ring: 2, wave: 'fugaz',      angle: 4.15, freqMod: 1.02, note: 'Campana puntual de embarcación.' },
                    { id: 'M-08', ring: 2, wave: 'abierta',    angle: 5.40, freqMod: 0.95, note: 'Propagación limpia de voces humanas.' },
                    { id: 'M-09', ring: 3, wave: 'abierta',    angle: 0.25, freqMod: 1.01, note: 'Llamados abiertos de lancheros.' },
                    { id: 'M-10', ring: 3, wave: 'envolvente', angle: 1.50, freqMod: 1.03, note: 'Mar y viento salino envolvente.' },
                    { id: 'M-11', ring: 3, wave: 'abierta',    angle: 2.75, freqMod: 0.98, note: 'Murmullo colectivo en la explanada.' },
                    { id: 'M-12', ring: 3, wave: 'fugaz',      angle: 4.00, freqMod: 1.04, note: 'Aves marinas y señales de amarre.' },
                    { id: 'M-13', ring: 3, wave: 'abierta',    angle: 5.25, freqMod: 1.00, note: 'Voces abiertas sin eco arquitectónico.' },
                    { id: 'M-14', ring: 4, wave: 'abierta',    angle: 0.90, freqMod: 1.05, note: 'Pregones abiertos hacia la bahía.' },
                    { id: 'M-15', ring: 4, wave: 'envolvente', angle: 2.45, freqMod: 1.02, note: 'Oleaje profundo bajo los pilotes.' },
                    { id: 'M-16', ring: 4, wave: 'intensa',    angle: 4.00, freqMod: 1.08, note: 'Motor diésel de lancha turística.' },
                    { id: 'M-17', ring: 4, wave: 'abierta',    angle: 5.55, freqMod: 1.03, note: 'Coro abierto de voces frente al mar.' },
                    { id: 'M-18', ring: 5, wave: 'intensa',    angle: 1.20, freqMod: 1.12, note: 'Remolcador cercano en maniobra.' },
                    { id: 'M-19', ring: 5, wave: 'abierta',    angle: 3.30, freqMod: 1.07, note: 'Onda abierta masiva en hora punta.' },
                    { id: 'M-20', ring: 5, wave: 'envolvente', angle: 5.10, freqMod: 1.05, note: 'Viento fuerte y mar envolvente.' }
                ]
            },

            buenosaires: {
                id: 'buenosaires',
                name: 'Buenos Aires',
                subtitle: 'Trama metropolitana y pulso continuo',
                // Posición asimétrica en Etapa 1: Tamaño menor (N=18), abajo-centro
                layoutRatio: { x: 0.49, y: 0.68, sizeScale: 0.90 },
                people: [
                    { id: 'B-01', ring: 1, wave: 'envolvente', angle: 1.10, freqMod: 0.98, note: 'Follaje amortiguando la ciudad.' },
                    { id: 'B-02', ring: 1, wave: 'abierta',    angle: 4.20, freqMod: 0.96, note: 'Conversación en apertura de parque.' },
                    { id: 'B-03', ring: 2, wave: 'envolvente', angle: 0.60, freqMod: 1.01, note: 'Brisa entre copas de árboles.' },
                    { id: 'B-04', ring: 2, wave: 'fugaz',      angle: 2.70, freqMod: 1.03, note: 'Timbre breve y señal peatonal.' },
                    { id: 'B-05', ring: 2, wave: 'abierta',    angle: 4.80, freqMod: 0.99, note: 'Murmullo humano en vereda.' },
                    { id: 'B-06', ring: 3, wave: 'intensa',    angle: 0.40, freqMod: 1.05, note: 'Flujo continuo de avenidas.' },
                    { id: 'B-07', ring: 3, wave: 'envolvente', angle: 1.95, freqMod: 1.02, note: 'Atmósfera contenida por fachadas.' },
                    { id: 'B-08', ring: 3, wave: 'fugaz',      angle: 3.50, freqMod: 1.06, note: 'Alertas breves en cruce diagonal.' },
                    { id: 'B-09', ring: 3, wave: 'intensa',    angle: 5.05, freqMod: 1.08, note: 'Vibración mecánica del subterráneo.' },
                    { id: 'B-10', ring: 4, wave: 'intensa',    angle: 0.20, freqMod: 1.09, note: 'Corredor de colectivos y tránsito.' },
                    { id: 'B-11', ring: 4, wave: 'envolvente', angle: 1.45, freqMod: 1.04, note: 'Cañón urbano envolvente.' },
                    { id: 'B-12', ring: 4, wave: 'intensa',    angle: 2.70, freqMod: 1.11, note: 'Motores intensos en el cruce.' },
                    { id: 'B-13', ring: 4, wave: 'fugaz',      angle: 3.95, freqMod: 1.07, note: 'Bocinas puntuales a lo lejos.' },
                    { id: 'B-14', ring: 4, wave: 'envolvente', angle: 5.20, freqMod: 1.03, note: 'Rumor denso al caer la tarde.' },
                    { id: 'B-15', ring: 5, wave: 'intensa',    angle: 0.85, freqMod: 1.14, note: 'Máxima vibración vehicular central.' },
                    { id: 'B-16', ring: 5, wave: 'intensa',    angle: 2.40, freqMod: 1.12, note: 'Frecuencia mecánica sobre asfalto.' },
                    { id: 'B-17', ring: 5, wave: 'envolvente', angle: 3.95, freqMod: 1.06, note: 'Inmersión acústica en hora pico.' },
                    { id: 'B-18', ring: 5, wave: 'intensa',    angle: 5.50, freqMod: 1.15, note: 'Resonancia máxima en anillo exterior.' }
                ]
            }
        };

        /**
         * ============================================================================
         * 2. MOTOR DE ARENA DE CUARZO FIJA Y DETERMINISTA (28,000 GRANOS)
         * ============================================================================
         */
        const PARTICLE_COUNT = 28000;
        let canvas, ctx;
        let width = window.innerWidth;
        let height = window.innerHeight;

        const px = new Float32Array(PARTICLE_COUNT);
        const py = new Float32Array(PARTICLE_COUNT);
        const vx = new Float32Array(PARTICLE_COUNT);
        const vy = new Float32Array(PARTICLE_COUNT);
        const pSize = new Float32Array(PARTICLE_COUNT);
        const pZoneAssign = new Uint8Array(PARTICLE_COUNT); // 0: Sotomayor, 1: Muelle, 2: BsAs

        const SAND_COLORS = [
            'rgba(252, 248, 240, 0.94)',
            'rgba(235, 228, 214, 0.88)',
            'rgba(216, 207, 188, 0.82)',
            'rgba(182, 172, 154, 0.74)',
            'rgba(255, 254, 250, 0.97)'
        ];

        // Etapas: 'intro' (Portada exacto al afiche) -> 'overview' (3 lugares en diversas alturas y tamaños en torno al total) -> 'detail' (Lugar individual)
        let currentStage = 'intro';
        let activePlaceKey = 'sotomayor';
        let activeWaveFilter = 'todas';
        let activeRingFilter = 0;
        let isolatedPerson = null;
        let hoveredItem = null;
        let settleEnergy = 1.0;

        const placeHarmonicSummary = {};

        window.onload = function () {
            canvas = document.getElementById('sandCanvas');
            ctx = canvas.getContext('2d');

            precomputeFixedSummaries();
            handleResize();

            window.addEventListener('resize', () => {
                handleResize();
                distributeParticlesForCurrentStage();
                settleImmediately();
            });

            initSandGrains();
            setupCanvasInteractions();
            settleImmediately();

            updatePosterTypography();
            updateHarmonicEmblem();
            requestAnimationFrame(renderLoop);
        };

        function precomputeFixedSummaries() {
            Object.keys(PLACES_DATA).forEach(key => {
                const people = PLACES_DATA[key].people;
                const total = people.length;
                const waveCounts = { envolvente: 0, intensa: 0, abierta: 0, fugaz: 0 };
                people.forEach(p => waveCounts[p.wave]++);

                const weights = {
                    envolvente: waveCounts.envolvente / total,
                    intensa: waveCounts.intensa / total,
                    abierta: waveCounts.abierta / total,
                    fugaz: waveCounts.fugaz / total
                };

                let dominantWave = 'envolvente';
                let maxC = -1;
                Object.keys(waveCounts).forEach(w => {
                    if (waveCounts[w] > maxC) {
                        maxC = waveCounts[w];
                        dominantWave = w;
                    }
                });

                placeHarmonicSummary[key] = { total, waveCounts, weights, dominantWave };
            });
        }

        function handleResize() {
            width = window.innerWidth;
            height = window.innerHeight;
            const dpr = Math.min(window.devicePixelRatio || 1, 2);
            canvas.width = width * dpr;
            canvas.height = height * dpr;
            ctx.scale(dpr, dpr);
        }

        function initSandGrains() {
            for (let i = 0; i < PARTICLE_COUNT; i++) {
                pSize[i] = (i % 5 === 0) ? 1.65 : 1.22;
                // Proporción exacta a N (24 / 62 = 39%, 20 / 62 = 32%, 18 / 62 = 29%)
                const mod = i % 62;
                if (mod < 24) pZoneAssign[i] = 0;
                else if (mod < 44) pZoneAssign[i] = 1;
                else pZoneAssign[i] = 2;
            }
            distributeParticlesForCurrentStage();
        }

        /**
         * GEOMETRÍA DE LAS 3 ETAPAS:
         * - Etapa 'intro': Gran placa a pantalla completa como el afiche de Handel.
         * - Etapa 'overview': Los 3 lugares en diversas alturas y tamaños proporcionales a su N (24, 20, 18) orbitando en torno a un núcleo central del Total (N=62).
         * - Etapa 'detail': Placa individual del lugar con sus 5 círculos concéntricos.
         */
        function getOverviewConstellationGeometry() {
            const isMobile = width < 768;
            const minDim = Math.min(width, height);
            const baseR = isMobile ? minDim * 0.165 : minDim * 0.145;

            // Centro de gravedad del Total (N = 62)
            const hubX = width * 0.49;
            const hubY = height * 0.47;

            if (isMobile) {
                return {
                    hub: { cx: width * 0.50, cy: height * 0.46, radius: baseR * 0.36 },
                    zones: [
                        // Sotomayor (N=24, el más grande, arriba-izquierda)
                        { key: 'sotomayor',   cx: width * 0.30, cy: height * 0.29, radius: baseR * 1.16 },
                        // Muelle Prat (N=20, mediano, derecha-medio)
                        { key: 'muelle',      cx: width * 0.72, cy: height * 0.43, radius: baseR * 1.00 },
                        // Buenos Aires (N=18, menor, abajo-izquierda/centro)
                        { key: 'buenosaires', cx: width * 0.43, cy: height * 0.65, radius: baseR * 0.88 }
                    ]
                };
            }

            return {
                hub: { cx: hubX, cy: hubY, radius: baseR * 0.38 },
                zones: [
                    // Sotomayor (N=24): Más grande, elevado a la izquierda
                    { key: 'sotomayor',   cx: width * 0.29, cy: height * 0.34, radius: baseR * 1.22 },
                    // Muelle Prat (N=20): Mediano, desplazado a la derecha a media altura
                    { key: 'muelle',      cx: width * 0.71, cy: height * 0.41, radius: baseR * 1.04 },
                    // Buenos Aires (N=18): Más compacto, en la parte inferior central
                    { key: 'buenosaires', cx: width * 0.48, cy: height * 0.71, radius: baseR * 0.92 }
                ]
            };
        }

        function getSinglePlateGeometry(isIntro = false) {
            const cx = width * 0.50;
            const cy = height * 0.49;
            const scale = isIntro ? 0.44 : (width < 640 ? 0.35 : 0.34);
            const radius = Math.min(width, height) * scale;
            return { cx, cy, radius };
        }

        function distributeParticlesForCurrentStage() {
            if (currentStage === 'overview') {
                const { zones } = getOverviewConstellationGeometry();
                for (let i = 0; i < PARTICLE_COUNT; i++) {
                    const z = zones[pZoneAssign[i]];
                    const a = (i * 1.6180339) % (Math.PI * 2);
                    const r = Math.sqrt(((i * 7919) % 10000) / 10000) * z.radius * 1.14;
                    px[i] = z.cx + Math.cos(a) * r;
                    py[i] = z.cy + Math.sin(a) * r;
                    vx[i] = 0;
                    vy[i] = 0;
                }
            } else {
                const plate = getSinglePlateGeometry(currentStage === 'intro');
                const spread = currentStage === 'intro' ? 1.45 : 1.12;
                for (let i = 0; i < PARTICLE_COUNT; i++) {
                    const a = (i * 1.6180339) % (Math.PI * 2);
                    const r = Math.sqrt(((i * 7919) % 10000) / 10000) * plate.radius * spread;
                    px[i] = plate.cx + Math.cos(a) * r;
                    py[i] = plate.cy + Math.sin(a) * r;
                    vx[i] = 0;
                    vy[i] = 0;
                }
            }
        }

        /**
         * ============================================================================
         * 3. ECUACIONES DE ONDA ESTACIONARIA (CHLADNI)
         * ============================================================================
         */
        function evaluateWaveMode(waveTypeObj, rNorm, theta, freqMod = 1.0) {
            const env = Math.min(1.0, Math.max(0.0, (rNorm - waveTypeObj.innerRing) * 1.48));
            const angular = waveTypeObj.lobeAmp * env * Math.cos(waveTypeObj.lobes * theta);
            return Math.sin(waveTypeObj.kRadial * freqMod * Math.PI * rNorm + angular * Math.PI);
        }

        // Ecuación de la Portada (Etapa 0): Figura cuadrilobular + anillo interior idéntica al póster Handel
        function evaluateIntroPosterWave(x, y, cx, cy, radius) {
            const nx = (x - cx) / radius;
            const ny = (y - cy) / radius;
            const r = Math.hypot(nx, ny);
            const theta = Math.atan2(ny, nx);

            if (r < 0.055) return 1.5;

            // Anillo circular interior limpio + Diamante redondeado de 4 lóbulos + Arcos en las esquinas
            const env = Math.min(1.0, Math.max(0.0, (r - 0.25) * 1.42));
            const angular = 0.45 * env * Math.cos(4 * theta);
            return Math.sin(2.22 * Math.PI * r + angular * Math.PI);
        }

        function evaluateZoneTotalWave(placeKey, x, y, cx, cy, radius) {
            const nx = (x - cx) / radius;
            const ny = (y - cy) / radius;
            const r = Math.hypot(nx, ny);
            const theta = Math.atan2(ny, nx);

            if (r < 0.08) return 1.4;
            if (r > 1.04) return (r - 1.04) * 3.0;

            const w = placeHarmonicSummary[placeKey].weights;
            let val = 0;
            val += w.envolvente * evaluateWaveMode(WAVE_TYPES.envolvente, r, theta);
            val += w.intensa    * evaluateWaveMode(WAVE_TYPES.intensa, r, theta);
            val += w.abierta    * evaluateWaveMode(WAVE_TYPES.abierta, r, theta);
            val += w.fugaz      * evaluateWaveMode(WAVE_TYPES.fugaz, r, theta);

            const outerBoundary = Math.sin(Math.PI * (r / 1.02));
            return val * 0.85 + outerBoundary * 0.15;
        }

        function evaluateDetailPlateWave(x, y, cx, cy, radius) {
            const nx = (x - cx) / radius;
            const ny = (y - cy) / radius;
            const r = Math.hypot(nx, ny);
            const theta = Math.atan2(ny, nx);

            if (r < 0.068) return 1.5;
            if (r > 1.08) return (r - 1.08) * 3.2;

            if (isolatedPerson) {
                const wObj = WAVE_TYPES[isolatedPerson.wave];
                const ringObj = INTENSITY_RINGS[isolatedPerson.ring - 1];
                const personWave = evaluateWaveMode(wObj, r, theta - isolatedPerson.angle, isolatedPerson.freqMod);
                const ringPull = Math.sin(((r - ringObj.radiusNorm) / 0.18) * Math.PI);
                return personWave * 0.65 + ringPull * 0.35;
            }

            const people = getFilteredPeopleInActivePlace();
            if (people.length === 0) return Math.sin(r * Math.PI * 3);

            const counts = { envolvente: 0, intensa: 0, abierta: 0, fugaz: 0 };
            people.forEach(p => counts[p.wave]++);
            const total = people.length;

            let waveSum = 0;
            if (counts.envolvente > 0) waveSum += (counts.envolvente / total) * evaluateWaveMode(WAVE_TYPES.envolvente, r, theta);
            if (counts.intensa > 0)    waveSum += (counts.intensa / total)    * evaluateWaveMode(WAVE_TYPES.intensa, r, theta);
            if (counts.abierta > 0)    waveSum += (counts.abierta / total)    * evaluateWaveMode(WAVE_TYPES.abierta, r, theta);
            if (counts.fugaz > 0)      waveSum += (counts.fugaz / total)      * evaluateWaveMode(WAVE_TYPES.fugaz, r, theta);

            if (activeRingFilter > 0) {
                const targetR = INTENSITY_RINGS[activeRingFilter - 1].radiusNorm;
                const distFromRing = Math.abs(r - targetR);
                if (distFromRing > 0.11) {
                    return (distFromRing - 0.05) * 2.4;
                }
            }
            return waveSum;
        }

        function stepSandSettlement(energyFactor) {
            if (energyFactor <= 0.001) return;
            const eps = 2.2;

            if (currentStage === 'intro') {
                const plate = getSinglePlateGeometry(true);
                for (let i = 0; i < PARTICLE_COUNT; i++) {
                    const isDust = (i % 9 === 0);
                    if (isDust && energyFactor < 0.38) continue;

                    let x = px[i], y = py[i];
                    const w0 = Math.abs(evaluateIntroPosterWave(x, y, plate.cx, plate.cy, plate.radius));
                    const wx = Math.abs(evaluateIntroPosterWave(x + eps, y, plate.cx, plate.cy, plate.radius)) - w0;
                    const wy = Math.abs(evaluateIntroPosterWave(x, y + eps, plate.cx, plate.cy, plate.radius)) - w0;

                    const pull = isDust ? 0.5 : 4.8;
                    vx[i] -= wx * pull;
                    vy[i] -= wy * pull;

                    const jitter = (w0 * 3.8 + 0.25) * energyFactor * (isDust ? 2.1 : 0.85);
                    vx[i] += (Math.random() - 0.5) * jitter;
                    vy[i] += (Math.random() - 0.5) * jitter;

                    vx[i] *= 0.64;
                    vy[i] *= 0.64;
                    px[i] += vx[i];
                    py[i] += vy[i];
                }
            } else if (currentStage === 'overview') {
                const { zones } = getOverviewConstellationGeometry();
                for (let i = 0; i < PARTICLE_COUNT; i++) {
                    const isDust = (i % 13 === 0);
                    if (isDust && energyFactor < 0.35) continue;

                    const z = zones[pZoneAssign[i]];
                    let x = px[i], y = py[i];

                    const w0 = Math.abs(evaluateZoneTotalWave(z.key, x, y, z.cx, z.cy, z.radius));
                    const wx = Math.abs(evaluateZoneTotalWave(z.key, x + eps, y, z.cx, z.cy, z.radius)) - w0;
                    const wy = Math.abs(evaluateZoneTotalWave(z.key, x, y + eps, z.cx, z.cy, z.radius)) - w0;

                    const pull = isDust ? 0.55 : 4.4;
                    vx[i] -= wx * pull;
                    vy[i] -= wy * pull;

                    const jitter = (w0 * 3.6 + 0.22) * energyFactor * (isDust ? 1.8 : 0.85);
                    vx[i] += (Math.random() - 0.5) * jitter;
                    vy[i] += (Math.random() - 0.5) * jitter;

                    vx[i] *= 0.65;
                    vy[i] *= 0.65;
                    px[i] += vx[i];
                    py[i] += vy[i];
                }
            } else {
                const plate = getSinglePlateGeometry(false);
                for (let i = 0; i < PARTICLE_COUNT; i++) {
                    const isDust = (i % 14 === 0);
                    if (isDust && energyFactor < 0.35) continue;

                    let x = px[i], y = py[i];
                    const w0 = Math.abs(evaluateDetailPlateWave(x, y, plate.cx, plate.cy, plate.radius));
                    const wx = Math.abs(evaluateDetailPlateWave(x + eps, y, plate.cx, plate.cy, plate.radius)) - w0;
                    const wy = Math.abs(evaluateDetailPlateWave(x, y + eps, plate.cx, plate.cy, plate.radius)) - w0;

                    const pull = isDust ? 0.55 : 4.6;
                    vx[i] -= wx * pull;
                    vy[i] -= wy * pull;

                    const jitter = (w0 * 4.0 + 0.24) * energyFactor * (isDust ? 1.9 : 0.85);
                    vx[i] += (Math.random() - 0.5) * jitter;
                    vy[i] += (Math.random() - 0.5) * jitter;

                    vx[i] *= 0.64;
                    vy[i] *= 0.64;
                    px[i] += vx[i];
                    py[i] += vy[i];
                }
            }
        }

        function settleImmediately() {
            for (let i = 0; i < 40; i++) {
                stepSandSettlement(0.72 * (1 - i / 40));
            }
            settleEnergy = 0.0;
        }

        function triggerGentleReorganization() {
            settleEnergy = 0.88;
            for (let s = 0; s < 16; s++) {
                stepSandSettlement(settleEnergy);
                settleEnergy *= 0.91;
            }
        }

        /**
         * ============================================================================
         * 4. RENDERIZADO VISUAL EN CANVAS
         * ============================================================================
         */
        function renderLoop() {
            if (settleEnergy > 0.004) {
                stepSandSettlement(settleEnergy);
                settleEnergy *= 0.90;
                if (settleEnergy <= 0.005) settleEnergy = 0;
            }

            ctx.fillStyle = '#121110';
            ctx.fillRect(0, 0, width, height);

            // Dibujar los 28,000 granos de arena de cuarzo
            for (let c = 0; c < SAND_COLORS.length; c++) {
                ctx.fillStyle = SAND_COLORS[c];
                ctx.beginPath();
                for (let i = c; i < PARTICLE_COUNT; i += SAND_COLORS.length) {
                    const s = pSize[i];
                    ctx.rect(px[i], py[i], s, s);
                }
                ctx.fill();
            }

            if (currentStage === 'intro') {
                const plate = getSinglePlateGeometry(true);
                drawHexBolt(plate.cx, plate.cy, 11.5);
            } else if (currentStage === 'overview') {
                renderOverviewConstellation();
            } else {
                renderDetailOverlay();
            }

            requestAnimationFrame(renderLoop);
        }

        // Etapa 1: Los 3 lugares en diversas alturas y tamaños orbitando en torno al Total (N=62)
        function renderOverviewConstellation() {
            const { hub, zones } = getOverviewConstellationGeometry();

            ctx.save();

            // 1. Filamentos capilares desde cada lugar hacia el núcleo del Total (N=62)
            zones.forEach(z => {
                const isHovered = hoveredItem && hoveredItem.type === 'zone' && hoveredItem.key === z.key;
                ctx.beginPath();
                ctx.setLineDash([3, 7]);
                ctx.strokeStyle = isHovered ? 'rgba(234, 179, 8, 0.7)' : 'rgba(234, 179, 8, 0.24)';
                ctx.lineWidth = isHovered ? 1.4 : 0.9;
                ctx.moveTo(hub.cx, hub.cy);
                ctx.lineTo(z.cx, z.cy);
                ctx.stroke();
            });
            ctx.setLineDash([]);

            // 2. Núcleo articulador del Total (N = 62) en el centro de la constelación
            ctx.beginPath();
            ctx.arc(hub.cx, hub.cy, 28, 0, Math.PI * 2);
            ctx.fillStyle = 'rgba(18, 17, 16, 0.88)';
            ctx.fill();
            ctx.strokeStyle = 'rgba(234, 179, 8, 0.55)';
            ctx.lineWidth = 1.2;
            ctx.stroke();

            ctx.textAlign = 'center';
            ctx.fillStyle = '#EAB308';
            ctx.font = '600 11px Montserrat';
            ctx.fillText('TOTAL', hub.cx, hub.cy - 3);
            ctx.font = '400 10px Montserrat';
            ctx.fillStyle = 'rgba(250, 246, 238, 0.85)';
            ctx.fillText('N = 62', hub.cx, hub.cy + 11);

            // 3. Dibujar cada una de las 3 placas en su altura y tamaño proporcional
            zones.forEach(z => {
                const place = PLACES_DATA[z.key];
                const summary = placeHarmonicSummary[z.key];
                const isHovered = hoveredItem && hoveredItem.type === 'zone' && hoveredItem.key === z.key;

                // Borde sutil de la placa
                ctx.beginPath();
                ctx.arc(z.cx, z.cy, z.radius * 1.02, 0, Math.PI * 2);
                ctx.strokeStyle = isHovered ? '#EAB308' : 'rgba(234, 179, 8, 0.30)';
                ctx.lineWidth = isHovered ? 1.9 : 1.0;
                ctx.stroke();

                // Perno metálico proporcional al tamaño de la placa
                drawHexBolt(z.cx, z.cy, 8.5 * (z.radius / 115));

                // Etiqueta limpia y aireada junto a cada círculo
                const labelY = z.cy - z.radius - 18;
                ctx.textAlign = 'center';
                ctx.fillStyle = '#EAB308';
                ctx.font = isHovered ? '600 13px Montserrat' : '500 12px Montserrat';
                ctx.fillText(`${place.name} (${summary.total})`, z.cx, labelY);

                ctx.fillStyle = isHovered ? '#FAF6EE' : 'rgba(234, 179, 8, 0.72)';
                ctx.font = '300 10.5px Montserrat';
                ctx.fillText(
                    isHovered ? 'Click para abrir círculos →' : WAVE_TYPES[summary.dominantWave].pictogramName,
                    z.cx,
                    z.cy + z.radius + 20
                );
            });

            ctx.restore();
        }

        // Etapa 2: Placa del lugar con sus 5 círculos de intensidad y las ondas de cada persona
        function renderDetailOverlay() {
            const plate = getSinglePlateGeometry(false);
            const place = PLACES_DATA[activePlaceKey];
            const filteredPeople = getFilteredPeopleInActivePlace();
            const filteredIds = new Set(filteredPeople.map(p => p.id));

            ctx.save();

            // 1. Los 5 Círculos concéntricos del instrumento
            INTENSITY_RINGS.forEach(ring => {
                const rPx = plate.radius * ring.radiusNorm;
                const isSelected = (activeRingFilter === ring.level);
                const isHovered = (hoveredItem && hoveredItem.type === 'ring' && hoveredItem.level === ring.level);

                ctx.beginPath();
                ctx.arc(plate.cx, plate.cy, rPx, 0, Math.PI * 2);

                if (isSelected || isHovered) {
                    ctx.strokeStyle = '#EAB308';
                    ctx.lineWidth = 1.6;
                    ctx.setLineDash([]);
                } else {
                    ctx.strokeStyle = activeRingFilter === 0 ? 'rgba(234, 179, 8, 0.24)' : 'rgba(234, 179, 8, 0.09)';
                    ctx.lineWidth = 0.85;
                    ctx.setLineDash([3, 6]);
                }
                ctx.stroke();
                ctx.setLineDash([]);

                // Numeración mínima C1..C5 en el eje vertical superior
                ctx.textAlign = 'center';
                ctx.font = (isSelected || isHovered) ? '600 9.5px Montserrat' : '400 9px Montserrat';
                ctx.fillStyle = (isSelected || isHovered) ? '#FDE047' : 'rgba(234, 179, 8, 0.55)';
                ctx.fillText(`C${ring.level}`, plate.cx, plate.cy - rPx - 5);
            });

            // 2. Nodos de personas y su onda estacionaria individual
            place.people.forEach(person => {
                const isIncluded = filteredIds.has(person.id) && (!isolatedPerson || isolatedPerson.id === person.id);
                const isHighlighted = (hoveredItem && hoveredItem.type === 'person' && hoveredItem.person.id === person.id) ||
                                      (isolatedPerson && isolatedPerson.id === person.id);

                const ringInfo = INTENSITY_RINGS[person.ring - 1];
                const waveInfo = WAVE_TYPES[person.wave];
                const baseR = plate.radius * ringInfo.radiusNorm;
                const pxNode = plate.cx + Math.cos(person.angle) * baseR;
                const pyNode = plate.cy + Math.sin(person.angle) * baseR;

                if (isIncluded) {
                    ctx.beginPath();
                    const arcSpan = isHighlighted ? Math.PI * 2 : 0.52;
                    const steps = isHighlighted ? 160 : 34;
                    const waveAmpPx = (5 + person.ring * 2.8) * (isHighlighted ? 1.4 : 0.8);

                    for (let s = 0; s <= steps; s++) {
                        const a = (person.angle - arcSpan / 2) + (s / steps) * arcSpan;
                        const env = isHighlighted ? 1.0 : Math.sin((s / steps) * Math.PI);
                        const osc = Math.sin((a - person.angle) * waveInfo.lobes * 2.4 * person.freqMod);
                        const rOsc = baseR + osc * waveAmpPx * env;
                        const wx = plate.cx + Math.cos(a) * rOsc;
                        const wy = plate.cy + Math.sin(a) * rOsc;
                        if (s === 0) ctx.moveTo(wx, wy);
                        else ctx.lineTo(wx, wy);
                    }
                    ctx.strokeStyle = isHighlighted ? '#FDE047' : 'rgba(234, 179, 8, 0.48)';
                    ctx.lineWidth = isHighlighted ? 1.9 : 1.1;
                    ctx.stroke();
                }

                // Punto dorado de la persona
                const rDot = isHighlighted ? 6.0 : (isIncluded ? 3.8 : 1.8);
                ctx.beginPath();
                ctx.arc(pxNode, pyNode, rDot, 0, Math.PI * 2);
                ctx.fillStyle = isHighlighted ? '#FAF6EE' : (isIncluded ? '#EAB308' : 'rgba(234, 179, 8, 0.18)');
                ctx.fill();
            });

            // 3. Perno metálico central
            drawHexBolt(plate.cx, plate.cy, 10.5);

            ctx.restore();
        }

        function drawHexBolt(cx, cy, hexRadius) {
            ctx.save();
            ctx.translate(cx, cy);

            ctx.beginPath();
            ctx.arc(1.5, 2.5, hexRadius * 1.35, 0, Math.PI * 2);
            ctx.fillStyle = 'rgba(0, 0, 0, 0.82)';
            ctx.fill();

            ctx.beginPath();
            ctx.arc(0, 0, hexRadius * 1.18, 0, Math.PI * 2);
            ctx.fillStyle = '#383532';
            ctx.fill();
            ctx.lineWidth = 1;
            ctx.strokeStyle = '#57534E';
            ctx.stroke();

            ctx.beginPath();
            for (let s = 0; s < 6; s++) {
                const ang = (s * Math.PI) / 3 - Math.PI / 6;
                const hx = Math.cos(ang) * hexRadius;
                const hy = Math.sin(ang) * hexRadius;
                if (s === 0) ctx.moveTo(hx, hy);
                else ctx.lineTo(hx, hy);
            }
            ctx.closePath();

            const grad = ctx.createLinearGradient(-hexRadius, -hexRadius, hexRadius, hexRadius);
            grad.addColorStop(0, '#E7E5E4');
            grad.addColorStop(0.5, '#A8A29E');
            grad.addColorStop(1, '#57534E');
            ctx.fillStyle = grad;
            ctx.fill();
            ctx.lineWidth = 0.9;
            ctx.strokeStyle = '#F5F5F4';
            ctx.stroke();

            ctx.beginPath();
            ctx.arc(0, 0, hexRadius * 0.46, 0, Math.PI * 2);
            ctx.fillStyle = '#D6D3D1';
            ctx.fill();
            ctx.lineWidth = 1;
            ctx.strokeStyle = '#44403C';
            ctx.stroke();

            ctx.restore();
        }

        /**
         * ============================================================================
         * 5. CONTROL DE ETAPAS Y DIAGRAMACIÓN EDITORIAL EN LAS ESQUINAS
         * ============================================================================
         */
        function handlePrimaryAction() {
            if (currentStage === 'intro') {
                goToStage('overview');
            } else if (currentStage === 'overview') {
                enterPlaceDetail('sotomayor');
            } else {
                goToStage('overview');
            }
        }

        function handleTopEmblemClick() {
            if (currentStage === 'intro') {
                goToStage('overview');
            } else if (currentStage === 'detail') {
                goToStage('overview');
            } else {
                goToStage('intro');
            }
        }

        function stepBack() {
            if (currentStage === 'detail') {
                goToStage('overview');
            } else if (currentStage === 'overview') {
                goToStage('intro');
            }
        }

        function goToStage(stageName) {
            currentStage = stageName;
            isolatedPerson = null;
            hoveredItem = null;

            const topNav = document.getElementById('topNavActions');
            const detailFilters = document.getElementById('detailFiltersCorner');
            const quickNav = document.getElementById('QuickPlaceNav');
            const clearPersonBtn = document.getElementById('clearPersonBtn');

            clearPersonBtn.classList.add('hidden');

            if (stageName === 'intro') {
                topNav.classList.add('hidden');
                topNav.classList.remove('flex');
                detailFilters.classList.add('hidden');
                detailFilters.classList.remove('flex');
                quickNav.classList.add('hidden');
            } else if (stageName === 'overview') {
                topNav.classList.remove('hidden');
                topNav.classList.add('flex');
                detailFilters.classList.add('hidden');
                detailFilters.classList.remove('flex');
                quickNav.classList.remove('hidden');
            } else if (stageName === 'detail') {
                topNav.classList.remove('hidden');
                topNav.classList.add('flex');
                detailFilters.classList.remove('hidden');
                detailFilters.classList.add('flex');
                quickNav.classList.remove('hidden');
            }

            distributeParticlesForCurrentStage();
            triggerGentleReorganization();
            updatePosterTypography();
            updateHarmonicEmblem();
        }

        function enterPlaceDetail(placeKey) {
            activePlaceKey = placeKey;
            activeWaveFilter = 'todas';
            activeRingFilter = 0;
            isolatedPerson = null;
            goToStage('detail');
            updateFilterButtonsState();
        }

        function getFilteredPeopleInActivePlace() {
            const all = PLACES_DATA[activePlaceKey].people;
            return all.filter(p => {
                const matchWave = (activeWaveFilter === 'todas' || p.wave === activeWaveFilter);
                const matchRing = (activeRingFilter === 0 || p.ring === activeRingFilter);
                return matchWave && matchRing;
            });
        }

        function setWaveFilter(waveKey) {
            activeWaveFilter = waveKey;
            isolatedPerson = null;
            document.getElementById('clearPersonBtn').classList.add('hidden');
            updateFilterButtonsState();
            triggerGentleReorganization();
            updatePosterTypography();
            updateHarmonicEmblem();
        }

        function setRingFilter(ringLevel) {
            activeRingFilter = (activeRingFilter === ringLevel && ringLevel !== 0) ? 0 : ringLevel;
            isolatedPerson = null;
            document.getElementById('clearPersonBtn').classList.add('hidden');
            updateFilterButtonsState();
            triggerGentleReorganization();
            updatePosterTypography();
            updateHarmonicEmblem();
        }

        function isolateSinglePerson(personObj) {
            isolatedPerson = personObj;
            document.getElementById('clearPersonBtn').classList.remove('hidden');
            triggerGentleReorganization();
            updatePosterTypography();
            updateHarmonicEmblem();
        }

        function clearIsolatedPerson() {
            isolatedPerson = null;
            document.getElementById('clearPersonBtn').classList.add('hidden');
            triggerGentleReorganization();
            updatePosterTypography();
            updateHarmonicEmblem();
        }

        function updateFilterButtonsState() {
            const place = PLACES_DATA[activePlaceKey];
            const summary = placeHarmonicSummary[activePlaceKey];

            document.getElementById('wfCount-todas').textContent = summary.total;
            ['envolvente', 'intensa', 'abierta', 'fugaz'].forEach(wKey => {
                const count = place.people.filter(p =>
                    p.wave === wKey && (activeRingFilter === 0 || p.ring === activeRingFilter)
                ).length;
                document.getElementById('wfCount-' + wKey).textContent = count;
            });

            for (let r = 1; r <= 5; r++) {
                const count = place.people.filter(p =>
                    p.ring === r && (activeWaveFilter === 'todas' || p.wave === activeWaveFilter)
                ).length;
                document.getElementById('rfCount-' + r).textContent = count;
            }

            ['todas', 'envolvente', 'intensa', 'abierta', 'fugaz'].forEach(wKey => {
                const btn = document.getElementById('wf-' + wKey);
                if (btn) btn.classList.toggle('active', activeWaveFilter === wKey);
            });

            for (let r = 0; r <= 5; r++) {
                const btn = document.getElementById('rf-' + r);
                if (btn) btn.classList.toggle('active', activeRingFilter === r);
            }
        }

        /**
         * ============================================================================
         * 6. ACTUALIZACIÓN DEL TEXTO DE LAS ESQUINAS (ESTILO SOUND IMAGE HANDEL)
         * ============================================================================
         */
        function updatePosterTypography() {
            const l1 = document.getElementById('posterLine1');
            const l2 = document.getElementById('posterLine2');
            const l3 = document.getElementById('posterLine3');
            const l4 = document.getElementById('posterLine4');
            const l5 = document.getElementById('posterLine5');
            const c1 = document.getElementById('smallCaption1');
            const c2 = document.getElementById('smallCaption2');

            // Si el usuario está pasando el cursor sobre un elemento, mostrar su síntesis sin abrir cajas invasivas
            if (hoveredItem) {
                if (hoveredItem.type === 'zone') {
                    const p = PLACES_DATA[hoveredItem.key];
                    const s = placeHarmonicSummary[hoveredItem.key];
                    l1.textContent = p.name;
                    l2.textContent = `${s.total} personas registradas`;
                    l3.textContent = `Predomina: ${WAVE_TYPES[s.dominantWave].pictogramName}`;
                    l4.textContent = `Naturaleza ${s.waveCounts.envolvente} · Tráfico ${s.waveCounts.intensa}`;
                    l5.textContent = `Voces ${s.waveCounts.abierta} · Puerto ${s.waveCounts.fugaz}`;
                    c1.textContent = 'Click en este círculo para desglosar →';
                    c2.textContent = 'Se abrirán sus 5 anillos y 4 pictogramas';
                    return;
                }
                if (hoveredItem.type === 'person') {
                    const per = hoveredItem.person;
                    const w = WAVE_TYPES[per.wave];
                    l1.textContent = `Registro ${per.id}`;
                    l2.textContent = `Pictograma: ${w.pictogramName}`;
                    l3.textContent = `${w.waveQuality} (n=${w.lobes})`;
                    l4.textContent = `Círculo ${per.ring} de 5`;
                    l5.textContent = per.note;
                    c1.textContent = 'Click para aislar esta onda individual →';
                    c2.textContent = PLACES_DATA[activePlaceKey].name;
                    return;
                }
            }

            if (currentStage === 'intro') {
                l1.textContent = 'Cartografía Cimática';
                l2.textContent = 'Percepción en ondas de arena';
                l3.textContent = '62 registros en tres territorios';
                l4.textContent = 'Sotomayor, Muelle Prat,';
                l5.textContent = 'Buenos Aires';
                c1.textContent = 'Click en la placa para ingresar al total →';
                c2.textContent = '4 pictogramas de onda · 5 círculos de intensidad';
                return;
            }

            if (currentStage === 'overview') {
                l1.textContent = 'Resonancia Total';
                l2.textContent = '62 personas en 3 territorios';
                l3.textContent = 'Plaza Sotomayor (24)';
                l4.textContent = 'Muelle Prat (20),';
                l5.textContent = 'Buenos Aires (18)';
                c1.textContent = 'Selecciona uno de los 3 lugares en la placa →';
                c2.textContent = 'Tamaños proporcionales al total de personas';
                return;
            }

            // Etapa 2: Lugar en detalle
            const place = PLACES_DATA[activePlaceKey];
            const summary = placeHarmonicSummary[activePlaceKey];
            const filtered = getFilteredPeopleInActivePlace();

            if (isolatedPerson) {
                const w = WAVE_TYPES[isolatedPerson.wave];
                l1.textContent = `${place.name} · ${isolatedPerson.id}`;
                l2.textContent = `Pictograma: ${w.pictogramName}`;
                l3.textContent = `${w.waveQuality} · Círculo ${isolatedPerson.ring}/5`;
                l4.textContent = isolatedPerson.note;
                l5.textContent = 'Onda individual aislada';
                c1.textContent = 'Click para volver al total del lugar →';
                c2.textContent = `${summary.total} registros en ${place.name}`;
                return;
            }

            l1.textContent = place.name;
            l2.textContent = `${filtered.length} de ${summary.total} personas activas`;
            l3.textContent = activeWaveFilter === 'todas'
                ? `Predomina: ${WAVE_TYPES[summary.dominantWave].pictogramName}`
                : `Pictograma: ${WAVE_TYPES[activeWaveFilter].pictogramName}`;
            l4.textContent = activeRingFilter === 0
                ? '5 círculos de intensidad (C1–C5)'
                : `${INTENSITY_RINGS[activeRingFilter - 1].label}`;
            l5.textContent = place.subtitle;
            c1.textContent = 'Filtra arriba por pictograma o toca un nodo →';
            c2.textContent = 'Click aquí para volver a los 3 territorios';
        }

        function updateHarmonicEmblem() {
            const svg = document.getElementById('harmonicEmblem');
            const waveKeys = ['envolvente', 'intensa', 'abierta', 'fugaz'];
            let weights = { envolvente: 0.36, intensa: 0.28, abierta: 0.22, fugaz: 0.14 };

            if (currentStage === 'detail') {
                const filtered = getFilteredPeopleInActivePlace();
                const total = Math.max(1, filtered.length);
                weights = { envolvente: 0, intensa: 0, abierta: 0, fugaz: 0 };
                filtered.forEach(p => weights[p.wave] += 1 / total);
            }

            let html = '';
            waveKeys.forEach((k, idx) => {
                const wInfo = WAVE_TYPES[k];
                const ratio = weights[k];
                const radius = 20 + ratio * 26;
                const sides = Math.max(4, wInfo.emblemSides);
                const rot = (idx * 19 * Math.PI) / 180;

                let pts = [];
                for (let s = 0; s < sides; s++) {
                    const a = (s * 2 * Math.PI) / sides + rot - Math.PI / 2;
                    pts.push(`${(Math.cos(a) * radius).toFixed(1)},${(Math.sin(a) * radius).toFixed(1)}`);
                }

                const isHighlighted = (activeWaveFilter === 'todas' || activeWaveFilter === k);
                const opacity = isHighlighted ? 0.92 : 0.22;
                html += `<polygon points="${pts.join(' ')}" fill="none" stroke="#EAB308" stroke-width="1.5" opacity="${opacity}" />`;
            });

            svg.innerHTML = html;
        }

        /**
         * ============================================================================
         * 7. INTERACCIÓN CON EL LIENZO
         * ============================================================================
         */
        function setupCanvasInteractions() {
            canvas.addEventListener('mousemove', (e) => {
                const mx = e.clientX;
                const my = e.clientY;

                if (currentStage === 'intro') {
                    canvas.style.cursor = 'pointer';
                    return;
                }

                if (currentStage === 'overview') {
                    const { zones } = getOverviewConstellationGeometry();
                    let found = null;
                    for (let z of zones) {
                        if (Math.hypot(mx - z.cx, my - z.cy) <= z.radius * 1.08) {
                            found = z;
                            break;
                        }
                    }
                    const prevKey = hoveredItem ? hoveredItem.key : null;
                    hoveredItem = found ? { type: 'zone', key: found.key } : null;
                    canvas.style.cursor = found ? 'pointer' : 'default';
                    if ((hoveredItem ? hoveredItem.key : null) !== prevKey) {
                        updatePosterTypography();
                    }
                    return;
                }

                // Etapa 2: Detalle del lugar
                const plate = getSinglePlateGeometry(false);
                const place = PLACES_DATA[activePlaceKey];
                let foundPerson = null;
                let minDist = 14;

                for (let p of place.people) {
                    const rPx = plate.radius * INTENSITY_RINGS[p.ring - 1].radiusNorm;
                    const pxNode = plate.cx + Math.cos(p.angle) * rPx;
                    const pyNode = plate.cy + Math.sin(p.angle) * rPx;
                    const d = Math.hypot(mx - pxNode, my - pyNode);
                    if (d < minDist) {
                        minDist = d;
                        foundPerson = p;
                    }
                }

                if (foundPerson) {
                    canvas.style.cursor = 'pointer';
                    hoveredItem = { type: 'person', person: foundPerson };
                    updatePosterTypography();
                    return;
                }

                const distCenter = Math.hypot(mx - plate.cx, my - plate.cy);
                let foundRing = null;
                for (let ring of INTENSITY_RINGS) {
                    if (Math.abs(distCenter - plate.radius * ring.radiusNorm) < 9) {
                        foundRing = ring;
                        break;
                    }
                }

                if (foundRing) {
                    canvas.style.cursor = 'pointer';
                    hoveredItem = { type: 'ring', level: foundRing.level };
                } else {
                    canvas.style.cursor = 'default';
                    if (hoveredItem) {
                        hoveredItem = null;
                        updatePosterTypography();
                    }
                }
            });

            canvas.addEventListener('click', () => {
                if (currentStage === 'intro') {
                    goToStage('overview');
                    return;
                }

                if (currentStage === 'overview') {
                    if (hoveredItem && hoveredItem.type === 'zone') {
                        enterPlaceDetail(hoveredItem.key);
                    }
                    return;
                }

                if (currentStage === 'detail' && hoveredItem) {
                    if (hoveredItem.type === 'person') {
                        if (isolatedPerson && isolatedPerson.id === hoveredItem.person.id) {
                            clearIsolatedPerson();
                        } else {
                            isolateSinglePerson(hoveredItem.person);
                        }
                    } else if (hoveredItem.type === 'ring') {
                        setRingFilter(hoveredItem.level);
                    }
                }
            });
        }
    </script>
</body>
</html>
