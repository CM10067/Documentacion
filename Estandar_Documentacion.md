
# HN - Estandar Documentación

En esta parte escribir una descripción general de todo el flujo de la colección, ejemplo:
Esta colección permite realizar el flujo del login, obteniendo su respectivo **Token** y a su vez cuenta con los métodos que obtienen la información cargada en la pantalla principal de **SP05**, permitiendo lo siguiente:  
+ *Realizar una lista*
+ Obtener la información general del usuario
+ Obtener la tasa de cambio actual
+ Top 10 de las ultimas transacciones realizadas
+ Top 50 de las diferentes cuentas registradas
+ Obtener las cuentas guardadas como favoritas

#### *Collection Path:*
[HN_EstandarDocumentacion](https://github.com/CM10067/Documentacion)

## Indices

* [200 OK](#200-ok)

  * [Init Authentication](#1-init-authentication)
  * [User Transactions - Top 10](#2-user-transactions---top-10)


--------


## 200 OK
**Methods with a successful response**



### 1. Init Authentication


***Escribir una descripción general de la acción del método, ejemplo:***

Este método nos permite iniciar sesión es **SP05**, brindando los token necesario para poder navegar dentro de la plataforma

#### *Url Parameters:*
| **Key** | **Value**  | **Description** |
| -- | -- | -- |
| UserID | {{UserID}} | Si la url necesita un parametro agregarlo en esta tabla |

#### *Request Body:*
| **Key** | **Value**  | **Description** |
| -- | -- | -- |
| Username | {{Username}} | Es el nombre de usuario con el cual se iniciará sesión |
| Password | {{Password}} | Es la contraseña respectiva del usuario |
| AppType | {{AppType}} | Especifica por donde nos estamos conectando, ya sea (Web/Mobile) |
| UserLocale | {{Country}} / {{Language}} | Nos permite especificar la locación por medio de 2 parametros |
| Country | {{Country}} | Ciudad donde se está ubicado |
| Language | {{Language}} | El respectivo lenguaje |


#### *Response:* 
***Escribir una descripción o dato importante con respecto a la respuesta obtenida***\

Este es un ejemplo de una repuesta


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{URL}}/odata/ns/authenticationservice/SecureUsers
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json | Tipo de contenido |
| Accept | application/json | Tipo de respuesta aceptada |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| action | init | Acción iniciar |



***Body:***

```js        
{
  "Id": "",
    "UserName": "{{Username}}",
    "AppType": "{{AppType}}",
    "ChannelType": "{{ChannelType}}",
    "UserLocale": {
        "Country": "{{Country}}",
        "Language": "{{Language}}"
    },
    "Password": "{{Password}}"
}
```



***More example Requests/Responses:***


##### I. Example Request: Init Authentication


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |
| Accept | application/json |  |



***Query:***

| Key | Value | Description |
| --- | ------|-------------|
| action | init |  |



***Body:***

```js        
{
  "Id": "",
    "UserName": "{{Username}}",
    "AppType": "{{AppType}}",
    "ChannelType": "{{ChannelType}}",
    "UserLocale": {
        "Country": "{{Country}}",
        "Language": "{{Language}}"
    },
    "Password": "{{Password}}"
}
```



##### I. Example Response: Init Authentication
```js
{
    "d": {
        "__metadata": {
            "id": "http://localhost:8888/odata/ns/authenticationservice/SecureUsers('ZW5jezhmY2M2ODAyOWVmMzgxYTQ2M2Q2NDA5NGNkNjRhOTM0fQ')",
            "uri": "http://localhost:8888/odata/ns/authenticationservice/SecureUsers('ZW5jezhmY2M2ODAyOWVmMzgxYTQ2M2Q2NDA5NGNkNjRhOTM0fQ')",
            "type": "com.sap.banking.common.endpoint.v1_0.beans.SecureUser"
        },
        "AffiliateID": "1",
        "AppType": "Consumers",
        "BankID": "1000",
        "BaseCurrency": "LPS",
        "BusinessCIF": null,
        "BusinessCustId": null,
        "BusinessID": 0,
        "BusinessName": null,
        "ChannelType": "Web",
        "CurrentMfaType": "1",
        "EntitlementID": 2008,
        "ServicePackageId": "51",
        "Id": "ZW5jezhmY2M2ODAyOWVmMzgxYTQ2M2Q2NDA5NGNkNjRhOTM0fQ",
        "NeedToAcceptTerms": true,
        "CarrierTermsAccepted": true,
        "Password": "",
        "UserProfileID": "ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ",
        "ProfileID": 0,
        "SmallBusinessUser": false,
        "WalletUser": false,
        "DaBusinessUser": false,
        "UserLocale": {
            "__metadata": {
                "type": "com.sap.banking.common.endpoint.v1_0.beans.UserLocale"
            },
            "Country": "HN",
            "DateFormat": "dd/MM/yyyy",
            "DateFormatName": "dd/MM/yyyy",
            "DateTimeFormat": "dd/MM/yyyy HH:mm",
            "DateTimeFormatName": "dd/MM/yyyy HH:mm",
            "Language": "es",
            "Locale": "es_HN",
            "LocaleName": null,
            "TimeFormat": "HH:mm",
            "TimeFormatName": "HH:mm",
            "ZoneFormat": "z",
            "ZoneFormatName": "z"
        },
        "UserName": "pvelasq017",
        "UserType": 1,
        "BPWFIID": "1003",
        "DeviceId": null,
        "MacId": null,
        "CustomToken": null,
        "UsuarioNombre": "mockUsuario",
        "DolarCompra": null,
        "DolarVenta": null,
        "EuroCompra": null,
        "EuroVenta": null,
        "ValidatedPersonalToken": false,
        "SecretImageExt": "jpg",
        "SecretImageURL": "https://ocbweb.bancatlan.hn/cb/web/grafx/user/secretimages",
        "DeploymentBank": "hn",
        "LastLoginIP": "0:0:0:0:0:0:0:1",
        "LastActiveDate": "06/04/2021 16:11",
        "CurrentLoginIP": "0:0:0:0:0:0:0:1",
        "Token": null,
        "EmailId": null,
        "PhoneNumber": null,
        "OTP": null,
        "ConcurrentLogin": null,
        "FileSizeLimit": null,
        "FileTypesLimit": null,
        "FileNamesMaxLength": null,
        "FileNamesAllowedChar": null,
        "RecurringTransfer": true,
        "RecurringPayment": true,
        "ScheduleTransfer": true,
        "SchedulePayment": true,
        "SchedulePaymentTypes": "OCB_THIRDPARTY",
        "ScheduleMultipleTransfer": false,
        "ScheduleMultiplePayment": false,
        "AuthToken": null,
        "PushNotificationTopicName": "all_registered_users_qa",
        "AccountAvailable": true,
        "MultifactorInfo": {
            "__deferred": {
                "uri": "http://localhost:8888/odata/ns/authenticationservice/SecureUsers('ZW5jezhmY2M2ODAyOWVmMzgxYTQ2M2Q2NDA5NGNkNjRhOTM0fQ')/MultifactorInfo"
            }
        }
    }
}
```


***Status Code:*** 201

<br>



### 2. User Transactions - Top 10


***Escribir una descripción general de la acción del método, ejemplo:***
Este método nos permite obtener el **Top 10** de las ultimas transacciones realizadas por el usuario con el cual se inició sesión, este resultado es mostrado en un box en la pantalla principal del menú

#### *Response:*
***Escribir una descripción o dato importante con respecto a la respuesta obtenida***

Como resultado se obtienen las ultimas transacciones realizadas


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{URL}}/odata/services/transactionservice/Transactions
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| x-csrf-token | {{x-csrf-token}} | Token obtenido en el incio de sesión |
| TokenKey | {{TokenKey}} | Token obtenido en el incio de sesión |
| Content-Type | application/json | Tipo de contenido |
| Accept | application/json | Tipo de respuesta aceptada |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| $skip | 0 | Nos permite omitir una cantidad de registro iniciales |
| $top | 10 | Es la cantidad maxima de registros a obtener |
| $filter | Type%20eq%20%27HOME%27 | Filtro de la peticion |
| $inlinecount | allpages | Nos permite contar todas los registros obtenido |



***More example Requests/Responses:***


##### I. Example Request: User Transactions - Top 10


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| x-csrf-token | {{x-csrf-token}} |  |
| TokenKey | {{TokenKey}} |  |
| Content-Type | application/json |  |
| Accept | application/json |  |



***Query:***

| Key | Value | Description |
| --- | ------|-------------|
| $skip | 0 | Se ultilza si se quiere oomitar una cantidad de registros |
| $top | 10 | Es el valor maximo de registros en la respuesta |
| $filter | Type%20eq%20%27HOME%27 | Filtro para la consulta |
| $inlinecount | allpages | Parametro para contar los resultados obtenidos |



##### I. Example Response: User Transactions - Top 10
```js
{
    "d": {
        "__count": "40",
        "results": [
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4237006')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4237006')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4237006",
                "InstanceType": null,
                "ReferenceNumber": "23161765487919900",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "100.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "RETIRO_SIN_TARJETA",
                "PayDate": "/Date(1617580800000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "PRUEBA POSTMAN",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "14:35:43",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4237005')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4237005')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4237005",
                "InstanceType": null,
                "ReferenceNumber": "23161765191183400",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "100.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "RETIRO_SIN_TARJETA",
                "PayDate": "/Date(1617580800000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "PRUEBA POSTMAN",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "13:45:47",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4237004')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4237004')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4237004",
                "InstanceType": null,
                "ReferenceNumber": "23161765113870400",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "25.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "TIGO",
                "PayDate": "/Date(1617580800000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "PRUEBA POSTMAN",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "13:32:51",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4237003')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4237003')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4237003",
                "InstanceType": null,
                "ReferenceNumber": "23161764960100000",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "25.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "TIGO",
                "PayDate": "/Date(1617580800000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "PRUEBA POSTMAN",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "13:07:14",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4237002')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4237002')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4237002",
                "InstanceType": null,
                "ReferenceNumber": "23161764868794200",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "1000.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "OCB_LOTERIAAMOR",
                "PayDate": "/Date(1617580800000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "PRUEBA POSTMAN",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "12:52:44",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4237001')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4237001')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4237001",
                "InstanceType": null,
                "ReferenceNumber": "23161764737520400",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "1000.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "OCB_LOTERIAAMOR",
                "PayDate": "/Date(1617580800000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "PRUEBA POSTMAN",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "12:30:10",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4228005')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4228005')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4228005",
                "InstanceType": null,
                "ReferenceNumber": "23161733565215300",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "1000.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "GIRONACIONAL",
                "PayDate": "/Date(1617235200000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "Notita",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "21:54:45",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4228004')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4228004')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4228004",
                "InstanceType": null,
                "ReferenceNumber": "23161714352595700",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "1000.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "GIRONACIONAL",
                "PayDate": "/Date(1617062400000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "Notita",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "16:32:34",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4234003')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4234003')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4234003",
                "InstanceType": null,
                "ReferenceNumber": "23161712736450500",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "1000.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "GIRONACIONAL",
                "PayDate": "/Date(1617062400000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "PRUEBA POSTMAN",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "12:03:43",
                "customPaquetigoDescription": null
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/transactionservice/Transactions('4234002')",
                    "uri": "http://localhost:8888/odata/services/transactionservice/Transactions('4234002')",
                    "type": "com.sap.banking.custom.transaction.endpoint.v1_0.beans.Transaction"
                },
                "Id": "4234002",
                "InstanceType": null,
                "ReferenceNumber": "23161712539026800",
                "FundsType": null,
                "TrackingID": null,
                "Amount": "1000.00",
                "AmountCurrency": "LPS",
                "UserName": null,
                "TransactionIndex": "0",
                "SubmittedBy": null,
                "SubmittedByUserName": null,
                "ApprovalID": null,
                "ApproverName": null,
                "ApproverIsGroup": false,
                "RejectReason": null,
                "ResultOfApproval": null,
                "CanEdit": false,
                "CanDelete": false,
                "CanLoad": false,
                "CanSkip": false,
                "CanInquire": false,
                "ExternalID": null,
                "TemplateID": null,
                "FrequencyDisplayName": null,
                "BackendErrorDescription": null,
                "PaymentSubType": null,
                "PaymentType": "GIRONACIONAL",
                "PayDate": "/Date(1617062400000)/",
                "AccountID": "1100000106-1",
                "MaskedAccountNumber": "xxxxxx0106",
                "AccountType": "CHECKING",
                "StatusName": "Completado",
                "Status": "5",
                "Memo": "PRUEBA POSTMAN",
                "AccountDisplayText": "xxxxxx0106-Cheques",
                "Date": null,
                "Type": null,
                "PayTime": "11:30:20",
                "customPaquetigoDescription": null
            }
        ]
    }
}
```


***Status Code:*** 200

<br>



---
[Back to top](#hn---estandar-documentación)
> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2021-04-07 22:04:25 by [docgen](https://github.com/thedevsaddam/docgen)
