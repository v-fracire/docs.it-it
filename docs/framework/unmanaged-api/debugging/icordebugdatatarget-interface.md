---
title: Interfaccia ICorDebugDataTarget
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 972c650e0fb3b42e943838b72faf2658f65543ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412903"
---
# <a name="icordebugdatatarget-interface"></a>Interfaccia ICorDebugDataTarget
Fornisce un'interfaccia di callback che consente di accedere a un determinato processo di destinazione.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Vengono fornite informazioni sulla piattaforma, tra cui architettura del processore e il sistema operativo, in cui viene eseguito il processo di destinazione.|  
|[Metodo ReadVirtual](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Ottiene un blocco di memoria contigua a partire dall'indirizzo specificato e lo restituisce nel buffer fornito.|  
|[Metodo GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Le richieste nel contesto del thread corrente per il thread specificato.|  
  
## <a name="remarks"></a>Note  
 `ICorDebugDataTarget` e i relativi metodi presentano le caratteristiche seguenti:  
  
-   I servizi di debug chiamare metodi su questa interfaccia per accedere a memoria e altri dati nel processo di destinazione.  
  
-   Il client del debugger deve implementare questa interfaccia in modo appropriato per la particolare destinazione (ad esempio, un processo reale o un'immagine della memoria).  
  
-   Il `ICorDebugDataTarget` metodi possono essere richiamati solo dai metodi implementati in altro `ICorDebug*` interfacce. In questo modo si garantisce che il client del debugger dispone di controllo su quale thread viene richiamato in e quando.  
  
-   Il `ICorDebugDataTarget` implementazione deve restituire sempre le informazioni aggiornate sulla destinazione.  
  
 Il processo di destinazione deve essere arrestato e non è stato modificato in alcun modo durante `ICorDebug*` interfacce (e pertanto `ICorDebugDataTarget` metodi) vengono chiamati. Se la destinazione è un processo reale e il relativo stato cambia, il [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metodo deve essere chiamato di nuovo per fornire un'istanza di ICorDebugProcess sostitutiva.  
  
> [!NOTE]
>  Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Cordebug. idl, Cordebug. H  
  
 **Libreria:** CorGuids. lib  
  
 **Versioni di .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di debug](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debug](../../../../docs/framework/unmanaged-api/debugging/index.md)
