## Estratégias de Atualização de Deployments no Kubernetes

Quando criamos um **Deployment** no Kubernetes, não precisamos necessariamente definir uma estratégia de atualização. Nesse caso, o Kubernetes aplica automaticamente a estratégia padrão: **RollingUpdate**.

Mas você sabia que o Kubernetes oferece **duas estratégias principais** para atualizar seus Deployments?

- **RollingUpdate**
- **Recreate**

Essas estratégias definem como os Pods de um Deployment serão atualizados quando há alterações na definição do recurso — como uma nova imagem de container ou mudanças nas configurações.
