---
title: srv_setcollen (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_setcollen
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_setcollen
ms.assetid: 3c60f1c3-4562-463a-a259-12df172788bd
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e3023e2ac239e074656329da7d8af3aba3afa88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714365"
---
# <a name="srv_setcollen-extended-stored-procedure-api"></a><span data-ttu-id="45664-102">srv_setcollen (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="45664-102">srv_setcollen (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="45664-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="45664-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="45664-104">可変長列または NULL 値を許容する列の、現在のデータ長をバイト数で指定します。</span><span class="sxs-lookup"><span data-stu-id="45664-104">Specifies the current data length in bytes of a variable-length column or a column that allows NULL values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45664-105">構文</span><span class="sxs-lookup"><span data-stu-id="45664-105">Syntax</span></span>  
  
```  
  
int srv_setcollen (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="45664-106">引数</span><span class="sxs-lookup"><span data-stu-id="45664-106">Arguments</span></span>  
 <span data-ttu-id="45664-107">*srvproc*</span><span class="sxs-lookup"><span data-stu-id="45664-107">*srvproc*</span></span>  
 <span data-ttu-id="45664-108">特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="45664-108">Is a pointer to the SRV_PROC structure that is the handle for a particular client connection.</span></span> <span data-ttu-id="45664-109">この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="45664-109">The structure contains information the Extended Stored Procedure API library uses to manage communication and data between the application and the client.</span></span>  
  
 <span data-ttu-id="45664-110">*column*</span><span class="sxs-lookup"><span data-stu-id="45664-110">*column*</span></span>  
 <span data-ttu-id="45664-111">データ長を指定している列の番号を示します。</span><span class="sxs-lookup"><span data-stu-id="45664-111">Indicates the number of the column for which the data length is being specified.</span></span> <span data-ttu-id="45664-112">列には 1 から始まる番号が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="45664-112">Columns are numbered beginning with 1.</span></span>  
  
 <span data-ttu-id="45664-113">*len*</span><span class="sxs-lookup"><span data-stu-id="45664-113">*len*</span></span>  
 <span data-ttu-id="45664-114">列データの長さをバイト数で指定します。</span><span class="sxs-lookup"><span data-stu-id="45664-114">Indicates the length, in bytes, of the column data.</span></span> <span data-ttu-id="45664-115">長さが 0 である場合、列データの値が NULL であることを示します。</span><span class="sxs-lookup"><span data-stu-id="45664-115">A length of 0 means the column data value is null.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="45664-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="45664-116">Returns</span></span>  
 <span data-ttu-id="45664-117">SUCCEED または FAIL。</span><span class="sxs-lookup"><span data-stu-id="45664-117">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45664-118">解説</span><span class="sxs-lookup"><span data-stu-id="45664-118">Remarks</span></span>  
 <span data-ttu-id="45664-119">行の各列は最初に **srv_describe** で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45664-119">Each column of the row must first be defined with **srv_describe**.</span></span> <span data-ttu-id="45664-120">列のデータ長は **srv_describe** または **srv_setcollen** の前回呼び出し時に設定されます。</span><span class="sxs-lookup"><span data-stu-id="45664-120">The column data length is set by the last call to **srv_describe** or **srv_setcollen**.</span></span> <span data-ttu-id="45664-121">ある行について可変長のデータ (NULL 終端データ) が変化する場合、**srv_sendrow** を呼び出す前に、**srv_setcollen** を使用してデータを新しい長さに変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45664-121">If variable-length data (null-terminated data) changes for a row, **srv_setcollen** must be used to set it to the new length before calling **srv_sendrow**.</span></span> <span data-ttu-id="45664-122">NULL 値を許容する列では、NULL を許容する SRVINTN などのデータ型に *desttype* を設定して **srv_describe** を呼び出してから、*len* を 0 に設定して **srv_setcollen** を呼び出すことにより NULL データを指定します。</span><span class="sxs-lookup"><span data-stu-id="45664-122">For a column that allows null values, **srv_describe** must have been called with *desttype* set to a data type that allows nulls (like SRVINTN) and null data is specified by calling **srv_setcollen** with *len* set to 0.</span></span> <span data-ttu-id="45664-123">拡張ストアド プロシージャ API を使用して長さがゼロのデータを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="45664-123">Zero length data cannot be specified using the Extended Stored Procedure API.</span></span>  
  
 <span data-ttu-id="45664-124">列データ型が可変長の場合、*len* の値は確認されません。</span><span class="sxs-lookup"><span data-stu-id="45664-124">Note that when the data type of the column is variable-length, *len* is not checked.</span></span> <span data-ttu-id="45664-125">固定長の列について呼び出された場合、この関数は FAIL を返します。</span><span class="sxs-lookup"><span data-stu-id="45664-125">This function returns FAIL if called for a fixed-length column.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="45664-126">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="45664-126">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="45664-127">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="45664-127">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45664-128">参照</span><span class="sxs-lookup"><span data-stu-id="45664-128">See Also</span></span>  
 [<span data-ttu-id="45664-129">srv_describe &#40;拡張ストアド プロシージャ API&#41;</span><span class="sxs-lookup"><span data-stu-id="45664-129">srv_describe &#40;Extended Stored Procedure API&#41;</span></span>](srv-describe-extended-stored-procedure-api.md)  
  
  
