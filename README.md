# ATIVIDADE PRÁTICA INTEGRADA

## Computação em Nuvem: Arquitetura, Adoção, Custos e Governança

*Estudo de caso autossuficiente baseado nos conceitos das Aulas 03 e 04*

| **Público-alvo**     | Alunos em introdução à computação em nuvem / fundamentos AWS            |
|----------------------|-------------------------------------------------------------------------|
| **Formato**          | Individual ou grupos de 3 a 5 alunos                                    |
| **Duração sugerida** | 90 a 120 minutos + 10 minutos de apresentação                           |
| **Pré-requisito**    | Nenhum material externo é obrigatório; calculadora simples é suficiente |

> **Objetivo central**
>
> Você atuará como uma equipe de arquitetura de nuvem. A missão é avaliar uma empresa fictícia, propor uma solução AWS coerente e defender a decisão considerando tecnologia, adoção organizacional, custo, governança e suporte.

**IMPORTANTE** — Os preços usados neste exercício são fictícios e servem exclusivamente para cálculo didático. Não representam a tabela atual da AWS.

# 1. O que você deverá demonstrar

- Diferenciar computação em nuvem de infraestrutura tradicional e reconhecer os modelos IaaS, PaaS e SaaS.

- Selecionar um modelo de implantação adequado: nuvem, híbrido ou ambiente privado/local.

- Relacionar necessidades tradicionais de TI a serviços de nuvem, principalmente VPC, EC2, armazenamento, banco de dados, balanceamento e IAM.

- Aplicar os principais benefícios da nuvem: custo variável, economia de escala, elasticidade, agilidade, redução da operação de datacenter e alcance global.

- Usar as seis perspectivas do AWS Cloud Adoption Framework (CAF) para organizar ações de adoção.

- Analisar direcionadores de custo, TCO, cobrança conforme uso e compromissos/reservas.

- Propor governança de contas com AWS Organizations, unidades organizacionais, IAM e SCPs.

- Selecionar ferramentas de acompanhamento de custos e um nível de suporte compatível com criticidade.

# 2. Guia rápido de conceitos

Use esta seção como referência durante a atividade. Ela contém o conhecimento mínimo necessário para resolver o estudo de caso.

## 2.1 Modelos de serviço

| **Modelo** | **O que o provedor entrega**                              | **Responsabilidade típica do cliente**                               | **Exemplo de uso**                                   |
|------------|-----------------------------------------------------------|----------------------------------------------------------------------|------------------------------------------------------|
| IaaS       | Infraestrutura virtual: computação, rede e armazenamento. | Sistema operacional, aplicações, configurações e parte da segurança. | Máquinas virtuais para uma aplicação legada.         |
| PaaS       | Plataforma gerenciada para executar aplicações ou dados.  | Código, configuração da aplicação, dados e políticas de acesso.      | Banco de dados gerenciado ou plataforma de execução. |
| SaaS       | Aplicação pronta consumida como serviço.                  | Usuários, dados inseridos, configurações e governança de uso.        | E-mail corporativo ou sistema de colaboração.        |

## 2.2 Modelos de implantação

| **Modelo**    | **Descrição simplificada**                                      | **Quando pode fazer sentido**                                                                                        |
|---------------|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Nuvem         | A maior parte ou toda a carga é executada no provedor de nuvem. | Quando a organização quer elasticidade, rapidez e reduzir dependência de datacenter próprio.                         |
| Híbrido       | Integra recursos locais e recursos em nuvem.                    | Quando há sistemas que precisam permanecer locais, dependências legadas, requisitos de latência ou migração gradual. |
| Privado/local | Infraestrutura permanece sob controle direto da organização.    | Quando restrições específicas exigem operação local ou quando a migração ainda não é viável.                         |

## 2.3 Vocabulário AWS usado no exercício

| **Serviço/conceito**           | **Papel no exercício**                                                                |
|--------------------------------|---------------------------------------------------------------------------------------|
| Amazon VPC                     | Rede virtual isolada para organizar recursos de rede.                                 |
| Amazon EC2                     | Capacidade de computação por máquinas virtuais.                                       |
| Elastic Load Balancing         | Distribui tráfego entre múltiplas instâncias/serviços.                                |
| Amazon S3                      | Armazenamento de objetos; adequado para arquivos, backups e conteúdo estático.        |
| Amazon EBS / EFS               | Armazenamento em bloco / sistema de arquivos para cargas que precisam desses modelos. |
| Amazon RDS                     | Banco de dados relacional gerenciado.                                                 |
| IAM                            | Define identidades, funções e permissões dentro das contas.                           |
| AWS Organizations / OUs / SCPs | Organiza múltiplas contas e estabelece limites de permissão em nível organizacional.  |

## 2.4 Seis vantagens da computação em nuvem

| **Vantagem**                    | **Leitura prática**                                                                                   |
|---------------------------------|-------------------------------------------------------------------------------------------------------|
| CAPEX → despesa variável        | Evita comprar capacidade antecipadamente; paga-se de acordo com o uso e o modelo contratado.          |
| Economia de escala              | O provedor compartilha ganhos de escala entre muitos clientes.                                        |
| Menos adivinhação de capacidade | Recursos podem crescer ou diminuir conforme a demanda, reduzindo excesso ou falta de capacidade.      |
| Mais velocidade e agilidade     | Provisionamento pode ocorrer em minutos em vez de depender de aquisição e instalação física.          |
| Menos operação de datacenter    | A equipe pode concentrar esforço em aplicações e negócio, reduzindo tarefas de infraestrutura física. |
| Alcance global                  | É possível implantar recursos em diferentes regiões geográficas com mais rapidez.                     |

## 2.5 AWS Cloud Adoption Framework (CAF): seis perspectivas

| **Perspectiva** | **Pergunta que ela ajuda a responder**             | **Exemplos de ações**                                                 |
|-----------------|----------------------------------------------------|-----------------------------------------------------------------------|
| Negócios        | Que resultado empresarial esperamos obter?         | Caso de negócio, benefícios, riscos, finanças de TI.                  |
| Pessoas         | Quem precisa desenvolver novas capacidades?        | Treinamento, papéis, mudança organizacional e carreiras.              |
| Governança      | Como priorizar, controlar e medir a transformação? | Portfólio, projetos, métricas, políticas e gestão de riscos.          |
| Plataforma      | Como será a arquitetura técnica de destino?        | Rede, computação, armazenamento, banco de dados e aplicações.         |
| Segurança       | Como proteger identidades, infraestrutura e dados? | IAM, proteção de dados, controles detectivos e resposta a incidentes. |
| Operações       | Como o ambiente será operado de forma confiável?   | Monitoramento, mudanças, inventário, relatórios, continuidade e DR.   |

## 2.6 Economia, TCO e gestão de custos

- Três direcionadores básicos de custo: computação, armazenamento e transferência de dados.

- Pagamento conforme uso: custos variam com o consumo. Compromissos/reservas podem reduzir preço em troca de menor flexibilidade.

- TCO (custo total de propriedade) considera mais do que hardware: licenças, rede, espaço, energia, refrigeração, manutenção, administração, backup e mão de obra também importam.

- Ferramentas de gestão de custos: Billing/contas, Cost Explorer para análise histórica/tendências, Budgets para limites e alertas, e relatório de custo e uso para detalhamento.

## 2.7 IAM x SCP

> **Regra mental**
>
> IAM concede ou nega permissões para identidades em uma conta. SCP define o limite máximo de ações permitido às contas/OU de uma organização. Uma SCP não concede acesso por si só; ela restringe o que poderá ser autorizado por IAM.

# 3. Estudo de caso — NexaVarejo

A NexaVarejo é uma empresa de comércio eletrônico em crescimento. Hoje, seu ambiente principal está em um pequeno datacenter próprio. O negócio sofre picos de acesso em campanhas, quer lançar novos produtos com mais rapidez e pretende atender clientes de outros países.

A diretoria aprovou um estudo de migração para AWS, mas exige uma proposta que trate simultaneamente de arquitetura, custos, governança, segurança, operação e risco.

## 3.1 Situação atual

| **Item**        | **Situação atual**                                     | **Problema percebido**                                        |
|-----------------|--------------------------------------------------------|---------------------------------------------------------------|
| Aplicação web   | 4 servidores físicos para aplicação.                   | Capacidade ociosa fora de campanhas e saturação em picos.     |
| Banco de dados  | 1 servidor físico relacional.                          | Backup manual e janela de manutenção longa.                   |
| Arquivos/backup | 4 TB em storage local.                                 | Expansão exige compra de disco e há pouca automação.          |
| Rede            | Firewall e balanceador locais.                         | Mudanças dependem de equipe e janela de manutenção.           |
| Provisionamento | Compra e configuração manual.                          | Novos ambientes levam de 2 a 4 semanas.                       |
| Operação        | Equipe executa hardware, SO, backup e troubleshooting. | Pouco tempo para automação e melhoria contínua.               |
| Negócio         | Campanhas geram variação de 3× no tráfego.             | Risco de indisponibilidade ou compra excessiva de capacidade. |

## 3.2 Restrições e metas

- A loja deve continuar disponível durante a migração.

- Dados transacionais devem permanecer em banco relacional.

- Arquivos e backups podem ser migrados para armazenamento de objetos.

- Produção deve ser separada de desenvolvimento/homologação.

- A equipe quer evitar permissões administrativas amplas em contas de produção.

- A diretoria quer acompanhar gastos, receber alertas de orçamento e comparar TCO.

- A operação de e-commerce é considerada crítica para a receita.

## 3.3 Catálogo de opções que você pode usar

| **Necessidade**          | **Opções disponíveis neste exercício**                    |
|--------------------------|-----------------------------------------------------------|
| Rede isolada             | Amazon VPC                                                |
| Computação               | Amazon EC2                                                |
| Distribuição de tráfego  | Elastic Load Balancing                                    |
| Banco relacional         | Amazon RDS                                                |
| Arquivos e backups       | Amazon S3                                                 |
| Disco para instâncias    | Amazon EBS                                                |
| Identidades e permissões | IAM                                                       |
| Organização de contas    | AWS Organizations + OUs + SCPs                            |
| Custos                   | Billing, Cost Explorer, Budgets, relatório de custo e uso |

# 4. Atividade prática

> **Como entregar**
>
> Produza as respostas das Partes A a G e finalize com uma recomendação executiva. Desenhos podem ser feitos à mão ou em qualquer ferramenta. O foco da avaliação é a coerência da justificativa.

## Parte A — Diagnóstico de nuvem e modelos de serviço (15 pontos)

A1. Escolha o modelo de implantação.

A NexaVarejo deve adotar nuvem, híbrido ou manter ambiente local? Escolha uma opção como estratégia-alvo e justifique com pelo menos três argumentos.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

A2. Classifique IaaS, PaaS e SaaS.

| **Componente/necessidade**      | **Modelo mais próximo** | **Quem gerencia mais infraestrutura?** | **Justificativa** |
|---------------------------------|-------------------------|----------------------------------------|-------------------|
| EC2 para aplicação              |                         |                                        |                   |
| RDS para banco de dados         |                         |                                        |                   |
| Software de e-mail pronto       |                         |                                        |                   |
| Aplicação própria da NexaVarejo |                         |                                        |                   |

## Parte B — Arquitetura e benefícios da nuvem (15 pontos)

B1. Proponha a arquitetura.

Monte um fluxo mínimo usando os serviços do catálogo. A proposta deve mostrar: usuários, entrada de tráfego, VPC, balanceamento, computação, banco relacional e armazenamento de arquivos/backups.

**Modelo de representação textual (você pode substituir por um desenho):** Usuários → \[serviço\] → \[serviço\] → \[serviço\] → Banco; Arquivos/backup → \[serviço\].

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

B2. Conecte arquitetura a valor.

Selecione quatro das seis vantagens da nuvem e explique como cada uma reduz um problema específico do cenário.

| **Vantagem** | **Problema do cenário** | **Como a proposta ajuda** |
|--------------|-------------------------|---------------------------|
|              |                         |                           |
|              |                         |                           |
|              |                         |                           |
|              |                         |                           |

## Parte C — Plano de adoção com AWS CAF (15 pontos)

Para cada perspectiva, proponha uma ação concreta para os primeiros 90 dias. Evite respostas genéricas: associe a ação ao caso da NexaVarejo.

| **Perspectiva** | **Risco/pergunta principal** | **Ação de 90 dias** | **Evidência de conclusão** |
|-----------------|------------------------------|---------------------|----------------------------|
| Negócios        |                              |                     |                            |
| Pessoas         |                              |                     |                            |
| Governança      |                              |                     |                            |
| Plataforma      |                              |                     |                            |
| Segurança       |                              |                     |                            |
| Operações       |                              |                     |                            |

## Parte D — Economia de nuvem e TCO (20 pontos)

Considere os seguintes valores anuais do ambiente atual:

| **Componente do TCO on-premises**          | **Custo anual (R\$)** |
|--------------------------------------------|-----------------------|
| Hardware e manutenção                      | 120.000               |
| Licenças e suporte de software             | 48.000                |
| Espaço, energia e refrigeração             | 72.000                |
| Conectividade/rede                         | 36.000                |
| Operação e administração de infraestrutura | 96.000                |
| Backup e recuperação de desastre           | 42.000                |

Para a alternativa em nuvem, use os custos mensais fictícios abaixo:

| **Componente**            | **Sob demanda (R\$/mês)** | **Com compromisso/reserva (R\$/mês)** |
|---------------------------|---------------------------|---------------------------------------|
| Computação                | 11.200                    | 7.600                                 |
| Armazenamento             | 1.800                     | 1.800                                 |
| Banco de dados gerenciado | 4.200                     | 4.200                                 |
| Transferência de dados    | 2.100                     | 2.100                                 |
| Monitoramento e segurança | 900                       | 900                                   |
| Suporte                   | 2.000                     | 2.000                                 |
| Custo único de migração   | 45.000 (uma vez)          | 45.000 (uma vez)                      |

D1. Calcule o TCO atual anual.

Some todos os itens do ambiente on-premises.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

D2. Calcule o custo anual recorrente da nuvem em dois cenários.

- Cenário 1: computação sob demanda.

- Cenário 2: computação com compromisso/reserva.

Não inclua o custo único de migração neste cálculo recorrente.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

D3. Calcule o custo do primeiro ano com migração e o TCO de três anos.

Use o cenário com compromisso/reserva. Considere que os demais valores permanecem constantes.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

D4. Tome uma decisão.

A migração é justificável apenas pelo custo? Cite também dois benefícios não financeiros (ou menos diretamente mensuráveis) que devem entrar no caso de negócio.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Parte E — Governança de contas, IAM e SCP (15 pontos)

E1. Estruture a organização.

A empresa terá três contas iniciais: Produção, Desenvolvimento/Homologação e Segurança/Logs. Proponha uma estrutura de OUs e indique onde colocaria cada conta.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

E2. Defina três guardrails.

Escreva três regras que fariam sentido como limites organizacionais/SCPs. Exemplos de intenção: impedir desativação de trilhas de auditoria, limitar regiões não aprovadas ou bloquear criação de recursos fora do padrão. Não é necessário escrever JSON.

| **Guardrail proposto** | **OU/conta alvo** | **Risco reduzido** |
|------------------------|-------------------|--------------------|
|                        |                   |                    |
|                        |                   |                    |
|                        |                   |                    |

E3. Explique IAM x SCP em uma frase.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Parte F — Gestão de custos e suporte (10 pontos)

F1. Escolha a ferramenta mais adequada para cada necessidade.

| **Necessidade**                                                  | **Ferramenta escolhida** | **Por quê?** |
|------------------------------------------------------------------|--------------------------|--------------|
| Analisar tendência de gasto dos últimos meses.                   |                          |              |
| Receber alerta antes de ultrapassar um orçamento.                |                          |              |
| Obter detalhamento granular de uso e custo para análise externa. |                          |              |
| Visualizar cobranças e faturas da conta.                         |                          |              |
| Comparar o custo de diferentes serviços ao longo do tempo.       |                          |              |

F2. Selecione o suporte.

Para fins deste exercício, considere quatro níveis didáticos: Básico (autoatendimento), Developer (desenvolvimento), Business (carga de produção) e Enterprise (carga crítica ao negócio com necessidade de orientação mais próxima). Qual você recomendaria para a NexaVarejo no momento da entrada em produção? Justifique com criticidade, impacto e capacidade interna.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Parte G — Recomendação executiva (10 pontos)

Escreva uma recomendação de 8 a 12 linhas para a diretoria. Ela deve responder: (1) por que migrar; (2) arquitetura-alvo; (3) principais ganhos; (4) custo/TCO; (5) como controlar risco, acesso e gastos.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

# 5. Checklist de entrega do aluno

☐ Modelo de implantação escolhido e justificado.

☐ Classificação IaaS/PaaS/SaaS preenchida.

☐ Arquitetura mínima proposta.

☐ Quatro benefícios da nuvem associados ao caso.

☐ Plano AWS CAF com seis perspectivas.

☐ Cálculos de TCO e comparação dos dois modelos de custo.

☐ Estrutura de OUs e três guardrails/SCPs.

☐ Escolha de ferramentas de gestão de custos.

☐ Recomendação de suporte.

☐ Recomendação executiva final.

# 6. Extensão opcional — modo hands-on

Se houver acesso à internet ou a uma conta de laboratório, o professor pode transformar o exercício em uma validação prática. Esta etapa não é necessária para resolver a atividade principal.

1.  Recrie uma estimativa equivalente na AWS Pricing Calculator e compare o total com a tabela didática.

2.  Pesquise quais serviços geram custos de computação, armazenamento e transferência de dados na arquitetura proposta.

3.  Em um ambiente de laboratório autorizado, navegue pelo Cost Explorer/Budgets sem criar recursos pagos.

4.  Desenhe a estrutura de AWS Organizations e escreva uma SCP em pseudocódigo ou JSON, sem aplicá-la em produção.

5.  Registre diferenças entre a estimativa didática e a ferramenta real e explique por que preços de nuvem variam por região, configuração e consumo.

> **Cuidados**
>
> Não crie recursos em uma conta real sem autorização e orçamento. Em laboratórios, remova recursos ao final. Nunca use credenciais pessoais em materiais compartilhados.

# 7. Gabarito orientativo e notas para o professor

> **Uso do gabarito**
>
> As respostas abaixo são referências. Arquiteturas e decisões diferentes podem receber pontuação integral quando forem tecnicamente coerentes e bem justificadas.

## 7.1 Parte A — Respostas esperadas

A1. Estratégia-alvo recomendada: nuvem, com migração gradual para reduzir risco. Uma resposta híbrida como etapa de transição também é válida.

- A elasticidade ajuda a lidar com picos de campanhas.

- O provisionamento mais rápido atende à necessidade de agilidade.

- A redução da dependência de hardware local diminui esforço de datacenter.

- O alcance geográfico pode apoiar expansão internacional.

A2. Classificação de referência:

| **Item**          | **Classificação**                    | **Justificativa curta**                                                      |
|-------------------|--------------------------------------|------------------------------------------------------------------------------|
| EC2               | IaaS                                 | Cliente ainda controla SO e aplicação.                                       |
| RDS               | PaaS/serviço gerenciado              | Provedor assume parte relevante da operação da plataforma de banco.          |
| E-mail pronto     | SaaS                                 | Aplicação completa é consumida pelo usuário.                                 |
| Aplicação própria | Não é, sozinha, um modelo de serviço | O modelo depende de onde/como ela é hospedada; em EC2 tende a consumir IaaS. |

## 7.2 Parte B — Arquitetura de referência

**Fluxo mínimo:** Usuários → Elastic Load Balancing → instâncias EC2 dentro de uma VPC → Amazon RDS. Arquivos e backups → Amazon S3. Discos das instâncias → EBS quando necessário. IAM controla acessos administrativos.

Uma resposta mais madura pode adicionar múltiplas zonas de disponibilidade, sub-redes públicas/privadas, monitoramento e automação. Esses itens não são obrigatórios se ainda não foram estudados.

Associações típicas de benefício:

| **Benefício**           | **Aplicação ao caso**                                                                        |
|-------------------------|----------------------------------------------------------------------------------------------|
| Despesa variável        | Evita comprar capacidade para o pico anual inteiro.                                          |
| Economia de escala      | A empresa consome infraestrutura compartilhada do provedor em vez de construir tudo sozinha. |
| Elasticidade/capacidade | Ajuda a responder ao tráfego 3× maior em campanhas.                                          |
| Agilidade               | Novos ambientes podem ser provisionados mais rapidamente.                                    |
| Menos datacenter        | Reduz esforço com energia, refrigeração e manutenção física.                                 |
| Alcance global          | Facilita expansão para outros mercados.                                                      |

## 7.3 Parte C — AWS CAF

| **Perspectiva** | **Ação possível em 90 dias**                                         | **Evidência**                               |
|-----------------|----------------------------------------------------------------------|---------------------------------------------|
| Negócios        | Aprovar caso de negócio e metas de disponibilidade/custo.            | Business case e KPIs aprovados.             |
| Pessoas         | Treinar equipe em fundamentos AWS, operação e segurança.             | Plano de capacitação e responsáveis.        |
| Governança      | Definir política de contas, tags, orçamento e aprovação de mudanças. | Políticas e matriz de responsabilidade.     |
| Plataforma      | Desenhar arquitetura-alvo e executar piloto não produtivo.           | Diagrama e ambiente piloto.                 |
| Segurança       | Definir IAM, segregação de contas, logging e proteção de dados.      | Matriz de acesso e requisitos de segurança. |
| Operações       | Criar monitoramento, alertas, runbooks, backup e plano de DR.        | Painéis, alarmes e runbook testado.         |

## 7.4 Parte D — Cálculos

D1. TCO anual on-premises:

**R\$ 120.000 + 48.000 + 72.000 + 36.000 + 96.000 + 42.000 = R\$ 414.000/ano**

D2. Nuvem — custo recorrente:

| **Cenário**         | **Mensal recorrente** | **Anual recorrente** | **Economia vs. on-premises** |
|---------------------|-----------------------|----------------------|------------------------------|
| Sob demanda         | R\$ 22.200            | R\$ 266.400          | R\$ 147.600/ano (≈35,7%)     |
| Compromisso/reserva | R\$ 18.600            | R\$ 223.200          | R\$ 190.800/ano (≈46,1%)     |

D3. Primeiro ano e três anos no cenário com compromisso/reserva:

- Primeiro ano = R\$ 223.200 + R\$ 45.000 de migração = R\$ 268.200.

- TCO on-premises em 3 anos = R\$ 414.000 × 3 = R\$ 1.242.000.

- TCO nuvem em 3 anos = R\$ 223.200 × 3 + R\$ 45.000 = R\$ 714.600.

- Economia acumulada em 3 anos = R\$ 527.400, aproximadamente 42,5%.

D4. A migração não deve ser defendida apenas pelo preço. Benefícios relevantes incluem menor tempo de provisionamento, elasticidade, maior foco da equipe no negócio, melhoria de continuidade/backup e possibilidade de expansão geográfica.

## 7.5 Parte E — Governança

Estrutura de referência:

- OU Produção → conta Produção.

- OU Não Produção → conta Desenvolvimento/Homologação.

- OU Segurança → conta Segurança/Logs.

Guardrails possíveis:

- Impedir alteração/desativação indevida de mecanismos centrais de auditoria.

- Restringir regiões não aprovadas pela organização.

- Bloquear ações administrativas de alto risco fora das contas/roles autorizadas.

IAM x SCP: IAM define o que uma identidade está autorizada a fazer dentro da conta; SCP estabelece o limite organizacional máximo dentro do qual essas permissões podem existir.

## 7.6 Parte F — Ferramentas e suporte

| **Necessidade**              | **Resposta de referência**       |
|------------------------------|----------------------------------|
| Tendência histórica          | Cost Explorer.                   |
| Alertas de orçamento         | AWS Budgets.                     |
| Detalhamento granular        | Relatório de custo e uso.        |
| Cobranças/faturas            | Billing / painel de faturamento. |
| Comparação ao longo do tempo | Cost Explorer.                   |

Suporte: Business é uma resposta defensável para uma carga de produção quando a equipe possui autonomia operacional suficiente; Enterprise também é defensável se a turma tratar o e-commerce como missão crítica, com alto impacto financeiro e necessidade de acompanhamento mais próximo. A justificativa vale mais do que a escolha isolada.

## 7.7 Exemplo de recomendação executiva

> Recomendamos migrar a NexaVarejo para uma arquitetura em nuvem AWS, iniciando por um piloto e avançando de forma controlada para produção. A aplicação pode operar em EC2 dentro de uma VPC, com balanceamento de carga, banco relacional em RDS e arquivos/backups em S3. O desenho responde aos picos de demanda, reduz o tempo de provisionamento e diminui a dependência do datacenter próprio. No cenário didático com compromisso de computação, o custo recorrente anual cai de R\$ 414 mil para R\$ 223,2 mil, e o TCO de três anos, incluindo migração, fica em R\$ 714,6 mil. A adoção deve ser acompanhada pelas seis perspectivas do CAF. Produção, não produção e segurança devem ficar segregadas em contas/OUs, com IAM de menor privilégio e SCPs como guardrails. Cost Explorer, Budgets e relatórios de custo e uso devem sustentar o controle financeiro. A entrada em produção deve utilizar um plano de suporte compatível com a criticidade do e-commerce.

# 8. Rubrica de avaliação — 100 pontos

| **Critério**             | **Excelente**                                                        | **Parcial**                                             | **Pontos** |
|--------------------------|----------------------------------------------------------------------|---------------------------------------------------------|------------|
| Modelos e diagnóstico    | Escolha coerente e conceitos IaaS/PaaS/SaaS corretos.                | Conceitos parcialmente corretos ou pouca justificativa. | 15         |
| Arquitetura e benefícios | Fluxo completo e benefícios ligados aos problemas do caso.           | Arquitetura incompleta ou benefícios genéricos.         | 15         |
| AWS CAF                  | Seis perspectivas com ações concretas e evidências.                  | Ações genéricas ou perspectivas ausentes.               | 15         |
| Economia e TCO           | Cálculos corretos e análise financeira + benefícios não financeiros. | Erros de cálculo ou análise limitada.                   | 20         |
| Governança               | OUs coerentes, guardrails e distinção IAM/SCP corretos.              | Estrutura ou conceitos incompletos.                     | 15         |
| Custos e suporte         | Ferramentas bem escolhidas e suporte justificado.                    | Escolhas pouco justificadas.                            | 10         |
| Recomendação executiva   | Síntese clara, integrada e orientada a decisão.                      | Resumo fragmentado ou sem conclusão.                    | 10         |
| TOTAL                    |                                                                      |                                                         | 100        |

# 9. Sugestão de condução em sala

| **Etapa**              | **Tempo** | **Dinâmica**                               |
|------------------------|-----------|--------------------------------------------|
| Leitura do caso        | 10 min    | Turma identifica problemas e restrições.   |
| Partes A–C             | 30 min    | Decisões de arquitetura e plano de adoção. |
| Parte D                | 20 min    | Cálculos de TCO e discussão de trade-offs. |
| Partes E–F             | 20 min    | Governança, custos e suporte.              |
| Parte G + apresentação | 20–30 min | Síntese executiva e defesa da solução.     |

> **Pergunta de fechamento**
>
> Qual decisão do grupo teria maior impacto negativo se estivesse errada: arquitetura, custo, governança, segurança ou suporte? Explique como você reduziria esse risco antes da migração.
