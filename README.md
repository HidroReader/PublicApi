# PublicApi

Api pública para acesso de terceiros as capturas de dispositivos HidroReader.

Para usar a API é necessário solicitar um token de acesso que o identificará
no sistema e estará ligado aos dispositivos adquiridos.

Para utilização basta fazer uma requisição GET para a seguinte URL:
`https://sistema.hidroreader.com.br/api/v1/get?token={TOKEN}`

Será retornado uma array JSON contendo as capturas dos últimos 2 dias, com um 
id único que pode ser usado para evitar duplicidade.

Um exemplo feito para a url com token válido:
```
HTTP STATUS: 200

[{"id":2943,"deviceid":818,"counter":0,"version":21,"timestamp":343507547,"flow":"00000000000000000000000000000000","mag":false,"mov":false,"ref":false,"cut":false,"receivedat":"2021-03-03T19:05:43.000Z","serial":"2001005951","number":null},{"id":3007,"deviceid":818,"counter":0,"version":21,"timestamp":343570817,"flow":"00000000000000000000000000000000","mag":false,"mov":false,"ref":false,"cut":false,"receivedat":"2021-03-04T12:40:01.000Z","serial":"2001005951","number":null}]
```

Um exemplo feito para a url com token inválido:
```
HTTP STATUS: 401

{}
```

## Limites de utilização
A API retornará status 429 caso mais de 10 requisições sejam feitas num período
de 10 minutos.

```
HTTP STATUS: 429

{}
```
