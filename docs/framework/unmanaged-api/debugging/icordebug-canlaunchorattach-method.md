---
title: Метод ICorDebug::CanLaunchOrAttach
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f86cc83936dd8150ca6b3f28c9b6a624278e2b36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcanlaunchorattach-method"></a>Метод ICorDebug::CanLaunchOrAttach
Возвращает значение HRESULT, указывающее, возможна ли запуск нового процесса или вложение указанным существующий процесс в контексте текущей конфигурации компьютера и среды выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwProcessId`  
 [in] Идентификатор существующего процесса.  
  
 `win32DebuggingEnabled`  
 [in] Передайте `true` Если планируется запускать с включенной отладкой Win32 или присоединение с отладкой Win32; в противном случае, передайте `false`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если службы отладки определения того, что запуск нового процесса или вложение в данный процесс можно, информацию о текущей конфигурации компьютера и среды выполнения. Приведены возможные значения HRESULT.  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Примечания  
 Этот метод носит исключительно информационный характер. Интерфейс не будет останавливать можно запускать или присоединение к процессу, независимо от значения, возвращенные `CanLaunchOrAttach`.  
  
 Если вы планируете запускать с включенной отладкой Win32 или присоединить с включенной отладкой Win32, передает `true` для `win32DebuggingEnabled`. Значение HRESULT, возвращенное `CanLaunchOrAttach` могут отличаться, если этот параметр используется.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorDebug.idl, CorDebug.h  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейс ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
