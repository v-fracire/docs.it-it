---
title: "Procedura: distribuire un'applicazione di integrazione COM+"
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 872d0f0c84c1ac0ea96a87ed24a386bb9bedcf85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490139"
---
# <a name="how-to-deploy-a-com-integration-application"></a>Procedura: distribuire un'applicazione di integrazione COM+
Dopo aver scritto un'applicazione di integrazione COM+, è possibile distribuirla ad altri computer. In questo argomento viene illustrato come trasferire un'applicazione di integrazione COM+ da un computer a un altro.  
  
### <a name="moving-a-com-hosted-integration-app"></a>Trasferimento di un'applicazione di integrazione COM+ ospitata  
  
1.  Verificare che WCF sia installato su entrambi i computer.  
  
2.  Esportare l'applicazione dal computer A.  
  
3.  Importare l'applicazione nel computer B.  
  
4.  Impostare la directory principale dell'applicazione. Per convenzione, è %PROGRAMFILES%/ComPlus Applications/{AppGUID}.  
  
5.  Copiare i file Application.config e Application.manifest dalla directory principale dell'applicazione del computer A nella directory principale dell'applicazione del computer B.  
  
6.  Modificare gli indirizzi endpoint del servizio nel file Application.config nel computer B per identificare il computer appropriato. Ad esempio, modificare http://machineA/MyService a http://machineB/MyService.  
  
### <a name="moving-a-web-hosted-integration-application"></a>Trasferimento di un'applicazione di integrazione ospitata da Web  
  
1.  Verificare che WCF sia installato su entrambi i computer.  
  
2.  Esportare l'applicazione dal computer A.  
  
3.  Importare l'applicazione nel computer B.  
  
4.  Creare una radice virtuale di IIS nel computer B.  
  
5.  Copiare il file con estensione svc (componentName.svc) e il file Web.config dalla radice virtuale nel computer A nella radice virtuale appena creata nel computer B.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dell'integrazione con applicazioni COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [Procedura: Configurare le impostazioni del servizio COM+](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [Procedura: Usare lo strumento di configurazione del modello di servizi COM+](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
