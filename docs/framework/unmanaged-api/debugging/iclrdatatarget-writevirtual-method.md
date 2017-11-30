---
title: "Метод ICLRDataTarget::WriteVirtual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.WriteVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ffce593824599e9f8f41c38966b69a9076924608
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="8a7e2-102">Метод ICLRDataTarget::WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="8a7e2-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="8a7e2-103">Записывает данные из указанного буфера указанного адреса виртуальной памяти.</span><span class="sxs-lookup"><span data-stu-id="8a7e2-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a7e2-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a7e2-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a7e2-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="8a7e2-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="8a7e2-106">[in] CLRDATA_ADDRESS, в которой хранятся адресов виртуальной памяти.</span><span class="sxs-lookup"><span data-stu-id="8a7e2-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8a7e2-107">[in] Указатель на буфер, в которой хранятся данные, которые требуется записать.</span><span class="sxs-lookup"><span data-stu-id="8a7e2-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="8a7e2-108">[in] Число байтов для записи.</span><span class="sxs-lookup"><span data-stu-id="8a7e2-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="8a7e2-109">[out] Указатель на фактическое число байтов, которые были записаны.</span><span class="sxs-lookup"><span data-stu-id="8a7e2-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a7e2-110">Требования</span><span class="sxs-lookup"><span data-stu-id="8a7e2-110">Requirements</span></span>  
 <span data-ttu-id="8a7e2-111">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a7e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a7e2-112">**Заголовок:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8a7e2-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8a7e2-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a7e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a7e2-114">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a7e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a7e2-115">См. также</span><span class="sxs-lookup"><span data-stu-id="8a7e2-115">See Also</span></span>  
 [<span data-ttu-id="8a7e2-116">ICLRDataTarget-интерфейс</span><span class="sxs-lookup"><span data-stu-id="8a7e2-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)