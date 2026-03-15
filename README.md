AGENTES CREADOS POR MI PARA COMPARTIR CON LA MUCHACHADA! 2026

[![n8n](https://img.shields.io/badge/n8n-FF6C37?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io/)
[![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![JSON](https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white)](https://www.json.org/json-en.html)
[![GitHub License](https://img.shields.io/github/license/Giragui/Agentes-N8N-con-cerebro-y-tickets?style=for-the-badge)](https://github.com/Giragui/Agentes-N8N-con-cerebro-y-tickets/blob/main/LICENSE.txt)

# Ecosistema de Agentes IA con n8n 🤖🚀

Este repositorio contiene una colección de flujos de trabajo (workflows) de **n8n** diseñados para la automatización de comunidades, soporte técnico y gestión de contenidos, integrando modelos de IA con bases de datos dinámicas. (en el archivo .json esta la totalidad de los agentes, en los TXT dentro de la carpeta N8N workflows tengo los agentes separados.) "SALUDOS ESPERO Q TE SIRBA BRO"

## 🧠 Arquitectura de los Agentes

La lógica de estos agentes se basa en un modelo de **Memoria Externa y Gestión de Estados**:

* **Cerebro (Google Sheets):** Los agentes consultan y escriben en hojas de cálculo que actúan como memoria persistente, permitiendo recordar contextos de usuarios y reglas de negocio sin depender solo de la ventana de contexto del LLM.
* **Sistema de Ticketing:** Flujo automatizado para capturar leads o problemas técnicos en Sheets, facilitando el seguimiento humano posterior.
* **Omnicanalidad:** Integración fluida con **Telegram** e **Instagram** para la interacción directa con el usuario final.

## 🤖 Workflows Principales

### 🦊 UronBot (Gestión de Redes)
* **Canales:** Instagram y Telegram.
* **Función:** Automatización de respuestas y filtrado de interacciones.
* **IA:** Conectado a modelos para interpretar la intención del usuario y decidir si deriva a un humano o resuelve con la base de conocimientos.

### 🍄 Docobot (Academia Docdoco)
* **Especialidad:** Micología y cultivo.
* **Lógica:** Gestiona el login y las consultas de alumnos de la academia `iragui.ddns.net`.
* **Memoria:** Utiliza Sheets para validar estados de usuarios y registrar el progreso de consultas.

### 📰 News Dev Agent
* **Función:** Curación de contenidos para desarrolladores.
* **Proceso:** Scrapea fuentes de noticias, las procesa mediante IA para resumirlas y las publica en canales específicos.

## 🛠️ Stack Tecnológico

* **Motor de Automatización:** n8n (Self-hosted en Docker).
* **Base de Datos / Memoria:** Google Sheets API.
* **Interfaces de Usuario:** Telegram Bot API, Instagram Graph API.
* **Infraestructura:** VPS con Caddy como Reverse Proxy.

## 🚀 Cómo usar estos Workflows

1.  Importa los archivos `.json` en tu panel de n8n.
2.  Configura las **Credentials** para Google Cloud, Telegram e Instagram.
3.  Asegúrate de que las IDs de las hojas de cálculo en los nodos de Sheets coincidan con tus archivos locales.

### 🏗️ Arquitectura del Sistema

```mermaid
graph TD
    User((Usuario/Admin)) -->|Puerto 80/443| Caddy[Caddy Server]
    User -->|VPN| WG[WireGuard]
    
    subgraph "Docker Stack"
        Caddy -->|Proxy| n8n[n8n Automation]
        n8n -->|Memoria| GS[Google Sheets]
        n8n -->|Tickets| Agent[Agente IA]
    end

