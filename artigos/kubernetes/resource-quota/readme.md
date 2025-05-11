## O que é o ResourceQuota?

O ResourceQuota no Kubernetes é uma ferramenta para gerenciar e limitar o uso de recursos em um namespace. Ele garante que equipes ou aplicações compartilhem os recursos de forma controlada dentro de um cluster. Com o ResourceQuota, é possível definir limites máximos para memória, CPU, armazenamento, quantidade de objetos como pods, serviços, volumes, entre outros.
Isso é útil em ambientes com múltiplos usuários ou aplicações, prevenindo que uma única aplicação consuma todos os recursos do cluster. O ResourceQuota trabalha em conjunto com as configurações de Requests e Limits, que são definidas nos contêineres.

## Tipos de Recursos Suportados

Você pode incluir diferentes tipos de recursos no ResourceQuota

#### Recursos computacionais

- requests.cpu, requests.memory
- limits.cpu, limits.memory

#### Recursos de armazenamento

- requests.storage
- Limite por StorageClass (persistentVolumeClaims, storageclass.<name>.resquests.storage)

#### Quantidade de objetos

- Número máximo de pods (pods), serviços (services), ingress (ingresses), ConfigMaps (configmaps), Secrets (secrets), entre outros.

## Principais Benefícios

- Controle de recursos no nível de namespace.
- Prevenção contra abuso de recursos.
- Melhor gerenciamento de custos em clusters compartilhados.

## Recomendações

- **Analise o uso do namespace:** Garanta que os limites do ResourceQuota atendem à carga esperada.
- **Planeje os recursos dos pods:** Certifique-se de que os requests e limits sejam otimizados para evitar disperdício ou restrições desnecessárias.
- Use ferramentas como o kubectl describe quota <quota-name> para verificar o consumo atual e entender melhor os limites impostos.

## Como ResouceQuota interage com Requests e Limits?

