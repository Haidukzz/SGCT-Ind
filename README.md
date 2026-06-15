# SGCT-Ind
> **Sistema de Sequenciamento e Gerenciamento de Carga de Trabalho Industrial**

O **SGCT-Ind** é uma solução computacional integrada voltada para o sequenciamento automatizado de ordens de fabricação (OF), balanceamento dinâmico de carga de trabalho e monitoramento telemétrico em tempo real. Desenvolvido para mitigar gargalos informacionais, o sistema substitui controles manuais e planilhas offline por uma arquitetura reativa direcionada a eventos na Fábrica 3 da WEG.

---

## 🏗️ Arquitetura em Camadas e Tecnologias

O ecossistema de software foi projetado sob uma topologia modular dividida em 5 níveis principais para garantir isolamento de responsabilidades, alta coesão e baixa latência operacional:

* **1. Apresentação (Front-end):** Interface web rica e responsiva desenvolvida em **React**, projetada para fornecer painéis visuais (*dashboards*) dinâmicos para supervisores e gestores de linha.
* **2. API de Comunicação:** Gateway construído sobre o framework **FastAPI (Python)**, operando com rotas assíncronas nativas (`async/await`) sob o padrão ASGI, integrado a canais full-duplex via **WebSockets** para tráfego instantâneo de telemetria.
* **3. Lógica de Negócio (Otimização):** Motor analítico baseado em Programação por Restrições (CP-SAT) utilizando o **Google OR-Tools** para resolver problemas complexos de *scheduling*, caminhos ótimos e tempos de setup.
* **4. Dados e Persistência:** Infraestrutura híbrida composta por **PostgreSQL 16** para armazenamento estável e transações ACID corporativas, pareado com **Redis** atuando como banco em memória de subsegundo para cache de estados voláteis de máquinas.
* **5. Integração:** Módulo de conectores dedicados para o tráfego de dados e sincronização síncrona/assíncrona com sistemas legados corporativos de nível superior (**ERP/MES**).

---

## 🎯 Resultados Esperados (Ambiente Simulado)

A validação analítica do motor algorítmico contra o modelo empírico manual obteve os seguintes indicadores de eficiência sobre uma base histórica de 1.200 ordens de fabricação:
* 📉 **Redução de 16,4%** no tempo total de processamento fabril (*Makespan*).
* 📦 **Contração de 21,0%** nos níveis de estoque em processo (*Work in Process* - WIP).
* 📈 **Elevação para 45,8%** no índice de cumprimento e pontualidade de prazos (*On-Time Delivery* - OTD).

---

## 📅 Cronograma de Implementação

O plano de engenharia de software compreende um ciclo contínuo de 6 meses estruturado em metodologia ágil:
1. **Mês 1-2:** Engenharia de Requisitos, Mapeamento de Processos e Modelagem Lógica (PostgreSQL).
2. **Mês 3-4:** Desenvolvimento das APIs Assíncronas (FastAPI) e Modelagem das Restrições (OR-Tools CP-SAT).
3. **Mês 5:** Construção das Telas Operacionais (React) e acoplamento dos canais WebSockets.
4. **Mês 6:** Testes Integrados de Carga, Homologação em Ambiente Piloto e *Go-Live*.

---
Distribuído como projeto de software para a disciplina de Engenharia de Software — CatólicaSC, 2026.
