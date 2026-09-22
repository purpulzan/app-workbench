<p align="center">
  <img src="https://img.shields.io/badge/status-active-success" alt="status" />
  <img src="https://img.shields.io/badge/stack-Next.js%20%7C%20Node-black" alt="stack" />
  <img src="https://img.shields.io/badge/AI-GPT%2FClaude-blueviolet" alt="ai" />
</p>

<h1 align="center">⚡ Servicios Automáticos GPT</h1>
<p align="center">
  <strong>Automatizamos lo repetitivo de tu negocio para que tú hagas lo que importa.</strong>
</p>

---

## 🧠 Qué es

**Servicios Automáticos GPT** es una plataforma que construye asistentes y
automatizaciones inteligentes sobre modelos de lenguaje (GPT / Claude) para
pequeñas y medianas empresas:

- 📄 Generación de documentos, propuestas y presupuestos
- 📧 Respuesta automática a correos y consultas frecuentes
- 📅 Gestión de citas, recordatorios y seguimiento de clientes
- 🌐 Webs y landing pages generadas a partir de una descripción
- 📊 Extracción de datos de PDFs, facturas y hojas de cálculo

## 🏗️ Arquitectura

```
cliente (web)
    |
    v
API (Node.js / Next.js API routes)
    |-- procesos de negocio (workflows)
    `-- proveedores de IA (OpenAI / Anthropic / Bedrock)
            |
            v
base de datos (PostgreSQL) + cola de tareas
```

| Capa | Tecnología |
|---|---|
| Frontend | Next.js + TailwindCSS |
| Backend | Node.js + Next.js API routes |
| IA | OpenAI GPT · Anthropic Claude · AWS Bedrock |
| Datos | PostgreSQL + Prisma |
| Deploy | Vercel (web) + AWS (tareas pesadas) |

## 🚀 Deploy al dominio propio

### Opción A — Vercel (recomendado)

```bash
git clone https://github.com/tuusuario/serviciosautomaticosgpt.git
cd serviciosautomaticosgpt

npm install
cp .env.example .env

vercel login
vercel link
vercel --prod
```

**Para apuntar tu dominio en Vercel:**

1. Vercel → tu proyecto → *Settings* → *Domains*
2. Añade `tudominio.com` (y `www.tudominio.com`)
3. En tu registrador (Porkbun, Cloudflare, etc.) crea dos registros:
   - `CNAME @ → cname.vercel-dns.com`
   - `CNAME www → cname.vercel-dns.com`
4. Espera a que propague (5–30 min) y el dominio quedará en línea con SSL automático.

### Opción B — Docker

```bash
docker build -t serviciosautomaticosgpt .
docker run -p 3000:3000 --env-file .env serviciosautomaticosgpt
```

## ⚙️ Variables de entorno

Copia `.env.example` a `.env` y completa:

```
OPENAI_API_KEY=sk-...
ANTHROPIC_API_KEY=sk-ant-...
DATABASE_URL=postgresql://usuario:pass@host:5432/db
REDIS_URL=redis://host:6379
```

## 🧰 Desarrollo local

```bash
npm run dev
```

Abre [http://localhost:3000](http://localhost:3000).

## 📁 Estructura del proyecto

```
├── app/            # frontend (Next.js App Router)
├── lib/            # clientes de IA y utilidades
├── workflows/      # automatizaciones de negocio
├── prisma/         # esquema de base de datos
└── public/         # estáticos
```

## Licencia

MIT — ver [LICENSE](LICENSE).

---

Hecho con ⚡ por **Servicios Automáticos GPT** · [serviciosautogpt.xyz](https://serviciosautogpt.xyz)
