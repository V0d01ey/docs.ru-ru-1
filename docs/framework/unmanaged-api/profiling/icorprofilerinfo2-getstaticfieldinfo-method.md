---
title: Метод ICorProfilerInfo2::GetStaticFieldInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2ab0d482366b037f92a55f00dd33df8a312e84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>Метод ICorProfilerInfo2::GetStaticFieldInfo
Возвращает значение, указывающее тип статического объекта, применяемого для указанного поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
#### <a name="parameters"></a>Параметры  
 `classId`  
 [in] Идентификатор класса, в котором определен статического поля.  
  
 `fieldToken`  
 [in] Токен метаданных для статического поля.  
  
 `pFieldInfo`  
 [out] Указатель на значение [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) перечисления, указывающее, является ли указанное поле статическим, и если таким образом, тип статического объекта, относящееся к полю.  
  
## <a name="remarks"></a>Примечания  
 Эти сведения можно использовать для определения функции, которую необходимо вызвать для получения адреса статического поля.  
  
 Профилировщик кода следует выполнять проверку метаданных для статического поля гарантировать, что фактически адреса. Статические литералы (константы) существуют только в метаданных и не имеют адреса.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl, CorProf.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Интерфейс ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
