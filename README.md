# engman-copilot
Assistente de IA para diagnóstico de falhas em ativos de rodovias (FIAP x Motiva)

## 1. Integrantes

- Bruna Ferreira Santos — RM: [576941] — Turma: 1CCPB
- Isabelle Barbosa de Aguiar Sobral — RM: [576857] — Turma: 1CCPB
- Rafael Meirelles Alves Ferreira — RM: [574688] — Turma: 1CCPB
  
## Problema abordado

O monitoramento das rodovias conta com diferentes equipamentos, como câmeras de CFTV, sensores e painéis de mensagens, que ajudam a acompanhar o trânsito e manter a segurança nas vias. Com o tempo, esses equipamentos podem apresentar falhas, seja pelo uso constante ou pela exposição às condições do ambiente. Quando isso acontece, as equipes de manutenção precisam identificar o problema, entender suas possíveis causas e definir quais medidas devem ser tomadas para que o equipamento volte a funcionar corretamente.

No caso das câmeras de CFTV, essa tarefa pode ser ainda mais difícil. Segundo o briefing da Motiva, as câmeras ficam expostas à chuva, poeira, fuligem, insetos e vibrações, que podem afetar a qualidade das imagens. Um dos problemas apontados é que a identificação de lentes sujas ou imagens desfocadas depende da observação dos operadores do Centro de Controle Operacional (CCO). Ao perceber uma falha, o operador precisa comunicar a equipe de engenharia para que o problema seja avaliado. Esse processo acaba sendo reativo, já que a manutenção depende da identificação da falha, o que pode atrasar a intervenção e comprometer o monitoramento da rodovia.

A dificuldade escolhida pelo grupo está relacionada ao diagnóstico de falhas nas câmeras de CFTV e ao acesso às informações necessárias para orientar a manutenção. De acordo com o briefing da Motiva, uma concessionária pode administrar centenas de câmeras distribuídas por longos trechos de rodovia, o que torna o acompanhamento desses equipamentos mais complexo. O documento também destaca a importância de melhorar a confiabilidade dos equipamentos eletrônicos e utilizar históricos de falhas para apoiar o planejamento da manutenção. Diante desse cenário, o grupo propõe um assistente de inteligência artificial que ajude os engenheiros a consultar registros de falhas, identificar possíveis causas e encontrar procedimentos técnicos. A ideia é facilitar a análise dos problemas e apoiar decisões de manutenção, sem substituir a avaliação dos profissionais.

## Recorte e persona

O grupo escolheu o Recorte A — Diagnóstico e Confiabilidade, com foco no Tema 2.1 — Câmeras de CFTV.

A persona principal do EngMan Copilot é o engenheiro de manutenção da Motiva, responsável por analisar falhas nos equipamentos e orientar os procedimentos de manutenção.

O grupo optou por esse recorte por considerar interessante trabalhar com a identificação de falhas e entender como a tecnologia pode ajudar na manutenção dos equipamentos rodoviários. Entre os equipamentos apresentados no briefing, escolhemos as câmeras de CFTV por sua importância no monitoramento das vias e pelos diferentes problemas que podem afetar seu funcionamento. Já o engenheiro de manutenção foi escolhido como usuário principal porque participa diretamente da análise desses problemas e poderia utilizar o assistente para consultar informações técnicas e apoiar suas decisões.

## Escopo do assistente

### O que o assistente faz

O EngMan Copilot será um assistente de inteligência artificial voltado ao apoio dos engenheiros de manutenção da Motiva no diagnóstico de falhas em câmeras de CFTV. Para isso, terá as seguintes funcionalidades:

-Consulta de equipamentos: acesso a informações como identificação (TAG), modelo, localização e criticidade das câmeras.

-Histórico de falhas: consulta a registros de ocorrências anteriores e manutenções realizadas, permitindo identificar problemas recorrentes.

-Apoio ao diagnóstico: apresentação de possíveis causas para as falhas relatadas, com base nos registros e documentos técnicos disponíveis.

-Consulta de procedimentos: acesso a orientações técnicas de inspeção e manutenção dos equipamentos.

-Avaliação de criticidade: apoio na análise da gravidade das falhas e na definição das prioridades de atendimento.

-Recomendação de manutenção: indicação de possíveis intervenções, como manutenção corretiva, preventiva ou inspeção.

-Ordens de serviço: organização das informações necessárias e solicitação de abertura simulada de uma ordem de serviço, mediante confirmação do engenheiro.


O assistente poderá responder a perguntas relacionadas ao funcionamento das câmeras de CFTV, aos sintomas de falhas, às possíveis causas dos problemas e às intervenções de manutenção. Por exemplo, o engenheiro poderá perguntar se determinada câmera apresenta um histórico de falhas recorrentes, quais fatores podem causar perda de imagem ou quais procedimentos são recomendados para investigar uma falha de comunicação.

Para elaborar suas respostas, o EngMan Copilot consultará informações disponíveis em sua base de conhecimento, como fichas técnicas dos equipamentos, históricos de manutenção, planos preventivos e procedimentos operacionais. As respostas deverão se basear nesses registros, diferenciando informações documentadas de possíveis hipóteses de diagnóstico.


### O que o assistente não faz

O EngMan Copilot terá sua atuação limitada ao apoio técnico no diagnóstico e na manutenção de câmeras de CFTV. Dessa forma, não poderá:

-Analisar imagens ou vídeos: identificar automaticamente problemas visuais nas câmeras, como lentes sujas ou imagens desfocadas.

-Controlar equipamentos: acessar câmeras remotamente para alterar configurações, reiniciar sistemas ou executar reparos.

-Realizar intervenções: executar atividades de manutenção ou substituir a atuação dos profissionais responsáveis.

-Emitir laudos técnicos: produzir diagnósticos definitivos, pareceres ou documentos que exijam responsabilidade técnica de um profissional habilitado.

-Inventar informações: apresentar dados de equipamentos, históricos de falhas ou procedimentos que não estejam disponíveis nas fontes consultadas.

-Atuar fora do escopo: responder a solicitações que não estejam relacionadas à manutenção das câmeras de CFTV.


O EngMan Copilot deverá recusar solicitações fora de seu escopo, pedidos de acesso ou divulgação não autorizada de informações confidenciais e dados pessoais, além de orientações que contrariem os procedimentos oficiais de segurança. Caso não encontre informações suficientes para responder a uma pergunta, deverá informar essa limitação e, quando necessário, solicitar dados adicionais, sem inventar informações.

As recomendações fornecidas pelo sistema, incluindo possíveis causas de falhas, prioridades de atendimento e tipos de intervenção, deverão ser avaliadas pelo engenheiro de manutenção antes de sua aplicação. A abertura simulada de ordens de serviço também dependerá de sua confirmação. Dessa forma, o EngMan Copilot auxiliará na análise e organização das informações, enquanto a responsabilidade pelas decisões técnicas permanecerá com o profissional habilitado.

## Arquitetura da solução

### Fluxograma

[Inserir o fluxograma da arquitetura disponível em docs/arquitetura.png.]

### Funcionamento da arquitetura

[Explicar como uma pergunta do usuário passa pelo sistema até a resposta final.]

[Descrever os 8 blocos da arquitetura: entrada do usuário, guardrail de entrada, montagem de contexto, chamada ao LLM, decisão sobre consultas, execução de ferramentas, guardrail de saída e resposta final com histórico.]

## Stack e justificativa técnica

### Comparação de modelos de linguagem

[Comparar pelo menos 2 modelos de linguagem (LLMs).]

[Considerar custo, licença ou termos de uso, suporte ao português, tamanho de contexto, privacidade, integração com Python e maturidade.]

### Comparação de bancos vetoriais

[Comparar pelo menos 2 opções de vector stores.]

[Apresentar os critérios utilizados na comparação, incluindo custos, integração, privacidade e limitações.]

### Tecnologias escolhidas

[Informar quais tecnologias o grupo escolheu e justificar a decisão.]

[Explicar as vantagens, as limitações aceitas e como seria possível executar a solução utilizando recursos gratuitos.]

## Base de conhecimento

### Documentos previstos

[Resumir os pelo menos 8 documentos planejados para a base de conhecimento, conforme o arquivo data/knowledge_base/inventario.md.]

[Informar quais tipos de informações esses documentos fornecerão ao assistente.]

### Utilização do RAG

[Explicar como o assistente consultaria os documentos para encontrar informações relevantes antes de responder ao usuário.]

[Informar como os documentos seriam divididos em trechos, quais metadados seriam utilizados e quais dados sensíveis ficariam de fora.]

## System Prompt

[Resumir as principais instruções dadas ao assistente, incluindo seu papel, objetivo, regras, limites e comportamento diante de informações ausentes.]

[Inserir o link para prompts/system_prompt.md.]

## Eval Set

[Explicar que o conjunto de avaliação contém pelo menos 10 casos de teste, distribuídos entre as categorias exigidas pelo professor.]

[Resumir como os testes verificam se o assistente responde corretamente, solicita dados ausentes e recusa pedidos inadequados.]

[Inserir o link para evals/sprint1_eval_set.json.]

## Tools especificadas

[Apresentar as ferramentas planejadas para o assistente.]

[Montar uma tabela contendo o nome de cada ferramenta, sua função e seus parâmetros principais.]

[Incluir as ferramentas obrigatórias: consultar_ativo, consultar_historico_falhas, abrir_ordem_servico e consultar_procedimento.]

[Inserir o link para tools/tools_spec.json.]

## Riscos e mitigações

[Resumir os pelo menos 8 riscos identificados no arquivo docs/riscos_lgpd.md.]

[Explicar o impacto de cada risco e como ele será reduzido por regras do system prompt, verificações da arquitetura ou testes.]

## Limitações conhecidas

[Explicar quais são as limitações da solução proposta.]

[Informar quais funcionalidades ainda não estarão disponíveis e quais informações ou recursos seriam necessários para o funcionamento completo do assistente.]

## Referências

[Listar as fontes utilizadas na elaboração do projeto.]

[Incluir o briefing da Motiva, os materiais da disciplina e as documentações técnicas efetivamente consultadas.]

[Adicionar normas ou outras referências apenas quando forem utilizadas no trabalho.]
