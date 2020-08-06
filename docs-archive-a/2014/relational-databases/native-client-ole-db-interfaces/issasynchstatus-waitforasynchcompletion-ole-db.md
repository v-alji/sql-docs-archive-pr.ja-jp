---
title: ISSAsynchStatus::WaitForAsynchCompletion (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- WaitForAsynchCompletion method
ms.assetid: 9f65e9e7-eb93-47a1-bc42-acd4649fbd0e
author: rothja
ms.author: jroth
ms.openlocfilehash: f57211d1c62535828704dc971e345b412c284cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634497"
---
# <a name="issasynchstatuswaitforasynchcompletion-ole-db"></a><span data-ttu-id="a3710-102">ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="a3710-102">ISSAsynchStatus::WaitForAsynchCompletion (OLE DB)</span></span>
  <span data-ttu-id="a3710-103">非同期で実行している操作が完了するまで、またはタイムアウトが発生するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="a3710-103">Waits until the asynchronously executing operation is complete or until a time-out occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3710-104">構文</span><span class="sxs-lookup"><span data-stu-id="a3710-104">Syntax</span></span>  
  
```  
  
HRESULT WaitForAsynchCompletion(   
  DWORD dwMillisecTimeOut);  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3710-105">引数</span><span class="sxs-lookup"><span data-stu-id="a3710-105">Arguments</span></span>  
 <span data-ttu-id="a3710-106">*dwMillisecTimeOut*[in]</span><span class="sxs-lookup"><span data-stu-id="a3710-106">*dwMillisecTimeOut*[in]</span></span>  
 <span data-ttu-id="a3710-107">ミリ秒単位のタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="a3710-107">Time-out in milliseconds.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="a3710-108">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="a3710-108">Return Code Values</span></span>  
 <span data-ttu-id="a3710-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3710-109">S_OK</span></span>  
 <span data-ttu-id="a3710-110">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="a3710-110">The method succeeded.</span></span>  
  
 <span data-ttu-id="a3710-111">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="a3710-111">E_UNEXPECTED</span></span>  
 <span data-ttu-id="a3710-112">**Itransaction:: Commit**または**Itransaction:: Abort**が呼び出されたか、初期化フェーズ中に行セットが取り消されたため、行セットが未使用の状態になっています。</span><span class="sxs-lookup"><span data-stu-id="a3710-112">A rowset is in an unused state because **ITransaction::Commit** or **ITransaction::Abort** has been called or the rowset was cancelled during its initialization phase.</span></span>  
  
 <span data-ttu-id="a3710-113">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="a3710-113">DB_E_CANCELED</span></span>  
 <span data-ttu-id="a3710-114">行セットの設定中またはデータ ソース オブジェクトの初期化中に、非同期処理が取り消されました。</span><span class="sxs-lookup"><span data-stu-id="a3710-114">Asynchronous processing was cancelled during rowset population or data source object initialization.</span></span>  
  
 <span data-ttu-id="a3710-115">DB_S_ASYNCHRONOUS</span><span class="sxs-lookup"><span data-stu-id="a3710-115">DB_S_ASYNCHRONOUS</span></span>  
 <span data-ttu-id="a3710-116">指定したタイムアウトに達しても、操作が完了していません。</span><span class="sxs-lookup"><span data-stu-id="a3710-116">The operation has not yet completed even though specified time-out has been reached.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3710-117">**ISSAsynchStatus::WaitForAsynchCompletion** メソッドでは、上記のリターン コード値以外に、主要な OLEDB **ICommand::Execute** メソッドや **IDBInitialize::Initialize** メソッドによって返されたリターン コード値もサポートします。</span><span class="sxs-lookup"><span data-stu-id="a3710-117">In addition to the return code values listed above, the **ISSAsynchStatus::WaitForAsynchCompletion** method also supports the return code values returned by the core OLEDB **ICommand::Execute** and **IDBInitialize::Initialize** methods.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3710-118">解説</span><span class="sxs-lookup"><span data-stu-id="a3710-118">Remarks</span></span>  
 <span data-ttu-id="a3710-119">タイムアウト値 (ミリ秒) が経過するか、保留になっている操作が完了するまでは、**ISSAsynchStatus::WaitForAsynchCompletion** メソッドから制御が戻りません。</span><span class="sxs-lookup"><span data-stu-id="a3710-119">The **ISSAsynchStatus::WaitForAsynchCompletion** method will not return until the time-out value (in milliseconds) has passed or the pending operation is done.</span></span> <span data-ttu-id="a3710-120">**Command**オブジェクトには、クエリがタイムアウトするまでに実行される秒数を制御する**CommandTimeout**プロパティがあります。**ISSAsynchStatus:: WaitForAsynchCompletion**メソッドと共に使用する場合、 **CommandTimeout**プロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="a3710-120">The **Command** object has a **CommandTimeout** property that controls the number of seconds a query will run before timing out. The **CommandTimeout** property will be ignored if used in conjunction with **ISSAsynchStatus::WaitForAsynchCompletion** method.</span></span>  
  
 <span data-ttu-id="a3710-121">非同期操作では、タイムアウト プロパティが無視されます。</span><span class="sxs-lookup"><span data-stu-id="a3710-121">The time-out property is ignored for asynchronous operations.</span></span> <span data-ttu-id="a3710-122">**ISSAsynchStatus::WaitForAsynchCompletion** のタイムアウト パラメーターに、制御が呼び出し元に返されるまでに経過する最大時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3710-122">The time-out parameter of **ISSAsynchStatus::WaitForAsynchCompletion** specifies the maximum amount of time that will elapse before control is returned to the caller.</span></span> <span data-ttu-id="a3710-123">タイムアウトが発生すると、DB_S_ASYNCHRONOUS が返されます。</span><span class="sxs-lookup"><span data-stu-id="a3710-123">If this time-out expires, DB_S_ASYNCHRONOUS will be returned.</span></span> <span data-ttu-id="a3710-124">タイムアウトによって非同期操作が取り消されることはありません。</span><span class="sxs-lookup"><span data-stu-id="a3710-124">Time-outs never cancel asynchronous operations.</span></span> <span data-ttu-id="a3710-125">タイムアウト期間内に完了しない非同期操作をアプリケーションで取り消す必要がある場合、タイムアウトを待機後、DB_S_ASYNCHRONOUS が返されたときに明示的に操作を取り消す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3710-125">If the application needs to cancel an asynchronous operation that does not complete within a time-out period, it must wait for the time-out and then explicitly cancel the operation if DB_S_ASYNCHRONOUS is returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3710-126">OLE DB サービス コンポーネントを使用していて、DB_S_ASYNCHRONOUS を待機しているときに S_OK が返されることがあります。そのため、S_OK または DB_S_ASYNCHRONOUS が返される場合は、[ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) を呼び出して完了をチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3710-126">When the OLE DB Service Components are used, S_OK may be returned when DB_S_ASYNCHRONOUS is expected, so applications should call [ISSAsynchStatus::GetStatus](issasynchstatus-getstatus-ole-db.md) to check for completion when S_OK or DB_S_ASYNCHRONOUS is returned.</span></span>  
  
 <span data-ttu-id="a3710-127">*dwMillisecTimeOut* の値を INFINITE に設定すると、**ISSAsynchStatus::WaitForAsynchCompletion** メソッドは操作が完了するまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="a3710-127">If the *dwMillisecTimeOut* value is set to INFINITE, the **ISSAsynchStatus::WaitForAsynchCompletion** method blocks until the operation is done.</span></span> <span data-ttu-id="a3710-128">*dwMillisecTimeOut* の値を 0 に設定すると、メソッドからすぐに制御が戻り、保留中の操作の状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="a3710-128">If the *dwMillisecTimeOut* value is set to 0, then the method will return immediately with the status of the pending operation.</span></span> <span data-ttu-id="a3710-129">操作が完了する前にタイムアウトが発生すると、DB_S_ASYNCHRONOUS が返されます。</span><span class="sxs-lookup"><span data-stu-id="a3710-129">If the time-out expires before the operation is complete DB_S_ASYNCHRONOUS will be returned.</span></span>  
  
 <span data-ttu-id="a3710-130">タイムアウトが発生する前に操作が完了すると、返される HRESULT には操作から返された HRESULT が設定されます (返される HRESULT は、操作が同期的に実行された場合に返される HRESULT になります)。</span><span class="sxs-lookup"><span data-stu-id="a3710-130">If the operation completes before the time-out expires, the returned HRESULT will be the HRESULT returned by the operation (the HRESULT that would have been returned had the operation been performed synchronously).</span></span>  
  
 <span data-ttu-id="a3710-131">また、DBPROPSET_SQLSERVERROWSET プロパティ セットに SSPROP_ISSAsynchStatus プロパティが追加されています。</span><span class="sxs-lookup"><span data-stu-id="a3710-131">In addition, the SSPROP_ISSAsynchStatus property has been added to the DBPROPSET_SQLSERVERROWSET property set.</span></span> <span data-ttu-id="a3710-132">[ISSAsynchStatus](issasynchstatus-ole-db.md) インターフェイスをサポートするプロバイダーは、値 VARIANT_TRUE を指定してこのプロパティを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3710-132">Providers that support the [ISSAsynchStatus](issasynchstatus-ole-db.md) interface must implement this property with a value of VARIANT_TRUE.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3710-133">参照</span><span class="sxs-lookup"><span data-stu-id="a3710-133">See Also</span></span>  
 <span data-ttu-id="a3710-134">[非同期操作の実行](../native-client/features/performing-asynchronous-operations.md) </span><span class="sxs-lookup"><span data-stu-id="a3710-134">[Performing Asynchronous Operations](../native-client/features/performing-asynchronous-operations.md) </span></span>  
 [<span data-ttu-id="a3710-135">ISSAsynchStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a3710-135">ISSAsynchStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-ole-db.md)  
  
  
