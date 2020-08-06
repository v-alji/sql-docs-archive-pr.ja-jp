---
title: ISSAbort::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSAbort::Abort (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: rothja
ms.author: jroth
ms.openlocfilehash: 3daad53087c876af8dc46bccc9c4bf7952976067
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718117"
---
# <a name="issabortabort-ole-db"></a><span data-ttu-id="ca779-102">ISSAbort::Abort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="ca779-102">ISSAbort::Abort (OLE DB)</span></span>
  <span data-ttu-id="ca779-103">現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。</span><span class="sxs-lookup"><span data-stu-id="ca779-103">Cancels the current rowset plus any batched commands associated with the current command.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca779-104">構文</span><span class="sxs-lookup"><span data-stu-id="ca779-104">Syntax</span></span>  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="ca779-105">解説</span><span class="sxs-lookup"><span data-stu-id="ca779-105">Remarks</span></span>  
 <span data-ttu-id="ca779-106">中止されるコマンドがストアド プロシージャの場合、ストアド プロシージャ (およびそのプロシージャを呼び出したすべてのプロシージャ) の実行と、そのストアド プロシージャの呼び出しが含まれるコマンド バッチの実行が終了します。</span><span class="sxs-lookup"><span data-stu-id="ca779-106">If the command being aborted is in a stored procedure, execution of the stored procedure (and any procedures which had called that procedure) will be terminated as well as the command batch which contains the stored procedure call.</span></span> <span data-ttu-id="ca779-107">サーバーがクライアントに結果セットを転送中の場合、この処理も停止します。</span><span class="sxs-lookup"><span data-stu-id="ca779-107">If the server is in the process of transferring a result set to the client, this will be stopped.</span></span> <span data-ttu-id="ca779-108">クライアントが結果セットを使用しない場合、行セットを解放する前に **ISSAbort::Abort** を呼び出すと、行セットの解放が高速になります。ただし、開いているトランザクションがあり、XACT_ABORT が ON の場合、**ISSAbort::Abort** が呼び出されたときに、トランザクションがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="ca779-108">If the client does not want to consume a result set, calling **ISSAbort::Abort** before releasing the rowset will speed up the rowset release, but if there is an open transaction and XACT_ABORT is ON, the transaction will be rolled back when **ISSAbort::Abort** is called</span></span>  
  
 <span data-ttu-id="ca779-109">**Issabort:: Abort**が S_OK を返すと、関連付けられた**IMultipleResults**インターフェイスは使用できない状態になり、解放されるまで、すべてのメソッド呼び出し ( **IUnknown**インターフェイスによって定義されるメソッドを除く) に DB_E_CANCELED を返します。</span><span class="sxs-lookup"><span data-stu-id="ca779-109">After **ISSAbort::Abort** returns S_OK, the associated **IMultipleResults** interface enters a unusable state and returns DB_E_CANCELED to all method calls (except for methods defined by the **IUnknown** interface) until it is released.</span></span> <span data-ttu-id="ca779-110">**Abort** を呼び出す前に、**IMultipleResults** から **IRowset** を取得している場合、これも使用できない状態になり、**ISSAbort::Abort** の正常な呼び出し後にこのインターフェイスが解放されるまでは、すべてのメソッド呼び出しで DB_E_CANCELED が返されます (ただし、**IUnknown** インターフェイスと **IRowset::ReleaseRows** で定義されたメソッドは除きます)。</span><span class="sxs-lookup"><span data-stu-id="ca779-110">If an **IRowset** had been obtained from **IMultipleResults** prior to a call to **Abort**, it also enters an unusable state and returns DB_E_CANCELED to all method calls (except for methods defined by the **IUnknown** interface and **IRowset::ReleaseRows**) until it is released after a successful call to **ISSAbort::Abort**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca779-111">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、サーバーの XACT_ABORT 状態が ON の場合、**ISSAbort::Abort** を実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するときに、現在のすべての暗黙的または明示的なトランザクションが終了し、ロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="ca779-111">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], if the server XACT_ABORT state is ON, executing **ISSAbort::Abort** will terminate and roll back any current implicit or explicit transaction when connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ca779-112">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、現在のトランザクションは中止されません。</span><span class="sxs-lookup"><span data-stu-id="ca779-112">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will not abort the current transaction.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="ca779-113">引数</span><span class="sxs-lookup"><span data-stu-id="ca779-113">Arguments</span></span>  
 <span data-ttu-id="ca779-114">[なし] :</span><span class="sxs-lookup"><span data-stu-id="ca779-114">None.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="ca779-115">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="ca779-115">Return Code Values</span></span>  
 <span data-ttu-id="ca779-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca779-116">S_OK</span></span>  
 <span data-ttu-id="ca779-117">**ISSAbort::Abort** メソッドは、バッチが取り消された場合 S_OK を、それ以外の場合 DB_E_CANTCANCEL を返します。</span><span class="sxs-lookup"><span data-stu-id="ca779-117">The **ISSAbort::Abort** method returns S_OK if the batch was canceled and DB_E_CANTCANCEL otherwise.</span></span> <span data-ttu-id="ca779-118">バッチが既に取り消されている場合は、DB_E_CANCELED を返します。</span><span class="sxs-lookup"><span data-stu-id="ca779-118">If the batch has already been canceled, DB_E_CANCELED is returned.</span></span>  
  
 <span data-ttu-id="ca779-119">DB_E_CANCELED</span><span class="sxs-lookup"><span data-stu-id="ca779-119">DB_E_CANCELED</span></span>  
 <span data-ttu-id="ca779-120">バッチは既に取り消されています。</span><span class="sxs-lookup"><span data-stu-id="ca779-120">The batch has already been canceled.</span></span>  
  
 <span data-ttu-id="ca779-121">DB_E_CANTCANCEL</span><span class="sxs-lookup"><span data-stu-id="ca779-121">DB_E_CANTCANCEL</span></span>  
 <span data-ttu-id="ca779-122">バッチは取り消されませんでした。</span><span class="sxs-lookup"><span data-stu-id="ca779-122">The batch was not canceled.</span></span>  
  
 <span data-ttu-id="ca779-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca779-123">E_FAIL</span></span>  
 <span data-ttu-id="ca779-124">プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="ca779-124">A provider specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="ca779-125">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="ca779-125">E_UNEXPECTED</span></span>  
 <span data-ttu-id="ca779-126">メソッドの呼び出しが予期されませんでした。</span><span class="sxs-lookup"><span data-stu-id="ca779-126">The call to the method was unexpected.</span></span> <span data-ttu-id="ca779-127">たとえば、**ISSAbort::Abort** が既に呼び出されていたために、オブジェクトがゾンビ状態になっている場合などです。</span><span class="sxs-lookup"><span data-stu-id="ca779-127">For example, the object is in a zombie state because **ISSAbort::Abort** has already been called.</span></span>  
  
 <span data-ttu-id="ca779-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ca779-128">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ca779-129">メモリ不足エラー。</span><span class="sxs-lookup"><span data-stu-id="ca779-129">Out of memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca779-130">参照</span><span class="sxs-lookup"><span data-stu-id="ca779-130">See Also</span></span>  
 [<span data-ttu-id="ca779-131">ISSAbort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ca779-131">ISSAbort &#40;OLE DB&#41;</span></span>](../../database-engine/dev-guide/issabort-ole-db.md)  
  
  
