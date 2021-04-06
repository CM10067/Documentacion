
# HN - Login

Esta colección permite realizar el flujo del login, obteniendo su respectivo **Token** y a su vez cuenta con los métodos que obtienen la información cargada en la pantalla principal de **SP05**, permitiendo lo siguiente:

+ Obtener la información general del usuario
+ Obtener la tasa de cambio actual
+ Top 10 de las ultimas transacciones realizadas
+ Top 50 de las diferentes cuentas registradas
+ Obtener las cuentas guardadas como favoritas

## Indices

* [200 OK](#200-ok)

  * [Check Concurrent Session](#1-check-concurrent-session)
  * [Exchange Rate](#2-exchange-rate)
  * [Information Products - Top 50](#3-information-products---top-50)
  * [Init Authentication](#4-init-authentication)
  * [User Favorites Accounts - Top 100](#5-user-favorites-accounts---top-100)
  * [User Information by ID](#6-user-information-by-id)
  * [User Transactions - Top 10](#7-user-transactions---top-10)


--------


## 200 OK
**Peticiones con una respuesta exitosa**



### 1. Check Concurrent Session


#### Verificar las Sesiones Actuales
Este método nos permite saber cuantas sesiones actuales existen de un usuario en específico.

###### Parametros necesario
Es necesario enviar en el cuerpo de la petición con formato ***json*** los siguientes parametros:

- `Username` : Es el nombre de usuario por el cual se buscará

- `AppType` : Especifica por donde nos estamos conectando, ya sea **(Web/Mobile)**

- `UserLocale` : Nos permite especificar:

- `Country`: Ciudad donde se está ubicado

- `Language` : El respectivo lenguaje

###### Respuesta


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{URL}}/odata/ns/authenticationservice/SecureUsers
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |
| Accept | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| action | checkConcurrentSession |  |



***Body:***

```js        
{"UserName": "{{Username}}",
"UserLocale": {
        "Country": "{{Country}}",
        "Language": "{{Language}}"
    }}
```



***More example Requests/Responses:***


##### I. Example Request: Check Concurrent Session


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |
| Accept | application/json |  |



***Query:***

| Key | Value | Description |
| --- | ------|-------------|
| action | checkConcurrentSession |  |



***Body:***

```js        
{"UserName": "{{Username}}",
"UserLocale": {
        "Country": "{{Country}}",
        "Language": "{{Language}}"
    }}
```



##### I. Example Response: Check Concurrent Session
```js
{
    "d": {
        "__metadata": {
            "id": "http://localhost:8888/odata/ns/authenticationservice/SecureUsers('')",
            "uri": "http://localhost:8888/odata/ns/authenticationservice/SecureUsers('')",
            "type": "com.sap.banking.common.endpoint.v1_0.beans.SecureUser"
        },
        "AffiliateID": null,
        "AppType": null,
        "BankID": null,
        "BaseCurrency": null,
        "BusinessCIF": null,
        "BusinessCustId": null,
        "BusinessID": 0,
        "BusinessName": null,
        "ChannelType": "Web",
        "CurrentMfaType": null,
        "EntitlementID": 0,
        "ServicePackageId": null,
        "Id": "",
        "NeedToAcceptTerms": false,
        "CarrierTermsAccepted": false,
        "Password": "",
        "UserProfileID": null,
        "ProfileID": 0,
        "SmallBusinessUser": false,
        "WalletUser": false,
        "DaBusinessUser": false,
        "UserLocale": {
            "__metadata": {
                "type": "com.sap.banking.common.endpoint.v1_0.beans.UserLocale"
            },
            "Country": "HN",
            "DateFormat": null,
            "DateFormatName": null,
            "DateTimeFormat": null,
            "DateTimeFormatName": null,
            "Language": "es",
            "Locale": null,
            "LocaleName": null,
            "TimeFormat": null,
            "TimeFormatName": null,
            "ZoneFormat": null,
            "ZoneFormatName": null
        },
        "UserName": "pvelasq017",
        "UserType": 1,
        "BPWFIID": null,
        "DeviceId": null,
        "MacId": null,
        "CustomToken": null,
        "UsuarioNombre": null,
        "DolarCompra": null,
        "DolarVenta": null,
        "EuroCompra": null,
        "EuroVenta": null,
        "ValidatedPersonalToken": null,
        "SecretImageExt": null,
        "SecretImageURL": null,
        "DeploymentBank": null,
        "LastLoginIP": null,
        "LastActiveDate": null,
        "CurrentLoginIP": null,
        "Token": null,
        "EmailId": null,
        "PhoneNumber": null,
        "OTP": null,
        "ConcurrentLogin": false,
        "FileSizeLimit": null,
        "FileTypesLimit": null,
        "FileNamesMaxLength": null,
        "FileNamesAllowedChar": null,
        "RecurringTransfer": null,
        "RecurringPayment": null,
        "ScheduleTransfer": null,
        "SchedulePayment": null,
        "SchedulePaymentTypes": null,
        "ScheduleMultipleTransfer": null,
        "ScheduleMultiplePayment": null,
        "AuthToken": null,
        "PushNotificationTopicName": null,
        "AccountAvailable": null,
        "MultifactorInfo": {
            "__deferred": {
                "uri": "http://localhost:8888/odata/ns/authenticationservice/SecureUsers('')/MultifactorInfo"
            }
        }
    }
}
```


***Status Code:*** 201

<br>



### 2. Exchange Rate


#### Tasa de Cambio
Este método nos permite obtener el costo actuales del **Dolar** como el **Euro** al valor en **Lempiras**

###### Parametros necesario
Es necesario enviar en el header de la petición los siguientes parametros:

- `x-csrf-token` : Este parametro es obtenido al momento de iniciar sesión

- `TokenKey` : Token obtenido en el incio de sesión

- `Content-Type` : Ingresando como valor para el tipo de contenido **application/json**

- `Accept` : Aceptando como respuesta el valor **application/json**

###### Respuesta
Como resultado se obtiene la tasa de cambio actual tanto para Dolares **($)** como Euros **(Є)**


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{URL}}/odata/services/exchangerateservice/ExchangeRates
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| TokenKey | {{TokenKey}} |  |
| x-csrf-token | {{x-csrf-token}} |  |
| Content-Type | application/json |  |
| Accept | application/json |  |



***More example Requests/Responses:***


##### I. Example Request: Exchange Rate


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| TokenKey | {{TokenKey}} |  |
| x-csrf-token | {{x-csrf-token}} |  |
| Content-Type | application/json |  |
| Accept | application/json |  |



##### I. Example Response: Exchange Rate
```js
{
    "d": {
        "results": [
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/exchangerateservice/ExchangeRates('LPS')",
                    "uri": "http://localhost:8888/odata/services/exchangerateservice/ExchangeRates('LPS')",
                    "type": "com.sap.banking.custom.exchangerate.endpoint.v1_0.beans.ExchangeRate"
                },
                "BaseCurrency": "LPS",
                "TargetCurrency": "USD",
                "BuyRate": "24.3393",
                "SellRate": "24.5095"
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/exchangerateservice/ExchangeRates('LPS')",
                    "uri": "http://localhost:8888/odata/services/exchangerateservice/ExchangeRates('LPS')",
                    "type": "com.sap.banking.custom.exchangerate.endpoint.v1_0.beans.ExchangeRate"
                },
                "BaseCurrency": "LPS",
                "TargetCurrency": "EUR",
                "BuyRate": "27.0891",
                "SellRate": "29.2187"
            }
        ]
    }
}
```


***Status Code:*** 200

<br>



### 3. Information Products - Top 50


#### Top 50 productos del usuario
Este método nos permite obtener el **Top 50** de los productos o cuentas propias del usuario con el cual se inició sesión, este resultado es mostrado en un box en la pantalla principal del menú

###### Parametros necesario
Es necesario enviar en el header de la petición los siguientes parametros:

- `x-csrf-token` : Este parametro es obtenido al momento de iniciar sesión

- `TokenKey` : Token obtenido en el incio de sesión

- `Content-Type` : Ingresando como valor para el tipo de contenido **application/json**

- `Accept` : Aceptando como respuesta el valor **application/json**

###### Respuesta
Como resultado se obtienen el **Top 50** de las cuentas del usuario


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{URL}}/odata/services/productservice/Products
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| x-csrf-token | {{x-csrf-token}} |  |
| TokenKey | {{TokenKey}} |  |
| Content-Type | application/json |  |
| Accept | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| $top | 50 |  |
| $expand | Form |  |



***More example Requests/Responses:***


##### I. Example Request: Information Products - Top 50


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
| $top | 50 |  |
| $expand | Form |  |



##### I. Example Response: Information Products - Top 50
```js
{
    "d": {
        "results": [
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/productservice/Products('1000')",
                    "uri": "http://localhost:8888/odata/services/productservice/Products('1000')",
                    "type": "com.sap.banking.product.endpoint.v1_0.beans.Product"
                },
                "ProductId": "1000",
                "ExternalProductId": "0",
                "ProductCategory": "Product",
                "SubProductCategory": "Loan",
                "ProductName": "Solicitud de préstamo",
                "ProductShortName": null,
                "Description": "En Banco Atlántida estamos listos para satisfacer todas sus necesidades, por ello le ofrecemos una gama de productos crediticios que le permitirán de forma sencilla disponer de dinero, para obtener lo que necesita o lo que siempre ha querido tener.",
                "CategoryId": "7",
                "SubCategoryId": "101",
                "BankId": "1000",
                "Url": null,
                "Form": {
                    "__metadata": {
                        "id": "http://localhost:8888/odata/services/productservice/Forms('101')",
                        "uri": "http://localhost:8888/odata/services/productservice/Forms('101')",
                        "type": "com.sap.banking.applications.endpoint.v1_0.beans.Form"
                    },
                    "ID": "101",
                    "Name": "app_loanapp_context",
                    "ProcessName": "productloanapplication",
                    "ContextEntitySetName": "LoanApplications",
                    "FormSteps": "personaldetailapp,incomedetailapp",
                    "LoadViewDynamic": true
                },
                "ProductFeatures": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1000')/ProductFeatures"
                    }
                },
                "ProductDetails": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1000')/ProductDetails"
                    }
                },
                "InlineMessages": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1000')/InlineMessages"
                    }
                }
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/productservice/Products('1001')",
                    "uri": "http://localhost:8888/odata/services/productservice/Products('1001')",
                    "type": "com.sap.banking.product.endpoint.v1_0.beans.Product"
                },
                "ProductId": "1001",
                "ExternalProductId": "0",
                "ProductCategory": "Product",
                "SubProductCategory": "Credit Card",
                "ProductName": "Solicitud de tarjeta de crédito",
                "ProductShortName": null,
                "Description": "Nuestras Tarjetas de Crédito están diseñadas para satisfacer tus necesidades, brindarte mayor seguridad, máxima conveniencia y acceso a la más amplia y diversa red de comercios afiliados.",
                "CategoryId": "7",
                "SubCategoryId": "102",
                "BankId": "1000",
                "Url": null,
                "Form": {
                    "__metadata": {
                        "id": "http://localhost:8888/odata/services/productservice/Forms('102')",
                        "uri": "http://localhost:8888/odata/services/productservice/Forms('102')",
                        "type": "com.sap.banking.applications.endpoint.v1_0.beans.Form"
                    },
                    "ID": "102",
                    "Name": "app_creditcard_context",
                    "ProcessName": "creditcardapplication",
                    "ContextEntitySetName": "CreditCardApplications",
                    "FormSteps": "personaldetailapp,incomedetailapp",
                    "LoadViewDynamic": true
                },
                "ProductFeatures": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1001')/ProductFeatures"
                    }
                },
                "ProductDetails": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1001')/ProductDetails"
                    }
                },
                "InlineMessages": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1001')/InlineMessages"
                    }
                }
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/productservice/Products('1002')",
                    "uri": "http://localhost:8888/odata/services/productservice/Products('1002')",
                    "type": "com.sap.banking.product.endpoint.v1_0.beans.Product"
                },
                "ProductId": "1002",
                "ExternalProductId": "0",
                "ProductCategory": "Product",
                "SubProductCategory": "Account",
                "ProductName": "Solicitud de cuenta",
                "ProductShortName": null,
                "Description": "En Banco Atlántida le ofrecemos las herramientas que necesita para administrar su dinero y ahorrar para el futuro. Tenemos una amplia gama de cuentas diseñadas con el propósito de brindarle lo necesario para que pueda tomar control de sus finanzas eficientemente.",
                "CategoryId": "7",
                "SubCategoryId": "103",
                "BankId": "1000",
                "Url": null,
                "Form": {
                    "__metadata": {
                        "id": "http://localhost:8888/odata/services/productservice/Forms('103')",
                        "uri": "http://localhost:8888/odata/services/productservice/Forms('103')",
                        "type": "com.sap.banking.applications.endpoint.v1_0.beans.Form"
                    },
                    "ID": "103",
                    "Name": "app_account_context",
                    "ProcessName": "accountapplication",
                    "ContextEntitySetName": "AccountApplications",
                    "FormSteps": "personaldetailapp,incomedetailapp",
                    "LoadViewDynamic": true
                },
                "ProductFeatures": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1002')/ProductFeatures"
                    }
                },
                "ProductDetails": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1002')/ProductDetails"
                    }
                },
                "InlineMessages": {
                    "__deferred": {
                        "uri": "http://localhost:8888/odata/services/productservice/Products('1002')/InlineMessages"
                    }
                }
            }
        ]
    }
}
```


***Status Code:*** 200

<br>



### 4. Init Authentication


#### Inicio de Sesión 
Este método nos permite iniciar sesión es **SP05**, brindando los token necesario para poder navegar dentro de la plataforma

###### Parametros necesario
Es necesario enviar en el cuerpo de la petición con formato ***json*** los siguientes parametros:

- `Username` : Es el nombre de usuario con el cual se iniciará sesión

- `Password` : Es la contraseña respectiva del usuario

- `AppType` : Especifica por donde nos estamos conectando, ya sea **(Web/Mobile)**

- `UserLocale` : Nos permite especificar:

- `Country`: Ciudad donde se está ubicado

- `Language` : El respectivo lenguaje

###### Respuesta


***Endpoint:***

```bash
Method: POST
Type: RAW
URL: {{URL}}/odata/ns/authenticationservice/SecureUsers
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| Content-Type | application/json |  |
| Accept | application/json |  |



***Query params:***

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



### 5. User Favorites Accounts - Top 100


#### Top 100 Cuentas favoritas del usuario
Este método nos permite obtener el **Top 100** de las cuentas favoritas del usuario con el cual se inició sesión, este resultado es mostrado en un box en la pantalla principal del menú

###### Parametros necesario
Es necesario enviar en el header de la petición los siguientes parametros:

- `x-csrf-token` : Este parametro es obtenido al momento de iniciar sesión

- `TokenKey` : Token obtenido en el incio de sesión

- `Content-Type` : Ingresando como valor para el tipo de contenido **application/json**

- `Accept` : Aceptando como respuesta el valor **application/json**

###### Respuesta
Como resultado se obtienen el **Top 100** de las cuentas favoritas del usuario


***Endpoint:***

```bash
Method: GET
Type: RAW
URL: {{URL}}/odata/services/accountservice/Accounts
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| x-csrf-token | {{x-csrf-token}} |  |
| TokenKey | {{TokenKey}} |  |
| Content-Type | application/json |  |
| Accept | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| $skip | 0 |  |
| $top | 1000 |  |
| $filter | Favorite%20eq%20true |  |
| $inlinecount | allpages |  |



***More example Requests/Responses:***


##### I. Example Request: User Favorites Accounts - Top 100


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
| $skip | 0 |  |
| $top | 1000 |  |
| $filter | Favorite%20eq%20true |  |
| $inlinecount | allpages |  |



##### I. Example Response: User Favorites Accounts - Top 100
```js
{
    "d": {
        "__count": "6",
        "results": [
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezQ2YWUxNDViZjliNjM2ZDUyNWI0NDRiOTc2ZjIxOGJhfQ')",
                    "uri": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezQ2YWUxNDViZjliNjM2ZDUyNWI0NDRiOTc2ZjIxOGJhfQ')",
                    "type": "com.sap.banking.common.endpoint.v1_0.beans.Account"
                },
                "Id": "ZW5jezQ2YWUxNDViZjliNjM2ZDUyNWI0NDRiOTc2ZjIxOGJhfQ",
                "Number": "20213006743",
                "NumberMasked": "XXXXXXX6743",
                "BankID": "1000",
                "BankName": "",
                "NickName": "Virtual",
                "Type": "CHECKING",
                "Status": "ACTIVE",
                "CurrencyCode": "LPS",
                "TrackingID": null,
                "AccountGroup": "DEPOSIT",
                "PrimaryAccount": "0",
                "CoreAccount": "1",
                "RoutingNum": "660110110",
                "LocationID": null,
                "AccountDisplayText": "XXXXXXX6743",
                "PriorDayBalance": "0",
                "CurrentBalance": "0.00",
                "IntradayCurrentBalance": null,
                "AvailableBalance": "0.00",
                "Favorite": true,
                "EntitlementObjectId": "ZW5jezdhYjViYjQ5Y2NmY2YzMmVjMWNmNTE1ODhkMzhkYzg5MmQ1ODYzODE4ZDUyNWVjNWVmZGZkZDhiNWE3NjQ2ZWN9",
                "customCCAvailableBalanceUSD": null,
                "customCCAvailableBalanceBaseCurrency": null,
                "customStatus": "A",
                "customLimit": null,
                "customHoldBalance": "400.0",
                "customDeferredBalance": "-400.0",
                "customOriginalBalance": null,
                "customInterestFee": null,
                "customOpeningDate": null,
                "customClosingDate": null,
                "customRenewalDate": null,
                "customCCEndDate": null,
                "customCCEndDateBalance": null,
                "customCCEndDateBalanceLPS": null,
                "customCCEndDateBalanceUSD": null,
                "customCCLastPaymentDate": null,
                "customCCMinPayment": null,
                "customLimitLPS": null,
                "customCCMinPaymentLPS": null,
                "customLimitUSD": null,
                "customCCMinPaymentUSD": null,
                "customCCCurrentBalanceUSD": null,
                "customCCCurrentBalanceLPS": null,
                "customAplicacion": null,
                "customPeriodCollectionJSON": "{\"periodos\": [{\"periodo\":\"00\", \"descripcion\":\"Periodo Finalizando el 31/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|00|Periodo Finalizando el 31/03/21|\", \"valido\":\"S\"},{\"periodo\":\"01\", \"descripcion\":\"Periodo Finalizado el 28/02/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|01|Periodo Finalizado el 28/02/21|\", \"valido\":\"S\"},{\"periodo\":\"02\", \"descripcion\":\"Periodo Finalizado el 31/01/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|02|Periodo Finalizado el 31/01/21|\", \"valido\":\"S\"},{\"periodo\":\"03\", \"descripcion\":\"Periodo Finalizado el 31/12/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|03|Periodo Finalizado el 31/12/20|\", \"valido\":\"S\"},{\"periodo\":\"04\", \"descripcion\":\"Periodo Finalizado el 30/11/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|04|Periodo Finalizado el 30/11/20|\", \"valido\":\"S\"},{\"periodo\":\"05\", \"descripcion\":\"Periodo Finalizado el 31/10/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|05|Periodo Finalizado el 31/10/20|\", \"valido\":\"S\"},{\"periodo\":\"06\", \"descripcion\":\"Periodo Finalizado el 30/09/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|06|Periodo Finalizado el 30/09/20|\", \"valido\":\"S\"},{\"periodo\":\"90\", \"descripcion\":\"Transacciones del Dia 29/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|90|Transacciones del Dia 29/03/21|\", \"valido\":\"S\"},{\"periodo\":\"91\", \"descripcion\":\"Transacciones del Dia 26/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"20213006743|91|Transacciones del Dia 26/03/21|\", \"valido\":\"S\"}]}",
                "customCCMPInitialBalance": null,
                "customCCMPCredits": null,
                "customCCMPDebits": null,
                "customCCMPFinalBalance": null,
                "customReferenceNumber": null,
                "customExpirationDate": null,
                "customApprovedLimit": null,
                "customAmountUsed": null,
                "customAccruedInterestToday": null,
                "customFloatingFund": null,
                "customInterestDue": null,
                "customReserverFund": null,
                "customCollectionOfArrears": null,
                "customOtherLocks": null,
                "customInterestForLatePayment": null,
                "customTotalToPay": null,
                "mensaje": "T"
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezQxYTdmZTBjN2MyNjJmNGQ2ZGU4N2Y5YTNjMDI1MDE4fQ')",
                    "uri": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezQxYTdmZTBjN2MyNjJmNGQ2ZGU4N2Y5YTNjMDI1MDE4fQ')",
                    "type": "com.sap.banking.common.endpoint.v1_0.beans.Account"
                },
                "Id": "ZW5jezQxYTdmZTBjN2MyNjJmNGQ2ZGU4N2Y5YTNjMDI1MDE4fQ",
                "Number": "10121001076",
                "NumberMasked": "XXXXXXX1076",
                "BankID": "1000",
                "BankName": "",
                "NickName": "Virtual Prueba MO",
                "Type": "SAVINGS",
                "Status": "ACTIVE",
                "CurrencyCode": "LPS",
                "TrackingID": null,
                "AccountGroup": "DEPOSIT",
                "PrimaryAccount": "0",
                "CoreAccount": "1",
                "RoutingNum": "660110110",
                "LocationID": null,
                "AccountDisplayText": "XXXXXXX1076",
                "PriorDayBalance": "0",
                "CurrentBalance": "9000000.08",
                "IntradayCurrentBalance": null,
                "AvailableBalance": "8000000.08",
                "Favorite": true,
                "EntitlementObjectId": "ZW5jezQ3MTNiNzFiY2UzMWMzNDNjMGM2NTljMGYyMDBiY2YwZDdjZmQ3ZjJkZmFhNWYzNWYzOGM3NWUyZjE3NjM3MDB9",
                "customCCAvailableBalanceUSD": null,
                "customCCAvailableBalanceBaseCurrency": null,
                "customStatus": "A",
                "customLimit": null,
                "customHoldBalance": "400.0",
                "customDeferredBalance": "999600.0",
                "customOriginalBalance": null,
                "customInterestFee": null,
                "customOpeningDate": null,
                "customClosingDate": null,
                "customRenewalDate": null,
                "customCCEndDate": null,
                "customCCEndDateBalance": null,
                "customCCEndDateBalanceLPS": null,
                "customCCEndDateBalanceUSD": null,
                "customCCLastPaymentDate": null,
                "customCCMinPayment": null,
                "customLimitLPS": null,
                "customCCMinPaymentLPS": null,
                "customLimitUSD": null,
                "customCCMinPaymentUSD": null,
                "customCCCurrentBalanceUSD": null,
                "customCCCurrentBalanceLPS": null,
                "customAplicacion": null,
                "customPeriodCollectionJSON": "{\"periodos\": [{\"periodo\":\"00\", \"descripcion\":\"Estado de Cuenta al 29/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"10121001076|00|Estado de Cuenta al 29/03/21|\", \"valido\":\"S\"}]}",
                "customCCMPInitialBalance": null,
                "customCCMPCredits": null,
                "customCCMPDebits": null,
                "customCCMPFinalBalance": null,
                "customReferenceNumber": null,
                "customExpirationDate": null,
                "customApprovedLimit": null,
                "customAmountUsed": null,
                "customAccruedInterestToday": null,
                "customFloatingFund": null,
                "customInterestDue": null,
                "customReserverFund": null,
                "customCollectionOfArrears": null,
                "customOtherLocks": null,
                "customInterestForLatePayment": null,
                "customTotalToPay": null,
                "mensaje": "T"
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezQ1MTU2N2NlMjk4NjE1NmZiMWFmZWE4YjJhM2Y3NzJhfQ')",
                    "uri": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezQ1MTU2N2NlMjk4NjE1NmZiMWFmZWE4YjJhM2Y3NzJhfQ')",
                    "type": "com.sap.banking.common.endpoint.v1_0.beans.Account"
                },
                "Id": "ZW5jezQ1MTU2N2NlMjk4NjE1NmZiMWFmZWE4YjJhM2Y3NzJhfQ",
                "Number": "1100000114",
                "NumberMasked": "XXXXXX0114",
                "BankID": "1000",
                "BankName": "",
                "NickName": "Cuenta de prueba secundaria",
                "Type": "CHECKING",
                "Status": "ACTIVE",
                "CurrencyCode": "LPS",
                "TrackingID": null,
                "AccountGroup": "DEPOSIT",
                "PrimaryAccount": "0",
                "CoreAccount": "1",
                "RoutingNum": "660110110",
                "LocationID": null,
                "AccountDisplayText": "XXXXXX0114",
                "PriorDayBalance": "0",
                "CurrentBalance": "9000000.08",
                "IntradayCurrentBalance": null,
                "AvailableBalance": "8000000.08",
                "Favorite": true,
                "EntitlementObjectId": "ZW5je2YxN2RlOGJkZTNmNTQxY2I4OGE0ZDk5MDliYzhlOTg3ODZhOWZjMmFiMTI3YjMwZTEzN2M5NWQzMTNkNTAyYTJ9",
                "customCCAvailableBalanceUSD": null,
                "customCCAvailableBalanceBaseCurrency": null,
                "customStatus": "A",
                "customLimit": null,
                "customHoldBalance": "400.0",
                "customDeferredBalance": "999600.0",
                "customOriginalBalance": null,
                "customInterestFee": null,
                "customOpeningDate": null,
                "customClosingDate": null,
                "customRenewalDate": null,
                "customCCEndDate": null,
                "customCCEndDateBalance": null,
                "customCCEndDateBalanceLPS": null,
                "customCCEndDateBalanceUSD": null,
                "customCCLastPaymentDate": null,
                "customCCMinPayment": null,
                "customLimitLPS": null,
                "customCCMinPaymentLPS": null,
                "customLimitUSD": null,
                "customCCMinPaymentUSD": null,
                "customCCCurrentBalanceUSD": null,
                "customCCCurrentBalanceLPS": null,
                "customAplicacion": null,
                "customPeriodCollectionJSON": "{\"periodos\": [{\"periodo\":\"00\", \"descripcion\":\"Periodo Finalizando el 31/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|00|Periodo Finalizando el 31/03/21|\", \"valido\":\"S\"},{\"periodo\":\"01\", \"descripcion\":\"Periodo Finalizado el 28/02/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|01|Periodo Finalizado el 28/02/21|\", \"valido\":\"S\"},{\"periodo\":\"02\", \"descripcion\":\"Periodo Finalizado el 31/01/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|02|Periodo Finalizado el 31/01/21|\", \"valido\":\"S\"},{\"periodo\":\"03\", \"descripcion\":\"Periodo Finalizado el 31/12/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|03|Periodo Finalizado el 31/12/20|\", \"valido\":\"S\"},{\"periodo\":\"04\", \"descripcion\":\"Periodo Finalizado el 30/11/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|04|Periodo Finalizado el 30/11/20|\", \"valido\":\"S\"},{\"periodo\":\"05\", \"descripcion\":\"Periodo Finalizado el 31/10/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|05|Periodo Finalizado el 31/10/20|\", \"valido\":\"S\"},{\"periodo\":\"06\", \"descripcion\":\"Periodo Finalizado el 30/09/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|06|Periodo Finalizado el 30/09/20|\", \"valido\":\"S\"},{\"periodo\":\"07\", \"descripcion\":\"Periodo Finalizado el 31/08/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|07|Periodo Finalizado el 31/08/20|\", \"valido\":\"S\"},{\"periodo\":\"08\", \"descripcion\":\"Periodo Finalizado el 31/07/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|08|Periodo Finalizado el 31/07/20|\", \"valido\":\"S\"},{\"periodo\":\"09\", \"descripcion\":\"Periodo Finalizado el 30/06/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|09|Periodo Finalizado el 30/06/20|\", \"valido\":\"S\"},{\"periodo\":\"010\", \"descripcion\":\"Periodo Finalizado el 31/05/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|010|Periodo Finalizado el 31/05/20|\", \"valido\":\"S\"},{\"periodo\":\"90\", \"descripcion\":\"Transacciones del Dia 29/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|90|Transacciones del Dia 29/03/21|\", \"valido\":\"S\"},{\"periodo\":\"91\", \"descripcion\":\"Transacciones del Dia 26/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"1100000114|91|Transacciones del Dia 26/03/21|\", \"valido\":\"S\"}]}",
                "customCCMPInitialBalance": null,
                "customCCMPCredits": null,
                "customCCMPDebits": null,
                "customCCMPFinalBalance": null,
                "customReferenceNumber": null,
                "customExpirationDate": null,
                "customApprovedLimit": null,
                "customAmountUsed": null,
                "customAccruedInterestToday": null,
                "customFloatingFund": null,
                "customInterestDue": null,
                "customReserverFund": null,
                "customCollectionOfArrears": null,
                "customOtherLocks": null,
                "customInterestForLatePayment": null,
                "customTotalToPay": null,
                "mensaje": "T"
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezc3OWRkNzU2MTU4OGE4MDA1ZTk1MTI1NTExNmFjNjY1fQ')",
                    "uri": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezc3OWRkNzU2MTU4OGE4MDA1ZTk1MTI1NTExNmFjNjY1fQ')",
                    "type": "com.sap.banking.common.endpoint.v1_0.beans.Account"
                },
                "Id": "ZW5jezc3OWRkNzU2MTU4OGE4MDA1ZTk1MTI1NTExNmFjNjY1fQ",
                "Number": "750019003786",
                "NumberMasked": "XXXXXXXX3786",
                "BankID": "1000",
                "BankName": "",
                "NickName": "Cuenta de empleado",
                "Type": "CHECKING",
                "Status": "ACTIVE",
                "CurrencyCode": "LPS",
                "TrackingID": null,
                "AccountGroup": "DEPOSIT",
                "PrimaryAccount": "0",
                "CoreAccount": "1",
                "RoutingNum": "660110110",
                "LocationID": null,
                "AccountDisplayText": "XXXXXXXX3786",
                "PriorDayBalance": "0",
                "CurrentBalance": "9000000.08",
                "IntradayCurrentBalance": null,
                "AvailableBalance": "8000000.08",
                "Favorite": true,
                "EntitlementObjectId": "ZW5je2RlNDkyYjU2MDFjNzFiZTkyNDRhODNlOGMzNzk1ODliYzVmNWEyYzRkMjU1MTZiMjExNWJjYTkzOThhZjQ0ZDl9",
                "customCCAvailableBalanceUSD": null,
                "customCCAvailableBalanceBaseCurrency": null,
                "customStatus": "A",
                "customLimit": null,
                "customHoldBalance": "400.0",
                "customDeferredBalance": "999600.0",
                "customOriginalBalance": null,
                "customInterestFee": null,
                "customOpeningDate": null,
                "customClosingDate": null,
                "customRenewalDate": null,
                "customCCEndDate": null,
                "customCCEndDateBalance": null,
                "customCCEndDateBalanceLPS": null,
                "customCCEndDateBalanceUSD": null,
                "customCCLastPaymentDate": null,
                "customCCMinPayment": null,
                "customLimitLPS": null,
                "customCCMinPaymentLPS": null,
                "customLimitUSD": null,
                "customCCMinPaymentUSD": null,
                "customCCCurrentBalanceUSD": null,
                "customCCCurrentBalanceLPS": null,
                "customAplicacion": null,
                "customPeriodCollectionJSON": "{\"periodos\": [{\"periodo\":\"00\", \"descripcion\":\"Periodo Finalizando el 31/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|00|Periodo Finalizando el 31/03/21|\", \"valido\":\"S\"},{\"periodo\":\"01\", \"descripcion\":\"Periodo Finalizado el 28/02/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|01|Periodo Finalizado el 28/02/21|\", \"valido\":\"S\"},{\"periodo\":\"02\", \"descripcion\":\"Periodo Finalizado el 31/01/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|02|Periodo Finalizado el 31/01/21|\", \"valido\":\"S\"},{\"periodo\":\"03\", \"descripcion\":\"Periodo Finalizado el 31/12/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|03|Periodo Finalizado el 31/12/20|\", \"valido\":\"S\"},{\"periodo\":\"04\", \"descripcion\":\"Periodo Finalizado el 30/11/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|04|Periodo Finalizado el 30/11/20|\", \"valido\":\"S\"},{\"periodo\":\"05\", \"descripcion\":\"Periodo Finalizado el 31/10/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|05|Periodo Finalizado el 31/10/20|\", \"valido\":\"S\"},{\"periodo\":\"06\", \"descripcion\":\"Periodo Finalizado el 30/09/20\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|06|Periodo Finalizado el 30/09/20|\", \"valido\":\"S\"},{\"periodo\":\"90\", \"descripcion\":\"Transacciones del Dia 29/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|90|Transacciones del Dia 29/03/21|\", \"valido\":\"S\"},{\"periodo\":\"91\", \"descripcion\":\"Transacciones del Dia 26/03/21\", \"fechaInicio\":\"\", \"fechaFinal\":\"\", \"mensaje\":\"750019003786|91|Transacciones del Dia 26/03/21|\", \"valido\":\"S\"}]}",
                "customCCMPInitialBalance": null,
                "customCCMPCredits": null,
                "customCCMPDebits": null,
                "customCCMPFinalBalance": null,
                "customReferenceNumber": null,
                "customExpirationDate": null,
                "customApprovedLimit": null,
                "customAmountUsed": null,
                "customAccruedInterestToday": null,
                "customFloatingFund": null,
                "customInterestDue": null,
                "customReserverFund": null,
                "customCollectionOfArrears": null,
                "customOtherLocks": null,
                "customInterestForLatePayment": null,
                "customTotalToPay": null,
                "mensaje": "T"
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezczODQ4NmFmNDg3NzVlMTE3ZmJlNjRlYjFkZDcwNjg4fQ')",
                    "uri": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezczODQ4NmFmNDg3NzVlMTE3ZmJlNjRlYjFkZDcwNjg4fQ')",
                    "type": "com.sap.banking.common.endpoint.v1_0.beans.Account"
                },
                "Id": "ZW5jezczODQ4NmFmNDg3NzVlMTE3ZmJlNjRlYjFkZDcwNjg4fQ",
                "Number": "528020090971",
                "NumberMasked": "XXXXXXXX0971",
                "BankID": "1000",
                "BankName": "",
                "NickName": "CLB - Tarjeta Credito Celebra",
                "Type": "CREDIT",
                "Status": "ACTIVE",
                "CurrencyCode": "LPS",
                "TrackingID": null,
                "AccountGroup": "CREDITCARD",
                "PrimaryAccount": "0",
                "CoreAccount": "1",
                "RoutingNum": "660110110",
                "LocationID": null,
                "AccountDisplayText": "XXXXXXXX0971",
                "PriorDayBalance": null,
                "CurrentBalance": "3195.38",
                "IntradayCurrentBalance": null,
                "AvailableBalance": "1131445105.5",
                "Favorite": true,
                "EntitlementObjectId": "ZW5jezE1YmI0ZTQ3OTEzYzlkNzQ5OWE4YzdjMTAyMzdjY2M2Mjg2YTRlYTFhZGVhYjYwNGMzY2UxNjdiNWUyYzVlOTl9",
                "customCCAvailableBalanceUSD": "7.54",
                "customCCAvailableBalanceBaseCurrency": null,
                "customStatus": "A",
                "customLimit": "0.00",
                "customHoldBalance": null,
                "customDeferredBalance": null,
                "customOriginalBalance": null,
                "customInterestFee": null,
                "customOpeningDate": null,
                "customClosingDate": null,
                "customRenewalDate": null,
                "customCCEndDate": "08/08/2013",
                "customCCEndDateBalance": "3103.86",
                "customCCEndDateBalanceLPS": "3103.86",
                "customCCEndDateBalanceUSD": "10.42",
                "customCCLastPaymentDate": "02/09/2013",
                "customCCMinPayment": "370.00",
                "customLimitLPS": "0.00",
                "customCCMinPaymentLPS": "370.00",
                "customLimitUSD": "0.00",
                "customCCMinPaymentUSD": "3.54",
                "customCCCurrentBalanceUSD": "5.65",
                "customCCCurrentBalanceLPS": "3195.38",
                "customAplicacion": "01",
                "customPeriodCollectionJSON": "{\"periodos\": [{\"periodo\":\"00\", \"descripcion\":\"Estado de Cuenta al 06/04/21\", \"fechaInicio\":\"20210406\", \"fechaFinal\":\"20210406\", \"mensaje\":\"528020090971|00|Estado de Cuenta al 06/04/21|\", \"valido\":\"S\"},{\"periodo\":\"90\", \"descripcion\":\"Movimientos al dia 06/04/21\", \"fechaInicio\":\"20210406\", \"fechaFinal\":\"20210406\", \"mensaje\":\"528020090971|90|Movimientos al dia 06/04/21|\", \"valido\":\"S\"}]}",
                "customCCMPInitialBalance": "968.21",
                "customCCMPCredits": "0.00",
                "customCCMPDebits": "0.00",
                "customCCMPFinalBalance": "968.21",
                "customReferenceNumber": null,
                "customExpirationDate": null,
                "customApprovedLimit": null,
                "customAmountUsed": null,
                "customAccruedInterestToday": null,
                "customFloatingFund": null,
                "customInterestDue": null,
                "customReserverFund": null,
                "customCollectionOfArrears": null,
                "customOtherLocks": null,
                "customInterestForLatePayment": null,
                "customTotalToPay": null,
                "mensaje": "T"
            },
            {
                "__metadata": {
                    "id": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezE4NGNlYTQwOGI1NjgyNWQwMDg1NjNjMjdiZmI3YzI2fQ')",
                    "uri": "http://localhost:8888/odata/services/accountservice/Accounts('ZW5jezE4NGNlYTQwOGI1NjgyNWQwMDg1NjNjMjdiZmI3YzI2fQ')",
                    "type": "com.sap.banking.common.endpoint.v1_0.beans.Account"
                },
                "Id": "ZW5jezE4NGNlYTQwOGI1NjgyNWQwMDg1NjNjMjdiZmI3YzI2fQ",
                "Number": "498400080105",
                "NumberMasked": "XXXXXXXX0105",
                "BankID": "1000",
                "BankName": "",
                "NickName": "TC VISA INTERNACIONAL",
                "Type": "CREDIT",
                "Status": "ACTIVE",
                "CurrencyCode": "LPS",
                "TrackingID": null,
                "AccountGroup": "CREDITCARD",
                "PrimaryAccount": "0",
                "CoreAccount": "1",
                "RoutingNum": "660110110",
                "LocationID": null,
                "AccountDisplayText": "XXXXXXXX0105",
                "PriorDayBalance": null,
                "CurrentBalance": "3195.38",
                "IntradayCurrentBalance": null,
                "AvailableBalance": "1131445105.5",
                "Favorite": true,
                "EntitlementObjectId": "ZW5jezhmYjUwOTU3MDJlMjIwMmU0OTk4MTZhNWQ2MWZlMmEwZTUyZjkyNDdjYmE0ZDBhMTU0NTZiYTljOWUxMDQ5YTZ9",
                "customCCAvailableBalanceUSD": "7.54",
                "customCCAvailableBalanceBaseCurrency": null,
                "customStatus": "A",
                "customLimit": "0.00",
                "customHoldBalance": null,
                "customDeferredBalance": null,
                "customOriginalBalance": null,
                "customInterestFee": null,
                "customOpeningDate": null,
                "customClosingDate": null,
                "customRenewalDate": null,
                "customCCEndDate": "08/08/2013",
                "customCCEndDateBalance": "3103.86",
                "customCCEndDateBalanceLPS": "3103.86",
                "customCCEndDateBalanceUSD": "10.42",
                "customCCLastPaymentDate": "02/09/2013",
                "customCCMinPayment": "370.00",
                "customLimitLPS": "0.00",
                "customCCMinPaymentLPS": "370.00",
                "customLimitUSD": "0.00",
                "customCCMinPaymentUSD": "3.54",
                "customCCCurrentBalanceUSD": "5.65",
                "customCCCurrentBalanceLPS": "3195.38",
                "customAplicacion": "00",
                "customPeriodCollectionJSON": "{\"periodos\": [{\"periodo\":\"00\", \"descripcion\":\"Estado de Cuenta al 06/04/21\", \"fechaInicio\":\"20210406\", \"fechaFinal\":\"20210406\", \"mensaje\":\"498400080105|00|Estado de Cuenta al 06/04/21|\", \"valido\":\"S\"},{\"periodo\":\"90\", \"descripcion\":\"Movimientos al dia 06/04/21\", \"fechaInicio\":\"20210406\", \"fechaFinal\":\"20210406\", \"mensaje\":\"498400080105|90|Movimientos al dia 06/04/21|\", \"valido\":\"S\"}]}",
                "customCCMPInitialBalance": "968.21",
                "customCCMPCredits": "0.00",
                "customCCMPDebits": "0.00",
                "customCCMPFinalBalance": "968.21",
                "customReferenceNumber": null,
                "customExpirationDate": null,
                "customApprovedLimit": null,
                "customAmountUsed": null,
                "customAccruedInterestToday": null,
                "customFloatingFund": null,
                "customInterestDue": null,
                "customReserverFund": null,
                "customCollectionOfArrears": null,
                "customOtherLocks": null,
                "customInterestForLatePayment": null,
                "customTotalToPay": null,
                "mensaje": "T"
            }
        ]
    }
}
```


***Status Code:*** 200

<br>



### 6. User Information by ID


#### Información del Usuario
Este método nos permite obtener toda la información del usuario con el cual se inició sesión
###### Parametros necesario
Es necesario enviar en el header de la petición los siguientes parametros:

- `x-csrf-token` : Este parametro es obtenido al momento de iniciar sesión

- `TokenKey` : Token obtenido en el incio de sesión

- `Content-Type` : Ingresando como valor para el tipo de contenido **application/json**

- `Accept` : Aceptando como respuesta el valor **application/json**

- `UserProfileID` : Es el código del usuario, este obtenido el la repuesta del login


###### Respuesta
Como resultado se obtiene la información respectiva del usuario


***Endpoint:***

```bash
Method: GET
Type: 
URL: {{URL}}/odata/services/retailuserservice/RetailUsers('{{UserProfileID}}')
```


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| x-csrf-token | {{x-csrf-token}} |  |
| Accept | application/json |  |
| TokenKey | {{TokenKey}} |  |



***More example Requests/Responses:***


##### I. Example Request: User Information by ID


***Headers:***

| Key | Value | Description |
| --- | ------|-------------|
| x-csrf-token | {{x-csrf-token}} |  |
| Accept | application/json |  |
| TokenKey | {{TokenKey}} |  |



##### I. Example Response: User Information by ID
```js
{
    "d": {
        "__metadata": {
            "id": "http://localhost:8888/odata/services/retailuserservice/RetailUsers('ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ')",
            "uri": "http://localhost:8888/odata/services/retailuserservice/RetailUsers('ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ')",
            "type": "com.sap.banking.user.endpoint.v1_0.beans.RetailUser"
        },
        "Id": "ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ",
        "FirstName": "PEDRO JOSE",
        "LastName": "VELASQUEZ ZAMBRANO",
        "MiddleName": null,
        "AffiliateBankID": 1,
        "BankId": "1000",
        "ConfirmPassword": null,
        "ConfirmPasswordReminder": null,
        "ConfirmPasswordReminder2": null,
        "CustId": "ZW5jezhmY2M2ODAyOWVmMzgxYTQ2M2Q2NDA5NGNkNjRhOTM0fQ",
        "Greeting": null,
        "GreetingType": "0",
        "Gender": "0",
        "Password": null,
        "PasswordClue": null,
        "PasswordClue2": null,
        "MemberId": null,
        "GroupId": "2008",
        "GroupName": null,
        "PasswordReminder": null,
        "PasswordReminder2": null,
        "PersonalBanker": "0",
        "PersonalBankerName": null,
        "Ssn": null,
        "MaskSSN": null,
        "UserName": "pvelasq017",
        "UserType": "1",
        "AccountStatus": "1",
        "Timeout": "900",
        "CustomerType": "2",
        "RequestedCarrierTCId": null,
        "OldPassword": null,
        "NewPassword": null,
        "PasswordStatus": "0",
        "Address": {
            "__metadata": {
                "type": "com.sap.banking.common.endpoint.v1_0.beans.Address"
            },
            "Street": "ALDEA CERRO GRANDE, VALLE DE ANGELES,",
            "Street2": null,
            "Street3": null,
            "City": "VALLE DE ANGELES",
            "State": null,
            "StreetCode": null,
            "Country": "HND",
            "Email": "ocbbanking@bancatlan.onmicrosoft.com",
            "Phone": "99820988",
            "Phone2": "22800000",
            "ZipCode": null,
            "DataPhone": "97539812",
            "FaxPhone": null,
            "PreferredContactMethod": null,
            "PreferredLanguage": "es_HN",
            "PreferredLanguageDisplayName": null
        },
        "ImageId": null,
        "SecretPhrase": null,
        "SecurityCredentials": {
            "__deferred": {
                "uri": "http://localhost:8888/odata/services/retailuserservice/RetailUsers('ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ')/SecurityCredentials"
            }
        },
        "Transactions": {
            "__deferred": {
                "uri": "http://localhost:8888/odata/services/retailuserservice/RetailUsers('ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ')/Transactions"
            }
        },
        "PersonalProfile": {
            "__deferred": {
                "uri": "http://localhost:8888/odata/services/retailuserservice/RetailUsers('ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ')/PersonalProfile"
            }
        },
        "RetailUserProfiles": {
            "__deferred": {
                "uri": "http://localhost:8888/odata/services/retailuserservice/RetailUsers('ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ')/RetailUserProfiles"
            }
        },
        "RetailUserFeatures": {
            "__deferred": {
                "uri": "http://localhost:8888/odata/services/retailuserservice/RetailUsers('ZW5jezY0NWRiZTcwZmIzYjkwOTRkMDBkZDQzNjIwYWVhOGU4fQ')/RetailUserFeatures"
            }
        }
    }
}
```


***Status Code:*** 200

<br>



### 7. User Transactions - Top 10


#### Top 10 ultimas transacciones
Este método nos permite obtener el **Top 10** de las ultimas transacciones realizadas por el usuario con el cual se inició sesión, este resultado es mostrado en un box en la pantalla principal del menú

###### Parametros necesario
Es necesario enviar en el header de la petición los siguientes parametros:

- `x-csrf-token` : Este parametro es obtenido al momento de iniciar sesión

- `TokenKey` : Token obtenido en el incio de sesión

- `Content-Type` : Ingresando como valor para el tipo de contenido **application/json**

- `Accept` : Aceptando como respuesta el valor **application/json**

###### Respuesta
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
| x-csrf-token | {{x-csrf-token}} |  |
| TokenKey | {{TokenKey}} |  |
| Content-Type | application/json |  |
| Accept | application/json |  |



***Query params:***

| Key | Value | Description |
| --- | ------|-------------|
| $skip | 0 |  |
| $top | 10 |  |
| $filter | Type%20eq%20%27HOME%27 |  |
| $inlinecount | allpages |  |



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
| $skip | 0 |  |
| $top | 10 |  |
| $filter | Type%20eq%20%27HOME%27 |  |
| $inlinecount | allpages |  |



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
[Back to top](#hn---login)
> Made with &#9829; by [thedevsaddam](https://github.com/thedevsaddam) | Generated at: 2021-04-06 17:40:13 by [docgen](https://github.com/thedevsaddam/docgen)
