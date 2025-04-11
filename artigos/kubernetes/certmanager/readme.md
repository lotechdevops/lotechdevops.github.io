## O que é o cert-manager?

O cert-manager é um controlador nativo do Kubernetes que automatiza a criação, renovação e gerenciamento de certificados SSL/TLS. Ele facilita a integração com Autoridades Certificadoras (CAs), como o Let’s Encrypt, permitindo que os certificados sejam emitidos e renovados automaticamente dentro de um cluster Kubernetes.

Ele é essencial para manter conexões seguras em apliações expostas via ingress controllers, como o NGINX Ingress, Traefik ou Istio.

## Como ele funciona?
O cert-manager gerencia certificados no Kubernetes por meio do Custom Resource Definitions (CRDs), que permitem definir regras para emissão e renovação de certificados. Ele opera em quatros etapas principais:

1 — Issuer/ClusterIssuer

* Define a CA responsável pela emissão dos certificados.
* Pode ser um Issuer (válido apenas no namespace onde foi criado) ou um ClusterIssuer (válido em todo o cluster).