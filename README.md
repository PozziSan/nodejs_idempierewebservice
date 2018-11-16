# NodeJS-iDempiereWebService

## Caracteristicas

iDempiere WebService es una interfaz que permite llamar a Servicios Web de un sistema iDempiere v3.1, esto para ejecutar en su mayor parte, Procesos confgurados previamente

## Instalación

```bash
npm install --save git+https://github.com/fercarvo/NodeJS-iDempiereWebService.git
```

En caso de no tener git, solo

```bash
npm install --save https://github.com/fercarvo/NodeJS-iDempiereWebService/tarball/master
```

## Cómo Usar

```js
var { requestWS } = require('NodeJS_iDempiereWebService')

var params = [ //Parametros del proceso (Informe y proceso)
    {column: "C_Project_ID", val: 1000000},
    {column: "S_TimeExpense_ID", val: 1000001},
    {column: "fecha_infogasto", val: '2018-11-11'}
]

var url = 'https://idempiere.facebook.com' //URL del servidor idempiere

var context = { //Parametros del usuario de sesion, es el ctx, quien ejecuta el proceso
    ad_client_id: 1000002.
    ad_role_id: 1000099,
    ad_org_id: 1000000,
    m_warehouse_id: 1000008 //Puede obviarse
}

var nombre_web_service = "crear_comisiones"

var user = "foobar" //nombre de usuario del que ejecuta el proceso
var password = "123456secret" //password del usuario que ejecuta el proceso 

requestWS(url, nombre_web_service, context, user, password, params)
  .then(data => {
    console.log('data de la respuesta del web service', data)
  })
  .catch(e => console.error(e))

```