---
title: "Метод ICorDebugEval2::NewStringWithLength"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewStringWithLength
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b794482e491dc9825b0311cf1731d159082bd1f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="81bdc-102">Метод ICorDebugEval2::NewStringWithLength</span><span class="sxs-lookup"><span data-stu-id="81bdc-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="81bdc-103">Создает строку указанной длины с указанным содержимым.</span><span class="sxs-lookup"><span data-stu-id="81bdc-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81bdc-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="81bdc-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81bdc-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="81bdc-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="81bdc-106">[in] Указатель на строковое значение.</span><span class="sxs-lookup"><span data-stu-id="81bdc-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="81bdc-107">[in] Длина строки.</span><span class="sxs-lookup"><span data-stu-id="81bdc-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81bdc-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="81bdc-108">Remarks</span></span>  
 <span data-ttu-id="81bdc-109">Если строка замыкающие символ null должно быть в строке управляемый код, вызывающий `NewStringWithLength` метода необходимо убедиться, что длина строки включает конечный символ null.</span><span class="sxs-lookup"><span data-stu-id="81bdc-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="81bdc-110">Строка всегда создается в домене приложения, в котором в настоящее время выполняется поток.</span><span class="sxs-lookup"><span data-stu-id="81bdc-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81bdc-111">Требования</span><span class="sxs-lookup"><span data-stu-id="81bdc-111">Requirements</span></span>  
 <span data-ttu-id="81bdc-112">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81bdc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81bdc-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81bdc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81bdc-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81bdc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81bdc-115">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81bdc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>