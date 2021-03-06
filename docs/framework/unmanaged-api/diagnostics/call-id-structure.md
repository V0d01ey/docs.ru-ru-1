---
title: Структура CALL_ID
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8d6b16f3eeb32e41f3568e0b237f18c945a8cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="callid-structure"></a>Структура CALL_ID
Сведения о функции, которая вызывается в отладчике. В разделе [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) интерфейс для получения дополнительной информации.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>Участники  
  
|Член|Описание|  
|------------|-----------------|  
|`szMachine`|Идентифицирует компьютер, который выполняет вызов.|  
|`dwPid`|Определяет процессор компьютера.|  
|`pUserThread`|Определяет поток, который выполняет вызов.|  
|`addrStackPointer`|Задает адрес стека вызовов.|  
|`szEntryPoint`|Задает адрес вызова.|  
|`szDestinationMachine`|Идентифицирует компьютер, который будет выполнять вызов.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>См. также  
 [Интерфейс INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [Структуры хранилища символов диагностики](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
