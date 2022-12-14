<p align="center">
    <img src="https://pluga.co/blog/wp-content/uploads/2022/01/tudo-sobre-magento-2.png" width="400px" " alt="Magento Commerce" />
</p>

#  Modelo Básico Magento 2 Docker :rocket:

- Antes de fazer a instalação e configuração do Magento é necessário ter uma conta no site no [Marketplace do Magento](https://marketplace.magento.com/extensions.html)
- Depois da conta criada, vá no seu nome, clique na seta e em My Profile
- Vá até o link Acess Keys, e clique no botão Create A New Acess Key
- Gerá gerado um par de chaves plubica e privada
- Você precisará dessas chaves para autenticar o seu Magento e instalar módulos

## Tecnologias e Ferramentas utilizadas :robot:

- VsCode
- Magento 2.4
- Apache
- PHP 7.1, PHP 7.2, PHP 7.3, PHP 7.4
- Xdebug 2.9.8
- MariaDB 10.4.13
- Elasticsearch 7.6
- Varnish 6.4
- Redis
- MailHog
- n98-magerun

| PHP Version  | Composer  | [hirak/prestissimo](https://github.com/hirak/prestissimo) |
|---|---|---|
|7.1|1.10.17|Yes|
|7.2|1.10.17|Yes|
|7.3|1.10.17|Yes|
|7.4|2.*|No|

### Requisitos 

**Linux:**

Instale [Docker](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/) e o [Docker-compose](https://docs.docker.com/compose/install/#install-compose).

### Instalação:

- Clone o projeto, e abra dentro de um terminal
- Na pasta do projeto digite os seguintes comandos na sequência:

```
bin/shell  
rm index.php  
install-magento2
```

- Será instalado o Magento e todas as suas dependências. Demora um pouco esse processo.

### Possíveis erros:

- Pare o seu mysql e o apache que tiver instalado em sua máquina com os comandos:

```
sudo systemctl stop apache2
sudo systemctl stop mysql
```

### Deploy Frontend:

**Web server:** http://localhost/

**Local emails:** http://localhost:8025


### Deploy Backend:

**Dashboard server:** http://localhost/admin


### Criando seu usuário: 

```
bin/magento admin:user:create --admin-user=seu_usuario --admin-password=sua_senha --admin-email=seu_email --admin-firstname=admin --admin-lastname=admin
```

### Desabilitando a autenticação de dois fatores: 

- Digite os seguites comandos em sequência:

```
bin/magento module:disable Magento_TwoFactorAuth 
bin/magento cache:flush 
bin/magento setup:di:compile 
```
- Depois atualize a página 


## Traduzindo para o Português: 

- Efetue o [download do zip](https://github.com/rafaelstz/traducao_magento2_pt_br/archive/master.zip)
- Extraia o conteúdo do zip
- Abra o projeto no seu VsCode 
- Crie a sequência diretórios em src/app **i18n/rafaelcg/language_pt_br**
- Pegue o conteúdo que você extraiu do zip e coloque dentro do último diretório criado
  
  
### Habilitar para o Português: 

Para começar a usar a tradução instalada na loja e no painel administrativo da loja siga esses passos:

- Acesse no painel administrativo da sua loja: Vá em `Stores -> Configuration -> General -> General -> Locale options` e selecione em **Locale** a opção **Brazilian Portuguese (Brazil)**.


### Habilitar painel admin em Português:

- Acesse no painel administrativo da sua loja clique no icone do seu usuário no canto superior direito e então clique em `Account Setting` e selecione em **Interface Locale** a opção **Brazilian Portuguese (Brazil)**.


### Limpando cache do magento:

- O Magento faz uso de cache tags, que devem ser especificadas no momento que um dado é salvo no cache. No entanto, nem sempre estas tags são especificadas.

- Sempre que você fizer uma atualização na loja é bom limpar o cache do Magento, então digite o seguinte comando:

```
bin/magento cache:clean
```
ou
``` 
bin/magento cache:flush
```
                                                                                                                               
- cache:clean - irá limpar apenas os caches que estão em uso pelo Magento.
                                                                                                                               
- cache:flush - limpará todo o storage do cache.                                                                                                                            
                                                                                                                             
## Criando loja de exemplo:

- Digite o comando para criar um loja de exemplo com produtos e categorias:

```
bin/magento sampledata:deploy
```
                                                                                                                               
## Plataforma sem tema dockerizada:


https://user-images.githubusercontent.com/20332960/202967998-9a91df9a-e3dc-4fba-aec7-dfd9b1521726.mp4
                                                                                                                             
                                                                                                                               
## Módulos no Magento:

- Para verificar os módulos instalados, usamos o comando:

```
bin/magento module:status
```

- Para atualizar todos os módulos, digite o comando:

```
bin/magento setup:upgrade
```

### Módulos Gratuítos:

- [Rede](https://github.com/DevelopersRede/magento2)

- [PagSeguro](https://github.com/pagseguro/pagseguro-modulo-magento-v2)

- [Correios](https://github.com/Bleez/Bleez-Correios)

- [Freenet](https://github.com/FrenetGatewaydeFretes/frenet-magento2)


## Para reiniciar container:

- Execute o comando dentro da pasta do projeto

```
bin/shell  
bin/start
```

### [Documentação do Magento](https://devdocs.magento.com/) 
