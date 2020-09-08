# Desafio NodeJS #

Nesse desafio, a tarefa é implementar uma aplicação que sirva como um servidor de chat da Trílogo. Nele, cada sala está associada a um ticket e os seus participantes são os usuários que têm acesso ao ticket.

No escopo desse teste, não será possível criar uma sala "avulsa", sem associação a nenhum ticket. Portanto cada sala terá:

* ticket_id: Código do ticket (sala)
* description: descrição do problema ao qual o ticket se refere
* permalink: uma imagem registrada no momento da criação do ticket

O servidor de chat deverá ser escrito em NodeJS e os dados devem ser armazenados em um MongoDB, com o uso de algum recurso que viabilize a reatividade entre os clientes que consultam o servidor do chat. Portanto, ao enviar uma mensagem, um outro cliente deverá visualizá-la em tempo real.

As mensagens podem ser apenas em formato de texto e deverá existir o conceito de "não lido". Ele deverá aplicado em:

* Contador de mensagens não lidas por sala
* Contador de salas com mensagens não lidas

Os dados utilizados para compor o chat (salas, mensagens e participantes) poderão ser mockados diretamente no banco de dados.

Por fim, a aplicação deverá contemplar as seguintes operações:

* Listar salas de chat (paginada, com pesquisa por id e descrição da sala)
* Listar mensagens de uma determinada sala
* Enviar e receber mensagens em tempo real
* Criar uma sala de chat
* Listar os participantes de uma sala

Para dar início ao desafio, o candidato deve dar um fork no repositório e, ao fim do desenvolvimento, dar acesso ao usuário **_washington@trilogo.com.br_** e ao usuário **_hugo@trilogo.com.br_** ao seu repositório para análise do trabalho.

**Extras**

* Utilização de um ORM para definir os modelos dos dados
* Implementação de um mecanismo de autorização (uso de JWT, por exemplo) para validar as chamadas aos endpoints
* Implementação de uma arquitetura escalável, de forma que o servidor possa ser instanciado em mais de uma máquina
* Implementação de uma limitação de acesso as salas, de forma que um usuário X não consiga visualizar uma sala A, enquanto que um usuário Y consegue
* Aplicação de boas práticas

Os itens extras (opcionais) contarão positivamente na análise do seu desafio.

Abaixo alguns endpoints que deverão ser implementados no desafio.

### GET `/api/chatroomsbyuser?userId={userId}&limit={limit}&offset={offset}&term={term}`
Esse endpoint recebe o código do usuário para listar salas

### GET `/api/chatmessages/{ticketId}`
Endpoint que realiza a consulta de mensagens de uma sala pelo _id_ do ticket correspondente

### POST `/api/createchatroom`
Endpoint que recebe um JSON para a criação de uma sala

```json
{
   "Description":"Lâmpada queimada",
   "TicketId":"123",
   "permalink":"dadoMockado.jpg"
}
```
