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

