# Semana 01 — Responses API, OpenAI/Bedrock y Prompt & Context Engineering para Fintech

Perfecto. Tomo como base tu **Semana 1** del plan: **Responses API / OpenAI-Bedrock / prompt & context engineering**, cuyo objetivo es entender el runtime moderno de apps LLM y cerrar con un **LLM Runtime v1** con wrapper multi-proveedor, script o endpoint de chat, 3 prompts bien estructurados y README corto. Lo voy a bajar a un enfoque **fintech real**, alineado con tu perfil de AI/LLM en entorno regulado, soporte/ops/risk, guardrails, observabilidad y control de costo.

# Semana 1 — Formación completa

## Responses API + OpenAI/Bedrock + Prompt & Context Engineering aplicado a Fintech

## 1) Objetivo real de la semana

La meta no es “hacer un chatbot”.
La meta es entender cómo construir un **runtime LLM serio**, es decir, una capa de aplicación que:

- recibe una consulta,
- arma contexto útil,
- manda una instrucción sólida al modelo,
- obtiene una respuesta consistente,
- deja trazabilidad,
- y puede cambiar de proveedor sin romper la app.

En tu plan, esta semana apunta exactamente a eso: aprender el runtime moderno, separar instrucciones/contexto/input y dejar un **wrapper multi-proveedor** como primer entregable.

En fintech, eso importa porque el problema no es solo “responder lindo”, sino responder con:

- **consistencia**
- **bajo riesgo**
- **buen costo**
- **tiempo de respuesta aceptable**
- **controles de contexto**
- **capacidad de auditoría**

---

# 2) Qué es un “runtime moderno” de LLM

Antes, mucha gente integraba modelos así:

1. armaba un string grande,
2. se lo mandaba al modelo,
3. recibía texto,
4. lo pegaba en pantalla.

Eso sirve para demos.
No sirve para producción.

Un **runtime moderno** de LLM es una capa intermedia entre tu app y el modelo que resuelve al menos estas responsabilidades:

### a) Construcción del prompt

No mandar cualquier cosa.
Separar:

- instrucciones del sistema,
- contexto de negocio,
- input puntual del usuario,
- reglas,
- formato esperado.

### b) Selección de proveedor/modelo

Poder usar OpenAI o Bedrock sin rehacer toda la app.

### c) Normalización

Cada proveedor devuelve cosas distintas. El runtime las transforma a una forma común.

### d) Controles

Timeout, retry, logging, redacción de PII, límites de tamaño, fallback.

### e) Observabilidad mínima

Guardar qué prompt salió, con qué contexto, con qué modelo y qué devolvió.

### f) Gobernanza

Evitar que el modelo improvise fuera del scope.

---

# 3) Qué rol cumple la Responses API

La idea central de la Responses API es tratar la generación como una **respuesta estructurada de runtime**, en vez de pensar solo en “chat messages”.
Conceptualmente, te conviene verla como una interfaz moderna para:

- enviar input,
- configurar instrucciones,
- manejar salidas,
- soportar streaming,
- y luego evolucionar a tools/structured outputs en semanas siguientes.

En tu plan, Semana 1 arranca justamente por ahí: “primera llamada a modelo, inputs, outputs, streaming básico”, y recién después en Semana 2 pasás a structured outputs y tool calling.

## Idea importante

En Semana 1 todavía no estás optimizando JSON Schema ni tool execution.
Estás construyendo el músculo base:

- cómo instruís,
- cómo das contexto,
- cómo delimitás,
- cómo comparás prompts,
- cómo cambiás de proveedor.

---

# 4) OpenAI vs Bedrock en esta semana

Acá no te interesa todavía hacer una comparación académica.
Te interesa entender **qué cambia arquitectónicamente**.

## OpenAI

Pensalo como proveedor directo de modelos y runtime.

Ventajas típicas para aprender rápido:

- integración simple,
- DX muy buena,
- iteración rápida,
- ideal para probar prompts y comportamiento.

## Bedrock

Pensalo como la capa AWS para consumir modelos dentro de un entorno cloud más empresarial.

Ventajas típicas:

- encaje organizacional,
- alineación con seguridad/cloud enterprise,
- modelos de distintos vendors bajo una misma plataforma,
- mejor story de integración en algunas organizaciones AWS-first.

## Qué no cambia entre ambos

Si diseñaste bien tu runtime, no debería cambiar:

- la interfaz interna,
- la lógica de armado de contexto,
- la política de prompts,
- la trazabilidad básica.

## Qué sí cambia

- autenticación,
- request format,
- respuesta nativa,
- nombres de modelos,
- streaming específico,
- detalles de costos/latencias.

Por eso el primer activo serio que construís es el **wrapper multi-proveedor**.

---

# 5) Prompt engineering bien entendido

Prompt engineering no es “escribir más lindo”.
Es diseñar instrucciones para que el modelo se comporte de forma:

- más predecible,
- más consistente,
- más útil,
- menos riesgosa.

## Componentes de un buen prompt

### a) Rol

Quién es el asistente.

Ejemplo:
“Actuás como analista de soporte fintech especializado en tarjetas y cuentas.”

### b) Tarea

Qué tiene que hacer exactamente.

Ejemplo:
“Debés resumir el caso, detectar la intención principal y proponer próximo paso.”

### c) Restricciones

Qué no puede hacer.

Ejemplo:
“No inventes políticas, no prometas reversos, no des consejo legal.”

### d) Contexto

Información relevante para resolver.

Ejemplo:

- canal de entrada,
- país,
- producto,
- tipo de cliente,
- políticas internas,
- historial del caso.

### e) Formato

Cómo debe responder.

Ejemplo:

- resumen,
- riesgo,
- próximos pasos,
- aclaraciones.

### f) Criterio de incertidumbre

Qué hacer si no sabe.

Ejemplo:
“Si falta información crítica, decilo explícitamente.”

---

# 6) Context engineering

Este punto es todavía más importante que el prompt.

La mayoría de los problemas en apps LLM no vienen porque “el modelo es malo”, sino porque el **contexto es pobre, ambiguo o mal armado**.

## Qué es context engineering

Es el diseño de:

- qué contexto entra,
- en qué orden entra,
- cómo se recorta,
- cómo se etiqueta,
- cómo se delimita,
- y qué se deja afuera.

## Regla central

**No todo contexto útil es todo el contexto disponible.**

En fintech, meter demasiado contexto crudo puede empeorar:

- costo,
- latencia,
- foco,
- riesgo de mezclar casos,
- riesgo de exponer datos innecesarios.

## Contexto bueno vs contexto malo

### Contexto malo

- logs completos irrelevantes,
- conversación entera sin resumir,
- manuales mezclados,
- políticas viejas y nuevas juntas,
- JSON gigante sin explicación.

### Contexto bueno

- información seleccionada,
- etiquetada,
- actual,
- relevante al caso,
- y delimitada claramente.

---

# 7) Delimitación: por qué importa tanto

Delimitar significa decirle al modelo:

- esto es instrucción,
- esto es contexto,
- esto es input del usuario,
- esto es política,
- esto es ejemplo.

Si no delimitás, el modelo mezcla todo.

## Ejemplo malo

```txt
Sos analista fintech. El cliente dijo que le cobraron dos veces y acá hay una política y además respondé amable y no inventes. Caso: ...
```

Todo viene pegado. Hay menos control.

## Ejemplo mejor

```txt
[ROL]
Sos analista de soporte fintech especializado en pagos.

[OBJETIVO]
Debés resumir el caso y proponer próximo paso.

[RESTRICCIONES]
- No inventes políticas.
- No confirmes devoluciones no validadas.

[CONTEXTO]
- Producto: tarjeta prepaga
- País: Argentina
- Política vigente: ...
- Canal: chat app

[INPUT_USUARIO]
"Me cobraron dos veces una compra en un comercio"
```

Eso baja ambigüedad.

---

# 8) Ingeniería de prompts en fintech: qué cambia respecto a otros dominios

En fintech no alcanza con “ser útil”.

Tenés que considerar:

## a) Riesgo operativo

No inventar pasos que generen reclamos o incumplimientos.

## b) Riesgo regulatorio

No afirmar políticas inexistentes.

## c) Riesgo reputacional

No responder con tono incorrecto ante fraude, contracargos o bloqueos.

## d) Riesgo de privacidad

No exponer PII de más.

## e) Riesgo de acción incorrecta

No recomendar desbloqueos, devoluciones o aprobaciones fuera del proceso.

## Patrón recomendado

En semana 1, el modelo debería quedar en tareas como:

- resumir casos,
- clasificar intención,
- proponer borradores,
- explicar políticas,
- priorizar temas,
- preparar handoff humano.

Todavía no lo usaría para ejecutar acciones.

---

# 9) Casos fintech ideales para practicar en Semana 1

Estos son muy buenos porque tienen ROI y bajo riesgo relativo:

## Caso 1 — Resumen de ticket de soporte

Input: conversación larga.
Output: resumen claro para agente humano.

## Caso 2 — Clasificación de intención

Input: mensaje de cliente.
Output: fraude, disputa, cargo duplicado, límite, KYC, etc.

## Caso 3 — Explicación de política

Input: caso + política vigente.
Output: explicación simple al cliente.

## Caso 4 — Priorización operativa

Input: lote de consultas.
Output: cuál atender primero según severidad.

## Caso 5 — Hand-off a backoffice

Input: caso no resuelto.
Output: resumen + datos faltantes + siguiente equipo.

---

# 10) Arquitectura base del entregable “LLM Runtime v1”

Tu plan define como entregable un **wrapper OpenAI/Bedrock**, endpoint o script, 3 prompts bien estructurados y README.

Te propongo esta arquitectura mínima:

```txt
Cliente / Script / API
        |
        v
   LLM Runtime Service
        |
        +--> Prompt Builder
        |
        +--> Context Builder
        |
        +--> Provider Router
               |              \
               |               \
               v                v
        OpenAI Adapter     Bedrock Adapter
               \                /
                \              /
                 v            v
              Normalizer de respuesta
                      |
                      v
               Output + Logs básicos
```

## Responsabilidades

### Prompt Builder

Arma el bloque final con:

- rol,
- objetivo,
- restricciones,
- contexto,
- input usuario.

### Context Builder

Selecciona y ordena contexto.

### Provider Router

Decide si va a OpenAI o Bedrock.

### Adapter

Traduce la interfaz común a cada proveedor.

### Normalizer

Devuelve una forma uniforme de respuesta.

---

# 11) Estructura de proyecto recomendada

```txt
week1-llm-runtime/
  src/
    config.ts
    types.ts
    main.ts
    prompts/
      supportSummary.ts
      fraudTriage.ts
      collectionsAssistant.ts
    runtime/
      promptBuilder.ts
      contextBuilder.ts
      providerRouter.ts
    providers/
      llmProvider.ts
      openaiProvider.ts
      bedrockProvider.ts
    utils/
      logger.ts
      maskPII.ts
  .env
  package.json
  README.md
```

---

# 12) Código base completo — Node.js + TypeScript

## 12.1 types.ts

```ts
export type ProviderName = "openai" | "bedrock";

export interface ContextBlock {
  name: string;
  content: string;
}

export interface LLMRequest {
  provider: ProviderName;
  model: string;
  systemPrompt: string;
  userInput: string;
  contextBlocks?: ContextBlock[];
  temperature?: number;
  maxOutputTokens?: number;
}

export interface LLMResponse {
  provider: ProviderName;
  model: string;
  text: string;
  raw?: unknown;
  usage?: {
    inputTokens?: number;
    outputTokens?: number;
    totalTokens?: number;
  };
}
```

## 12.2 promptBuilder.ts

```ts
import { ContextBlock } from "../types";

export function buildPrompt(userInput: string, contextBlocks: ContextBlock[] = []) {
  const contextText = contextBlocks
    .map(
      (b) => `[CONTEXTO: ${b.name}]
${b.content}`
    )
    .join("\n\n");

  return `
[INSTRUCCIÓN]
Respondé usando únicamente la información relevante provista.
Si falta información crítica, indicarlo explícitamente.
No inventes políticas, montos, aprobaciones ni estados operativos.

${contextText ? `${contextText}\n` : ""}

[INPUT_USUARIO]
${userInput}
`.trim();
}
```

## 12.3 llmProvider.ts

```ts
import { LLMRequest, LLMResponse } from "../types";

export interface LLMProvider {
  generate(request: LLMRequest): Promise<LLMResponse>;
}
```

## 12.4 openaiProvider.ts

```ts
import OpenAI from "openai";
import { LLMProvider } from "./llmProvider";
import { LLMRequest, LLMResponse } from "../types";
import { buildPrompt } from "../runtime/promptBuilder";

export class OpenAIProvider implements LLMProvider {
  private client: OpenAI;

  constructor(apiKey: string) {
    this.client = new OpenAI({ apiKey });
  }

  async generate(request: LLMRequest): Promise<LLMResponse> {
    const prompt = buildPrompt(request.userInput, request.contextBlocks);

    const response = await this.client.responses.create({
      model: request.model,
      temperature: request.temperature ?? 0.2,
      max_output_tokens: request.maxOutputTokens ?? 500,
      input: [
        {
          role: "system",
          content: [{ type: "input_text", text: request.systemPrompt }],
        },
        {
          role: "user",
          content: [{ type: "input_text", text: prompt }],
        },
      ],
    });

    const text =
      response.output_text ??
      "";

    return {
      provider: "openai",
      model: request.model,
      text,
      raw: response,
      usage: {
        inputTokens: response.usage?.input_tokens,
        outputTokens: response.usage?.output_tokens,
        totalTokens: response.usage?.total_tokens,
      },
    };
  }
}
```

## 12.5 bedrockProvider.ts

```ts
import { BedrockRuntimeClient, InvokeModelCommand } from "@aws-sdk/client-bedrock-runtime";
import { LLMProvider } from "./llmProvider";
import { LLMRequest, LLMResponse } from "../types";
import { buildPrompt } from "../runtime/promptBuilder";

export class BedrockProvider implements LLMProvider {
  private client: BedrockRuntimeClient;

  constructor(region: string) {
    this.client = new BedrockRuntimeClient({ region });
  }

  async generate(request: LLMRequest): Promise<LLMResponse> {
    const prompt = buildPrompt(request.userInput, request.contextBlocks);

    const body = {
      anthropic_version: "bedrock-2023-05-31",
      max_tokens: request.maxOutputTokens ?? 500,
      temperature: request.temperature ?? 0.2,
      system: request.systemPrompt,
      messages: [
        {
          role: "user",
          content: [{ type: "text", text: prompt }],
        },
      ],
    };

    const command = new InvokeModelCommand({
      modelId: request.model,
      contentType: "application/json",
      accept: "application/json",
      body: JSON.stringify(body),
    });

    const response = await this.client.send(command);
    const rawText = new TextDecoder().decode(response.body);
    const parsed = JSON.parse(rawText);

    const text =
      parsed?.content?.map((c: any) => c.text).join("\n") ??
      "";

    return {
      provider: "bedrock",
      model: request.model,
      text,
      raw: parsed,
    };
  }
}
```

## 12.6 providerRouter.ts

```ts
import { LLMRequest } from "../types";
import { OpenAIProvider } from "../providers/openaiProvider";
import { BedrockProvider } from "../providers/bedrockProvider";

export class ProviderRouter {
  private openai: OpenAIProvider;
  private bedrock: BedrockProvider;

  constructor(openaiApiKey: string, awsRegion: string) {
    this.openai = new OpenAIProvider(openaiApiKey);
    this.bedrock = new BedrockProvider(awsRegion);
  }

  async generate(request: LLMRequest) {
    if (request.provider === "openai") {
      return this.openai.generate(request);
    }
    if (request.provider === "bedrock") {
      return this.bedrock.generate(request);
    }
    throw new Error(`Proveedor no soportado: ${request.provider}`);
  }
}
```

## 12.7 supportSummary.ts

```ts
export const supportSummarySystemPrompt = `
Sos un analista de soporte fintech senior.
Tu tarea es resumir casos de clientes de forma clara, precisa y segura.

Objetivos:
1. Identificar el problema principal.
2. Resumir hechos importantes.
3. Sugerir el siguiente paso operativo.
4. Explicar incertidumbres o datos faltantes.

Restricciones:
- No inventes resoluciones.
- No prometas reintegros.
- No afirmes fraude si no está validado.
- No expongas más datos personales de los necesarios.

Formato de salida:
1. Resumen breve
2. Intención principal
3. Riesgo/criticidad
4. Próximo paso sugerido
5. Datos faltantes
`.trim();
```

## 12.8 fraudTriage.ts

```ts
export const fraudTriageSystemPrompt = `
Sos un analista de pre-triage de fraude en una fintech.

Debés:
- leer el caso,
- identificar señales de urgencia,
- clasificar severidad en BAJA, MEDIA o ALTA,
- proponer derivación operativa.

Restricciones:
- No confirmar fraude.
- No bloquear productos.
- No des instrucciones irreversibles.
- Si la evidencia es insuficiente, marcar "requiere validación".

Formato:
1. Clasificación
2. Señales observadas
3. Severidad
4. Acción sugerida
5. Aclaraciones
`.trim();
```

## 12.9 main.ts

```ts
import "dotenv/config";
import { ProviderRouter } from "./runtime/providerRouter";
import { supportSummarySystemPrompt } from "./prompts/supportSummary";
import { fraudTriageSystemPrompt } from "./prompts/fraudTriage";

async function run() {
  const router = new ProviderRouter(
    process.env.OPENAI_API_KEY || "",
    process.env.AWS_REGION || "us-east-1"
  );

  const userInput = `
Cliente indica:
- "Me cobraron dos veces una compra de supermercado"
- La primera operación figura aprobada
- La segunda también
- Ocurrió hace 20 minutos
- No sabe si es duplicado del comercio o retención temporal
`;

  const contextBlocks = [
    {
      name: "producto",
      content: "Tarjeta prepaga virtual y física",
    },
    {
      name: "pais",
      content: "Argentina",
    },
    {
      name: "politica_operativa",
      content:
        "No confirmar devoluciones automáticas. Sugerir revisión del comercio, estado de la autorización y canal de reclamo si corresponde.",
    },
    {
      name: "tono",
      content: "Claro, profesional, empático y no alarmista",
    },
  ];

  const response = await router.generate({
    provider: "openai",
    model: process.env.OPENAI_MODEL || "gpt-4.1-mini",
    systemPrompt: supportSummarySystemPrompt,
    userInput,
    contextBlocks,
    temperature: 0.2,
    maxOutputTokens: 400,
  });

  console.log("=== RESPUESTA ===");
  console.log(response.text);

  const fraudResponse = await router.generate({
    provider: "openai",
    model: process.env.OPENAI_MODEL || "gpt-4.1-mini",
    systemPrompt: fraudTriageSystemPrompt,
    userInput,
    contextBlocks,
    temperature: 0.1,
    maxOutputTokens: 300,
  });

  console.log("\n=== TRIAGE FRAUDE ===");
  console.log(fraudResponse.text);
}

run().catch(console.error);
```

## 12.10 package.json mínimo

```json
{
  "name": "week1-llm-runtime",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "tsx src/main.ts"
  },
  "dependencies": {
    "@aws-sdk/client-bedrock-runtime": "^3.0.0",
    "dotenv": "^16.0.0",
    "openai": "^4.0.0"
  },
  "devDependencies": {
    "tsx": "^4.0.0",
    "typescript": "^5.0.0"
  }
}
```

---

# 13) Cómo ejecutar el laboratorio

## Paso 1

Crear `.env`

```env
OPENAI_API_KEY=tu_api_key
OPENAI_MODEL=gpt-4.1-mini
AWS_REGION=us-east-1
```

## Paso 2

Instalar dependencias

```bash
npm install
```

## Paso 3

Ejecutar

```bash
npm run dev
```

## Paso 4

Cambiar `provider: "openai"` por `provider: "bedrock"` y ajustar `model`.

---

# 14) Los 3 prompts que deberías dejar listos en Semana 1

Tu plan pide 3 prompts bien estructurados.
Te recomiendo estos:

## Prompt 1 — Support Summary

Para resumir tickets de soporte.

## Prompt 2 — Fraud Triage

Para pre-clasificar casos sospechosos.

## Prompt 3 — Collections/Delinquency Assistant

Para explicar estado de deuda sin prometer acuerdos inexistentes.

Ejemplo del tercero:

```ts
export const collectionsAssistantSystemPrompt = `
Sos un asistente de operaciones de cobranzas fintech.

Debés:
- explicar el caso de deuda en términos simples,
- resumir estado, urgencia y próximo paso,
- mantener tono respetuoso y no amenazante.

Restricciones:
- No ofrecer planes no confirmados.
- No inventar condonaciones.
- No ejercer presión indebida.
- Si falta información contractual, indicarlo.

Formato:
1. Estado del caso
2. Nivel de urgencia
3. Próximo paso sugerido
4. Información faltante
`.trim();
```

---

# 15) Ejercicios prácticos completos

## Ejercicio 1 — Comparar prompt malo vs prompt bueno

### Objetivo

Entender por qué la estructura importa.

### Input

```txt
El cliente dice que le cobraron dos veces y está enojado.
```

### Prompt malo

```txt
Sos de soporte. Respondé este caso.
```

### Prompt bueno

```txt
Sos un analista de soporte fintech especializado en pagos.

Objetivo:
- resumir el caso,
- identificar intención principal,
- sugerir siguiente paso.

Restricciones:
- no inventes devoluciones,
- no confirmes fraude,
- no des pasos irreversibles.

Contexto:
- producto: tarjeta prepaga
- política: validar estado de autorización y reclamo si corresponde
- tono: empático y preciso

Input:
"El cliente dice que le cobraron dos veces y está enojado."
```

### Qué tenés que observar

- el malo suele ser genérico,
- el bueno suele ser más preciso,
- el bueno reduce improvisación.

### Resultado esperado

Que documentes:

- diferencias de foco,
- diferencias de tono,
- diferencias de seguridad,
- diferencias de utilidad.

---

## Ejercicio 2 — Resumen de ticket largo

### Objetivo

Practicar context engineering.

### Caso

```txt
Cliente: "Ayer intenté pagar una compra y me apareció error. Después probé otra vez y ahora veo dos consumos. Necesito saber si me van a devolver uno. Además no puedo hablar con el comercio."
Agente anterior: "Puede ser una retención temporal."
Cliente: "Pero las dos figuran aprobadas."
Canal: app chat
País: Argentina
Producto: tarjeta prepaga
```

### Tarea

Construir contexto en 4 bloques:

- producto
- canal
- política
- tono

### Salida esperada

```txt
Resumen breve:
Cliente reporta dos consumos aprobados por una misma compra tras reintentar un pago fallido.

Intención principal:
Cargo duplicado / posible duplicidad de autorización.

Riesgo/criticidad:
Media. Impacto monetario y ansiedad del cliente, pero sin evidencia suficiente para confirmar fraude.

Próximo paso sugerido:
Validar si se trata de duplicación real o retención temporal y orientar al canal de reclamo correspondiente.

Datos faltantes:
Fecha exacta, monto, comercio y últimos 4 dígitos del instrumento.
```

---

## Ejercicio 3 — Triage de fraude sin sobrerreaccionar

### Objetivo

Aprender a no mezclar “sospecha” con “confirmación”.

### Caso

```txt
Cliente informa una compra internacional no reconocida por USD 420 realizada hace 15 minutos.
Indica que nunca usó la tarjeta fuera del país.
Dice que recibió un SMS de validación que no respondió.
```

### Tarea

Pedir al modelo:

- severidad,
- señales,
- acción sugerida,
- aclaraciones.

### Lo correcto

El modelo debería decir algo como:

- severidad alta,
- señales relevantes,
- requiere validación inmediata,
- no confirmar fraude definitivo.

### Error típico

Que el modelo diga:
“Se trata de fraude confirmado”.

Eso no debería pasar si el prompt está bien diseñado.

---

## Ejercicio 4 — Comparación OpenAI vs Bedrock

### Objetivo

Entender el valor del wrapper.

### Tarea

Ejecutar el mismo caso con ambos proveedores y documentar:

- calidad percibida,
- claridad de respuesta,
- longitud,
- consistencia,
- latencia aproximada,
- facilidad de integración.

### Aprendizaje esperado

Que el valor mayor no está solo en el modelo sino en:

- cómo armás el prompt,
- cómo armás el contexto,
- cómo abstraés el proveedor.

---

## Ejercicio 5 — Diseñar tu primer runtime productizable

### Objetivo

No quedarte en un script.

### Tarea

Agregar:

- `requestId`
- logs mínimos
- tiempo de ejecución
- proveedor usado
- modelo usado

Ejemplo:

```ts
const startedAt = Date.now();
const response = await router.generate(...);
const elapsedMs = Date.now() - startedAt;

console.log({
  requestId: "req-001",
  provider: response.provider,
  model: response.model,
  elapsedMs,
  preview: response.text.slice(0, 200),
});
```

Eso ya te entrena para observabilidad de semanas posteriores, algo muy alineado con tu experiencia objetivo en fintech productivo.

---

# 16) Qué deberías aprender conceptualmente al terminar la semana

## A. Responses API

Entender que la interacción con el modelo no es “mandar texto”, sino operar un runtime de entrada/salida.

## B. Prompt engineering

Entender cómo bajar ambigüedad y guiar el comportamiento.

## C. Context engineering

Entender qué contexto meter, cuál no y cómo ordenarlo.

## D. Delimitación

Entender cómo separar rol, reglas, contexto e input.

## E. Wrapper multi-proveedor

Entender cómo desacoplar negocio de vendor.

## F. Casos fintech seguros

Entender dónde el LLM agrega valor sin tomar acciones de riesgo.

---

# 17) Errores típicos de Semana 1

## Error 1

Meter toda la conversación sin resumir.

## Error 2

No separar instrucciones de contexto.

## Error 3

Pedir “respondé bien” en vez de definir objetivo y restricciones.

## Error 4

No definir qué hacer ante incertidumbre.

## Error 5

Comparar modelos cuando en realidad el problema era el prompt.

## Error 6

Usar casos demasiado amplios.
Semana 1 necesita casos acotados.

---

# 18) Cómo documentar el entregable

## README mínimo recomendado

```md
# LLM Runtime v1

## Objetivo
Runtime básico para comparar OpenAI y Bedrock en casos fintech de soporte y triage.

## Alcance
- Wrapper multi-proveedor
- Prompt builder
- Context builder
- 3 prompts base
- Script de ejecución

## Casos incluidos
1. Support summary
2. Fraud triage
3. Collections assistant

## Arquitectura
Cliente -> Runtime -> Prompt Builder -> Context Builder -> Provider Router -> OpenAI/Bedrock -> Normalizer

## Aprendizajes
- Separación de instrucciones, contexto e input
- Importancia de delimitación
- Comparación de proveedores
- Primeras prácticas de seguridad y trazabilidad

## Próximos pasos
- Structured outputs
- JSON Schema
- Tool calling
```

---

# 19) Checklist de salida de la semana

Esto sale directo de tu plan, pero te lo traduzco a validación práctica.

## Tenés que poder decir:

### 1. “Entiendo cuándo usar Responses API”

Sí, cuando querés construir un runtime serio y no solo un texto improvisado.

### 2. “Sé diseñar un prompt de sistema sólido”

Sí, si incluís rol, tarea, restricciones, contexto y formato.

### 3. “Sé separar instrucciones, contexto y entrada”

Sí, si tu prompt builder ya los delimita.

### 4. “Tengo un wrapper simple multi-proveedor”

Sí, si podés cambiar de OpenAI a Bedrock desde una misma interfaz.

### 5. “Puedo explicar diferencias de costo/calidad a alto nivel”

Sí, aunque sea de forma cualitativa en esta semana.

---

# 20) Resultado final esperado de la Semana 1

Al cerrar la semana deberías tener:

- un proyecto ejecutable,
- un runtime mínimo,
- 3 prompts buenos,
- 2 o 3 casos fintech de prueba,
- comparación básica entre proveedores,
- y una comprensión clara de esta idea:

> el valor real de una app LLM no está solo en el modelo; está en el runtime, el contexto y las restricciones.

Eso encaja perfecto con el objetivo formal de tu Semana 1 y con el tipo de perfil/productización que venís construyendo en fintech.

Si querés, en el próximo mensaje te doy la **versión final en formato README/GitHub lista para copiar y pegar** de toda esta Semana 1.