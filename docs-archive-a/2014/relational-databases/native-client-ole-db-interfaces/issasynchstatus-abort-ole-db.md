---
title: ISSAsynchStatus::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: 2a4bd312-839a-45a8-a299-fc8609be9a2a
author: rothja
ms.author: jroth
ms.openlocfilehash: 0fb352b6541240126dcd4c60521b93d57d6839f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718111"
---
# <a name="issasynchstatusabort-ole-db"></a><span data-ttu-id="4a7fa-102">ISSAsynchStatus::Abort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="4a7fa-102">ISSAsynchStatus::Abort (OLE DB)</span></span>
  <span data-ttu-id="4a7fa-103">非同期に実行されている操作を取り消します。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-103">Cancels an asynchronously executing operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a7fa-104">構文</span><span class="sxs-lookup"><span data-stu-id="4a7fa-104">Syntax</span></span>  
  
```  
  
HRESULT Abort(  
  HCHAPTER hChapter,  
  DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a7fa-105">引数</span><span class="sxs-lookup"><span data-stu-id="4a7fa-105">Arguments</span></span>  
 <span data-ttu-id="4a7fa-106">*hChapter*[in]</span><span class="sxs-lookup"><span data-stu-id="4a7fa-106">*hChapter*[in]</span></span>  
 <span data-ttu-id="4a7fa-107">操作を中止するチャプターのハンドル。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-107">The handle of the chapter for which to abort the operation.</span></span> <span data-ttu-id="4a7fa-108">呼び出されるオブジェクトが行セットオブジェクトではない場合、または操作がチャプターに適用されない場合、呼び出し元は*Hchapter*を DB_NULL_HCHAPTER に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-108">If the object being called is not a rowset object or the operation does not apply to a chapter, the caller must set *hChapter* to DB_NULL_HCHAPTER.</span></span>  
  
 <span data-ttu-id="4a7fa-109">*eOperation*[in]</span><span class="sxs-lookup"><span data-stu-id="4a7fa-109">*eOperation*[in]</span></span>  
 <span data-ttu-id="4a7fa-110">中止する操作。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-110">The operation to abort.</span></span> <span data-ttu-id="4a7fa-111">この引数には、</span><span class="sxs-lookup"><span data-stu-id="4a7fa-111">This should be the following value:</span></span>  
  
 <span data-ttu-id="4a7fa-112">DBASYNCHOP_OPEN。キャンセル要求が適用されるのは、行セットを非同期で開くか設定する場合、またはデータ ソース オブジェクトを非同期で初期化する場合です。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-112">DBASYNCHOP_OPEN-The request to cancel applies to the asynchronous opening or population of a rowset or to the asynchronous initialization of a data source object.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="4a7fa-113">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="4a7fa-113">Return Code Values</span></span>  
 <span data-ttu-id="4a7fa-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a7fa-114">S_OK</span></span>  
 <span data-ttu-id="4a7fa-115">非同期操作を取り消す要求が処理されました。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-115">The request to cancel the asynchronous operation was processed.</span></span> <span data-ttu-id="4a7fa-116">ただし、その操作自体が取り消されることが保証されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-116">This does not guarantee that the operation itself was canceled.</span></span> <span data-ttu-id="4a7fa-117">実際に操作が取り消されたかどうかを判断するには、コンシューマーで [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) を呼び出し、DB_E_CANCELED が返されるかどうかを調べる必要があります。ただし、要求直後に呼び出しても、この値が返されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-117">To determine whether the operation was canceled, the consumer should call [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) and check for DB_E_CANCELED; however, it might not be returned in the very next call.</span></span>  
  
 <span data-ttu-id="4a7fa-118">DB_E_CANTCANCEL</span><span class="sxs-lookup"><span data-stu-id="4a7fa-118">DB_E_CANTCANCEL</span></span>  
 <span data-ttu-id="4a7fa-119">非同期操作をキャンセルできません。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-119">The asynchronous operation cannot be canceled.</span></span>  
  
 <span data-ttu-id="4a7fa-120">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="4a7fa-120">DB_E_CANCELED</span></span>  
 <span data-ttu-id="4a7fa-121">非同期操作を中止する要求は、通知中に取り消されました。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-121">The request to abort the asynchronous operation was canceled during notifications.</span></span> <span data-ttu-id="4a7fa-122">操作は引き続き非同期に実行されます。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-122">The operation is still being executed asynchronously.</span></span>  
  
 <span data-ttu-id="4a7fa-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a7fa-123">E_FAIL</span></span>  
 <span data-ttu-id="4a7fa-124">プロバイダー固有のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-124">A provider-specific error occurred.</span></span>  
  
 <span data-ttu-id="4a7fa-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4a7fa-125">E_INVALIDARG</span></span>  
 <span data-ttu-id="4a7fa-126">*Hchapter*パラメーターが DB_NULL_HCHAPTER ないか、または*eoperation*が DBASYNCH_OPEN ではありません。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-126">The *hChapter* parameter is not DB_NULL_HCHAPTER or *eOperation* is not DBASYNCH_OPEN.</span></span>  
  
 <span data-ttu-id="4a7fa-127">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="4a7fa-127">E_UNEXPECTED</span></span>  
 <span data-ttu-id="4a7fa-128">**IDBInitialize:: Initialize**が呼び出されていないか、または完了していないデータソースオブジェクトに対して**ISSAsynchStatus:: Abort**が呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-128">**ISSAsynchStatus::Abort** was called on a data source object on which **IDBInitialize::Initialize** has not been called, or has not completed.</span></span>  
  
 <span data-ttu-id="4a7fa-129">**IDBInitialize:: Initialize**が呼び出されたが、その後初期化前にキャンセルされたか、またはタイムアウトしたデータソースオブジェクトに対して**ISSAsynchStatus:: Abort**が呼び出されました。データソースオブジェクトはまだ初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-129">**ISSAsynchStatus::Abort** was called on a data source object on which **IDBInitialize::Initialize** was called but subsequently canceled before initialization, or has timed out. The data source object is still uninitialized.</span></span>  
  
 <span data-ttu-id="4a7fa-130">**Itransaction:: commit**または**Itransaction:: Abort**が以前に呼び出された行セットで**ISSAsynchStatus:: abort**が呼び出されましたが、行セットがコミットまたは中止になっておらず、ゾンビ状態になっています。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-130">**ISSAsynchStatus::Abort** was called on a rowset on which **ITransaction::Commit** or **ITransaction::Abort** was previously called, and the rowset did not survive the commit or abort and is in a zombie state.</span></span>  
  
 <span data-ttu-id="4a7fa-131">初期化フェーズで非同期に取り消された行セットに対して **ISSAsynchStatus::Abort** が呼び出された場合も、この値が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-131">**ISSAsynchStatus::Abort** was called on a rowset that was asynchronously canceled in its initialization phase.</span></span> <span data-ttu-id="4a7fa-132">行セットはゾンビ状態になります。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-132">The rowset is in a zombie state.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a7fa-133">解説</span><span class="sxs-lookup"><span data-stu-id="4a7fa-133">Remarks</span></span>  
 <span data-ttu-id="4a7fa-134">行セットまたはデータ ソース オブジェクトの初期化を中止すると、その行セットまたはデータ ソース オブジェクトはゾンビ状態になり、**IUnknown** メソッド以外のすべてのメソッドから E_UNEXPECTED が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-134">Aborting the initialization of a rowset or data source object might leave the rowset or data source object in a zombie state, such that all methods other than **IUnknown** methods return E_UNEXPECTED.</span></span> <span data-ttu-id="4a7fa-135">この状態になると、コンシューマーはその行セットまたはデータ ソース オブジェクトの解放しか実行できません。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-135">When this happens, the only possible action for the consumer is to release the rowset or data source object.</span></span>  
  
 <span data-ttu-id="4a7fa-136">*eOperation* に DBASYNCHOP_OPEN 以外の値を渡して **ISSAsynchStatus::Abort** を呼び出すと、S_OK が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-136">Calling **ISSAsynchStatus::Abort** and passing a value for *eOperation* other than DBASYNCHOP_OPEN returns S_OK.</span></span> <span data-ttu-id="4a7fa-137">これは、操作が完了したか取り消されたことを示すわけではありません。</span><span class="sxs-lookup"><span data-stu-id="4a7fa-137">This does not imply that the operation completed or was canceled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7fa-138">参照</span><span class="sxs-lookup"><span data-stu-id="4a7fa-138">See Also</span></span>  
 [<span data-ttu-id="4a7fa-139">非同期操作の実行</span><span class="sxs-lookup"><span data-stu-id="4a7fa-139">Performing Asynchronous Operations</span></span>](../native-client/features/performing-asynchronous-operations.md)  
  
  
