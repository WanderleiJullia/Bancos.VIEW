# Bancos.VIEW
Atividade a seguir tem objetivo de estar complementando a lista de tarefas solicitadas para AC2. Possui como principal atividade a utilização de VIEW, que é utilizado no bancos de dados para a visuzalização de dados especificos de uma ou mais tabelas. 
## Exercicios 

# Crie uma view que mostra todos os produtos e suas respectivas marcas; 
![image](https://github.com/WanderleiJullia/Bancos.VIEW/assets/144744092/db77f383-2db5-4f59-8b85-4e0797578240)

``` SQL
Inserir o código aqui

create or replace view Produtos_e_marcas as select
prd_nome   'Nome',
mrc_nome   'Marca'
from 
Produtos left join marcas 
on Produtos.prd_marca_id = marcas.mrc_id

order by prd_nome;
```

## Crie uma view que mostra todos os produtos e seus respectivos fornecedores;
![image](https://github.com/WanderleiJullia/Bancos.VIEW/assets/144744092/514a981f-b1c6-4a5e-876b-ba0d5c911c25)


 ``` SQL
Inserir o código aqui
CREATE VIEW Produtos_Fornececores AS 
SELECT 
	produtos.prd_nome AS produtos,
	fornecedor.frn_nome AS fornececores 
FROM produtos 	
JOIN produtos_has_fornecedor ON produtos_has_fornecedor.pf_prod_id = produtos.prd_id 
JOIN fornecedor ON produtos_has_fornecedor.pf_forn_id = fornecedor.frn_id;
```
## Crie uma view que mostra todos os produtos e seus respectivos fornecedores e marcas;
![image](https://github.com/WanderleiJullia/Bancos.VIEW/assets/144744092/b45a2e4d-e4d5-40ea-b5f9-dce704eefea5)

```SQL
Inserir o código aqui

create view Produtos_Fornecedores_marcas as 
	produtos.prd_nome as produtos,
	fornecedor.frn_nome as fornecedores ,
	marcas.marc_nome as	 marca
from produtos 	
join produtos_has_fornecedor on produtos_has_fornecedor.pf_prod_id = produtos.prd_id 
join fornecedor on produtos_has_fornecedor.pf_forn_id = fornecedor.frn_id
join marcas on marcas.mrc_id = produtos.prd_marca_id ;
```

## Crie uma view que mostra todos os produtos com estoque abaixo do mínimo;
![image](https://github.com/WanderleiJullia/Bancos.VIEW/assets/144744092/0cc7be37-b9d2-489b-b82a-ac33c1014c1a)

```SQL
Inserir o código aqui
create view Tab_Abaixo_media as 
select * from Produtos where prd_estoque < prd_estoque_min;
```

## Adicione o campo data de validade. Insira novos produtos com essa informação; 
![image](https://github.com/WanderleiJullia/Bancos.VIEW/assets/144744092/540f1a88-7520-4f76-bd2f-b10c1d5a7037)

```SQL
Inserir o código aqui

alter table produtos add prd_data_validade date;

```

## Crie uma view que mostra todos os produtos e suas respectivas marcas com validade vencida;
![image](https://github.com/WanderleiJullia/Bancos.VIEW/assets/144744092/5ceb3402-3bea-43f0-984b-75e7f3f4111c)

``` SQL
Inserir o código aqui


CREATE OR REPLACE VIEW Produtos_Data_Validade_Vencida AS
SELECT
    prd_nome,
    prd_data_validade
FROM produtos
WHERE prd_data_validade < CURDATE();
```  
## Selecionar os produtos com preço acima da média;

![image](https://github.com/WanderleiJullia/Bancos.VIEW/assets/144744092/a1b5ab14-106f-4d8b-ad74-8b0d70fdf4da)

``` SQL
Inserir o código aqui
SELECT *
FROM Produtos
WHERE prd_valor > (SELECT AVG(prd_valor) FROM produtos);
``` 
## Jullia Santos Wanderlei 
Bancos de Dados 



