# Diretrizes do Projeto Semestral: Programação para Internet
## Período Letivo: 2026.2

Este documento estabelece as diretrizes fundamentais, os requisitos técnicos e os critérios de avaliação para o desenvolvimento do projeto prático da disciplina de **Programação para Internet**. O objetivo deste trabalho é vivenciar o ciclo completo de desenvolvimento de uma aplicação web moderna utilizando ferramentas, fluxos de trabalho e padrões exigidos pelo mercado profissional.

## 1. Disposições Gerais e Formação de Equipes

* **Constituição dos Grupos:** As equipes deverão ser formadas por no **máximo 4 estudantes**.
> **Aviso Rigoroso sobre o Limite de Integrantes:** Por questões de equalização de carga de trabalho e gerenciamento pedagógico, o limite de 4 alunos por equipe é estrito. **Não insistam: não serão abertas exceções sob nenhuma hipótese para inclusão de um 5º componente.** Os grupos que não atingirem o limite podem rodar com menos integrantes, se necessário.
* **Ciclo de Vida da Equipe:** Uma vez consolidados e validados, os grupos permanecerão inalterados e serão utilizados para o desenvolvimento de todas as etapas práticas até o encerramento do semestre letivo de **2026.2**.

## 2. Ecossistema de Desenvolvimento (Stack Técnica)

O projeto deverá ser construído seguindo rigidamente as seguintes especificações tecnológicas de infraestrutura e arquitetura:

* **Ambiente Backend (Obrigatório):** Toda a lógica de negócio do servidor, rotas e processamento deve ser implementada utilizando a linguagem **Python** e o micro-framework **Flask**.
* **Camada de Persistência de Dados (Obrigatório):** É proibida a utilização de armazenamento temporário em memória volátil (como listas ou dicionários em escopo global) ou arquivos de texto puro para produção. O projeto deve obrigatoriamente realizar a persistência de dados utilizando um Sistema Gerenciador de Banco de Dados (SGBD) relacional, limitando-se às seguintes opções:
    * **MySQL**
    * **PostgreSQL**
* **Camada de Frontend (Livre Escolha):** Fica a critério e maturidade de cada equipe definir a abordagem visual. São permitidas:
    * **Renderização no Servidor (SSR):** Utilização do motor de templates padrão do Flask (**Jinja2**), integrando HTML5, CSS3 e Javascript puro ou frameworks CSS (Bootstrap, Tailwind, etc.).
    * **Arquitetura Desacoplada (API REST):** O backend Flask atuará exclusivamente como uma API RESTful fornecendo dados estruturados (JSON), os quais serão consumidos por uma Single Page Application (SPA) estruturada em frameworks modernos no cliente, como o **Angular**.

## 3. Governança, Versionamento e DevOps no GitHub

O gerenciamento do código-fonte e o ritmo de entrega do projeto seguirão práticas formais de engenharia de software através do uso de ferramentas de versionamento.

* **Hospedagem de Código:** O projeto deve obrigatoriamente residir dentro da **Organização oficial** criada no GitHub pelo professor para a turma. Repositórios criados fora dessa organização em perfis pessoais dos estudantes não serão computados nem avaliados.
* **Monitoramento de Participação Individual:** A nota de cada estudante não será atribuída unicamente pelo resultado coletivo. O professor utilizará as métricas internas do GitHub para auditoria individual, avaliando a constância e relevância de:
    * **Commits:** Histórico coerente e mensagens claras que evidenciem quem escreveu cada bloco do código.
    * **Pull Requests (PRs):** Uso obrigatório de PRs para a integração de novas funcionalidades, exercitando revisões de código entre os membros da equipe.
    * **Issues:** Planejamento e distribuição de tarefas documentadas na aba de gerenciamento do repositório.

### Configuração Obrigatória de Integração Contínua (CI) via GitHub Actions

Para mitigar falhas de integração e garantir a estabilidade mútua do código, cada equipe deverá implementar um fluxo automatizado de validação (*Workflow*) desde o primeiro dia do repositório ativo.

Em termos profissionais, CI garante que toda modificação inserida no código passe por testes e checagens automáticas num servidor independente, assegurando que o novo código não quebrou o projeto existente. Mesmo que a equipe nunca tenha utilizado o recurso, a configuração básica é simples e obrigatória.

O arquivo de configuração do pipeline deve ser criado no caminho exato `.github/workflows/ci.yml` na raiz do projeto e deve automatizar o seguinte comportamento a cada `push` ou `pull_request` direcionado à ramificação estável do projeto (ex: `main` ou `develop`):

1.  **Provisionamento do Ambiente:** Subir uma imagem virtual controlada (ex: Ubuntu Linux) e instalar a versão estável do Python adotada pela equipe.
2.  **Resolução de Dependências:** Instalar automaticamente os pacotes obrigatórios do projeto executando o isolamento do ambiente e o comando `pip install -r requirements.txt`.
3.  **Validação de Boas Práticas (Linter):** Executar ferramentas de checagem estática de sintaxe e estilo de código Python (como `flake8`, `black` ou `pylint`) para garantir conformidade com as regras da comunidade (PEP 8).

>**A Regra da Esteira Verde:** O status do pipeline do GitHub Actions deve manter-se prioritariamente em conformidade ("Check Verde"). Commits que apresentarem falhas de build ou erros de linter ("X Vermelho") sem correção ágil por parte do grupo indicarão negligência técnica e afetarão diretamente os critérios de avaliação individual e coletiva de governança.

## 4. Dinâmica de Escolha e Validação do Tema

* **Regra de Exclusividade:** Não será permitida a repetição de temas em sala de aula. O critério de reserva de um tema será baseado na ordem cronológica de aprovação do escopo.
* **Proibição de Projetos Clichês:** Sistemas demasiadamente genéricos que funcionam meramente como formulários de cadastro simples estão explicitamente proibidos. Exemplos de temas banidos antecipadamente:
    * Sistemas convencionais de controle de biblioteca (livros/empréstimos).
    * Sistemas genéricos de cadastro de usuários, clínicas ou petshops sem lógica de negócio densa.
    * Agendas de contatos ou listas de tarefas (To-Do Lists) tradicionais.
> Os projetos devem possuir um contexto de mercado real ou propor soluções criativas para problemas específicos (ex: uma plataforma integrada para monitoramento e troca de figurinhas colecionáveis da Copa do Mundo de 2026).*
* **Processo de Submissão e Validação:** A ideia deve partir da equipe. O grupo deverá detalhar o escopo inicial, descrevendo os principais objetivos da aplicação e os requisitos funcionais vislumbrados. Esse texto deve ser escrito diretamente no arquivo `README.md` principal do repositório oficial da equipe criado dentro da Organização. O professor revisará o arquivo e efetuará a aprovação ou solicitará ajustes no escopo de forma presencial ou via comentários no próprio GitHub.

## 5. Processo de Avaliação e Entregas (Ciclo de Vida)

A avaliação do projeto ocorrerá de forma contínua, incremental e processual ao longo do período letivo, dividida nos seguintes marcos de acompanhamento:

| Etapa do Projeto | Descrição do Marco de Entrega | Formato de Avaliação |
| :--- | :--- | :--- |
| **Acompanhamento de Commits** | Avaliação regular e contínua do ritmo de postagem e distribuição das tarefas entre os integrantes do grupo via Git. | Auditoria assíncrona nas métricas do GitHub. |
| **Protótipo** | Estruturação inicial da arquitetura de navegação, mapeamento de banco de dados e as primeiras interfaces estáticas das telas. | Apresentação em laboratório / Feedback intermediário. |
| **MVP (Minimum Viable Product)** | Produto Mínimo Viável. Aplicação com as rotas principais integradas ao SGBD executando as operações fundamentais do negócio de ponta a ponta. | Banca parcial de validação técnica. |
| **Apresentações Parciais e Finais** | Apresentações para a turma demonstrando a evolução do projeto, desafios encontrados, soluções de arquitetura e defesa do software rodando ao vivo. | Avaliação da postura técnica e demonstração prática do software. 