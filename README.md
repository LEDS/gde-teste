**Build Status**: [![Build Status](https://travis-ci.org/paulossjunior/ledszeppellin_2.png)](https://travis-ci.org/paulossjunior/ledszeppellin_2)

# LedsZeppellin: Exemplificando a Integração Contínua e Entrega Contínuo do Leds

## Introdução

O **LedsZeppellin** é um exemplo de aplicação web que visa apresentar como construir sistemas utilizando técnicas de Integração contínua e Entregas Contínuas. Para o desenvolvimento desse tutorial utilizaremos as seguintes tecnologias:

    Linguagem de Programação: Python
    Framework Web: Django
    Repositório de códigos: GitHub
    Framework de Behavior Driven Development: Behave
    Serviço de Integração Contínua: Travis
    Serviço de Deploy de aplicação: OpenShift

### Pré-requisitos:

1. [Instalar e configurar o OpenShift e o Travis localmente](https://blog.openshift.com/how-to-build-and-deploy-openshift-java-projects-using-travis-ci/).
2. Instalar o Python 3.3.

## Etapa Zero: Um pouco de conceitos

>"Integração Contínua é uma pratica de desenvolvimento de software onde os membros de um time integram seu trabalho frequentemente, geralmente cada pessoa integra pelo menos diariamente – podendo haver multiplas integrações por dia. Cada integração é verificada por um ***build automatizado (incluindo testes)*** para detectar erros de integração o mais rápido possível. Muitos times acham que essa abordagem leva a uma significante redução nos problemas de integração e permite que um time desenvolva software coeso mais rapidamente." ***[Martin Fowler](http://martinfowler.com/articles/continuousIntegration.html) -  [Caelum](http://blog.caelum.com.br/integracao-continua/)***


## Segunda etapa: Construir uma aplicação com teste

A nossa aplicação será hospedada no **OpenShift**. O [OpenShift](https://www.openshift.com/) é um PASS (Platforma-as-a-Service) que permite aos desenvolvedores, de forma rápida, o desenvolvimento, hospedagem e a escala de suas aplicações em um ambiente cloud. 

Para criar a nossa aplicação no ambiente do OpenShift é necessário executar o seguinte comando:
    
    rhc app create aplicacaoX python-3.3 postgresql-9.2

Esse comando está informando ao OpenShift que desejamos criar uma aplicação que use python 3.3 e postgresql 9.2. Quando o criamos uma aplicação o OpenShift copia alguns arquivo para o máquina local. Esses arquivos não serão úteis para o nosso projeto. Assim, iremos apagá-los:
    
   cd aplicacaoX
   git rm -rf *
   git commit -am "deleted project"
   
O próximo passo é usarmos um template de projeto que utiliza Django e Python, disponibilizado pela equipe do OpenShift, para o nosso projeto.

   git remote add upstream -m master git://github.com/openshift/django-example.git
   git pull -s recursive -X theirs upstream master
   git remote rename origin openshift
   
É importante comentar que o OpenShift trabalha de duas formas para gerenciar as dependências de biblioteas do projeto: (i) utilizando o arquivo de Setup.py ou requirimentes.txt.  

## Aumatizando a Integração Contínua com o Travis e Github


## Delivery Contínuo 

### Com OpenShift 

##Referências:

**[Tutorial de BDD com Python, Django e Behave](https://semaphoreci.com/community/tutorials/setting-up-a-bdd-stack-on-a-django-application)**

**[How to Build and Deploy OpenShift Java Projects using Travis CI](https://blog.openshift.com/how-to-build-and-deploy-openshift-java-projects-using-travis-ci/)**

**[Integração Contínua e o processo Agile](http://blog.caelum.com.br/integracao-continua/)**
