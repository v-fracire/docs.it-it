---
title: Sviluppo di applicazioni di servizio Windows
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
manager: douge
ms.openlocfilehash: 2c7fb148b96d5ff9804bcb0bb7c842c475c0f117
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207096"
---
# <a name="developing-windows-service-applications"></a>Sviluppo di applicazioni di servizio Windows
Usando Microsoft Visual Studio o Microsoft [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK, è possibile creare facilmente servizi mediante la creazione di un'applicazione installata come servizio. Questo tipo di applicazione viene chiamata servizio Windows. Con le funzionalità del framework, è possibile creare servizi, installarli, avviarli, arrestarli e controllarne in altri modi il funzionamento.  
  
> [!WARNING]
>  Il modello di servizio Windows per C++ non era incluso in Visual Studio 2010. Per creare un servizio Windows, è possibile creare un servizio in codice gestito in Visual C# o Visual Basic, che può interagire con il codice C++ esistente se necessario, oppure è possibile creare un servizio Windows in C++ nativo tramite la [Creazione guidata progetto ATL](/cpp/atl/reference/atl-project-wizard).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Introduzione alle applicazioni di servizio Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 Offre una panoramica sulle applicazioni servizio Windows, sulla durata di un servizio e sulle differenze tra le applicazioni servizio e altri tipi di progetto comuni.  
  
 [Procedura dettagliata: creazione di un'applicazione di servizio Windows in Progettazione componenti](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 Offre un esempio di creazione di un servizio in Visual Basic e Visual C#.  
  
 [Architettura di programmazione delle applicazioni di servizio](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 Illustra gli elementi del linguaggio utilizzati usati programmazione dei servizi.  
  
 [Procedura: creare servizi Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 Descrive il processo di creazione e configurazione dei servizi Windows usando il modello di progetto per servizi Windows.  
  
## <a name="related-sections"></a>Sezioni correlate  
 <xref:System.ServiceProcess.ServiceBase>  
 Descrive le funzionalità principali della classe <xref:System.ServiceProcess.ServiceBase> usata per creare servizi.  
  
 <xref:System.ServiceProcess.ServiceProcessInstaller>  
 Descrive le funzionalità della classe <xref:System.ServiceProcess.ServiceProcessInstaller> usata insieme alla classe <xref:System.ServiceProcess.ServiceInstaller> per installare e disinstallare servizi.  
  
 <xref:System.ServiceProcess.ServiceInstaller>  
 Descrive le funzionalità della classe <xref:System.ServiceProcess.ServiceInstaller> usata insieme alla classe <xref:System.ServiceProcess.ServiceProcessInstaller> per installare e disinstallare un servizio.  
  
 [NIB Creazione di progetti da modelli](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2)  
 Descrive i tipi di progetto usati in questo capitolo e come scegliere tra i vari tipi.
