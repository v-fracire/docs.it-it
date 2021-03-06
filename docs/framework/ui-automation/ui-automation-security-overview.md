---
title: Cenni preliminari sulla sicurezza di automazione interfaccia utente
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b35014993f10c3a60c16f784e7dd11b9a20f4f4c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400595"
---
# <a name="ui-automation-security-overview"></a>Cenni preliminari sulla sicurezza di automazione interfaccia utente
> [!NOTE]
>  Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>. Per informazioni aggiornate sulle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vedere [Windows Automation API: automazione dell'interfaccia utente](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Questa panoramica descrive il modello di sicurezza per [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] in [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a>Controllo dell'account utente  
 La sicurezza è un obiettivo fondamentale di [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] e una delle novità è la possibilità per gli utenti di operare come utenti standard (non amministratori) senza che venga bloccata l'esecuzione di applicazioni e servizi che richiedono privilegi più elevati.  
  
 In [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], la maggior parte delle applicazioni viene fornita con un token standard o amministrativo. Per impostazione predefinita, se un'applicazione non può essere identificata come applicazione amministrativa, viene avviata come applicazione standard. Prima che un'applicazione identificata come amministrativa possa essere avviata, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] chiede all'utente il consenso per eseguire l'applicazione come utente con privilegi elevati. La richiesta di consenso viene visualizzata per impostazione predefinita, anche se l'utente è membro del gruppo Administrators locale, perché gli amministratori operano come utenti standard finché un'applicazione o un componente di sistema, per cui sono necessarie credenziali amministrative, non richiede l'autorizzazione per l'esecuzione.  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a>Attività che richiedono privilegi più elevati  
 Quando un utente tenta di eseguire un'attività che richiede privilegi amministrativi, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] visualizza una finestra di dialogo che chiede all'utente il consenso per continuare. Questa finestra di dialogo è protetta dalla comunicazione tra processi, in modo che un software dannoso non possa simulare l'input utente. Analogamente, la schermata di accesso al desktop in genere non è accessibile ad altri processi.  
  
 I client di automazione interfaccia utente devono comunicare con altri processi, alcuni dei quali potrebbero essere in esecuzione con un livello di privilegi più elevato. I client potrebbero anche aver bisogno di accedere alle finestre di dialogo di sistema che non sono in genere visibili ad altri processi. Di conseguenza, i client di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] devono essere considerati attendibili dal sistema e devono essere eseguiti con privilegi speciali.  
  
 Per essere considerate attendibili e comunicare con applicazioni in esecuzione con un livello di privilegi più elevato, le applicazioni devono essere firmate.  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a>File manifesto  
 Per accedere all' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]di  sistema protetta, le applicazioni devono essere compilate con un file manifesto che include un attributo speciale. Questo attributo `uiAccess` è incluso nel tag `requestedExecutionLevel` , come indicato di seguito:  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 Il valore dell'attributo `level` in questo codice è solo un esempio.  
  
 `UIAccess` è "false" per impostazione predefinita, ovvero, se l'attributo viene omesso o se non esiste alcun manifesto per l'assembly, l'applicazione non sarà in grado di accedere all' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]protetta.  
  
 Per ulteriori informazioni sul [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] sicurezza, sulla firma delle applicazioni e sulla creazione di manifesti dell'assembly, vedere "Per gli sviluppatori migliori procedure consigliate e linee guida per le applicazioni in un con privilegi ambiente minimi" su [MSDN](https://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).
