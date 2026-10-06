# Repositório de Aulas — PAOO (Programação Avançada Orientada a Objetos - Fatec Ipiranga)

Este repositório contém os códigos e anotações desenvolvidos durante as aulas da disciplina de **PAOO** na **Fatec Ipiranga** (Semestre 2025/2).  
O foco principal deste projeto é o estudo avançado de JavaScript (Node.js), abordando desde os fundamentos de escopo léxico até a manipulação de assincronismo e consumo de APIs externas.

---

## Funcionalidades e Tópicos Abordados

* **Closures e Funções de Alta Ordem:** Criação de funções que preservam o ambiente/escopo em que foram criadas e passagem de funções como parâmetros ou retornos.
* **Manipulação de Objetos Literais:** Estruturação, iteração e filtragem de dados complexos em JavaScript.
* **Síncrono vs Assíncrono:** Demonstração prática do *Event Loop* do Node.js, ordem de execução e a transição do temido *Callback Hell* para estruturas modernas.
* **Implementação de Promises:** Criação, resolução (`resolve`), rejeição (`reject`) e encadeamento de métodos (`.then()` e `.catch()`) para processamentos demorados.
* **Consumo de API Externa (Weather App):** Integração real com a API do **OpenWeatherMap** (5 Day/3 Hour forecast) para busca de dados meteorológicos dinâmicos.

---

## Arquitetura e Estrutura dos Arquivos

O repositório está dividido conceitualmente entre os fundamentos da linguagem e a aplicação prática:

| Arquivo / Diretório | Descrição |
| :--- | :--- |
| `js/intro/` | Anotações detalhadas de aula contendo códigos explicativos sobre Closures, Callbacks, Arrays/Objetos e Promises puras. |
| `js/previsao_do_tempo/index.js` | Script principal que constrói a URL dinamicamente e dispara a requisição HTTP via Axios para a API do OpenWeatherMap. |
| `js/previsao_do_tempo/package.json` | Arquivo de manifesto do Node.js contendo os scripts de execução (`start`, `dev`) e o mapeamento das dependências. |
| `js/previsao_do_tempo/.env` | (Omitido do controle de versão) Arquivo de parametrização para proteção de dados sensíveis (Chave de API `APPID`, `PROTOCOL`, `BASE_URL`). |

---

## Aprendizado Progressivo de Conceitos

Através do desenvolvimento dos scripts de aula, foi possível consolidar uma evolução clara de conceitos essenciais para o ecossistema JavaScript/Node.js:

### 1. Escopo e Closures
* **Retenção de Memória:** Compreensão de como uma função filha "carrega como uma mochila" as variáveis de seu contexto léxico pai, permitindo a construção de fábricas de funções (ex: `saudacoesFactory`).
* **High-Order Functions:** Entendimento profundo de invocações sequenciais (ex: `g()()`) e passagem de lógicas por referência.

### 2. Controle de Fluxo Assíncrono
* **O Problema (Callback Hell):** Análise da complexidade de operações de I/O (*I/O bound*) usando o módulo nativo `fs` (File System), onde callbacks aninhados dificultam a manutenção e leitura.
* **A Solução (Promises):** Refatoração mental e prática para o uso de Promises, tratando o sucesso ou falha da operação no futuro de forma linear e previsível.

### 3. Integração e Segurança em Node.js
* **Axios HTTP Client:** Substituição de ferramentas rudimentares pelo Axios para disparar requisições GET limpas e orientadas a Promise.
* **Variáveis de Ambiente (`dotenv`):** Separação estrita entre código e configuração. Uso do `process.env` para carregar chaves de API dinamicamente, garantindo que credenciais sensíveis não sejam enviadas ao repositório via `.gitignore`.

---

## Como Executar o Projeto de Previsão do Tempo

### Pré-requisitos
* **Node.js** instalado.
* Conta ativa no [OpenWeatherMap](https://openweathermap.org/api) e uma chave de API válida (App ID).

### Passos para configuração e execução:

1. **Acesse o diretório do projeto:**
   ```bash
   cd js/previsao_do_tempo

2. **Instale as dependências do pacote (axios e dotenv):**
   ```bash
   npm install

3. **Configure as Variáveis de Ambiente:**

    Crie um arquivo chamado .env na raiz da pasta previsao_do_tempo e preencha com as suas credenciais:
    ```bash
    PROTOCOL=https
    BASE_URL=api.openweathermap.org/data/2.5/forecast
    APPID=sua_chave_de_api_aqui
    UNITS=metric
    Q=Sao Paulo
    LANG=pt_br
    CNT=5

4. **Execute a aplicação:**

   ```bash
   Para rodar com monitoramento contínuo (modo dev):
   npm run dev
  
   Para rodar no modo padrão:
   npm start
