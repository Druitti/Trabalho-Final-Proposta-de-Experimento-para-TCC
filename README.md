
# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento
Comparação entre revisão de código manual (peer review) e revisão automatizada por SonarQube na redução da densidade de defeitos em projetos Java.

### 1.2 ID / código
EXP-SE-001

### 1.3 Versão do documento e histórico de revisão
- **Versão atual:** v3.0  
- **Histórico:**  
  - v1.0 — criação inicial do documento, contendo escopo e fundamentos teóricos.
  - v2.0 — expansão com objetivos específicos, GQM, stakeholders e riscos.
  - v3.0 — modelo conceitual e hipóteses; variáveis, fatores, tratamentos e objetos de estudo; desenho experimental
  - v3.1 — ajustes de precisão nas métricas e operacionalização de critérios.

### 1.4 Datas (criação, última atualização)
- **Data de criação:** 23/11/2025  
- **Última atualização:** 25/11/2025

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
│                    Tipo de Revisão de Código                │
│                    (Variável Independente)                  │
└──────────────────────┬──────────────────────────────────────┘
                       │ 
        ┌──────────────┴──────────────┐
        │                             │
        ▼                             ▼
┌──────────────────┐        ┌──────────────────┐
│ Revisão Manual   │        │ SonarQube (Auto) │
│  (Peer Review)   │        │    (Análise      │   
│                  │        │    Estática)     │
└────────┬─────────┘        └────────┬─────────┘
         ▼                           ▼
         │                         │
         │ Detecta:                │ Detecta:              │
         │ • Lógica complexa       │ • Padrões estruturais │
         │ • Contexto de negócio   │ • Vulnerabilidades    │
         │ • Casos extremos        │ • Complexidade        │
         │ • Design patterns       │ • Duplicação          │
         │                         │ • Code smells         │
         │                         │───────────────────────┘
         └───────────┬─────────────┘
                     │  
                     ▼
         ┌────────────────────────────┐
         │ Qualidade do Código        │
         │  (Métrica Primária)        │
         │                            │
         │ • Densidade de Defeitos    │
         │   (M1: defeitos/KLOC)      │
         │ • Taxa de Críticos (M2)    │
         │ • Defeitos Pós-Entrega     │
         │   (M3)                     │
         └──────────────┬─────────────┘
                        │
                        ▼
         ┌────────────────────────────┐
         │  Resultado Final           │
         │  (Efeito Observado)        │
         │                            │
         │ Redução de Defeitos        │
         │ em Produção?               │
         └────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│  Variáveis Moderadoras / Contexto                           │
│  • Experiência dos desenvolvedores (M14: Confiança)         │
│  • Complexidade do código (M8: Complexidade Ciclomática)    │ 
│  • Tamanho do PR (linhas modificadas)                       │ 
│  • Criticidade da funcionalidade                            │
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
| **CF3** | **Familiaridade com SonarQube** | Desenvolvedores aprendem a "burlar" ou ignorar warnings da ferramenta | Reduz efetividade do tratamento T2 ao longo do experimento | • Treinamento inicial sobre importância das regras <br> • Quality gate rígido (não permite merge com issues críticos) <br> • Auditoria aleatória de PRs | Taxa de issues ignorados ou suprimidos |
| **CF4** | **Viés de Seleção de Tarefas** | Tarefas mais complexas podem ser alocadas desproporcionalmente a um grupo | Grupo com tarefas mais difíceis apresenta mais defeitos por natureza da tarefa | • Randomização da alocação de PRs <br> • Bloqueio por complexidade (VC2) <br> • Registro da complexidade percebida | Verificação de balanceamento pós-alocação |
| **CF5** | **Diferenças entre Revisores** | Revisores manuais têm estilos e níveis de rigor diferentes | Variabilidade na qualidade da revisão manual (T1) | • Treinamento padronizado <br> • Checklist obrigatório (VC5) <br> • Rodízio de revisores entre PRs <br> • Auditoria de amostra de revisões | Análise de concordância inter-revisor |
| **CF6** | **Carga de Trabalho Variável** | Desenvolvedores podem estar mais ou menos ocupados em momentos diferentes | Qualidade do código pode cair sob pressão de prazo | • Distribuir PRs uniformemente ao longo das sprints <br> • Monitorar carga de trabalho via retrospectivas | Registro de horas trabalhadas e número de tarefas simultâneas |
| **CF7** | **Comunicação Informal** | Desenvolvedores discutem código fora do processo oficial de revisão | Feedback informal pode compensar ausência de revisão formal em T2 | • Instruir equipe a documentar todas as discussões no PR <br> • Observação participante em reuniões | Análise de comunicação via Slack/Discord |
| **CF8** | **Qualidade dos Testes em Staging** | Testes de validação podem variar em rigor | Defeitos podem não ser detectados por testes fracos, não por falha do método de revisão | • Padronizar suíte de testes <br> • Cobertura mínima exigida (80%) <br> • Casos de teste pré-definidos para cada feature | Análise de cobertura de testes por PR |
| **CF9** | **Falhas Técnicas Temporárias** | SonarQube pode ficar indisponível; CI/CD pode falhar | PRs do grupo T2 podem não receber análise adequada | • Monitoramento de uptime do SonarQube <br> • Política de re-análise em caso de falha <br> • Backup de dados de análise | Logs de falhas técnicas com timestamps |
| **CF10** | **Motivação / Engajamento Diferencial** | Participantes podem gostar mais de um método que outro | Desenvolvedores podem se esforçar mais em revisões que consideram mais úteis | • Balancear exposição aos dois métodos <br> • Coletar dados de satisfação (VD10, VD11) <br> • Análise de correlação entre satisfação e qualidade | Questionários de motivação durante experimento |

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
```
┌─────────────────────────────────────────────────────────────┐
│                    População de PRs                          │
│                  (Todos os PRs do projeto)                   │
└──────────────────────┬──────────────────────────────────────┘
                       │
                       ▼
         ┌─────────────────────────────┐
         │  Estratificação em Blocos   │
         └─────────────┬───────────────┘
                       │
        ┌──────────────┼──────────────┐
        │              │              │
        ▼              ▼              ▼
   ┌─────────┐   ┌─────────┐   ┌─────────┐
   │ Bloco 1 │   │ Bloco 2 │   │ Bloco 3 │
   │(Pequeno)│   │ (Médio) │   │(Grande) │
   │50-150   │   │151-300  │   │301-500  │
   │  LOC    │   │  LOC    │   │  LOC    │
   └────┬────┘   └────┬────┘   └────┬────┘
        │             │             │
        │ Randomização│             │
        │  dentro do  │             │
        │    bloco    │             │
        ▼             ▼             ▼
   ┌────────┐    ┌────────┐    ┌────────┐
   │T1  │T2 │    │T1  │T2 │    │T1  │T2 │
   │(n) │(n)│    │(n) │(n)│    │(n) │(n)│
   └────────┘    └────────┘    └────────┘
   
   Legenda:
   T1 = Revisão Manual
   T2 = Revisão Automatizada (SonarQube)
   n = número aproximadamente igual de PRs por célula
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



