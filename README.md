
# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento
Comparação entre revisão de código manual (peer review) e revisão automatizada por SonarQube na redução da densidade de defeitos em projetos Java.

### 1.2 ID / código
EXP-SE-001

### 1.3 Versão do documento e histórico de revisão
- **Versão atual:** v2.0  
- **Histórico:**  
  - v1.0 — criação inicial do documento, contendo escopo e fundamentos teóricos.
  - v2.0 — expansão com objetivos específicos, GQM, stakeholders e riscos.

### 1.4 Datas (criação, última atualização)
- **Data de criação:** 23/11/2025  
- **Última atualização:** 24/11/2025

### 1.5 Autores (nome, área, contato)
- **Autor:** [Gabriel Ferreira Amaral] — Engenharia de Software — gabriel.afa@outlook.com

### 1.6 Responsável principal (PI / dono do experimento)
[Gabriel Ferriera Amaral] — responsável pelo direcionamento científico do estudo.

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

```
┌─────────────────────────────────────────────────────────────┐
│                    Tipo de Revisão de Código                    │
│                    (Variável Independente)                      │
└──────────────────────┬──────────────────────────────────────┘
                        │ 
        ┌──────────────┴──────────────┐
        │                               │
        ▼                               ▼
┌──────────────────┐        ┌─────────────────┐
│ Revisão Manual    │        │ SonarQube (Auto)  │
│  (Peer Review)    │        │    (Análise       │   
│                   │        │    Estática)      │
└────────┬─────────┘        └────────┬─────────┘
          ▼                            ▼
         │                         │
         │ Detecta:                │ Detecta:              │
         │ • Lógica complexa       │ • Padrões estruturais │
         │ • Contexto de negócio   │ • Vulnerabilidades    │
         │ • Casos extremos        │ • Complexidade        │
         │ • Design patterns       │ • Duplicação          │
         │                         │ • Code smells         │
         │                         │──────────────────────┘
         └───────────┬───────────┘
                      │  
                      ▼
         ┌──────────────────────────┐
         │ Qualidade do Código        │
         │  (Métrica Primária)        │
         │                            │
         │ • Densidade de Defeitos    │
         │   (M1: defeitos/KLOC)      │
         │ • Taxa de Críticos (M2)    │
         │ • Defeitos Pós-Entrega     │
         │   (M3)                     │
         └──────────────┬───────────┘
                         │
                         ▼
         ┌──────────────────────────┐
         │  Resultado Final           │
         │  (Efeito Observado)        │
         │                            │
         │ Redução de Defeitos        │
         │ em Produção?               │
         └──────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  Variáveis Moderadoras / Contexto                               │
│  • Experiência dos desenvolvedores (M14: Confiança)             │
│  • Complexidade do código (M8: Complexidade Ciclomática)        │ 
│  • Tamanho do PR (linhas modificadas)                           │ 
│  • Criticidade da funcionalidade                                │
└─────────────────────────────────────────────────────────────┘
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


---

