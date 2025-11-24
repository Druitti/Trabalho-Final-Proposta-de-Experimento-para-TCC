
# Plano de Experimento – Scoping e Planejamento

## 1. Identificação básica

### 1.1 Título do experimento
Comparação entre revisão de código manual (peer review) e revisão automatizada por SonarQube na redução da densidade de defeitos em projetos Java.

### 1.2 ID / código
EXP-SE-001

### 1.3 Versão do documento e histórico de revisão
- **Versão atual:** v1.0  
- **Histórico:**  
  - v1.0 — criação inicial do documento, contendo escopo e fundamentos teóricos.

### 1.4 Datas (criação, última atualização)
- **Data de criação:** 23/11/2025  
- **Última atualização:** 23/11/2025

### 1.5 Autores (nome, área, contato)
- **Autor:** [Gabriel Ferreira Amaral] — Engenharia de Software — gabriel.afa@outlook.com

### 1.6 Responsável principal (PI / dono do experimento)
[Nome do orientador] — responsável pelo direcionamento científico do estudo.

### 1.7 Projeto / produto / iniciativa relacionada
Projeto acadêmico de desenvolvimento de software em Java, vinculado à disciplina de Engenharia de Software e ao Trabalho de Conclusão de Curso (TCC).  
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

---
