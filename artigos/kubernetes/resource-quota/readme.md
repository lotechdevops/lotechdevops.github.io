## O que é o ResourceQuota?

O ResourceQuota no Kubernetes é uma ferramenta para gerenciar e limitar o uso de recursos em um namespace. Ele garante que equipes ou aplicações compartilhem os recursos de forma controlada dentro de um cluster. Com o ResourceQuota, é possível definir limites máximos para memória, CPU, armazenamento, quantidade de objetos como pods, serviços, volumes, entre outros.
Isso é útil em ambientes com múltiplos usuários ou aplicações, prevenindo que uma única aplicação consuma todos os recursos do cluster. O ResourceQuota trabalha em conjunto com as configurações de Requests e Limits, que são definidas nos contêineres.

### Tipos de Recursos Suportados

Você pode incluir diferentes tipos de recursos no ResourceQuota

### Tipos de Recursos Suportados

Você pode incluir diferentes tipos de recursos no ResourceQuota

#### Recursos computacionais

- requests.cpu, requests.memory
- limits.cpu, limits.memory