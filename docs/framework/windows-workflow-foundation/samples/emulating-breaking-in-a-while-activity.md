---
title: Emulazione di interruzione in un'attività While
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 4938e07364609520f6528688877bce112be26d3f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253299"
---
# <a name="emulating-breaking-in-a-while-activity"></a>Emulazione di interruzione in un'attività While
In questo esempio viene illustrato come interrompere il meccanismo di ciclo delle attività seguenti: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While> e <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 Ciò è utile perché Windows Workflow Foundation (WF) non include alcuna attività per interrompere l'esecuzione di questi cicli.  
  
## <a name="scenario"></a>Scenario  
 Nell'esempio viene rilevato il primo fornitore affidabile in un elenco di fornitori (istanze della classe `Vendor`). Ogni fornitore dispone di un oggetto `ID`, di un oggetto `Name` e di un valore di affidabilità numerico che determina l'affidabilità del fornitore. Nell'esempio viene creata un'attività personalizzata denominata `FindReliableVendor` che riceve due parametri di input (un elenco di fornitori e un valore di affidabilità minimo) e restituisce il primo fornitore dell'elenco che corrisponde ai criteri forniti.  
  
## <a name="breaking-a-loop"></a>Interruzione di un ciclo  
 Windows Workflow Foundation (WF) non è inclusa un'attività per interrompere un ciclo. Nell'esempio di codice viene eseguita l'interruzione di un ciclo tramite un'attività <xref:System.Activities.Statements.If> e diverse variabili. Nell'esempio, l'attività <xref:System.Activities.Statements.While> viene interrotta dopo che alla variabile `reliableVendor` viene assegnato un valore diverso da `null`.  
  
 Nell'esempio di codice seguente viene illustrato il modo in cui l'esempio interrompe un ciclo while.  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>Per usare questo esempio  
  
1.  In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] aprire il file della soluzione EmulatingBreakInWhile.sln.  
  
2.  Per compilare la soluzione, premere CTRL+MAIUSC+B.  
  
3.  Per eseguire la soluzione, premere CTRL+F5.  
  
> [!IMPORTANT]
>  È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se questa directory non esiste, andare al [Windows Communication Foundation (WCF) e gli esempi di Windows Workflow Foundation (WF) per .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) per scaricare tutti i Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] esempi. Questo esempio si trova nella directory seguente.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`