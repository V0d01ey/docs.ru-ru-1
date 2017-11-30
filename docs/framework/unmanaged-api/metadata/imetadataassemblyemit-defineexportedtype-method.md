---
title: "Метод IMetaDataAssemblyEmit::DefineExportedType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineExportedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 245a485289335b096ee60a8eb3696a087e6871e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="60265-102">Метод IMetaDataAssemblyEmit::DefineExportedType</span><span class="sxs-lookup"><span data-stu-id="60265-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="60265-103">Создает структуру `ExportedType`, содержащую метаданные для указанного экспортированного типа, и возвращает связанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="60265-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60265-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60265-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60265-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="60265-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="60265-106">[in] Имя типа должны быть экспортированы.</span><span class="sxs-lookup"><span data-stu-id="60265-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="60265-107">Версии 1.1 среды common language runtime имя экспортируемого типа должно точно соответствовать имени в `TypeDef` для типа.</span><span class="sxs-lookup"><span data-stu-id="60265-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="60265-108">[in] Токен, указав, где реализуется экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="60265-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="60265-109">Ниже приведены допустимые значения и их связанные значения.</span><span class="sxs-lookup"><span data-stu-id="60265-109">The valid values and their associated meanings are:</span></span>  
  
-   <span data-ttu-id="60265-110">`mdFile`Тип реализуется в другой файл в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="60265-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
-   <span data-ttu-id="60265-111">`mdAssemblyRef`Тип реализуется в другой сборке.</span><span class="sxs-lookup"><span data-stu-id="60265-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
-   <span data-ttu-id="60265-112">`mdExportedTYpe`Тип, вложенный в другой тип.</span><span class="sxs-lookup"><span data-stu-id="60265-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
-   <span data-ttu-id="60265-113">`mdFileNil`Тип находится в тот же файл манифеста и не является вложенным типом.</span><span class="sxs-lookup"><span data-stu-id="60265-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="60265-114">[in] Токен метаданных, указывающий тип для экспорта.</span><span class="sxs-lookup"><span data-stu-id="60265-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="60265-115">Это значение, введенное в `TypeDef` таблице в файле, который реализует тип элемента и используется только в том случае, если этот файл находится в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="60265-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="60265-116">[in] Побитовое сочетание [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) значений перечисления, определяющих параметры свойств для экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="60265-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="60265-117">[out] Указатель на токен возвращенные метаданные, указывающее экспортируемого типа.</span><span class="sxs-lookup"><span data-stu-id="60265-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60265-118">Примечания</span><span class="sxs-lookup"><span data-stu-id="60265-118">Remarks</span></span>  
 <span data-ttu-id="60265-119">`ExportedType` Структуру метаданных должны быть определены для каждого типа, представленного этой сборке и реализуемую в модуле, отличном от того, содержащем манифест.</span><span class="sxs-lookup"><span data-stu-id="60265-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60265-120">Требования</span><span class="sxs-lookup"><span data-stu-id="60265-120">Requirements</span></span>  
 <span data-ttu-id="60265-121">**Платформа:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60265-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60265-122">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="60265-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60265-123">**Библиотека:** используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60265-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60265-124">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60265-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60265-125">См. также</span><span class="sxs-lookup"><span data-stu-id="60265-125">See Also</span></span>  
 [<span data-ttu-id="60265-126">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="60265-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)