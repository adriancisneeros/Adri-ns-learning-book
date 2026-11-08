# CAWI Prompt Studio — Estudio de Prompts Intencionales para Imagen y Video

Estudio de ingeniería de prompts guiado por la filosofía "Creating All With Intention" (CAWI), diseñado para transformar ideas casuales en prompts de IA cinematográficos, precisos y de alto impacto para imagen y video, con sistema de afinación dinámica, preservación facial estricta (*Identity Lock*) y soporte bilingüe (Español / Inglés).

## Decisiones Críticas y Confirmaciones del Usuario

> [!IMPORTANT]
> A continuación se resumen las elecciones clave confirmadas en la Fase 1 para la arquitectura y experiencia de la aplicación:

- **Enfoque de Herramientas**: Enfoque universal independiente de la herramienta con formulación basada en intenciones puras (iluminación, composición, óptica de cámara, textura y narrativa), compatible con los principales motores (Midjourney, Flux, Imagen, Kling, Runway Gen-3, Luma Dream Machine, Sora) y etiquetas opcionales por plataforma.
- **Formulación de Preguntas de Afinación**: Motor dinámico con IA (Gemini 3.8 Flash) que analiza la idea inicial casual y formula 2 o 3 preguntas específicas y contextuales sobre ambiente/iluminación, estilo visual/lente y elementos inmutables, con opciones rápidas seleccionables y campo libre.
- **Soporte de Foto de Referencia e Identity Lock**: Módulo de carga de foto con preview y detector automático de retratos/personas. Aplica un bloque estricto de directivas de *Identity Lock* para salvaguardar facciones, estructura ósea, textura cutánea y proporciones sin filtros embellecedores ni distorsiones.

---

## 1. Visión General y Concepto Central

- **Propósito**: Eliminar la sobrecarga de adjetivos huecos ("hyperrealistic", "8k", "trending on artstation") reemplazándolos con prompts cortos, cinematográficos y cargados de propósito.
- **Audiencia Objetivo**: Creadores audiovisuales, diseñadores, directores de arte, fotógrafos y narradores que buscan resultados profesionales en generación de imagen y video con IA.
- **Valor Diferencial CAWI**:
  1. *Prompt Principal Intencional*: Conciso, cinematográfico y listo para copiar en 1 clic.
  2. *Variante Creativa Alternativa*: Otra perspectiva visual o ángulo cinematográfico complementario.
  3. *Nota de Intención*: Desglose pedagógico de por qué se eligió cada término clave y cómo influye en el modelo.
  4. *Identity Lock*: Protocolo de consistencia para retratos y modelos reales.
  5. *Modo Dual Español/Inglés*: Generación directa en español con traducción y optimización inmediata a inglés con 1 clic.

---

## 2. Experiencia de Usuario y Diseño Visual

### Identidad Visual y Paleta
- **Atmósfera**: Oscura, minimalista, cinematográfica y solemne (fondo obsidiana profundo `#090A0F`, superficies `#11131B` con bordes ultrafinos dorados sutiles).
- **Acentos**:
  - Oro refinado (`#D4AF37`, `#F2D06B`) para acciones principales, foco y llamados a la acción de alto valor.
  - Verde Esmeralda joya (`#10B981`, `#059669`, `#064E3B`) para estados activos, candado de identidad (*Identity Lock*) y confirmación de copiado.
  - Blanco puro y marfil (`#F8FAFC`, `#E2E8F0`) con tipografía nítida para máxima legibilidad.
- **Tipografía**:
  - Títulos y Wordmark: `Plus Jakarta Sans` / `Cinzel` con tracking amplio para un carácter editorial refinado.
  - Cuerpo e interfaz: `Plus Jakarta Sans` y `DM Sans` con balance visual anti-huérfanos.
  - Prompts y parámetros: `JetBrains Mono` con números tabulares para inspección de texto y copiado preciso.

### Flujo de Interacción
```
┌────────────────────────────────────────────────────────────────────────┐
│ 1. ENTRADA CASUAL + REFERENCIA                                         │
│ Ingrese idea (ej. "video de mi retrato en una ciudad cyberpunk")       │
│ + Carga opcional de foto de referencia (dispara Identity Lock)        │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 2. AFINACIÓN DINÁMICA DE INTENCIÓN (2-3 Preguntas IA)                  │
│ • Pregunta 1: Atmósfera y Luz (ej. Neón crepuscular vs. Lluvia fría)  │
│ • Pregunta 2: Estilo Óptico / Movimiento (ej. Anamórfico 35mm vs...)  │
│ • Pregunta 3: Elementos inmutables (ej. Facciones, ropa, paleta)       │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 3. RESULTADOS CAWI (1-Click Copiar & Alternar Idioma ES/EN)            │
│ ┌───────────────────────────┐ ┌───────────────────────────┐            │
│ │ Prompt Principal          │ │ Variante Alternativa      │            │
│ │ [Intención pura / Copiar] │ │ [Enfoque divergente]      │            │
│ └───────────────────────────┘ └───────────────────────────┘            │
│ ┌─────────────────────────────────────────────────────────┐            │
│ │ Por qué funciona: Explicación de cada término elegido   │            │
│ └─────────────────────────────────────────────────────────┘            │
│ ┌─────────────────────────────────────────────────────────┐            │
│ │ Bloque Identity Lock: Directivas para salvaguardar rostro│            │
│ └─────────────────────────────────────────────────────────┘            │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│ 4. HISTORIAL Y BIBLIOTECA LOCAL                                        │
│ Guardado automático en localStorage con filtrado, favoritos y descarga │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 3. Decisiones Clave de Producto y Reglas del Generador

### Regla 1: Intención Primero, Herramientas Después
- Se descartan adjetivos vacíos ("ultra detailed", "photorealistic", "masterpiece").
- Se priorizan descriptores funcionales: iluminación (fuente, dirección, temperatura de color), lente y distancia focal (e.g. 50mm f/1.4, 35mm anamórfico), dinámica de movimiento (en video: dolly in sutil, cámara en mano con paneo lento), textura de piel y grano analógico cinematográfico.

### Regla 2: Identity Lock Riguroso
- Si el usuario sube una foto o describe un sujeto específico ("mi retrato", "una persona específica"):
  - Activa la etiqueta y cláusula de seguridad: `[IDENTITY LOCK: Maintain exact facial proportions, authentic skin texture, unaltered eye shape and nose contours without digital beautification, artificial slimming, or smoothing]`.
  - Proporciona las directivas adaptadas tanto para generadores con soporte `--cref / --cw` (Midjourney), control de imagen en Flux/ComfyUI, como para generadores de video con image-to-video (Runway, Kling).

### Regla 3: Versión Bilingüe Inteligente
- Generación nativa en Español y traducción técnica cinematográfica al Inglés (ya que muchos modelos responden mejor en inglés británico/americano con términos de cinematografía internacional como *chiaroscuro, rim light, shallow depth of field*).
- Selector instantáneo de visualización y botón de copiado directo para cada idioma.

### Regla 4: Resiliencia y Modo Sin Conexión
- Servicio backend con Gemini 3.8 Flash (`@google/genai`) para síntesis semántica profunda.
- Motor de reglas sintácticas CAWI en frontend como salvaguarda inmediata si no hay conexión o si la API no está disponible en un momento dado, garantizando que el usuario jamás quede bloqueado.

---

## 4. Arquitectura Técnica y Estrategia de Datos

```
┌─────────────────────────────────────────────────────────────────────────┐
│ NAVEGADOR / CLIENTE REACT (Port 3000)                                   │
│                                                                         │
│ ┌─────────────────────────────────────────────────────────────────────┐ │
│ │ Componentes:                                                        │ │
│ │ • Header (Brand CAWI Prompt Studio + Stats de prompts + Ayuda)      │ │
│ │ • PromptInputArea (Texto casual + Drag&drop de foto + Modo Imagen/V)│ │
│ │ • ClarificationModal/Wizard (Preguntas dinámicas con opciones)       │ │
│ │ • ResultsViewer (Prompt Principal, Variante, Razón, Identity Lock)   │ │
│ │ • PromptHistoryDrawer (Historial con búsqueda, pines y exportación)  │ │
│ └──────────────────────────────────┬──────────────────────────────────┘ │
│                                    │                                    │
│                         Fetch /api │ LocalStorage (Cache + Historial)   │
└────────────────────────────────────┼────────────────────────────────────┘
                                     ▼
┌─────────────────────────────────────────────────────────────────────────┐
│ SERVIDOR FULL-STACK (Vite Dev Plugin / Express en server.ts)           │
│                                                                         │
│ • POST /api/generate-questions -> Analiza idea inicial con Gemini 3.8  │
│ • POST /api/generate-prompts   -> Genera prompt, variante y notas      │
│ • POST /api/translate-prompt   -> Optimiza traducción a inglés técnico │
│                                                                         │
│ Llamadas seguras a @google/genai con GEMINI_API_KEY                     │
└─────────────────────────────────────────────────────────────────────────┘
```

### Modelo de Datos
- `PromptSession`:
  - `id`: string (UUID)
  - `timestamp`: number
  - `casualInput`: string
  - `mediaType`: `'image' | 'video'`
  - `referenceImage`: string | null (dataUrl)
  - `hasIdentityLock`: boolean
  - `questionsAndAnswers`: Array<{ question: string, answer: string }>
  - `mainPrompt`: { es: string, en: string }
  - `variantPrompt`: { es: string, en: string }
  - `identityLockDirectives`: { es: string, en: string } | null
  - `explanation`: { es: string, en: string }
  - `isPinned`: boolean
  - `tags`: string[]

---

## 5. Fases de Implementación tras Aprobación

1. **Configuración de Servidor y Rutas de API**: Integrar soporte de API proxy en Vite y Express `server.ts` con `@google/genai` (modelo `gemini-3.8-flash`).
2. **Sistema de Diseño CAWI**: Definir tokens Tailwind para obsidian, oro pulido y verde esmeralda, tipografía y contenedor centrado sin elementos tipo pill decorativos.
3. **Flujo de Entrada y Afinación**:
   - Área de descripción casual con reconocimiento de intención.
   - Componente de subida de foto de referencia con toggle de *Identity Lock*.
   - Modal/Panel interactivo de 2-3 preguntas dinámicas generadas contextualmente.
4. **Visor de Prompts y Resultados**:
   - Tarjeta de Prompt Principal con copiado en 1 clic.
   - Tarjeta de Variante Alternativa con enfoque divergente.
   - Panel de "Por qué funciona" (justificación y descomposición intencional).
   - Bloque de Identity Lock con directivas específicas para herramientas.
   - Selector de idioma Español / Inglés.
5. **Historial y Biblioteca Persistente**: Guardado local, filtrado por tipo (imagen/video), marcado de favoritos y exportación en formato Markdown/JSON.
6. **Verificación y Compilación**: Pruebas de compilación TypeScript (`compile_applet` y `lint_applet`) y reinicio de servidor de desarrollo.
