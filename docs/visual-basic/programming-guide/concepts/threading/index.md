---
title: Threading (Visual Basic)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 704bb04b-ff23-471d-ab12-3cec1c2bca59
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 840cc7df20250acb67bd09a8d39b353c772e82da
ms.contentlocale: it-it
ms.lasthandoff: 07/28/2017

---
# <a name="threading-visual-basic"></a>Threading (Visual Basic)
Il threading consente al programma Visual Basic di attivare l'elaborazione simultanea per eseguire più operazioni contemporaneamente. Ad esempio, è possibile usare il threading per monitorare l'input dell'utente, eseguire attività in background e gestire flussi di input simultanei.  
  
 I thread hanno le caratteristiche seguenti:  
  
-   Consentono al programma di eseguire elaborazioni simultanee.  
  
-   Possono essere usati facilmente grazie allo spazio dei nomi <xref:System.Threading> di .NET Framework.  
  
-   Condividono le risorse dell'applicazione. Per altre informazioni, vedere [Uso di thread e threading](https://msdn.microsoft.com/library/e1dx6b2h).  
  
 Per impostazione predefinita un programma Visual Basic ha un solo thread. È possibile tuttavia creare thread ausiliari da usare per eseguire il codice in parallelo al thread primario. Questi thread sono spesso chiamati *thread di lavoro*.  
  
 I thread di lavoro possono essere usati per eseguire attività lunghe e con tempi critici senza sovraccaricare il thread primario. Ad esempio, i thread di lavoro vengono spesso usati nelle applicazioni server per soddisfare le richieste in arrivo senza attendere il completamento della richiesta precedente. I thread di lavoro vengono usati anche per eseguire attività in background nelle applicazioni desktop, in modo tale che il thread principale, che gestisce gli elementi dell'interfaccia utente, garantisca tempi di risposta ottimali per le azioni dell'utente.  
  
 Il threading consente di risolvere i problemi legati alla velocità effettiva e alla velocità di risposta, ma può comportare problemi di condivisione delle risorse, quali deadlock e race condition. L'uso di più thread è consigliato per le attività che richiedono risorse differenti, ad esempio handle di file e connessioni di rete. L'assegnazione di più thread a un'unica risorsa potrebbe generare errori di sincronizzazione e se i thread vengono bloccati di frequente in attesa di altri thread lo scopo del multithreading risulta vanificato.  
  
 Una strategia comune consiste nell'usare i thread di lavoro per eseguire attività lunghe o con tempi critici ma che non richiedono molte delle risorse usate da altri thread. È necessario, naturalmente, che ad alcune risorse del programma accedano più thread. In questi casi, lo spazio dei nomi <xref:System.Threading> offre le classi per la sincronizzazione dei thread. Queste classi includono <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent>.  
  
 È possibile usare alcune o tutte queste classi per sincronizzare le attività di più thread, ma il supporto per il threading viene offerto in parte dal linguaggio Visual Basic. Ad esempio, l'[istruzione SyncLock](../../../../visual-basic/language-reference/statements/synclock-statement.md) offre funzionalità di sincronizzazione attraverso l'uso implicito di <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  A partire da [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], la programmazione multithreading è notevolmente semplificata con le classi <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> e <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), le nuove classi di raccolta simultanee nello spazio dei nomi <xref:System.Collections.Concurrent?displayProperty=fullName> e un nuovo modello di programmazione che si basa sul concetto di attività anziché di thread. Per altre informazioni, vedere [Programmazione parallela](https://msdn.microsoft.com/library/dd460693).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Applicazioni multithreading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)|Descrive come creare e usare i thread.|  
|[Parametri e valori restituiti per routine multithreading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Descrive come passare e restituire parametri con le applicazioni multithreading.|  
|[Procedura dettagliata: Multithreading con il componente BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Illustra come creare un'applicazione multithreading semplice.|  
|[Sincronizzazione di thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)|Descrive come controllare le interazioni dei thread.|  
|[Timer di thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)|Descrive come eseguire le routine su thread separati a intervalli fissi.|  
|[Creazione di pool di thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)|Descrive come usare un pool di thread di lavoro gestiti dal sistema.|  
|[Procedura: Usare un pool di thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Illustra l'uso sincronizzato di più thread nel pool di thread.|  
|[Threading](https://msdn.microsoft.com/library/3e8s7xdd)|Descrive come implementare il threading in .NET Framework.|
