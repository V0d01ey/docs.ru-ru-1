---
title: Функция FunctionEnter
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77de59de8fcf3797237245ce42c7f0eaa96d3d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="functionenter-function"></a>Функция FunctionEnter
Уведомляет профилировщик о передаче управления функции.  
  
> [!NOTE]
>  `FunctionEnter` Функция рекомендуется в .NET Framework версии 2.0 и ее использование повлечет за собой снижение производительности. Используйте [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) вместо этого функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `funcID`  
 [in] Идентификатор функции, в которую передается элемента управления.  
  
## <a name="remarks"></a>Примечания  
 `FunctionEnter` Функция является обратным вызовом, необходимо произвести его. В реализации должен использоваться `__declspec`(`naked`) атрибут класса хранения.  
  
 Перед вызовом этой функции ядро выполнения не сохраняет значения регистров.  
  
-   При входе необходимо сохранить все используемые регистры, включая те, в единицах измерения с плавающей запятой (FPU).  
  
-   При выходе необходимо восстановить стек путем выталкивания из всех параметров, переведенных вызывающим кодом.  
  
 Реализация `FunctionEnter` не должен блокироваться, поскольку это приведет к задержке сборки мусора. Реализация не должны предпринимать попытки сбора мусора, так как стек может находиться в состоянии понятного имени сбора мусора. При попытке сбора мусора, среда выполнения будет блокироваться до `FunctionEnter` возвращает.  
  
 Кроме того `FunctionEnter` функции не следует вызывать управляемый код или каким-либо образом вызывать управляемое распределение памяти.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** CorProf.idl  
  
 **Библиотека:** CorGuids.lib  
  
 **Версии платформы .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>См. также  
 [Функция FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [Функция FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [Функция FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [Метод SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Глобальные статические функции профилирования](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
