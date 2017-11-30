---
title: "Метод ICorDebugEval::NewObject"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e478f057b3c319d099b0156188f3d1e23bb82e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="3ed12-102">Метод ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="3ed12-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="3ed12-103">Выделяет новый экземпляр объекта и вызывает заданный метод конструктора.</span><span class="sxs-lookup"><span data-stu-id="3ed12-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="3ed12-104">Этот метод является устаревшим в .NET Framework версии 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ed12-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3ed12-105">Используйте [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) вместо него.</span><span class="sxs-lookup"><span data-stu-id="3ed12-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ed12-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3ed12-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ed12-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="3ed12-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="3ed12-108">[in] Вызываемый конструктор.</span><span class="sxs-lookup"><span data-stu-id="3ed12-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="3ed12-109">[in] Размер массива `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="3ed12-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="3ed12-110">[in] Массив объектов ICorDebugValue, каждый из которых представляет аргумент, передаваемый в конструктор.</span><span class="sxs-lookup"><span data-stu-id="3ed12-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ed12-111">Требования</span><span class="sxs-lookup"><span data-stu-id="3ed12-111">Requirements</span></span>  
 <span data-ttu-id="3ed12-112">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ed12-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ed12-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ed12-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ed12-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ed12-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ed12-115">**Версии платформы .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="3ed12-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed12-116">См. также</span><span class="sxs-lookup"><span data-stu-id="3ed12-116">See Also</span></span>  
 [<span data-ttu-id="3ed12-117">Метод NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="3ed12-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)