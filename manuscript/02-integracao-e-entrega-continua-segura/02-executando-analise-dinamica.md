# Executando testes dinâmicos com ferramentas OWASP
Neste capítulo vamos entender como uma ferramenta de análise dinâmica funciona e a importância de realizar verificações de segurança em bibliotecas.

## O Zed Attack Proxy

O [Zed Attack Proxy – ZAP](https://github.com/zaproxy/) é um dos softwares de segurança gratuitos mais populares para testes automatizados em aplicações web. Escrito em Java e mantido pelo Open Web Application Security Project (OWASP), ele se encaixa no que o mercado chama de ferramentas de teste dinâmico ou _blackbox_, conforme vimos em aulas anteriores.

Os testes por análise dinâmica para aplicações web funcionam basicamente em dois passos: 
	
1. É executada uma varredura completa na aplicação, identificado as páginas e recursos por meio de navegação nas URLs, processo conhecido pelo termo em inglês _crawling_.

1. Baseado no resultado na navegação, é inferido possíveis vulnerabilidades que o recurso possa ter. Então é realizado a tentativa de exploração da falha, desde a manipulação de cookies à injeção de SQL. Baseado na resposta do servidor, é possível identificar se a vulnerabilidade é explorável ou não.

O ZAP é útil quando queremos descobrir fragilidades que um atacante sem muito esforço possa explorar, sem necessitar um conhecimento prévio da aplicação. Além do ZAP, existe uma dezena de outras ferramentas que podem integrar-se com o Jenkins e realizar testes dinâmicos automatizados. Virtualmente qualquer solução que exponha uma API é capaz de integrar com uma solução de CI.

O ZAP inclui módulos distintos voltados para cada etapa de um teste dinâmico:

**Intercepting Proxy:** Permite interceptar requisições e respostas no navegador.

**Active Scanner:** Executa verificações de segurança automáticas contra determinada aplicação Web alvo.

**Passive Scanner:** Recupera informações sobre vulnerabilidades de segurança em páginas que são baixadas usando ferramentas de varredura (crawling / spider).

**Spiders:** Antes que o ZAP possa atacar uma aplicação, ele cria um mapa de navegação rastreando todas as páginas e recursos.

**REST API:** Permite que o ZAP seja executado no modo headless e controlado para executar scans automatizados.

Há uma versão do ZAP em contêiner Docker, com a capacidade da interface visual Java ser acessível pelo navegador, por meio WebSwing. Além disso, possui plugin para o Jenkins nativo, onde por meio da API é possível coordenar a execução automática dos testes.

## Verificação de vulnerabilidades em bibliotecas
> _Softwares modernos são mais "montados" e menos "codificados"._

Hoje a maior parte do código de uma aplicação é originado de bibliotecas de fonte aberto ou código proprietário. As bibliotecas são módulos de software projetados para executar funções frequentemente necessárias. Elas fornecem mecanismos como suporte para acesso a dados, gerenciamento de recursos, comunicações e criação de interface com o usuário.

Os pesquisadores de segurança periodicamente identificam vulnerabilidades em bibliotecas e disponibilizam os detalhes da descoberta através de um processo de divulgação de sua própria escolha. Algumas dessas divulgações são coordenadas com o CVE - Common Vulnerabilities and Exposures ou com o Open Source Vulnerability Database (OSVDB). Porém uma boa parte simplesmente as publica em posts de blogs ou e-mails para listas de discussão.

As vulnerabilidades que as bibliotecas podem conter colocam em risco a segurança da aplicação como um todo. Por isso é importante adotar meios de verificar se as versões das bibliotecas utilizadas possuem vulnerabilidades conhecidas. Uma atenção especial deve ser data às bibliotecas de segurança, que fornecem controles como criptografia, validação de entrada, registro em log, controle de acesso e outras funções críticas de segurança.

O **Dependency Checker** da OWASP é uma das soluções que permite verificar se sua aplicação usa bibliotecas em versões que possuem vulnerabilidades conhecidas. Atualmente são suportadas checagens em softwares escritos em Java e .NET, além de suporte experimental a Ruby, Node.js, Python e parcial para C/C++. Um plugin nativo para o Jenkins é disponibilizado para integração.

É indicado também a procura por uma ferramenta que identifique vulnerabilidades em bibliotecas na linguagem que sua aplicação utiliza, já que dessa forma a verificação tende a ser mais rápida e os resultados mais assertivos. Exemplos de soluções são Node Security Platform (NSP, hoje integrado ao gerenciador de dependências npm) e Retire.js, exclusivos para Node.js.
	
Após saltar um nível de maturidade na cultura DevSecOps, é possível implantar um processo de homologação de bibliotecas, onde execução de testes de análise estática e dinâmica são realizados com o objetivo de buscar vulnerabilidades que ainda não foram descobertas.