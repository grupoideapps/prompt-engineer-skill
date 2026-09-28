# Estrutura Obrigatória para Geração de Prompts

Para garantir a máxima eficácia, clareza e consistência, todo prompt gerado por esta skill **DEVE** seguir a estrutura detalhada abaixo. Cada seção tem um propósito específico e contribui para a qualidade da resposta final do LLM.

---

### 1. ROLE (Papel)

**Propósito**: Definir a persona do LLM para que ele adote um tom, estilo e nível de conhecimento específicos.

**Instruções**:
- Defina quem o modelo deve ser, com especialidade, escopo e estilo de raciocínio.
- É permitido combinar papéis quando necessário (ex.: "Você é um estrategista de marketing e um redator criativo"), desde que não haja conflito de interesses entre os papéis.

**Exemplo**:
> `Você é um analista de dados sênior com especialização em visualização de dados e um comunicador eficaz, capaz de traduzir insights complexos em recomendações de negócios acionáveis.`

### 2. TASK (Tarefa)

**Propósito**: Descrever a entrega final de forma clara e inequívoca.

**Instruções**:
- Comece a descrição com um verbo de ação forte (ex: crie, analise, compare, escreva, planeje).
- Inclua um critério de sucesso claro: o que torna a resposta boa, completa e útil para o objetivo final.

**Exemplo**:
> `Crie um relatório de análise de sentimento a partir dos dados de feedback do cliente. O sucesso será medido pela clareza na identificação dos 3 principais temas positivos e 3 negativos, e pela profundidade das recomendações para cada tema.`

### 3. INPUTS / DADOS

**Propósito**: Fornecer todos os fatos, dados brutos e restrições objetivas que o LLM deve usar.

**Instruções**:
- Liste apenas o que é fato e foi fornecido pelo usuário (variáveis, textos, links, tabelas, números).
- Se uma informação crucial não foi fornecida, não a invente. Marque-a explicitamente como `[DADO AUSENTE]`.

**Exemplo**:
> `- Texto para análise: [texto completo do feedback do cliente]
> - Período da análise: Q4 2023
> - Nome do produto: Produto X
> - [DADO AUSENTE]: Dados demográficos dos clientes`

### 4. CONTEXT (Contexto)

**Propósito**: Descrever o cenário, o público-alvo e a intenção por trás da tarefa.

**Instruções**:
- Explique o cenário (ex: reunião de planejamento, post para blog), o público-alvo (ex: C-level, desenvolvedores, público leigo), o canal (email, post, documento, roteiro) e o objetivo prático (por que isso será usado e por quem).

**Exemplo**:
> `Este relatório será apresentado à diretoria de produto para decidir sobre as prioridades de desenvolvimento para o próximo trimestre. A linguagem deve ser profissional e direta, focada em impacto de negócio.`

### 5. SPECIFICS (Especificações)

**Propósito**: Detalhar o processo de execução e o formato da saída.

**Instruções**:
- **Processo de execução**: Defina as etapas que o modelo deve seguir (ex: "1. Leia o texto. 2. Identifique as entidades. 3. Classifique o sentimento."). Inclua checagens internas de coerência.
- **Formato de saída**: Seja exato sobre a estrutura (títulos, lista numerada, tabela com colunas específicas, JSON, checklist). Defina o nível de detalhe e limites (palavras, seções).
- **Qualidade**: Liste itens obrigatórios a serem incluídos (ex: incluir exemplos, riscos, alternativas, recomendação final).

**Exemplo**:
> `- Processo: 1. Analise o sentimento de cada frase. 2. Agrupe por temas. 3. Sintetize os achados.
> - Formato de Saída: Um documento Markdown com:
>   - Título: "Análise de Sentimento - Q4 2023"
>   - Seção "Temas Positivos" com 3 itens em lista.
>   - Seção "Temas Negativos" com 3 itens em lista.
>   - Uma tabela com colunas | Tema | Frequência | Recomendação |.
> - Qualidade: Cada recomendação deve ser acionável e específica.`

### 6. NOTES (Notas)

**Propósito**: Definir restrições, limites e protocolos para lidar com incertezas.

**Instruções**:
- **Restrições e Limites**: O que evitar (jargão excessivo, tom informal), proibições (não mencionar concorrentes), compliance, privacidade.
- **Protocolo de Incerteza**: Defina o que fazer se faltar um dado. (ex: "Se faltar um dado essencial, faça até 2 perguntas para esclarecer antes de responder.", "Se houver múltiplas interpretações, apresente as 2 mais prováveis e peça uma escolha.").
- **Validação Final**: Inclua um checklist final que o modelo deve confirmar antes de entregar a resposta (ex: "Validação: 1. Verifiquei se todos os temas foram cobertos. 2. Confirmei se o formato de saída está correto. 3. Garanti que nenhuma informação pessoal foi exposta.").

**Exemplo**:
> `- Restrições: Evite linguagem excessivamente técnica. Não prometa funcionalidades futuras.
> - Protocolo de Incerteza: Se um feedback for ambíguo, classifique-o como "Neutro" e liste-o em uma seção separada para revisão manual.
> - Validação Final: Confirme que o relatório não excede 500 palavras.`
