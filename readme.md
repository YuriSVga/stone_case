Esse repositório se destina à respondermos as questões propostas no case de data engineer da Stone. 

# Objetivo gerais:
Avaliar o candidato nos conceitos de capacidade analítica , qualidade de código, aplicação de boas práticas, resiliência, disponibilidade, performance e o bom uso do git (clareza dos commits, divisão do trabalho e melhores práticas).

# Objetivo proposto pelo case: 
Desenvolver um processo que receba um valor máximo em dinheiro e, olhando a base de dados da empresa, distribua o montante para os funcionários já cadastrados. Os pesos seguem a seguinte distribuição: 

## 1 - Peso por área de atuação (Quanto maior o peso maior o valor recebido):
    Peso 1: Diretoria;
    Peso 2: Contabilidade, Financeiro, Tecnologia;
    Peso 3: Serviços Gerais;
    Peso 5: Relacionamento com o Cliente;
    
## 2 - Peso por faixa salarial e uma exceção para estagiários(Quanto maior o peso menor o valor recebido):
    Peso 5: Acima de 8 salários mínimos;
    Peso 3: Acima de 5 salários mínimos e menor que 8 salários mínimos;
    Peso 2: Acima de 3 salários mínimos e menor que 5 salários mínimos;
    Peso 1: Todos os estagiários e funcionários que ganham até 3 salários mínimos;
    
## 3 - Peso por tempo de admissão(Quanto maior o peso maior o valor recebido):
    Peso 1: Até 1 ano de casa;
    Peso 2: Mais de 1 ano e menos de 3 anos;
    Peso 3: Acima de 3 anos e menos de 8 anos;
    Peso 5: Mais de 8 anos
    
# A Entrega: 
Como entrega desse case podemos apresentar um notebook com a explicação passo a passo do processo. Essas etapas seriam equivalentes às quebras em tasks caso no futuro optemos por dividir o processo e transformá-lo em uma DAG. 


# Algumas considerações finais: 
1 - O processo apresentado pressupõe a utilização de alguma ferramenta de scheduling, por exemplo, o airflow. Porém, por se tratar de um processamento com uma peridiocidade baixa esse ponto está aberto. Podemos discutir em conjunto sobre a melhor maneira de realizar esse processo.     
2 - O processo consome os arquivos json de uma pasta local, porém a maneira de consumo pode variar denpendendo da origem. Poderíamos fazer uma integração para buscar esses dados constantemente em algum endpoint, mas a princípio esses dados serão consumidos de uma pasta local.     
3 - Utilizamos uma infraestrutura em python, mas poderíamos usar o pyspark para realizar esse processamento em casos onde essa quantidade de dados aumente considerávelmente.    
4 - O processo construído leva em consideração um peso ponderado de acordo com cada critério estabelecido para chegar ao peso final do bônus. Esse peso ponderado é então multiplicado pelo valor total a ser distribuído obtendo o valor que cada funcionário vai receber.     
5 - Algumas variáveis foram pré-fixadas no código como o valor do salário mínimo e a porcentagem dos lucros a ser distribuída, mas poderíamos, no caso de evoluir para uma interface interativa, deixar o preenchimento desses campos sob a responsabilidade do usuário final.    
6 - Apesar de não haver nenhum problema na base de dados apresentada, o processo conta com uma etapa de validação do Json e dos formatos esperados para cada dado. Essa verificação foi feita usando os próprios métodos do python, mas existem outras ferarmentas que poderiam ser realizadas com esse propósito específico.    



