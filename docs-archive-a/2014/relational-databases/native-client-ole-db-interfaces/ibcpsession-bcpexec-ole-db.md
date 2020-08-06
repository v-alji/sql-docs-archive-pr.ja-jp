---
title: IBCPSession::BCPExec (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPExec (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
author: rothja
ms.author: jroth
ms.openlocfilehash: 1452888e046b6223c64a6cdf6fe09b074b815702
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713121"
---
# <a name="ibcpsessionbcpexec-ole-db"></a><span data-ttu-id="db115-102">IBCPSession::BCPExec (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="db115-102">IBCPSession::BCPExec (OLE DB)</span></span>
  <span data-ttu-id="db115-103">一括コピー操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="db115-103">Performs the bulk copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db115-104">構文</span><span class="sxs-lookup"><span data-stu-id="db115-104">Syntax</span></span>  
  
```  
  
HRESULT BCPExec(   
DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a><span data-ttu-id="db115-105">解説</span><span class="sxs-lookup"><span data-stu-id="db115-105">Remarks</span></span>  
 <span data-ttu-id="db115-106">**BCPExec** メソッドでは、[IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) メソッドで使用されている *eDirection* パラメーターの値に従って、データをユーザー ファイルからデータベース テーブルに、またはデータベース テーブルからユーザー ファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="db115-106">The **BCPExec** method copies data from a user file to a database table or vice versa, depending on the value of the *eDirection* parameter used with the [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) method.</span></span>  
  
 <span data-ttu-id="db115-107">**BCPExec** を呼び出す前に、有効なユーザー ファイル名を指定して **BCPInit** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="db115-107">Before calling **BCPExec**, call the **BCPInit** method with a valid user file name.</span></span> <span data-ttu-id="db115-108">この操作を行わないと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="db115-108">Failure to do so results in an error.</span></span> <span data-ttu-id="db115-109">唯一の例外は、一括コピーの出力操作にクエリを使用する場合です。</span><span class="sxs-lookup"><span data-stu-id="db115-109">The only exception is if a query is to be used for a bulk copy out operation.</span></span> <span data-ttu-id="db115-110">この場合は、**BCPInit** メソッドでテーブル名に NULL を指定してから、BCP_OPTION_HINTS オプションを使用してクエリを指定します。</span><span class="sxs-lookup"><span data-stu-id="db115-110">In that case specify NULL for the table name in the **BCPInit** method and then specify the query using the BCP_OPTION_HINTS option.</span></span>  
  
 <span data-ttu-id="db115-111">**BCPExec** メソッドは、短時間に優れた結果を得られる唯一の一括コピー メソッドです。</span><span class="sxs-lookup"><span data-stu-id="db115-111">The **BCPExec** method is the only bulk copy method that is likely to be outstanding for any length of time.</span></span> <span data-ttu-id="db115-112">そのため、このメソッドは非同期モードをサポートする唯一の一括コピー メソッドでもあります。</span><span class="sxs-lookup"><span data-stu-id="db115-112">It is therefore the only bulk copy method that supports asynchronous mode.</span></span> <span data-ttu-id="db115-113">非同期モードを使用するには、プロバイダー固有のセッション プロパティ SSPROP_ASYNCH_BULKCOPY を VARIANT_TRUE に設定してから、**BCPExec** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="db115-113">To use asynchronous mode, set the provider specific session property SSPROP_ASYNCH_BULKCOPY to VARIANT_TRUE before calling the **BCPExec** method.</span></span> <span data-ttu-id="db115-114">このプロパティは、DBPROPSET_SQLSERVERSESSION プロパティ セットに含まれています。</span><span class="sxs-lookup"><span data-stu-id="db115-114">This property is available in the DBPROPSET_SQLSERVERSESSION property set.</span></span> <span data-ttu-id="db115-115">コピーの完了を確認するには、同じパラメーターを指定して **BCPExec** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="db115-115">To test for completion, call the **BCPExec** method with the same parameters.</span></span> <span data-ttu-id="db115-116">一括コピーがまだ完了していない場合は、**BCPExec** メソッドから DB_S_ASYNCHRONOUS が返されます。</span><span class="sxs-lookup"><span data-stu-id="db115-116">If the bulk copy has not yet completed, the **BCPExec** method returns DB_S_ASYNCHRONOUS.</span></span> <span data-ttu-id="db115-117">また、*pRowsCopied* 引数には、サーバーとの間で送受信される行数の進行状況を表す数も返されます。</span><span class="sxs-lookup"><span data-stu-id="db115-117">It also returns in the *pRowsCopied* argument a status count of the number of rows that have been sent to or received from the server.</span></span> <span data-ttu-id="db115-118">サーバーに送信された行は、バッチの終わりに到達するまではコミットされません。</span><span class="sxs-lookup"><span data-stu-id="db115-118">Rows sent to the server are not committed until the end of a batch has been reached.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="db115-119">引数</span><span class="sxs-lookup"><span data-stu-id="db115-119">Arguments</span></span>  
 <span data-ttu-id="db115-120">*pRowsCopied*[out]</span><span class="sxs-lookup"><span data-stu-id="db115-120">*pRowsCopied*[out]</span></span>  
 <span data-ttu-id="db115-121">DWORD へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="db115-121">A pointer to a DWORD.</span></span> <span data-ttu-id="db115-122">**BCPExec** メソッドは、正常にコピーされた行数を使用して、DWORD を設定します。</span><span class="sxs-lookup"><span data-stu-id="db115-122">The **BCPExec** method fills the DWORD with the number of rows successfully copied.</span></span> <span data-ttu-id="db115-123">*pRowsCopied* 引数に NULL を設定すると、**BCPExec** メソッドはこの引数を無視します。</span><span class="sxs-lookup"><span data-stu-id="db115-123">If the *pRowsCopied* argument is set to NULL, it is ignored by the **BCPExec** method.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="db115-124">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="db115-124">Return Code Values</span></span>  
 <span data-ttu-id="db115-125">S_OK</span><span class="sxs-lookup"><span data-stu-id="db115-125">S_OK</span></span>  
 <span data-ttu-id="db115-126">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="db115-126">The method succeeded.</span></span>  
  
 <span data-ttu-id="db115-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db115-127">E_FAIL</span></span>  
 <span data-ttu-id="db115-128">プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="db115-128">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="db115-129">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="db115-129">E_UNEXPECTED</span></span>  
 <span data-ttu-id="db115-130">メソッドの呼び出しが予期されませんでした。</span><span class="sxs-lookup"><span data-stu-id="db115-130">The call to the method was unexpected.</span></span> <span data-ttu-id="db115-131">たとえば、このメソッドを呼び出す前に、**BCPInit** メソッドが呼び出されなかった場合などです。</span><span class="sxs-lookup"><span data-stu-id="db115-131">For example, the **BCPInit** method was not called before calling this method.</span></span> <span data-ttu-id="db115-132">また、操作が BCP_OPTION_ABORT オプションを使用して中断され、その後、**BCPExec** メソッドが呼び出された場合にも発生します。</span><span class="sxs-lookup"><span data-stu-id="db115-132">Also occurs if the operation has been aborted through using the BCP_OPTION_ABORT option, and the **BCPExec** method was called afterwards.</span></span>  
  
 <span data-ttu-id="db115-133">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="db115-133">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="db115-134">メモリ不足エラーです。</span><span class="sxs-lookup"><span data-stu-id="db115-134">Out-of-memory error.</span></span>  
  
 <span data-ttu-id="db115-135">DB_S_ENDOFROWSET</span><span class="sxs-lookup"><span data-stu-id="db115-135">DB_S_ENDOFROWSET</span></span>  
 <span data-ttu-id="db115-136">一括コピー操作が終了し、すべてのデータ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="db115-136">The bulk copy operation finished, and all the data transfer was completed.</span></span>  
  
 <span data-ttu-id="db115-137">DB_S_ASYNCHRONOUS</span><span class="sxs-lookup"><span data-stu-id="db115-137">DB_S_ASYNCHRONOUS</span></span>  
 <span data-ttu-id="db115-138">行の現在のバッチがコピーされました。</span><span class="sxs-lookup"><span data-stu-id="db115-138">The current batch of rows has been copied.</span></span> <span data-ttu-id="db115-139">次のバッチを転送するには、**BCPExec** メソッドを再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="db115-139">Call the **BCPExec** method again to transfer the next batch.</span></span>  
  
 <span data-ttu-id="db115-140">DB_S_ERRORSOCCURRED</span><span class="sxs-lookup"><span data-stu-id="db115-140">DB_S_ERRORSOCCURRED</span></span>  
 <span data-ttu-id="db115-141">一括コピー操作中にエラーが発生しました。そのため、一部の行がコピーされなかった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="db115-141">Errors occurred during the bulk copy operation, and some rows might not have been copied.</span></span> <span data-ttu-id="db115-142">エラー数は、許容されるエラーの最大数には達していません。</span><span class="sxs-lookup"><span data-stu-id="db115-142">The number of errors is still less than the maximum errors allowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db115-143">参照</span><span class="sxs-lookup"><span data-stu-id="db115-143">See Also</span></span>  
 <span data-ttu-id="db115-144">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="db115-144">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="db115-145">一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="db115-145">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
