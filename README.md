🛡️ LAB 01: Prompt Injection & Defense in Depth (OWASP LLM01) — Qwen 2.5 Edition

Este repositório contém o laboratório prático de cibersegurança em Inteligência Artificial focado em Prompt Injection e implementação de Defesa em Profundidade (Defense in Depth) utilizando modelos open-source otimizados.

🎯 Objetivo do Laboratório
Demonstrar na prática como falhas de concatenação direta em Large Language Models (LLMs) permitem ataques de Prompt Injection e Jailbreak, comprometendo dados confidenciais corporativos, e como mitigá-las utilizando barreiras defensivas em Python (Output Guardrails).

🧪 Estrutura da Atividade
🔴 Red Team (Ataque)
• Conceito: Exploração da vulnerabilidade OWASP LLM01 no modelo Qwen 2.5 (1.5B-Instruct), onde a entrada do usuário é concatenada diretamente com o System Prompt.
• Vetor de Testes: Aplicação de ataques por Injeção Direta, Preenchimento de Prefixo (Prefix Injection), Engenharia Social (Roleplay) e Comandos de Autoridade (System Override) para forçar o vazamento do código confidencial (`SUPER_SECRET_2026_OFF`).

🔵 Blue Team (Defesa)
• Conceito: Aplicação do princípio de Defense in Depth (admitindo que instruções textuais na IA por si só falham sob ataques direcionados).
• Solução: Implementação de uma camada de validação e pós-processamento (Output Guardrail) que inspeciona a resposta gerada pela IA em tempo de execução e intercepta tentativas de vazamento antes de entregá-las ao usuário final.
