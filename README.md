# Architectural Modeling - C4 Model

> Domine a criação de arquiteturas de software claras, comunicáveis e evolutivas utilizando o C4 Model.

## Sobre o Repositório

Este repositório consolida os estudos, anotações e materiais produzidos a partir do curso:

- [Modelagem Arquitetural - C4 Model (Udemy)](https://udemy.com/course/modelagem-arquitetural-c4-model/)
- [Documentação Oficial do C4 Model](https://c4model.com/)

📄 Certificado de conclusão:  
![Certificado](./images/certificado.jpg)

## Objetivo

Apresentar, de forma estruturada e didática, os conceitos do **C4 Model**, com foco em:

- Comunicação arquitetural eficiente
- Uso de diferentes níveis de abstração
- Aplicação prática em um sistema real
- Boas práticas de modelagem

## O que é o C4 Model?

O **C4 Model**, criado por **Simon Brown**, é uma abordagem para modelar arquiteturas de software baseada em **quatro
níveis de abstração**.

### Conceito central

> Visualizar o sistema em diferentes níveis de detalhe — do mais amplo ao mais específico.

### Analogia

Semelhante ao Google Maps:

1. Contexto (visão global)
2. Containers (estrutura)
3. Componentes (detalhamento interno)
4. Código (implementação)

## Estrutura do Repositório

O conteúdo está organizado seguindo os níveis do C4 Model:

```text
.
├── images/
├── docs/
│ ├── 01-context.md
│ ├── 02-container.md
│ ├── 03-component.md
│ └── 04-code.md
└── README.md
```

## Níveis do C4 Model

### 1. Contexto (Context)

- Visão geral do sistema
- Atores e sistemas externos
- Relacionamentos

Pergunta respondida:
> Como o sistema se encaixa no mundo?

![Context 1](./images/002-context.png)

![Context 2](./images/003-context.png)

### 2. Container

- Estrutura interna do sistema
- Principais aplicações e bancos
- Tecnologias utilizadas

Pergunta respondida:
> Quais são as partes principais do sistema?

![Container](./images/005-container.png)

### 3. Componentes (Component)

- Detalhamento de um container específico
- Módulos, controllers e services
- Responsabilidades internas

Pergunta respondida:
> Como o sistema funciona internamente?

![Escopo do Container](./images/006-escopo-container.png)

![Componente](./images/007-component.png)

### 4. Código (Code)

- Representação da implementação
- Estrutura do código-fonte

Importante:
> Não é recomendado manter diagramas desse nível manualmente.

Alternativa recomendada:

- Link direto para o repositório de código

_Atualizar imagem_

Exemplo de estrutura de código (module, controller, service)

## Projeto Prático

O curso utiliza um sistema real como estudo de caso:

### Sistema de Auditoria de WhatsApp

#### Objetivo

Monitorar e auditar mensagens de múltiplos números de WhatsApp.

#### Componentes principais

- Integração com WhatsApp
- API Backend (NestJS)
- Frontend (Next.js)
- Banco de dados:
    - PostgreSQL
    - MongoDB

![Visão Inicial do Projeto](./images/001-visao-inicial-do-projeto.png)

## Fluxo Simplificado

1. Usuário escaneia QR Code
2. Sistema conecta ao WhatsApp
3. Workers capturam mensagens
4. Dados são armazenados
5. Admin consulta via dashboard

## Ferramentas Utilizadas

### Modelagem visual

- draw.io (diagrams.net)
- Lucidchart
- Miro
- Figma

### Modelagem como código

- Mermaid
- PlantUML
- Structurizr

## Comparação de Abordagens

| Tipo       | Vantagem      | Desvantagem          |
|------------|---------------|----------------------|
| Visual     | Simples       | Manual               |
| Código     | Automatizável | Curva de aprendizado |
| Enterprise | Completo      | Complexo             |

## Elementos do C4 Model

### Principais

- **Person** → Usuário
- **Software System** → Sistema
- **Container** → Aplicação ou banco
- **Component** → Parte interna

### Relacionamentos

- Representados por setas
- Indicam comunicação/interação

## Problema que o C4 resolve

Projetos sem modelagem enfrentam:

- Falhas de comunicação
- Retrabalho
- Ambiguidade

### Impacto direto

- Tempo
- Custo
- Qualidade

## Insight Importante

> O valor do C4 Model não está nos diagramas, mas na **clareza da comunicação**.

## Boas Práticas

- Modelar apenas o necessário
- Evitar excesso de detalhamento
- Atualizar conforme evolução
- Focar em comunicação

## Erros Comuns

- Diagramas complexos demais
- Linguagem técnica no nível de contexto
- Falta de padronização
- Ignorar stakeholders

## Quando usar cada nível

| Nível      | Quando usar                    |
|------------|--------------------------------|
| Contexto   | Sempre                         |
| Container  | Sempre                         |
| Componente | Apenas se necessário           |
| Código     | Evitar (usar link para código) |

## Conclusão

O C4 Model permite:

- Melhor comunicação entre times
- Redução de riscos
- Clareza arquitetural
- Evolução sustentável do sistema

## Referências

- https://c4model.com/
- https://udemy.com/course/modelagem-arquitetural-c4-model/

## Autor do Curso

- Jorge Santana
- Instagram: https://www.instagram.com/jorge.sant.ana/

## Licença

Este repositório tem fins educacionais.









