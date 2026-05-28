
# 🚀 Tekton Minikube CI/CD Demo

Pipeline completo de CI/CD ejecutándose localmente con Kubernetes usando Tekton y Minikube.

Cada cambio en el repositorio puede construirse y desplegarse automáticamente dentro de un cluster Kubernetes local.

---

# 🏗 Arquitectura

```text
GitHub Push
    ↓
GitHub Webhook
    ↓
ngrok Tunnel
    ↓
Tekton EventListener
    ↓
Tekton Trigger
    ↓
Tekton Pipeline
    ↓
Build Docker Image
    ↓
Deploy en Kubernetes
    ↓
Aplicación actualizada automáticamente
````

---

# 🧱 Stack Tecnológico

* Kubernetes
* Minikube
* Tekton Pipelines
* Tekton Triggers
* Docker
* GitHub Webhooks
* ngrok
* Nginx

---

# 📦 Estructura del Proyecto

```text
.
├── app/                       # Aplicación demo
│   ├── index.html
│   └── Dockerfile
│
├── k8s/                       # Recursos Kubernetes
│   ├── deployment.yaml
│   └── service.yaml
│
├── tekton/                    # Recursos Tekton
│   ├── pipeline.yaml
│   ├── pipelinerun.yaml
│   ├── trigger-template.yaml
│   ├── trigger-binding.yaml
│   ├── event-listener.yaml
│   └── tasks/
│
└── README.md
```

---

# ⚙️ ¿Cómo funciona?

## 1. Aplicación

La aplicación es una página HTML simple servida con Nginx.

```html
<h1>CI/CD Demo - Version 1</h1>
```

---

## 2. Build de imagen

Tekton construye automáticamente la imagen Docker:

```bash
docker build -t demo-app:latest .
```

---

## 3. Deploy en Kubernetes

Luego despliega la aplicación en Minikube:

```bash
kubectl apply -f k8s/
```

---

## 4. Automatización CI/CD

Cuando se realiza un `git push`:

1. GitHub envía un webhook
2. ngrok expone el EventListener localmente
3. Tekton Trigger crea un `PipelineRun`
4. Se construye una nueva imagen
5. Kubernetes actualiza el Deployment automáticamente

---

# 🧪 Ejecución Local

## 1. Iniciar Minikube

```bash
minikube start
```

---

## 2. Aplicar recursos Kubernetes y Tekton

```bash
kubectl apply -f k8s/
kubectl apply -f tekton/
```

---

## 3. Exponer el EventListener

```bash
kubectl port-forward svc/el-cicd-listener 8080:8080 -n demo
```

---

## 4. Crear túnel con ngrok

```bash
ngrok http 8080
```

---

## 5. Configurar Webhook en GitHub

### URL

```text
https://xxxx.ngrok.io
```

### Content Type

```text
application/json
```

### Evento

```text
push
```

---

# 🎯 Resultado

Cada `git push` ejecuta automáticamente:

* ✔ Clonado del repositorio
* ✔ Build de imagen Docker
* ✔ Deploy en Kubernetes
* ✔ Actualización automática de la aplicación

---

# 📸 Idea de Demo (TikTok / LinkedIn)

1. Editar `index.html`
2. Hacer commit y push
3. Mostrar Tekton ejecutando el pipeline
4. Mostrar la app actualizándose automáticamente en el navegador

---

# 🧠 Objetivo del Proyecto

Demostrar un flujo real de CI/CD cloud-native usando herramientas modernas del ecosistema Kubernetes, de forma:

* Local
* Reproducible
* Visual
* Fácil de entender

Ideal para aprender conceptos reales de DevOps y Platform Engineering.

---

# 🔥 Autor

**Javier Martinez**
DevOps Engineer

```
```

