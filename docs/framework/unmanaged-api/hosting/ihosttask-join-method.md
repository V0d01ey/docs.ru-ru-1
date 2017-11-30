---
title: "Метод IHostTask::Join"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Join
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5dbfcfc87a520925f36e09d4f2d21dbffadfe1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="08e9a-102">Метод IHostTask::Join</span><span class="sxs-lookup"><span data-stu-id="08e9a-102">IHostTask::Join Method</span></span>
<span data-ttu-id="08e9a-103">Блокирует вызывающий задачу до выполнения задачи, представленный текущим [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) завершения экземпляра, истечения заданного интервала, или [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) вызывается.</span><span class="sxs-lookup"><span data-stu-id="08e9a-103">Blocks the calling task until the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e9a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08e9a-104">Syntax</span></span>  
  
```  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08e9a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="08e9a-105">Parameters</span></span>  
 `milliseconds`  
 <span data-ttu-id="08e9a-106">[in] Интервал времени в миллисекундах для ожидания завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="08e9a-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="08e9a-107">Если это время истекает до завершения задачи, задача вызова разблокируется.</span><span class="sxs-lookup"><span data-stu-id="08e9a-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="08e9a-108">[in] Один из [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) значения.</span><span class="sxs-lookup"><span data-stu-id="08e9a-108">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values.</span></span> <span data-ttu-id="08e9a-109">Значение WAIT_ALERTABLE указывает узлу задачи, если в `Alert` вызывается перед `milliseconds` истекает.</span><span class="sxs-lookup"><span data-stu-id="08e9a-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08e9a-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="08e9a-110">Return Value</span></span>  
  
|<span data-ttu-id="08e9a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08e9a-111">HRESULT</span></span>|<span data-ttu-id="08e9a-112">Описание</span><span class="sxs-lookup"><span data-stu-id="08e9a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08e9a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="08e9a-113">S_OK</span></span>|<span data-ttu-id="08e9a-114">`Join`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="08e9a-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="08e9a-115">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08e9a-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08e9a-116">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="08e9a-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08e9a-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08e9a-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08e9a-118">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="08e9a-118">The call timed out.</span></span>|  
|<span data-ttu-id="08e9a-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08e9a-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08e9a-120">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="08e9a-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08e9a-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08e9a-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08e9a-122">Событие было отменено при заблокированных потоков или волокон ожидал либо текущий `IHostTask` экземпляра не связан с задачей.</span><span class="sxs-lookup"><span data-stu-id="08e9a-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="08e9a-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08e9a-123">E_FAIL</span></span>|<span data-ttu-id="08e9a-124">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="08e9a-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08e9a-125">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="08e9a-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08e9a-126">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="08e9a-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08e9a-127">Требования</span><span class="sxs-lookup"><span data-stu-id="08e9a-127">Requirements</span></span>  
 <span data-ttu-id="08e9a-128">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08e9a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08e9a-129">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08e9a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08e9a-130">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08e9a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08e9a-131">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08e9a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e9a-132">См. также</span><span class="sxs-lookup"><span data-stu-id="08e9a-132">See Also</span></span>  
 [<span data-ttu-id="08e9a-133">ICLRTask-интерфейс</span><span class="sxs-lookup"><span data-stu-id="08e9a-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="08e9a-134">ICLRTaskManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="08e9a-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="08e9a-135">IHostTask-интерфейс</span><span class="sxs-lookup"><span data-stu-id="08e9a-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="08e9a-136">IHostTaskManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="08e9a-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="08e9a-137">Wait_option-перечисление</span><span class="sxs-lookup"><span data-stu-id="08e9a-137">WAIT_OPTION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)