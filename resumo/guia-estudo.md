Este guia de estudos foi estruturado com foco nos tópicos de **Banco de Dados** mais recorrentes em concursos de TI, com ênfase no perfil da banca **Cesgranrio** (responsável pelo Banco do Brasil). Ele integra conceitos técnicos fundamentais e a metodologia de estudos sugerida nas fontes.

---

### 1. Arquitetura e Modelagem de Dados
O projeto de banco de dados é dividido em três etapas de abstração que você deve dominar:
*   **Modelo Conceitual:** O nível mais alto e abstrato, representado pelo **Diagrama Entidade-Relacionamento (DER)**. Foca em "o que" o software deve possuir de acordo com os requisitos.
*   **Modelo Lógico:** Nível intermediário que utiliza a **abordagem relacional**. Aqui, entidades viram tabelas (relações), atributos viram colunas e surgem as chaves primárias e estrangeiras.
*   **Modelo Físico:** A implementação final no **SGBD** (Sistema Gerenciador de Banco de Dados).

**Mapeamento de Relacionamentos (Dica para Prova):**
*   **1:1 (Um para um):** Geralmente resulta em **fusão de tabelas** para evitar junções desnecessárias.
*   **1:N (Um para muitos):** Adiciona-se uma coluna de **chave estrangeira** na tabela do lado "N".
*   **N:N (Muitos para muitos):** Gera obrigatoriamente uma **tabela intermediária** que conterá as chaves das tabelas envolvidas.

---

### 2. Teoria da Normalização
A normalização visa eliminar redundâncias e prevenir anomalias de inserção, exclusão e atualização.
*   **1ª Forma Normal (1FN):** Exige que todos os atributos possuam **valores atômicos** e indivisíveis.
*   **2ª Forma Normal (2FN):** Deve estar na 1FN e não conter **dependências parciais** (atributos não-chave devem depender da totalidade da chave primária composta).
*   **3ª Forma Normal (3FN):** Deve estar na 2FN e remover **dependências transitivas** (um atributo não-chave não pode ser determinado por outro atributo não-chave).
*   **Forma Normal de Boyce-Codd (FNBC):** Restrição severa onde todo determinante deve ser uma **superchave**.
*   **4ª e 5ª FN:** Tratam, respectivamente, de dependências multivaloradas e dependências de junção.

---

### 3. Linguagem SQL (DDL e DML)
Para o Banco do Brasil, priorize o domínio da sintaxe e da ordem lógica de execução das cláusulas.
*   **DDL (Definição):** Comandos `CREATE`, `ALTER`, `DROP` e `TRUNCATE` (este último apaga registros mas mantém a estrutura e **não permite recuperação**).
*   **DML (Manipulação):** Comandos `SELECT`, `INSERT`, `UPDATE` e `DELETE`.
*   **Window Functions (Tema predileto do setor bancário):** Ao contrário do `GROUP BY`, as funções de janela (cláusula `OVER`) realizam cálculos sem colapsar as linhas. Estude `DENSE_RANK()`, `LEAD()` e `LAG()`.
*   **Constraints (Restrições):** `NOT NULL`, `UNIQUE`, `PRIMARY KEY`, `FOREIGN KEY` (integridade referencial) e `CHECK` (validação de condições como "salário > 0").

---

### 4. Transações e Propriedades ACID
Toda transação lógica em um SGBD deve garantir quatro propriedades críticas:
1.  **Atomicidade:** A transação é "tudo ou nada"; se falhar, ocorre o *rollback*.
2.  **Consistência:** Garante que o banco passe de um estado íntegro para outro igualmente válido.
3.  **Isolamento:** Transações simultâneas não devem interferir umas nas outras.
4.  **Durabilidade:** Uma vez confirmado (*commit*), o dado deve sobreviver a falhas de hardware.

---

### 5. Data Warehouse, Data Lake e OLAP
Conceitos fundamentais para a análise estratégica de grandes volumes de dados.
*   **Data Warehouse (DW):** Repositório centralizado, **não volátil** (dados não são alterados após a carga), integrado, orientado por assuntos e variante no tempo. Utiliza o processo **ETL** (Extração, Transformação e Carga).
*   **Data Lake:** Armazena dados brutos (não estruturados) e aplica a modelagem apenas na leitura (**schema-on-read**).
*   **Modelagem Dimensional:**
    *   **Star Schema (Estrela):** Tabelas dimensão não normalizadas ligadas diretamente à tabela de fatos central.
    *   **Snowflake Schema (Floco de Neve):** Tabelas dimensão normalizadas (mais junções, menos espaço).
*   **Operações OLAP:**
    *   **Drill-down:** Detalhamento progressivo (menor granularidade).
    *   **Roll-up:** Agregação/generalização (maior granularidade).
    *   **Slice/Dice:** Recorte de uma fatia ou subcubo de dados.
    *   **Pivot:** Rotação do cubo para nova perspectiva.

---

### 6. Big Data, NoSQL e Machine Learning
*   **Big Data (5 Vs):** Volume, Velocidade, Variedade, Veracidade e Valor.
*   **Teorema CAP:** Em sistemas distribuídos, é impossível garantir simultaneamente **C**onsistência, **A**disponibilidade e Tolerância a **P**artição.
*   **Arquiteturas NoSQL:** Baseadas em documentos (MongoDB), chave-valor (Redis), colunas largas (Cassandra) ou grafos (Neo4j).
*   **Ecossistema Hadoop/Spark:** O **HDFS** é o sistema de arquivos distribuído e o **Spark** otimiza o processamento em memória por meio de **RDDs**.
*   **K-Means:** Algoritmo clássico de **clusterização** (aprendizado não supervisionado) para agrupamento de dados por características similares.

---

### 7. Estratégia de Estudos: O Segundo Cérebro
Dada a carga massiva de sintaxes e arquiteturas, as fontes recomendam o método **PKM (Gestão do Conhecimento Pessoal)**:
1.  **CODE:** **C**apturar o que ressoa, **O**rganizar por ação, **D**estilar a essência (método Feynman) e **E**xpressar através de exercícios.
2.  **PARA:** Organize suas notas em **P**rojetos (ex: BB 2026), **Á**reas (Bancos de Dados), **R**ecursos (Cheat sheets SQL) e **A**rquivos (editais passados).
3.  **Active Recall:** Utilize ferramentas como **Anki** ou plugins do **Obsidian** para criar flashcards e forçar a recuperação da informação, evitando a releitura passiva.
