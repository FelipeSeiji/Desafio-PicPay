# 🚀 Desafio Back-End

## 🏦 Desafio de Backend - Plataforma de Pagamentos

Primeiramente, obrigado pelo seu interesse! Este desafio tem como objetivo avaliar suas habilidades técnicas na construção de uma API RESTful simulando uma plataforma de pagamentos simplificada.

## 💻 Sobre o ambiente de desenvolvimento

- Utilize qualquer linguagem ou framework com o qual se sinta confortável.
- É permitido desenvolver sem framework, utilizando apenas scripts e bibliotecas, se desejar.
- Evite o uso excessivo de métodos mágicos ou automações que escondam sua lógica.
- Valorize uma boa estruturação, desacoplamento e uso de containers (Docker).

## 🎯 Objetivo

Desenvolver uma API RESTful que simula um sistema de pagamentos, permitindo transferências de valores entre usuários, considerando as seguintes regras de negócio.

## 🔗 Regras de Negócio

- Dois tipos de usuários:
  - **Comum:** pode enviar e receber transferências.
  - **Lojista:** **somente recebe** transferências.

- Dados obrigatórios para cadastro:
  - Nome completo
  - CPF/CNPJ (único)
  - E-mail (único)
  - Senha

- Validações:
  - Não permitir cadastros com CPF/CNPJ ou e-mails duplicados.
  - Validar saldo suficiente antes de realizar transferências.
  - Lojistas **não podem** enviar dinheiro.

- Integrações externas:
  - Verificar autorização da transação via serviço externo (GET):  
    👉 https://util.devi.tools/api/v2/authorize
  - Notificar o recebedor via serviço externo (POST):  
    👉 https://util.devi.tools/api/v1/notify

- As transferências devem ser tratadas como **transações atômicas**. Em caso de erro em qualquer etapa, a operação deve ser desfeita.

## 📑 Contrato da API de Transferência

### Endpoint

POST /transfer

### Request

```json
{
  "value": 100.0,
  "payer": 4,
  "payee": 15
}
