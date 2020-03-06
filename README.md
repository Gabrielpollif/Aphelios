# Demonstração IoT + IA

Este é uma pequena demonstração do ciclo de vida de um projeto de Machine Learning: 

* Conceber o funcionamento do sistema
* Coletar os dados
* Armazenar e gerenciar os dados
* Treinar um modelo
* Avaliar, interpretar, melhorar

Apesar de simples, o projeto foi estruturado de forma a poder ser facilmente reutilizado e aprimorado

# Microcontrolador

Para implementar o seu basta mudar o endereço IP para o servidor que você subiu, montar os componentes eletrônicos (LDR, resistores e botão) e gravar o arduino

Tecnologias utilizadas:

* Microcontrolador: pequeno processador que consegue ler valor de tensão, se comunicar pela internet, etc
* Linguagem C: linguagem de programação de baixo nível
* Wiring: adaptação da linguagem C

Palavras chaves:

* Sistema embarcado

* IoT: microcontrolador enviado dados pra um servidor

# Servidor web

Linguagens e tecnologias:

* HTML: para diagramar a página
* CSS: aplica estilos (cores, tamanhos, etc)
* Javascript and VueJS framework: requisita os dados e atualiza a tabela
* PHP: faz a API (Application Programming Interface) para receber e buscar os dados
* SQL: linguagem para interagir com o Banco de Dados
* MySQL: o Banco de Dados em sí (software)
* PHPmyAdming: software para acessar graficamente o banco de dados (pelo browser)

Palavras chaves:

* Single Page Application: a página atualiza sem precisar dar F5
* AJAX: técnica para buscar os dados de forma assíncrona
* Cloud Computing
* Responsive web design

## Setup do servidor

Amazon Web Services (gratuito no primeiro ano)

Instância básica EC2 com o stack LAMP (Linux, Apache, MySQL, PHP) instalado: ver [este tutorial](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-lamp-amazon-linux-2.html)

Outra opção mais simples: 000webhost

## Setup do banco de dados

Crie o banco de dados: lado esquerdo do PHPmyAdmin, *new table*, eu dei o nome *IA_demo* (se você mudar o nome deve mudar no código também)

Crie a tabela para organizar os dados:

```
 CREATE TABLE `demo_LDR` ( 
     `id` INT NOT NULL AUTO_INCREMENT,
     `LDR1` INT NULL ,
     `LDR2` INT NULL ,
     `button` INT NULL , 
     
     PRIMARY KEY (`id`)
 )
 ```SQL
```

## Setup do website

Envie os arquivos usando scp. Exemplo:

```
scp -i <local-da-chave> demo-arduino-IA-IoT/02\ -\ Servidor\ web/* ec2-user@:<endereço-web>/var/www/html/demo/
```

Teste tudo inserindo um dado fake, digintado no navegador (ou seja, fazendo um get request):

```
<endereço-web>/demo/API_data_receive.php?LDR1=150&LDR2=250&button=1
```

# Análise