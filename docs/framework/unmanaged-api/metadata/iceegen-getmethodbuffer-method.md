---
title: "Метод ICeeGen::GetMethodBuffer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be6b74de649a9b13092e6a5dcd2d2f80a215a16d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="cd9a3-102">Метод ICeeGen::GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="cd9a3-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="cd9a3-103">Получает буфер соответствующего размера в указанный относительный виртуальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="cd9a3-104">Этот метод является устаревшим и не должны использоваться.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cd9a3-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd9a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cd9a3-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="cd9a3-107">[in] Относительный виртуальный адрес метода, для которого необходимо вернуть буфера.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="cd9a3-108">[out] Указатель на возвращаемый буфер.</span><span class="sxs-lookup"><span data-stu-id="cd9a3-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd9a3-109">Требования</span><span class="sxs-lookup"><span data-stu-id="cd9a3-109">Requirements</span></span>  
 <span data-ttu-id="cd9a3-110">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd9a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd9a3-111">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd9a3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd9a3-112">**Библиотека:** используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd9a3-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd9a3-113">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd9a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9a3-114">См. также</span><span class="sxs-lookup"><span data-stu-id="cd9a3-114">See Also</span></span>  
 [<span data-ttu-id="cd9a3-115">ICeeGen-интерфейс</span><span class="sxs-lookup"><span data-stu-id="cd9a3-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)