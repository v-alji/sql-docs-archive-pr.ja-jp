---
title: srv_paraminfo (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paraminfo
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
ms.openlocfilehash: cc3d51acc2ca560246c46267840db72934223999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742138"
---
# <a name="srv_paraminfo-extended-stored-procedure-api"></a><span data-ttu-id="35fff-102">srv_paraminfo (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="35fff-102">srv_paraminfo (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="35fff-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="35fff-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="35fff-104">パラメーターに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="35fff-104">Returns information about a parameter.</span></span> <span data-ttu-id="35fff-105">この関数は、[srv_paramtype](srv-paramtype-extended-stored-procedure-api.md)、[srv_paramlen](srv-paramlen-extended-stored-procedure-api.md)、[srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md)、および [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md) に代わる関数です。</span><span class="sxs-lookup"><span data-stu-id="35fff-105">This function supersedes the following functions: [srv_paramtype](srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md), and [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md).</span></span> <span data-ttu-id="35fff-106">**srv_paraminfo** では、「[データ型 (拡張ストアド プロシージャ API)](data-types-extended-stored-procedure-api.md)」に記載されているデータ型、および長さがゼロのデータをサポートします。</span><span class="sxs-lookup"><span data-stu-id="35fff-106">**srv_paraminfo** supports the data types in [Data Types](data-types-extended-stored-procedure-api.md) and zero-length data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35fff-107">構文</span><span class="sxs-lookup"><span data-stu-id="35fff-107">Syntax</span></span>  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="35fff-108">引数</span><span class="sxs-lookup"><span data-stu-id="35fff-108">Arguments</span></span>  
 <span data-ttu-id="35fff-109">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="35fff-109">*srvproc*</span></span>  
 <span data-ttu-id="35fff-110">クライアント接続のためのハンドルです。</span><span class="sxs-lookup"><span data-stu-id="35fff-110">A handle for a client connection.</span></span>  
  
 <span data-ttu-id="35fff-111">*n*</span><span class="sxs-lookup"><span data-stu-id="35fff-111">*n*</span></span>  
 <span data-ttu-id="35fff-112">設定するパラメーターの序数です。</span><span class="sxs-lookup"><span data-stu-id="35fff-112">The ordinal number of the parameter to be set.</span></span> <span data-ttu-id="35fff-113">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="35fff-113">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="35fff-114">*pbType*</span><span class="sxs-lookup"><span data-stu-id="35fff-114">*pbType*</span></span>  
 <span data-ttu-id="35fff-115">パラメーターのデータ型です。</span><span class="sxs-lookup"><span data-stu-id="35fff-115">The data type of the parameter.</span></span>  
  
 <span data-ttu-id="35fff-116">*pcbMaxLen*</span><span class="sxs-lookup"><span data-stu-id="35fff-116">*pcbMaxLen*</span></span>  
 <span data-ttu-id="35fff-117">パラメーターの最大長へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="35fff-117">Pointer to the maximum length of the parameter.</span></span>  
  
 <span data-ttu-id="35fff-118">*pcbActualLen*</span><span class="sxs-lookup"><span data-stu-id="35fff-118">*pcbActualLen*</span></span>  
 <span data-ttu-id="35fff-119">パラメーターの実際の長さへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="35fff-119">Pointer to the actual length of the parameter.</span></span> <span data-ttu-id="35fff-120">*pfNull* が FALSE に設定されている場合、値 0 (\**pcbActualLen* == 0) はデータの長さがゼロであることを示します。</span><span class="sxs-lookup"><span data-stu-id="35fff-120">A value of 0 (\**pcbActualLen* == 0) signifies zero-length data if \**pfNull* is set to FALSE.</span></span>  
  
 <span data-ttu-id="35fff-121">*pbData*</span><span class="sxs-lookup"><span data-stu-id="35fff-121">*pbData*</span></span>  
 <span data-ttu-id="35fff-122">パラメーター データのバッファーへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="35fff-122">Pointer to the buffer for parameter data.</span></span> <span data-ttu-id="35fff-123">*pbData* が NULL でない場合、拡張ストアド プロシージャ API により \**pbData* に \**pcbActualLen* バイトのデータが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="35fff-123">If *pbData* is not NULL, the Extended Store Procedure API writes \**pcbActualLen* bytes of data to \**pbData*.</span></span> <span data-ttu-id="35fff-124">*pbData* が NULL の場合、\**pbData* にデータは書き込まれませんが、関数により \**pbType*、\**pcbMaxLen*、\**pcbActualLen*、\**pfNull* が返されます。</span><span class="sxs-lookup"><span data-stu-id="35fff-124">If *pbData* is NULL, no data is written to \**pbData* but the function returns \**pbType*, \**pcbMaxLen*, \**pcbActualLen*, and \**pfNull*.</span></span> <span data-ttu-id="35fff-125">このバッファーのメモリは、アプリケーションで管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35fff-125">The memory for this buffer must be managed by the application.</span></span>  
  
 <span data-ttu-id="35fff-126">*pfNull*</span><span class="sxs-lookup"><span data-stu-id="35fff-126">*pfNull*</span></span>  
 <span data-ttu-id="35fff-127">NULL フラグへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="35fff-127">Pointer to a null flag.</span></span><span data-ttu-id="35fff-128">このパラメーターの値が NULL である場合、 \**pfNull* は TRUE に設定されます。</span><span class="sxs-lookup"><span data-stu-id="35fff-128">\ **pfNull* is set to TRUE if the value of the parameter is NULL.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="35fff-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="35fff-129">Returns</span></span>  
 <span data-ttu-id="35fff-130">パラメーター情報が正常に取得された場合は SUCCEED を返し、それ以外の場合は FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="35fff-130">If the parameter information was successfully obtained, SUCCEED is returned; otherwise, FAIL.</span></span> <span data-ttu-id="35fff-131">FAIL が返されるのは、現在のリモート ストアド プロシージャがない場合、および *n* 番目のリモート ストアド プロシージャ パラメーターがない場合です。</span><span class="sxs-lookup"><span data-stu-id="35fff-131">FAIL is returned when there is no current remote stored procedure and when there is no *n*th remote stored procedure parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35fff-132">解説</span><span class="sxs-lookup"><span data-stu-id="35fff-132">Remarks</span></span>  
 <span data-ttu-id="35fff-133">**セキュリティに関する注意** 拡張ストアド プロシージャのソース コードを十分に確認し、コンパイルした DLL をテストしたうえで実稼働サーバーにインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="35fff-133">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="35fff-134">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="35fff-134">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fff-135">参照</span><span class="sxs-lookup"><span data-stu-id="35fff-135">See Also</span></span>  
 [<span data-ttu-id="35fff-136">拡張ストアド プロシージャのプログラマーズ リファレンス</span><span class="sxs-lookup"><span data-stu-id="35fff-136">Extended Stored Procedures Programmer's Reference</span></span>](database-engine-extended-stored-procedures-reference.md)  
  
  
