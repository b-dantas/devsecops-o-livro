# Entendendo Integração Contínua e Entrega Contínua com Jenkins
Neste capítulo vamos entender qual o papel da Integração e Entrega Contínua utilizando Jenkins.

## Compreendendo o conceito de Integração Contínua
> _Um fluxo de CI deve iniciar toda vez que alguém enviar código para o repositório_

Os desenvolvedores que praticam Integração Contínua (conhecido pelo termo em inglês _Continuous Integration - CI_) combinam as mudanças que fazem no código-fonte da aplicação com a maior frequência possível. As alterações são validadas por meio de compilação ou empacotamento do código, além da execução de testes unitários e funcionais automatizados. Fazendo isso, evita-se grandes esforços no dia de implantação da aplicação para combinação de código modificado por diversas pessoas do time. Esse procedimento ocorre no instante logo após o envio do código para o repositório que o versiona.

## Ferramentas de CI
> _Mesmo que o desenvolvimento de um software não esteja utilizando uma ferramenta de CI, o time de segurança pode ser protagonista na iniciativa e implantar uma solução dessa para permitir as automações de verificação de segurança, além de possibilitar a futura melhoria no desenvolvimento e implantação do software._

As ferramentas que operacionalizam o CI são importantes no processo de injetar segurança dentro do DevOps, já que por meio dela que serão feitas a maior parte das automações de verificação. O Jenkins é uma das ferramentas de CI mais utilizadas. Além dela, são também famosas o Gitlab CI, Travis CI, Bamboo e Circle CI.

Funcionalmente as soluções de CI podem ser consideradas meros orquestradores, ou seja, coordenam a execução de outras ferramentas que fazem parte do SDLC, a partir de um determinado gatilho. Uma ferramenta de CI em si não possui grande capacidade por ela própria de executar as tarefas de uma esteira

## Entendendo o que é Entrega Contínua
> _Um fluxo de CD inicia-se toda vez que queremos fazer o deploy da aplicação._

A Entrega Contínua (conhecido pelo termo em inglês _Continuous Deployment - CD_) é uma extensão da Integração Contínua. Além dos testes, a implantação da aplicação também ocorre de maneira automatizada. Isso permite o deploy de mudanças de maneira frequente, chegando até diversas vezes ao dia, porém o gatilho para isso ocorrer é manual.

Geralmente as ferramentas de CI tem capacidade de realizar fluxos de CD também. Em ambientes DevOps é comum o uso de uma única ferramenta para os dois processos, CI e CD.

## Como evoluir para Implantação Contínua
> _Implantação Contínua difere-se da Entrega Contínua com a fase de implantação automática._

Após atingir um alto nível de maturidade realizando CI e CD, uma forma de acelerar a velocidade das entregas é automatizar a implantação do software como um todo, sempre que uma esteira de compilação ou empacotamento for executada. A evolução para esse modelo obriga que a realização de testes unitários e funcionais esteja em níveis próximos da excelência, já que a qualidade dos releases dependerá disso.

## O Jenkins
Um das ferramentas mais utilizados para viabilizar os processos (também chamado de esteiras) de CI e CD é o Jenkins (https://jenkins.io/). Foi criado em 2011, após a separação do projeto original Hudson. Há uma versão com suporte pago e recursos adicionais chamada CloudBees.

Escrito em Java, o Jenkins possibilita que você crie esteiras por diversas formas, sendo as duas principais maneiras:

**Freestyle** é o modo mais simples e rápido para criação de uma esteira. Por meio de uma interface gráfica web, definimos os passos para recuperação do código-fonte do repositório, sua compilação ou empacotamento e testes. Existem centenas de plugins voltados para integração com outras ferramentas de SDLC, de maneira que seja possível estender suas as capacidades. 

**Pipeline** é o modo um pouco mais avançado e pode exigir conhecimento de programação Groovy. Os passos da esteira são codificados, permitindo melhor flexibilidade no que se pode fazer nas esteiras. Caso não queira utilizar Groovy para codificação total, pode-se fazer o uso de qualquer outra tecnologia como playbooks Ansible ou scripts em Python. Nesse caso o papel do código Groovy será estruturar o pipeline e ser o chamador para os outros scripts e programas. Nesse modo, alguns plugins feitos para Freestyle podem não estar disponíveis ou funcionar.

## Usando o Jenkins para operacionalizar CI e CD
Vamos criar um projeto que representará uma esteira de CD. Nela vamos recuperar o código-fonte de uma aplicação em um repositório Git escrita em Java e fazer seu build (compilação) com o Maven. Para isso, após autenticar no Jenkins siga os passos:

1. Escolha a opção "New Item" do menu lateral direito
1. No campo "Enter an item name" coloque "Minha Primeira Esteira"
1. Escolha a opção "Freestyle Project"
1. Clique no botão "OK" para concluir

Na página seguinte são exibidas as fases disponíveis para configuração da esteira freestyle.

1. Em "Source Code Management" escolha Git e em seguida informe em "Respository URL" o endereço {ENDEREÇO}
1. Mantenha os demais campos como estão
1. {Etapa de Build}
1. Clique em "Save" para salvar as configurações
1. Agora clique "Build Now" do menu esquerdo para que a esteira seja executada.

Após a esteira ter sido concluída, nossa aplicação deverá estar disponível no endereço {ENDEREÇO}.

## Fases padrão de uma esteira freestyle
As fases de uma esteira freestyle podem variar de acordo com os plugins que estejam instalados no Jenkins. As principais fases de uma instalação padrão são:

**General:** Nome e descrição do projeto, bem como as configurações globais que afetam ele como um todo.

**Source Code Management:** A partir de qual repositório o código-fonte será recuperado. A instalação padrão vem com suporte para Git e Subversion. Outros plugins podem permitir a recuperação de código a partir de outras ferramentas de versionamento como Mercurial, CVS, ou mesmo uma pasta em um sistema de arquivos.

**Build Triggers:** Define qual gatilho será utilizado para iniciar a execução da esteira. Muito útil quando desejamos configurar esteiras de CI ou builds noturnos _(nightly builds)_, que executam diariamente de forma recorrente.	

**Build Environment:** Configura parâmetros de ambiente para que o build seja realizado. Opções uteis aqui incluem a injeção de senha em tempo de compilação, de modo a que ela não fique fixa em um código-fonte.

**Build:** Nessa fase é onde configuramos a maior parte das ações. Da compilação ou empacotamento, passando pela publicação da aplicação propriamente dita. Na fase Build é onde se concentra a maior parte da integração com ferramentas de segurança.

**Post-build Actions:** Aqui definimos quais ações devem ser executadas após um build ser concluído. Há opções desde o envio de um e-mail de alerta, até a publicação do código compilado ou empacotado em um repositório.