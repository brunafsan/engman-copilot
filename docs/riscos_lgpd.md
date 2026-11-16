
# Riscos e LGPD — EngMan Copilot

## Identificação dos riscos

O EngMan Copilot é um assistente de inteligência artificial proposto para apoiar engenheiros de manutenção na análise de falhas em câmeras de CFTV. Embora possa auxiliar na consulta de informações técnicas e na identificação de possíveis causas de problemas, sua utilização apresenta riscos que precisam ser considerados.
Foram identificados oito riscos relacionados à confiabilidade das respostas, à segurança operacional, à proteção de dados e ao funcionamento do assistente. Para cada risco, serão apresentados os possíveis impactos, as medidas de prevenção e os componentes do projeto nos quais essas medidas estão previstas.

## Risco 1 — Alucinação da IA

**Descrição do risco:** O EngMan Copilot poderá apresentar informações incorretas ou inexistentes como se fossem verdadeiras, como inventar históricos de falhas, características de equipamentos ou diagnósticos sem comprovação nos documentos consultados.

**Impacto:** O engenheiro poderá tomar decisões com base em informações falsas, resultando em diagnósticos incorretos, manutenções desnecessárias, aumento de custos e atrasos na resolução dos problemas.

**Medida de prevenção:** O assistente deverá fundamentar suas respostas nos documentos disponíveis, identificar as fontes consultadas e distinguir informações comprovadas de hipóteses. Quando não houver dados suficientes, deverá informar essa limitação, sem inventar registros ou diagnósticos.

**Onde a proteção aparecerá:** No bloco REGRAS do system_prompt.md, no guardrail de saída da arquitetura, responsável por verificar as respostas, e nos casos de teste da categoria dado_inexistente do sprint1_eval_set.json.

## Risco 2 — Prompt Injection

**Descrição do risco:** O EngMan Copilot poderá receber instruções maliciosas em perguntas ou documentos consultados, tentando modificar seu comportamento e fazê-lo desrespeitar as regras estabelecidas, como revelar informações confidenciais, expor instruções internas do sistema ou fornecer orientações proibidas.

**Impacto:** O assistente poderá apresentar respostas fora do escopo do projeto, divulgar informações não autorizadas ou fornecer recomendações inadequadas, comprometendo a segurança e a confiabilidade do sistema.

**Medida de prevenção:** O assistente deverá seguir as regras definidas no system prompt, sem aceitar instruções externas que tentem modificá-las. As informações recuperadas dos documentos deverão ser tratadas como dados de consulta, e não como novas instruções. Também serão previstas verificações nas entradas e saídas para identificar tentativas de manipulação e reduzir o risco de descumprimento das regras.

**Onde a proteção aparecerá:** Nos blocos REGRAS e BORDA do system_prompt.md, nos guardrails de entrada e saída da arquitetura e nos casos de teste da categoria jailbreak do sprint1_eval_set.json, destinados a avaliar tentativas de contornar as regras do assistente.

## Risco 3 — Segurança operacional

**Descrição do risco:** O EngMan Copilot poderá recomendar procedimentos inadequados ou inseguros para a manutenção das câmeras CFTV, sem considerar os riscos envolvidos em atividades como intervenções elétricas, trabalhos em altura e serviços realizados em rodovias.

**Impacto:** A execução dessas recomendações poderá provocar acidentes de trabalho, danos aos equipamentos e interrupções no funcionamento das câmeras, comprometendo a segurança dos profissionais e a disponibilidade do sistema de monitoramento.

**Medida de prevenção:** O assistente deverá utilizar os procedimentos técnicos disponíveis como referência, respeitando os requisitos de segurança aplicáveis, como as normas NR-10 e NR-35. Não deverá recomendar intervenções que desconsiderem medidas obrigatórias de segurança e deverá orientar que a execução dos serviços seja avaliada e autorizada por profissionais habilitados, quando exigido.

**Onde a proteção aparecerá:** Nos blocos REGRAS e BORDA do system_prompt.md, nos guardrails de entrada e saída da arquitetura e nos casos de teste da categoria risco_operacional do sprint1_eval_set.json.

## Risco 4 — Viés na priorização

**Descrição do risco:** O EngMan Copilot poderá priorizar incorretamente a manutenção das câmeras CFTV, utilizando critérios inconsistentes ou desconsiderando informações importantes sobre a criticidade dos equipamentos.

**Impacto:** Equipamentos com maior impacto na segurança viária, na arrecadação ou na disponibilidade dos serviços poderão receber menor prioridade, provocando atrasos em manutenções importantes e comprometendo a eficiência das operações.

**Medida de prevenção:** O assistente deverá consultar a matriz de criticidade prevista na base de conhecimento, considerando os impactos na segurança viária, na arrecadação e na disponibilidade dos serviços. As recomendações deverão apresentar os critérios utilizados e ser submetidas à avaliação do engenheiro de manutenção. Na ausência de informações suficientes, o assistente não deverá definir uma prioridade como definitiva.

**Onde a proteção aparecerá:** Nos blocos REGRAS e FORMATO do system_prompt.md, na montagem do contexto com documentos recuperados pelo RAG (bloco 3 da arquitetura), na matriz de criticidade prevista no inventario.md e no teste factual C01 do sprint1_eval_set.json, que verifica a consulta correta às informações de criticidade dos equipamentos.

## Risco 5 — LGPD e dados pessoais

**Descrição do risco:** O EngMan Copilot poderá receber ou expor dados pessoais desnecessários para a análise de falhas, como informações de funcionários, imagens que permitam identificar pessoas ou placas de veículos, comprometendo a privacidade dos envolvidos.

**Impacto:** O tratamento ou a divulgação inadequada dessas informações poderá violar a privacidade dos titulares, ocasionar exposição indevida de dados e gerar consequências legais para a empresa, incluindo possíveis sanções previstas na LGPD.

**Medida de prevenção:** O assistente deverá evitar o tratamento de dados pessoais desnecessários, utilizando dados fictícios na base de conhecimento acadêmica. Também deverão ser previstas verificações para impedir a inclusão e a exposição indevida dessas informações, respeitando os princípios de necessidade, segurança e prevenção da LGPD.

**Onde a proteção aparecerá:** Nos blocos REGRAS e BORDA do system_prompt.md, nas verificações de entrada e saída previstas na arquitetura (blocos 2 e 7), que deverão contemplar a proteção de dados pessoais, e nas diretrizes de privacidade do inventario.md, que estabelecem restrições aos dados utilizados na base de conhecimento.


## Risco 6 — Confidencialidade

**Descrição do risco:** O EngMan Copilot poderá expor informações internas ou confidenciais da Motiva, como históricos de manutenção, registros de falhas, localizações de equipamentos e procedimentos operacionais restritos, caso esses dados sejam utilizados ou divulgados sem autorização.

**Impacto:** A exposição dessas informações poderá comprometer a segurança das operações, facilitar o uso indevido de informações técnicas e causar prejuízos operacionais e à confidencialidade dos dados da empresa.

**Medida de prevenção:** O projeto deverá utilizar apenas dados simulados ou informações públicas e autorizadas, impedindo a inclusão de documentos internos restritos na base de conhecimento. Em uma futura implementação com dados reais, deverão ser previstos controles de acesso conforme as permissões dos usuários, além de verificações para evitar a divulgação de informações não autorizadas.

**Onde a proteção aparecerá:** Nos blocos REGRAS e BORDA do system_prompt.md, no guardrail de saída da arquitetura (bloco 7), nas verificações de entrada a serem detalhadas (bloco 2) e nas diretrizes de origem e disponibilidade dos documentos do inventario.md.


## Risco 7 — Excesso de confiança

**Descrição do risco:** O EngMan Copilot poderá apresentar hipóteses sobre falhas em câmeras CFTV como se fossem diagnósticos confirmados, demonstrando um nível de certeza maior do que as informações disponíveis permitem.

**Impacto:** O engenheiro poderá confiar excessivamente nas conclusões do assistente, ocasionando diagnósticos incorretos, substituições desnecessárias de componentes e decisões de manutenção inadequadas.

**Medida de prevenção:** O assistente deverá diferenciar fatos documentados de hipóteses, indicar as fontes utilizadas e comunicar seu nível de confiança de acordo com as evidências disponíveis. Quando não houver informações suficientes para confirmar uma causa, deverá informar essa limitação e recomendar a avaliação do engenheiro, sem apresentar conclusões definitivas.

**Onde a proteção aparecerá:** Nos blocos REGRAS e FORMATO do system_prompt.md, no guardrail de saída da arquitetura (bloco 7) e nos casos de teste C02 (factual) e C05 (ambíguo) do sprint1_eval_set.json, que verificam a diferenciação entre informações documentadas e possíveis causas, além do reconhecimento de informações insuficientes.


## Risco 8 — Limite de contexto

**Descrição do risco:** O EngMan Copilot poderá perder ou desconsiderar informações importantes durante conversas extensas ou consultas com muitos documentos, causando confusão entre os históricos, as falhas e as identificações (TAGs) de diferentes câmeras CFTV.

**Impacto:** O assistente poderá apresentar informações incompletas ou associar registros de falhas ao equipamento incorreto, prejudicando a precisão dos diagnósticos e das recomendações de manutenção.

**Medida de prevenção:** O sistema deverá limitar o histórico da conversa e utilizar o mecanismo RAG para recuperar os trechos mais relevantes dos documentos, utilizando filtros por TAG quando possível. O assistente também deverá confirmar a identificação do equipamento quando houver ambiguidade, evitando misturar registros de câmeras diferentes.

**Onde a proteção aparecerá:** Nos blocos REGRAS e BORDA do system_prompt.md, na montagem do contexto e no controle do histórico da conversa (blocos 3 e 8 da arquitetura) e no caso de teste C10, da categoria memoria_contexto, do sprint1_eval_set.json.


## Relação com as medidas de proteção

[Explicar onde as medidas de prevenção aparecem no projeto: nas regras do system prompt, nos blocos da arquitetura ou nos casos de teste do eval set.]

[Indicar, para cada risco, pelo menos uma medida concreta de proteção e onde ela será documentada.]

