## Estratégias de Atualização de Deployments no Kubernetes

Quando criamos um **Deployment** no Kubernetes, não precisamos necessariamente definir uma estratégia de atualização. Nesse caso, o Kubernetes aplica automaticamente a estratégia padrão: **RollingUpdate**.

Mas você sabia que o Kubernetes oferece **duas estratégias principais** para atualizar seus Deployments?

- **RollingUpdate**
- **Recreate**

Essas estratégias definem como os Pods de um Deployment serão atualizados quando há alterações na definição do recurso — como uma nova imagem de container ou mudanças nas configurações.

### Estratégia RollingUpdate

A estratégia **RollingUpdate** é a **padrão** utilizada pelo Kubernetes para atualizar os Pods de um Deployment de forma **gradual** — ou seja, ela atualiza um Pod por vez ou em pequenos grupos, sem interromper todo o serviço de uma só vez.

Essa abordagem é ideal para garantir **alta disponibilidade** durante atualizações, principalmente em ambientes de produção.

---

## 🔧 Exemplo de Configuração

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webserver
spec: 
  replicas: 10
  selector: 
    matchLabels: 
      app: webserver
  strategy: 
    type: RollingUpdate
    rollingUpdate: 
      maxSurge: 5
      maxUnavailable: 5
  template:
    metadata:
      labels:
        app: webserver
    spec:
      containers:
        - name: nginx
          image: nginx:latest
```

