# Decisões Técnicas — EngMan Copilot

## Objetivo das decisões técnicas

Antes de escolher as tecnologias de uma futura implementação do EngMan Copilot, o grupo comparou alternativas. Cada opção tem vantagens e limitações em custo, privacidade, qualidade das respostas e facilidade de uso, e a escolha precisa combinar com as regras do projeto: as respostas devem se basear em documentos, os dados internos não podem ser expostos e a solução deve poder rodar sem custos obrigatórios.

Nesta Sprint, nenhuma tecnologia foi implementada. As decisões abaixo registram o que seria usado e por quê.

### Critérios de escolha

| Critério | Por que importa para o projeto |
|---|---|
| Custo | O projeto acadêmico precisa de um caminho gratuito. |
| Licença e termos de uso | A tecnologia precisa poder ser usada e adaptada sem restrições que impeçam o projeto. |
| Suporte ao português | O engenheiro faz perguntas e recebe respostas em português. |
| Janela de contexto | O modelo precisa receber, ao mesmo tempo, o system prompt, o histórico da conversa, os trechos dos documentos e o resultado das tools. |
| Privacidade | Históricos de manutenção são informações internas e não devem ser enviados a terceiros sem autorização. |
| Integração com Python | A futura implementação seria feita em Python. |
| Maturidade | Documentação e comunidade ativas reduzem o risco de problemas sem solução. |

## Comparação de modelos de linguagem (LLMs)

### Modelo 1

**Nome:** Qwen3 8B, executado localmente com o Ollama (`qwen3:8b`).

**Custo:** Gratuito. O modelo é baixado e executado no próprio computador, sem cobrança por uso. O custo é o do hardware: o arquivo do modelo tem 5,2 GB (versão quantizada Q4_K_M).

**Licença e termos de uso:** Apache 2.0, que permite uso, modificação e uso comercial.

**Suporte ao português:** O relatório técnico do Qwen3 informa suporte a 119 idiomas e dialetos. Como o português não aparece destacado no resumo do relatório, a qualidade das respostas em português técnico precisaria ser validada com o eval set.

**Janela de contexto:** 32.768 tokens nativos, podendo chegar a 131.072 tokens com a técnica YaRN. Para o EngMan Copilot, 32 mil tokens são suficientes para o system prompt, o histórico recente e alguns trechos de documentos.

**Privacidade:** Alta. Todo o processamento acontece no computador local, e nenhuma pergunta ou documento é enviado para servidores externos.

**Integração com Python:** Pela biblioteca oficial `ollama` para Python. O Ollama oferece suporte a tool calling, e a própria documentação usa o Qwen3 nos exemplos, o que permite chamar as quatro tools do `tools_spec.json`.

**Maturidade:** Boa. O Ollama tem documentação oficial e comunidade grande, e o Qwen3 é uma família de modelos abertos amplamente usada.

### Modelo 2

**Nome:** Gemini (família Flash), acessado pela Gemini API do Google.

**Custo:** Possui camada gratuita (free tier) em modelos como o Gemini 2.5 Flash, com limites de uso que podem mudar. Acima desses limites, ou para ter garantias de privacidade, é necessário o plano pago.

**Licença e termos de uso:** Serviço comercial, regido pelos termos de uso da Gemini API. O modelo não pode ser baixado nem executado localmente.

**Suporte ao português:** Modelo multilíngue, com bom desempenho esperado em português.

**Janela de contexto:** Muito grande. Os modelos Flash atuais, como o Gemini 3.6 Flash, aceitam até 1.048.576 tokens de entrada e 65.536 de saída.

**Privacidade:** Baixa na camada gratuita. A página de preços informa que, no free tier, o conteúdo enviado é usado para melhorar os produtos do Google; no plano pago, não. Por isso, o modelo só poderia receber dados simulados na versão gratuita.

**Integração com Python:** Pelo SDK oficial do Google, com suporte a function calling.

**Maturidade:** Alta. Serviço mantido pelo Google, com documentação oficial completa. Por outro lado, os modelos são substituídos com frequência (o Gemini 3.5 Flash, por exemplo, já foi substituído pelo 3.6 Flash), o que exige acompanhar as mudanças.

### Resumo da comparação de LLMs

| Critério | Qwen3 8B (Ollama, local) | Gemini Flash (API) |
|---|---|---|
| Custo | Gratuito (usa o hardware próprio) | Free tier com limites; depois, pago |
| Licença | Apache 2.0 | Termos de serviço do Google |
| Português | 119 idiomas; validar no eval set | Multilíngue |
| Contexto | 32.768 tokens (até 131.072) | Até 1.048.576 tokens |
| Privacidade | Dados ficam no computador | Free tier usa os dados para melhorar produtos |
| Python | Biblioteca `ollama`, com tool calling | SDK do Google, com function calling |
| Maturidade | Boa | Alta, mas com troca frequente de versões |

## Comparação de bancos vetoriais (Vector Stores)

Um banco vetorial guarda os documentos da base de conhecimento em forma de vetores (listas de números que representam o significado do texto). Assim, o assistente consegue encontrar os trechos mais parecidos com a pergunta do engenheiro, que é a base do RAG.

### Banco vetorial 1

**Nome:** ChromaDB.

**Custo:** Gratuito e de código aberto.

**Licença e termos de uso:** Apache 2.0.

**Integração com Python:** Instalação com `pip install chromadb`, com API simples para adicionar documentos e fazer buscas.

**Privacidade:** Pode rodar localmente, então os documentos não saem do computador.

**Maturidade:** Projeto ativo, com versões recentes (1.5.9, de maio de 2026) e documentação oficial.

**Vantagens e limitações:** A principal vantagem é aceitar metadados em cada trecho e filtrar a busca por eles (cláusula `where`). Isso combina com os metadados planejados no inventário (TAG, tipo de documento, tipo de falha, data, fonte e versão): por exemplo, buscar apenas no histórico da CFTV-001. A limitação é ter desempenho menor que bibliotecas especializadas em volumes muito grandes de dados, o que não é o caso de uma base com oito documentos.

### Banco vetorial 2

**Nome:** FAISS (Facebook AI Similarity Search).

**Custo:** Gratuito e de código aberto.

**Licença e termos de uso:** MIT.

**Integração com Python:** Escrito em C++, com interface completa para Python.

**Privacidade:** Roda localmente.

**Maturidade:** Alta. Mantido pela Meta, é muito usado em pesquisa e em produção.

**Vantagens e limitações:** É muito rápido e oferece suporte opcional a GPU, ideal para milhões de vetores. Porém, é uma biblioteca de índices, e não um banco de dados completo: cada vetor é identificado só por um número inteiro. Guardar os textos e os metadados (TAG, fonte, data) e fazer filtros exigiria código extra.

### Resumo da comparação de bancos vetoriais

| Critério | ChromaDB | FAISS |
|---|---|---|
| Custo | Gratuito | Gratuito |
| Licença | Apache 2.0 | MIT |
| Integração com Python | Nativa e simples | Interface Python sobre C++ |
| Metadados e filtros | Sim, com `where` | Não nativamente; exige código extra |
| Privacidade | Local | Local |
| Ponto forte | Simplicidade e filtros por TAG e documento | Velocidade em bases enormes |

## Embeddings, RAG e orquestração

**Embeddings:** São os vetores que representam o significado de cada trecho. A opção prevista é o modelo **BGE-M3**, disponível no Ollama (`bge-m3`). Ele tem licença MIT, suporta mais de 100 idiomas, aceita textos de até 8.192 tokens e tem cerca de 1,2 GB, o que permite rodar localmente junto com o LLM.

**RAG:** Os documentos do inventário seriam divididos em trechos (chunks) com seus metadados e guardados no ChromaDB. A cada pergunta, o sistema busca os trechos mais relevantes, filtrando por TAG ou tipo de documento quando possível, e os envia ao modelo na etapa de montagem do contexto (bloco 3 do fluxograma).

**Orquestração:** Um programa em Python, usando a biblioteca `ollama`, coordenaria as etapas do fluxograma: guardrail de entrada, busca no ChromaDB, chamada ao modelo, execução das tools quando o modelo pedir e guardrail de saída. O próprio tool calling do Ollama permite que o modelo peça uma tool, receba o resultado e só então finalize a resposta, que é o retorno desenhado entre os blocos 6 e 4.

## Tecnologias escolhidas

**Modelo de linguagem escolhido:** Qwen3 8B, executado localmente com o Ollama.

**Banco vetorial escolhido:** ChromaDB.

**Embeddings:** BGE-M3, também pelo Ollama.

O grupo escolheu o **Qwen3 8B local** principalmente pela **privacidade**: históricos de manutenção são informações internas, e na camada gratuita do Gemini os dados enviados podem ser usados para melhorar os produtos do Google. Além disso, a licença Apache 2.0 e o custo zero de uso combinam com um projeto acadêmico, e o suporte a tool calling atende às quatro tools especificadas.

O **ChromaDB** foi escolhido por permitir **filtrar a busca por metadados**, como a TAG da câmera e o tipo de documento. Isso ajuda a cumprir regras importantes do projeto: não misturar informações de câmeras diferentes e sempre saber de qual documento veio cada informação.

## Trade-off aceito

O grupo priorizou **privacidade, custo zero e controle sobre os dados**. Em troca, aceitou estas limitações:

- **Exigência de hardware:** o modelo local precisa de um computador com memória suficiente (o arquivo do Qwen3 8B tem 5,2 GB). Sem GPU, as respostas ficam mais lentas.
- **Qualidade menor que modelos grandes na nuvem:** um modelo de 8 bilhões de parâmetros pode errar mais em perguntas complexas. Por isso, os guardrails, a temperatura baixa e a regra de separar fato de hipótese são ainda mais importantes.
- **Português a validar:** o suporte ao português técnico precisa ser confirmado nos testes do eval set.
- **Contexto menor:** 32 mil tokens, contra cerca de 1 milhão do Gemini. Isso é compensado pelo RAG, que envia ao modelo apenas os trechos relevantes, e pelo limite de histórico da conversa.

O Gemini poderia ser usado apenas para comparação de qualidade, desde que somente com dados simulados.

## Caminho de execução gratuita

Toda a solução pode rodar sem nenhum custo obrigatório, em um único computador:

1. Instalar o **Ollama** (gratuito).
2. Baixar o modelo de linguagem com `ollama pull qwen3:8b` e o de embeddings com `ollama pull bge-m3`.
3. Instalar as bibliotecas Python com `pip install ollama chromadb`.
4. Carregar no ChromaDB os documentos simulados da base de conhecimento.
5. Rodar o programa em Python que segue as etapas do fluxograma.

Nenhuma etapa exige chave de API paga, e os dados não saem do computador.

## Referências técnicas

Todas as fontes foram consultadas em 11/11/2026.

- Qwen. *Qwen3-8B-GGUF* (licença, janela de contexto e uso com Ollama). Disponível em: https://huggingface.co/Qwen/Qwen3-8B-GGUF
- Yang, A. et al. *Qwen3 Technical Report*. arXiv:2505.09388, 2025. Disponível em: https://arxiv.org/abs/2505.09388
- Ollama. *qwen3:8b* (tamanho, quantização e licença). Disponível em: https://registry.ollama.ai/library/qwen3:8b
- Ollama. *Tool calling*. Disponível em: https://docs.ollama.com/capabilities/tool-calling
- Ollama. *bge-m3*. Disponível em: https://registry.ollama.ai/library/bge-m3
- BAAI. *bge-m3* (licença, idiomas e tamanho máximo de entrada). Disponível em: https://huggingface.co/BAAI/bge-m3
- Google. *Gemini Developer API pricing* (camada gratuita e uso dos dados). Disponível em: https://ai.google.dev/gemini-api/docs/pricing
- Google. *Gemini 3.6 Flash* (limites de tokens e function calling). Disponível em: https://ai.google.dev/gemini-api/docs/models/gemini-3.6-flash
- Google. *Gemini 3.5 Flash* (aviso de substituição pelo 3.6 Flash). Disponível em: https://ai.google.dev/gemini-api/docs/models/gemini-3.5-flash
- Chroma. *chromadb* no PyPI (licença, versão e filtros por metadados). Disponível em: https://pypi.org/project/chromadb/
- Meta. *FAISS* no GitHub (licença e funcionamento). Disponível em: https://github.com/facebookresearch/faiss
