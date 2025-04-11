## O que é o cert-manager?

O cert-manager é um controlador nativo do Kubernetes que automatiza a criação, renovação e gerenciamento de certificados SSL/TLS. Ele facilita a integração com Autoridades Certificadoras (CAs), como o Let’s Encrypt, permitindo que os certificados sejam emitidos e renovados automaticamente dentro de um cluster Kubernetes.

Ele é essencial para manter conexões seguras em apliações expostas via ingress controllers, como o NGINX Ingress, Traefik ou Istio.

## Como ele funciona?
O cert-manager gerencia certificados no Kubernetes por meio do Custom Resource Definitions (CRDs), que permitem definir regras para emissão e renovação de certificados. Ele opera em quatros etapas principais:

**1 — Issuer/ClusterIssuer**

* Define a CA responsável pela emissão dos certificados.
* Pode ser um Issuer (válido apenas no namespace onde foi criado) ou um ClusterIssuer (válido em todo o cluster).

**2 — Solicitação de Certificados (Certificate)**

* Define um recurso Certificate para solicitar certificados com base no Issuer ou ClusterIssuer.

**3 — Validação do domínio**

* O cert-manager usa desafios ACME (HTTP-01 ou DNS-01) para validar a posse do domínio.

**4 — Emissão e renovação automática**

* O certificado é armazenado como um Secret no Kubernetes e é automaticamente renovado antes do vencimento.

## O que é o Let’s Encrypt?

O Let’s Encrypt é uma Autoridade Certificadora (CA) gratuita e automatizada que fornece certificados SSL/TLS para proteger aplicações com criptografia HTTPS. Ele é amplamente utilizado para garantir conexões seguras na web sem a necessidade de comprar certificados de outras CAs pagas.

### Como ele funciona?

O Let’s Encrypt utiliza um protocolo chamado ACME (Automated Certificate Management Environmet), que permite a emissão e renovação automática dos certificados. O processo ocorre em três etapas principais:

**1 — Validação do Domínio**

* O Let’s Encrypt verifica se você realmente tem controle sobre o domínio para o qual deseja emitir o certificado.

* Isso pode ser feito de três maneiras:

    1 - **HTTP-01:** Um arquivo temporário é criado no servidor web para ser acessado pelo Let’s Encrypt.

    2 - **DNS-01:** Um registro TXT é adicionado ao DNS do domínio.
    
    3 - **TLS-ALPN-01:** Um certificado especial é servido via TLS.

**2 — Emissão do Certificado**

* Após validar o domínio, o Let’s Encrypt emite um certificado SSL/TLS válido por 90 dias.

**3 — Renovação automática**

* Ferramentas como cert-manager podem ser configurados para renovar os certifiados automaticamente antes do vencimento.


## 🛠️ Passo a Passo Configuração

Nosso nosso exemplo iremos utilizar um domínio hospedado na AWS Route53.

**1 — Criar um Secret com as credenciais da conta da AWS:**

```bash
kubectl create secret generic route53-credentials-secret \
  --from-literal=access-key-id=SEU_ACCESS_KEY \
  --from-literal=secret-access-key=SEU_SECRET_KEY \
  -n cert-manager
```