---
title: Interfaccia IAppIdAuthority
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 819afec2c448e5f396ab54e2dde00c01da310b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433750"
---
# <a name="iappidauthority-interface"></a>Interfaccia IAppIdAuthority
Fornisce metodi che generano e confrontare le chiavi per le identità delle applicazioni e i riferimenti.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Ottiene un valore che indica se le due [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) istanze sono uguali. È possibile passare il valore del flag IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION per ignorare le rispettive informazioni sulla versione.|  
|`IAppIdAuthority::AreReferencesEqual`|Ottiene un valore che indica se le due [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) istanze sono uguali. È possibile passare il valore del flag IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION per ignorare le rispettive informazioni sulla versione.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Ottiene un valore che indica se le due definizioni di stringa specificato sono uguali. È possibile passare il valore del flag IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION per ignorare le rispettive informazioni sulla versione.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Ottiene un valore che indica se i due riferimenti di stringa specificato sono uguali. È possibile passare il valore del flag IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION per ignorare le rispettive informazioni sulla versione.|  
|`IAppIdAuthority::CreateDefinition`|Ottiene un puntatore a interfaccia a un oggetto appena generato `IDefinitionAppId` istanza che rappresenta l'assembly nell'ambito corrente.|  
|`IAppIdAuthority::CreateReference`|Ottiene un puntatore a interfaccia a un oggetto appena creato `IReferenceAppId` che rappresenta l'assembly nell'ambito corrente.|  
|`IAppIdAuthority::DefinitionToText`|Ottiene una versione stringa dell'oggetto specificato `IDefinitionAppId`, utilizzando i valori di flag specificato.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Ottiene un valore che indica se l'oggetto specificato `IDefinitionAppId` e `IReferenceAppId` rappresentano lo stesso assembly.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Ottiene un valore che indica se la stringa di definizione specificato e una stringa di riferimento rappresentano lo stesso assembly.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Ottiene una chiave di stringa che rappresenta l'oggetto specificato `IDefinitionAppId` istanza.|  
|`IAppIdAuthority::GenerateReferenceKey`|Ottiene una chiave di stringa che rappresenta l'oggetto specificato `IReferenceAppId` istanza.|  
|`IAppIdAuthority::HashDefinition`|Ottiene una chiave hash per l'oggetto specificato `IDefinitionAppId` istanza.|  
|`IAppIdAuthority::HashReference`|Ottiene una chiave hash per l'oggetto specificato `IReferenceAppId` istanza.|  
|`IAppIdAuthority::ReferenceToText`|Ottiene una versione stringa dell'oggetto specificato `IReferenceAppId`, utilizzando i valori di flag specificato.|  
|`IAppIdAuthority::TextToDefinition`|Ottiene un puntatore a interfaccia a un `IDefinitionAppId` istanza che rappresenta l'assembly a cui fa riferimento la chiave di stringa specificata.|  
|`IAppIdAuthority::TextToReference`|Ottiene un puntatore a interfaccia a un `IReferenceAppId` istanza che rappresenta l'assembly a cui fa riferimento la chiave di stringa specificata.|  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Isolation. h  
  
 **Versioni di .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce Fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
