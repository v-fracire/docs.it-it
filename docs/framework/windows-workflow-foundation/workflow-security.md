---
title: Sicurezza del flusso di lavoro
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: ebce4daf433647179a0bce5751f66cdfab7a4d80
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195719"
---
# <a name="workflow-security"></a>Sicurezza del flusso di lavoro
Windows Workflow Foundation (WF) si integra con varie tecnologie diverse, ad esempio Microsoft SQL Server e Windows Communication Foundation (WCF). L'interazione con queste tecnologie può introdurre problemi di sicurezza nel flusso di lavoro, se eseguito in modo errato.

## <a name="persistence-security-concerns"></a>Problemi di sicurezza della persistenza

1.  I flussi di lavoro che usano un'attività <xref:System.Activities.Statements.Delay> e la persistenza devono essere riattivati da un servizio. In Windows AppFabric viene usato il Servizio di gestione flussi di lavoro (WMS) per riattivare i flussi di lavoro con timer scaduti. WMS consente di creare un oggetto <xref:System.ServiceModel.WorkflowServiceHost> per ospitare il flusso di lavoro riattivato. Se il servizio WMS viene arrestato, i flussi di lavoro persistenti non verranno riattivati quando i timer scadono.

2.  L'accesso alle istanze durevoli dovrebbe essere protetto da entità dannose esterne al dominio applicazione. Inoltre, gli sviluppatori devono assicurarsi che il codice dannoso non possa essere eseguito nello stesso dominio applicazione del codice dell'istanza durevole.

3.  L'istanza durevole non deve essere eseguita con autorizzazioni (di amministratore) elevate.

4.  I dati che vengono elaborati all'esterno del dominio applicazione devono essere protetti.

5.  Le applicazioni che richiedono una isolamento di sicurezza non devono condividere la stessa istanza dell'astrazione dello schema. Tali applicazioni devono usare provider di archiviazione differenti o provider di archiviazione configurati per l'uso di istanze di archiviazione.

## <a name="sql-server-security-concerns"></a>Problemi di sicurezza relativi a SQL Server

-   Quando si usano numerose attività figlio, percorsi, segnalibri, estensioni host o ambiti o quando si usano segnalibri con payload di notevoli dimensioni, la memoria può esaurirsi o si può allocare eccessivo spazio del database durante la persistenza. Questa situazione può essere attenuata con la sicurezza a livello di oggetto e a livello di database.

-   Quando si usa l'oggetto <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, l'archivio di istanze deve essere protetto. Per altre informazioni, vedere [SQL Server Best Practices](https://go.microsoft.com/fwlink/?LinkId=164972).

-   I dati sensibili nell'archivio di istanze devono essere crittografati. Per altre informazioni, vedere [crittografia di sicurezza SQL](https://go.microsoft.com/fwlink/?LinkId=164976).

-   Poiché la stringa di connessione del database è spesso inclusa in un file di configurazione, è necessario usare la sicurezza a livello di Windows (ACL) per assicurarsi che il file di configurazione (in genere Web.Config) sia protetto e che le informazioni sull'accesso e sulla password non siano incluse nella stringa di connessione. Tra il database e il server Web dovrebbe invece essere usata l'autenticazione di Windows.

## <a name="considerations-for-workflowservicehost"></a>Considerazioni su WorkflowServiceHost

-   Endpoint Windows Communication Foundation (WCF) usati nei flussi di lavoro deve essere protetto. Per altre informazioni, vedere [Cenni preliminari sulla sicurezza](https://go.microsoft.com/fwlink/?LinkID=164975).

-   È possibile implementare l'autorizzazione a livello host usando <xref:System.ServiceModel.ServiceAuthorizationManager>. Visualizzare [procedura: creare un gestore autorizzazioni personalizzato per un servizio](https://go.microsoft.com/fwlink/?LinkId=192228) per informazioni dettagliate. Ciò è dimostrato anche nell'esempio seguente: [protezione di servizi flusso di lavoro](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md).

-   L'oggetto ServiceSecurityContext per il messaggio in arrivo è disponibile anche dall'interno del flusso di lavoro tramite l'accesso a OperationContext.

## <a name="wf-security-pack-ctp"></a>WF Security Pack CTP
 Microsoft WF Security Pack CTP 1 è la prima versione di anteprima (CTP) tecnologia della community di un set di attività e relative implementazioni basato su [Windows Workflow Foundation](https://msdn.microsoft.com/netframework/aa663328.aspx)nelle [.NET Framework 4](https://msdn.microsoft.com/netframework/default.aspx) (WF 4) e il [Windows Identity Foundation (WIF)](https://msdn.microsoft.com/security/aa570351.aspx).  Microsoft WF Security Pack CTP 1 contiene sia le attività e che le finestre di progettazione che illustrano come attivare facilmente i diversi scenari relativi alla sicurezza mediante il flusso di lavoro, tra cui:

1.  Rappresentazione di un'identità client nel flusso di lavoro

2.  Autorizzazione nel flusso di lavoro, come PrincipalPermission e la convalida delle attestazioni

3.  La messaggistica autenticata usando ClientCredentials specificato nel flusso di lavoro, ad esempio il nome utente/password o un token recuperato da un servizio token di sicurezza (STS)

4.  Propagazione di un token di sicurezza client a un servizio back-end (delega basata su richieste) usando ActAs di WS-Trust

Per altre informazioni e per scaricare WF Security Pack CTP, vedere: [WF Security Pack CTP](http://wf.codeplex.com/releases/view/48114)