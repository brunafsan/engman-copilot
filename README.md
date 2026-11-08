# engman-copilot
Assistente de IA para diagnóstico de falhas em ativos de rodovias (FIAP x Motiva)

## 1. Integrantes

- Bruna Ferreira Santos — RM: [576941] — Turma: 1CCPB
- Isabelle Barbosa de Aguiar Sobral — RM: [576857] — Turma: 1CCPB
- Rafael Meirelles Alves Ferreira — RM: [574688] — Turma: 1CCPB
  
## Problema abordado

[Escrever de 1 a 2 parágrafos explicando o problema enfrentado pela Motiva em relação ao monitoramento e à manutenção dos equipamentos.]

[Apresentar a dificuldade escolhida pelo grupo e utilizar informações ou evidências do briefing da Motiva para justificar a importância do problema.]

## Recorte e persona

[Informar qual recorte e tema o grupo escolheu, conforme as opções apresentadas pelo professor.]

[Identificar a persona principal, ou seja, quem utilizará o assistente.]

[Escrever de 2 a 3 frases justificando por que o grupo escolheu esse recorte e essa persona.]

## Escopo do assistente

### O que o assistente faz

[Listar as funções que o assistente poderá realizar para ajudar o usuário principal.]

[Explicar quais tipos de perguntas ele poderá responder e quais informações poderá consultar.]

### O que o assistente não faz

[Listar as ações que o assistente não poderá realizar.]

[Explicar quais solicitações deverão ser recusadas e quais decisões dependerão de validação humana.]

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
