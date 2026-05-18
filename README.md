# projeto-banco-de-dados
Repositório acadêmico com alguns modelos de banco de dados

# tb_estacionamento 

O código desenha o esqueleto de um banco de dados para gerenciar uma frota de veículos e o uso de um estacionamento corporativo.

Ele organiza as informações de uma empresa que precisa controlar exatamente o seguinte:

Pessoas: Quem são os funcionários, em quais setores trabalham e quais são seus cargos.

Veículos: Quais carros estão sob responsabilidade da empresa ou dos funcionários (registrando a placa, a marca e o modelo).

Movimentação: O controle da catraca/cancelas do estacionamento, gerando um número de ticket e registrando a data e hora exatas em que um veículo (identificado pela placa) entrou e saiu.

Chave Primária (Identificador Único): É o que garante que um registro não seja confundido com outro. No seu modelo, o cpf é a chave primária do Funcionário, a placa é a do Veículo e o nr_ticket é a do Estacionamento.

Chave Estrangeira (A Ponte de Ligação): É quando a chave primária de uma tabela aparece dentro de outra tabela para criar a relação. Por exemplo, na tabela tb_estacionamento, existe o campo tb_veiculo_placa. Isso significa que o ticket do estacionamento "puxa" os dados do carro através da placa dele, conectando as duas coisas sem precisar recadastrar o carro a cada nova entrada.

# tb_loja_departamento

O código desenha a estrutura de um banco de dados para gerenciar as vendas de uma loja de departamentos (ou rede varejista).

Ele organiza as informações para que a empresa tenha controle total sobre a sua operação comercial, registrando:

Produtos: O que está sendo vendido e qual o seu valor (detalhe: no código, a tabela foi escrita com um pequeno erro de digitação como tb_prooduto).

Estrutura de Vendas: Quem são os vendedores e a qual filial (identificada pelo CNPJ) eles pertencem.

Geografia/Localização: Onde as vendas ou filiais estão localizadas, separando isso em Cidades e Estados.

A Venda em si: O registro principal que une tudo isso. Cada venda guarda a data, o valor total, qual produto foi vendido, quem foi o vendedor e em qual cidade a venda ocorreu.

Chave Primária (Identificador Único): É o "RG" de cada registro. Por exemplo: o cnpj é a chave primária da Filial; a matricula é a chave do Vendedor; e o nr_venda (número da venda) é a chave da Venda.

Chave Estrangeira (A Ponte de Ligação): É como as tabelas conversam. A tabela central desse sistema é a tb_venda. Nela, não está escrito o nome do produto ou do vendedor. Em vez disso, ela possui as chaves estrangeiras tb_prooduto_cd_produto e tb_vendedor_matricula. Quando o sistema quer saber quem vendeu, ele pega a matrícula registrada na venda, vai até a tabela de Vendedores e "puxa" os dados completos dele. Da mesma forma, a Cidade (tb_cidade) tem uma chave apontando para o Estado (tb_estado_cd_estado), criando um efeito cascata de organização.

# tb_vd

O código desenha a estrutura de um banco de dados para gerenciar uma Videolocadora (ou um sistema de aluguel de mídias/DVDs).

Ele organiza as informações para que o estabelecimento tenha controle sobre o seu acervo e as suas locações, registrando exatamente o seguinte:

Acervo (Catálogo): Quais são os filmes/DVDs disponíveis (tb_titulo_dvd), a qual gênero eles pertencem (Ação, Comédia, etc. em tb_genero) e de qual distribuidora eles vieram (tb_distribuidora).

Clientes: Quem são as pessoas que alugam os filmes, guardando dados pessoais como CPF, nome, data de nascimento, endereço e telefone (tb_cliente).

Aluguéis (Movimentação): O registro principal do negócio (rl_aluguel), que anota o número da locação, a data em que ocorreu, qual cliente alugou e qual filme foi levado.

Chave Primária (Identificador Único): É o código exclusivo de cada item. O cd_titulo garante que um DVD não seja confundido com outro; o cd_genero identifica o gênero; e o nr_aluguel é o número do recibo daquela locação. (Nota técnica: no código do tb_cliente, vários campos como nome e endereço foram marcados acidentalmente como chaves primárias junto com o CPF, o que é um erro comum de modelagem na ferramenta, pois apenas o CPF deveria ser o identificador único).

Chave Estrangeira (A Ponte de Ligação): É o que faz o sistema funcionar como uma teia inteligente. A tabela central de movimentação é a rl_aluguel. Para registrar que o "João" alugou "Matrix", essa tabela não escreve esses nomes. Ela "puxa" o código do título (tb_titulo_dvd_cd_titulo) e os dados do cliente que fez a locação. Assim, se o cliente mudar de telefone ou endereço na tabela de Clientes, a locadora não perde o histórico de aluguéis dele, pois tudo está conectado pelos códigos, e não por textos soltos.

