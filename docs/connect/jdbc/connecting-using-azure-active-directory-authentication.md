---
title: Connessione con l'autenticazione di Azure Active Directory | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2020
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7019efd6e1071624eb3e89873918fb9eb2775833
ms.sourcegitcommit: 4b2c9d648b7a7bdf9c3052ebfeef182e2f9d66af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "77004643"
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Connessione con l'autenticazione di Azure Active Directory

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Questo articolo offre informazioni su come sviluppare applicazioni Java per usare la funzionalità di autenticazione di Azure Active Directory con Microsoft JDBC Driver per SQL Server.

È possibile usare l'autenticazione di Azure Active Directory (AAD) che è un meccanismo di connessione al database SQL di Azure v12 tramite identità in Azure Active Directory. Usare l'autenticazione di Azure Active Directory per gestire centralmente le identità degli utenti del database e come alternativa all'autenticazione di SQL Server. Il driver JDBC consente di specificare le credenziali di Azure Active Directory nella stringa di connessione JDBC per connettersi al database SQL di Azure. Per informazioni su come configurare l'autenticazione di Azure Active Directory, vedere [Connessione al database SQL usando l'autenticazione di Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Le proprietà di connessione per supportare l'autenticazione di Azure Active Directory in Microsoft JDBC Driver per SQL Server sono le seguenti:
*   **authentication**:  usare questa proprietà per specificare il metodo di autenticazione SQL da usare per la connessione. I valori possibili sono: 
    * **ActiveDirectoryMSI**
        * Supportato a partire dalla versione del driver **v7.2**, `authentication=ActiveDirectoryMSI` consente di connettersi a un database SQL di Azure o ad Azure SQL Data Warehouse dall'interno di una risorsa di Azure con il supporto di identità abilitato. Facoltativamente, è possibile specificare insieme a questa modalità di autenticazione anche **msiClientId** nelle proprietà Connection/DataSource che devono includere l'ID client dell'identità di un servizio gestito da usare per acquisire **accessToken** per stabilire la connessione.
    * **ActiveDirectoryIntegrated**
        * Supportato a partire dalla versione del driver **v6.0**, `authentication=ActiveDirectoryIntegrated` consente di connettersi a un database SQL di Azure o ad Azure SQL Data Warehouse usando l'autenticazione integrata. Per usare questa modalità di autenticazione, è necessaria la federazione di Active Directory Federation Services (ADFS) locale con Azure Active Directory nel cloud. Al termine della configurazione, è possibile connettersi aggiungendo la libreria nativa 'mssql-jdbc_auth-\<versione>-\<arch>.dll' al percorso della classe dell'applicazione nel sistema operativo Windows o impostando un ticket Kerberos per il supporto dell'autenticazione multipiattaforma. È possibile accedere al database SQL di Azure o ad Azure SQL Data Warehouse senza che vengano richieste le credenziali quando si è connessi a un computer aggiunto al dominio.
    * **ActiveDirectoryPassword**
        * Supportato a partire dalla versione del driver **v6.0**, `authentication=ActiveDirectoryPassword` consente di connettersi a un database SQL di Azure o ad Azure SQL Data Warehouse usando il nome di un'entità di sicurezza e la password.
    * **SqlPassword**
        * Usare `authentication=SqlPassword` per connettersi a SQL Server usando le proprietà userName/user e password.
    * **NotSpecified**
        * Usare `authentication=NotSpecified` o lasciare l'impostazione predefinita quando nessuno di questi metodi di autenticazione è necessario.

*   **accessToken**: usare questa proprietà di connessione per connettersi a un database SQL usando un token di accesso. accessToken può essere impostato solo usando il parametro Properties del metodo getConnection() nella classe DriverManager. Non può essere usato nell'URL di connessione.  

Per altre informazioni, vedere la proprietà di autenticazione nella pagina [Impostazione delle proprietà delle connessioni](../../connect/jdbc/setting-the-connection-properties.md).  


## <a name="client-setup-requirements"></a>Requisiti di installazione del client
Per l'autenticazione **ActiveDirectoryMSI**, è necessario installare nel computer client i componenti seguenti:
* Java 8 o versione successiva
* Microsoft JDBC Driver 7.2 (o versione successiva) per SQL Server
* L'ambiente client deve essere una risorsa di Azure e deve avere il supporto della funzionalità di identità abilitato.
* È necessario che nel database di destinazione sia presente un utente del database indipendente che rappresenta l'identità gestita assegnata dal sistema o l'identità gestita assegnata dall'utente della risorsa di Azure o uno dei gruppi a cui appartiene il file MSI e deve avere l'autorizzazione CONNECT.

Per le altre modalità di autenticazione, è necessario installare nel computer client i componenti seguenti:
* Java 7 o versione successiva
* Microsoft JDBC Driver 6.0 (o versione successiva) per SQL Server
* Se si usa la modalità di autenticazione basata su token di accesso, è necessario avere [azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze per eseguire gli esempi di questo articolo. Per altre informazioni, vedere la sezione **Connessione tramite token di accesso**.
* Se si utilizza la modalità di autenticazione **ActiveDirectoryPassword**, è necessario avere [azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze. Per altre informazioni, vedere la sezione **Connessione tramite la modalità di autenticazione ActiveDirectoryPassword**.
* Se si usa la modalità **ActiveDirectoryIntegrated**, è necessario avere azure-activedirectory-library-for-java e le relative dipendenze. Per altre informazioni, vedere la sezione **Connessione tramite la modalità di autenticazione ActiveDirectoryIntegrated**.

## <a name="connecting-using-activedirectorymsi-authentication-mode"></a>Connessione tramite la modalità di autenticazione ActiveDirectoryMSI
L'esempio seguente illustra come usare la modalità `authentication=ActiveDirectoryMSI`. Eseguire questo esempio dall'interno di una risorsa di Azure, ad esempio una macchina virtuale di Azure, un servizio app o un'app per le funzioni federata con Azure Active Directory.

Prima di eseguire l'esempio, sostituire il nome del server o database con il nome del proprio server o database nelle righe seguenti:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
//Optional
ds.setMsiClientId("94de34e9-8e8c-470a-96df-08110924b814"); // Replace with Client ID of User-Assigned MSI to be used
```

Esempio di utilizzo della modalità di autenticazione ActiveDirectoryMSI:

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AAD_MSI {
    public static void main(String[] args) throws Exception {

        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryMSI");
        // Optional
        ds.setMsiClientId("94de34e9-8e8c-470a-96df-08110924b814"); // Replace with Client ID of User-Assigned MSI to be used

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```

L'esecuzione di questo esempio in una macchina virtuale di Azure recupera un token di accesso dall'_identità gestita assegnata dal sistema_ o dall'_identità gestita assegnata dall'utente_ (se **msiClientId** è specificato) e stabilisce una connessione con il token di accesso recuperato. Se viene stabilita una connessione, verrà visualizzato il messaggio seguente:

```bash
You have successfully logged on as: <your MSI username>
```

## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Connessione tramite la modalità di autenticazione ActiveDirectoryIntegrated
Con la versione 6.4, Microsoft JDBC Driver aggiunge il supporto dell'autenticazione ActiveDirectoryIntegrated usando un ticket Kerberos su più piattaforme (Windows, Linux e macOS).
Per altre informazioni, vedere [Impostare un ticket Kerberos in Windows, Linux e Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac). In alternativa, in Windows è anche possibile usare mssql-jdbc_auth-\<versione>-\<arch>.dll per l'autenticazione ActiveDirectoryIntegrated con un driver JDBC.

> [!NOTE]
>  Se si usa una versione precedente del driver, cercare in questo [collegamento](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) le relative dipendenze necessarie per usare questa modalità di autenticazione. 

L'esempio seguente illustra come usare la modalità `authentication=ActiveDirectoryIntegrated`. Eseguire questo esempio in un computer aggiunto a un dominio federato con Azure Active Directory. È necessario che nel database di destinazione sia presente un utente del database indipendente che rappresenta l'entità di sicurezza di Azure AD o uno dei gruppi cui si appartiene e deve avere l'autorizzazione CONNECT. 

Prima di compilare ed eseguire l'esempio, nel computer client in cui si vuole eseguire l'esempio scaricare il [file di libreria azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze e includerli nel percorso di compilazione Java

Prima di eseguire l'esempio, sostituire il nome del server o database con il nome del proprio server o database nelle righe seguenti:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

Esempio di utilizzo della modalità di autenticazione ActiveDirectoryIntegrated:
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADIntegrated {
    public static void main(String[] args) throws Exception {

        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```

Se si esegue questo esempio in un computer client, viene usato automaticamente il ticket Kerberos e non viene richiesta alcuna password. Se viene stabilita una connessione, verrà visualizzato il messaggio seguente:

```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Impostare un ticket Kerberos in Windows, Linux e Mac

È necessario configurare un ticket Kerberos che collega l'utente corrente a un account di dominio di Windows. Di seguito è riportato un riepilogo dei passaggi principali.

#### <a name="windows"></a>Windows
JDK include `kinit` che consente di ottenere un ticket di concessione ticket dal Centro distribuzione chiavi (KDC) in un computer aggiunto al dominio che è federato con Azure Active Directory.

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>Passaggio 1: Recupero del ticket di concessione ticket
- **Eseguire in**: Windows
- **Azione**:
  - Usare il comando `kinit username@DOMAIN.COMPANY.COM` per ottenere un ticket di concessione ticket (TGT) dal Centro distribuzione chiavi (KDC). Verrà quindi richiesta la password del dominio.
  - Usare `klist` per visualizzare i ticket disponibili. Se kinit ha avuto esito positivo, verrà visualizzato un ticket proveniente da krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

> [!NOTE]
>  Potrebbe essere necessario specificare un file `.ini` con `-Djava.security.krb5.conf` per consentire all'applicazione di individuare il Centro distribuzione chiavi (KDC).

#### <a name="linux-and-mac"></a>Linux e Mac

##### <a name="requirements"></a>Requisiti
Accesso a un computer aggiunto a un dominio di Windows per eseguire una query sul controller di dominio Kerberos.

##### <a name="step-1-find-kerberos-kdc"></a>Passaggio 1: Trovare il Centro distribuzione chiavi (KDC) Kerberos
- **Eseguire in**: Riga di comando di Windows
- **Azione**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (dove "DOMAIN.COMPANY.COM" viene mappato al nome del dominio)
- **Output di esempio**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **Informazioni da estrarre** Il nome DC, in questo caso `co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>Passaggio 2: Configurare il Centro distribuzione chiavi (KDC) in krb5.conf
- **Eseguire in**: Linux/Mac
- **Azione**: Modificare il file /etc/krb5.conf in un editor di propria scelta. Configurare le chiavi seguenti
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  Salvare quindi il file krb5.conf e uscire

> [!NOTE]
>  Il dominio deve essere in lettere MAIUSCOLE.

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>Passaggio 3: Test del recupero del ticket di concessione ticket
- **Eseguire in**: Linux/Mac
- **Azione**:
  - Usare il comando `kinit username@DOMAIN.COMPANY.COM` per ottenere un ticket di concessione ticket (TGT) dal Centro distribuzione chiavi (KDC). Verrà quindi richiesta la password del dominio.
  - Usare `klist` per visualizzare i ticket disponibili. Se kinit ha avuto esito positivo, verrà visualizzato un ticket proveniente da krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Connessione tramite la modalità di autenticazione ActiveDirectoryPassword
L'esempio seguente illustra come usare la modalità `authentication=ActiveDirectoryPassword`.

Prima di compilare ed eseguire l'esempio:
1.  Nel computer client in cui si vuole eseguire l'esempio scaricare il [file di libreria azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze e includerli nel percorso di compilazione Java
2.  Individuare le righe di codice seguenti e sostituire il nome del server o database con il nome del proprio server o database.
    ```java
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  Individuare le righe di codice seguenti e sostituire il nome utente con il nome dell'utente di AAD con cui si vuole connettersi.
    ```java
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

Esempio di utilizzo della modalità di autenticazione ActiveDirectoryPassword:
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADUserPassword {
    
    public static void main(String[] args) throws Exception{
        
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        
        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
Se viene stabilita la connessione, verrà visualizzato il messaggio seguente:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> È necessario che nel database sia presente un utente del database indipendente che rappresenta l'utente di Azure AD specificato o uno dei gruppi a cui appartiene l'utente e deve avere l'autorizzazione CONNECT (ad eccezione dell'amministratore del server o del gruppo di Azure Active Directory)

## <a name="connecting-using-access-token"></a>Connessione tramite token di accesso
Le applicazioni e i servizi possono recuperare un token di accesso da Azure Active Directory e usarlo per connettersi al database SQL di Azure o ad Azure Data Warehouse.

> [!NOTE] 
> **accessToken** può essere impostato solo usando il parametro Properties del metodo getConnection() nella classe DriverManager. Non può essere usato nella stringa di connessione.

L'esempio seguente contiene un'applicazione Java semplice che si connette al database SQL di Azure o ad Azure Data Warehouse usando l'autenticazione basata su token di accesso. Prima di compilare ed eseguire l'esempio, seguire questa procedura:
1.  Creare un account dell'applicazione in Azure Active Directory per il servizio.
    1. Accedere al portale di Azure.
    2. Nel riquadro di spostamento a sinistra fare clic su Azure Active Directory.
    3. Fare clic su "Registrazioni app".
    4. Nel menu di spostamento fare clic su "Registrazione nuova applicazione".
    5. Immettere mytokentest come nome descrittivo per l'applicazione e selezionare "App Web/API".
    6. L'URL di accesso non è necessario. Specificare ad esempio "https://mytokentest".
    7. Fare clic su "Crea" nella parte inferiore della schermata.
    9. Sempre nel portale di Azure fare clic sulla scheda "Impostazioni" dell'applicazione e aprire la scheda "Proprietà".
    10. Trovare il valore "ID applicazione" (noto anche come ID client) e copiarlo. L'ID sarà necessario successivamente durante la configurazione dell'applicazione (ad esempio, 1846943b-ad04-4808-aa13-4702d908b5c1). Vedere lo snapshot seguente.
    11. Nella sezione "Chiavi" creare una chiave specificando un valore nel campo nome, selezionando la durata della chiave e salvando la configurazione (lasciare vuoto il campo valore). Dopo il salvataggio, il campo valore viene specificato automaticamente. Copiare il valore generato. Questo è il segreto client.
    12. Nel pannello di sinistra fare clic su Azure Active Directory. In "Registrazioni app" trovare la scheda "Endpoint". Copiare l'URL in "OATH 2.0 TOKEN ENDPOINT". Si tratta dell'URL STS.
    
    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Accedere al database utente del server SQL Azure come amministratore di Azure Active Directory e usando un comando T-SQL effettuare il provisioning di un utente di database indipendente per l'entità di sicurezza dell'applicazione. Per altre informazioni su come creare un amministratore di Azure Active Directory e un utente di database indipendente, vedere [Connessione al database o al data warehouse SQL tramite l'autenticazione di Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  Nel computer client in cui si vuole eseguire l'esempio scaricare il file di libreria [azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) e le relative dipendenze e includerli nel percorso di compilazione Java Si noti che azure-activedirectory-library-for-java è necessario solo per eseguire questo esempio specifico. L'esempio usa le API di questa libreria per recuperare il token di accesso da Azure AAD. Se si ha già un token di accesso, ignorare questo passaggio. Si noti che è necessario anche rimuovere dall'esempio la sezione che recupera il token di accesso.

Nell'esempio seguente sostituire l'URL STS, l'ID client, il segreto client, il nome del server e del database con i propri valori.

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD.
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;

public class AADTokenBased {

    public static void main(String[] args) throws Exception {

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
        String clientId = "1846943b-ad04-4808-aa13-4702d908b5c1"; // Replace with your client ID.
        String clientSecret = "..."; // Replace with your client secret.

        AuthenticationContext context = new AuthenticationContext(stsurl, false, Executors.newFixedThreadPool(1));
        ClientCredential cred = new ClientCredential(clientId, clientSecret);

        Future<AuthenticationResult> future = context.acquireToken(spn, cred, null);
        String accessToken = future.get().getAccessToken();

        System.out.println("Access Token: " + accessToken);

        // Connect with the access token.
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name.
        ds.setDatabaseName("demo"); // Replace with your database name.
        ds.setAccessToken(accessToken);

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
``` 

Se la connessione viene stabilita correttamente, verrà visualizzato il messaggio seguente:

```bash
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
