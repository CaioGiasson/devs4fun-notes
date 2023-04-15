# Devs4Fun
Anotações referentes às práticas de programação do Devs4Fun

## ENCONTRO ZERO - 2023-04-15
* Levantamos algumas sugestões de projetos para serem temas de estudo/práticas
* Metodologia de desenvolvimento das aplicações
	Cada aplicação possui ao menos 4 etapas
	* Arquitetura/Projeto - Definições de quais funcionalidades básicas a aplicação vai ter
	* Backend - Rodando localmente. Vamos usar, de modo geral, a metodologia Backend first, exceto quando não é aplicável
	* Frontend - Rodando localmente
	* Deploy (CI/CD) - Publicar a aplicação e automatizar alguns processos

## Aplicações para desenvolvermos
* Divisão de contas, PWA
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

* Aplicação de anotações
	* Aplicação inspiradora: 
		* Dontpad
	* Problemas a serem solucionados:
		* Segurança - Dontpad não permite colocar senha em um link
		* Formatação - Dontpad não usa fonte monospace
		* Conforto - Dontpad usa um tema de cores muito claro/brilhante (não tem dark mode)
	* Funcionalidades
		* Na raiz do site mostrar um campo de texto que permite criar um link (por padrão, sem senha)
		* Se a pessoa acessar diretamente pela URL, tem duas possibilidades:
			1. Link já existe. Se o link tiver senha, a tela pede a senha antes de mostrar o conteúdo. Caso contrário, já mostra.
			2. Link não existe. Nesse caso ele é criado, sem senha
		* Fonte monoespaçada, como o VSCode. Utilizar uma fonte do fonts.google.com para evitar problemas de licença
		* Ao menos dois temas (Dark mode e Light mode). Pesquisar paletas de cores
		* Bloqueio de link. É possível definir uma senha para um link, mas para definir uma senha é necessário informar um e-mail (para recuperar essa senha, se necessário). Informar que o e-mail não será utilizado para entrar em contato.
		* Para futuro: Permitir alterar entre o modo monospace e o modo rich text 
		* Ter um modo "leitor" e um modo "editor"
		* Funcionalidade de compartilhar link. Versões compartilhadas devem ser somente leitura.
		* Estudar uma forma de contornar a concorrência de gravação de dados no backend, para permitir mais de um editor simultâneo

* Quadro Kanban simples
	* Aplicação inspiradora: 
		* Trello
	* Problemas a serem solucionados:
		* Criar facilmente um quadro sem precisar de cadastro, ou seja, com link fácil similar ao dontpad
	* Funcionalidades
		* Na raiz do site mostrar um campo de texto que permite criar um link para um quadro(por padrão, sem senha)
		* Assim que criar um quadro o usuário já cai na tela inicial do quadro. Cada quadro começa com uma coluna, com título "A fazer"
		* A pessoa pode adicionar colunas. Para adicionar uma coluna é necessário informar um título para essa coluna
		* No topo de cada coluna deve ter dois ícones
			* Lápis, para editar o título da coluna
			* Lixeira, para remover a coluna
				* Ao clicar para remover, se tiver tarefas na coluna o usuário é perguntado se quer remover as tarefas ou mover para a primeira coluna. Não há terceira opção, mas ainda é possível cancelar.
		* O usuário pode alterar a ordem das colunas clicando e arrastando pelo título da coluna
		* Dentro de cada coluna, no topo, tem um "card" como uma tarefa, mas reduzido em altura e somente com um botão "+". Ao clicar ali o usuário precisa definir um texto para ficar dentro do card. Cada card tem no máximo 140 caracteres.
		* Ao clicar e arrastar um card é possível mover ele para outra coluna ou ainda mudar a posição dele dentro da mesma coluna.
		* O quadro deve se atualizar automaticamente de tempos em tempos, para caso outra pessoa tenha editado seu conteúdo
		* Modo "somente leitura"
		* Deve haver um link para compartilhamento. Antes de compartilhar deve ser perguntado ao usuário se é um link somente leitura ou editor
		* Proteção para evitar colisões: Enviar sempre o estado antes e depois de uma alteração, e o servidor valida se o estado atual é compatível com o "antes", e só se for compatível, salva o "depois"


