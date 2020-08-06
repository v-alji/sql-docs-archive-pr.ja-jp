---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: rothja
ms.author: jroth
ms.openlocfilehash: c3e325cd99276e04a178b89c19b233289edc09fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718129"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a><span data-ttu-id="8efa6-102">ISQLServerErrorInfo::GetErrorInfo (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="8efa6-102">ISQLServerErrorInfo::GetErrorInfo (OLE DB)</span></span>
  <span data-ttu-id="8efa6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーの詳細を格納している Native Client OLE DB プロバイダー SSERRORINFO 構造体へのポインターを返し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="8efa6-103">Returns a pointer to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider SSERRORINFO structure containing the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error details.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8efa6-104">構文</span><span class="sxs-lookup"><span data-stu-id="8efa6-104">Syntax</span></span>  
  
```  
  
   HRESULT GetErrorInfo(  
SSERRORINFO**ppSSErrorInfo,  
OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a><span data-ttu-id="8efa6-105">引数</span><span class="sxs-lookup"><span data-stu-id="8efa6-105">Arguments</span></span>  
 <span data-ttu-id="8efa6-106">*ppSSErrorInfo*[out]</span><span class="sxs-lookup"><span data-stu-id="8efa6-106">*ppSSErrorInfo*[out]</span></span>  
 <span data-ttu-id="8efa6-107">SSERRORINFO 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8efa6-107">A pointer to a SSERRORINFO structure.</span></span> <span data-ttu-id="8efa6-108">メソッドが失敗するか、エラーに関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 情報がない場合、プロバイダーはメモリの割り当てを行わず、出力時に *ppSSErrorInfo* 引数に NULL ポインターを設定します。</span><span class="sxs-lookup"><span data-stu-id="8efa6-108">If the method fails or there is no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information associated with the error, the provider does not allocate any memory, and ensures that the *ppSSErrorInfo* argument is a null pointer on output.</span></span>  
  
 <span data-ttu-id="8efa6-109">*ppErrorStrings*[out]</span><span class="sxs-lookup"><span data-stu-id="8efa6-109">*ppErrorStrings*[out]</span></span>  
 <span data-ttu-id="8efa6-110">Unicode 文字列ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8efa6-110">A pointer to a Unicode character-string pointer.</span></span> <span data-ttu-id="8efa6-111">メソッドが失敗するか、エラーに関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 情報がない場合、プロバイダーはメモリの割り当てを行わず、出力時に *ppErrorStrings* 引数に NULL ポインターを設定します。</span><span class="sxs-lookup"><span data-stu-id="8efa6-111">If the method fails or there is no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] information associated with an error, the provider does not allocate any memory, and ensures that the *ppErrorStrings* argument is a null pointer on output.</span></span> <span data-ttu-id="8efa6-112">**IMalloc::Free** メソッドを使用して *ppErrorStrings* 引数を解放すると、メモリがブロック単位で割り当てられているので、結果の SSERRORINFO 構造体の 3 つの各文字列メンバーが解放されます。</span><span class="sxs-lookup"><span data-stu-id="8efa6-112">Freeing the *ppErrorStrings* argument with the **IMalloc::Free** method frees the three individual string members of the returned SSERRORINFO structure, as the memory is allocated in a block.</span></span>  
  
## <a name="return-code-values"></a><span data-ttu-id="8efa6-113">リターン コードの値</span><span class="sxs-lookup"><span data-stu-id="8efa6-113">Return Code Values</span></span>  
 <span data-ttu-id="8efa6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8efa6-114">S_OK</span></span>  
 <span data-ttu-id="8efa6-115">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="8efa6-115">The method succeeded.</span></span>  
  
 <span data-ttu-id="8efa6-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8efa6-116">E_INVALIDARG</span></span>  
 <span data-ttu-id="8efa6-117">*ppSSErrorInfo* または *ppErrorStrings* 引数のいずれかが NULL でした。</span><span class="sxs-lookup"><span data-stu-id="8efa6-117">Either the *ppSSErrorInfo* or the *ppErrorStrings* argument was NULL.</span></span>  
  
 <span data-ttu-id="8efa6-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8efa6-118">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="8efa6-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、要求を完了するために必要なメモリを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="8efa6-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider could not allocate sufficient memory to complete the request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8efa6-120">解説</span><span class="sxs-lookup"><span data-stu-id="8efa6-120">Remarks</span></span>  
 <span data-ttu-id="8efa6-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、コンシューマーによって渡されたポインターによって返される SSERRORINFO および OLECHAR 文字列にメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8efa6-121">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider allocates memory for the SSERRORINFO and OLECHAR strings returned through the pointers passed by the consumer.</span></span> <span data-ttu-id="8efa6-122">コンシューマーはエラー データにアクセスする必要がなくなった時点で、**IMalloc::Free** メソッドを使用してこのメモリの割り当てを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8efa6-122">The consumer must deallocate this memory by using the **IMalloc::Free** method when it no longer requires access to the error data.</span></span>  
  
 <span data-ttu-id="8efa6-123">SSERRORINFO 構造体は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="8efa6-123">The SSERRORINFO structure is defined as follows:</span></span>  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|<span data-ttu-id="8efa6-124">メンバー</span><span class="sxs-lookup"><span data-stu-id="8efa6-124">Member</span></span>|<span data-ttu-id="8efa6-125">説明</span><span class="sxs-lookup"><span data-stu-id="8efa6-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8efa6-126">*pwszMessage*</span><span class="sxs-lookup"><span data-stu-id="8efa6-126">*pwszMessage*</span></span>|<span data-ttu-id="8efa6-127">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー メッセージ。</span><span class="sxs-lookup"><span data-stu-id="8efa6-127">The error message from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8efa6-128">このメッセージは、**IErrorInfo::GetDescription** メソッドにより返されます。</span><span class="sxs-lookup"><span data-stu-id="8efa6-128">The message is returned through the **IErrorInfo::GetDescription** method.</span></span>|  
|<span data-ttu-id="8efa6-129">*pwszServer*</span><span class="sxs-lookup"><span data-stu-id="8efa6-129">*pwszServer*</span></span>|<span data-ttu-id="8efa6-130">エラーが発生した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="8efa6-130">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which the error occurred.</span></span>|  
|<span data-ttu-id="8efa6-131">*pwszProcedure*</span><span class="sxs-lookup"><span data-stu-id="8efa6-131">*pwszProcedure*</span></span>|<span data-ttu-id="8efa6-132">エラーがストアド プロシージャ内で発生している場合は、エラーが発生したストアド プロシージャの名前です。それ以外の場合は、空文字列になります。</span><span class="sxs-lookup"><span data-stu-id="8efa6-132">The name of the stored procedure generating the error if the error occurred in a stored procedure; otherwise, an empty string.</span></span>|  
|<span data-ttu-id="8efa6-133">*lNative*</span><span class="sxs-lookup"><span data-stu-id="8efa6-133">*lNative*</span></span>|<span data-ttu-id="8efa6-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー番号。</span><span class="sxs-lookup"><span data-stu-id="8efa6-134">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error number.</span></span> <span data-ttu-id="8efa6-135">このエラー番号は、**ISQLErrorInfo::GetSQLInfo** メソッドの *plNativeError* パラメーターに返されるものと同じになります。</span><span class="sxs-lookup"><span data-stu-id="8efa6-135">The error number is identical to that returned in the *plNativeError* parameter of the **ISQLErrorInfo::GetSQLInfo** method.</span></span>|  
|<span data-ttu-id="8efa6-136">*bState*</span><span class="sxs-lookup"><span data-stu-id="8efa6-136">*bState*</span></span>|<span data-ttu-id="8efa6-137">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの状態。</span><span class="sxs-lookup"><span data-stu-id="8efa6-137">The state of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error.</span></span>|  
|<span data-ttu-id="8efa6-138">*bClass*</span><span class="sxs-lookup"><span data-stu-id="8efa6-138">*bClass*</span></span>|<span data-ttu-id="8efa6-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの重大度。</span><span class="sxs-lookup"><span data-stu-id="8efa6-139">The severity of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error.</span></span>|  
|<span data-ttu-id="8efa6-140">*wLineNumber*</span><span class="sxs-lookup"><span data-stu-id="8efa6-140">*wLineNumber*</span></span>|<span data-ttu-id="8efa6-141">該当する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャのエラー メッセージを生成した行です。</span><span class="sxs-lookup"><span data-stu-id="8efa6-141">When applicable, the line of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedure that generated the error message.</span></span> <span data-ttu-id="8efa6-142">プロシージャが関係していない場合は、既定値 1 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8efa6-142">If no procedure is involved, the default value is 1.</span></span>|  
  
 <span data-ttu-id="8efa6-143">構造体内のポインターは、*ppErrorStrings* 引数に返される文字列内のアドレスを指します。</span><span class="sxs-lookup"><span data-stu-id="8efa6-143">Pointers in the structure reference addresses in the string returned in the *ppErrorStrings* argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8efa6-144">参照</span><span class="sxs-lookup"><span data-stu-id="8efa6-144">See Also</span></span>  
 <span data-ttu-id="8efa6-145">[ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="8efa6-145">[ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) </span></span>  
 [<span data-ttu-id="8efa6-146">RAISERROR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8efa6-146">RAISERROR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
