---
title: Metodo ICorProfilerInfo3::GetRuntimeInformation
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67e1d20f7faf38fa37083f1a5b1cc0c1060b7a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>Metodo ICorProfilerInfo3::GetRuntimeInformation
Vengono fornite informazioni di versione di common language runtime (CLR) che si sta profilando.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pClrInstanceId`  
 [out] ID rappresentativo di un'istanza CLR in esecuzione in un processo. Questo è lo stesso come il `ClrInstanceID` che segnala la traccia eventi per l'evento di avvio di Windows (ETW).  
  
 `pRuntimeType`  
 [out] Il tipo di runtime. Questo parametro restituisce `COR_PRF_DESKTOP_CLR` per la versione desktop di CLR, o `COR_PRF_CORE_CLR` per la versione principale di CLR utilizzata in Silverlight.  
  
 `pMajorVersion`  
 [out] Il numero di versione principale di CLR.  
  
 `pMinorVersion`  
 [out] Il numero di versione secondaria di CLR.  
  
 `pBuildVersion`  
 [out] Il numero di versione di build di Common Language Runtime.  
  
 `pQFEVersion`  
 [out] Il numero di versione di CLR associato a un aggiornamento software.  
  
 `cchVersionString`  
 [in] Lunghezza, espressa in caratteri, del buffer che `szVersionString` punta a.  
  
 `pcchVersionString`  
 [out] Lunghezza, espressa in caratteri, di `szVersionString`.  
  
 `szVersionString`  
 [out] La stringa di versione CLR.  
  
## <a name="remarks"></a>Note  
 È possibile passare null per qualsiasi parametro. Tuttavia, `pcchVersionString` non può essere null a meno che non `szVersionString` è null.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorProf.idl, CorProf.h  
  
 **Libreria:** CorGuids. lib  
  
 **Versioni di .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfacce di profilatura](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilatura](../../../../docs/framework/unmanaged-api/profiling/index.md)
