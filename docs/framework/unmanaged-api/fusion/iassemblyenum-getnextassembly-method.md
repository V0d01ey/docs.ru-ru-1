---
title: "Метод IAssemblyEnum::GetNextAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyEnum.GetNextAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cef1624d0432d571edfddfa772f31366e23074f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="9ec3c-102">Метод IAssemblyEnum::GetNextAssembly</span><span class="sxs-lookup"><span data-stu-id="9ec3c-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="9ec3c-103">Возвращает указатель на следующий [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) , содержащихся в данном [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) объекта.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec3c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9ec3c-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ec3c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="9ec3c-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="9ec3c-106">[in] Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9ec3c-107">`pvReserved`должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="9ec3c-108">[out] Возвращенный `IAssemblyName` указателя.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9ec3c-109">[in] Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9ec3c-110">`dwFlags`должно быть 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="9ec3c-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec3c-111">Требования</span><span class="sxs-lookup"><span data-stu-id="9ec3c-111">Requirements</span></span>  
 <span data-ttu-id="9ec3c-112">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ec3c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec3c-113">**Заголовок:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9ec3c-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9ec3c-114">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec3c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec3c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="9ec3c-115">See Also</span></span>  
 [<span data-ttu-id="9ec3c-116">IAssemblyName-интерфейс</span><span class="sxs-lookup"><span data-stu-id="9ec3c-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="9ec3c-117">IAssemblyEnum-интерфейс</span><span class="sxs-lookup"><span data-stu-id="9ec3c-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)