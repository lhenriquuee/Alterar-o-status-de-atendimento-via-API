# Alterar o status de um atendimento via API
Aprenda como alterar o status de um protocolo de atendimento na plataforma via API. 

## Visão Geral
1. O que é uma API ?
2. Autenticando o usuário


### O que é uma API ?
Uma API (Interface de Programação de Aplicativos) é um conjunto de regras, protocolos e ferramentas que permitem que diferentes softwares se comuniquem e interajam uns com os outros. Permite que os desenvolvedores criem aplicativos que se integrem com outros sistemas, compartilhando dados e funcionalidades.

### Autenticando o usuário 
Para autenticar um usuário na plataforma, utilize o seguinte endpoint : ***/api/usuario/login***
No retorno com sucesso para o método post será exibido uma mensagem contendo o token de acesso aos demais endpoints dessa API.
