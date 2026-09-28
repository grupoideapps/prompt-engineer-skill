# Técnicas Avançadas de Prompting

Para tarefas complexas que exigem raciocínio profundo, precisão ou criatividade, utilize estas técnicas avançadas em conjunto com a estrutura de prompt obrigatória.

### 1. Chain-of-Thought (CoT) Prompting

**O que é**: Instruir o LLM a detalhar seu processo de raciocínio passo a passo antes de chegar à resposta final. É a implementação prática da seção **SPECIFICS -> Processo de execução**.

**Quando usar**: Problemas que envolvem múltiplas etapas de cálculo, inferência ou lógica.

**Exemplo**:

> **Prompt com Chain-of-Thought**:
> `Q: A cafeteria tinha 23 maçãs. Se eles usaram 20 para fazer o almoço e compraram mais 6, quantas maçãs eles têm?`
> `A: Vamos analisar passo a passo:
> 1. Maçãs iniciais: 23
> 2. Maçãs usadas: 20. Então, 23 - 20 = 3.
> 3. Maçãs compradas: 6. Então, 3 + 6 = 9.
> Resposta: Eles têm 9 maçãs.`

### 2. Few-Shot Prompting

**O que é**: Fornecer ao LLM alguns exemplos (shots) de pares de entrada/saída para demonstrar o padrão desejado. É uma forma poderosa de especificar o **Formato de saída** na seção **SPECIFICS**.

**Quando usar**: Quando o formato de saída é muito específico, o estilo é sutil ou a tarefa é nova para o modelo.

**Exemplo**:

> **Prompt com Few-Shot**:
> `Traduza o nome do filme para emoji.
>
> De volta para o Futuro: 👨‍🔬🚗🕰️
> Star Wars: 🌟⚔️🤖
> O Senhor dos Anéis: 🧙‍♂️💍🌋
> Matrix:`

### 3. Retrieval-Augmented Generation (RAG)

**O que é**: Aumentar o conhecimento do LLM com informações externas. Em vez de depender apenas de seus dados de treinamento, o modelo consulta uma base de dados externa (ex: documentos, artigos, banco de dados) para obter informações relevantes antes de responder. É a aplicação formal da seção **INPUTS / DADOS**.

**Quando usar**: Quando a tarefa requer conhecimento muito específico, recente ou proprietário que não está nos dados de treinamento do modelo.

**Como implementar**:
1.  Identifique a base de conhecimento relevante.
2.  Use uma ferramenta de busca (vector search) para encontrar os trechos mais relevantes para a pergunta do usuário.
3.  Insira esses trechos no prompt, dentro da seção **INPUTS / DADOS**.
4.  Instrua o LLM a basear sua resposta estritamente nas informações fornecidas.

### 4. Prompt Chaining (Encadeamento de Prompts)

**O que é**: Decompor uma tarefa complexa em uma série de prompts mais simples, onde a saída de um prompt se torna a entrada do próximo. Isso reflete um **Processo de execução** bem definido na seção **SPECIFICS**.

**Quando usar**: Para tarefas muito complexas que um único prompt não consegue resolver de forma confiável.

**Exemplo**: Criar um relatório de mercado.
-   **Prompt 1**: `Analise os dados de vendas [dados.csv] e identifique os 5 produtos mais vendidos.`
-   **Prompt 2**: `Para cada um dos 5 produtos identificados, pesquise os 3 principais concorrentes.`
-   **Prompt 3**: `Com base na lista de produtos e concorrentes, escreva um relatório resumido sobre o posicionamento de mercado de cada produto.`

### 5. Self-Correction / Critique Prompting

**O que é**: Instruir o modelo a revisar e criticar sua própria resposta antes de entregá-la. É a implementação do **Protocolo de Validação Final** na seção **NOTES**.

**Quando usar**: Em todas as tarefas onde a qualidade e a precisão são críticas.

**Exemplo**:

> `...[Resto do prompt]...
> Antes de finalizar, revise sua resposta. Ela atende a todos os critérios da seção TASK? O formato de saída está correto? Há alguma ambiguidade? Corrija a si mesmo e forneça apenas a versão final e aprimorada.`

### 6. Step-Back Prompting

**O que é**: Ensinar o modelo a "dar um passo para trás" para pensar em conceitos e princípios gerais antes de mergulhar na pergunta específica. Isso ajuda a ancorar o raciocínio e melhora a qualidade da resposta.

**Quando usar**: Para perguntas complexas ou de nicho, onde entender o contexto mais amplo é fundamental.

**Exemplo**:

> **Pergunta**: `Como posso implementar a equalização de histograma para uma imagem em tons de cinza usando a biblioteca X?`
>
> **Prompt com Step-Back**:
> `Dê um passo para trás. Primeiro, explique o que é equalização de histograma em processamento de imagens e qual o seu objetivo. Em seguida, forneça o código para implementar a equalização de histograma para uma imagem em tons de cinza usando a biblioteca X, explicando cada passo.`

### 7. Prompting de Rejeição Deliberada

**O que é**: Instruir o modelo a se recusar a responder se não tiver confiança suficiente ou se a pergunta for baseada em premissas falsas. É a implementação do **Protocolo de Incerteza**.

**Quando usar**: Em aplicações onde a precisão factual é crítica.

**Exemplo**:

> `...[Resto do prompt]...
> Se a pergunta for ambígua, enganosa ou se você não tiver certeza da resposta, responda com "Não tenho informações suficientes para responder a essa pergunta."`
