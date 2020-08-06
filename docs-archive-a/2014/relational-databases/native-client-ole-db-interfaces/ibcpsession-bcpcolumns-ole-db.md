---
title: IBCPSession::BCPColumns (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
author: rothja
ms.author: jroth
ms.openlocfilehash: c842b2a815074c0db7e6ab21e0a85eac68a986a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739822"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a><span data-ttu-id="32ebb-102">IBCPSession::BCPColumns (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="32ebb-102">IBCPSession::BCPColumns (OLE DB)</span></span>
  <span data-ttu-id="32ebb-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。</span><span class="sxs-lookup"><span data-stu-id="32ebb-103">Sets the number of fields that are to be bound to the columns in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ebb-104">構文</span><span class="sxs-lookup"><span data-stu-id="32ebb-104">Syntax</span></span>  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a><span data-ttu-id="32ebb-105">解説</span><span class="sxs-lookup"><span data-stu-id="32ebb-105">Remarks</span></span>  
 <span data-ttu-id="32ebb-106">このメソッドは、内部的に [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) を呼び出して、フィールド データの既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="32ebb-106">Internally it calls [IBCPSession::BCPColFmt](ibcpsession-bcpcolfmt-ole-db.md) to set the default values for field data.</span></span> <span data-ttu-id="32ebb-107">これらの既定値は、[IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md) を使用してテーブル名を指定するときに、プロバイダーが内部的に取得する SQL Server の列情報を基に設定されます。</span><span class="sxs-lookup"><span data-stu-id="32ebb-107">These default values are obtained from the SQL Server column information that the provider internally retrieves when the table name is specified through [IBCPSession::BCPInit](ibcpsession-bcpinit-ole-db.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32ebb-108">有効なファイル名を指定して **BCPInit** を呼び出した後でのみ、このメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="32ebb-108">This method can be called only after **BCPInit** has been called with a valid file name.</span></span>  
  
 <span data-ttu-id="32ebb-109">既定とは異なる形式のユーザー ファイルを使用する場合にのみ、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="32ebb-109">You should call this method only if you intend to use a user-file format that differs from the default.</span></span> <span data-ttu-id="32ebb-110">ユーザー ファイルの既定の形式の詳細については、**BCPInit** メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32ebb-110">For more information about a description of the default user-file format, see the **BCPInit** method.</span></span>  
  
 <span data-ttu-id="32ebb-111">独自のファイル形式を完全に定義するために、**BCPColumns** メソッドを呼び出した後、ユーザー ファイル内の列ごとに **BCPColFmt** メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="32ebb-111">After calling the **BCPColumns** method, you must call the **BCPColFmt** method for each column in the user file to completely define a custom file format.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="32ebb-112">引数</span><span class="sxs-lookup"><span data-stu-id="32ebb-112">Arguments</span></span>  
 <span data-ttu-id="32ebb-113">*nColumns*[in]</span><span class="sxs-lookup"><span data-stu-id="32ebb-113">*nColumns*[in]</span></span>  
 <span data-ttu-id="32ebb-114">ユーザー ファイル内のフィールドの総数です。</span><span class="sxs-lookup"><span data-stu-id="32ebb-114">The total number of fields in the user file.</span></span> <span data-ttu-id="32ebb-115">ユーザー ファイルから SQL Server テーブルへのデータの一括コピーを準備していて、ユーザー ファイル内のすべてのフィールドをコピーしない場合でも、*nColumns* 引数にユーザー ファイル内のフィールドの総数を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32ebb-115">Even if you are preparing to bulk copy data from the user file to a SQL Server table and do not intend to copy all fields in the user file, you must still set the *nColumns* argument to the total number of user-file fields.</span></span> <span data-ttu-id="32ebb-116">その後、スキップするフィールドを **BCPColFmt** を使って指定できます。</span><span class="sxs-lookup"><span data-stu-id="32ebb-116">The skipped fields can then be specified through **BCPColFmt**.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="32ebb-117">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="32ebb-117">Return Code Values</span></span>  
 <span data-ttu-id="32ebb-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="32ebb-118">S_OK</span></span>  
 <span data-ttu-id="32ebb-119">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="32ebb-119">The method succeeded.</span></span>  
  
 <span data-ttu-id="32ebb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32ebb-120">E_FAIL</span></span>  
 <span data-ttu-id="32ebb-121">プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="32ebb-121">A provider-specific error occurred; for detailed information, use the [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) interface.</span></span>  
  
 <span data-ttu-id="32ebb-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="32ebb-122">E_UNEXPECTED</span></span>  
 <span data-ttu-id="32ebb-123">メソッドの呼び出しが予期されませんでした。</span><span class="sxs-lookup"><span data-stu-id="32ebb-123">The call to the method was unexpected.</span></span> <span data-ttu-id="32ebb-124">たとえば、このメソッドを呼び出す前に、**BCPInit** メソッドが呼び出されなかった場合などです。</span><span class="sxs-lookup"><span data-stu-id="32ebb-124">For example, the **BCPInit** method was not called before calling this method.</span></span> <span data-ttu-id="32ebb-125">また、1 回の一括コピー操作でこのメソッドが複数回呼び出されたときもこのリターン コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="32ebb-125">Also occurs when this method is called more than once for a bulk copy operation.</span></span>  
  
 <span data-ttu-id="32ebb-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="32ebb-126">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="32ebb-127">メモリ不足エラーです。</span><span class="sxs-lookup"><span data-stu-id="32ebb-127">Out-of-memory error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ebb-128">参照</span><span class="sxs-lookup"><span data-stu-id="32ebb-128">See Also</span></span>  
 <span data-ttu-id="32ebb-129">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="32ebb-129">[IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md) </span></span>  
 [<span data-ttu-id="32ebb-130">一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="32ebb-130">Performing Bulk Copy Operations</span></span>](../native-client/features/performing-bulk-copy-operations.md)  
  
  
