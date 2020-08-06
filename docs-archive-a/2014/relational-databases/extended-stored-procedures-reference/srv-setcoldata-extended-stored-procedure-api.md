---
title: srv_setcoldata (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcoldata
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcoldata
ms.assetid: 2e19205a-25ca-4d4a-916b-d591cf2c892b
author: rothja
ms.author: jroth
ms.openlocfilehash: b67aa2f7b5a37057d2ed87846689919d84ec4aaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739985"
---
# <a name="srv_setcoldata-extended-stored-procedure-api"></a><span data-ttu-id="a5df0-102">srv_setcoldata (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="a5df0-102">srv_setcoldata (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="a5df0-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="a5df0-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="a5df0-104">列のデータの現在のアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a5df0-104">Specifies the current address for a column's data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5df0-105">構文</span><span class="sxs-lookup"><span data-stu-id="a5df0-105">Syntax</span></span>  
  
```  
  
int srv_setcoldata (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
void *  
data   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5df0-106">引数</span><span class="sxs-lookup"><span data-stu-id="a5df0-106">Arguments</span></span>  
 <span data-ttu-id="a5df0-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="a5df0-107">*srvproc*</span></span>  
 <span data-ttu-id="a5df0-108">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="a5df0-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="a5df0-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a5df0-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="a5df0-110">*column*</span><span class="sxs-lookup"><span data-stu-id="a5df0-110">*column*</span></span>  
 <span data-ttu-id="a5df0-111">アドレスを指定している列の番号を示します。</span><span class="sxs-lookup"><span data-stu-id="a5df0-111">Indicates the number of the column the address is being specified for.</span></span> <span data-ttu-id="a5df0-112">列には 1 から始まる番号が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a5df0-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="a5df0-113">*data*</span><span class="sxs-lookup"><span data-stu-id="a5df0-113">*data*</span></span>  
 <span data-ttu-id="a5df0-114">列のデータを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="a5df0-114">Is a pointer for a column's data.</span></span> <span data-ttu-id="a5df0-115">別に **srv_setcoldata** を呼び出して列データを置き換えるか、**srv_senddone** を呼び出すまでは、*data* に割り当てたメモリを解放しないでください。</span><span class="sxs-lookup"><span data-stu-id="a5df0-115">Memory allocated for *data* should not be freed until the column data is replaced by another call to **srv_setcoldata**, or until **srv_senddone** is called.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="a5df0-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="a5df0-116">Returns</span></span>  
 <span data-ttu-id="a5df0-117">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="a5df0-117">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5df0-118">解説</span><span class="sxs-lookup"><span data-stu-id="a5df0-118">Remarks</span></span>  
 <span data-ttu-id="a5df0-119">行の各列はあらかじめ **srv_describe** で定義しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5df0-119">Each column of the row must be defined first with **srv_describe**.</span></span> <span data-ttu-id="a5df0-120">列データのアドレスは、最初は **srv_describe** で設定されます。</span><span class="sxs-lookup"><span data-stu-id="a5df0-120">Column data addresses are initially set with **srv_describe**.</span></span> <span data-ttu-id="a5df0-121">列データのアドレスが変わった場合は、データの新しいアドレスを指定するために **srv_setcoldata** を呼び出してから、変更された各列について改めて **srv_setcoldata** を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5df0-121">If the address of the column data changes, **srv_setcoldata** must be called to specify the new address of the data and **srv_setcoldata** must be called separately for each changed column.</span></span>  
  
 <span data-ttu-id="a5df0-122">NULL データを表現するには、**srv_setcollen** を使用して列の長さを 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="a5df0-122">Null data is represented by setting the column's length to 0 with **srv_setcollen**.</span></span> <span data-ttu-id="a5df0-123">これにより、データのアドレスは無視されます。</span><span class="sxs-lookup"><span data-stu-id="a5df0-123">The data address is then ignored.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a5df0-124">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5df0-124">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="a5df0-125">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a5df0-125">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5df0-126">参照</span><span class="sxs-lookup"><span data-stu-id="a5df0-126">See Also</span></span>  
 [<span data-ttu-id="a5df0-127">srv_describe &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="a5df0-127">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
