# DevSecOps - Adotando uma cultura de segurança ágil

*Subtítulo*

## Sumário

1. [Introdução ao DevOps](manuscript/introducao-ao-devops/_index.md)
   1. [Formas tradicionais de criar e implantar software](manuscript/introducao-ao-devops/formas-tradicionais-de-criar-e-implantar-software.md)
   1. Porquê se preocupar com segurança em software
   1. Maneiras comuns de fazer segurança no SDLC
   1. O conceito e princípios do DevOps
1. Integração e Entrega Contínua Segura
   1. Entendendo Integração Contínua e Entrega Contínua com Jenkins
   1. Executando testes dinâmicos com ferramentas OWASP
   1. Código fonte seguro em cada commit do Git com SonarQube
1. O que é DevSecOps
   1. Propósito e benefícios do DevSecOps
   1. Aonde injetar segurança dentro do DevOps
   1. Ferramentas para segurança no DevOps
1. Como criar software seguro desde o início
   1. O princípio SSL e controles de segurança proativos OWASP
   1. Fazendo modelagens de ameaça descomplicadas
   1. O software seguro por padrão e por design
1. Infraestrutura como Código segura
   1. Ansible: formas de provisionar infraestrutura
   1. Checando a segurança de playbooks Ansible
   1. Uso do Ansible Tower/AWX
1. Segurança como Código
   1. Aplicando hardening por meio do Ansible
   1. Automatizando cenários de ataque com Gauntlt
   1. Revisão de código com Gerrit
1. Segurança em Containers
   1. Encontrando e mitigando vulnerabilidades no Docker
   1. Como escolher distros Linux mais seguras para containers
   1. Segurança por meio de plataformas como OpenShift
1. Segurança em Nuvens Pública e Privada
   1. Fazendo gestão de acessos e identidade
   1. Segurança em nuvens públicas como AWS
   1. Segurança em nuvens privadas como OpenStack
1. Segurança na Produção
   1. Segurança em APIs e microserviços com ModSecurity
   1. Gerenciando senhas em ambientes automatizados com Vault
   1. Monitoração e inteligência nos logs
1. Segurança das ferramentas de DevOps
   1. Protegendo o código fonte do Git
   1. Controlando os acessos ao Jenkins
   1. Auditoria automática usando recursos nativos do Git e Jenkins
1. Compliance como Código
   1. O DevOps Audit Defense Toolkit
   1. Estabelecendo barreiras para controle
   1. Gestão de vulnerabilidades com JIRA
1. Disseminando as práticas de segurança
   1. Como treinar ~~os desenvolvedores~~ quem escreve código
   1. Gameficação e hackathons
   1. Criando programas de bug bounty e práticas blameless
   1. Exercícios de Red & Blue Team
   1. Indo além: DevOps dentro da segurança