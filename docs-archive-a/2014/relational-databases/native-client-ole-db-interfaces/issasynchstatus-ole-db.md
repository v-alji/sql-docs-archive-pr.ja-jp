---
title: ISSAsynchStatus (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAsynchStatus (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- ISSAsynchStatus interface
ms.assetid: c643f09f-9ccc-4d8b-9243-3cde86c2bd46
author: rothja
ms.author: jroth
ms.openlocfilehash: 4489f9d1ad576d49d885842f6969f9b61065791c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634498"
---
# <a name="issasynchstatus-ole-db"></a><span data-ttu-id="51378-102">ISSAsynchStatus (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="51378-102">ISSAsynchStatus (OLE DB)</span></span>
  <span data-ttu-id="51378-103">**ISSAsynchStatus**は、非同期操作のサポートを公開 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="51378-103">**ISSAsynchStatus** exposes support for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] asynchronous operations.</span></span> <span data-ttu-id="51378-104">これは、コア OLE DB インターフェイス**id**から継承される省略可能なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="51378-104">This is an optional interface that inherits from the core OLE DB interface **IDBAsynchStatus**.</span></span> <span data-ttu-id="51378-105">**ISSAsynchStatus** には、**IDBAsynchStatus** から継承される **Abort** メソッドと **GetStatus** メソッドに加えて、非同期操作が完了するかタイムアウトが発生するまで待機する際に使用する新しいメソッドが 1 つ用意されています。</span><span class="sxs-lookup"><span data-stu-id="51378-105">In addition to the **Abort** and **GetStatus** methods inherited from **IDBAsynchStatus**, **ISSAsynchStatus** provides one new method that is used to wait until an asynchronous operation has completed or a time-out occurs.</span></span>  
  
|<span data-ttu-id="51378-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="51378-106">Method</span></span>|<span data-ttu-id="51378-107">説明</span><span class="sxs-lookup"><span data-stu-id="51378-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51378-108">ISSAsynchStatus::Abort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="51378-108">ISSAsynchStatus::Abort &#40;OLE DB&#41;</span></span>](issasynchstatus-abort-ole-db.md)|<span data-ttu-id="51378-109">非同期に実行されている操作を取り消します。</span><span class="sxs-lookup"><span data-stu-id="51378-109">Cancels an asynchronously executing operation.</span></span>|  
|[<span data-ttu-id="51378-110">ISSAsynchStatus::GetStatus &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="51378-110">ISSAsynchStatus::GetStatus &#40;OLE DB&#41;</span></span>](issasynchstatus-getstatus-ole-db.md)|<span data-ttu-id="51378-111">非同期に実行されている操作の状態を返します。</span><span class="sxs-lookup"><span data-stu-id="51378-111">Returns the status of an asynchronously executing operation.</span></span>|  
|[<span data-ttu-id="51378-112">ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="51378-112">ISSAsynchStatus::WaitForAsynchCompletion &#40;OLE DB&#41;</span></span>](issasynchstatus-waitforasynchcompletion-ole-db.md)|<span data-ttu-id="51378-113">非同期に実行されている操作が完了するかタイムアウトが発生するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="51378-113">Waits until the asynchronously executing operation is complete or a time-out occurs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51378-114">解説</span><span class="sxs-lookup"><span data-stu-id="51378-114">Remarks</span></span>  
 <span data-ttu-id="51378-115">**ISSAsynchStatus** に実装される **ISSAsynchStatus::GetStatus** メソッドは、**IDBAsynchStatus::GetStatus** メソッドと同じです。ただし、データ ソース オブジェクトの初期化が中止された場合、DB_E_CANCELED ではなく E_UNEXPECTED が返される点が異なります (**ISSAsynchStatus::WaitForAsynchCompletion** は、DB_E_CANCELED を返します)。</span><span class="sxs-lookup"><span data-stu-id="51378-115">The **ISSAsynchStatus** implementation of the **ISSAsynchStatus::GetStatus** method is the same as the **IDBAsynchStatus::GetStatus** method except that if the initialization of a data source object is aborted, E_UNEXPECTED is returned rather than DB_E_CANCELED (although **ISSAsynchStatus::WaitForAsynchCompletion** returns DB_E_CANCELED).</span></span> <span data-ttu-id="51378-116">これは、初期化の中止後、追加の初期化操作が試行される場合に備えて、データ ソース オブジェクトの状態が通常の状態のままにならないためです。</span><span class="sxs-lookup"><span data-stu-id="51378-116">This is because the data source object is not left in the usual state following an abort operation, so that further initialization operations may be attempted.</span></span>  
  
 <span data-ttu-id="51378-117">次に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の非同期実行の使用をサポートしているメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="51378-117">The following methods support the use of asynchronous execution in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="51378-118">**ICommand::Execute**</span><span class="sxs-lookup"><span data-stu-id="51378-118">**ICommand::Execute**</span></span>  
  
-   <span data-ttu-id="51378-119">**IOpenRowset::OpenRowset**</span><span class="sxs-lookup"><span data-stu-id="51378-119">**IOpenRowset::OpenRowset**</span></span>  
  
-   <span data-ttu-id="51378-120">**IMultipleResults::GetResult**</span><span class="sxs-lookup"><span data-stu-id="51378-120">**IMultipleResults::GetResult**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51378-121">参照</span><span class="sxs-lookup"><span data-stu-id="51378-121">See Also</span></span>  
 <span data-ttu-id="51378-122">[インターフェイス &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="51378-122">[Interfaces &#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md) </span></span>  
 [<span data-ttu-id="51378-123">非同期操作の実行</span><span class="sxs-lookup"><span data-stu-id="51378-123">Performing Asynchronous Operations</span></span>](../native-client/features/performing-asynchronous-operations.md)  
  
  
