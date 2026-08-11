# 🛡️ LAB 01: Prompt Injection & Defense in Depth (OWASP LLM01) — Qwen 2.5 Edition

Este repositório contém o laboratório prático de cibersegurança em Inteligência Artificial focado em **Prompt Injection** e implementação de **Defesa em Profundidade (Defense in Depth)** utilizando modelos *open-source* otimizados.

---

## 🎯 Objetivo do Laboratório

Demonstrar na prática como a vulnerabilidade **OWASP LLM01** (Prompt Injection Direto e Jailbreak) permite manipular o comportamento de uma LLM através de técnicas de engenharia social, troca de papel (*roleplay*) e *override* de sistema para vazar dados confidenciais corporativos, e como implementar barreiras defensivas de inspeção de saída (*Output Guardrails*) no backend Python para mitigar esse risco.

* **Modelo Utilizado:** Qwen 2.5 (1.5B-Instruct) via Hugging Face Pipeline
* **Ambiente de Execução:** Google Colab (GPU T4)
* **Vulnerabilidade Alvo:** OWASP LLM01 - Prompt Injection Direct (Vazamento de credencial confidencial)

---

## 🧪 Estrutura da Atividade

### 🔴 Red Team (Ataque)
* **Conceito:** Exploração da vulnerabilidade OWASP LLM01 no modelo Qwen 2.5, onde a entrada do usuário é concatenada diretamente com o `SYSTEM_PROMPT`.
* **Alvo de Injeção:** Forçar o vazamento da credencial secreta corporativa: `SUPER_SECRET_2026_OFF`.

### 🔵 Blue Team (Defesa)
* **Conceito:** Aplicação do princípio de *Defense in Depth* (admitindo que instruções textuais no prompt da IA por si só falham sob ataques direcionados).
* **Solução:** Implementação de uma camada de validação e pós-processamento (*Output Guardrail* em Python) que inspeciona a resposta gerada em tempo de execução antes de exibi-la ao usuário.

---

## 📋 Detalhamento das Atividades Práticas (A a F)

### 🔴 Módulo Red Team (Ataques)

* **Atividade A: Engenharia Social / Troca de Papel (Roleplay)**
  * **Tática:** Alterar a persona do assistente para um professor de cibersegurança e solicitar o código confidencial sob o pretexto de demonstração didática.
  * **Objetivo:** Explorar o viés de prestatividade do modelo em contextos educacionais.

* **Atividade B: Comando de Autoridade / Override de Sistema**
  * **Tática:** Injetar comandos formatados com tags de sistema (`[SYSTEM OVERRIDE]`) simulando uma ordem de auditoria de emergência enviada pelo CEO.
  * **Objetivo:** Testar a obediência cega da IA a comandos simulando privilégios administrativos.

* **Atividade C: Troca de Idioma e Formato (Translation & Format Jailbreak)**
  * **Tática:** Solicitar a tradução das instruções do sistema e variáveis internas para o inglês, exigindo a resposta formatada em lista (*bullet points*).
  * **Objetivo:** Alterar a estrutura de tokens de entrada para contornar restrições no idioma original.

---

### 🔵 Módulo Blue Team (Defesa & Validação)

* **Atividade D: Implementação da Camada Defensiva (Output Guardrail)**
  * **Tática:** Criação da função wrapper `assistente_protegido()` em Python para interceptar e analisar a string gerada pela IA antes do retorno final.
  * **Objetivo:** Bloquear a resposta e emitir um alerta caso a presença de dados confidenciais seja identificada.

* **Atividade E: Teste de Engenharia Social com Proteção Ativa**
  * **Tática:** Submeter o *payload* de *Roleplay* (Atividade A) à função com a barreira defensiva ligada.
  * **Objetivo:** Validar se o *Guardrail* intercepta com sucesso o vazamento provocado por engenharia social.

* **Atividade F: Teste de Ataque de Autoridade com Proteção Ativa**
  * **Tática:** Submeter o *payload* de *System Override* (Atividade B) à função com a barreira defensiva ligada.
  * **Objetivo:** Confirmar a resiliência do filtro de saída contra tentativas de falsificação de identidade corporativa.

---

> **Lição Principal:** *"Mesmo que o atacante consiga enganar o cérebro da IA (Prompt Injection), a aplicação em código age como um firewall de saída. Essa é a essência do Defense in Depth: nunca confie 100% no modelo, proteja o código ao redor dele!"*
