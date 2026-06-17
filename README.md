# 📚 Miniguia de Estudos: Monitoramento de Redes (Zabbix e TR-069) com NotebookLM

![Capa do Projeto](https://img.shields.io/badge/Status-Concluído-success?style=for-the-badge)
![Ferramenta](https://img.shields.io/badge/NotebookLM-Google-blue?style=for-the-badge&logo=google)
![Tema](https://img.shields.io/badge/Infraestrutura-Redes-orange?style=for-the-badge)

## 🎯 Contexto e Objetivos

Este repositório é o resultado de um projeto prático explorando a Inteligência Artificial (NotebookLM do Google) como ferramenta de aprendizagem ativa. O tema central escolhido para este caderno temático é a **Arquitetura de Monitoramento de Redes focada na integração de Zabbix, OLTs e o Protocolo TR-069**.

**Objetivos de Estudo:**
* Compreender o funcionamento do protocolo TR-069 no gerenciamento remoto de CPEs.
* Mapear como ferramentas como o Zabbix podem ser utilizadas para coletar métricas de equipamentos de rede (switches, roteadores e OLTs).
* Aplicar o NotebookLM para sintetizar documentações técnicas complexas e gerar guias de troubleshooting rápido para o suporte técnico.

---

## 🗂️ Curadoria de Fontes

Para alimentar a base de conhecimento do NotebookLM, foram selecionadas as seguintes fontes abertas e documentações oficiais (em PDF e Texto):

1. **Broadband Forum - CPE WAN Management Protocol (TR-069):** * **Tipo:** PDF Oficial.
   * **Descrição:** A especificação técnica oficial original do protocolo CWMP, detalhando a comunicação entre o ACS e a CPE, provisionamento dinâmico e diagnósticos remotos.
   * **Link da fonte:** [Acessar Especificação TR-069 (Broadband Forum)](https://www.broadband-forum.org/pdfs/tr-069-1-2-0.pdf)

2. **Documentação Oficial Zabbix - Monitoramento SNMP:** * **Tipo:** Documentação Web / Texto.
   * **Descrição:** Guia oficial de integração e coleta de dados (itens, triggers e templates) via Simple Network Management Protocol, essencial para capturar logs de switches e OLTs.
   * **Link da fonte:** [Acessar Zabbix SNMP Manual](https://www.zabbix.com/integrations/snmp)

3. **Dimensionamento e Cálculo de Atenuação em Redes Ópticas GPON:** * **Tipo:** Artigo Acadêmico / PDF.
   * **Descrição:** Material técnico acadêmico (USP/Unicamp) detalhando métricas físicas, divisores ópticos (splitters), cálculo de potência, atenuação de conectores e níveis de dBm críticos.
   * **Link da fonte:** [Acessar PDF sobre Atenuação (Repositório Aberto)](https://teses.usp.br/teses/disponiveis/18/18133/tde-22092005-205226/publico/Takeuti_Final.pdf)

4. **Huawei Enterprise - GPON OLT Configuration Guide (Referência Complementar):** * **Tipo:** Base de Conhecimento Web.
   * **Descrição:** Guias de suporte a equipamentos para entender na prática como fabricantes implementam limites lógicos e físicos de sinal na porta PON.
   * **Link da fonte:** [Acessar Fórum Huawei Enterprise](https://forum.huawei.com/enterprise/en/access-network/gpon/forum/100181)

---

## ⚙️ Engenharia de Prompts e "Cicatrizes" (Troubleshooting)

Nesta etapa, testei diferentes abordagens com a IA para extrair as melhores correlações entre os documentos fornecidos.

### 🔴 Teste 1: Abordagem Direta (Genérica)
* **Prompt testado:** *"O que é o protocolo TR-069 e como ele ajuda provedores de internet?"*
* **Resultado:** A IA gerou um resumo muito superficial, focando apenas no significado da sigla (CWMP) sem entrar na aplicação prática do dia a dia do suporte.
* **Cicatriz/Lição:** Prompts muito amplos em documentações técnicas geram respostas teóricas demais. Faltou contexto operacional.

### 🟡 Teste 2: Adicionando Contexto e Papel
* **Prompt testado:** *"Atuando como um analista de suporte técnico de redes, explique como o TR-069 interage com a OLT para o provisionamento de um novo cliente. Cite as principais vantagens em relação ao tempo de atendimento."*
* **Resultado:** Resposta muito melhor. A IA conseguiu relacionar a documentação do Broadband Forum com a redução do tempo de suporte (SLA), mencionando a configuração zero-touch.

### 🟢 Teste 3: Cruzamento de Fontes (O "Pulo do Gato")
* **Prompt testado:** *"Com base na documentação do Zabbix e nos manuais de GPON, crie uma tabela de correlação: quais métricas de uma rede óptica (como atenuação de sinal) eu devo priorizar no monitoramento do Zabbix para evitar indisponibilidades no cliente final?"*
* **Resultado:** Excelente. A IA conectou a teoria de redes ópticas com a prática de monitoramento, gerando alertas sugeridos para níveis de dBm críticos.

---

## 📖 Miniguia de Estudo (Entrega Final)

### 1. Resumos Estruturados do Assunto

**O Papel do TR-069 no Suporte Técnico:**
O TR-069 (CWMP) é o padrão ouro para comunicação entre um Auto Configuration Server (ACS) e os equipamentos do cliente (CPEs), como modems e roteadores Wi-Fi. Ele permite que o suporte de redes realize configurações em massa, atualizações de firmware e diagnósticos de conexão remotamente, eliminando a necessidade de visitas técnicas presenciais para problemas lógicos de configuração.

**Monitoramento Ativo com Zabbix:**
Enquanto o TR-069 gerencia o CPE, o Zabbix atua no monitoramento da infraestrutura central (Switches, Roteadores de Borda e OLTs). Utilizando o protocolo SNMP, o Zabbix coleta dados cruciais como uso de CPU, tráfego de interfaces e temperatura dos equipamentos. A junção do monitoramento (Zabbix) com a gerência (TR-069) cria uma rede altamente proativa.

### 2. Glossário de Conceitos

* **ACS (Auto Configuration Server):** Servidor central que se comunica com os dispositivos na casa do cliente via TR-069.
* **CPE (Customer Premises Equipment):** O equipamento de telecomunicações que fica nas instalações do cliente (ex: roteador).
* **SNMP (Simple Network Management Protocol):** Protocolo padrão da internet para coleta e organização de informações sobre dispositivos gerenciados em redes IP.
* **OLT (Optical Line Terminal):** O equipamento provedor de serviços (ponto de origem) em uma rede óptica passiva (PON).
* **Zabbix:** Ferramenta de software open-source para monitoramento de infraestruturas de TI, como redes, servidores e serviços.
* **Atenuação de Sinal:** Perda de potência do sinal óptico ao longo da fibra, geralmente medida em decibéis (dBm).

### 3. Prompts Reutilizáveis para Revisão Contínua

Para manter o conhecimento sempre atualizado, utilize os seguintes prompts no seu próprio NotebookLM com suas fontes carregadas:

1. > *"Estou analisando uma falha de autenticação PPPoe em um cliente específico. Com base no manual de gerência TR-069 fornecido, liste o passo a passo para extrair os logs de erro da CPE através do servidor ACS."*
2. > *"Quais são os triggers recomendados na documentação do Zabbix para alertar sobre alta atenuação de sinal na porta PON de uma OLT?"*
3. > *"Crie um checklist de atendimento rápido para o nível 1 de suporte focado em validação de parâmetros físicos e lógicos da conexão do cliente."*

---
*Projeto desenvolvido para o Desafio de Projeto da [DIO](https://www.dio.me/).*
