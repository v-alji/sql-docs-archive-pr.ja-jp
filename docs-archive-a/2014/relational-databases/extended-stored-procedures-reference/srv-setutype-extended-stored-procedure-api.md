---
title: srv_setutype (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setutype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
author: rothja
ms.author: jroth
ms.openlocfilehash: e9e02605995e44f5869633d5e8778a955236005f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739984"
---
# <a name="srv_setutype-extended-stored-procedure-api"></a><span data-ttu-id="84f40-102">srv_setutype (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="84f40-102">srv_setutype (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="84f40-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="84f40-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="84f40-104">行内の列について、ユーザー定義データ型を設定します。</span><span class="sxs-lookup"><span data-stu-id="84f40-104">Sets the user-defined data type for a column in a row.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f40-105">構文</span><span class="sxs-lookup"><span data-stu-id="84f40-105">Syntax</span></span>  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="84f40-106">引数</span><span class="sxs-lookup"><span data-stu-id="84f40-106">Arguments</span></span>  
 <span data-ttu-id="84f40-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="84f40-107">*srvproc*</span></span>  
 <span data-ttu-id="84f40-108">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="84f40-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="84f40-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="84f40-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="84f40-110">*column*</span><span class="sxs-lookup"><span data-stu-id="84f40-110">*column*</span></span>  
 <span data-ttu-id="84f40-111">設定する列を示します。</span><span class="sxs-lookup"><span data-stu-id="84f40-111">Indicates which column to set.</span></span> <span data-ttu-id="84f40-112">列には 1 から始まる番号が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="84f40-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="84f40-113">*user_type*</span><span class="sxs-lookup"><span data-stu-id="84f40-113">*user_type*</span></span>  
 <span data-ttu-id="84f40-114">ユーザー定義データ型のコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="84f40-114">Specifies the user-defined data type code.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="84f40-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="84f40-115">Returns</span></span>  
 <span data-ttu-id="84f40-116">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="84f40-116">SUCCEED or FAIL.</span></span> <span data-ttu-id="84f40-117">列が存在しない場合は FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="84f40-117">Returns FAIL if the column does not exist.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84f40-118">解説</span><span class="sxs-lookup"><span data-stu-id="84f40-118">Remarks</span></span>  
 <span data-ttu-id="84f40-119">列には、実際のデータ型とユーザー定義データ型の 2 つのデータ型があります。</span><span class="sxs-lookup"><span data-stu-id="84f40-119">A column has two data types: its actual data type and its user-defined data type.</span></span> <span data-ttu-id="84f40-120">では、このユーザー定義データ型を使用して、列 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の実際のユーザー定義データ型 (存在する場合) と、列の null 値の許容と更新などの列の説明情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="84f40-120">The user-defined data type is used by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to store the actual user-defined data type of the column, if any, and column description information, such as nullability and updatability, for the column.</span></span>  
  
 <span data-ttu-id="84f40-121">**srv_setutype** 関数は、**srv_describe** で *column* が定義されいれば、最後の行を送信する前のどの時点でも呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="84f40-121">The **srv_setutype** function can be called any time that *column* has been defined with **srv_describe** and before the last row has been sent.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="84f40-122">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="84f40-122">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="84f40-123">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="84f40-123">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f40-124">参照</span><span class="sxs-lookup"><span data-stu-id="84f40-124">See Also</span></span>  
 [<span data-ttu-id="84f40-125">srv_describe &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="84f40-125">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
