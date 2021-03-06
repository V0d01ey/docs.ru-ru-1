---
title: ICorDebugFunction интерфейс1
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 344acf109d58d0ed2fbc8a91da0761b4dd148a27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunction-interface1"></a>ICorDebugFunction интерфейс1
Представляет управляемую функцию или метод.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод CreateBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Создает точку останова в начале этой функции.|  
|[Метод GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Возвращает объект ICorDebugClass, представляющий класс, членом которых является эта функция.|  
|[Метод GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Получает номер версии последней правки этой функции.|  
|[Метод GetILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Возвращает код на промежуточном языке (MSIL) для этой функции.|  
|[Метод GetLocalVarSigToken](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Получает маркер метаданных для подписи локальной переменной функции, представленный этим `ICorDebugFunction` экземпляра.|  
|[Метод GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Возвращает модуль, в котором определена эта функция.|  
|[Метод GetNativeCode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Получает машинный код для этой функции.|  
|[Метод GetToken](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Получает маркер метаданных для этой функции.|  
  
## <a name="remarks"></a>Примечания  
 `ICorDebugFunction` Интерфейса не представляет функцию с параметрами универсального типа. Например `ICorDebugFunction` представляет экземпляр `Func<T>` , но не `Func<string>`. Вызовите [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) для получения параметров универсального типа.  
  
 Связь между токен метаданных метода, `mdMethodDef`, а также метод `ICorDebugFunction` объекта зависит от того, разрешено ли на функцию Изменить и продолжить:  
  
-   Если изменить и продолжить не разрешен в функции, между существует однозначное `ICorDebugFunction` объекта и `mdMethodDef` маркеров. То есть функция имеет один `ICorDebugFunction` объекта и один `mdMethodDef` токена.  
  
-   Если на функцию может изменить и продолжить, многие к одному связь существует между `ICorDebugFunction` объекта и `mdMethodDef` маркеров. То есть функция может иметь много экземпляров `ICorDebugFunction`, один для каждой версии функции, но только один `mdMethodDef` токена.  
  
> [!NOTE]
>  Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
