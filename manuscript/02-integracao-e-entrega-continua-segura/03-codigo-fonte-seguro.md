# Código-fonte seguro em cada commit do Git com SonarQube
Neste capítulo vamos entender como uma ferramenta de análise estática funciona e o papel do SonarQube para isso.

## A análise estática em aplicações
O processo de teste por análise estática consiste na verificação do código-fonte de uma aplicação para identificar vulnerabilidades de segurança sem a sua execução. As ferramentas que fazem esse tipo de teste podem realizar essa atividade de formas diferentes:

**Por análise estrutural do código**, específico da linguagem, em busca de inconsistências com as práticas de codificação segura. Esse processo costuma ser executado por meio de validação com expressões regulares.

**Por análise de fluxo de dados**, com a compilação do código para uma linguagem intermediaria (como um _bytecode_) juntamente com suas dependências, criando gráficos de chamada. Esses gráficos possibilitam identificar o fluxo da informação dentro do código, checando se o dado está sendo sanitizado ou não, em funções, métodos e pontos de entrada.

**Por meio de verificação semântica**, com checagem de sintaxe, identificando se as boas práticas de programação estão sendo adotadas. Essas ferramentas são conhecidas como de tipo _Lint_.

Infelizmente essa tecnologia tem se mostrado propensa a identificar falhas como falso-positivas, pois qualquer suspeita de vulnerabilidade é apontada, mesmo que não seja possível explorá-la. Porém se adequadamente utilizada, esse tipo de ferramenta trará benefícios de grande valor ao DevSecOps, já que é uma das que o time de Desenvolvimento costuma preferir utilizar, pois os apontamentos feitos indicam sempre a linha de código onde há suspeita do problema. 

# O SonarQube
O SonarQube é uma das ferramentas de qualidade de software mais conhecidas. A partir de 2016 o fabricante, SonarSource, adicionou a capacidade de encontrar vulnerabilidades de segurança no código-fonte verificado. Ela acaba então encaixando-se no que o mercado chama de ferramentas de teste por análise estática ou _whitebox_, conforme vimos em aulas anteriores.

Originalmente o SonarQube foi disponibilizado open source, porém hoje ele possui módulos proprietários. A verificação para linguagens como Objective-C e Swift, C / C ++ está disponível apenas em uma versão paga. Entretanto há um bom suporte na versão de código aberto para Java, JavaScript, PHP e outras linguagens baseadas em Erlang.

Uma abordagem que pode ser colocada em prática é a verificação pelo SonarQube de todo trecho de código feito commit em um repositório Git. Um dos ciclos onde é possível automatizar isso é o de Integração Contínua, por meio de plugin nativo existente para o Jenkins. Além disso, o SonarQube oferece o chamado _Quality Gate_, onde caso seja verificado que a modificação inclui vulnerabilidades em demasia, é possível automaticamente barrar o próximo passo de uma esteira de CI / CD.