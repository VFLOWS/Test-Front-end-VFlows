## Funcionalidades

### **Página de Acesso**

O usuário que estiver acessando essa página deverá conseguir informar os seguintes campos:

- campo **CNPJ**, com máscara de CNPJ ao digitar, e deverá ser um CNPJ válido.

- botão “Acessar”

Ao clicar no botão “Acessar”, o sistema deverá:

1. Validar se o CNPJ informador é válido;
   - Caso seja, ir para 2.
   - Caso não seja, enviar mensagem ao usuário: “CNPJ inválido”.
2. Realizar uma pesquisa em um array **users**, através de uma função **login**, utilizando como parâmetro o CNPJ informado.
   - Caso a consulta retorne os dados do CNPJ, abrir a tela `Contratos Vinculados`.
   - Caso a consulta não retorne os dados do CNPJ, enviar mensagem ao usuário: “CNPJ sem contratos ativos.”

### **Página Contratos Vinculados**

O sistema deverá apresentar as seguintes informações para o usuário:

- Consultar um array **contracts**, através da função **getUserContracts** passando como parâmetro o CNPJ informado na tela da consulta. Carregar os dados retornados da consultas conforme abaixo:
- Tela de Seleção de Contratos Vinculados
  - Header com as seguintes informações:
    - Razão Social, texto informativo, não permitido alteração;
    - CNPJ, texto informativo, não permitido alteração;
    - Nome Fantasia, texto informativo, não permitido alteração;
  - Lista dos Contratos Vinculados ao CNPJ contendo:
    - Campo tipo checkbox com opção de selecionar;
    - Nome do Contrato, texto informativo, não permitindo alteração;
    - Código do Contrato, texto informativo, não permitido alteração;
    - Percentual da Retenção Técnica, texto informativo, não permitido alteração;
    - Botão “Detalhes”, tipo botão, permitindo ação de click;
      - (Colocar as infos do modal)
  - Botão “Anterior”, tipo botão, permitindo click:
    - Ao clicar, o sistema deverá retornar a página de `acesso`.
  - Botão “Próxima”, tipo botão, permitindo click:
    - Ao clicar, o sistema deverá validar;
      - Se apenas uma linha foi selecionada, ir para a tela `Dados da Nota Fiscal`
      - Se for selecionada mais de uma linha, retorna mensagem para o usuário: “Somente um Contrato deverá ser selecionado”
      - Se não houve linha selecionada, retornar mensagem para o usuário: “Ao menos um Contrato deverá ser selecionado”

### **Página Dados da Nota Fiscal**

O sistema deverá apresentar as seguintes informações para o usuário:

- Header com as seguintes informações:
  - Razão Social, texto informativo, não permitido alteração;
  - CNPJ, texto informativo, não permitido alteração;
  - Nome Fantasia, texto informativo, não permitido alteração;

O usuário que estiver acessando essa página deverá conseguir informar os seguintes campos:

- campo “Número da Nota”, numérico, permitindo preenchimento
- campo “Data de Emissão”, data, permitindo preenchimento
- campo “Data de Vencimento”, data, permitindo preenchimento
- campo “Valor”, decimal com duas casas decimais, permitindo preenchimento
- campo “Retenção de Impostos”, checkbox, clicável e, ao clicar:
  - Caso campo esteja selecionado:
    - Demonstrar o painel “Dados de Impostos” com os seguintes campos:
    - campo “ISSQN”, decimal com dois inteiros e duas decimais, permitindo preenchimento
    - campo “IRRF”, decimal com dois inteiros e duas decimais, permitindo preenchimento
    - campo “CSLL”, decimal com dois inteiros e duas decimais, permitindo preenchimento
    - campo “COFINS”, decimal com dois inteiros e duas decimais, permitindo preenchimento
    - campo “INSS”, decimal com dois inteiros e duas decimais, permitindo preenchimento
    - campo “PIS”, decimal com dois inteiros e duas decimais, permitindo preenchimento
- campo “Retenção Técnica”, checkbox, clicável e, ao clicar:
  - Demonstrar o painel “Dados da Retenção Técnica” com os seguintes campos:
    - campo “Valor”, decimal com duas casas decimais, com preenchimento baseado no percentual de retenção do contrato;
    - campo “Percentual”, decimal com dois inteiros e duas decimais, com preenchimento baseado no campo de percentual de retenção técnica do contrato;
- botão “Anexar Nota Fiscal”, botão, clicável e, ao clicar, poder anexar um arquivo local;
  - após anexar ao menos um arquivo, deverá ser gerada lista de documentos anexados, onde em cada linha poderá ser excluído o documento;
- Botão “Anterior”, tipo botão, permitindo click:
  - Ao clicar, o sistema deverá retornar a página de seleção de contratos;
- Botão “Próxima”, tipo botão, permitindo click:
  - Ao clicar, o sistema deverá validar;
    - campo “Número da Nota” preenchido;
      - Se sim, ok
      - se não, retornar mensagem para o usuário: “Número da Nota Obrigatório”
    - campo “Data de Emissão”, preenchido e ser uma data válida;
      - Se sim, ok
      - se não, retornar mensagem para o usuário: “Data de Emissão Obrigatório”
    - campo “Data de Vencimento”, preenchido e ser uma data válida:
      - Se sim, ok
      - se não, retornar mensagem para o usuário: “Data de Vencimento Obrigatório”
    - campo “Valor”, preenchido e maior que zero;
      - Se sim, ok
      - se não, retornar mensagem para o usuário: “Valor Obrigatório”
    - campo “Retenção de Impostos”, selecionado;
      - campo “ISSQN”, caso preenchido, maior que zero;
        - Se sim, ok
        - se não, retornar mensagem para o usuário: “ISSQN” deve ser maior que zero”
      - campo “IRRF”, caso preenchido, maior que zero;
        - Se sim, ok
        - se não, retornar mensagem para o usuário: “IRRF” deve ser maior que zero”
      - campo “CSLL”, caso preenchido, maior que zero:
        - Se sim, ok
        - se não, retornar mensagem para o usuário: “CSLL” deve ser maior que zero”
      - campo “COFINS”, caso preenchido, maior que zero:
        - Se sim, ok
        - se não, retornar mensagem para o usuário: “COFINS” deve ser maior que zero”
      - campo “INSS”, caso preenchido, maior que zero:
        - Se sim, ok
        - se não, retornar mensagem para o usuário: “INSS” deve ser maior que zero”
      - campo “PIS”, caso preenchido, maior que zero:
        - Se sim, ok
        - se não, retornar mensagem para o usuário: “PIS” deve ser maior que zero”
    - campo “Retenção Técnica”, selecionado;
      - campo “Valor”, valor deve ter sido calculado baseado no percentual de retenção do contrato;
      - campo “Percentual”, valor deve ser o percentual de retenção técnica do contrato;
    - Se todos os campos estiverem "ok":
      - O sistema deverá chamar uma função **sendData** enviando as informações preenchidas como parâmetro. Essa função deverá imprimir no terminal (`console.log`), e retornar ao usuário a seguinte mensagem “Solicitação 999999 foi enviada com sucesso.“ e ir para a tela `Página de acesso`
