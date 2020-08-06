---
title: srv_alloc (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_alloc
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
author: rothja
ms.author: jroth
ms.openlocfilehash: 7b372c1b43987e5bebd1fb82e995dc6d262455ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633854"
---
# <a name="srv_alloc-extended-stored-procedure-api"></a><span data-ttu-id="6f1b9-102">srv_alloc (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="6f1b9-102">srv_alloc (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="6f1b9-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="6f1b9-104">メモリを動的に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-104">Allocates memory dynamically.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f1b9-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f1b9-105">Syntax</span></span>  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6f1b9-106">引数</span><span class="sxs-lookup"><span data-stu-id="6f1b9-106">Arguments</span></span>  
 <span data-ttu-id="6f1b9-107">*size*</span><span class="sxs-lookup"><span data-stu-id="6f1b9-107">*size*</span></span>  
 <span data-ttu-id="6f1b9-108">割り当てるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-108">Specifies the number of bytes to allocate.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="6f1b9-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="6f1b9-109">Returns</span></span>  
 <span data-ttu-id="6f1b9-110">新しく割り当てた領域を指すポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-110">A pointer to the newly allocated space.</span></span> <span data-ttu-id="6f1b9-111">*size* で指定したバイト数を割り当てられない場合は、NULL ポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-111">If *size* bytes cannot be allocated, a null pointer is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f1b9-112">解説</span><span class="sxs-lookup"><span data-stu-id="6f1b9-112">Remarks</span></span>  
 <span data-ttu-id="6f1b9-113">**srv_alloc** 関数は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API の **GlobalAlloc** 関数に相当します。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-113">The **srv_alloc** function is equivalent to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API  **GlobalAlloc** function.</span></span> <span data-ttu-id="6f1b9-114">拡張ストアド プロシージャ API アプリケーションでは、通常の Windows API C ランタイムのメモリ管理関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-114">Normal Windows API C run-time memory management functions can be used in an Extended Stored Procedure API application.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="6f1b9-115">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-115">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="6f1b9-116">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6f1b9-116">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
