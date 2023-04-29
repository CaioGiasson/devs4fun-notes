# PWA de Divisão de contas
	* Problemas a serem solucionados:
		* Ao criar um link é necessário dizer do que é o link (exemplo: "Churras", "Almoço", "Niver Fulano")
		* Dividir despesas, por exemplo, em um churrasco, almoço, festa, etc
		* Criação fácil de quadros de despesas, sem precisar que os usuários se cadastrem previamente
	* Funcionalidades
		* Inserir pessoas. Inicialmente cada pessoa participa da divisão total
		* Inserir itens, cada item com um valor
		* Na raiz do link já mostra a lista de pessoas e quanto cada um vai pagar
		* Deve também ter na aplicação uma lista de itens e o valor de cada item
		* Ao inserir cada item, logo abaixo aparece a lista de pessoas, todas selecionadas por padrão. Ao clicar em uma pessoa ela alterna entre selecionada / não selecionada. Ao salvar um item com algumas pessoas não selecionadas o rateio é recalculado considerando que essas pessoas não participam do rateio daquele item
		* Somente quem gerou o link pode editar
		* Ter um botão "Compartilhar", que permite enviar por whatsapp para um ou mais contatos
	* Pendências
		* Nome para a aplicação

## Fluxo básico (MVP)
- Usuário acessa https://divisao-de-contas.devs4.fun
- Aparece uma tela descrevendo o que a aplicação faz e um campo de texto para criar o "nome" do seu rateio
- Usuário digitou um nome para o rateio. Por exemplo: `Churras4fun`
- Sistema cria um link `https://divisao-de-contas.devs4.fun/churras4fun`
- Usuário vê uma tela de "resumo" com valor total do `Churras4fun`. Inicialmente é R$ 0,00
- Usuário vê também uma lista de itens (que tem 0 itens), com um botão "Adicionar item"
	Ao clicar no botão Adicionar Item usuário vai pra tela de cadastrar item
- Usuário vê também uma lista de pessoas (que tem 0 pessoas), com um botão "Adicionar pessoa"
	Ao clicar no botão Adicionar Pessoa usuário vai pra tela de cadastrar pessoa

## Simplificações
- Na MVP não precisa ter dois níveis de usuário. Qualquer pessoa com o link pode editar (e qualquer pessoa com o link tb vê o que foi editado)
- Itens terão somente Nome e Valor
- Pessoas terão somente Valor

## Entidades

### Link
- id
- nome

### Itens
- id
- link
- nome
- valor

### pessoas
- id
- link
- nome

## Frontend
NextJS - ReactJS

## Banco de dados
MySQL

## Backend
NodeJS

## Linguagem
Javascript com Typescript

## Próximo encontro
* Planejar quais endpoints são necessários
* Criar repositório
* Criar projeto
* Criar domínio
[TALVEZ] Publicar em uma máquina virtual com o domínio criado

## Tópicos seguintes
* Documentação e implementação dos endpoints
* Testes
