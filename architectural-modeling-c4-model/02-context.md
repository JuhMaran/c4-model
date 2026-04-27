# Nível 1 - Contexto (Context)

## Objetivo da Seção

Nesta seção você aprenderá a:

* Compreender o **nível de contexto** do C4 Model
* Identificar **atores, sistemas externos e responsabilidades**
* Construir um **diagrama de contexto claro e acessível**
* Extrair **insights arquiteturais ainda na fase de design**

## 1. O que é o Nível de Contexto?

O **nível de contexto** é a camada mais **abstrata e inicial** do C4 Model.

### Finalidade

Apresentar:

* O sistema principal
* Quem interage com ele
* Quais sistemas externos existem
* Como essas interações acontecem

### Público-alvo

Este nível é direcionado para:

* Stakeholders técnicos (devs, arquitetos)
* Stakeholders não técnicos (negócio, gestores)
* Pessoas externas ao time

👉 Por isso:

* Use linguagem **simples**
* Evite termos técnicos desnecessários
* Foque na **clareza**

### Pergunta que esse nível responde:

> “Como o sistema se encaixa no mundo ao seu redor?”

## 2. Elementos do Diagrama de Contexto

### Principais elementos

* **Person (Pessoa)** → Usuários ou atores
* **Software System** → Sistema principal ou externo
* **Relationship** → Interações entre elementos

### Boas práticas

* Nome claro e objetivo
* Descrição em linguagem acessível
* Relacionamentos com verbos (ex: “consultar”, “enviar”, “gerenciar”)

## 3. Construindo o Diagrama de Contexto

### Sistema analisado

Sistema de Auditoria de mensagens do WhatsApp.

### Passo 1: Identificar o ator principal

#### Responsável pelo número telefônico

* **Descrição:**
  Profissional da instituição responsável pela comunicação via WhatsApp

### Passo 2: Identificar sistema externo

#### WhatsApp

* **Tipo:** Sistema externo
* **Descrição:** Sistema de mensagens instantâneas

### Passo 3: Identificar o sistema principal

#### Sistema de Auditoria

* **Descrição:**
  Sistema de vinculação e monitoramento de mensagens

### Passo 4: Definir relacionamentos

| Origem  | Destino  | Descrição           |
|---------|----------|---------------------|
| Usuário | WhatsApp | Trocar mensagens    |
| Usuário | Sistema  | Ler QR Code         |
| Sistema | WhatsApp | Consultar mensagens |

### Visualização do contexto inicial

![](../images/002-context.png)

### Interpretação

Esse primeiro desenho já permite:

* Entender o **papel do sistema**
* Identificar **fluxos principais**
* Visualizar dependências externas

## 4. Extraindo Insights do Diagrama

### Problema identificado

Pergunta crítica:

> O que impede qualquer pessoa de vincular um número ao sistema?

### Risco

* Qualquer usuário poderia:
    * Vincular números indevidos
    * Comprometer segurança
    * Violar LGPD

### Insight importante

> O diagrama revelou um problema **antes da implementação**

**✔️ Benefício direto:**

* Evita retrabalho
* Reduz impacto em custo e prazo

## 5. Evolução do Diagrama de Contexto

### Nova necessidade

Controle de acesso e gestão de números

### Novo ator

#### Administrador

* **Descrição:**
  Responsável pela gestão dos números monitorados

### Novo relacionamento

| Origem        | Destino | Descrição         |
|---------------|---------|-------------------|
| Administrador | Sistema | Gerenciar números |

### Nova dependência externa

#### Sistema de Login (SSO)

Exemplo:

* Keycloak

### Relacionamento adicional

| Origem  | Destino | Descrição                  |
|---------|---------|----------------------------|
| Sistema | SSO     | Autenticação / Autorização |

### Diagrama de contexto evoluído

![](../images/003-context.png)

### Interpretação da evolução

Agora o sistema possui:

* Controle de acesso
* Separação de responsabilidades
* Segurança adequada
* Melhor alinhamento com requisitos legais

## 6. Aprendizados da Camada de Contexto

### Principais benefícios

* Visão clara do sistema no ecossistema
* Comunicação eficiente com qualquer público
* Identificação precoce de riscos
* Base sólida para próximas camadas

### Erros comuns

* Usar termos técnicos demais
* Excesso de detalhes
* Ignorar atores externos
* Não descrever relacionamentos

## 7. Resumo Estruturado

### Elementos definidos

#### Pessoas

* Responsável pelo número telefônico
* Administrador

#### Sistemas

* Sistema de Auditoria (principal)
* WhatsApp (externo)
* SSO / Keycloak (externo)

#### Relacionamentos

* Troca de mensagens
* Leitura de QR Code
* Consulta de mensagens
* Gerenciamento de números
* Autenticação / Autorização

## Conclusão

O nível de contexto é essencial porque:

* Define o **ponto de partida da arquitetura**
* Facilita a comunicação com **qualquer stakeholder**
* Permite identificar problemas **antes do código existir**

## Tabelas Resumo

### Sistemas e Atores

| Tipo            | Nome                               | Descrição                                          |
|-----------------|------------------------------------|----------------------------------------------------|
| Person          | Responsável pelo número telefônico | Profissional que utiliza o WhatsApp institucional  |
| Person          | Administrador                      | Responsável pela gestão dos números monitorados    |
| Software System | Sistema de Auditoria               | Sistema de vinculação e monitoramento de mensagens |
| External System | WhatsApp                           | Sistema de mensagens instantâneas                  |
| External System | SSO (Keycloak)                     | Sistema de autenticação e autorização              |

### Relacionamentos

| Origem                             | Destino              | Tipo de Interação | Descrição                                                 |
|------------------------------------|----------------------|-------------------|-----------------------------------------------------------|
| Responsável pelo número telefônico | WhatsApp             | Comunicação       | Trocar mensagens                                          |
| Responsável pelo número telefônico | Sistema de Auditoria | Vinculação        | Efetua leitura do QR Code                                 |
| Sistema de Auditoria               | WhatsApp             | Integração        | Consultar mensagens                                       |
| Administrador                      | Sistema de Auditoria | Gestão            | Gerenciar números telefônicos (criar, atualizar, remover) |
| Sistema de Auditoria               | SSO (Keycloak)       | Segurança         | Autenticação e autorização                                |

### Leitura Rápida

* **Atores principais:** Usuário operacional + Administrador
* **Sistema central:** Sistema de Auditoria
* **Dependências externas:** WhatsApp + SSO
* **Foco dos relacionamentos:** Comunicação, vinculação, gestão e segurança.

Essa tabela consolida a visão de contexto e serve como referência rápida para entendimento da arquitetura antes de
avançar para os próximos níveis do C4 Model.

