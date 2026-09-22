<p align="center">
  <img src="https://img.shields.io/badge/status-active-success" alt="status" />
  <img src="https://img.shields.io/badge/stack-Next.js%20%7C%20Node-black" alt="stack" />
  <img src="https://img.shields.io/badge/AI-GPT%2FClaude-blueviolet" alt="ai" />
</p>

<h1 align="center">&#9889; Servicios Automáticos GPT</h1>
<p align="center">
  <strong>Automatizamos lo repetitivo de tu negocio para que tú hagas lo que importa.</strong>
</p>

---

## &#129504; Qué es

**Servicios Automáticos GPT** es una plataforma que construye asistentes y
automatizaciones inteligentes sobre modelos de lenguaje (GPT / Claude) para
pequeñas y medianas empresas:

- &#128196; Generación de documentos, propuestas y presupuestos
- &#128231; Respuesta automática a correos y consultas frecuentes
- &#128197; Gestión de citas, recordatorios y seguimiento de clientes
- &#127760; Webs y landing pages generadas a partir de una descripción
- &#128202; Extracción de datos de PDFs, facturas y hojas de cálculo

## &#127959;&#65039; Arquitectura

`
cliente (web)
    |
    v
API (Node.js / Next.js API routes)
    |-- procesos de negocio (workflows)
    -- proveedores de IA (OpenAI / Anthropic / Bedrock)
            |
            v
base de datos (PostgreSQL) + cola de tareas
`

| Capa | Tecnología |
|---|---|
| Frontend | Next.js + TailwindCSS |
| Backend | Node.js + Next.js API routes |
| IA | OpenAI GPT · Anthropic Claude · AWS Bedrock |
| Datos | PostgreSQL + Prisma |
| Deploy | Vercel (web) + AWS (tareas pesadas) |

## &#128640; Deploy al dominio propio

### Opción A — Vercel (recomendado)

`ash
git clone https://github.com/tuusuario/serviciosautomaticosgpt.git
cd serviciosautomaticosgpt

npm install
cp .env.example .env

vercel login
vercel link
vercel --prod
`

**Para apuntar tu dominio en Vercel:**

1. Vercel &#8594; tu proyecto &#8594; *Settings* &#8594; *Domains*
2. Añade 	udominio.com (y www.tudominio.com)
3. En tu registrador (Porkbun, Cloudflare, etc.) crea dos registros:
   - CNAME  @    &#8594;  cname.vercel-dns.com
   - CNAME  www  &#8594;  cname.vercel-dns.com
4. Espera a que propague (5–30 min) y el dominio quedará en línea con SSL automático.

### Opción B — Docker

`ash
docker build -t serviciosautomaticosgpt .
docker run -p 3000:3000 --env-file .env serviciosautomaticosgpt
`

## &#9881;&#65039; Variables de entorno

Copia .env.example a .env y completa:

`
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
DATABASE_URL=postgresql://usuario:pass@host:5432/db
REDIS_URL=redis://host:6379
`

## &#129520; Desarrollo local

`ash
npm run dev
`

Abre [http://localhost:3000](http://localhost:3000).

## &#128193; Estructura del proyecto

`
├── app/            # frontend (Next.js App Router)
├── lib/            # clientes de IA y utilidades
├── workflows/      # automatizaciones de negocio
├── prisma/         # esquema de base de datos
└── public/         # estáticos
`

## Licencia

MIT — ver [LICENSE](LICENSE).

---

Hecho con &#9889; por **Servicios Automáticos GPT** · [serviciosautogpt.xyz](https://serviciosautogpt.xyz)
