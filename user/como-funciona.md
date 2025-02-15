# Como Funciona?

O SONIC é um cluster com Slurm, o que significa que jobs são submetidos para esse serviço, sendo ele responsável por organizar uma fila com esses jobs. Existem dois tipos de nós computacionais (ou computadores) disponíveis: nós de login e nós de computação. 
Estando em um nó login é possível, apenas, realizar um pedido de recursos ao Slurm para executar sua aplicação. Para rodar uma aplicação qualquer, esta deve ser rodada em nós de computação, ninguém tem acesso direto a esses nós, exceto por meio de jobs interativos. 

Nós de login tem como função a preparação dos seus experimentos e de suas aplicações. Nele você terá acesso a um espaço de armazenamento visível pelo cluster inteiro, ou seja, o que for feito nesse espaço é acessível em todos os nós. Nestes tipos de nós é esperado que você baixe (ou git clone) seu código, transfira arquivos necessários para seus experimentos, compile seu código, modifique seus arquivos, e por fim, submeta *jobs*. Algo importante a se lembrar é: **NÃO É PARA RODAR EXPERIMENTOS NOS NÓS DE LOGIN!!!** Esses nós são compartilhados com todos usuários com o fim de realizar tarefas simples neles, como verificar uma saída, ou preparar um experimento. Uma pessoa rodando tarefas intensivas neste nó atrapalha a todos. Sobre compilação, evitar usar mais de 10% dos cores disponíveis para make paralelo (mínimo de 1 core obviamente).

Nós de computação são onde você executará seus experimentos. Ao ganhar uma alocação apenas você terá acesso ao nó alocado pelo período de alocação. Ao fim da alocação os recursos usados são retornados à fila, para serem usados por outro job. Todo job tem um tempo limite (se não for definido pelo usuário é usado um valor default). Chegando ao fim desse tempo, o Slurm mata sua aplicação e devolve o nó *computacional* para a fila. Caso haja dados armazenados localmente, esses podem-se considerar perdidos. Para evitar experimentos quebrados no meio do caminho é recomendado que se coloque mais tempo que se julgue necessário. PoR qUe NÃo sIMpLesMEntE coLoCAr 100 anOs ENtãO? Pode fazer isso, mas depois você perde prioridade para rodar os experimentos (a ver mais a frente). Atualmente não existe limite de uso. Se houver recursos livres você poderá usá-los.

No caso, o nó de login trata-se da máquina `phocus4`. E a partição das gorgonas, que por sua vez engloba 7 máquinas númeradas de 1 a 7 e 10, são nós de computação (e.g., `gorgona1`). Conforme supracitado, os usuários tem dentro do cluster um espaço de armazenamento que é visivel ao cluster inteiro. É nesse espaço que ficaram os aquivos de código (\*.py, .\*ipynb, ou afins) e arquivos de bash (\*.sh) i.e., scripts para prompts de comando. Como localizar e lidar com esses diretórios é detalhado em [Como submeter jobs](submissao-slurm.md).

___

# TLDR
 - Nós de comutação e login
 - Existe espaço de armazenamento global, acessível por todos os nós
 - Prepare seus experimentos no nó de login (`phocus4`)
 - **NUNCA** rodar experimentos no nó de login
 - Submeta jobs a partir do nó de login para execução em nós de computação
 - Alocações tem tempo máximo, se estourar o tempo para tudo e perde-se o que não tiver salvo
 - Coloque mais tempo do que julga ser necessário nas alocações, tente apenas acertar a ordem de grandeza do tempo necessário (e.g., acho que deve demorar umas 4 hrs, vou pedir 10 hrs)
 - Alocações são exclusivas: se você tem um nó alocado, ninguém mais pode acessá-lo enquanto você tiver a alocação

___


[Anterior tópico: README.md](../README.md)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[Próximo tópico: Acessando o cluster](acesso.md)

