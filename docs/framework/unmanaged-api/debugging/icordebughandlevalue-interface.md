---
title: "ICorDebugHandleValue 接口 1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue
helpviewer_keywords: ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b56c23caaaed2bc63c724769db1198fd088f7f1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="c5992-102">ICorDebugHandleValue 接口 1</span><span class="sxs-lookup"><span data-stu-id="c5992-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="c5992-103">表示调试器已为其创建了垃圾回收句柄的引用值的 ICorDebugReferenceValue 子类。</span><span class="sxs-lookup"><span data-stu-id="c5992-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5992-104">方法</span><span class="sxs-lookup"><span data-stu-id="c5992-104">Methods</span></span>  
  
|<span data-ttu-id="c5992-105">方法</span><span class="sxs-lookup"><span data-stu-id="c5992-105">Method</span></span>|<span data-ttu-id="c5992-106">描述</span><span class="sxs-lookup"><span data-stu-id="c5992-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5992-107">Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="c5992-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="c5992-108">释放此引用的句柄`ICorDebugHandleValue`而不显式释放的接口指针的对象。</span><span class="sxs-lookup"><span data-stu-id="c5992-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="c5992-109">GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="c5992-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="c5992-110">获取描述的句柄引用的一个 CorDebugHandleType 值`ICorDebugHandleValue`。</span><span class="sxs-lookup"><span data-stu-id="c5992-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5992-111">备注</span><span class="sxs-lookup"><span data-stu-id="c5992-111">Remarks</span></span>  
 <span data-ttu-id="c5992-112">`ICorDebugReferenceValue`对象失效的调试代码的执行中出现中断。</span><span class="sxs-lookup"><span data-stu-id="c5992-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="c5992-113">`ICorDebugHandleValue`显式释放前保持在中断和延续，其引用。</span><span class="sxs-lookup"><span data-stu-id="c5992-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5992-114">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="c5992-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5992-115">要求</span><span class="sxs-lookup"><span data-stu-id="c5992-115">Requirements</span></span>  
 <span data-ttu-id="c5992-116">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5992-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5992-117">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5992-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5992-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5992-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5992-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5992-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5992-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c5992-120">See Also</span></span>  
 [<span data-ttu-id="c5992-121">调试接口</span><span class="sxs-lookup"><span data-stu-id="c5992-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)