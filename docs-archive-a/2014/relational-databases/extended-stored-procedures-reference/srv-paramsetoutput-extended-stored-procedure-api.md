---
title: srv_paramsetoutput (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramsetoutput
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramsetoutput
ms.assetid: f2810e19-e513-458b-8925-5756b6ee1313
author: rothja
ms.author: jroth
ms.openlocfilehash: 2847367fe5d6052728cebf30467b68cb14fb8e63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632472"
---
# <a name="srv_paramsetoutput-extended-stored-procedure-api"></a><span data-ttu-id="6ffe2-102">srv_paramsetoutput (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="6ffe2-102">srv_paramsetoutput (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="6ffe2-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="6ffe2-104">戻りパラメーターの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-104">Sets the value of a return parameter.</span></span> <span data-ttu-id="6ffe2-105">この関数は、**srv_paramset** 関数に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-105">This function supersedes the **srv_paramset** function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ffe2-106">構文</span><span class="sxs-lookup"><span data-stu-id="6ffe2-106">Syntax</span></span>  
  
```  
  
int srv_paramsetoutput (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbData  
,  
ULONG   
cbLen  
,  
BOOL  
fNull   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ffe2-107">引数</span><span class="sxs-lookup"><span data-stu-id="6ffe2-107">Arguments</span></span>  
 <span data-ttu-id="6ffe2-108">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="6ffe2-108">*srvproc*</span></span>  
 <span data-ttu-id="6ffe2-109">クライアント接続のためのハンドルです。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-109">Is a handle for a client connection.</span></span>  
  
 <span data-ttu-id="6ffe2-110">*n*</span><span class="sxs-lookup"><span data-stu-id="6ffe2-110">*n*</span></span>  
 <span data-ttu-id="6ffe2-111">設定するパラメーターの序数です。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-111">Is the ordinal number of the parameter to be set.</span></span> <span data-ttu-id="6ffe2-112">最初のパラメーターは 1 です。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-112">The first parameter is 1.</span></span>  
  
 <span data-ttu-id="6ffe2-113">*pbData*</span><span class="sxs-lookup"><span data-stu-id="6ffe2-113">*pbData*</span></span>  
 <span data-ttu-id="6ffe2-114">プロシージャの戻りパラメーターとしてクライアントに返されるデータ値を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-114">Is a pointer to the data value to be sent back to the client as a procedure return parameter.</span></span>  
  
 <span data-ttu-id="6ffe2-115">*cbLen*</span><span class="sxs-lookup"><span data-stu-id="6ffe2-115">*cbLen*</span></span>  
 <span data-ttu-id="6ffe2-116">返されるデータの実際の長さです。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-116">Is the actual length of the data to be returned.</span></span> <span data-ttu-id="6ffe2-117">パラメーターのデータ型が固定長の値を指定しており、NULL 値を許容しない型 (*srvbit*、*srvint1* など) である場合、*cbLen* は無視されます。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-117">If the data type of the parameter specifies values of a constant length and does not allow null values (for example, *srvbit* or *srvint1*), *cbLen* is ignored.</span></span> <span data-ttu-id="6ffe2-118">*fNull* が FALSE の場合、値 0 は長さ 0 のデータを示します。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-118">A value of 0 signifies zero-length data if *fNull* is FALSE.</span></span>  
  
 <span data-ttu-id="6ffe2-119">*fNull*</span><span class="sxs-lookup"><span data-stu-id="6ffe2-119">*fNull*</span></span>  
 <span data-ttu-id="6ffe2-120">戻りパラメーターの値が NULL かどうかを示すフラグです。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-120">Is a flag indicating whether the value of the return parameter is NULL.</span></span> <span data-ttu-id="6ffe2-121">パラメーターを NULL に設定する必要がある場合は、このフラグを TRUE に設定します。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-121">Set this flag to TRUE if the parameter should be set to NULL.</span></span> <span data-ttu-id="6ffe2-122">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-122">The default value is FALSE.</span></span> <span data-ttu-id="6ffe2-123">*fNull* を TRUE に設定した場合は、*cbLen* を 0 に設定する必要があります。このように設定しないと関数は失敗します。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-123">If *fNull* is set to TRUE, *cbLen* should be set to 0 or the function will fail.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6ffe2-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="6ffe2-124">Returns</span></span>  
 <span data-ttu-id="6ffe2-125">パラメーター情報が正常に設定された場合は SUCCEED を返し、それ以外の場合は FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-125">If the parameter information was successfully set, SUCCEED is returned; otherwise, FAIL.</span></span> <span data-ttu-id="6ffe2-126">FAIL が返されるのは、次の場合です。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-126">FAIL is returned when</span></span>  
  
-   <span data-ttu-id="6ffe2-127">パラメーターが戻りパラメーターでない場合。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-127">the parameter is not a return parameter, or</span></span>  
  
-   <span data-ttu-id="6ffe2-128">*cbLen* 引数が無効である場合。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-128">the *cbLen* argument is invalid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ffe2-129">解説</span><span class="sxs-lookup"><span data-stu-id="6ffe2-129">Remarks</span></span>  
 <span data-ttu-id="6ffe2-130">**セキュリティに関する注意** 拡張ストアド プロシージャのソース コードを十分に確認し、コンパイルした DLL をテストしたうえで実稼働サーバーにインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-130">**Security Note** You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="6ffe2-131">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6ffe2-131">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
