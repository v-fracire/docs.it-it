---
title: Proprietà di esecuzione
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748194"
---
# <a name="execution-properties"></a>Proprietà di esecuzione
In questo esempio viene illustrato come definire e usare una proprietà di esecuzione in un'attività personalizzata. In questo esempio la proprietà di esecuzione determina il colore di primo piano della console. Un flusso di lavoro di esempio illustra come i diversi percorsi logici di esecuzione (rami di un'attività <xref:System.Activities.Statements.Parallel> ) possono gestire diversi colori della console nonostante esecuzione interleave delle attività (attraverso i rami dell'attività <xref:System.Activities.Statements.Parallel> ).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Per impostare, compilare ed eseguire l'esempio  
  
1.  Aprire la soluzione di esempio ExecutionProperties.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    > [!NOTE]
    >  Se si visualizza ThreeColors.xaml prima di compilare la soluzione viene visualizzato un errore, perché le attività personalizzate usate devono essere compilate contemporaneamente alla soluzione.  
  
2.  Compilare ed eseguire la soluzione.  
  
> [!IMPORTANT]
>  È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se questa directory non esiste, andare al [Windows Communication Foundation (WCF) e gli esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] esempi. Questo esempio si trova nella directory seguente.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`