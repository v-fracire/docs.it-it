---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 7e7bd48d206456af6a5a8662516c4d9c82b3ed2f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196902"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Impossibile spostare o eliminare il messaggio.  
  
## <a name="description"></a>Descrizione  
 La traccia indica che si è verificato un errore durante il tentativo di spostare, eliminare o rifiutare un messaggio MSMQ.  
  
 I messaggi MSMQ vengono usati da Windows Communication Foundation (WCF) (se utilizzato con NetMsmqBinding o MsmqIntegrationBinding). Questa traccia è correlata al valore scelto del `ReceiveErrorHandling` proprietà su NetMsmqBinding o MsmqIntegrationBinding.  
  
 Questa traccia non è indicativa di un errore di sistema complessivo. Tuttavia, indica che l'eliminazione del messaggio non elaborabile scelta ha avuto esito negativo per un messaggio. Visualizzare [dei messaggi non elaborabili](https://go.microsoft.com/fwlink/?LinkID=99546) per altri dettagli su cui i messaggi diventano non elaborabili e su come configurare il servizio per gestirli in modo appropriato.  
  
## <a name="see-also"></a>Vedere anche  
 [Traccia](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uso delle tracce per risolvere i problemi di un'applicazione](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Amministrazione e diagnostica](../../../../../docs/framework/wcf/diagnostics/index.md)
