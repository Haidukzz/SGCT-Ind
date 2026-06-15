# SGCT-Ind
> **Sistema de Sequenciamento e Gerenciamento de Carga de Trabalho Industrial**

O **SGCT-Ind** é um sistema desenvolvido para automatizar o sequenciamento de ordens de fabricação (OF), equilibrar a carga de trabalho entre as máquinas e monitorar o chão de fábrica em tempo real. O objetivo principal é substituir o controle manual e o uso de planilhas locais por uma solução centralizada e automática, rodando diretamente na Fábrica 3 da WEG em Jaraguá do Sul.

---

## 🛠️ Como o sistema é estruturado (Tecnologias)

Para garantir que o sistema seja rápido e não trave, a arquitetura foi dividida em 5 camadas bem definidas:

* **Apresentação (Front-end):** Telas e dashboards interativos desenvolvidos em **React**, feitos para os supervisores e gestores acompanharem o andamento do chão de fábrica.
* **API (Back-end):** Construída com **FastAPI (Python)** usando programação assíncrona. Essa camada gerencia as requisições HTTP padrão (REST) e mantém canais de comunicação abertos via **WebSocket** para enviar os dados de telemetria na hora.
* **Lógica de Negócio (Otimização):** É o coração do sistema. Ele usa o resolvedor **CP-SAT do Google OR-Tools** para calcular a sequência ótima de produção, levando em conta os tempos de setup e as restrições das máquinas.
* **Dados:** Combina o **PostgreSQL** para salvar com segurança os dados brutos e históricos (como o cadastro de ordens e usuários) com o **Redis**, que roda em memória para atualizar o status instantâneo das máquinas sem pesar o sistema.
* **Integração:** Conectores desenvolvidos especificamente para trocar dados de forma limpa com os sistemas corporativos de nível superior já usados na empresa (**ERP e MES**).

---

## 📊 Resultados Esperados

A lógica dos algoritmos foi testada em um ambiente de simulação utilizando uma base histórica real de 1.200 ordens de fabricação da Fábrica 3. Em comparação com o controle manual atual, os resultados projetados são:
* 📉 **Redução de 16,4%** no tempo total de processamento (*Makespan*).
* 📦 **Redução de até 21%** no estoque parado entre os processos (*Work in Process - WIP*).
* 📈 **Aumento para 35%** no índice de entregas no prazo (*On-Time Delivery - OTD*).

---

## 📅 Plano de Desenvolvimento (6 Meses)

O projeto está planejado para acontecer ao longo de 24 semanas, dividido nas seguintes etapas técnicas:
* **Mês 1:** Mapeamento do processo atual e levantamento de todos os requisitos de software.
* **Mês 1 e 2:** Modelagem do banco de dados e configuração inicial do PostgreSQL e do Redis.
* **Mês 2, 3 e 4:** Desenvolvimento do back-end e das rotas assíncronas na API com FastAPI.
* **Mês 3 e 4:** Programação das regras de negócio e restrições de setup usando o OR-Tools CP-SAT.
* **Mês 4 e 5:** Construção das telas e componentes visuais do dashboard em React.
* **Mês 5 e 6:** Integração entre o front-end e o back-end através de WebSockets, seguido por testes de carga.
* **Mês 6:** Instalação do sistema e homologação final.

---
