---
title: "DNS"
date: "2024-06-05"
author: ["Luiz Felipe"]
categories: 
- rede
weight: # 1 means pin the article, sort articles according to this number
slug: ""
draft: false # draft or not
comments: false
showToc: true # show contents
TocOpen: false # open contents automantically
hidemeta: false # hide information (author, create date, etc.)
disableShare: false	# do not show share button
showbreadcrumbs: true # show current path
---



### O que é DNS?
O DNS (Domain Name System) converte nomes de domínio legíveis por humanos em endereços IP legíveis por máquinas.

Todos os dispositivos presentes na internet utilizam endereços numéricos únicos atribuídos a cada um para se encontrar e comunicar entre si. Esses números são conhecidos como endereços IP. Um endereço IP pode ser algo como 192.168.100.1 (IPv4), composto por quatro conjuntos de números entre 0 e 255 separados por pontos, ou pode ser uma versão alfanumérica mais complexa e recente, como 2001:0db8:85a3:0000:0000:8a2e:0370:7334 (IPv6).

Quando navegamos pela internet utilizando um navegador web, não precisamos informar um número longo e complicado; apenas um nome de domínio é suficiente para encontrar o que desejamos.


### Serviço DNS
O DNS é um componente fundamental na infraestrutura da internet, globalmente distribuído, que funciona basicamente como uma agenda telefônica, gerenciando o mapeamento entre nomes de domínio e seus respectivos endereços IP. Os servidores DNS convertem solicitações de nomes em endereços IP, controlando a qual servidor o usuário final irá se conectar quando digitar um nome de domínio no navegador. Essas solicitações feitas pelo cliente para um servidor DNS são chamadas de **consultas**.


### Tipos de Serviço DNS

#### DNS Recursivo
Quando um cliente faz uma consulta, o servidor DNS recursivo age como um intermediário para obter as informações de DNS e responder à solicitação. Se a referência do DNS solicitada estiver armazenada no cache do servidor recursivo, ele responderá à consulta diretamente. Caso contrário, encaminhará a consulta para um ou mais servidores DNS autoritativos até obter todas as informações necessárias para responder ao cliente.

#### DNS Autoritativo
O DNS autoritativo tem a autoridade final sobre o domínio, sendo responsável por fornecer respostas aos servidores DNS recursivos com informações de endereços IP de nomes de domínio específicos. Também são utilizados por administradores para gerenciar nomes DNS públicos.

##### Tipos de Registros DNS Autoritativos
Existem vários tipos de registros DNS autoritativos que fornecem diferentes tipos de informações. Alguns dos mais comuns são:

* **Registro A:** Mapeia um nome de domínio para um endereço IPv4.

* **Registro AAAA:** Mapeia um nome de domínio para um endereço IPv6.

* **Registro MX (Mail EXchange):** Direciona emails para servidores de correio eletrônico para o domínio.

* **Registro CNAME (Canonical Name):** Alia um nome de domínio a outro nome de domínio, permitindo aliasing.

* **Registro TXT:** Armazena texto arbitrário que pode ser usado para vários propósitos, incluindo verificação de domínio e informações de configuração.

* **Registro NS (Name Server):** Especifica os servidores de um nome para o domínio.

* **Registro PTR (Pointer):** Utilizando para resoluções reversas de DNS, mapeando um endereço IP a um nome de domínio.


### Como Funciona o DNS
Quatro servidores DNS estão envolvidos no carregamento de um conteúdo da internet. Esses servidores operam de forma distribuída e hierárquica:

1. Recursor de DNS:
É o ponto de contato inicial do seu dispositivo com os servidores DNS. Ele é projetado para receber solicitações de máquinas clientes por meio de aplicações como navegadores web. O recursor é responsável por fazer solicitações adicionais ao resto da infraestrutura DNS para atender à solicitação do cliente. Frequentemente é fornecido pelo seu Provedor de Internet (ISP) ou por um serviço de terceiros, como o Google Public DNS.


2. Servidor-raiz:
No topo da hierarquia, os servidores raiz realizam o primeiro passo da resolução de nome de domínio em endereço IP. Eles orientam consultas DNS para os servidores de domínio de nível superior apropriados.


3. Servidor de Domínio de Nível Superior (TLD):
Esses servidores guardam as informações da última parte da URL (.com, .net, .org, .gov). Eles respondem a consultas DNS com o endereço do servidor DNS autoritativo correspondente.


4. Servidor DNS Autoritativo:
Responsáveis por armazenar os registros DNS, os servidores DNS autoritativos conhecem o endereço do nome de domínio específico solicitado e não necessitam fazer consulta ou redirecionamento a outros servidores para responder a solicitações com o endereço IP.


### Esquema do funcionamento dos serviços DNS

![DNS-esquema-pt](https://raw.githubusercontent.com/lfelipeee/hugo-site/main/static/imagens/dns-pt.png)

1. O usuário final utiliza um navegador web para solicitar os recursos de www.example.com.

2. A máquina não pode traduzir esse nome de domínio a um endereço IP, então faz uma consulta ao Recursor DNS.

3. O Recursor DNS, por sua vez, não tem a informação armazenada em cache, então consulta um Servidor-raiz.

4. O Servidor-raiz encaminha o Recursor DNS para o Servidor de Domínio de Nível Superior (TLD) responsável por domínios '.com'.

5. O Recursor DNS consulta o Servidor TLD indicado.

6. O Servidor TLD encaminha o Recursor DNS para o Servidor Autoritativo que possui o endereço IP desejado.

7. O Recursor DNS consulta o Servidor Autoritativo indicado.

8. O Servidor Autoritativo responde com o endereço IP para o nome de domínio solicitado.

9. O Recursor DNS encaminha o endereço IP para a máquina do usuário final.

10. O navegador web faz a solicitação dos recursos encontrados no IP informado por meio do protocolo HTTP.

11. O servidor web envia o conteúdo da página web solicitada para o navegador web do usuário final.
