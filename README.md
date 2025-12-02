
# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento
Comparação entre revisão de código manual (peer review) e revisão automatizada por SonarQube na redução da densidade de defeitos em projetos Java.

### 1.2 ID / código
EXP-SE-001

### 1.3 Versão do documento e histórico de revisão
- **Versão atual:** v4.0  
- **Histórico:**  
  - v1.0 — criação inicial do documento, contendo escopo e fundamentos teóricos.
  - v2.0 — expansão com objetivos específicos, GQM, stakeholders e riscos.
  - v3.0 — modelo conceitual e hipóteses; variáveis, fatores, tratamentos e objetos de estudo; desenho experimental
  - v3.1 — ajustes de precisão nas métricas e operacionalização de critérios.
  - v4.0 — População, sujeitos e amostragem; Instrumentação e protocolo operacional; Plano de análise de dados (pré-execução) + Avaliação de validade (ameaças e mitigação)
  - v5.0 — Ética, privacidade e conformidade Recursos, infraestrutura e orçamento Cronograma, marcos e riscos operacionais
  - v5.1 — Atualização dos diagramas para formato Mermaid.js
  - v5.2 — Remoção de redundâncias em determinadas seções, correção no tópico 8.7 e condensação do tópico 13


### 1.4 Datas (criação, última atualização)
- **Data de criação:** 23/11/2025  
- **Última atualização:** 02/12/2025

### 1.5 Autores (nome, área, contato)
- **Autor:** [Gabriel Ferreira Amaral] — Engenharia de Software — gabriel.afa@outlook.com

### 1.6 Responsável principal (PI / dono do experimento)
[Gabriel Ferreira Amaral] — responsável pelo direcionamento científico do estudo.

### 1.7 Projeto / produto / iniciativa relacionada
Projeto acadêmico de desenvolvimento de software em Java, vinculado à disciplina de Engenharia de Software e ao Experimento de Trabalho de Conclusão de Curso (TCC).  
Foco: análise comparativa de práticas de garantia de qualidade no ciclo de desenvolvimento.

---

## 2. Contexto e problema

### 2.1 Descrição do problema / oportunidade
Equipes de desenvolvimento utilizam revisões de código manuais como mecanismo principal de detecção de defeitos antes da integração. Contudo, ferramentas de análise estática, como SonarQube, têm sido adotadas para automatizar parte desse processo, oferecendo relatórios imediatos sobre problemas estruturais, duplicações e vulnerabilidades.  
Ainda não há clareza, no contexto estudado, sobre qual método resulta em menor densidade de defeitos pós-entrega. Assim, surge a oportunidade de comparar empiricamente esses dois métodos de revisão com base em métricas objetivas de qualidade.

### 2.2 Contexto organizacional e técnico
O experimento será conduzido em um ambiente acadêmico, com equipes de estudantes desenvolvendo sistemas Java utilizando GitHub, CI/CD básico e práticas ágeis.  
Tecnologias relevantes incluem:
- Java 17+, Spring Boot  
- Git e GitHub (branches, PRs, issues)  
- SonarQube (regras padrão + qualidade mínima exigida)  
- GitHub Actions para integração contínua  

O processo padrão envolve desenvolvimento em feature branches, abertura de pull requests, revisão manual e posterior integração.

### 2.3 Trabalhos e evidências prévias (internos e externos)
Evidências existentes incluem:
- Estudos empíricos que avaliam a eficácia da revisão de código manual na redução de defeitos.  
- Pesquisas sobre o uso de ferramentas como SonarQube para identificação automática de smells e vulnerabilidades.  
- Estudos comparativos mostrando que cada abordagem captura tipos diferentes de problemas (manuais captam lógica; ferramentas captam padrões estruturais).  
- Em contextos internos, observou-se aumento de retrabalho quando revisões manuais são superficiais e ausência de ferramentas automatizadas leva à negligência de problemas estruturais.

### 2.4 Referencial teórico e empírico essencial
O experimento fundamenta-se nos seguintes conceitos-chave:
- **Code Review Manual:** técnica tradicional que envolve inspeção humana do código, amplamente adotada em processos ágeis e DevOps.  
- **Análise Estática de Código:** uso de ferramentas que identificam problemas automaticamente antes da execução, como complexidade, duplicação, vulnerabilidades e violações de boas práticas.  
- **Qualidade de Software:** conceitos como densidade de defeitos, complexidade ciclomática, cobertura de testes e maintainability index orientam o estudo.  
- **Engenharia de Software Empírica:** uso de experimentos controlados para avaliar práticas de desenvolvimento e fundamentar decisões baseadas em evidências.  
- **Estudos anteriores** mostram que combinar revisão manual com análises automatizadas pode melhorar a qualidade, mas o impacto relativo e isolado de cada abordagem ainda é pouco quantificado em ambientes pequenos/médios.

## 3. Objetivos e Questões (Goal / Question / Metric)

### 3.1 Objetivo Geral (Goal Template)

**Analisar** a efetividade de duas estratégias de revisão de código (manual e automatizada via SonarQube) **com o propósito de** identificar qual método resulta em menor densidade de defeitos pós-entrega e maior qualidade estrutural, **sob a perspectiva de** gerentes de qualidade, desenvolvedores e arquitetos de software, **no contexto de** projetos acadêmicos de desenvolvimento Java em equipes pequenas/médias (4-6 pessoas).

---

### 3.2 Objetivos Específicos

| ID | Objetivo Específico | Descrição |
|---|---|---|
| O1 | Comparar a densidade de defeitos | Medir e comparar a quantidade de defeitos detectados pós-entrega em sprints com revisão manual versus automatizada |
| O2 | Avaliar a cobertura de detecção | Identificar quais categorias de problemas (segurança, complexidade, duplicação, etc.) cada método detecta melhor |
| O3 | Quantificar o impacto no tempo e esforço | Medir tempo gasto em revisão, número de comentários gerados e ciclos de retrabalho em cada abordagem |
| O4 | Analisar a satisfação e percepção | Avaliar a aceitação, confiança e conforto dos desenvolvedores com cada método de revisão |

---

### 3.3 Tabela GQM (Goal / Question / Metric)

| Objetivo | Pergunta (Q) | Métricas Associadas | ID Métricas |
|---|---|---|---|
| O1 | Q1.1: Qual é a densidade de defeitos detectados após entrega entre os dois métodos? | M1 (Densidade de Defeitos), M2 (Taxa de Defeitos Críticos) | M1, M2 |
| O1 | Q1.2: Quantos defeitos são encontrados em produção/homologação para cada abordagem? | M3 (Defeitos Pós-Entrega), M4 (Severity Distribution) | M3, M4 |
| O1 | Q1.3: Qual é a correlação entre problemas identificados em revisão e defeitos reais em produção? | M1 (Densidade de Defeitos), M5 (True Positive Rate) | M1, M5 |
| O2 | Q2.1: Quantos problemas de segurança cada método consegue identificar? | M6 (Vulnerabilidades Detectadas), M7 (Security Issues) | M6, M7 |
| O2 | Q2.2: Qual é o desempenho de cada método na identificação de complexidade excessiva? | M8 (Complexidade Ciclomática Média), M2 (Taxa de Defeitos Críticos) | M8, M2 |
| O2 | Q2.3: Como cada abordagem se comporta na detecção de duplicação de código? | M9 (Duplicação de Código %), M5 (True Positive Rate) | M9, M5 |
| O3 | Q3.1: Quanto tempo é gasto em cada tipo de revisão? | M10 (Tempo Médio de Revisão), M11 (Ciclos de Retrabalho) | M10, M11 |
| O3 | Q3.2: Qual é o volume de comentários/feedback gerado em cada método? | M12 (Número de Comentários), M10 (Tempo Médio de Revisão) | M12, M10 |
| O3 | Q3.3: Quantos ciclos de retrabalho são necessários em cada abordagem? | M11 (Ciclos de Retrabalho), M3 (Defeitos Pós-Entrega) | M11, M3 |
| O4 | Q4.1: Como os desenvolvedores avaliam a utilidade de cada método? | M13 (Satisfação Percebida), M14 (Confiança no Método) | M13, M14 |
| O4 | Q4.2: Qual método é considerado menos intrusivo/mais aceitável? | M14 (Confiança no Método), M15 (Taxa de Adoção) | M14, M15 |
| O4 | Q4.3: Qual é o aprendizado percebido pelos desenvolvedores em cada estratégia? | M13 (Satisfação Percebida), M16 (Feedback Qualitativo) | M13, M16 |

---

### 3.4 Catálogo de Métricas

| ID | Nome da Métrica | Descrição | Unidade | Fonte de Dados |
|---|---|---|---|---|
| M1 | Densidade de Defeitos | Número de defeitos encontrados pós-entrega por 1.000 linhas de código | defeitos/KLOC | Relatórios de defeitos, análise de issues |
| M2 | Taxa de Defeitos Críticos | Percentual de defeitos com severidade crítica ou alta em relação ao total | % | Sistema de gerenciamento de defeitos |
| M3 | Defeitos Pós-Entrega | Número absoluto de defeitos identificados após entrega/merge para main | quantidade | GitHub Issues, sistema de rastreamento de bugs |
| M4 | Severity Distribution | Distribuição de defeitos por nível de severidade (crítico, alto, médio, baixo) | % por severidade | Análise de defeitos registrados |
| M5 | True Positive Rate | Percentual de problemas flagged que correspondem a defeitos reais | % | Validação manual/testes de aceitação |
| M6 | Vulnerabilidades Detectadas | Número total de vulnerabilidades de segurança identificadas | quantidade | Relatórios SonarQube + comentários de revisão manual |
| M7 | Security Issues | Número específico de issues ligados a segurança (SQL injection, XSS, etc.) | quantidade | SonarQube + análise manual |
| M8 | Complexidade Ciclomática Média | Média da complexidade de funções/métodos no código revisado | índice | SonarQube metrics |
| M9 | Duplicação de Código % | Percentual de linhas duplicadas em relação ao total do projeto | % | SonarQube duplicate detection |
| M10 | Tempo Médio de Revisão | Tempo gasto por um revisor/ferramenta para revisar um PR | minutos | Timestamps de PR, logs de análise SonarQube |
| M11 | Ciclos de Retrabalho | Número de vezes que um PR requer correções antes da aprovação | quantidade | Histórico de commits/iterações em PR |
| M12 | Número de Comentários | Quantidade total de comentários (feedback) deixados em revisão | quantidade | GitHub PR comments |
| M13 | Satisfação Percebida | Avaliação subjetiva dos desenvolvedores quanto à utilidade do método (escala 1-5) | escala Likert | Pesquisa/questionário pós-experimento |
| M14 | Confiança no Método | Grau de confiança que os desenvolvedores têm na capacidade do método identificar problemas | escala Likert (1-5) | Entrevista/questionário estruturado |
| M15 | Taxa de Adoção | Percentual de PRs que seguem o protocolo de revisão proposto | % | Auditoria de PRs no repositório |
| M16 | Feedback Qualitativo | Observações e comentários coletados via entrevistas semi-estruturadas | texto/temas | Transcrições de entrevistas |

---

## 4. Escopo e Contexto do Experimento

### 4.1 Escopo Funcional / de Processo

#### Incluído no escopo:
- Desenvolvimento de features/user stories em Java utilizando Spring Boot
- Abertura de pull requests (PRs) no GitHub
- Aplicação da estratégia de revisão manual (peer review tradicional) em metade dos PRs
- Aplicação da estratégia de revisão automatizada (SonarQube) em outra metade dos PRs
- Registro de métricas de qualidade pré e pós-integração
- Testes em ambiente de staging/homologação para detecção de defeitos reais
- Coleta de feedback qualitativo via entrevistas/questionários com desenvolvedores
- Análise comparativa dos resultados entre os dois métodos

#### Excluído do escopo:
- Revisão de infraestrutura e DevOps
- Análise de performance (tempo de execução, throughput)
- Testes de aceitação por usuários finais
- Modificações estruturais no SonarQube ou criação de regras customizadas (utilizar configuração padrão)
- Análise de impacto em projetos de larga escala (>100 KLOC)
- Outras ferramentas de análise estática (Findbugs, SpotBugs, Checkstyle) — foco exclusivo em SonarQube
- Revisão de código de testes unitários (escopo limitado a lógica de negócio)

---

### 4.2 Contexto do Estudo

| Aspecto | Descrição |
|---|---|
| **Tipo de Organização** | Acadêmica (instituição de ensino superior) |
| **Tamanho** | Pequeno (4-6 estudantes por equipe) |
| **Tipo de Projeto** | Desenvolvimento de aplicação web (back-end Java + frontend básico) |
| **Criticidade** | Média (projeto acadêmico, sem críticos em produção real) |
| **Perfil de Experiência dos Participantes** | Misto: estudantes do 4º/5º semestre com experiência variada em Java (6-18 meses) |
| **Ambiente de Execução** | Repositório GitHub; CI/CD com GitHub Actions; SonarQube em cloud gratuito ou self-hosted; staging em servidor de testes |
| **Duração Prevista** | 3-4 sprints (6-8 semanas) |
| **Linguagem de Programação** | Java 17+ |
| **Framework Principal** | Spring Boot 3.x |

---

### 4.3 Premissas

| ID | Premissa | Justificativa |
|---|---|---|
| P1 | Todos os participantes possuem experiência básica em Git, GitHub e Java | Necessário para aplicação consistente de ambos os métodos |
| P2 | SonarQube permanecerá disponível e estável durante todo o experimento | Falhas de ferramenta invalidariam dados da abordagem automatizada |
| P3 | Os PRs são do tamanho e complexidade comparáveis entre os dois grupos | Necessário para comparação justa entre métodos |
| P4 | Os revisores manuais aplicarão critérios consistentes e fundamentados | Reduz viés e padroniza a qualidade da revisão manual |
| P5 | Os testes em homologação identificarão adequadamente defeitos reais | Essencial para validar se os métodos capturam problemas significativos |
| P6 | A equipe manterá registro consistente de tempo, comentários e iterações | Dados essenciais para M10, M11, M12 |

---

### 4.4 Restrições

| Tipo | Descrição | Impacto |
|---|---|---|
| **Tempo** | Disponibilidade de sprints acadêmicos limitada a 6-8 semanas | Pode reduzir volume de PRs analisados; limita profundidade de análise |
| **Orçamento** | Projeto sem financiamento; uso de ferramentas gratuitas | SonarQube limitado a cloud gratuito ou versão community; sem suporte premium |
| **Ferramentas** | GitHub Actions com quotas gratuitas; SonarQube comunidade | Sem acesso a features premium; possíveis limitações de relatórios |
| **Acesso** | Ambiente de staging compartilhado; possível contenção de recursos | Testes em homologação podem sofrer atrasos; variabilidade nos resultados |
| **Amostra** | Pequena equipe (4-6 pessoas) | Baixa generalização; possível viés por conhecimento interpessoal |
| **Regras Organizacionais** | Calendário acadêmico rígido; feriados e períodos de prova | Interrupções involuntárias no fluxo de desenvolvimento |

---

### 4.5 Limitações Previstas (Validez Externa)

- **Contexto acadêmico vs. industrial:** resultados podem não ser generalizáveis para equipes profissionais com projetos críticos
- **Tamanho reduzido da amostra:** 4-6 desenvolvedores; conclusões limitadas em relação a equipes maiores (10+)
- **Projeto pequeno/médio:** aplicação a sistemas com >200 KLOC pode apresentar dinâmica diferente
- **Configuração padrão do SonarQube:** não reflete customizações específicas de organizações reais
- **Possível Hawthorne effect:** desenvolvedores sabem que estão sendo avaliados; comportamento pode não refletir prática rotineira
- **Falta de randomização verdadeira:** possível viés na atribuição de PRs aos grupos (manual vs. automatizado)
- **Curva de aprendizado:** equipe pode melhorar ao longo do tempo, confundindo efeito do método com maturação

---

## 5. Stakeholders e Impacto Esperado

### 5.1 Stakeholders Principais

| Stakeholder | Descrição | Interesse |
|---|---|---|
| **Desenvolvedores (Participantes)** | Estudantes que desenvolvem e revisam código no experimento | Compreender qual método agrega mais valor; reduzir retrabalho |
| **Professor/Orientador** | Responsável acadêmico pelo experimento; orienta pesquisa | Validar hipóteses; gerar conhecimento científico sobre práticas de qualidade |
| **Gerentes de Qualidade / QA** | Profissionais interessados em políticas de revisão | Embasar decisão sobre adoção de ferramentas automatizadas |
| **Arquitetos de Software** | Responsáveis por definir padrões de qualidade e processos | Fundamentar padrões de revisão; definir políticas de integração |
| **Comunidade Acadêmica** | Outros estudantes, pesquisadores em Engenharia de Software | Contribuir com evidências para tomadas de decisão em contextos similares |

---

### 5.2 Interesses e Expectativas dos Stakeholders

| Stakeholder | Expectativa | Benefício Esperado |
|---|---|---|
| **Desenvolvedores** | Aprender quais técnicas de revisão são mais eficazes | Melhorar qualidade do código; reduzir tempo em revisão improdutiva |
| **Professor/Orientador** | Gerar dados empíricos sólidos para publicação ou conclusão de TCC | Fundamentar recomendações com evidência; contribuir ao conhecimento em ES |
| **Gerentes de Qualidade** | Conhecer o custo-benefício de ferramentas automatizadas vs. manual | Justificar investimento em ferramentas; otimizar processo de QA |
| **Arquitetos** | Definir políticas de revisão baseadas em evidências | Padronizar prática; aumentar eficiência e qualidade de produtos |
| **Comunidade Acadêmica** | Ter estudo de referência em revisão de código | Usar como base para pesquisas futuras; informar curriculum |

---

### 5.3 Impactos Potenciais no Processo / Produto

#### Durante o experimento:
- Possível aumento inicial de tempo em code review devido ao protocolo estruturado
- Carga adicional na equipe por coleta de dados e pesquisas
- Possível desconforto com mudanças de processo habitual
- Contenção de recursos em ambiente de staging durante testes

#### Após o experimento:
- Recomendações fundamentadas sobre estratégia de revisão a adotar
- Melhor compreensão dos pontos fortes de cada abordagem
- Potencial adoção de método híbrido (manual + automatizado)
- Aumento de confiança na qualidade do código entregue
- Base para políticas de qualidade em futuras disciplinas/projetos

---

## 6. Riscos de Alto Nível, Premissas e Critérios de Sucesso

### 6.1 Riscos de Alto Nível (Negócio, Técnicos, etc.)

| ID | Risco | Categoria | Probabilidade | Impacto | Mitigation | Contingência |
|---|---|---|---|---|---|---|
| R1 | Indisponibilidade ou falha do SonarQube durante experimento | Técnico | Média | Alto | Usar cloud gratuito com SLA; ter backup local self-hosted | Pausar coleta de dados; ampliar janela de tempo |
| R2 | Baixa adesão da equipe ao protocolo estruturado | Negócio/Pessoas | Alta | Alto | Comunicar claramente benefícios; treinar participantes | Reforçar incentivos; ajustar protocolo se necessário |
| R3 | Falta de defeitos suficientes em produção para validar diferenças | Técnico | Média | Alto | Usar testes rigorosos em staging; considerar defeitos simulados | Ampliar critério de "defeito"; aumentir período experimental |
| R4 | Viés do Hawthorne (comportamento alterado por observação) | Pesquisa | Alta | Médio | Minimizar comunicação sobre métricas durante experimento | Coletar dados retrospectivamente; validar com histórico |
| R5 | Atrito de participantes (desistências, indisponibilidade) | Negócio | Média | Médio | Recrutar com antecedência; ter suplentes preparados | Reduzir escopo; alongar cronograma |
| R6 | Inconsistência na aplicação de critérios de revisão manual | Pesquisa | Alta | Médio | Desenvolver checklist; treinamento de revisores; auditar amostra | Padronizar critérios retrospectivamente; usar média de 2+ revisores |
| R7 | Problemas técnicos em CI/CD ou repositório | Técnico | Média | Médio | Usar infraestrutura confiável (GitHub); backup de dados | Restaurar de backup; repetir análise |
| R8 | Amostra insuficiente de PRs por falta de atividade de desenvolvimento | Negócio | Média | Alto | Estimular fluxo de features; usar sprints curtas | Estender calendário; aceitar N menor com análise mais cautelosa |

---

### 6.2 Critérios de Sucesso Globais (Go / No-Go)

| Critério | Condição | Decisão | Responsável |
|---|---|---|---|
| **C1** | Mínimo 20 PRs por grupo (40 no total) coletados com dados completos | **Go:** ≥40 PRs; **No-Go:** <30 PRs | Pesquisador |
| **C2** | Pelo menos 10+ defeitos pós-entrega identificados (distribuídos entre grupos) para permitir análise estatística significativa | **Go:** ≥10 defeitos totais; **No-Go:** <5 defeitos | QA / Testes |
| **C3** | Taxa de aderência ao protocolo ≥80% (pelo menos 80% dos PRs seguem o método designado) | **Go:** ≥80%; **No-Go:** <60% | Pesquisador |
| **C4** | Dados de todas as 16 métricas coletados com <10% de valores faltantes | **Go:** <10% faltantes; **No-Go:** >20% faltantes | Pesquisador |
| **C5** | Teste t / Mann-Whitney pode ser executado com validade estatística (pressupostos testados) | **Go:** Pressupostos atendidos; **No-Go:** Violações graves | Analista |
| **C6** | Pelos menos 80% dos participantes completam questionário/entrevista qualitativa | **Go:** ≥80%; **No-Go:** <50% | Pesquisador |

**Decisão Final:** Experimento considerado bem-sucedido se **mínimo 5 de 6 critérios** forem atingidos (Go).

---

### 6.3 Critérios de Parada Antecipada (Pré-Execução)

| Situação | Ação | Responsável |
|---|---|---|
| **Reprovação ética** — Comitê de ética não aprova protocolo experimental | **Cancelar** experimento até aprovação ser obtida | Professor / Coordenador |
| **Recursos críticos indisponíveis** — SonarQube ou GitHub indisponíveis por >5 dias consecutivos antes de início | **Adiar** para data posterior; buscar alternativas | Pesquisador + TI |
| **Baixa adesão inicial** — <50% da equipe confirmada na fase de recrutamento | **Revisar escopo** e redimensionar; ou **cancelar** se não viável | Professor / Pesquisador |
| **Mudança significativa de contexto** — Calendário acadêmico alterado; feriados não previstos prolongam gap >6 meses | **Renegociar** cronograma; se impacto muito grande, **cancelar** | Coordenador Acadêmico |
| **Impossibilidade técnica demonstrada** — Stack Java não compatível com SonarQube; ambiente não suporta CI/CD | **Adiar** até resolver; considerar **mudança de tecnologia** | Pesquisador + TI |
| **Conflito de interesses ou viés não mitigável** — Revisor manual é também author do código; resultados confundidos | **Redesenhar amostra** ou **parar experimento** | Professor |

---

## 7. Modelo Conceitual e Hipóteses

### 7.1 Modelo Conceitual do Experimento

#### Diagrama de Influências

```mermaid
flowchart LR

    %% --------------------------
    %% NÓS PRINCIPAIS
    %% --------------------------

    A["Tipo de Revisão de Código
(Variável Independente)"]

    B1["Revisão Manual
(Peer Review)

Detecta:
• Lógica complexa
• Contexto de negócio
• Casos extremos
• Design patterns"]

    B2["SonarQube (Automática)
(Análise Estática)

Detecta:
• Padrões estruturais
• Vulnerabilidades
• Complexidade
• Duplicação
• Code smells"]

    C["Qualidade do Código
(Métrica Primária)

• Densidade de Defeitos (M1)
• Taxa de Críticos (M2)
• Defeitos Pós-Entrega (M3)"]

    D["Resultado Final
(Efeito Observado)

Redução de defeitos
em produção?"]

    CTX["Variáveis Moderadoras / Contexto

• Experiência dos devs (M14)
• Complexidade do código (M8)
• Tamanho do PR
• Criticidade da funcionalidade"]


    %% --------------------------
    %% FLUXO HORIZONTAL
    %% --------------------------

    A --> B1
    A --> B2

    B1 --> C
    B2 --> C

    C --> D

    %% Contexto abaixo
    A --- CTX
    B1 --- CTX
    B2 --- CTX
    C --- CTX


    %% --------------------------
    %% ESTILOS DE CORES
    %% --------------------------

    classDef indep fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#0d47a1,rx:10,ry:10;
    classDef review fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#1b5e20,rx:10,ry:10;
    classDef metric fill:#fff3e0,stroke:#ef6c00,stroke-width:2px,color:#e65100,rx:10,ry:10;
    classDef result fill:#f3e5f5,stroke:#8e24aa,stroke-width:2px,color:#6a1b9a,rx:10,ry:10;
    classDef ctx fill:#eeeeee,stroke:#424242,stroke-width:1.8px,color:#212121,rx:10,ry:10;

    %% Aplicação dos estilos
    class A indep;
    class B1,B2 review;
    class C metric;
    class D result;
    class CTX ctx;
```


#### Mecanismo de Ação Esperado

**Hipótese Conceitual:**

1. **Revisão Manual** funciona melhor para detectar problemas de lógica, contexto de negócio e casos extremos, pois um revisor experiente compreende a intenção e pode identificar fluxos anômalos.

2. **Análise Estática (SonarQube)** funciona melhor para identificar padrões estruturais repetitivos, vulnerabilidades conhecidas, complexidade excessiva e duplicação, pois executa regras consistentes em todo o código.

3. **Esperado (H₁ direcional):** Combinando ambos os métodos, é possível capturar categorias diferentes de problemas, resultando em menor densidade de defeitos pós-entrega que qualquer método isolado.

4. **Incerteza Principal:** Qual método (manual ou automatizado) reduz *mais* defeitos críticos que chegam à produção? Ou não há diferença significativa?

---

### 7.2 Hipóteses Formais (H₀, H₁)

#### Hipótese Principal (Bilateral)

**H₀ (Hipótese Nula):**

Não há diferença estatisticamente significativa na densidade de defeitos pós-entrega entre código revisado manualmente e código revisado automaticamente via SonarQube em projetos Java pequenos/médios.

Formalmente: *μ(Defeitos_Manual) = μ(Defeitos_SonarQube)*

**H₁ (Hipótese Alternativa - Bilateral):**

Existe diferença estatisticamente significativa na densidade de defeitos pós-entrega entre os dois métodos de revisão.

Formalmente: *μ(Defeitos_Manual) ≠ μ(Defeitos_SonarQube)*

---

#### Hipóteses Secundárias (Exploratórias)

| ID | Questão | H₀ | H₁ (Direção Esperada) |
|---|---|---|---|
| H2 | Qual método detecta mais vulnerabilidades de segurança? | Nenhuma diferença em M6/M7 | SonarQube > Manual (automatizado detecta padrões) |
| H3 | Qual método identifica melhor problemas de complexidade? | Nenhuma diferença em M8 | SonarQube > Manual (métrica objetiva) |
| H4 | Qual abordagem gasta menos tempo em revisão? | Tempo Manual = Tempo SonarQube (M10) | SonarQube < Manual (automatizado é mais rápido) |
| H5 | Desenvolvedores confiam mais em qual método? | Confiança Manual = Confiança SonarQube (M14) | Manual ≥ SonarQube (experiência humana) |
| H6 | Qual método resulta em menos ciclos de retrabalho? | Ciclos Manual = Ciclos SonarQube (M11) | SonarQube < Manual (menos ambiguidade) |

---

### 7.3 Nível de Significância e Considerações de Poder

#### Nível de Significância (α)

**α = 0.05** (confiança de 95%)

**Justificativa:** Nível padrão em pesquisa de Engenharia de Software; oferece balanço aceitável entre risco de erro Tipo I (rejeitar H₀ quando verdadeira) e Tipo II (não rejeitar H₀ quando falsa).

---

#### Considerações de Poder Estatístico

| Parâmetro | Valor | Justificativa |
|---|---|---|
| **Poder (1 - β)** | 0.80 (80%) | Padrão em pesquisa aplicada; β = 0.20 (risco aceitável de Erro Tipo II) |
| **Tamanho de Efeito (d de Cohen)** | ≥ 0.5 | Efeito médio; diferenças práticas entre métodos devem ser detectáveis |
| **Tamanho de Amostra Planejado (n)** | ~20-30 PRs por grupo (40-60 total) | Baseado em cálculo a posteriori para poder 0.80, α=0.05, d=0.5 |
| **Teste Estatístico** | Teste t de Student (two-tailed) ou Mann-Whitney U (não-paramétrico) | t apropriado para N > 15; Mann-Whitney se pressupostos de normalidade violados |

---

#### Análise de Poder Prognóstica

**Cálculo Estimado (usando G*Power ou fórmula de Cohen):**

Para teste t independente com:
- α = 0.05 (two-tailed)
- Poder = 0.80
- d = 0.5 (efeito médio)

**N necessário ≈ 64 por grupo** (128 total para máxima precisão)

**Realidade do projeto:**
- N planejado = 20-30 PRs por grupo (~40-60 total)
- Poder esperado ≈ 0.60-0.70 (reduzido, mas aceitável em pesquisa aplicada)
- **Implicação:** Estudo tem poder moderado; diferenças pequenas (d < 0.3) podem não ser detectadas; intervalos de confiança serão mais largos

**Mitigação:**
- Priorizar detecção de efeitos de tamanho médio ou maior (d ≥ 0.5)
- Relatar intervalos de confiança (IC 95%) além de p-values
- Usar análise de tamanho de efeito (Cohen's d, η²) para complementar testes clássicos
- Justificar conclusões conservadoras quando poder é limitado

---

#### Pressupostos Estatísticos a Testar

Antes de aplicar teste t, serão validados:

1. **Normalidade:** Teste de Shapiro-Wilk ou gráfico Q-Q para cada grupo
2. **Homogeneidade de Variâncias:** Teste de Levene
3. **Independência:** Garantida pelo design (amostras aleatórias, grupos distintos)

Se pressupostos forem violados:
- Usar **teste Mann-Whitney U** (não-paramétrico, mais robusto)
- Aplicar **transformações logarítmicas** aos dados se apropriado
- Reportar tanto teste paramétrico quanto não-paramétrico


## 8. Variáveis, fatores, tratamentos e objetos de estudo

### 8.1 Objetos de estudo

Os objetos de estudo neste experimento são **Pull Requests (PRs)** contendo implementações de features ou correções de bugs em código Java. Cada PR representa uma unidade experimental que será submetida a um dos dois métodos de revisão.

**Características dos objetos:**

- **Tipo:** Pull Requests no GitHub contendo código-fonte Java
- **Escopo funcional:** Implementações de user stories, features de backend (REST APIs, lógica de negócio, persistência de dados)
- **Tamanho esperado:** PRs com 50-500 linhas de código modificadas (LOC)
- **Complexidade:** Variada — desde CRUDs simples até lógica de negócio com regras condicionais complexas
- **Framework:** Spring Boot 3.x com Java 17+
- **Repositório:** Código versionado no GitHub com histórico completo de commits, comentários e iterações

**Critérios de inclusão:**
- PRs que modificam **lógica de negócio, REST APIs ou funcionalidades** (não apenas refatorações de estilo, formatting ou comentários)
- PRs com pelo menos 50 LOC modificadas em **código-fonte** (excluso testes automaticamente gerados)
- PRs abertos após o início oficial do experimento
- PRs que passam por todo o fluxo de revisão (abertura → revisão → aprovação/rejeição → merge/retrabalho)
- PRs com descrição clara da funcionalidade no título ou descrição

**Critérios de exclusão:**
- PRs puramente de documentação (README, comentários)
- PRs que modificam apenas configurações (YAML, properties)
- PRs abandonados ou fechados sem merge
- PRs com <50 LOC (muito triviais para análise significativa)

---

### 8.2 Sujeitos / participantes (visão geral)

**Perfil dos participantes:**

| Aspecto | Descrição |
|---|---|
| **Função** | Estudantes de graduação em Ciência da Computação/Engenharia de Software atuando como desenvolvedores e revisores |
| **Quantidade** | 4-6 participantes (equipe única) |
| **Experiência com Java** | Mista: 6-18 meses de experiência prática; pelo menos 1 disciplina de Programação Orientada a Objetos concluída |
| **Experiência com Git/GitHub** | Básica a intermediária; todos devem saber criar branches, PRs e realizar code review |
| **Experiência com Spring Boot** | Pelo menos 1 projeto acadêmico prévio |
| **Conhecimento de SonarQube** | Não obrigatório (será fornecido treinamento) |

**Papéis no experimento:**

1. **Autores de PRs:** Desenvolvedores que implementam features e abrem PRs
2. **Revisores manuais:** Participantes designados para realizar peer review tradicional
3. **Operadores do SonarQube:** Participantes que interpretam relatórios automatizados (pode ser o próprio autor)
4. **Testadores:** Responsáveis por validar código em staging/homologação (podem ser os mesmos desenvolvedores em rodízio)

**Recrutamento:**
- Convite direto a estudantes matriculados na disciplina de Engenharia de Software
- Consentimento informado com explicação clara dos objetivos e procedimentos
- Participação voluntária; possibilidade de desistência sem penalização acadêmica

---

### 8.3 Variáveis independentes (fatores) e seus níveis

| Fator | Descrição | Níveis (Tratamentos) | Tipo |
|---|---|---|---|
| **F1: Método de Revisão** | Estratégia utilizada para revisar o código antes da integração | **Nível 1:** Revisão Manual (Peer Review) <br> **Nível 2:** Revisão Automatizada (SonarQube) | Categórico (2 níveis) |

**Detalhamento do fator F1:**

**Nível 1 — Revisão Manual (Peer Review):**
- Revisor humano designado analisa o código linha a linha
- Utiliza checklist padronizado (lógica, legibilidade, boas práticas, segurança, casos extremos)
- Deixa comentários diretamente no GitHub PR
- Aprova ou solicita mudanças com justificativa
- **Não utiliza** ferramentas automatizadas durante a revisão

**Nível 2 — Revisão Automatizada (SonarQube):**
- Análise estática executada automaticamente via CI/CD (GitHub Actions)
- Relatório SonarQube gerado com issues categorizadas (bugs, vulnerabilities, code smells, coverage, duplicação)
- Autor do PR corrige problemas identificados pela ferramenta
- Aprovação automática se quality gate for atingido (configuração padrão: sem bugs críticos, cobertura mínima)
- **Não há** revisão humana adicional neste grupo

---

### 8.4 Tratamentos (condições experimentais)

| Tratamento | Descrição Completa | Protocolo |
|---|---|---|
| **T1: Controle (Revisão Manual)** | PR passa por revisão humana tradicional sem uso de ferramentas automatizadas | 1. Desenvolvedor abre PR no GitHub <br> 2. Revisor humano designado recebe notificação <br> 3. Revisor analisa código usando checklist padronizado <br> 4. Revisor deixa comentários e aprova ou solicita mudanças <br> 5. Autor corrige e atualiza PR (se necessário) <br> 6. Após aprovação, PR é mergeado <br> 7. Código é testado em staging/homologação |
| **T2: Tratamento (Revisão Automatizada SonarQube)** | PR passa por análise estática automática; aprovação baseada em quality gate da ferramenta | 1. Desenvolvedor abre PR no GitHub <br> 2. GitHub Actions dispara análise SonarQube automaticamente <br> 3. Relatório é gerado com issues identificadas <br> 4. Autor analisa relatório e corrige problemas críticos <br> 5. PR é atualizado; nova análise é executada <br> 6. Quality gate aprovado → PR é mergeado <br> 7. Código é testado em staging/homologação |

**Diferenciação entre tratamentos:**

| Aspecto | T1 (Manual) | T2 (Automatizado) |
|---|---|---|
| **Revisor** | Humano | Ferramenta (SonarQube) |
| **Critérios de aprovação** | Subjetivos + checklist | Objetivos (quality gate) |
| **Tempo de resposta** | Variável (depende de disponibilidade) | Imediato (CI/CD) |
| **Tipo de problemas detectados** | Lógica, contexto, design | Padrões, estrutura, métricas |
| **Feedback** | Comentários textuais no GitHub | Relatório estruturado com categorias |

---

### 8.5 Variáveis dependentes (respostas)

| ID | Nome da Variável | Descrição | Unidade de Medida | Forma de Coleta | Métrica Associada |
|---|---|---|---|---|---|
| **VD1** | **Densidade de Defeitos Pós-Entrega** | Número de defeitos encontrados em staging/homologação após o merge do PR, normalizados por 1.000 linhas de código | defeitos/KLOC | Rastreamento de issues no GitHub + análise de logs de testes | M1 |
| **VD2** | **Taxa de Defeitos Críticos** | Percentual de defeitos com severidade crítica ou alta em relação ao total de defeitos encontrados | % | Classificação manual de severidade nos issues reportados | M2 |
| **VD3** | **Defeitos Pós-Entrega (Absoluto)** | Número absoluto de defeitos identificados após merge (sem normalização) | quantidade | Contagem de issues criados após merge do PR | M3 |
| **VD4** | **Vulnerabilidades Detectadas** | Número total de vulnerabilidades de segurança identificadas durante a revisão (manual ou automatizada) | quantidade | Comentários de revisão manual + relatório SonarQube (Security Hotspots) | M6 |
| **VD5** | **Complexidade Ciclomática Média** | Média da complexidade ciclomática das funções/métodos no código do PR | índice | Relatório SonarQube (Complexity metrics) | M8 |
| **VD6** | **Duplicação de Código** | Percentual de linhas duplicadas identificadas no PR | % | Relatório SonarQube (Duplication metrics) | M9 |
| **VD7** | **Tempo de Revisão** | Tempo total gasto desde a abertura do PR até a aprovação final | minutos | Diferença entre timestamps (PR opened → approved) no GitHub API | M10 |
| **VD8** | **Ciclos de Retrabalho** | Número de iterações (pushes após comentários) necessárias antes da aprovação | quantidade | Contagem de commits após primeira revisão | M11 |
| **VD9** | **Número de Comentários** | Quantidade total de comentários deixados durante a revisão (manual) ou issues flagadas (automatizada) | quantidade | GitHub PR comments API + SonarQube issues count | M12 |
| **VD10** | **Satisfação Percebida** | Avaliação subjetiva dos desenvolvedores sobre a utilidade do método de revisão | escala Likert (1-5) | Questionário pós-experimento | M13 |
| **VD11** | **Confiança no Método** | Grau de confiança dos desenvolvedores na capacidade do método de identificar problemas | escala Likert (1-5) | Questionário pós-experimento | M14 |
| **VD12** | **True Positive Rate** | Percentual de problemas identificados na revisão que correspondem a defeitos reais validados em testes | % | Validação cruzada: issues revisão vs. defeitos em staging | M5 |
| **VD13** | **Severity Distribution** | Distribuição de defeitos pós-entrega por nível de severidade (crítico, alto, médio, baixo) | % por severidade | Classificação manual dos issues reportados | M4 |
| **VD14** | **Feedback Qualitativo** | Temas, insights e observações coletadas em entrevistas/questionários abertos | texto/temas codificadas | Transcrições de entrevistas semi-estruturadas | M16 |

#### Variáveis Dependentes Primárias (Principal Analysis)

As seguintes variáveis serão o **foco principal** da análise estatística para teste de hipóteses:

1. **VD1 (Densidade de Defeitos Pós-Entrega)** — métrica primária para H₀/H₁
2. **VD2 (Taxa de Defeitos Críticos)** — complementa análise de qualidade
3. **VD7 (Tempo de Revisão)** — eficiência do processo

#### Variáveis Dependentes Secundárias (Exploratory Analysis)

Variáveis complementares para análise exploratória e discussão qualitativa:

- VD4, VD5, VD6 — caracterização de problemas detectados
- VD8, VD9 — dinâmica do processo de revisão
- VD10, VD11 — percepção e aceitação dos métodos
- VD12 — validação da qualidade da detecção
- VD13, VD14 — análise detalhada de severidade e feedback qualitativo

---

### 8.6 Variáveis de controle / bloqueio

Variáveis que serão **mantidas constantes** ou usadas para **formação de blocos** a fim de reduzir variabilidade não relacionada ao tratamento:

| ID | Nome da Variável | Descrição | Estratégia de Controle | Justificativa |
|---|---|---|---|---|
| **VC1** | **Tamanho do PR (LOC)** | Número de linhas de código modificadas no PR | **Bloqueio:** PRs serão agrupados em 3 blocos por tamanho (pequeno: 50-150 LOC; médio: 151-300 LOC; grande: 301-500 LOC). Alocação balanceada entre tratamentos dentro de cada bloco. | Tamanho influencia tempo de revisão e probabilidade de defeitos |
| **VC2** | **Complexidade da Feature** | Nível de complexidade da funcionalidade implementada (simples/média/complexa) | **Bloqueio:** Features classificadas em 3 níveis; distribuição equilibrada entre T1 e T2 | Complexidade afeta densidade de defeitos independentemente do método de revisão |
| **VC3** | **Experiência do Desenvolvedor** | Tempo de experiência com Java (em meses) | **Controle:** Rodízio de autores entre tratamentos; cada desenvolvedor contribui com PRs em ambos os grupos | Desenvolvedores mais experientes tendem a produzir menos defeitos |
| **VC4** | **Configuração do SonarQube** | Regras e quality gate utilizados | **Controle:** Configuração padrão do SonarQube mantida constante durante todo o experimento | Variações nas regras distorceriam comparação |
| **VC5** | **Checklist de Revisão Manual** | Critérios utilizados na revisão humana | **Controle:** Checklist padronizado fornecido a todos os revisores; treinamento inicial | Padronização garante comparabilidade entre revisores |
| **VC6** | **Ambiente de Testes** | Infraestrutura de staging/homologação | **Controle:** Mesmo ambiente usado para todos os PRs; configuração fixa | Diferenças de ambiente podem mascarar ou criar defeitos artificialmente |
| **VC7** | **Sprint / Período Temporal** | Momento em que o PR é desenvolvido | **Bloqueio:** Análise estratificada por sprint; efeitos de aprendizagem controlados | Equipe pode melhorar ao longo do tempo (maturação) |
| **VC8** | **Tipo de Funcionalidade** | Categoria da feature (CRUD, API REST, regra de negócio, etc.) | **Bloqueio:** Tipos funcionais balanceados entre tratamentos | Diferentes tipos têm perfis de risco distintos |

---

### 8.7 Possíveis variáveis de confusão conhecidas

Fatores que podem distorcer os resultados e que serão **monitorados** e/ou **mitigados**:

| ID | Variável de Confusão | Descrição do Risco | Impacto Potencial | Estratégia de Mitigação | Monitoramento |
|---|---|---|---|---|---|
| **CF1** | **Efeito Hawthorne** | Participantes alteram comportamento por saberem que estão sendo observados | Desenvolvedores podem caprichar mais na qualidade do código, reduzindo defeitos artificialmente | • Minimizar comunicação sobre métricas durante experimento <br> • Não revelar qual PR está em qual grupo <br> • Coletar dados de forma discreta | Análise retrospectiva de padrões comportamentais |
| **CF2** | **Aprendizado / Maturação** | Equipe melhora habilidades ao longo do tempo | Defeitos podem diminuir naturalmente com o tempo, independente do tratamento | • Controlar por sprint (VC7) <br> • Alternar tratamentos ao longo do tempo <br> • Análise de tendência temporal | Gráficos de densidade de defeitos por semana |
| **CF3** | **Viés de Seleção de Tarefas** | Tarefas mais complexas podem ser alocadas desproporcionalmente a um grupo | Grupo com tarefas mais difíceis apresenta mais defeitos por natureza da tarefa | • Randomização da alocação de PRs <br> • Bloqueio por complexidade (VC2) <br> • Registro da complexidade percebida | Verificação de balanceamento pós-alocação |
| **CF4** | **Diferenças entre Revisores** | Revisores manuais têm estilos e níveis de rigor diferentes | Variabilidade na qualidade da revisão manual (T1) | • Treinamento padronizado <br> • Checklist obrigatório (VC5) <br> • Rodízio de revisores entre PRs <br> • Auditoria de amostra de revisões | Análise de concordância inter-revisor |
| **CF5** | **Qualidade dos Testes em Staging** | Testes de validação podem variar em rigor | Defeitos podem não ser detectados por testes fracos, não por falha do método de revisão | • Padronizar suíte de testes <br> • Cobertura mínima exigida (80%) <br> • Casos de teste pré-definidos para cada feature | Análise de cobertura de testes por PR |
| **CF6** | **Falhas Técnicas Temporárias** | SonarQube pode ficar indisponível; CI/CD pode falhar | PRs do grupo T2 podem não receber análise adequada | • Monitoramento de uptime do SonarQube <br> • Política de re-análise em caso de falha <br> • Backup de dados de análise | Logs de falhas técnicas com timestamps |


---

## 9. Desenho experimental

### 9.1 Tipo de desenho (completamente randomizado, blocos, fatorial, etc.)

**Desenho escolhido:** **Desenho em Blocos Randomizados (Randomized Block Design)**

**Justificativa:**

O desenho em blocos é apropriado para este experimento porque:

1. **Heterogeneidade conhecida:** Os PRs variam naturalmente em tamanho, complexidade e tipo de funcionalidade. Essa variabilidade pode obscurecer o efeito real do tratamento.

2. **Controle de variáveis de confusão:** Ao agrupar PRs em blocos homogêneos (por tamanho, complexidade, tipo), reduzimos a variância intra-bloco e aumentamos a precisão na detecção de diferenças entre tratamentos.

3. **Tamanho de amostra limitado:** Com ~40-60 PRs esperados, é essencial maximizar o poder estatístico controlando fontes de variação conhecidas.

4. **Comparabilidade:** Garante que ambos os tratamentos (T1 e T2) sejam aplicados a PRs similares, evitando viés de seleção.

**Estrutura do desenho:**
```mermaid
flowchart TD

    A["População de PRs
(Todos os PRs do projeto)"]
    A --> B["Estratificação em Blocos"]

    B --> C1["Bloco 1
(Pequeno)
50–150 LOC"]

    B --> C2["Bloco 2
(Médio)
151–300 LOC"]

    B --> C3["Bloco 3
(Grande)
301–500 LOC"]

    C1 --> D1["Randomização
dentro do bloco"]
    C2 --> D2["Randomização
dentro do bloco"]
    C3 --> D3["Randomização
dentro do bloco"]

    D1 --> E1["T1 (n)
T2 (n)"]
    D2 --> E2["T1 (n)
T2 (n)"]
    D3 --> E3["T1 (n)
T2 (n)"]

    %% Legenda
    subgraph Legenda
        L1["T1 = Revisão Manual"]
        L2["T2 = Revisão Automatizada (SonarQube)"]
        L3["n = número aproximadamente igual de PRs por célula"]
    end

    %% ===========================
    %% ESTILOS DE CORES
    %% ===========================
    classDef main fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#0d47a1,rx:10,ry:10;
    classDef block fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#1b5e20,rx:10,ry:10;
    classDef random fill:#fff3e0,stroke:#ef6c00,stroke-width:2px,color:#e65100,rx:10,ry:10;
    classDef result fill:#f3e5f5,stroke:#8e24aa,stroke-width:2px,color:#6a1b9a,rx:10,ry:10;
    classDef legend fill:#eeeeee,stroke:#424242,stroke-width:1.5px,color:#212121,rx:6,ry:6;

    %% Atribuir estilos
    class A,B main;
    class C1,C2,C3 block;
    class D1,D2,D3 random;
    class E1,E2,E3 result;
    class L1,L2,L3 legend;
```


**Critérios de bloqueio:**

| Bloco | Critério Principal | Critério Secundário | Justificativa |
|---|---|---|---|
| **Bloco 1 (Pequeno)** | 50-150 LOC | Complexidade: Simples a Média | PRs menores com escopo reduzido |
| **Bloco 2 (Médio)** | 151-300 LOC | Complexidade: Média | PRs de tamanho moderado, escopo padrão |
| **Bloco 3 (Grande)** | 301-500 LOC | Complexidade: Média a Alta | PRs maiores com múltiplas componentes ou lógica complexa |

**Número esperado de unidades por bloco:**

- **Meta:** ~6-10 PRs por célula (tratamento × bloco)
- **Total esperado:** 36-60 PRs distribuídos em 6 células (3 blocos × 2 tratamentos)

**Modelo estatístico:**

O modelo ANOVA para blocos randomizados será:
```
Y_ij = μ + τ_i + β_j + ε_ij

Onde:
Y_ij = resposta observada (ex: densidade de defeitos)
μ = média geral
τ_i = efeito do tratamento i (i = 1,2)
β_j = efeito do bloco j (j = 1,2,3)
ε_ij = erro aleatório
```

---

### 9.2 Randomização e alocação

**Processo de randomização:**

A randomização será realizada **dentro de cada bloco** para garantir balanceamento e reduzir viés.

**Etapas práticas:**

1. **Classificação inicial de PRs:**
   - No momento da abertura do PR, o pesquisador/facilitador registra:
     - Número de LOC modificadas (via GitHub API)
     - Complexidade estimada da feature (via discussão com autor ou análise do título/descrição)
     - Tipo de funcionalidade (CRUD, API, lógica de negócio, etc.)

2. **Alocação ao bloco:**
   - PR é alocado ao bloco correspondente baseado no tamanho (LOC)
   - Bloco 1: 50-150 LOC
   - Bloco 2: 151-300 LOC
   - Bloco 3: 301-500 LOC

3. **Randomização do tratamento:**
   - Dentro de cada bloco, PRs são randomizados para T1 ou T2 usando gerador de números aleatórios
   - **Ferramenta:** Script Python com `random.choice(['T1', 'T2'])` ou planilha com função `=ALEATÓRIO()`
   - **Restrição de balanceamento:** Se diferença entre T1 e T2 dentro do bloco exceder 2 PRs, próximo PR é alocado ao grupo menor para forçar equilíbrio

4. **Registro da alocação:**
   - Tabela mestre mantida em planilha segura:
```
     PR_ID | LOC | Complexidade | Bloco | Tratamento | Data_Abertura
```
   - Apenas pesquisador tem acesso à alocação completa (cegamento parcial dos participantes)

**Exemplo de código Python para randomização:**
```python
import random

def alocar_tratamento(bloco, historico_bloco):
    """
    Aloca tratamento garantindo balanceamento dentro do bloco
    """
    contagem_t1 = historico_bloco.count('T1')
    contagem_t2 = historico_bloco.count('T2')
    
    # Se diferença > 2, força alocação ao grupo menor
    if contagem_t1 - contagem_t2 >= 2:
        return 'T2'
    elif contagem_t2 - contagem_t1 >= 2:
        return 'T1'
    else:
        return random.choice(['T1', 'T2'])

# Exemplo de uso
bloco1_historico = []
for pr in range(10):
    tratamento = alocar_tratamento('Bloco1', bloco1_historico)
    bloco1_historico.append(tratamento)
    print(f"PR {pr+1}: {tratamento}")
```

**O que será randomizado:**

| Elemento | Randomizado? | Justificativa |
|---|---|---|
| **Alocação de PR ao tratamento** | ✅ Sim | Evita viés de seleção; garante comparabilidade |
| **Ordem de revisão dentro de sprint** | ❌ Não | Não relevante; PRs revisados conforme abertura |
| **Escolha do revisor manual** | ✅ Sim (rodízio) | Evita viés de revisor específico |
| **Ordem dos testes em staging** | ❌ Não | Todos testados após merge |

**O que NÃO será randomizado:**

- **Features/tarefas:** Alocação de features aos desenvolvedores segue planejamento normal da sprint (não interferimos no processo de desenvolvimento)
- **Momento de abertura do PR:** Desenvolvedores abrem PRs naturalmente ao completarem features
- **Blocos:** PRs são alocados deterministicamente aos blocos baseado em LOC

---

### 9.3 Balanceamento e contrabalanço

**Balanceamento:**

Estratégias para garantir que os grupos (T1 e T2) sejam comparáveis:

1. **Balanceamento de tamanho de amostra:**
   - **Meta:** N_T1 ≈ N_T2 dentro de cada bloco (diferença máxima de 1-2 PRs)
   - **Mecanismo:** Randomização com restrição (seção 9.2)
   - **Verificação:** Contagem periódica (semanal) de PRs por tratamento/bloco

2. **Balanceamento de complexidade:**
   - PRs complexos distribuídos uniformemente entre T1 e T2
   - Classificação de complexidade (simples/média/alta) realizada por 2 avaliadores independentes
   - Se discordância, consenso via discussão

3. **Balanceamento de autores:**
   - Cada desenvolvedor contribui com PRs em **ambos** os tratamentos
   - Rodízio forçado: se desenvolvedor X já tem 3 PRs em T1, próximo PR dele é alocado a T2
   - **Tabela de rastreamento:**
 Desenvolvedor | PRs_T1 | PRs_T2 | Diferença
 Dev_A         |   3    |   2    |    +1
 Dev_B         |   2    |   3    |    -1

4. **Balanceamento temporal:**
   - Ambos os tratamentos aplicados em todas as sprints (não concentrar T1 no início e T2 no final)
   - Alternância entre sprints se possível

**Contrabalanço (para controlar efeitos de ordem/aprendizagem):**

Embora o desenho não seja crossover (cada PR recebe apenas 1 tratamento), aplicamos contrabalanço para outros fatores:

1. **Ordem de exposição dos desenvolvedores aos tratamentos:**
   - **Problema:** Desenvolvedores podem aprender com SonarQube e depois escrever código melhor na revisão manual
   - **Solução:** Alternar ordem de exposição:
     - Metade dos desenvolvedores inicia com T1 (manual), depois T2 (automatizado)
     - Outra metade inicia com T2, depois T1
   
2. **Sequência de revisores manuais:**
   - **Problema:** Mesmo revisor pode ficar mais rigoroso ou relaxado ao longo do tempo
   - **Solução:** Rodízio sistemático de revisores em T1; cada revisor atua em PRs de diferentes blocos e sprints

3. **Ordem de testes em staging:**
   - **Problema:** Testadores podem ficar mais atentos após encontrar defeitos
   - **Solução:** Aleatorizar ordem de teste dos PRs em staging (não testar todos T1 primeiro, depois T2)

**Verificação de balanceamento:**

Análise pré-experimento (após coleta mas antes da análise estatística):

| Fator | Teste de Balanceamento | Critério de Aceitação |
|---|---|---|
| **Tamanho (LOC)** | Teste t: média LOC_T1 vs. LOC_T2 | p > 0.05 (não significativo) |
| **Complexidade** | Teste χ²: distribuição de complexidade | p > 0.05 |
| **Autores** | Teste χ²: distribuição de PRs por desenvolvedor | p > 0.05 |
| **Sprints** | Teste χ²: distribuição temporal | p > 0.05 |

Se balanceamento falhar (p < 0.05), usar **covariáveis** na análise estatística (ANCOVA) para ajustar diferenças.

---
### 9.4 Número de grupos e sessões

**Número de grupos experimentais:**

- **2 grupos de tratamento:**
  - Grupo 1 (T1): Revisão Manual
  - Grupo 2 (T2): Revisão Automatizada (SonarQube)

- **3 blocos** (por tamanho de PR):
  - Bloco 1: Pequeno (50-150 LOC)
  - Bloco 2: Médio (151-300 LOC)
  - Bloco 3: Grande (301-500 LOC)

- **Total de células experimentais:** 2 tratamentos × 3 blocos = **6 células**

**Distribuição esperada de PRs:**

| Bloco | T1 (Manual) | T2 (SonarQube) | Total por Bloco |
|---|---|---|---|
|Bloco 1 (Pequeno) | 6-10 PRs | 6-10 PRs | 12-20 PRs |
| Bloco 2 (Médio) | 6-10 PRs | 6-10 PRs | 12-20 PRs |
| Bloco 3 (Grande) | 6-10 PRs | 6-10 PRs | 12-20 PRs |
| Total | 18-30 PRs | 18-30 PRs | 36-60 PRs |

**Número de "sessões" (sprints):**

- **Duração:** 3-4 sprints de 2 semanas cada
- **Total:** 6-8 semanas de coleta de dados
- **PRs por sprint (estimativa):** 9-15 PRs (3-5 PRs por sprint × 2 tratamentos)

**Participação dos sujeitos:**

- **Cada desenvolvedor:**
  - Atua como **autor** de PRs em ambos os tratamentos (exposição balanceada)
  - Atua como **revisor manual** em PRs do grupo T1 (rodízio)
  - Interage com **relatórios SonarQube** em seus próprios PRs do grupo T2

- **Exposição esperada por desenvolvedor (assumindo 6 participantes):**
  - Autoria: 6-10 PRs ao longo do experimento (mix T1/T2)
  - Revisão manual: 3-5 PRs de outros autores (apenas T1)
  - Total de interações: ~9-15 PRs

**Justificativa do tamanho de amostra:**

| Aspecto | Valor | Justificativa |
|---|---|---|
| **N total esperado** | 36-60 PRs | Viável em 6-8 semanas; equipe de 6 pessoas produz ~1.5 PRs/semana/pessoa |
| **N por tratamento** | 18-30 PRs | Suficiente para teste t com poder moderado (0.60-0.70) para efeito médio (d=0.5) |
| **N por célula (bloco×tratamento)** | 6-10 PRs | Permite ANOVA de blocos; reduz risco de células vazias |
| **Poder estatístico** | ~0.60-0.70 | Abaixo do ideal (0.80), mas aceitável para estudo exploratório em contexto acadêmico |

**Considerações sobre viabilidade:**

- **Mínimo aceitável:** 30 PRs totais (15 por tratamento) para análise válida
- **Meta ideal:** 50+ PRs totais (25+ por tratamento) para poder adequado
- **Contingência:** Se N < 30 ao final da coleta, estender período experimental em 2 semanas ou reduzir escopo de análise (focar em análise descritiva + tamanho de efeito)

---
## 10. População, sujeitos e amostragem

### 10.1 População-alvo

A **população-alvo** deste experimento é definida como:

> Desenvolvedores que trabalham com **Java e Spring Boot**, atuando em **equipes pequenas/médias (4-6 pessoas)** de desenvolvimento de software, em contextos acadêmicos ou industriais, que realizam revisão de código como prática de garantia de qualidade.

**Critérios de caracterização da população:**

| Critério | Definição |
|---|---|
| **Tecnologia principal** | Java 17+ com Spring Boot 3.x |
| **Tamanho de equipe** | 4-6 desenvolvedores (equipes pequenas/médias) |
| **Contexto** | Acadêmico (prioridade) ou industrial pequeno/médio |
| **Prática de desenvolvimento** | Uso de Git, GitHub, PRs e code review como rotina |
| **Experiência mínima** | 6+ meses com Java; pelo menos 1 projeto em Spring Boot |
| **Engajamento** | Participação voluntária em práticas de qualidade de software |

**Justificativa da população:**

- Alinhada com **objetivo O1-O4** de comparar métodos de revisão
- Representa contexto real onde ambas as práticas (manual + automatizada) são aplicáveis
- Amostra homogênea reduz variabilidade não relacionada ao tratamento

---

### 10.2 Critérios de inclusão de sujeitos

Um participante é **elegível** se atender a TODOS os critérios abaixo:

| Critério | Descrição | Verificação |
|---|---|---|
| **C1: Matriculado na disciplina** | Aluno regularmente matriculado em Engenharia de Software ou disciplina equivalente | Lista oficial da instituição |
| **C2: Experiência com Java** | Mínimo 6 meses de experiência prática com Java (documentado em CV ou projeto anterior) | Entrevista / verificação de projetos anteriores |
| **C3: Experiência com Git/GitHub** | Capacidade de criar branches, fazer commits, abrir PRs e fazer code review básico | Teste prático ou portfolio de commits no GitHub |
| **C4: Disponibilidade de tempo** | Disponibilidade de 3-4 horas/semana para participar do experimento (desenvolvimento, revisão, coleta de dados) | Assinatura de termo de compromisso; verificação de calendário |
| **C5: Consentimento informado** | Leitura e assinatura do termo de consentimento (TCLE) explicando objetivos, riscos e benefícios | Documento assinado antes do início |
| **C6: Acesso a ferramentas** | Tem acesso a computador com Internet, Git instalado e acesso ao repositório GitHub do projeto | Verificação prévia de acesso |

**Processo de verificação:**

1. **Divulgação:** Comunicação por e-mail e em sala de aula com convite para participar
2. **Pré-screening:** Questionário inicial (2-3 minutos) via formulário online para verificar C1-C4
3. **Entrevista/Validação:** Conversa breve (10-15 min) com candidatos pré-selecionados para confirmar critérios
4. **Assinatura:** Coleta de TCLE e termo de concordância
5. **Confirmação:** Lista de participantes confirmados 1 semana antes do início

---

### 10.3 Critérios de exclusão de sujeitos

Um participante é **excluído** se apresentar QUALQUER uma das condições abaixo:

| Critério | Descrição | Impacto na Exclusão |
|---|---|---|
| **E1: Experiência insuficiente** | Menos de 6 meses de experiência com Java | Risco de não conseguir completar tarefas; viés na qualidade do código |
| **E2: Indisponibilidade comprovada** | Menos de 3 horas/semana disponíveis durante o período experimental (férias, trabalho externo, conflitos) | Impossibilidade de participar adequadamente; dados incompletos |
| **E3: Conflito de interesse** | Membro da equipe de suporte técnico/TI que poderia manipular ferramentas; alguém com interesse corporativo em resultado específico | Viés na coleta de dados; comprometimento da integridade científica |
| **E4: Restrição ética/legal** | Menores de idade sem consentimento de responsável; indivíduos com restrições de privacidade ou legal | Violação de normas éticas; impossibilidade de prosseguir |
| **E5: Desempenho insuficiente no pré-teste** | Se houver teste técnico inicial e desempenho < 50%, indicando falta de skills críticas | Risco de não compreender protocolo; resultados não válidos |
| **E6: Desistência durante experimento** | Participante comunica formalmente que deseja sair do estudo | Coleta de dados incompleta; exclusão a posteriori |
| **E7: Falta de adesão ao protocolo** | Participante não segue protocolo (ex: faz review manual quando deveria usar SonarQube; não registra dados) | Invalidação de dados dessa unidade experimental |
| **E8: Eventos adversos** | Participante sofre incidente de segurança da informação (hack de conta, vazamento de código) | Impossibilidade de garantir confidencialidade dos dados |

**Processo de exclusão:**

- **Exclusão pré-experimento:** Se critério E1-E5 detectado, participante é informado educadamente e não iniciada coleta de dados
- **Exclusão mid-experimento:** Se E6-E8 ocorrem, dados do participante até esse ponto são **análisados separadamente** (análise de sensibilidade) ou removidos conforme critério adotado
- **Comunicação:** Participantes excluídos recebem comunicação clara das razões e garantia de que exclusão não afeta nota/avaliação acadêmica

---

### 10.4 Tamanho da amostra planejado (por grupo)

#### Cálculo do Tamanho de Amostra

**Objetivos da amostragem:**

1. Detectar diferença **estatisticamente significativa** entre T1 e T2 em VD1 (Densidade de Defeitos)
2. Ter **poder estatístico suficiente** para concluir se H₀ deve ser rejeitada
3. **Balancear** esforço experimental vs. tamanho da amostra

**Parâmetros estatísticos assumidos:**

| Parâmetro | Valor | Fonte/Justificativa |
|---|---|---|
| **Nível de significância (α)** | 0.05 | Padrão em pesquisa; risco de erro Tipo I |
| **Poder estatístico (1-β)** | 0.80 | Padrão recomendado; β=0.20 (erro Tipo II) |
| **Tamanho de efeito esperado (d de Cohen)** | 0.5 | Efeito médio; diferenças práticas que esperamos encontrar |
| **Teste estatístico** | Teste t independente (two-tailed) | Comparação de 2 grupos independentes |
| **Variância (σ)** | Estimada em ~1.2 defeitos/KLOC | Baseada em literatura; estudos prévios de code review |

**Cálculo (usando fórmula de Cohen para teste t):**

$$n = \frac{2(z_{\alpha/2} + z_\beta)^2 \cdot \sigma^2}{d^2}$$

Onde:
- $z_{\alpha/2} = 1.96$ (para α=0.05, bilateral)
- $z_\beta = 0.84$ (para poder=0.80)
- $d = 0.5$ (tamanho de efeito médio)
- $\sigma = 1.2$ (desvio padrão estimado)

$$n = \frac{2(1.96 + 0.84)^2 \cdot (1.2)^2}{(0.5)^2} = \frac{2 \cdot 7.84 \cdot 1.44}{0.25} \approx 90$$

**Conclusão do cálculo:** ~90 PRs por grupo (180 no total) seria o tamanho ideal para poder 0.80.

#### Ajustes Práticos e Restrições

**Realidade do projeto:** Não é viável alcançar 90 PRs por grupo em 6-8 semanas com equipe de 6 desenvolvedores.

**Amostra realística planejada:**

| Tratamento | PRs Planejados | Razão |
|---|---|---|
| **T1 (Revisão Manual)** | 15-25 PRs | Viável em 6-8 semanas; equipe de 6 gera ~1.5 PR/semana |
| **T2 (Revisão Automatizada)** | 15-25 PRs | Mesmo ritmo de desenvolvimento |
| **Total** | 30-50 PRs | Amostra pragmática balanceada |

**Consequências do tamanho reduzido:**

| Aspecto | Impacto |
|---|---|
| **Poder estatístico** | ~0.60-0.70 (abaixo do ideal 0.80) |
| **Intervalo de confiança (IC)** | Mais largo; precisão reduzida |
| **Tamanho de efeito detectável** | Necessário d ≥ 0.6-0.7 (efeito grande a médio) |
| **Análise de sensibilidade** | Essencial; reportar junto com p-values |

**Justificativa de aceitabilidade:**

- Tamanho de amostra **reduzido é aceitável** em estudos exploratórios e acadêmicos
- Poder 0.60-0.70 ainda oferece evidência considerável (não é "sem poder")
- Resultados serão reportados com **intervalo de confiança, d de Cohen e tamanho de efeito**, não apenas p-value
- Conclusões serão **conservadoras** ("sugestivo de diferença" vs. "diferença significativa")

---

#### Distribuição de Amostra entre Grupos

**Amostra por tratamento:**

| Tratamento | Célula 1 (Bloco Pequeno) | Célula 2 (Bloco Médio) | Célula 3 (Bloco Grande) | Total |
|---|---|---|---|---|
| **T1 (Manual)** | 5-8 PRs | 5-8 PRs | 5-8 PRs | 15-24 PRs |
| **T2 (SonarQube)** | 5-8 PRs | 5-8 PRs | 5-8 PRs | 15-24 PRs |
| **Total por bloco** | 10-16 PRs | 10-16 PRs | 10-16 PRs | 30-48 PRs |

**Amostra por desenvolvedor:**

Com 6 desenvolvedores:
- Cada um contribui com **5-8 PRs** ao longo do experimento (mix T1/T2)
- Cada um realiza **2-4 revisões manuais** de PRs de colegas (T1 apenas)
- Total de interações por pessoa: ~7-12 interações

**Meta mínima de sucesso (C1 do critério 6.2):**

- **Mínimo aceitável:** 30 PRs totais (15 por grupo)
- **Meta ambiciosa:** 40+ PRs totais (20+ por grupo)

---

### 10.5 Método de seleção / recrutamento

#### Estratégia de Recrutamento

**Abordagem:** **Amostragem por Conveniência Estruturada** com seleção de participantes elegíveis

**Racional:** 
- Contexto acadêmico obriga uso de alunos disponíveis em disciplina específica
- Não é viável randomização ao nível de participantes (todos precisam participar)
- Randomização ao nível de PRs/tratamentos garante comparabilidade

**Etapas de recrutamento:**

```mermaid
flowchart LR
    %% Direção horizontal
    %% LR = Left → Right
    %% Nós com estilo uniforme

    A["FASE 1: Divulgação e Convite
    • Apresentação do projeto em sala de aula
    • Distribuição de folder com objetivos e benefícios
    • E-mail com convite formal; link para pré-screening
    Responsável: Professor / Pesquisador
    Timeline: Semana 1 (2-3 dias)"]

    B["FASE 2: Pré-screening (Questionário Online)
    • Verificação de C1-C4: experiência, disponibilidade
    • Formulário de 3-5 minutos via Google Forms
    • Perguntas sobre: experiência Java, Git, horas/sem
    Responsável: Pesquisador (análise automática)
    Timeline: Semana 1 (até dia 5)"]

    C["FASE 3: Validação / Entrevista (10-15 min)
    • Conversa com candidatos pré-selecionados
    • Confirmação de critérios; avaliação de motivação
    • Teste técnico rápido (ex: criar PR no GitHub)
    Responsável: Pesquisador + Professor
    Timeline: Semana 1 (dias 6-7)"]

    D["FASE 4: Consentimento Informado (TCLE)
    • Fornecimento do Termo de Consentimento
    • Leitura; resposta a dúvidas
    • Assinatura e coleta de termo original
    Responsável: Pesquisador + Comitê Ética (se req.)
    Timeline: Semana 1 (fim de semana)"]

    E["FASE 5: Confirmação Final e Treinamento
    • Lista de participantes confirmados
    • Agendamento da sessão de treinamento
    • Distribuição de material (checklist, guias etc.)
    Responsável: Pesquisador
    Timeline: Semana 2 (segunda)"]

    %% Fluxo
    A --> B --> C --> D --> E

    %% Estilos
    classDef fase fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#0d47a1,rx:10,ry:10;
    class A,B,C,D,E fase;
```



#### Critérios de Aceitação / Rejeição

| Cenário | Decisão | Ação |
|---|---|---|
| **Candidato atende todos C1-C8** | ✅ Aceito | Convite formal; agendamento de treinamento |
| **Candidato atende C1-C3, C5-C8; C4 questionável** | ⚠️ Aceitação condicional | Conversa sobre disponibilidade; negociação de horários; menção em TCLE |
| **Candidato falha em C1 ou C2** | ❌ Rejeitado | E-mail educado; explicação de motivo; sugestão de participação futura |
| **Candidato não completa pré-screening** | ❌ Sem dados | Tentativa de contacto; se sem resposta em 5 dias, considera-se recusa |
| **Aceitação total < 4 participantes** | 🚫 Go/No-Go | Revisar convite; estender prazo; considerar cancelar se inviável |

---

### 10.6 Treinamento e preparação dos sujeitos

#### Objetivos do Treinamento

1. **Equalizar conhecimento:** Todos os participantes entendem protocolo e ferramentas
2. **Reduzir viés:** Minimizar variação na aplicação dos métodos
3. **Alinhar expectativas:** Deixar claro que experimento não afeta notas/avaliação
4. **Competência técnica:** Garantir que todos conseguem usar as ferramentas

#### Módulos de Treinamento

**Módulo 1: Visão Geral do Experimento (30 minutos)**

| Tópico | Conteúdo | Duração |
|---|---|---|
| **Objetivos** | Explicar por que estamos comparando revisão manual vs. automatizada | 5 min |
| **Estrutura** | Desenho experimental, grupos, métricas que serão coletadas | 10 min |
| **Cronograma** | Timeline de 6-8 semanas; sprints, datas-chave | 5 min |
| **Confidencialidade** | Segurança dos dados; quem tem acesso; anonimização | 5 min |
| **Engajamento** | Incentivos; como contribuir de forma igualitária | 5 min |

**Módulo 2: Protocolo de Revisão Manual (45 minutos)**

Conteúdo detalhado em seção 11.3.

| Tópico | Conteúdo | Duração | Material |
|---|---|---|---|
| **Checklist de revisão** | Apresentação de critérios de revisão (lógica, legibilidade, segurança, boas práticas) | 15 min | PDF com checklist; exemplos de problemas |
| **Casos de uso** | 3-4 exemplos de PRs; discussão em grupo de como revisar | 15 min | PRs de exemplo (anterior ou fictício) |
| **Feedback efetivo** | Como deixar comentários construtivos no GitHub | 10 min | Template de comentário; boas práticas |
| **Prática hands-on** | Participantes fazem review de PR de treino em tempo real | 5 min | PR de treino preparado; feedback do facilitador |

**Módulo 3: SonarQube e Análise Automatizada (45 minutos)**

| Tópico | Conteúdo | Duração | Material |
|---|---|---|---|
| **Tour de SonarQube** | Demonstração de painel, relatórios, quality gate | 15 min | Tela compartilhada; printscreens anotados |
| **Interpretação de issues** | Explicação de cada categoria (bugs, vulnerabilities, code smells, etc.) | 15 min | Documento com exemplos; referência rápida |
| **Quality gate** | O que significa passar/falhar; o que fazer se falhar | 10 min | Exemplo de relatório com quality gate falho |
| **Prática hands-on** | Participantes analisam relatório SonarQube de projeto teste | 5 min | Projeto teste preparado; discussão |

**Módulo 4: Processo GitHub e CI/CD (30 minutos)**

| Tópico | Conteúdo | Duração | Material |
|---|---|---|---|
| **Workflow padrão** | Fluxo de criar branch → commit → push → abrir PR → merge | 10 min | Diagrama; reprodução ao vivo |
| **Alocação de tratamentos** | "Sua próxima PR será revisada por [método]. Eis o que esperar:" | 10 min | Tabela de próximos PRs; roles de cada um |
| **Registro de dados** | Quais dados serão coletados automaticamente (timestamps, commits, etc.) | 5 min | Planilha de dados (anonimizada) |
| **Suporte técnico** | Como reportar problemas técnicos (SonarQube down, acesso perdido) | 5 min | Contato de suporte; SLA esperado |

**Módulo 5: Ética, Confidencialidade e Direitos dos Participantes (20 minutos)**

| Tópico | Conteúdo | Duração | Material |
|---|---|---|---|
| **Direitos** | Direito de desistir sem penalização; dados serão protegidos | 5 min | Resumo de direitos (em TCLE) |
| **Confidencialidade** | Como dados serão armazenados, quem pode acessar | 5 min | Política de privacidade do projeto |
| **Uso dos dados** | Dados usados apenas para pesquisa; será publicado anonimizado | 5 min | Exemplos de relatórios com anonimização |
| **Contato em caso de dúvida** | Professor, pesquisador, comitê ética | 5 min | Números, e-mails, horários |

#### Cronograma de Treinamento

**Sessão única integrada (3 horas total)**

```
Semana 2, segunda-feira, 14:00-17:00

14:00-14:30 → Módulo 1: Visão geral
14:30-15:15 → Módulo 2: Revisão manual + pausa 5 min
15:20-16:05 → Módulo 3: SonarQube + pausa 5 min
16:10-16:40 → Módulo 4: GitHub/CI-CD
16:40-17:00 → Módulo 5: Ética + Q&A
```

**Alternativa (se presencial problemático):** Gravação assíncrona disponibilizada; sessão ao vivo (30 min) para Q&A

#### Materiais de Suporte

**Documentos a fornecer:**

1. **Checklist de Revisão Manual (PDF/Markdown)**
   - Versão impressa e digital
   - Inclui exemplos de cada critério

2. **Quick Reference Guide — SonarQube (1-2 páginas)**
   - Categorias de issues
   - Como interpretar cada tipo
   - Links para documentação completa

3. **Protocolo Experimental (resumido)**
   - O que fazer em cada fase
   - O que não fazer
   - Contato para dúvidas

4. **Vídeo de Tutorial (5-10 min)**
   - Gravação do treinamento ou compilação de demos
   - Disponibilizada para revisão posterior

5. **FAQ (Frequently Asked Questions)**
   - Perguntas comuns sobre protocolo, ferramentas, ética
   - Atualizado durante experimento conforme surgem dúvidas

#### Validação do Aprendizado

**Pós-treinamento, avaliação breve:**

| Método | Questão | Critério de Sucesso |
|---|---|---|
| **Questionário** | "Qual é o objetivo do experimento?" | ≥80% respostas corretas |
| **Demonstração** | Participante faz review de PR fictício usando checklist | Identifica ≥3/4 problemas plantados |
| **Interpretação** | Participante explica um issue SonarQube | Explicação correta de bug/vulnerability |

**Se não atingir sucesso:** Fornecimento de reforço de treinamento 1-on-1; adiamento do início até competência confirmada

---

## 11. Instrumentação e protocolo operacional

### 11.1 Instrumentos de coleta (questionários, logs, planilhas, etc.)

#### Instrumentos primários de coleta de dados

| ID | Instrumento | Descrição | Formato | Variáveis Coletadas | Responsável |
|---|---|---|---|---|---|
| **I1** | **Planilha de Registro de PRs** | Planilha mestre para tracking de todos os PRs do experimento | Google Sheets | PR_ID, Autor, Data_Abertura, LOC, Bloco, Tratamento, Data_Merge, Status | Pesquisador |
| **I2** | **Checklist de Revisão Manual** | Formulário padronizado para revisores humanos preencherem durante análise de PRs em T1 | Google Forms | Critérios de qualidade (lógica, segurança, legibilidade), Comentários, Tempo de revisão, Aprovação/Rejeição | Revisor manual |
| **I3** | **Relatórios SonarQube** | Exports JSON dos relatórios de análise estática para PRs em T2 | JSON (API) | Bugs, Vulnerabilities, Code Smells, Complexity, Duplicação, Coverage | GitHub Actions (automático) |
| **I4** | **Registro de Defeitos Pós-Entrega** | Template de issue no GitHub para reportar defeitos encontrados em staging/produção | GitHub Issues | Defeito_ID, PR_Origem, Severidade, Categoria, Descrição, Reprodução | Testador |
| **I5** | **Logs de Tempo de Revisão** | Script que captura timestamps de eventos no GitHub (PR opened, reviewed, approved, merged) | CSV (GitHub API) | PR_ID, Timestamp_Abertura, Timestamp_Primeira_Revisão, Timestamp_Aprovação, Timestamp_Merge | Script automático |
| **I6** | **Contador de Comentários e Iterações** | Script que conta número de comentários e commits após primeira revisão | CSV (GitHub API) | PR_ID, Num_Comentarios, Num_Commits_Pos_Revisao, Num_Iteracoes | Script automático |
| **I7** | **Questionário de Satisfação (Pós-Experimento)** | Questionário Likert + perguntas abertas sobre percepção dos métodos de revisão | Google Forms | Satisfação (M13), Confiança (M14), Utilidade percebida, Preferências, Sugestões | Participante |
| **I8** | **Entrevista Semi-Estruturada** | Roteiro de entrevista qualitativa para aprofundar percepções individuais | Áudio + Transcrição | Feedback qualitativo (M16), Experiências, Desafios, Aprendizados | Pesquisador (entrevistador) |
| **I9** | **Formulário de Classificação de Complexidade** | Formulário rápido para autor e revisor classificarem complexidade da feature | Google Forms (1 pergunta) | Complexidade percebida (Simples/Média/Alta) | Autor + Revisor |
| **I10** | **Planilha de Validação (True Positives)** | Planilha para cruzar issues de revisão com defeitos reais encontrados em testes | Google Sheets | Issue_ID, Defeito_Correspondente, Validado (Sim/Não/Parcial) | Pesquisador + QA |

#### Instrumentos secundários (documentação e controle)

| ID | Instrumento | Descrição | Formato | Finalidade |
|---|---|---|---|---|
| **I11** | **Termo de Consentimento Livre e Esclarecido (TCLE)** | Documento legal de consentimento dos participantes | PDF assinado | Ética e conformidade |
| **I12** | **Diário de Campo do Pesquisador** | Notas de observação sobre dinâmica do experimento, incidentes, ajustes | Markdown | Contexto qualitativo; análise de ameaças à validade |
| **I13** | **Log de Incidentes Técnicos** | Registro de falhas de ferramentas (SonarQube offline, CI/CD falhando) | Google Sheets | Controle de qualidade dos dados |
| **I14** | **Checklist de Prontidão (Definition of Ready)** | Checklist para verificar se todos os requisitos foram cumpridos antes de iniciar | Checklist (digital) | Governança |

---

### 11.2 Materiais de suporte (instruções, guias)

#### Materiais para participantes

| Material | Descrição | Formato | Público | Momento de Entrega |
|---|---|---|---|---|
| **Guia do Participante** | Documento completo com visão geral do experimento, papéis, responsabilidades, cronograma | PDF (10 páginas) | Todos os participantes | Sessão de treinamento |
| **Checklist de Revisão Manual** | Lista de verificação com critérios padronizados (lógica, segurança, performance, legibilidade, testes) | PDF (2 páginas) | Revisores manuais | Sessão 1 de treinamento |
| **Guia Rápido do SonarQube** | Tutorial visual de como interpretar relatórios, priorizar issues e corrigir problemas | PDF (4 páginas) + vídeo (5 min) | Autores de PRs em T2 | Sessão 2 de treinamento |
| **Template de Descrição de PR** | Modelo padrão para descrição de PRs (contexto, mudanças, testes realizados) | Markdown (arquivo no repo) | Autores de PRs | Início do experimento |
| **Template de Issue de Defeito** | Modelo para reportar defeitos encontrados em staging (passos de reprodução, severidade, screenshots) | Markdown (issue template no GitHub) | Testadores | Início do experimento |
| **Fluxograma do Protocolo Experimental** | Diagrama visual do fluxo completo desde abertura de PR até coleta de dados (ver seção 11.3) | PDF A3 + PNG | Todos os participantes | Sessão 3 de treinamento |
| **FAQ do Experimento** | Perguntas frequentes sobre procedimentos, ferramentas, prazos | Markdown (wiki do GitHub) | Todos os participantes | Disponível continuamente |
| **Glossário de Termos** | Definições de termos técnicos (code smell, technical debt, quality gate, etc.) | PDF (2 páginas) | Todos os participantes | Sessão 2 de treinamento |

#### Materiais para administradores do experimento

| Material | Descrição | Formato | Finalidade |
|---|---|---|---|
| **Manual de Operação do Experimento** | Guia completo para o pesquisador executar o experimento (configuração, coleta, troubleshooting) | Markdown (20 páginas) | Referência operacional |
| **Scripts de Automação** | Coleção de scripts Python/Shell para coletar dados do GitHub API e SonarQube | GitHub repo (`/scripts`) | Automação da coleta |
| **Protocolo de Randomização** | Documento com algoritmo e registro de alocação de PRs aos tratamentos | Markdown + planilha | Auditoria e transparência |
| **Checklist de Verificação Semanal** | Lista de tarefas de monitoramento (conferir aderência, resolver bloqueios, atualizar planilhas) | Checklist (Notion/Trello) | Governança operacional |
| **Roteiro de Entrevista Semi-Estruturada** | Perguntas abertas para explorar percepções dos participantes pós-experimento | Documento Word/PDF | Coleta qualitativa |
| **Plano de Contingência** | Procedimentos para lidar com cenários de risco (desistências, falhas técnicas, baixa adesão) | Markdown | Gestão de riscos |

---

### 11.3 Procedimento experimental (protocolo – visão passo a passo)

#### Fluxograma do Protocolo Experimental

![Fluxograma do Protocolo Experimental](imagens/fluxograma_protocolo_experimental.png)




## 11.4 Plano de piloto (se haverá piloto, escopo e critérios de ajuste)

### **Realização de piloto**

**Decisão:** Sim, será realizado um piloto limitado antes da operação completa do experimento.

**Justificativa:**  
O piloto é essencial para:

- Validar a viabilidade operacional do protocolo  
- Identificar gargalos ou ambiguidades nas instruções  
- Testar a funcionalidade dos instrumentos de coleta (formulários, scripts)  
- Calibrar estimativas de tempo e carga de trabalho  
- Ajustar o treinamento dos participantes baseado em dificuldades reais  

---

### **Escopo do piloto**

| Aspecto | Detalhamento |
|--------|--------------|
| **Participantes** | 2–3 desenvolvedores voluntários (preferencialmente não participarão do experimento principal, ou seus dados do piloto serão descartados) |
| **Duração** | 1 sprint (2 semanas) |
| **Número de PRs** | 4–6 PRs no total (2–3 por tratamento) |
| **Cobertura de tratamentos** | Ambos os tratamentos (T1 e T2) |
| **Cobertura de blocos** | Ao menos 2 blocos (Pequeno e Médio) |
| **Ferramentas** | GitHub, SonarQube, CI/CD, formulários, scripts |
| **Coleta completa** | Sim, todos os instrumentos (I1–I10) serão usados |

---

### **Objetivos específicos do piloto**

| Objetivo | Critério de Validação | Método |
|---------|------------------------|--------|
| Validar clareza do protocolo | 100% dos participantes conseguem executar tarefas sem assistência | Observação + questionário pós-piloto |
| Testar instrumentos de coleta | Formulários e scripts funcionam sem erros | Inspeção manual |
| Verificar integração CI/CD + SonarQube | Pipeline sem falhas; relatório em <10 min | Logs técnicos |
| Calibrar tempo de revisão | Estimativa dentro de ±30% do observado | Comparação estimado vs. real |
| Identificar pontos de confusão | Lista de dúvidas dos participantes | Diário do pesquisador |
| Testar checklist de revisão | Checklist sem ambiguidades | análise de consistência |
| Validar randomização | PRs alocados corretamente | Auditoria em I1 |

---

### **Critérios de ajuste do protocolo**

| Problema Identificado | Ajuste Permitido | Ajuste Não Permitido |
|----------------------|------------------|------------------------|
| Instruções ambíguas | Reescrever materiais | Mudar hipóteses |
| Checklist extenso | Ajustar itens | Remover segurança |
| Formulários difíceis | Simplificar perguntas | Remover métricas VD1–VD14 |
| Bugs em scripts | Corrigir | Alterar fonte dos dados |
| Tempo muito alto de revisão | Ajustar estimativas | Reduzir rigor |
| Erros no SonarQube | Ajustar quality gate | Remover tratamento T2 |
| Confusão sobre papéis | Melhorar treinamento | Alterar desenho experimental |
| Defeitos não detectados | Reforçar testes | Aceitar ausência como normal |
| Baixa resposta | Simplificar questionário | Remover qualitativo |
| Variabilidade alta | Reforçar treinamento | Aceitar inconsistência |

---

### **Decisão Go/No-Go pós-piloto**

| Critério | Go | No-Go |
|----------|----|--------|
| Viabilidade técnica | Tudo funciona | Falhas críticas |
| Clareza do protocolo | ≥80% aderência | <60% aderência |
| Qualidade dos dados | Completos e consistentes | >20% faltantes |
| Viabilidade de tempo | Dentro do cronograma | >8 semanas |
| Engajamento | Boa motivação | Resistência |

**Decisão final:** Se **4/5** critérios forem Go → iniciar experimento.  
Se não → ajustes + mini-piloto (1 semana).

---

# 12. Plano de análise de dados (pré-execução)



## 12.1 Estratégia geral de análise

### **Estrutura da análise**

| Questão | Estratégia | Variáveis | Técnica |
|--------|------------|-----------|---------|
| Q1.1 | Comparar densidade de defeitos | VD1, VC1 | t-test / Mann-Whitney / ANOVA |
| Q1.2 | Comparar defeitos pós-entrega | VD3, VD13 | Wilcoxon / χ² |
| Q1.3 | Relação entre issues de revisão e defeitos | VD12, VD9 | Correlação Spearman |
| Q2.1 | Vulnerabilidades identificadas | VD4, M7 | Mann-Whitney |
| Q2.2 | Complexidade | VD5, VD2 | t-test / correlação |
| Q2.3 | Duplicação | VD6, VD1 | t-test / regressão |
| Q3.1 | Tempo de revisão | VD7, LOC | t-test / ANCOVA |
| Q3.2 | Comentários | VD9 | Mann-Whitney |
| Q3.3 | Ciclos de retrabalho | VD8 | Mann-Whitney |
| Q4.1 | Satisfação | VD10, VD14 | Mann-Whitney + qualitativo |
| Q4.2 | Aceitabilidade | VD11, VD15 | Mann-Whitney |
| Q4.3 | Aprendizado | VD14 | Codificação temática |

---

### **Fluxo geral de análise**

## Preparação e limpeza

- Preparação e limpeza dos dados  
- Análise exploratória  
- Teste de pressupostos  
- Testes de hipóteses  
- Tamanho de efeito  
- Análise qualitativa  
- Triangulação  
- Discussão  

---

## 12.2 Métodos estatísticos

### **Testes paramétricos**

| Teste | Aplicação | Condições |
|-------|-----------|-----------|
| t-test | VD1, VD2, VD5, VD6, VD7 | Normalidade + homogeneidade |
| ANOVA | Efeito de tratamento e bloco | Normalidade + balanceamento |
| ANCOVA | Controlar LOC/experiência | Linearidade |
| Regressão linear | VD6 → VD1 | Normalidade dos resíduos |
| Correlação Pearson | VD5 e VD1 | Relação linear |

---

### **Testes não-paramétricos**

| Teste | Aplicação |
|-------|-----------|
| Mann-Whitney | Comparação entre grupos |
| Kruskal-Wallis | Alternativa à ANOVA |
| Spearman | Correlação ordinal |
| χ² | Distribuições categóricas |
| Fisher | n pequeno |

---

### **Tamanho de efeito**

| Medida | Quando usar |
|--------|-------------|
| Cohen d | Testes paramétricos |
| r | Mann-Whitney |
| η² | ANOVA |
| V de Cramér | χ² |

---

## 12.3 Dados faltantes e outliers

### **Dados faltantes**

| Cenário | Ação |
|---------|------|
| MCAR <5% | Listwise deletion |
| MCAR 5–10% | Imputação simples |
| MCAR >10% | Multiple Imputation |
| MNAR | Sensibilidade |
| VD1 faltante | Excluir |
| Covariável faltante | Imputação por regressão |

---

### **Outliers**

| Tipo | Ação |
|------|------|
| Legítimo | Incluir + análise de sensibilidade |
| Erro | Corrigir ou excluir |
| Influente | Reportar com/sem |
| Secundário | Winsorizar |
| >10% no grupo | Investigar processo |

---

## 12.4 Análise qualitativa

### **Fontes**

- Respostas abertas (I7)  
- Entrevistas (I8)  
- Comentários de revisão (I2)  
- Diário de campo (I12)  

---

### **Método: Análise Temática (Braun & Clarke)**

1. Familiarização  
2. Codificação inicial  
3. Busca de temas  
4. Revisão  
5. Nomeação e definição  
6. Relatório final  

---

### **Técnicas**

- Contagem de frequência  
- Co-ocorrência  
- Comparação entre tratamentos  
- Análise de sentimento  
- Word cloud  

---

### **Rigor**

| Critério | Estratégia |
|----------|------------|
| Credibilidade | Triangulação, member checking |
| Transferibilidade | Descrição rica |
| Confiabilidade | Duplo codificador + Kappa > 0.7 |
| Confirmabilidade | Audit trail |

---

### **Triangulação**

| Cenário | Interpretação |
|---------|--------------|
| Convergência | Mesma direção |
| Complementaridade | Quali explica quanti |
| Divergência | Resultados conflitantes |
| Silêncio | Algo aparece só em um dos tipos |

---

## 13. Avaliação de validade (ameaças e mitigação)

### 13.1 Validade de conclusão
**Definição:** Validade de conclusão refere-se à robustez das inferências estatísticas sobre relação entre tratamento e resposta. Ameaças comprometem a capacidade de detectar efeitos reais ou levam a conclusões errôneas sobre significância.

## Ameaças identificadas e estratégias de mitigação

### C1 — Baixo poder estatístico
- **Risco:** Amostra pequena (n=40-60 PRs) reduz poder para detectar diferenças  
- **Impacto:** Erro Tipo II  
- **Mitigação:**  
  - Priorizar detecção de efeitos médios/grandes (d≥0.5)  
  - Usar testes não-paramétricos  
  - Reportar tamanho de efeito + IC95%  
  - Aceitar poder moderado (0.60-0.70) como limitação  
- **Monitoramento:** Cálculo de poder post-hoc; análise de sensibilidade

### C2 — Violação de pressupostos estatísticos
- **Risco:** Dados não-normais, variâncias heterogêneas  
- **Impacto:** p-values incorretos  
- **Mitigação:**  
  - Testes Shapiro-Wilk, Levene  
  - Testes não-paramétricos  
  - Transformações (log, Box-Cox)  
  - Reportar paramétrico + não-paramétrico  
- **Monitoramento:** Verificação de pressupostos e gráficos diagnósticos

### C3 — Confiabilidade de medidas
- **Risco:** Erro de medição em defeitos e timestamps  
- **Impacto:** Ruído obscurece sinal real  
- **Mitigação:**  
  - Scripts automáticos  
  - Auditoria manual de 20%  
  - Protocolos claros  
- **Monitoramento:** Auditoria e verificação de consistência

### C4 — Pesca de significância (p-hacking)
- **Mitigação:**  
  - Hipóteses definidas a priori  
  - Bonferroni (>5 testes)  
  - α=0.01 para exploratórios  
  - Reportar todos os testes  
- **Monitoramento:** Registro pré-análise

### C5 — Variabilidade da implementação do tratamento
- **Mitigação:**  
  - Treinamento padronizado  
  - Checklist obrigatório  
  - Configuração SonarQube congelada  
- **Monitoramento:** Logs semanais, auditoria

### C6 — Heterogeneidade de variância
- **Mitigação:**  
  - Teste t de Welch  
  - Teste de Levene  
  - Transformações  
- **Monitoramento:** Análise de resíduos

### C7 — Outliers influentes
- **Mitigação:**  
  - Sensibilidade com/sem outliers  
  - Mediana + Mann-Whitney  
  - Verificar causa  
- **Monitoramento:** Boxplots e Cook’s Distance

### C8 — Tamanho de amostra desbalanceado
- **Mitigação:**  
  - Randomização com balanceamento  
  - Monitoramento semanal  
  - Recrutar suplentes  
- **Monitoramento:** n_T1 vs n_T2 semanal

---

### 13.2 Validade interna (causalidade)

**Mitigações para 10 ameaças:** História, maturação, Hawthorne, instrumentação, seleção, atrito, contaminação, rivalidade, demoralização, história local.

- **Controles:** Período curto (6-8 sem.); análise por sprint; Kappa > 0.7; randomização com bloqueio; suplentes; cegamento parcial; análise temporal
- **Monitoramento:** Diário de campo; logs semanais; gráficos de tendência; auditoria 20%

---

### 13.3 Validade de constructo (operacionalização)

### CT1 — Inadequação
- **Mitigação:** Múltiplas métricas VDs; Triangulação

### CT2 — Múltiplos métodos
- **Mitigação:** Quanti + quali integrados

### CT4 — Rigor
- **Mitigação:** Definição clara; Kappa > 0.7; coleta automática


---

### 13.4 Validade externa (generalização)

**Limitações da pesquisa:**
- Contexto acadêmico; não generaliza para corporações
- Tamanho pequeno; não generaliza para projetos maiores
- Linguagem Java específica
- Período curto (6-8 semanas)
- Sem pressão competitiva real

**Pode generalizar para:** Equipes ágeis pequenas, projetos backend Java/C#, código novo

---

### 13.5 Resumo executivo: Top 5 ameaças críticas

| # | Ameaça | Impacto | Mitigação Primária | Status |
|---|--------|---------|--------|--------|
| 1 | **Baixo poder** (n=40-60) | Erro Tipo II | IC95% + d; testes não-param | ✅ Monit. post-hoc |
| 2 | **Maturação** (progresso dev) | Confusão com trat | Análise por sprint | ✅ Gráficos |
| 3 | **Reatividade** (Hawthorne) | Comportamento alterado | Coleta automática; cegamento | ✅ Análise temporal |
| 4 | **Contexto acadêmico** | Impossível generalizar ind | Limites claros na discussão | ⚠️ Amostra diversa |
| 5 | **Ambiguidade defeito** | Inconsistência class | Definição clara; Kappa > 0.7 | ✅ Validação dupla |

**Plano de mitigação integrado:**
- **Pré-execução:** Piloto, treinamento, definição de hipóteses, Kappa baseline
- **Durante:** Monitoramento semanal, diário de campo, auditoria 20%, re-treinamento
- **Pós:** Análise de sensibilidade, teste pressupostos, discussão de limitações

---

## 14. Ética, privacidade e conformidade

### 14.1 Questões éticas (uso de sujeitos, incentivos, etc.)

**Questões éticas identificadas:**

**Uso de estudantes como sujeitos de pesquisa:**
- Existe uma relação hierárquica entre pesquisador/professor e estudantes participantes
- Risco de pressão implícita para participação devido à dinâmica acadêmica
- Possível conflito entre objetivos didáticos da disciplina e objetivos da pesquisa

**Incentivos:**
- Não haverá incentivos financeiros ou acadêmicos diretos (pontos extras, etc.)
- Benefício indireto: aprendizado sobre práticas de qualidade de software e métodos empíricos
- Certificado de participação em pesquisa (opcional, apenas para currículo)

---

### 14.2 Consentimento informado

**Processo de obtenção de consentimento:**

**Fase 1: Apresentação inicial (Semana 0)**
- Reunião presencial de 30 minutos para apresentar o estudo
- Slides explicando objetivos, metodologia, riscos, benefícios e direitos dos participantes
- Sessão de perguntas e respostas
- Distribuição do Termo de Consentimento Livre e Esclarecido (TCLE)

**Informações fornecidas no TCLE:**
1. **Título e objetivo do estudo:** Comparação entre revisão manual e automatizada
2. **Procedimentos:** O que os participantes farão (desenvolver, revisar, responder questionários)
3. **Duração:** 6-8 semanas, com estimativa de tempo semanal (4-6 horas)
4. **Riscos mínimos:** Desconforto ao receber críticas; possível aumento de carga de trabalho
5. **Benefícios:** Aprendizado sobre qualidade de software; contribuição para conhecimento científico
6. **Confidencialidade:** Como dados serão anonimizados e protegidos
7. **Voluntariedade:** Direito de recusar ou desistir sem penalização
8. **Contatos:** Email e telefone do pesquisador e do comitê de ética

**Fase 2: Período de reflexão (1 semana)**
- Participantes levam TCLE para casa
- Podem consultar familiares, outros professores, colegas
- Prazo de 7 dias para decisão

**Fase 3: Coleta de consentimento (Semana 1)**
- Assinatura física ou digital do TCLE
- Coleta realizada por assistente de pesquisa (não pelo professor da disciplina)
- Duas vias: uma para participante, outra para arquivo da pesquisa
- Consentimento registrado em planilha segura (acesso restrito)

**Formato do consentimento:**
- Documento de 2-3 páginas em linguagem clara e acessível (evitar jargões)
- Checkbox para cada item lido e compreendido
- Espaço para perguntas adicionais antes da assinatura
- Versão digital com timestamp para rastreabilidade

**Reafirmação de consentimento:**
- Breve lembrete no início de cada sprint sobre direitos dos participantes
- Possibilidade de retirar consentimento via email a qualquer momento

---

### 14.3 Privacidade e proteção de dados

**Dados pessoais coletados:**

| Tipo de Dado | Informação Específica | Sensibilidade | Necessidade |
|---|---|---|---|
| **Identificação** | Nome, matrícula, email | Média | Necessário para rastreamento de PRs e follow-up |
| **Desempenho acadêmico** | Semestre, disciplinas cursadas | Baixa | Caracterização de experiência |
| **Código-fonte** | Repositório GitHub (username visível) | Média | Núcleo do experimento |
| **Métricas de qualidade** | Defeitos, complexidade, tempo de revisão | Média | Variáveis dependentes |
| **Feedback subjetivo** | Respostas de questionários, entrevistas | Média | Dados qualitativos |

**Estratégias de proteção:**

**Anonimização:**
- Cada participante receberá um **código único alfanumérico** (ex: P001, P002, ..., P006)
- Tabela de mapeamento (nome real ↔ código) armazenada separadamente em arquivo criptografado
- Apenas pesquisador principal terá acesso à tabela de mapeamento
- Publicações e relatórios usarão exclusivamente códigos anônimos

**Pseudoanonimização de repositórios:**
- Repositórios serão clonados para ambiente privado de análise
- Usernames do GitHub serão substituídos por códigos antes da análise
- Commits e comentários terão autores mascarados

**Controle de acesso:**
- Dados brutos armazenados em Google Drive com criptografia (2FA ativado)
- Acesso restrito ao pesquisador principal e orientador
- Logs de acesso habilitados
- Compartilhamento com terceiros apenas após anonimização completa

**Retenção de dados:**
- **Durante o experimento:** Dados completos mantidos em servidor seguro
- **Pós-experimento:** Dados anonimizados mantidos por 5 anos para auditoria e replicação
- **Dados identificáveis:** Descartados após 1 ano ou ao final da defesa do TCC (o que ocorrer primeiro)
- **Exclusão sob demanda:** Participantes podem solicitar exclusão total de seus dados até 30 dias após conclusão da coleta

**Conformidade com LGPD (Lei Geral de Proteção de Dados):**
- Base legal: Consentimento explícito (Art. 7º, I) e pesquisa científica (Art. 7º, IV)
- Finalidade específica: Pesquisa acadêmica sobre qualidade de software
- Minimização: Apenas dados estritamente necessários serão coletados
- Transparência: Participantes informados sobre todos os dados coletados e seu uso

**Compartilhamento de dados:**
- Dataset anonimizado pode ser publicado em repositório acadêmico (ex: Zenodo, figshare)
- Apenas com consentimento explícito adicional dos participantes
- Código-fonte não será publicado sem permissão

---

### 14.4 Aprovações necessárias (comitê de ética, jurídico, DPO, etc.)

**Órgãos e aprovações requeridas:**

| Órgão | Tipo de Aprovação | Status Atual | Prazo Estimado | Responsável |
|---|---|---|---|---|
| **Comitê de Ética em Pesquisa (CEP)** | Protocolo de pesquisa com seres humanos | ⏳ Pendente | 30-60 dias | Pesquisador + Orientador |
| **Coordenação do Curso** | Autorização para uso de disciplina | ✅ Aprovado | - | Professor da disciplina |
| **Departamento de TI** | Uso de infraestrutura (servidores, SonarQube) | ⏳ Em análise | 7-14 dias | Pesquisador |
| **Jurídico da Instituição** | Revisão do TCLE e conformidade LGPD | ⏳ Pendente | 14-21 dias | Setor jurídico |
| **DPO (Data Protection Officer)** | Validação de medidas de proteção de dados | ⏳ Pendente | 7 dias | Pesquisador + DPO |

**Documentação necessária para CEP:**

1. **Plataforma Brasil:** Cadastro completo do projeto
2. **Projeto detalhado:** Versão expandida deste documento
3. **TCLE:** Termo de consentimento revisado
4. **Folha de rosto:** Assinada pelo diretor da unidade
5. **Currículo Lattes:** Pesquisador e orientador atualizados
6. **Instrumentos de coleta:** Questionários, roteiros de entrevista, checklists
7. **Declaração de infraestrutura:** Confirmação de disponibilidade de recursos
8. **Cronograma detalhado:** Com previsão de início pós-aprovação

**Processo de submissão ao CEP:**

**Semana -8:** Preparação de documentação
**Semana -7:** Submissão via Plataforma Brasil
**Semana -6 a -2:** Análise pelo CEP; possíveis solicitações de ajustes
**Semana -1:** Aprovação final (estimativa)
**Semana 0:** Início do recrutamento de participantes


---

## 15. Recursos, infraestrutura e orçamento

### 15.1 Recursos humanos e papéis

**Equipe do experimento:**

**1. Pesquisador Principal (Gabriel Ferreira Amaral)**
- **Responsabilidades:**
  - Desenho experimental e definição de hipóteses
  - Coordenação geral do experimento
  - Coleta e análise de dados
  - Preparação de instrumentos (questionários, checklists)
  - Redação de relatórios e publicações
  - Garantia de conformidade ética
- **Dedicação:** 10-15 horas/semana durante 8 semanas
- **Qualificações:** Estudante de TCC em Engenharia de Software; experiência com Java, Git e pesquisa empírica

**2. Orientador Acadêmico (Professor [Danilo Maia])**
- **Responsabilidades:**
  - Supervisão metodológica e científica
  - Revisão de instrumentos e plano de análise
  - Apoio na interpretação de resultados
  - Co-autoria em publicações
  - Mediação de conflitos éticos ou operacionais
- **Dedicação:** 2-3 horas/semana
- **Qualificações:** Mestrado em Engenharia de Software; experiência em métodos empíricos

**3. Participantes / Desenvolvedores (4-6 estudantes)**
- **Responsabilidades:**
  - Desenvolver features em Java/Spring Boot
  - Abrir pull requests seguindo protocolo
  - Realizar revisões manuais (quando designados)
  - Interagir com SonarQube (quando aplicável)
  - Responder questionários e participar de entrevistas
  - Executar testes em staging/homologação
- **Dedicação:** 4-6 horas/semana (integrado ao trabalho normal da disciplina)
- **Qualificações:** Conforme critérios de inclusão (seção 10.2)

**4. Assistente de Pesquisa (Opcional)**
- **Responsabilidades:**
  - Coleta de consentimento informado
  - Organização de dados brutos
  - Suporte técnico em CI/CD e SonarQube
  - Transcrição de entrevistas
- **Dedicação:** 3-5 horas/semana
- **Qualificações:** Estudante de pós-graduação ou graduação avançada com experiência em pesquisa
- **Status:** Desejável, mas não crítico; pesquisador principal pode assumir essas funções se necessário

**5. Especialista em Estatística (Consultor)**
- **Responsabilidades:**
  - Revisão do desenho experimental e cálculo de poder
  - Consultoria na análise estatística (ANOVA, testes de hipóteses)
  - Validação de pressupostos e escolha de testes apropriados
- **Dedicação:** 2-4 horas total (consultorias pontuais)
- **Qualificações:** Professor ou profissional com expertise em estatística aplicada
- **Status:** Consulta pontual; não integrado à equipe

**6. Suporte Técnico de TI (Institucional)**
- **Responsabilidades:**
  - Configuração e manutenção de servidor SonarQube (se self-hosted)
  - Suporte em CI/CD (GitHub Actions)
  - Acesso a ambientes de staging
  - Backup de dados
- **Dedicação:** 1-2 horas/semana (sob demanda)
- **Status:** Dependente de aprovação institucional

**Matriz RACI (Responsável, Aprovador, Consultado, Informado):**

| Atividade | Pesquisador | Orientador | Participantes | Assist. Pesquisa | TI |
|---|---|---|---|---|---|
| Desenho experimental | R/A | C | I | - | - |
| Submissão ao CEP | R | A | - | C | - |
| Recrutamento | R | C | - | R | - |
| Coleta de dados | R | I | R | C | - |
| Revisão de código | I | I | R | - | - |
| Análise estatística | R/A | C | I | - | - |
| Infraestrutura técnica | C | I | I | C | R |
| Publicação | R | A | C | - | - |

---

### 15.2 Infraestrutura técnica necessária

**Repositório e Controle de Versão:**
- **GitHub (Cloud):**
  - Repositório privado com acesso controlado
  - GitHub Actions para CI/CD (quota gratuita: 2.000 minutos/mês)
  - Proteção de branch `main` (requer aprovação de PR)
  - Webhooks para integração com SonarQube
- **Requisitos:** Conta GitHub educacional (gratuita); internet estável

**Análise Estática de Código:**
- **SonarQube:**
  - **Opção 1 (preferencial):** SonarCloud (cloud gratuito para projetos open-source/educacionais)
    - Sem custo; sem manutenção
    - Integração nativa com GitHub
    - Limitações: dados armazenados em servidor terceiro
  - **Opção 2 (alternativa):** SonarQube Community Edition (self-hosted)
    - Servidor Linux com Docker
    - Requisitos: 2 vCPUs, 4 GB RAM, 20 GB disco
    - Vantagem: controle total dos dados
    - Desvantagem: requer manutenção
- **Configuração:** Regras padrão (Sonar Way); quality gate padrão

**Integração Contínua (CI/CD):**
- **GitHub Actions:**
  - Workflows para:
    - Build e testes automatizados (Maven/Gradle)
    - Análise SonarQube (acionada em cada push/PR)
    - Deploy para staging (opcional)
  - Secrets gerenciados via GitHub Secrets
- **Requisitos:** Arquivos `.github/workflows/*.yml` no repositório

**Ambiente de Desenvolvimento:**
- **Local (máquinas dos participantes):**
  - JDK 17+
  - IDE (IntelliJ IDEA Community ou VS Code com extensões Java)
  - Git CLI
  - Maven ou Gradle
- **Padronização:** Dockerfile ou `devcontainer.json` para consistência (opcional)

**Ambiente de Staging/Homologação:**
- **Servidor de testes:**
  - **Opção 1:** Heroku (plano gratuito, limitado)
  - **Opção 2:** Servidor institucional (se disponível)
  - **Opção 3:** Docker local compartilhado via ngrok/tunelamento
- **Requisitos:**
  - Banco de dados de testes (PostgreSQL ou MySQL)
  - Deploy automatizado via CI/CD
  - Logs centralizados (ex: Papertrail, Loggly)
- **Acesso:** URL compartilhada para testes manuais

**Coleta e Armazenamento de Dados:**
- **Google Drive (criptografado):**
  - Planilhas para rastreamento de PRs, métricas, alocações
  - Armazenamento de questionários e transcrições
  - Backup diário automático
- **GitHub API:**
  - Scripts Python para extração de métricas (tempo de revisão, comentários, commits)
  - Biblioteca: `PyGithub` ou `requests`
- **SonarQube API:**
  - Extração de métricas de qualidade (complexidade, duplicação, issues)
  - Biblioteca: `requests` + autenticação via token

**Ferramentas de Análise:**
- **Estatística:**
  - R ou Python (pandas, scipy, statsmodels)
  - Jupyter Notebooks para análise exploratória
- **Visualização:**
  - Matplotlib, Seaborn (Python) ou ggplot2 (R)
  - Tableau Public (opcional, para gráficos de apresentação)

**Comunicação:**
- **Slack ou Discord:**
  - Canal dedicado ao experimento
  - Comunicação assíncrona entre participantes e pesquisador
- **Google Meet / Zoom:**
  - Reuniões semanais de sprint e entrevistas
- **Email:**
  - Comunicações formais (consentimento, cronograma)

**Backup e Redundância:**
- **Dados críticos:**
  - Backup diário automático do Google Drive para disco externo local
  - Repositório Git clonado localmente toda semana
- **Código de análise:**
  - Versionado em repositório Git separado (privado)

**Checklist de infraestrutura (pré-operação):**
- [ ] Repositório GitHub criado com permissões configuradas
- [ ] SonarQube configurado e integrado ao GitHub
- [ ] GitHub Actions workflows testados e funcionais
- [ ] Ambiente de staging disponível e acessível
- [ ] Scripts de coleta de dados desenvolvidos e validados
- [ ] Google Drive estruturado com pastas e permissões
- [ ] Canal de comunicação criado e participantes adicionados
- [ ] Backup automatizado configurado e testado

---

### 15.3 Materiais e insumos

**Materiais digitais (templates e formulários):**

1. **Termo de Consentimento Livre e Esclarecido (TCLE)**
   - Formato: PDF e Google Forms (assinatura digital)
   - Versões: 2 vias (participante + arquivo)

2. **Checklist de Revisão Manual**
   - Formato: Markdown ou PDF
   - Conteúdo: 15-20 itens categorizados (lógica, segurança, legibilidade, boas práticas)
   - Distribuição: Anexado a cada PR do grupo T1

3. **Questionário Pós-Experimento**
   - Formato: Google Forms
   - Perguntas: ~20 itens (escala Likert + abertas)
   - Tempo estimado: 10 minutos
   - Seções: Satisfação, confiança, aprendizado, feedback qualitativo

4. **Roteiro de Entrevista Semi-Estruturada**
   - Formato: Documento Word/Google Docs
   - Perguntas: 8-10 questões abertas
   - Duração: 15-20 minutos por participante
   - Tópicos: Experiência com os métodos, percepção de qualidade, sugestões de melhoria

5. **Guia de Treinamento (Onboarding)**
   - Formato: Slide deck (Google Slides ou PowerPoint)
   - Conteúdo:
     - Visão geral do experimento (10 slides)
     - Como usar SonarQube (5 slides)
     - Protocolo de revisão manual (5 slides)
     - Fluxo de trabalho esperado (3 slides)
   - Sessão: 45 minutos presencial ou via videoconferência

6. **Template de Pull Request**
   - Formato: Markdown (`.github/PULL_REQUEST_TEMPLATE.md`)
   - Campos: Descrição da feature, checklist de auto-revisão, issues relacionados, tipo de mudança

7. **Planilha de Rastreamento de PRs**
   - Formato: Google Sheets
   - Colunas: PR_ID, Autor, Revisor, LOC, Bloco, Tratamento, Data_Abertura, Data_Merge, Defeitos_Encontrados, Tempo_Revisão, etc.
   - Compartilhamento: Apenas leitura para participantes

8. **Scripts de Coleta de Dados**
   - Formato: Python (`.py`) ou Jupyter Notebook (`.ipynb`)
   - Funções:
     - `coletar_metricas_github(pr_number)` — extrai timestamps, comentários, commits
     - `coletar_metricas_sonarqube(project_key)` — extrai complexidade, duplicação, issues
     - `calcular_densidade_defeitos(pr_id)` — normaliza defeitos por LOC
   - Repositório: GitHub privado separado

9. **Documento de Protocolo Operacional**
   - Formato: Markdown ou Google Docs
   - Conteúdo: Passo a passo detalhado do experimento (seção 11.3)
   - Versão: Impressa e digital

**Materiais físicos (se aplicável):**

- **Impressões:**
  - TCLE (2 vias por participante) — 12 páginas total
  - Checklist de revisão manual (1 por participante) — 6 páginas
  - Guia rápido de SonarQube (1 por participante) — 4 páginas
- **Total de impressões:** ~22 páginas (custo estimado: R$ 5,00)

**Licenças de software:**

| Software | Licença | Custo | Justificativa |
|---|---|---|---|
| **SonarCloud** | Gratuita (educacional) | R$ 0 | Projeto acadêmico; repositório privado |
| **GitHub** | Gratuita (educacional) | R$ 0 | Conta educacional; uso pessoal |
| **Google Workspace** | Gratuita (institucional) | R$ 0 | Email institucional fornece acesso |
| **Heroku** | Gratuita (hobby tier) | R$ 0 | Staging simples; limitações aceitáveis |
| **JetBrains IntelliJ** | Gratuita (Community) | R$ 0 | IDE padrão; licença open-source |
| **Microsoft Office** | Institucional | R$ 0 | Licença fornecida pela universidade |

**Dispositivos:**

- **Computadores dos participantes:**
  - Requisitos mínimos: i5, 8 GB RAM, 50 GB disco livre
  - Verificação: Checklist pré-experimento
- **Servidor (se self-hosted SonarQube):**
  - VM institucional ou instância AWS/GCP (se disponível via créditos educacionais)
  - Custo estimado: R$ 0 (créditos) ou R$ 50-100/mês (se pago)

**Contingência para indisponibilidade de materiais:**
- Se SonarCloud não for aprovado: usar SonarQube Community local
- Se Heroku falhar: usar Docker local + ngrok para staging
- Se impressões não forem viáveis: distribuir tudo digitalmente

---

### 15.4 Orçamento e custos estimados

**Premissas:**
- Experimento acadêmico sem financiamento externo
- Uso de ferramentas gratuitas sempre que possível
- Infraestrutura institucional aproveitada
- Trabalho voluntário de participantes (sem remuneração)

**Categorias de custo:**

**1. Recursos Humanos (horas-pessoa):**

| Recurso | Horas/Semana | Semanas | Total Horas | Custo/Hora (referência) | Custo Total |
|---|---|---|---|---|---|
| Pesquisador Principal | 12 | 10 | 120 | R$ 0 (voluntário) | R$ 0 |
| Orientador | 2 | 10 | 20 | R$ 0 (institucional) | R$ 0 |
| Participantes (6×4h) | 24 | 8 | 192 | R$ 0 (disciplina) | R$ 0 |
| Assistente de Pesquisa | 3 | 8 | 24 | R$ 0 (voluntário) | R$ 0 |
| **Total** | - | - | **356** | - | **R$ 0** |

*Nota: Se fossem remunerados (R$ 50/hora em média), custo seria ~R$ 17.800*

**2. Infraestrutura e Serviços:**

| Item | Tipo | Custo Mensal | Meses | Custo Total |
|---|---|---|---|---|
| SonarCloud | Gratuito (educacional) | R$ 0 | 2 | R$ 0 |
| GitHub | Gratuito (educacional) | R$ 0 | 2 | R$ 0 |
| Heroku (staging) | Gratuito (hobby tier) | R$ 0 | 2 | R$ 0 |
| Google Drive | Institucional (ilimitado) | R$ 0 | 2 | R$ 0 |
| Internet (participantes) | Pessoal | R$ 0 (assumido) | 2 | R$ 0 |
| Servidor institucional | Institucional | R$ 0 | 2 | R$ 0 |
| **Total** | - | - | - | **R$ 0** |

*Contingência: Se precisar usar serviços pagos (ex: AWS), custo estimado ~R$ 200*

**3. Materiais e Insumos:**

| Item | Quantidade | Custo Unitário | Custo Total |
|---|---|---|---|
| Impressões (TCLE, guias) | 22 páginas × 6 participantes | R$ 0,40/pág | R$ 52,80 |
| Pen drive (backup) | 1 (32 GB) | R$ 30,00 | R$ 30,00 |
| Certificados de participação | 6 (impressos) | R$ 5,00 | R$ 30,00 |
| Encadernação (relatório final) | 2 cópias | R$ 15,00 | R$ 30,00 |
| **Total** | - | - | **R$ 142,80** |

**4. Despesas Eventuais:**

| Item | Descrição | Custo Estimado |
|---|---|---|
| Transporte (reuniões presenciais) | 4 deslocamentos × R$ 10 | R$ 40,00 |
| Café/água (reuniões) | 4 reuniões × R$ 20 | R$ 80,00 |
| Taxa de submissão ao CEP | (Se aplicável) | R$ 0 (geralmente gratuito) |
| **Total** | - | **R$ 120,00** |

**Resumo do orçamento:**

| Categoria | Custo |
|---|---|
| Recursos Humanos | R$ 0 (voluntário) |
| Infraestrutura | R$ 0 (gratuito/institucional) |
| Materiais | R$ 142,80 |
| Despesas Eventuais | R$ 120,00 |
| **Total Geral** | **R$ 262,80** |

**Fonte de financiamento:**
- **Recursos próprios do pesquisador:** R$ 262,80
- **Contingência adicional:** R$ 200,00 (reserva para imprevistos)
- **Total disponível:** R$ 462,80

**Sensibilidade de custos:**
- Se SonarCloud não funcionar e precisar usar AWS: +R$ 200,00
- Se precisar remunerar assistente de pesquisa: +R$ 1.200,00 (24h × R$ 50/h)
- Se aumentar número de participantes para 10: +R$ 100,00 (materiais)


**Não incluído neste orçamento:**
- Custos de publicação em conferências/journals (futuro; fora do escopo do TCC)
- Equipamentos dos participantes (assumidos como já disponíveis)
- Conexão de internet (custo pessoal/institucional assumido)

---

## 16. Cronograma, marcos e riscos operacionais

### 16.1 Macrocronograma (até o início da execução)

**Cronograma detalhado (fase pré-execução):**

| Semana | Marco Principal | Atividades | Responsável | Entregável | Status |
|---|---|---|---|---|---|
| **-12** | Início do planejamento | • Definir escopo e objetivos<br>• Revisar literatura<br>• Esboçar desenho experimental | Pesquisador + Orientador | Esboço inicial do plano | ✅ Concluído |
| **-11** | Refinamento metodológico | • Definir variáveis e hipóteses<br>• Escolher testes estatísticos<br>• Calcular tamanho de amostra | Pesquisador | Seções 7 e 8 do plano | ✅ Concluído |
| **-10** | Desenho operacional | • Definir protocolo experimental<br>• Criar instrumentos (questionários, checklist)<br>• Preparar templates | Pesquisador | Seções 9, 10, 11 do plano | ✅ Concluído |
| **-9** | Finalização do plano | • Revisar plano completo<br>• Validar com orientador<br>• Ajustes finais | Pesquisador + Orientador | **Plano v3.0** | ✅ Concluído |
| **-8** | Submissão ao CEP | • Preparar documentação CEP<br>• Submeter via Plataforma Brasil<br>• Solicitar aprovações institucionais | Pesquisador | Protocolo submetido | ⏳ A fazer |
| **-7** | Preparação técnica | • Configurar repositório GitHub<br>• Instalar e configurar SonarQube<br>• Desenvolver scripts de coleta | Pesquisador + TI | Infraestrutura pronta | ⏳ A fazer |
| **-6** | Aguardar CEP | • Acompanhar análise do CEP<br>• Responder pendências (se houver)<br>• Testar ferramentas | Pesquisador | - | ⏳ A fazer |
| **-5** | Recrutamento | • Apresentar estudo à turma<br>• Distribuir TCLE<br>• Coletar consentimentos | Pesquisador + Assistente | Lista de participantes | ⏳ A fazer |
| **-4** | Treinamento | • Sessão de onboarding (2h)<br>• Apresentar SonarQube<br>• Explicar protocolo de revisão | Pesquisador | Participantes treinados | ⏳ A fazer |
| **-3** | Preparação final | • Revisar instrumentos<br>• Testar CI/CD completo<br>• Criar planilhas de rastreamento | Pesquisador | Checklist de prontidão | ⏳ A fazer |
| **-2** | Validação pré-piloto | • Validar com orientador<br>• Conferir aprovações<br>• Comunicar cronograma | Pesquisador | **Go/No-Go checkpoint** | ⏳ A fazer |
| **-1** | **Piloto** | • Executar piloto com 2 PRs<br>• Coletar feedback<br>• Ajustar protocolo se necessário | Todos | Relatório de piloto | ⏳ A fazer |
| **0** | **Início da execução** | • Sprint 1 começa<br>• Primeiros PRs abertos<br>• Coleta de dados inicia | Todos | Experimento em operação | ⏳ A fazer |

**Marcos críticos (Gates):**

1. **G1 (Semana -9): Plano aprovado** — Orientador valida plano completo
2. **G2 (Semana -5): CEP aprovado** — Autorização ética obtida
3. **G3 (Semana -2): Infraestrutura validada** — Todos os sistemas testados e funcionais
4. **G4 (Semana -1): Piloto bem-sucedido** — Protocolo validado; ajustes finalizados
5. **G5 (Semana 0): Go final para operação** — Todos os critérios de prontidão atingidos

**Datas estimadas (assumindo início em fevereiro/2026):**

| Marco | Data Estimada |
|---|---|
| Início do planejamento (Sem -12) | 25/11/2025 (histórico) |
| Submissão ao CEP (Sem -8) | 23/12/2025 |
| Aprovação CEP (Sem -5) | 13/01/2026 |
| Treinamento de participantes (Sem -4) | 20/01/2026 |
| Piloto (Sem -1) | 10/02/2026 |
| **Início da operação (Sem 0)** | **17/02/2026** |
| Término da coleta (Sem 8) | 14/04/2026 |
| Análise completa (Sem 12) | 12/05/2026 |

---
**Cronograma de comunicações:**

| Fase | Veículo | Conteúdo | Tempo |
|---|---|---|---|
| **Divulgação** | Apresentação em sala + E-mail | "Convite para participar de estudo de code review" | Semana 0, dia 0 |
| **Pré-screening** | E-mail + Link Google Forms | "Preencha formulário de pré-screening" | Semana 0, dia 2 |
| **Resultado pré-screening** | E-mail individual | "Você foi pré-selecionado! Agende entrevista." | Semana 0, dia 4 |
| **TCLE** | E-mail + PDF | "Termo de Consentimento — leia e traga assinado" | Semana 0, dia 6 |
| **Confirmação** | E-mail + Slack/Teams | "Bem-vindo! Treinamento na próxima segunda." | Semana 0, dia 7 |
| **Lembretes** | Slack/Teams | Lembretes semanais durante experimento | Semanal |
| **Feedback** | E-mail + Reunião | Resumo de resultados (mantendo cegamento) | Após experimento |

---

### 16.2 Dependências entre atividades

**Mapa de dependências (precedência):**
```mermaid
flowchart TD

    A["Plano Finalizado"]

    A --> B["Submissão ao CEP"]
    B --> C["Aprovação CEP"]

    B --> D["Aprovação
Institucional (TI)"]

    C --> F["Recrutamento +
Consentimento"]
    D --> F

    F --> G["Treinamento"]
    G --> H["Piloto"]
    H --> I["Início Operação"]

    %% ===========================
    %% ESTILOS DE CORES
    %% ===========================
    classDef main fill:#e3f2fd,stroke:#1565c0,stroke-width:2px,color:#0d47a1,rx:10,ry:10;
    classDef approve fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px,color:#1b5e20,rx:10,ry:10;
    classDef prep fill:#f3e5f5,stroke:#8e24aa,stroke-width:2px,color:#6a1b9a,rx:10,ry:10;
    classDef ops fill:#fff3e0,stroke:#ef6c00,stroke-width:2px,color:#e65100,rx:10,ry:10;

    %% Aplicar estilos
    class A main;
    class B,C,D approve;
    class F prep;
    class G,H,I ops;
```

**Tabela de dependências críticas:**

| Atividade (Dependente) | Depende de | Tipo de Dependência | Folga | Impacto se atrasar |
|---|---|---|---|---|
| **Submissão ao CEP** | Plano finalizado | Finish-to-Start (FS) | 0 dias | Atrasa todo cronograma |
| **Recrutamento** | Aprovação CEP | FS | 0 dias | Não pode iniciar sem aprovação ética |
| **Treinamento** | Recrutamento + Infra técnica | FS | 3 dias | Pode ser adiantado se infra pronta antes |
| **Piloto** | Treinamento + Aprovação TI | FS | 0 dias | Piloto inválido sem treinamento |
| **Início operação** | Piloto + Ajustes + TCLE assinado | FS | 0 dias | Critério de prontidão não atendido |
| **Configuração SonarQube** | Aprovação TI | FS | 7 dias | Pode ser feito em paralelo com CEP |
| **Desenvolvimento de scripts** | Infra técnica | FS | 5 dias | Pode iniciar com ambientes de teste |
| **Ajustes pós-piloto** | Feedback do piloto | FS | 2 dias | Pode ser acelerado se poucos ajustes |

**Atividades paralelas (podem acontecer simultaneamente):**

- Análise do CEP **||** Preparação técnica (configuração de servidores, scripts)
- Recrutamento **||** Finalização de instrumentos (questionários)
- Treinamento **||** Testes de integração CI/CD

**Caminho crítico (Critical Path):**
Plano → CEP → Aprovação CEP → Recrutamento → Treinamento → Piloto → Operação

**Duração total do caminho crítico:** 12 semanas (não pode ser reduzida sem comprometer qualidade)

**Folgas identificadas:**
- Configuração de SonarQube: +7 dias (pode ser feita enquanto aguarda CEP)
- Desenvolvimento de scripts: +5 dias (pode ser feito com dados mock)
- Revisão de instrumentos: +3 dias (pode ser feita até o piloto)

**Estratégias para reduzir dependências:**

1. **Antecipação de atividades não-críticas:**
   - Iniciar configuração técnica antes da aprovação do CEP (usar ambiente de teste)
   - Desenvolver scripts de coleta com dados simulados

2. **Paralelização agressiva:**
   - Submeter aprovação institucional (TI) em paralelo com CEP
   - Preparar materiais de treinamento durante análise do CEP

3. **Fast-tracking:**
   - Se CEP atrasar, iniciar recrutamento informal (apresentar estudo, mas não coletar consentimento)
   - Treinar participantes em ferramentas gerais (Git, GitHub) antes da aprovação formal

---

### 16.3 Riscos operacionais e plano de contingência

**Categorização de riscos:**

**1. Riscos de Cronograma**

| ID | Risco | Probabilidade | Impacto | Severidade | Contingência |
|---|---|---|---|---|---|
| **RC1** | Atraso na aprovação do CEP (>30 dias) | Alta (60%) | Alto | 🔴 Crítico | • Submeter com 2 meses de antecedência<br>• Ter documentação impecável<br>• Contato proativo com CEP<br>• Se atrasar >45 dias: adiar experimento para próximo semestre |
| **RC2** | Feriados ou greves afetam calendário acadêmico | Média (30%) | Médio | 🟡 Moderado | • Incluir buffer de 2 semanas no cronograma<br>• Monitorar comunicados institucionais<br>• Ter cronograma flexível (8-10 semanas) |
| **RC3** | Participantes desistem ou ficam indisponíveis | Média (40%) | Alto | 🔴 Crítico | • Recrutar 8 participantes para garantir 6 ativos<br>• Ter lista de suplentes<br>• Manter engajamento com comunicação constante |
| **RC4** | Piloto revela necessidade de grandes mudanças | Baixa (20%) | Médio | 🟡 Moderado | • Planejar 2 semanas para ajustes pós-piloto<br>• Ter orientador revisando protocolo antes do piloto<br>• Limitar mudanças ao essencial |

**2. Riscos Técnicos**

| ID | Risco | Probabilidade | Impacto | Severidade | Contingência |
|---|---|---|---|---|---|
| **RT1** | SonarCloud rejeita projeto (não qualifica como educacional) | Baixa (15%) | Alto | 🔴 Crítico | • Aplicar com antecedência<br>• Ter plano B: SonarQube self-hosted<br>• Reservar servidor institucional ou usar Docker local |
| **RT2** | GitHub Actions excede quota gratuita | Média (30%) | Médio | 🟡 Moderado | • Monitorar uso semanal<br>• Otimizar workflows (rodar apenas em PRs, não em todos os pushes)<br>• Usar conta GitHub Teams (maior quota) |
| **RT3** | Falhas intermitentes em CI/CD | Alta (50%) | Baixo | 🟢 Baixo | • Configurar retry automático em workflows<br>• Ter logs detalhados<br>• Política: re-executar análise em caso de falha |
| **RT4** | Ambiente de staging inacessível ou instável | Média (35%) | Médio | 🟡 Moderado | • Ter ambiente local como backup<br>• Usar Docker Compose para replicar staging<br>• Documentar setup para recuperação rápida |
| **RT5** | Perda de dados (corrupção, exclusão acidental) | Baixa (10%) | Alto | 🔴 Crítico | • Backup diário automático (Google Drive + disco local)<br>• Versionamento de planilhas (histórico do Google Sheets)<br>• Repositório Git para scripts e dados coletados |

**3. Riscos de Pessoas**

| ID | Risco | Probabilidade | Impacto | Severidade | Contingência |
|---|---|---|---|---|---|
| **RP1** | Baixa adesão ao protocolo (participantes ignoram instruções) | Alta (55%) | Alto | 🔴 Crítico | • Treinamento robusto com exemplos práticos<br>• Checklist obrigatório em cada PR<br>• Monitoramento semanal de conformidade<br>• Feedback imediato quando protocolo violado |
| **RP2** | Conflitos entre participantes (revisões conflituosas) | Baixa (15%) | Médio | 🟡 Moderado | • Código de conduta claro<br>• Revisões focadas em código, não em pessoas<br>• Mediação do pesquisador se necessário |
| **RP3** | Carga excessiva percebida pelos participantes | Média (40%) | Médio | 🟡 Moderado | • Comunicar claramente expectativas (4-6h/semana)<br>• Integrar ao trabalho normal da disciplina<br>• Oferecer suporte técnico rápido<br>• Permitir redução de escopo se necessário |
| **RP4** | Pesquisador fica indisponível (doença, emergência) | Baixa (10%) | Alto | 🟡 Moderado | • Assistente de pesquisa treinado como backup<br>• Protocolo documentado para continuidade<br>• Orientador pode assumir temporariamente |

**4. Riscos de Qualidade de Dados**

| ID | Risco | Probabilidade | Impacto | Severidade | Contingência |
|---|---|---|---|---|---|
| **RD1** | Poucos defeitos encontrados (N < 10 total) | Média (30%) | Alto | 🔴 Crítico | • Testes rigorosos em staging<br>• Ampliar definição de "defeito" (incluir code smells severos)<br>• Estender período de coleta<br>• Análise qualitativa se dados insuficientes |
| **RD2** | Dados faltantes (>20% de valores ausentes) | Média (35%) | Médio | 🟡 Moderado | • Validação em tempo real (alertas automáticos)<br>• Dupla verificação semanal<br>• Imputação estatística se padrão missing at random |
| **RD3** | Viés de Hawthorne muito forte (todos melhoram igualmente) | Alta (60%) | Médio | 🟡 Moderado | • Análise de tendência temporal<br>• Comparação com dados históricos (se disponíveis)<br>• Foco em diferenças relativas entre T1 e T2 |
| **RD4** | Desbalanceamento severo entre grupos (N_T1 << N_T2) | Baixa (20%) | Médio | 🟡 Moderado | • Randomização com restrição (seção 9.2)<br>• Monitoramento semanal de balanço<br>• Usar ANCOVA se desbalanceamento ocorrer |

**5. Riscos Éticos**

| ID | Risco | Probabilidade | Impacto | Severidade | Contingência |
|---|---|---|---|---|---|
| **RE1** | Participante se sente exposto ou constrangido | Média (25%) | Alto | 🟡 Moderado | • Anonimização rigorosa<br>• Feedback privado e construtivo<br>• Canal confidencial para relatar desconforto<br>• Permitir retirada imediata sem penalização |
| **RE2** | Vazamento de dados pessoais | Baixa (5%) | Alto | 🔴 Crítico | • Criptografia de dados<br>• Acesso restrito (2FA)<br>• Conformidade LGPD<br>• Plano de resposta a incidentes (notificação em 24h) |
| **RE3** | Pressão percebida para participar (coerção implícita) | Média (30%) | Médio | 🟡 Moderado | • Coleta de consentimento por terceiro<br>• Enfatizar voluntariedade<br>• Oferecer alternativas equivalentes |

**Plano de resposta a riscos (geral):**

1. **Monitoramento contínuo:**
   - Checklist semanal de riscos
   - Dashboard de métricas operacionais (adesão, dados coletados, infraestrutura)
   - Reuniões de retrospectiva ao final de cada sprint

2. **Gatilhos de ação:**
   - Se 3+ riscos críticos (🔴) se materializarem: pausar experimento e reavaliar
   - Se N < 30 PRs na semana 6: estender período de coleta
   - Se adesão < 60%: reunião emergencial com participantes

3. **Comunicação de riscos:**
   - Riscos críticos comunicados imediatamente ao orientador
   - Riscos moderados reportados em reuniões semanais
   - Log de riscos mantido em Google Sheets compartilhado

4. **Lições aprendidas:**
   - Documentar todos os problemas e soluções aplicadas
   - Retrospectiva final para melhorar futuros experimentos

---




