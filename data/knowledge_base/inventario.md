
# Inventário da Base de Conhecimento — EngMan Copilot

## Objetivo da base de conhecimento

A base de conhecimento do EngMan Copilot terá como finalidade reunir e organizar informações técnicas sobre câmeras de CFTV utilizadas no monitoramento rodoviário. Por meio desses documentos, o assistente poderá consultar características dos equipamentos, históricos de falhas, procedimentos de manutenção e critérios de criticidade, auxiliando o engenheiro de manutenção na análise de problemas e na tomada de decisões fundamentadas nas informações disponíveis.

## Documentos planejados

A base de conhecimento do EngMan Copilot contará com oito documentos planejados, voltados à identificação, ao diagnóstico de falhas e à manutenção das câmeras CFTV. Cada documento será apresentado com seu nome, descrição, principais campos e origem, permitindo compreender quais informações poderão ser utilizadas pelo assistente.

### Documento 1

**Nome:** Catálogo de ativos CFTV

**Descrição:** Documento destinado ao cadastro e à identificação das câmeras CFTV, reunindo informações técnicas e de localização dos equipamentos. Permitirá que o engenheiro de manutenção consulte as características de cada câmera para auxiliar na análise de falhas e no planejamento das atividades de manutenção.

**Campos:** TAG, tipo de equipamento, fabricante, modelo, quilômetro, praça/pórtico, data de instalação, vida útil estimada e criticidade.

**Origem:** Simulado, com dados fictícios para fins acadêmicos.

### Documento 2

**Nome:** Plano de manutenção preventiva das câmeras CFTV

**Descrição:** Documento que reunirá as atividades de manutenção preventiva previstas para as câmeras CFTV, incluindo a frequência de execução, os responsáveis e os recursos necessários. Servirá de referência para o engenheiro de manutenção no planejamento de inspeções e serviços destinados a reduzir a ocorrência de falhas nos equipamentos.

**Campos:** Ativo, tarefa, periodicidade, responsável, tempo estimado, recursos necessários e condição de execução.

**Origem:** Simulado, com informações fictícias para fins acadêmicos.

### Documento 3

**Nome:** Histórico de falhas do FSM — Câmeras CFTV

**Descrição:** Documento destinado ao registro e à consulta de falhas ocorridas nas câmeras CFTV, reunindo informações sobre os problemas identificados, suas causas e os reparos realizados. Permitirá que o engenheiro de manutenção consulte ocorrências anteriores, identifique falhas recorrentes e utilize esse histórico como apoio ao diagnóstico e ao planejamento da manutenção.

**Campos:** TAG, data da ocorrência, sintoma, causa identificada, tempo de reparo, peça substituída e reincidência.

**Origem:** Simulado, com registros fictícios de falhas para fins acadêmicos.

### Documento 4

**Nome:** Procedimentos Operacionais (POPs) — Câmeras CFTV

**Descrição:** Documento que reunirá procedimentos técnicos para atividades de inspeção, limpeza, ajuste de foco e testes de comunicação das câmeras CFTV. Incluirá as etapas de execução e os pré-requisitos de segurança, servindo como referência para o engenheiro de manutenção na consulta e no planejamento dessas atividades.

**Campos:** Nome do procedimento, equipamento, objetivo, pré-requisitos de segurança, materiais necessários, etapas de execução e verificações finais.

**Origem:** Simulado, com procedimentos fictícios para fins acadêmicos.

### Documento 5

**Nome:** Fichas técnicas das câmeras CFTV

**Descrição:** Documento que reunirá as especificações técnicas dos modelos de câmeras CFTV considerados no projeto, incluindo suas características de funcionamento e requisitos de instalação. Permitirá que o engenheiro de manutenção consulte informações técnicas para auxiliar na identificação de possíveis falhas e na avaliação das necessidades de manutenção.

**Campos:** Fabricante, modelo, tipo de câmera, resolução de imagem, alimentação elétrica, tipo de conexão, condições de operação e requisitos de instalação.

**Origem:** Real e simulado. As especificações poderão ser obtidas de fichas técnicas públicas dos fabricantes, enquanto as informações não disponíveis serão representadas por dados fictícios, devidamente identificados.

### Documento 6

**Nome:** Matriz de criticidade das câmeras CFTV

**Descrição:** Documento destinado à avaliação da criticidade das câmeras CFTV, considerando os impactos que suas falhas podem causar na arrecadação, na segurança viária e na disponibilidade dos serviços. Permitirá que o engenheiro de manutenção identifique os equipamentos mais críticos e estabeleça prioridades para as atividades de manutenção.

**Campos:** Ativo, impacto na arrecadação, impacto na segurança viária, impacto na disponibilidade e prioridade de manutenção.

**Origem:** Simulado, com avaliações fictícias para fins acadêmicos.

### Documento 7

**Nome:** Glossário de siglas técnicas

**Descrição:** Documento que reunirá as siglas e seus respectivos significados, utilizados nos processos de monitoramento rodoviário e manutenção de equipamentos.

**Campos:** Sigla, significado e descrição de sua aplicação no contexto da manutenção rodoviária.

**Origem:** Real, com base nas siglas utilizadas no briefing da Motiva e em referências técnicas.

### Documento 8

**Nome:** Normas e requisitos de segurança

**Descrição:** Documento que reunirá resumos das normas de segurança aplicáveis às atividades de manutenção das câmeras CFTV, incluindo requisitos relacionados a serviços com eletricidade, trabalho em altura e atividades realizadas em rodovias. Servirá como referência para que o engenheiro de manutenção consulte os cuidados e requisitos de segurança envolvidos no planejamento das intervenções.

**Campos:** Norma ou requisito, descrição, atividade relacionada, condições de aplicação e medidas de segurança exigidas.

**Origem:** Real (resumo), com base nas normas NR-10 e NR-35 e em orientações de segurança para trabalhos em vias, quando disponíveis e autorizadas.

## Origem e disponibilidade dos documentos

A base de conhecimento do EngMan Copilot será composta por documentos simulados e informações provenientes de fontes públicas. O catálogo de ativos, o plano de manutenção preventiva, o histórico de falhas, os procedimentos operacionais e a matriz de criticidade serão produzidos com dados fictícios. As fichas técnicas poderão utilizar informações públicas de fabricantes, enquanto o glossário de siglas e os resumos das normas de segurança serão baseados em referências técnicas e fontes oficiais.

Documentos internos da Motiva, como cadastros reais de equipamentos, registros de manutenção e procedimentos internos, não serão considerados disponíveis sem autorização da empresa. Portanto, o projeto não pressupõe acesso a essas informações.

Todos os documentos simulados serão identificados como fictícios e utilizados exclusivamente para fins acadêmicos. Quando necessário, informações indisponíveis poderão ser representadas por exemplos simulados, sem apresentá-los como dados reais da Motiva.

## Organização dos documentos para o RAG

### Divisão em trechos (chunks)

Os documentos da base de conhecimento serão divididos em trechos menores, chamados chunks, para facilitar a busca de informações pelo sistema RAG. Essa divisão será feita de acordo com a organização de cada documento, mantendo informações relacionadas no mesmo trecho, como os dados de uma câmera, o registro de uma falha ou as etapas de um procedimento.

Inicialmente, os trechos terão aproximadamente 300 a 500 tokens, com ajustes conforme o tipo de documento. Essa faixa foi escolhida para preservar o contexto das informações sem ocupar espaço desnecessário na janela de contexto do modelo de linguagem, que possui um limite de tokens para processar as informações recebidas.

### Metadados

Cada documento e seus respectivos trechos terão metadados para facilitar a organização e a busca de informações na base de conhecimento. Esses dados permitirão que o EngMan Copilot localize conteúdos relacionados ao equipamento ou problema consultado pelo engenheiro de manutenção.

Os metadados previstos incluem tipo de equipamento, TAG, tipo de documento, tipo de falha, data, fonte e versão do documento. Eles serão utilizados conforme as características de cada material, permitindo filtrar as informações e identificar sua origem.


## Privacidade e proteção dos dados

A base de conhecimento do EngMan Copilot não deverá incluir dados pessoais de funcionários, imagens que permitam identificar ocupantes de veículos, informações contratuais confidenciais ou registros internos da Motiva sem autorização. Essa restrição busca proteger informações sensíveis e respeitar os princípios da Lei Geral de Proteção de Dados (LGPD).

Quando não houver acesso autorizado a informações reais, serão utilizados dados fictícios para representar situações relacionadas à manutenção das câmeras CFTV. Esses dados serão identificados como simulados e utilizados exclusivamente para fins acadêmicos, sem serem apresentados como registros reais da Motiva.

