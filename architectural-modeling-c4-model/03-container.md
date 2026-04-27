# Nível 2 - Contêiner (Container)

## Objetivo da Seção

Nesta seção, o foco é compreender a **segunda camada do C4 Model**: o **nível de contêiner**. Aqui, deixamos de olhar o
sistema “de fora” (contexto) e passamos a analisar sua **estrutura interna**, identificando:

* Componentes principais (containers)
* Responsabilidades de cada parte
* Tecnologias utilizadas
* Relacionamentos entre os elementos

## 1. Conceito de Container no C4 Model

### Definição

Um **container** é uma unidade de software que:

* É **executável de forma independente**
* Possui uma **responsabilidade bem definida**
* Pode ser **implantada isoladamente**
* Pode ser **reutilizada em outros sistemas**

### Exemplos comuns de containers

* Aplicações Web
* APIs
* Aplicações Mobile
* Bancos de dados
* Sistemas de mensageria

## 2. Público-Alvo dessa Camada

A abstração em nível de contêiner é voltada para:

* Arquitetos de software
* Desenvolvedores
* Equipe de suporte
* Profissionais técnicos em geral

👉 Diferente do nível de contexto, aqui a comunicação já é **mais técnica**.

## 3. Escopo e Organização do Diagrama

### Elementos de Escopo

No nível de contêiner utilizamos:

* **Software System (escopo principal)**
* Containers internos ao sistema

O sistema é representado por um **limite (boundary)**, e dentro dele colocamos os containers.

![Escopo](./../images/004-context.png)

## 4. Construção da Arquitetura (Estudo de Caso)

### Sistema: Sistema de Auditoria

A seguir, são apresentados os containers identificados e suas responsabilidades.

## 5. Containers Identificados

### 5.1 Aplicação de Sincronização com WhatsApp

* **Nome:** Web Application
* **Tecnologia:** WhatsMeow
* **Responsabilidade:** Sincronizar mensagens do WhatsApp

#### Observação

A escolha foi validada por meio de uma PoC (Prova de Conceito).

### 5.2 Banco de Dados Relacional

* **Nome:** Banco de Dados
* **Tecnologia:** PostgreSQL
* **Responsabilidade:** Armazenar contatos e dados de sincronização

### 5.3 Banco de Dados Não Relacional

* **Nome:** Banco de Dados
* **Tecnologia:** MongoDB
* **Responsabilidade:** Armazenar mensagens em formato JSON

#### Justificativa:

* Melhor performance para leitura
* Estrutura compatível com JSON
* Separação de responsabilidades

### 5.4 Aplicação Web (QR Code)

* **Nome:** Single Page Application
* **Tecnologia:** Next.js
* **Responsabilidade:** Exibir QR Code para vinculação do WhatsApp

### 5.5 Aplicação Administrativa

* **Nome:** Single Page Application
* **Tecnologia:** Next.js
* **Responsabilidade:** Interface para administração e auditoria

### 5.6 API Backend

* **Nome:** Web API
* **Tecnologia:** NestJS
* **Responsabilidade:** Fornecer dados via API REST (JSON/HTTPS)

## 6. Relacionamentos entre Containers

### Principais Integrações

| Origem            | Destino    | Descrição          |
|-------------------|------------|--------------------|
| WhatsMeow         | PostgreSQL | Armazena contatos  |
| WhatsMeow         | MongoDB    | Armazena mensagens |
| Next.js (Admin)   | NestJS     | Consome API        |
| Next.js (QR Code) | NestJS     | Solicita QR Code   |
| NestJS            | MongoDB    | Recupera mensagens |
| NestJS            | PostgreSQL | Recupera contatos  |
| Next.js           | SSO        | Autenticação       |
| NestJS            | SSO        | Validação de token |

## 7. Autenticação e Segurança

O sistema utiliza um serviço de autenticação (SSO):

* Frontend obtém um **token**
* Backend valida esse token antes de responder

#### Isso garante:

* Segurança
* Controle de acesso
* Separação de responsabilidades

## 8. Fluxo de Geração do QR Code

### Passo a Passo

1. Usuário acessa a aplicação web
2. A aplicação chama a API
3. A API solicita à aplicação de sincronização
4. Um worker é iniciado
5. Um QR Code é gerado (em formato string)
6. Retorno para API → Frontend → Usuário

## 9. Decisões Arquiteturais Importantes

### Separação de bancos de dados

* Relacional → contatos
* Não relacional → mensagens

### Uso de API centralizada

* Desacoplamento entre frontends e serviços
* Facilita evolução futura (ex: Telegram)

### Uso de SPA

* Melhor experiência do usuário
* Separação clara entre frontend e backend

## 10. Boas Práticas Observadas

* Definição clara de responsabilidades
* Uso de PoC antes de decisões técnicas
* Desacoplamento entre componentes
* Escolha de tecnologias alinhadas ao time
* Preparação para escalabilidade

## 11. Resumo da Camada de Container

No nível de contêiner do C4 Model:

* O sistema é **decomposto em partes executáveis**
* Cada container tem:
    * Nome
    * Tecnologia
    * Responsabilidade
* Os **relacionamentos** são explícitos
* As **principais decisões técnicas são evidenciadas**

![Container](../images/005-container.png)