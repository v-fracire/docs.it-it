---
title: Enumerazione CorErrorIfEmitOutOfOrder
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4e9d03dcf4603f9470f8f2509050eb6f875746a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442640"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>Enumerazione CorErrorIfEmitOutOfOrder
Contiene valori di flag che indicano in quali condizioni è necessario generare un messaggio di errore per notificare che i metadati sono stati emessi senza ordine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|Indica il comportamento predefinito, che non genera messaggi di errore.|  
|`MDErrorOutOfOrderNone`|Indica che il compilatore non deve generare messaggi di errore.|  
|`MDErrorOutOfOrderAll`|Indica che il compilatore deve generare un messaggio di errore quando un campo, proprietà, evento, un metodo, o parametro è emesso senza ordine.|  
|`MDMethodOutOfOrder`|Indica che il compilatore deve generare un messaggio di errore quando un metodo è emesso senza ordine.|  
|`MDFieldOutOfOrder`|Indica che il compilatore deve generare un messaggio di errore quando un campo è emesso senza ordine.|  
|`MDParamOutOfOrder`|Indica che il compilatore deve generare un messaggio di errore quando un parametro è emesso senza ordine.|  
|`MDPropertyOutOfOrder`|Indica che il compilatore deve generare un messaggio di errore quando una proprietà è emesso senza ordine.|  
|`MDEventOutOfOrder`|Indica che il compilatore deve generare un messaggio di errore quando un evento è emesso senza ordine.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorHdr. H  
  
 **Versioni di .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni dei metadati](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
