🛡️ LAB1: OWASP LLM01_PROMPT INJECTION DIRECT & DEFENSE IN DEPTH
Este repositório contém o laboratório prático de cibersegurança em Inteligência Artificial, focado na exploração da vulnerabilidade OWASP LLM01 (Prompt Injection Direto) e na implementação de estratégias de Defense in Depth com modelos open-source otimizados.

🎯 Novo Objetivo do Laboratório
Demonstrar na prática como a vulnerabilidade OWASP LLM01 (Prompt Injection Direto e Jailbreak) permite manipular o comportamento de uma Large Language Model (LLM) por meio de engenharia social, troca de papéis (roleplay) e override de sistema para vazar dados confidenciais corporativos; e capacitar os alunos a projetarem, implementarem e validarem defesas em profundidade no backend, combinando barreiras de inspeção de saída (Output Guardrails) e técnicas automatizadas de detecção de vazamento de segredos para mitigar falhas de Insecure Output Handling (OWASP LLM02).

Modelo Utilizado: Qwen 2.5 (1.5B-Instruct) via Hugging Face Pipeline

Ambiente de Execução: Google Colab (GPU T4)

Vulnerabilidades Alvo:

OWASP LLM01: Prompt Injection Direct

OWASP LLM02: Insecure Output Handling

🧪 Estrutura da Atividade
🔴 Red Team (Ataque)
Conceito: Exploração da vulnerabilidade OWASP LLM01 no modelo Qwen 2.5, onde a entrada do usuário é concatenada diretamente com o SYSTEM_PROMPT.

Alvo de Injeção: Forçar o vazamento da credencial secreta corporativa: SUPER_SECRET_2026_OFF.

🔵 Blue Team (Defesa)
Conceito: Aplicação do princípio de Defense in Depth, assumindo que restrições textuais no prompt da IA falham sob ataques direcionados.

Solução: Implementação de uma camada de validação e pós-processamento (Output Guardrail em Python) para inspecionar o texto gerado em tempo de execução.

📋 Detalhamento das Atividades Práticas
Módulo Red Team (Ataques)
Atividade A: Engenharia Social / Troca de Papel (Roleplay) — Uso de persona de professor de cibersegurança para extrair o código confidencial.

Atividade B: Comando de Autoridade / Override de Sistema — Simulação de privilégios administrativos do CEO ([SYSTEM OVERRIDE]).

Atividade C: Troca de Idioma e Formato (Translation & Format Jailbreak) — Indução de tradução para contornar restrições estruturais.

Módulo Blue Team (Defesa & Validação)
Atividade D: Implementação da Camada Defensiva (Output Guardrail) — Criação do wrapper assistente_protegido() em Python.

Atividade E: Teste de Engenharia Social com Proteção Ativa — Validação do bloqueio sob ataques de roleplay.

Atividade F: Teste de Ataque de Autoridade com Proteção Ativa — Confirmação da resiliência do filtro contra falsificação corporativa.

Lição Principal: "Mesmo que o atacante consiga enganar o cérebro da IA (Prompt Injection), a aplicação em código age como um firewall de saída. Essa é a essência do Defense in Depth: nunca confie 100% no modelo, proteja o código ao redor dele!"
