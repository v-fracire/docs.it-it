---
title: socket
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ce7ded81ad23c2df55afa9360435e8391fea7a63
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176825"
---
# <a name="sockets"></a>socket
Lo spazio dei nomi <xref:System.Net.Sockets> contiene un'implementazione gestita dell'interfaccia Windows Sockets. Tutte le altre classi di accesso alla rete nello spazio dei nomi <xref:System.Net> si basano su questa implementazione dei socket.  
  
 La classe <xref:System.Net.Sockets.Socket> .NET Framework è una versione per codice gestito dei servizi socket forniti dall'API di Winsock32. Nella maggior parte dei casi, i metodi della classe **Socket** eseguono semplicemente il marshalling dei dati nelle rispettive controparti Win32 native e gestiscono gli eventuali controlli di sicurezza necessari.  
  
 La classe **Socket** supporta due modalità di base, sincrona e asincrona. In modalità sincrona, le chiamate a funzioni che eseguono operazioni di rete (ad esempio <xref:System.Net.Sockets.Socket.Send%2A> e <xref:System.Net.Sockets.Socket.Receive%2A>) attendono il completamento dell'operazione prima di restituire il controllo al programma chiamante. In modalità asincrona, queste chiamate restituiscono il controllo immediatamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare un socket](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Uso di protocolli applicativi](../../../docs/framework/network-programming/using-application-protocols.md)
