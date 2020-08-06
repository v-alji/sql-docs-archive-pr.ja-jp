---
title: srv_willconvert (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_willconvert
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_willconvert
ms.assetid: 6f4db5fd-215a-461c-95e4-17697852733e
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b9adfbd2a73b30cbfc0229b7942f79d3ddc1a82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742113"
---
# <a name="srv_willconvert-extended-stored-procedure-api"></a><span data-ttu-id="bd221-102">srv_willconvert (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="bd221-102">srv_willconvert (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="bd221-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="bd221-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="bd221-104">ODS Library 内で特定のデータ型の変換が可能かどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="bd221-104">Determines whether a specific data type conversion is available within the ODS Library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd221-105">構文</span><span class="sxs-lookup"><span data-stu-id="bd221-105">Syntax</span></span>  
  
```  
  
BOOL srv_willconvert (  
int  
srctype  
,  
int  
desttype   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="bd221-106">引数</span><span class="sxs-lookup"><span data-stu-id="bd221-106">Arguments</span></span>  
 <span data-ttu-id="bd221-107">*srctype*</span><span class="sxs-lookup"><span data-stu-id="bd221-107">*srctype*</span></span>  
 <span data-ttu-id="bd221-108">変換するソース データのデータ型を示します。</span><span class="sxs-lookup"><span data-stu-id="bd221-108">Indicates the data type of the data to be converted.</span></span> <span data-ttu-id="bd221-109">このパラメーターには、拡張ストアド プロシージャ API の任意のデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd221-109">This parameter can be any of the Extended Stored Procedure API data types.</span></span>  
  
 <span data-ttu-id="bd221-110">*desttype*</span><span class="sxs-lookup"><span data-stu-id="bd221-110">*desttype*</span></span>  
 <span data-ttu-id="bd221-111">ソース データを変換した後のデータ型を示します。</span><span class="sxs-lookup"><span data-stu-id="bd221-111">Indicates the data type to which the source data is converted.</span></span> <span data-ttu-id="bd221-112">このパラメーターには、拡張ストアド プロシージャ API の任意のデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd221-112">This parameter can be any of the Extended Stored Procedure API data types.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="bd221-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="bd221-113">Returns</span></span>  
 <span data-ttu-id="bd221-114">データ型の変換がサポートされている場合は TRUE を返します。サポートされていない場合は FALSE を返します。</span><span class="sxs-lookup"><span data-stu-id="bd221-114">TRUE if the data type conversion is supported; FALSE if the data type conversion is not supported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd221-115">解説</span><span class="sxs-lookup"><span data-stu-id="bd221-115">Remarks</span></span>  
 <span data-ttu-id="bd221-116">各データ型については、「[データ型 &#40;拡張ストアド プロシージャ API&#41;](data-types-extended-stored-procedure-api.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bd221-116">For a description of each data type, see [Data Types &#40;Extended Stored Procedure API&#41;](data-types-extended-stored-procedure-api.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="bd221-117">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd221-117">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="bd221-118">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bd221-118">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd221-119">参照</span><span class="sxs-lookup"><span data-stu-id="bd221-119">See Also</span></span>  
 [<span data-ttu-id="bd221-120">srv_convert &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="bd221-120">srv_convert &#40;Extended Stored Procedure API&#41;</span></span>](srv-convert-extended-stored-procedure-api.md)  
  
  
