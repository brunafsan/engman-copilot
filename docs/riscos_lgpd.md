
# Riscos e LGPD — EngMan Copilot

## Identificação dos riscos

O EngMan Copilot é um assistente de inteligência artificial proposto para apoiar engenheiros de manutenção na análise de falhas em câmeras de CFTV. Embora possa auxiliar na consulta de informações técnicas e na identificação de possíveis causas de problemas, sua utilização apresenta riscos que precisam ser considerados.
Foram identificados oito riscos relacionados à confiabilidade das respostas, à segurança operacional, à proteção de dados e ao funcionamento do assistente. Para cada risco, serão apresentados os possíveis impactos, as medidas de prevenção e os componentes do projeto nos quais essas medidas estão previstas.

## Risco 1 — Alucinação da IA

Descrição do risco: O EngMan Copilot poderá apresentar informações incorretas ou inexistentes como se fossem verdadeiras, como inventar históricos de falhas, características de equipamentos ou diagnósticos sem comprovação nos documentos consultados.
Impacto: O engenheiro poderá tomar decisões com base em informações falsas, resultando em diagnósticos incorretos, manutenções desnecessárias, aumento de custos e atrasos na resolução dos problemas.
Medida de prevenção: O assistente deverá fundamentar suas respostas nos documentos disponíveis, identificar as fontes consultadas e distinguir informações comprovadas de hipóteses. Quando não houver dados suficientes, deverá informar essa limitação, sem inventar registros ou diagnósticos.
Onde a proteção aparecerá: No bloco REGRAS do system_prompt.md, no guardrail de saída da arquitetura, responsável por verificar as respostas, e nos casos de teste da categoria dado_inexistente do sprint1_eval_set.json.

## Risco 2 — Prompt Injection

Risco 2 — Injeção de Prompt
Descrição do risco: O EngMan Copilot poderá receber instruções maliciosas em perguntas ou documentos consultados, tentando modificar seu comportamento e fazê-lo desrespeitar as regras estabelecidas, como revelar informações confidenciais, expor instruções internas do sistema ou fornecer orientações proibidas.
Impacto: O assistente poderá apresentar respostas fora do escopo do projeto, divulgar informações não autorizadas ou fornecer recomendações inadequadas, comprometendo a segurança e a confiabilidade do sistema.
Medida de prevenção: O assistente deverá seguir as regras definidas no system prompt, sem aceitar instruções externas que tentem modificá-las. As informações recuperadas dos documentos deverão ser tratadas como dados de consulta, e não como novas instruções. Também serão previstas verificações nas entradas e saídas para identificar tentativas de manipulação e reduzir o risco de descumprimento das regras.
Onde a proteção aparecerá: Nos blocos REGRAS e BORDA do system_prompt.md, nos guardrails de entrada e saída da arquitetura e nos casos de teste da categoria jailbreak do sprint1_eval_set.json, destinados a avaliar tentativas de contornar as regras do assistente.

## Risco 3 — Segurança operacional

[Explicar o risco de o assistente sugerir procedimentos inadequados ou inseguros para a manutenção dos equipamentos.]

[Descrever o impacto e a medida de prevenção.]

## Risco 4 — Viés na priorização

[Explicar o risco de o assistente priorizar incorretamente determinados equipamentos ou falhas.]

[Descrever o impacto e a medida de prevenção.]

## Risco 5 — LGPD e dados pessoais

[Explicar os riscos relacionados ao tratamento ou à exposição de dados pessoais.]

[Descrever quais dados deverão ser evitados e como a privacidade será protegida.]

## Risco 6 — Confidencialidade

[Explicar o risco de exposição de informações internas ou confidenciais da empresa.]

[Descrever o impacto e a medida de prevenção.]

## Risco 7 — Excesso de confiança

[Explicar o risco de o assistente apresentar conclusões com certeza maior do que as evidências permitem.]

[Descrever o impacto e a medida de prevenção.]

## Risco 8 — Limite de contexto

[Explicar o risco de informações importantes serem perdidas ou desconsideradas quando houver muito conteúdo na conversa.]

[Descrever o impacto e a medida de prevenção.]

## Relação com as medidas de proteção

[Explicar onde as medidas de prevenção aparecem no projeto: nas regras do system prompt, nos blocos da arquitetura ou nos casos de teste do eval set.]

[Indicar, para cada risco, pelo menos uma medida concreta de proteção e onde ela será documentada.]

