---
title: "DNS"
date: "2024-06-03"
author: ["Luiz Felipe"]
categories: 
- rede
tags: 
- dns
- rede
showTags: false
description: "Explicação sobre dns"
weight: # 1 means pin the article, sort articles according to this number
slug: ""
draft: false # draft or not
comments: true
showToc: true # show contents
TocOpen: false # open contents automantically
hidemeta: false # hide information (author, create date, etc.)
disableShare: false	# do not show share button
showbreadcrumbs: true # show current path
---



### O que é DNS?
O DNS (Domain Name System) converte nomes de domínio legíveis por humanos em endereços de IP legíveis por máquinas.


Todos os dispositivos presentes na internet utilizam endereços numéricos únicos atribuidos a cada um para se encontrar e comunicar entre si. Esses números são conhecidos como endereços IP, um endereço IP pode ser algo como 192.168.100.1 (IPv4), 4 conjuntos de números entre 0 - 255 separados por pontos, ou podem ser uma versão alfanumérica mais complexa e recente como 2001:0db8:85a3:0000:0000:8a2e:0370:7334 (IPv6).


Quando navegamos pela internet utilizando um navegador web por exemplo, não precisamos informar um número longo e complicado, apenas um nome de domínio já é o suficiente para encontrar o que deseja.


Um serviço DNS, é um componente fundamental na infraestrutura da internet, globalmente distribuído que funciona basicamente como uma agenda telefônica gerenciando o mapeamento entre os nomes de domínio e seus respectivos endereços IP. Os servidores DNS convertem solicitações de nomes em endereços de IP, controlando qual servidor o usuário final irá se conectar quando digitar um nome de domínio no navegador da web. Essas solicitações feitas pelo cliente para um servidor DNS são chamadas de **consultas**.


### Tipos de serviço DNS

#### DNS recursivo

Quando um cliente faz uma consulta, o servidor DNS recursivo age como um intermediário para obter as informações de DNS e responder a sua solicitação. Se a referência do DNS solicitada estiver armazenada no cache do servidor recursivo ele responderá a consulta diretamente. Caso contrário, encaminhará a consulta para um ou mais servidores DNS autoritativos até obter todas as informações necessárias para responder ao cliente.

#### DNS autoritativo

O DNS autoritativo tem a autoridade final sobre o domínio, além de ser responsável pela disponibilização de resposta para servidores DNS recursivos com informações de endereços de IP de nomes de domínio específicos. São também utilizados por administradores para gerenciar nomes DNS públicos.


### Como funciona o DNS?

São quatro servidores DNS envolvidos no carregamento de um conteúdo da internet, esses servidores operam de forma distribuída e hierárquica, são eles:

#### Recursor de DNS

É o ponto de contato inicial do seu dispositivo com os servidores DNS, ele é projetado para receber solicitações de máquinas clientes por meio de aplicações como navegadores web, é ele o responsável por fazer solicitações adicionais ao resto da infraestrutura DNS para atender a solicitação do cliente, frequentemente é fornecido pelo seu Provedor de Internet (ISP) ou um serviço de terceiros como o Google Public DNS.

#### Servidor raiz

São os servidores no topo da hierarquia, onde é realizado o primeiro passo da resolução de nome de domíminio em endereço IP, são responsáveis por orientar consultas DNS para os **servidores de domínio de nível superior** apropriados.

#### Servidor de Domínio de Nível Superior (TLD)

São os servidores responsáveis por guardar as informações da última parte da URL (.com, .net, .org, .gov), sendo diferentes servidores para cada, ele responde a consultas DNS com o endereço do servidor DNS autoritativo

#### Servidor de DNS autoritativo

São responsáveis por armazenar os registros DNS, o servidor DNS autoritativo conhece o endereço do nome de domínio específico que foi solicitado e não necessita de fazer consulta ou redirecionamento a outros servidores para responder a solicitações com o endereço de IP.


### Esquema do funcionamento dos serviços DNS

![DNS-esquema-pt](hugo-site/static/imagens/dns-pt.png)