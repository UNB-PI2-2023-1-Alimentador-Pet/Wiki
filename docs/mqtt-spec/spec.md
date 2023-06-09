## Especificação da Comunicação MQTT

### `topic`
Publishers:

 - xxx 

subscribers: 
 - xxx

```json
{
    "sender": "",
    "user_hash": "XXXXXXXXXXXXX",
    ...
}
```
obs: ... (opcional)

#### Observações gerais

- Pegar o binário do áudio pode ser feito em uma chamada de api
- Enviar a foto também pode ser feito via chamada de api
- `prefix` ainda a ser definido

### `prefix/provide_food`
Publishers:
 - backend

subscribers: 
 - main_esp
```json
{
    "sender": "server",
    "user_hash": "XXXXXXXXXXXXX",
    "qtde": int
}
```
obs: `qtde` é a quantidade em gramas

### `prefix/close_feeder`
Publishers:
 - backend 

subscribers: 
 - main_esp
```json
{
    "sender": "server",
    "user_hash": "XXXXXXXXXXXXX",
    "value": 1|0
}
```
obs: `value` é um booleano. `1` fecha o comedouro se ele estiver aberto e `0` abre se ele estiver fechado

### `prefix/schedule_save`
Publishers:
 - backend

subscribers: 
 - main_esp
```json
{
    "sender": "",
    "user_hash": "XXXXXXXXXXXXX",
    "schedule": [
        {
            "qtde": int,
            "timestamp": int
        },
        ...
    ]
}
```
obs: Ao receber essa mensagem, a esp deve salvar na memória as próximas n alimentações do pet.

### `prefix/tank_percent`
Publishers:
 - main_esp 

subscribers: 
 - backend
```json
{
    "sender": "esp32",
    "user_hash": "XXXXXXXXXXXXX",
    "value": int
}
```
obs: O valor é a porcentagem estimada de comida ainda disponível no reservatório. Publicações para este tópico devem ocorrer toda vez que o alimentador dispensar comida. O backend será responsável pela notificação caso a ração disponível seja menor que 20%.


