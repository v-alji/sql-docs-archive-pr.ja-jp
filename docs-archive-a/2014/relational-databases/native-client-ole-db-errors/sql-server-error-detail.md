---
title: SQL Server エラーの詳細 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c03cf62dd274f9bcca213d33fb8969b26c9d980
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643801"
---
# <a name="sql-server-error-detail"></a><span data-ttu-id="6b703-102">SQL Server エラーの詳細</span><span class="sxs-lookup"><span data-stu-id="6b703-102">SQL Server Error Detail</span></span>
  <span data-ttu-id="6b703-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、プロバイダー固有のエラーインターフェイス[ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)を定義します。</span><span class="sxs-lookup"><span data-stu-id="6b703-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the provider-specific error interface [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).</span></span> <span data-ttu-id="6b703-104">このインターフェイスにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの詳細が返されるので、コマンドの実行や行セットの操作が失敗したときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6b703-104">The interface returns more detail about a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error and is valuable when command execution or rowset operations fail.</span></span>  
  
 <span data-ttu-id="6b703-105">**ISQLServerErrorInfo** インターフェイスにアクセスする方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="6b703-105">There are two ways to obtain access to **ISQLServerErrorInfo** interface.</span></span>  
  
 <span data-ttu-id="6b703-106">次のコード サンプルに示すように、コンシューマーは **IErrorRecords::GetCustomerErrorObject** を呼び出して **ISQLServerErrorInfo** ポインターを取得できます。</span><span class="sxs-lookup"><span data-stu-id="6b703-106">The consumer may call **IErrorRecords::GetCustomerErrorObject** to obtain an **ISQLServerErrorInfo** pointer, as shown in the following code sample.</span></span> <span data-ttu-id="6b703-107">(**ISQLErrorInfo** を取得する必要はありません)。**ISQLErrorInfo** と **ISQLServerErrorInfo** は、どちらもカスタム OLE DB エラー オブジェクトです。**ISQLServerErrorInfo** は、プロシージャ名や行番号などの詳細情報を含むサーバー エラーの情報を取得するために使用するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="6b703-107">(There is no need to obtain **ISQLErrorInfo.**) Both **ISQLErrorInfo** and **ISQLServerErrorInfo** are custom OLE DB error objects, with **ISQLServerErrorInfo** being the interface to use to obtain information of server errors, including such details as procedure name and line numbers.</span></span>  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 <span data-ttu-id="6b703-108">**ISQLServerErrorInfo** ポインターを取得するもう 1 つの方法は、既に取得した **ISQLErrorInfo** ポインターの **QueryInterface** メソッドを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="6b703-108">Another way to get an **ISQLServerErrorInfo** pointer is to call the **QueryInterface** method on an already-obtained **ISQLErrorInfo** pointer.</span></span> <span data-ttu-id="6b703-109">ただし、**ISQLServerErrorInfo** には **ISQLErrorInfo** から取得できる情報のスーパーセットが含まれているので、**GetCustomerErrorObject** から直接 **ISQLServerErrorInfo** を取得する方が効果的です。</span><span class="sxs-lookup"><span data-stu-id="6b703-109">Note that because **ISQLServerErrorInfo** contains a superset of the information available from **ISQLErrorInfo**, it makes sense to go directly to **ISQLServerErrorInfo** through **GetCustomerErrorObject**.</span></span>  
  
 <span data-ttu-id="6b703-110">**ISQLServerErrorInfo** インターフェイスでは、メンバー関数 [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md) が公開されます。</span><span class="sxs-lookup"><span data-stu-id="6b703-110">The **ISQLServerErrorInfo** interface exposes one member function, [ISQLServerErrorInfo::GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md).</span></span> <span data-ttu-id="6b703-111">この関数では、SSERRORINFO 構造体へのポインターと文字列バッファーへのポインターが返されます。</span><span class="sxs-lookup"><span data-stu-id="6b703-111">The function returns a pointer to an SSERRORINFO structure and a pointer to a string buffer.</span></span> <span data-ttu-id="6b703-112">どちらのポインターが参照するメモリも、コンシューマーが **IMalloc::Free** メソッドを使用して割り当て解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b703-112">Both pointers reference memory the consumer must deallocate by using the **IMalloc::Free** method.</span></span>  
  
 <span data-ttu-id="6b703-113">コンシューマーでは SSERRORINFO 構造体のメンバーが次のように解釈されます。</span><span class="sxs-lookup"><span data-stu-id="6b703-113">SSERRORINFO structure members are interpreted by the consumer as follows.</span></span>  
  
|<span data-ttu-id="6b703-114">メンバー</span><span class="sxs-lookup"><span data-stu-id="6b703-114">Member</span></span>|<span data-ttu-id="6b703-115">説明</span><span class="sxs-lookup"><span data-stu-id="6b703-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6b703-116">*pwszMessage*</span><span class="sxs-lookup"><span data-stu-id="6b703-116">*pwszMessage*</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6b703-117">エラー メッセージです。</span><span class="sxs-lookup"><span data-stu-id="6b703-117">error message.</span></span> <span data-ttu-id="6b703-118">このエラー メッセージは、**IErrorInfo::GetDescription** で返される文字列と同じです。</span><span class="sxs-lookup"><span data-stu-id="6b703-118">Identical to the string returned in **IErrorInfo::GetDescription**.</span></span>|  
|<span data-ttu-id="6b703-119">*pwszServer*</span><span class="sxs-lookup"><span data-stu-id="6b703-119">*pwszServer*</span></span>|<span data-ttu-id="6b703-120">セッションの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="6b703-120">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for the session.</span></span>|  
|<span data-ttu-id="6b703-121">*pwszProcedure*</span><span class="sxs-lookup"><span data-stu-id="6b703-121">*pwszProcedure*</span></span>|<span data-ttu-id="6b703-122">該当する場合は、エラーが発生したプロシージャの名前です。</span><span class="sxs-lookup"><span data-stu-id="6b703-122">If appropriate, the name of the procedure in which the error originated.</span></span> <span data-ttu-id="6b703-123">該当しない場合は空文字列です。</span><span class="sxs-lookup"><span data-stu-id="6b703-123">An empty string otherwise.</span></span>|  
|<span data-ttu-id="6b703-124">*lNative*</span><span class="sxs-lookup"><span data-stu-id="6b703-124">*lNative*</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6b703-125">のネイティブ エラー番号です。</span><span class="sxs-lookup"><span data-stu-id="6b703-125">native error number.</span></span> <span data-ttu-id="6b703-126">**ISQLErrorInfo::GetSQLInfo** の *plNativeError* パラメーターで返される値と同じです。</span><span class="sxs-lookup"><span data-stu-id="6b703-126">Identical to the value returned in the *plNativeError* parameter of **ISQLErrorInfo::GetSQLInfo**.</span></span>|  
|<span data-ttu-id="6b703-127">*bState*</span><span class="sxs-lookup"><span data-stu-id="6b703-127">*bState*</span></span>|<span data-ttu-id="6b703-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー メッセージの状態です。</span><span class="sxs-lookup"><span data-stu-id="6b703-128">State of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message.</span></span>|  
|<span data-ttu-id="6b703-129">*bClass*</span><span class="sxs-lookup"><span data-stu-id="6b703-129">*bClass*</span></span>|<span data-ttu-id="6b703-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー メッセージの重大度です。</span><span class="sxs-lookup"><span data-stu-id="6b703-130">Severity of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error message.</span></span>|  
|<span data-ttu-id="6b703-131">*wLineNumber*</span><span class="sxs-lookup"><span data-stu-id="6b703-131">*wLineNumber*</span></span>|<span data-ttu-id="6b703-132">該当する場合は、ストアド プロシージャでエラーが発生した行番号です。</span><span class="sxs-lookup"><span data-stu-id="6b703-132">When applicable, the line number of a stored procedure on which the error occurred.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b703-133">参照</span><span class="sxs-lookup"><span data-stu-id="6b703-133">See Also</span></span>  
 <span data-ttu-id="6b703-134">[誤り](errors.md) </span><span class="sxs-lookup"><span data-stu-id="6b703-134">[Errors](errors.md) </span></span>  
 [<span data-ttu-id="6b703-135">RAISERROR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6b703-135">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
