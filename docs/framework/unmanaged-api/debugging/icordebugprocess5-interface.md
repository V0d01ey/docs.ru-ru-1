---
title: Интерфейс ICorDebugProcess5
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3aed85e989313e4778e12a6f6bb789ccef49747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5-interface"></a>Интерфейс ICorDebugProcess5
Чтобы определить, является ли отладчику загружать образы из приложения локального кэша машинных образов и расширяет их возможности ICorDebugProcess-интерфейс для поддержки доступа к управляемой куче, для предоставления сведений о сборке мусора управляемых объектов.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание|  
|------------|-----------------|  
|[Метод EnableNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|Задает значение, определяющее, каким образом приложение загружает образы в машинном коде во время выполнения в отладчике управляемого кода.|  
|[Метод EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|Возвращает перечислитель для всех объектов, которые должны быть мусора в процессе.|  
|[Метод EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|Возвращает перечислитель для маркеров объектов в процессе.|  
|[Метод EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|Возвращает перечислитель для объектов в управляемой куче.|  
|[Метод EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|Получает перечислитель для областей управляемой кучи.|  
|[Метод GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|Получает сведения о структуре массива в памяти.|  
|[Метод GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|Возвращает указатель на [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) структуру, содержащую сведения об объектах, которые должны быть мусора в управляемой куче.|  
|[Метод GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|Возвращает указатель на объект в управляемой куче.|  
|[Метод GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|Возвращает указатель на массив, содержащий сведения о полях для типа, на основе его идентификатора типа.|  
|[Метод GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|Возвращает тип объекта, который предоставляет сведения об объекте на основе ее типа идентификаторов.|  
|[Метод GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|Возвращает идентификатор типа для объекта по заданному адресу.|  
|[Метод GetTypeLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|Возвращает сведения о расположении объекта в памяти в зависимости от его типа идентификатора.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс логически расширяет интерфейс ICorDebugProcess ICorDebugProcess2, и [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) интерфейсов.  
  
> [!NOTE]
>  Этот интерфейс не поддерживает удаленные вызовы с другого компьютера или из другого процесса.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы отладки](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Отладка](../../../../docs/framework/unmanaged-api/debugging/index.md)
