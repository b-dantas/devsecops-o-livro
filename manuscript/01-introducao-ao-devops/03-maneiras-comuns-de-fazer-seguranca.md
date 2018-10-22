# Maneiras comuns de fazer segurança no SDLC
Neste capítulo iremos conhecer as formas tradicionais de adotar segurança no ciclo de desenvolvimento.

## Abordagens de teste de segurança
Há na indústria de segurança de software diversos modelos de teste:

**EHT _(Ethical Hacking Test)_ ou _pentest_ (teste de penetração)** é uma abordagem de teste de segurança onde um especialista por meio de técnicas manuais e com apoio de ferramentas, tenta subverter o funcionamento de um software a fim de encontrar vulnerabilidades. O profissional que realiza essa atividade é conhecido como pentester.

**DAST _(Dynamic Application Security Testing)_** é um teste automatizado de segurança dinâmico. Isso significa que aplicação é testada em tempo de execução. O DAST também é conhecido como caixa preta (blackbox), pois quem ataca não tem conhecimento prévio de como funciona o software. Nesse tipo de teste em aplicações web, as vulnerabilidades mais comuns de se encontrar são SQLi (SQL Injection) e XSS (Cross Site Scripting).

**SAST _(Static Application Security Testing)_** é uma forma automática de teste onde se verifica o código-fonte da aplicação. Dependendo da ferramenta pode ser ou não necessário compilá-lo para uma linguagem intermediária (bytecode). Esse teste pode ser chamado de caixa branca (whitebox), já que quem testa tem acesso a lógica de programação da aplicação. É comum nos resultados desse teste ser encontrado falhas como senha fixa no código, estouro de buffer e inspeção de variáveis sensíveis.

**IAST _(Interactive Application Security Testing)_** é uma combinação dos testes DAST e SAST, que visa diminuir a incidência de falsos-positivos.

**RASP _(Runtime Application Self-Protection)_** é um mecanismo que adiciona a aplicação formas de autodefesa contra ações de engenharia reversa e subversão de funcionamento.

## Modelos de processo de desenvolvimento seguro de software
Segurança em software não é apenas realizar testes para saber se ele está vulnerável. Para evitar que essas falhas se materializem, há diversos modelos de implementação de processo de desenvolvimento seguro, onde desde a concepção pensa-se em segurança, o chamado sSDLC (Security Software Development Lifecycle). Tradicionalmente as empresas que utilizam algum processo de desenvolvimento seguro seguem algum dos modelos abaixo:

**[OpenSAMM](https://www.opensamm.org/) _(Software Assurance Maturity Model)_** criado e mantido de forma aberta pelo OWASP, é um modelo de avaliação de maturidade, que auxilia a definir e priorizar quais pontos no processo de desenvolvimento seguro devem ser seguidos pela empresa que o adota.

**[BSIMM](https://www.bsimm.com/) _(Building Security in Maturity Model)_** criado e mantido por diversas empresas da indústria de software, também é um modelo de avaliação de maturidade, porém baseado na experiência de diversas companhias.

**[Microsoft SDL](https://www.microsoft.com/en-us/sdl) _(Security Development Lifecycle)_** é o modelo de desenvolvimento seguro adotado internamente pela Microsoft. É disponibilizado ao púbico para quem desejar segui-lo. Também existe uma versão voltada para práticas ágeis ([SDL for agile](https://www.microsoft.com/en-us/SDL/Discover/sdlagile.aspx)). 

**[ISO/IEC 27034](https://www.iso.org/standard/66229.html)** é uma norma que objetiva conduzir as empresas a adicionarem segurança dentro do processo de desenvolvimento de software. 

A iniciativa **[SAFECode](https://safecode.org/)** e a **[ISO/IEC 15408](https://www.iso.org/standard/50341.html)** podem auxiliar na adoção de um modelo de desenvolvimento seguro.