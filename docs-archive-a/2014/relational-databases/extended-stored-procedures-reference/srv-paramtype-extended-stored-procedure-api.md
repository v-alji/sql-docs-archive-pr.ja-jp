---
title: srv_paramtype (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramtype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramtype
ms.assetid: badc6d36-8a87-42b5-b28c-9c4f5ded8552
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c4b4006f8214670e3bd2bddfbaabe917fb9d778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633850"
---
# <a name="srv_paramtype-extended-stored-procedure-api"></a><span data-ttu-id="ac87e-102">srv_paramtype (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="ac87e-102">srv_paramtype (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="ac87e-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="ac87e-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="ac87e-104">リモート ストアド プロシージャ呼び出しのパラメーターのデータ型を返します。</span><span class="sxs-lookup"><span data-stu-id="ac87e-104">Returns the data type of a remote stored procedure call parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac87e-105">構文</span><span class="sxs-lookup"><span data-stu-id="ac87e-105">Syntax</span></span>  
  
```  
  
int srv_paramtype (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac87e-106">引数</span><span class="sxs-lookup"><span data-stu-id="ac87e-106">Arguments</span></span>  
 <span data-ttu-id="ac87e-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="ac87e-107">*srvproc*</span></span>  
 <span data-ttu-id="ac87e-108">特定のクライアント接続のためのハンドル (この場合は、リモート ストアド プロシージャ呼び出しを受け取るハンドル) である SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="ac87e-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection (in this case, the handle that received the remote stored procedure call).</span></span> <span data-ttu-id="ac87e-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="ac87e-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="ac87e-110">*n*</span><span class="sxs-lookup"><span data-stu-id="ac87e-110">*n*</span></span>  
 <span data-ttu-id="ac87e-111">パラメーターの番号を示します。</span><span class="sxs-lookup"><span data-stu-id="ac87e-111">Indicates the number of the parameter.</span></span> <span data-ttu-id="ac87e-112">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="ac87e-112">The first parameter is 1.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="ac87e-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac87e-113">Returns</span></span>  
 <span data-ttu-id="ac87e-114">パラメーターのデータ型のトークン値を返します。</span><span class="sxs-lookup"><span data-stu-id="ac87e-114">A token value for the data type of the parameter.</span></span> <span data-ttu-id="ac87e-115">データ型については、「[データ型 &#40;拡張ストアド プロシージャ API&#41;](data-types-extended-stored-procedure-api.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac87e-115">For information about data types, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span> <span data-ttu-id="ac87e-116">*n* 番目のパラメーターがない場合、またはリモート ストアド プロシージャがない場合は、- 1 を返します。</span><span class="sxs-lookup"><span data-stu-id="ac87e-116">If there is no *n*th parameter or if there is no remote stored procedure, it returns - 1.</span></span>  
  
 <span data-ttu-id="ac87e-117">パラメーターがデータ型の1つである場合、この関数は次の値を返し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="ac87e-117">This function returns the following values, if the parameter is one of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] data types.</span></span>  
  
|<span data-ttu-id="ac87e-118">新しいデータ型</span><span class="sxs-lookup"><span data-stu-id="ac87e-118">New data types</span></span>|<span data-ttu-id="ac87e-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="ac87e-119">Return value</span></span>|  
|--------------------|------------------|  
|`BITN`|<span data-ttu-id="ac87e-120">SRVBIT</span><span class="sxs-lookup"><span data-stu-id="ac87e-120">SRVBIT</span></span>|  
|`BIGVARCHAR`|<span data-ttu-id="ac87e-121">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="ac87e-121">VARCHAR</span></span>|  
|`BIGCHAR`|<span data-ttu-id="ac87e-122">CHAR</span><span class="sxs-lookup"><span data-stu-id="ac87e-122">CHAR</span></span>|  
|`BIGBINARY`|<span data-ttu-id="ac87e-123">BINARY</span><span class="sxs-lookup"><span data-stu-id="ac87e-123">BINARY</span></span>|  
|`BIGVARBINARY`|<span data-ttu-id="ac87e-124">VARBINARY</span><span class="sxs-lookup"><span data-stu-id="ac87e-124">VARBINARY</span></span>|  
|`NCHAR`|<span data-ttu-id="ac87e-125">CHAR</span><span class="sxs-lookup"><span data-stu-id="ac87e-125">CHAR</span></span>|  
|`NVARCHAR`|<span data-ttu-id="ac87e-126">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="ac87e-126">VARCHAR</span></span>|  
|`NTEXT`|<span data-ttu-id="ac87e-127">-1</span><span class="sxs-lookup"><span data-stu-id="ac87e-127">-1</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac87e-128">解説</span><span class="sxs-lookup"><span data-stu-id="ac87e-128">Remarks</span></span>  
 <span data-ttu-id="ac87e-129">パラメーターを指定してリモート ストアド プロシージャを呼び出す場合、パラメーターは名前で指定することも、名前を使用せずにその位置を指定して渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="ac87e-129">When a remote stored procedure call is made with parameters, the parameters can be passed either by name or by position (unnamed).</span></span> <span data-ttu-id="ac87e-130">名前によるパラメーター指定と位置によるパラメーター指定を混合してリモート ストアド プロシージャを呼び出すと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ac87e-130">If the remote stored procedure call is made with some parameters passed by name and some passed by position, an error occurs.</span></span> <span data-ttu-id="ac87e-131">SRV_RPC ハンドラーはまだ呼び出されていますが、パラメーターがなかったかのように見え、 **srv_rpcparams** 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="ac87e-131">The SRV_RPC handler is still called, but it appears as if there were no parameters and **srv_rpcparams** returns 0.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ac87e-132">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac87e-132">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="ac87e-133">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac87e-133">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac87e-134">参照</span><span class="sxs-lookup"><span data-stu-id="ac87e-134">See Also</span></span>  
 <span data-ttu-id="ac87e-135">[srv_paraminfo &#40;拡張ストアドプロシージャ API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span><span class="sxs-lookup"><span data-stu-id="ac87e-135">[srv_paraminfo &#40;Extended Stored Procedure API&#41;](srv-paraminfo-extended-stored-procedure-api.md) </span></span>  
 [<span data-ttu-id="ac87e-136">srv_rpcparams &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="ac87e-136">srv_rpcparams &#40;Extended Stored Procedure API&#41;</span></span>](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
