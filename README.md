<p align="center">
  <img src="https://img.shields.io/badge/status-active-success" />
  <img src="https://img.shields.io/badge/stack-Next.js%20%7C%20Node-black" />
  <img src="https://img.shields.io/badge/AI-GPT%2FClaude-blueviolet" />
</p>

<h1 align="center">⚡ Servicios Automáticos GPT</h1>
<p align="center">
  <b>Automatizamos lo repetitivo de tu negocio para que tú hagas lo que importa.</b>
</p>

---

## 🧠 Qué es

**Servicios Automáticos GPT** es una plataforma que construye asistentes y
automatizaciones inteligentes sobre modelos de lenguaje (GPT/Claude) para
pequeñas y medianas empresas:

- 📄 Generación de documentos, propuestas y presupuestos
- 📧 Respuesta automática a correos y consultas frecuentes
- 📅 Gestión de citas, recordatorios y seguimiento de clientes
- 🌐 Webs y landing pages generadas a partir de una descripción
- 📊 Extracción de datos de PDFs, facturas y hojas de cálculo

## 🏗️ Arquitectura

`
cliente (web)
   │
   ▼
API (Node.js / Next.js API routes)
   ├── procesos de negocio (workflows)
   └── proveedores de IA (OpenAI / Anthropic / Bedrock)
          │
          ▼
     base de datos (PostgreSQL) + cola de tareas
`

| Capa | Tecnología |
|---|---|
| Frontend | Next.js + TailwindCSS |
| Backend | Node.js + Next.js API routes |
| IA | OpenAI GPT · Anthropic Claude · AWS Bedrock |
| Datos | PostgreSQL + Prisma |
| Deploy | Vercel (web) + AWS (tareas pesadas) |

## 🚀 Deploy a tu dominio

### Opción A — Vercel (recomendado)

`ash
# 1. Clona el repo
git clone https://github.com/tuusuario/serviciosautomaticosgpt.git
cd serviciosautomaticosgpt

# 2. Instala y prepara
npm install
cp .env.example .env   # rellena .env con tus claves

# 3. Conecta el proyecto a Vercel
vercel login
vercel link

# 4. Despliega
vercel --prod
`

**Para el dominio propio en Vercel:**
1. Vercel → tu proyecto → *Settings → Domains*
2. Añade 	udominio.com (y www)
3. En tu registrador (Porkbun, Cloudflare...) crea:
   - CNAME  @  →  cname.vercel-dns.com
   - CNAME  www →  cname.vercel-dns.com
4. Espera a que propague (5–30 min) y listo.

### Opción B — Docker

`ash
docker build -t serviciosautomaticosgpt .
docker run -p 3000:3000 --env-file .env serviciosautomaticosgpt
`

## ⚙️ Variables de entorno

Copia .env.example a .env y completa:

`
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
DATABASE_URL=postgresql://usuario:pass@host:5432/db
REDIS_URL=redis://host:6379
`

## 🧪 Desarrollo local

`ash
npm run dev
# http://localhost:3000
`

## 📁 Estructura del proyecto

`
├── app/            # frontend (Next.js App Router)
├── lib/            # clientes de IA y utilidades
├── workflows/      # automatizaciones de negocio
├── prisma/         # esquema de base de datos
└── public/         # estáticos
`

## 🤝 Licencia

MIT — haz lo que quieras, atribución bienvenida.

---

<p align="center">
  Hecho con ⚡ por <a href="https://serviciosautomaticosgpt.com">Servicios Automáticos GPT</a>
</p>
