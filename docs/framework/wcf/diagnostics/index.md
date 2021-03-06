---
title: Amministrazione e diagnostica
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
ms.openlocfilehash: c69d5681b186fdfae168ceea8b35f5786eaf02c9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810005"
---
# <a name="administration-and-diagnostics"></a>Amministrazione e diagnostica
Windows Communication Foundation (WCF) fornisce un vasta gamma di funzionalità che consentono di monitorare le varie fasi del ciclo di vita dell'applicazione. È ad esempio possibile utilizzare la configurazione per impostare servizi e client in fase di distribuzione. WCF include un vasto set di contatori delle prestazioni che consentono di misurare le prestazioni dell'applicazione. WCF espone inoltre dati di ispezione di un servizio in fase di esecuzione tramite un provider di Strumentazione gestione Windows (WMI) di WCF. In caso di errore dell'applicazione o di comportamento non corretto, è possibile utilizzare il Registro eventi per controllare se si è verificato qualcosa di grave. È inoltre possibile utilizzare la registrazione messaggi e le tracce per controllare gli eventi end-to-end in corso nell'applicazione. Queste funzionalità aiutano sia gli sviluppatori e professionisti IT a risolvere i problemi di un'applicazione WCF quando non funziona correttamente.  
  
> [!NOTE]
>  Se si ricevono errori senza informazioni di dettaglio specifico, è necessario abilitare il `includeExceptionDetailInFaults` attributo del [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) elemento di configurazione. Ciò indica a WCF per inviare i dettagli dell'eccezione ai client, che consente di rilevare i problemi più comuni senza richiedere diagnosi più avanzate. Per ulteriori informazioni, vedere [invio e ricezione di errori](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Funzionalità di diagnostica fornite da WCF  
 WCF fornisce la funzionalità di diagnostica seguenti:  
  
-   Le tracce end-to-end forniscono dati di strumentazione per risolvere i problemi di un'applicazione senza utilizzare un debugger. WCF genera tracce per attività cardine di processo, nonché i messaggi di errore. Tale processo può comprendere l'apertura di una channel factory o l'invio e ricezione di messaggi tramite un host del servizio. È possibile attivare la traccia per monitorare lo stato di avanzamento di un'applicazione in esecuzione. Per altre informazioni, vedere la [traccia](../../../../docs/framework/wcf/diagnostics/tracing/index.md) argomento. Per comprendere come è possibile utilizzare la traccia per il debug dell'applicazione, vedere il [utilizzando opzioni di traccia per risolvere i problemi dell'applicazione](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) argomento.  
  
-   La registrazione dei messaggi consente di vedere il loro aspetto prima e dopo la trasmissione. Per altre informazioni, vedere la [registrazione messaggi](../../../../docs/framework/wcf/diagnostics/message-logging.md) argomento.  
  
-   La traccia eventi scrive gli eventi nel Registro eventi per qualsiasi problema importante. È quindi possibile utilizzare il Visualizzatore eventi per esaminare eventuali anomalie. Per altre informazioni, vedere la [la registrazione degli eventi](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) argomento.  
  
-   I contatori delle prestazioni esposti tramite Performance Monitor consentono di monitorare lo stato d'integrità dell'applicazione e del sistema. Per altre informazioni, vedere la [contatori delle prestazioni](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) argomento.  
  
-   Lo spazio dei nomi <xref:System.ServiceModel.Configuration> consente di caricare file di configurazione e configurare un endpoint del servizio o client. È possibile utilizzare il modello a oggetti per inserire in uno script le modifiche a numerose applicazioni quando è necessario distribuire gli aggiornamenti a più computer. In alternativa, è possibile utilizzare il [strumento Editor di configurazione (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) per modificare le impostazioni di configurazione tramite una procedura guidata grafica. Per altre informazioni, vedere la [configurazione dell'applicazione](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) argomento.  
  
-   Con WMI è possibile scoprire quali servizi sono in attesa in un computer e le associazioni utilizzate. Per altre informazioni, vedere la [tramite Strumentazione gestione Windows per la diagnostica](../../../../docs/framework/wcf/diagnostics/wmi/index.md) argomento.  
  
 WCF fornisce numerosi strumenti di interfaccia utente grafica e riga di comando per rendere più semplice per poter creare, distribuire e gestire le applicazioni WCF. Per altre informazioni, vedere [strumenti di Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Ad esempio, è possibile utilizzare il [strumento Editor di configurazione (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) per creare e modificare le impostazioni di configurazione WCF tramite una procedura guidata, anziché modificare direttamente il codice XML. È anche possibile usare il [strumento Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) per visualizzare, raggruppare e filtrare i messaggi di traccia in modo che è possibile diagnosticare, riparare e verificare i problemi dei servizi WCF.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione dell'applicazione](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [Distribuzione di servizi](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [Riferimenti per le eccezioni](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [Registrazione eventi](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [Registrazione messaggi](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Strumento Editor di configurazione (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Strumento Visualizzatore di tracce dei servizi (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Strumento di registrazione ServiceModel](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [Traccia](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uso di Strumentazione gestione Windows per la diagnostica](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [Contatori delle prestazioni](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Strumenti Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
