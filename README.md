# Alterar o status de um atendimento via API
Aprenda como alterar o status de um protocolo de atendimento na plataforma via API. 

## Visão Geral
1. O que é uma API ?
2. Sobre a API de Alteração de status de atendimento 
3. Autenticando o usuário


### O que é uma API ?
Uma API (Interface de Programação de Aplicativos) é um conjunto de regras, protocolos e ferramentas que permitem que diferentes softwares se comuniquem e interajam uns com os outros. Permite que os desenvolvedores criem aplicativos que se integrem com outros sistemas, compartilhando dados e funcionalidades.

### Sobre a API de Alteração de status de atendimento
Esta API foi implementada para que os status de atendimentos sejam atualizado automaticamente na plataforma, com isso o status poderá ser alterado a partir de um sistema externo, por meio de um Web Service.  


## Autenticando o usuário 
Para autenticar um usuário na plataforma, utilize o seguinte endpoint : **_/api/usuario/login_**
No retorno com sucesso para o método post será exibido uma mensagem contendo o token de acesso aos demais endpoints dessa API.
| Parâmetro  | Descrição |
| ------------- | ------------- |
| login  | 	Credencial de acesso do usuário na plataforma com permissão para alterar status de atendimentos  |
| senha  | Senha de autenticação do usuário na plataforma com permissão para alterar status de atendimentos |

### Exemplo: 
```

{
   "login": "user.api",
   "senha": "1234"
}

```

O retorno da chamada para o endpoint poderá ser um dos status a seguir:

### SUCESSO
* Acess token: código do token

### ERRO
* Usuário não encontrado
* Senha inválida
* Houve um problema para gerar um token
* Este campo é obrigatório – login
* Este campo é obrigatório senha
* Acess denied (Usuário sem permissão)
* Token is missing (Request sem token)
* JWT expired at ano-mes-data-hora Current Time:  ano-mes-data-hora, a difference of number milliseconds. Allowed clock skew: number miliseconds. (Token expirado)
* JWT signature does not match locally computed signature. JWT validity cannot be asserted and should not be trusted.  (Token com falha)

## Alteração do Status do Atendimento
Para alterar status de um protocolo de atendimento na plataforma, utilize o seguinte endpoint : **_api/atendimentos/status_**

Este endpoint poderá ser usado para alterar status de um atendimento para :
* Aberto
* Em atendimento
* Cancelado
* Improcedente
* Finalizado

### Requisitos do Usuário
> Para utilizar esta API, é preciso ter configurado um usuário para realizar a ação na plataforma. Este usuário precisa ter em seu perfil a permissão **_Alterar status de atendimento via api_**. 

Para os status *Cancelado, Improcedente* e para reabrir um atendimento que já estava com o status *Finalizado* deve ser enviado o parâmetro de **_Motivo_** para realizar a ação. Os  Motivos são utilizados para justificar determinadas ações executadas pelos usuários na plataforma, como alterações, exclusões e restrições.

| Parâmetro  | Descrição |
| ------------- | ------------- |
| protocolo  | 	Informe o número do protocolo do atendimento na plataforma que terá o status alterado  |
| status  | Informe o nome do status que deve alterado |
| motivoStatus  | Informe o nome do motivo cadastrado na plataforma para os status Cancelado, Improcedente e reabertura de um atendimento com o status Finalizado |

### Exemplo: 
```

{

"protocolo": "20221104000001",
"status": "Finalizado",
"motivoStatus:"Atendimento finalizado"

}

```

O retorno da chamada para o endpoint poderá ser um dos status a seguir:

### SUCESSO
* Message: Atendimento atualizado com sucesso

### ERRO
* Atendimento não encontrado
* Status não encontrado
* motivoStatus – esse campo é obrigatório
