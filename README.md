# FeedAI
FeedAI es una implementación local de GPT que integra Ollama, OpenWebUI y Rancher. Permite crear un asistente para soporte con contexto personalizado a partir de archivos PDF, DOC, TXT y más, usando el patrón RAG. Su objetivo es ser una solución simple y fácil de usar.



# 🧠 Instala tu propio ChatGPT local y gratis con Ollama + OpenWebUI

Este tutorial te enseña cómo montar una versión local de ChatGPT usando [Ollama](https://ollama.com/) y [OpenWebUI](https://github.com/open-webui/open-webui). No necesitas conexión a Internet una vez instalado ni pagar suscripciones.

---

## ✅ Requisitos

- Sistema operativo: Windows, macOS o Linux
- Conexión a Internet (solo para la instalación)
- Rancher Desktop
- Terminal / consola

---

## 1. Instalar Ollama

Ollama permite ejecutar modelos LLM localmente.

### 🔽 Paso 1: Descargar Ollama

Ve a: [https://ollama.com/download](https://ollama.com/download)

Elige tu sistema operativo e instala.

### ▶️ Paso 2: Ejecutar un modelo

Una vez instalado, abre la terminal y corre:

```bash
ollama run llama3
```

Esto descargará y ejecutará el modelo **LLaMA 3**, uno de los más avanzados actualmente disponibles.

---

## 2. Instalar OpenWebUI

Es una interfaz tipo ChatGPT que se conecta con Ollama.

### 🐮 Paso 1: Descargar Rancher Desktop

Desde: [https://rancherdesktop.io/](https://rancherdesktop.io/)

Sigue el instalador para tu sistema operativo.

### ⚙️ Paso 2: Configurar Rancher Desktop

- Asegúrate de tener activado **containerd** o **dockerd** como backend.

---

### 🚀 Paso : Ejecutar OpenWebUI con Rancher

Corre el siguiente comando:

```bash
docker run -d -p 3000:8080 -v open-webui:/app/backend/data -e OLLAMA_API_BASE_URL=http://host.docker.internal:11434 --name open-webui   --restart always ghcr.io/open-webui/pen-webui:main
```

Esto levantará la interfaz en: [http://localhost:3000](http://localhost:3000)

---

## 3. Usar ChatGPT localmente

1. Abre tu navegador en `http://localhost:3000`
2. Asegúrate de que Ollama esté corriendo en segundo plano
3. Empieza a chatear con el modelo descargado

---

## ⚙️ Consejos adicionales

- Puedes cambiar el modelo con: `ollama run mistral` o `ollama run gemma`
- Si tienes GPU, Ollama la usará automáticamente
- OpenWebUI guarda tu historial y permite personalizar la experiencia

---

## 🧼 Para detener

```bash
docker stop openwebui
ollama stop llama3
```

---

## 📚 Recursos

- Ollama Docs: https://ollama.com
- OpenWebUI GitHub: https://github.com/open-webui/open-webui

---

## 🧭 Seleccionar el contexto de Docker correcto para Rancher Desktop

Si estás usando Rancher Desktop, asegúrate de que tu terminal esté usando el contexto adecuado de Docker. Ejecuta:

```bash
docker context use rancher-desktop
```

Este comando garantiza que los contenedores se ejecuten en el entorno de Rancher y no en otro motor Docker que puedas tener instalado.

---
