---
title: Перечисление AssemblyComparisonResult
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82b81ec29dece182548ead046edc7cb754fbf00e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="assemblycomparisonresult-enumeration"></a>Перечисление AssemblyComparisonResult
Указывает на эквивалентность два идентификатора сборки, что определяется [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>Участники  
  
|Имя члена|Описание|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Указывает, что все поля сборки совпали при сравнении.|  
|`ACR_EquivalentFXUnified`|Указывает, что сборки эквивалентны на основе общих языка среды выполнения (CLR) версии унификации для номеров версии сборок в платформе .NET Framework версии 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Указывает частичное совпадение сборок на основе унификации среды CLR для номеров версии сборок в платформе .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Указывает частичное совпадение сборок.|  
|`ACR_EquivalentPartialUnified`|Указывает частичное совпадение сборок на основе унификации прежних версий для номеров версии.|  
|`ACR_EquivalentPartialWeakNamed`|Указывает частичное совпадение сборок с простыми именами.|  
|`ACR_EquivalentUnified`|Указывает, что сборки эквивалентны на основе унификации CLR номеров версии прежних версий платформы .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Указывает соответствие между двумя сборками простым именем, чьи номера версии были пропущены.|  
|`ACR_NonEquivalent`|Указывает, что соответствие между двумя сборками.|  
|`ACR_NonEquivalentPartialVersion`|Указывает, что две сборки соответствуют за исключением номеров версии, которые совпадают только частично.|  
|`ACR_NonEquivalentVersion`|Указывает, что две сборки соответствуют за исключением номеров версии, которые не совпадают.|  
|`ACR_Unknown`|Указывает, что причина неравенства не известна.|  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** Fusion.h  
  
 **Библиотека:** включена как ресурс в MsCorEE.dll  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Функция CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [Перечисления Fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
