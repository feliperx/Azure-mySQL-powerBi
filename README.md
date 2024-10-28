# Projeto: Processamento de Dados Simplificado com Power BI e MySQL no Azure

## Descrição do Projeto

Este projeto aplica práticas de processamento e transformação de dados utilizando Power BI e MySQL. O objetivo é criar e configurar um banco de dados em uma instância MySQL no Azure, integrá-lo ao Power BI e realizar transformações e análises, preparando os dados para um modelo estrela.

## Objetivos

- Configurar uma instância MySQL no Azure.
- Criar e popular o banco de dados com os scripts SQL fornecidos.
- Realizar transformações e validações de dados no Power BI para análise.

## Tecnologias Utilizadas

- **Microsoft Azure**: Instância MySQL hospedada para o banco de dados.
- **MySQL Workbench**: Ferramenta para gerenciar e manipular o banco de dados.
- **Power BI**: Ferramenta de BI utilizada para integrar, transformar e visualizar os dados.

## Passo a Passo do Projeto

### 1. Configuração da Instância MySQL no Azure

- **Passo**: Criar uma instância MySQL no portal Azure.
- **Detalhes**: Definir nome, usuário, senha e outras configurações. Obter as credenciais de conexão para uso no MySQL Workbench e Power BI.

### 2. Criação e População do Banco de Dados

- **Script**: `script_bd_company.sql`
  - **Descrição**: Cria as tabelas `employee` e `departament`, incluindo chaves primárias, estrangeiras e restrições.
- **Script**: `insercao_de_dados_e_queries_sql.sql`
  - **Descrição**: Insere dados de exemplo na tabela `employee`.

### 3. Integração com o Power BI

Conectar o Power BI ao banco de dados MySQL no Azure utilizando as credenciais da instância. Carregar os dados das tabelas `employee` e `departament` para iniciar as transformações.

### 4. Transformações de Dados no Power BI

- **Verificação de Cabeçalhos e Tipos de Dados**: Garantir que cabeçalhos e tipos estejam corretos e modificar valores monetários para o tipo double.
- **Verificação de Valores Nulos**:
  - Identificar registros NULL em `Super_ssn`, associando-os a possíveis gerentes.
  - Identificar NULL em `Mgr_ssn` na tabela `departament`. Caso existam, preencher com dados fictícios.
- **Análise e Separação de Colunas Complexas**: Separar colunas como Nome Completo em Nome e Sobrenome.
- **Junções e Mesclas**:
  - Mesclar `employee` com `departament` para associar colaboradores aos departamentos, removendo colunas desnecessárias.
  - Criar uma tabela para listar colaboradores e seus gerentes diretos.
  - Combinar as colunas de Nome e Sobrenome em uma única coluna de Nome Completo.
  - Unificar o nome e localização do departamento para criar combinações únicas `departamento-local`.
- **Agrupamento de Dados**: Agrupar colaboradores por gerente para facilitar análises de equipe e supervisão.

### 5. Explicação das Mesclas

No contexto do Power BI, as operações de mescla foram escolhidas para manter as associações originais das tabelas sem duplicações. Utilizar mescla em vez de atribuição direta permite que as tabelas mantenham a integridade referencial, garantindo consistência para o modelo estrela.

## Estrutura do Banco de Dados

**Tabelas**:

- **employee**: Contém informações sobre cada colaborador, como SSN, nome, endereço, salário e SSN do supervisor.
- **departament**: Armazena dados sobre departamentos, como nome, número, SSN do gerente e datas de criação.
