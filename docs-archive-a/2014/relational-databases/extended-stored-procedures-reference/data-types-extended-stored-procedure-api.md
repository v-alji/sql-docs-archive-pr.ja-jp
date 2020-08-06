---
title: データ型 (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
ms.openlocfilehash: aae0c6f2b309d182a93274171d2f8c21344fe3b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631023"
---
# <a name="data-types-extended-stored-procedure-api"></a><span data-ttu-id="2f995-102">データ型 (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="2f995-102">Data Types (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="2f995-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="2f995-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="2f995-104">拡張ストアド プロシージャ API のデータ型を使用するには、プログラムに Srv.h ヘッダー ファイルをインクルードします。</span><span class="sxs-lookup"><span data-stu-id="2f995-104">To use the Extended Stored Procedure API data types, include the Srv.h header file in your program.</span></span>  
  
|<span data-ttu-id="2f995-105">データ型</span><span class="sxs-lookup"><span data-stu-id="2f995-105">Data type</span></span>|<span data-ttu-id="2f995-106">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="2f995-106">SQL Server data type</span></span>|<span data-ttu-id="2f995-107">説明</span><span class="sxs-lookup"><span data-stu-id="2f995-107">Description</span></span>|  
|---------------|--------------------------|-----------------|  
|<span data-ttu-id="2f995-108">SRVBIGBINARY</span><span class="sxs-lookup"><span data-stu-id="2f995-108">SRVBIGBINARY</span></span>|`binary`|<span data-ttu-id="2f995-109">`binary` データ型。長さは 0 ～ 8,000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="2f995-109">`binary` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="2f995-110">SRVBIGCHAR</span><span class="sxs-lookup"><span data-stu-id="2f995-110">SRVBIGCHAR</span></span>|`char`|<span data-ttu-id="2f995-111">`character` データ型。長さは 0 ～ 8,000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="2f995-111">`character` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="2f995-112">SRVBIGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="2f995-112">SRVBIGVARBINARY</span></span>|`varbinary`|<span data-ttu-id="2f995-113">可変長 `binary` データ型。長さは 0 ～ 8,000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="2f995-113">Variable-length `binary` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="2f995-114">SRVBIGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="2f995-114">SRVBIGVARCHAR</span></span>|`varchar`|<span data-ttu-id="2f995-115">可変長 `character` データ型。長さは 0 ～ 8,000 バイトです。</span><span class="sxs-lookup"><span data-stu-id="2f995-115">Variable-length `character` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="2f995-116">SRVBINARY</span><span class="sxs-lookup"><span data-stu-id="2f995-116">SRVBINARY</span></span>|`binary`|<span data-ttu-id="2f995-117">`binary` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-117">`binary` data type.</span></span>|  
|<span data-ttu-id="2f995-118">SRVBIT</span><span class="sxs-lookup"><span data-stu-id="2f995-118">SRVBIT</span></span>|`Bit`|<span data-ttu-id="2f995-119">`bit` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-119">`bit` data type.</span></span>|  
|<span data-ttu-id="2f995-120">SRVBITN</span><span class="sxs-lookup"><span data-stu-id="2f995-120">SRVBITN</span></span>|`bit null`|<span data-ttu-id="2f995-121">`bit` データ型。NULL 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="2f995-121">`bit` data type, null values allowed.</span></span>|  
|<span data-ttu-id="2f995-122">SRVCHAR</span><span class="sxs-lookup"><span data-stu-id="2f995-122">SRVCHAR</span></span>|`char`|<span data-ttu-id="2f995-123">`character` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-123">`character` data type.</span></span>|  
|<span data-ttu-id="2f995-124">SRVDATETIME</span><span class="sxs-lookup"><span data-stu-id="2f995-124">SRVDATETIME</span></span>|`datetime`|<span data-ttu-id="2f995-125">8 バイトの `datetime` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-125">8-byte `datetime` data type.</span></span>|  
|<span data-ttu-id="2f995-126">SRVDATETIM4</span><span class="sxs-lookup"><span data-stu-id="2f995-126">SRVDATETIM4</span></span>|`smalldatetime`|<span data-ttu-id="2f995-127">4 バイトの `smalldatetime` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-127">4-byte `smalldatetime` data type.</span></span>|  
|<span data-ttu-id="2f995-128">SRVDATETIMN</span><span class="sxs-lookup"><span data-stu-id="2f995-128">SRVDATETIMN</span></span>|<span data-ttu-id="2f995-129">**datetime null**</span><span class="sxs-lookup"><span data-stu-id="2f995-129">**datetime null**</span></span>|<span data-ttu-id="2f995-130">`smalldatetime` データ型または `datetime` データ型。NULL 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="2f995-130">`smalldatetime` or `datetime` data type, null values allowed.</span></span>|  
|<span data-ttu-id="2f995-131">SRVDECIMAL</span><span class="sxs-lookup"><span data-stu-id="2f995-131">SRVDECIMAL</span></span>|`decimal`|<span data-ttu-id="2f995-132">`decimal` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-132">`decimal` data type.</span></span>|  
|<span data-ttu-id="2f995-133">SRVDECIMALN</span><span class="sxs-lookup"><span data-stu-id="2f995-133">SRVDECIMALN</span></span>|`decimal null`|<span data-ttu-id="2f995-134">`decimal` データ型。NULL 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="2f995-134">`decimal` data type, null values allowed.</span></span>|  
|<span data-ttu-id="2f995-135">SRVFLT4</span><span class="sxs-lookup"><span data-stu-id="2f995-135">SRVFLT4</span></span>|`real`|<span data-ttu-id="2f995-136">4 バイトの `real` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-136">4-byte `real` data type.</span></span>|  
|<span data-ttu-id="2f995-137">SRVFLT8</span><span class="sxs-lookup"><span data-stu-id="2f995-137">SRVFLT8</span></span>|`float`|<span data-ttu-id="2f995-138">8 バイトの `float` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-138">8-byte `float` data type.</span></span>|  
|<span data-ttu-id="2f995-139">SRVFLTN</span><span class="sxs-lookup"><span data-stu-id="2f995-139">SRVFLTN</span></span>|<span data-ttu-id="2f995-140">`real` &#124; `float null`</span><span class="sxs-lookup"><span data-stu-id="2f995-140">`real` &#124; `float null`</span></span>|<span data-ttu-id="2f995-141">`real` データ型または `float` データ型。NULL 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="2f995-141">`real` or `float` data type, null values allowed.</span></span>|  
|<span data-ttu-id="2f995-142">SRVIMAGE</span><span class="sxs-lookup"><span data-stu-id="2f995-142">SRVIMAGE</span></span>|`image`|<span data-ttu-id="2f995-143">`image` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-143">`image` data type.</span></span>|  
|<span data-ttu-id="2f995-144">SRVINT1</span><span class="sxs-lookup"><span data-stu-id="2f995-144">SRVINT1</span></span>|`tinyint`|<span data-ttu-id="2f995-145">1 バイトの `tinyint` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-145">1-byte `tinyint` data type.</span></span>|  
|<span data-ttu-id="2f995-146">SRVINT2</span><span class="sxs-lookup"><span data-stu-id="2f995-146">SRVINT2</span></span>|`smallint`|<span data-ttu-id="2f995-147">2 バイトの `smallint` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-147">2-byte `smallint` data type.</span></span>|  
|<span data-ttu-id="2f995-148">SRVINT4</span><span class="sxs-lookup"><span data-stu-id="2f995-148">SRVINT4</span></span>|`int`|<span data-ttu-id="2f995-149">4 バイトの `int` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-149">4-byte `int` data type.</span></span>|  
|<span data-ttu-id="2f995-150">SRVINTN</span><span class="sxs-lookup"><span data-stu-id="2f995-150">SRVINTN</span></span>|<span data-ttu-id="2f995-151">`tinyint` &#124; `smallint` &#124; `int null`</span><span class="sxs-lookup"><span data-stu-id="2f995-151">`tinyint` &#124; `smallint` &#124; `int null`</span></span>|<span data-ttu-id="2f995-152">`tinyint` データ型、`smallint` データ型、`int` データ型のいずれか。NULL 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="2f995-152">`tinyint`, `smallint`, or `int` data type, null values allowed.</span></span>|  
|<span data-ttu-id="2f995-153">SRVMONEY4</span><span class="sxs-lookup"><span data-stu-id="2f995-153">SRVMONEY4</span></span>|`smallmoney`|<span data-ttu-id="2f995-154">4 バイトの `smallmoney` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-154">4-byte `smallmoney` data type.</span></span>|  
|<span data-ttu-id="2f995-155">SRVMONEY</span><span class="sxs-lookup"><span data-stu-id="2f995-155">SRVMONEY</span></span>|`money`|<span data-ttu-id="2f995-156">8 バイトの `money` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-156">8-byte `money` data type.</span></span>|  
|<span data-ttu-id="2f995-157">SRVMONEYN</span><span class="sxs-lookup"><span data-stu-id="2f995-157">SRVMONEYN</span></span>|<span data-ttu-id="2f995-158">`money` &#124; `smallmoney null`</span><span class="sxs-lookup"><span data-stu-id="2f995-158">`money` &#124; `smallmoney null`</span></span>|<span data-ttu-id="2f995-159">`smallmoney` データ型または `money` データ型。NULL 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="2f995-159">`smallmoney` or `money` data type, null values allowed.</span></span>|  
|<span data-ttu-id="2f995-160">SRVNCHAR</span><span class="sxs-lookup"><span data-stu-id="2f995-160">SRVNCHAR</span></span>|<span data-ttu-id="2f995-161">**nchar**</span><span class="sxs-lookup"><span data-stu-id="2f995-161">**nchar**</span></span>|<span data-ttu-id="2f995-162">Unicode の `character` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-162">Unicode `character` data type.</span></span>|  
|<span data-ttu-id="2f995-163">SRVNTEXT</span><span class="sxs-lookup"><span data-stu-id="2f995-163">SRVNTEXT</span></span>|`ntext`|<span data-ttu-id="2f995-164">Unicode の `text` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-164">Unicode `text` data type.</span></span>|  
|<span data-ttu-id="2f995-165">SRVNUMERIC</span><span class="sxs-lookup"><span data-stu-id="2f995-165">SRVNUMERIC</span></span>|`numeric`|<span data-ttu-id="2f995-166">`numeric` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-166">`numeric` data type.</span></span>|  
|<span data-ttu-id="2f995-167">SRVNUMERICN</span><span class="sxs-lookup"><span data-stu-id="2f995-167">SRVNUMERICN</span></span>|`numeric null`|<span data-ttu-id="2f995-168">`numeric` データ型。NULL 値を許容します。</span><span class="sxs-lookup"><span data-stu-id="2f995-168">`numeric` data type, null values allowed.</span></span>|  
|<span data-ttu-id="2f995-169">SRVNVARCHAR</span><span class="sxs-lookup"><span data-stu-id="2f995-169">SRVNVARCHAR</span></span>|<span data-ttu-id="2f995-170">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="2f995-170">**nvarchar**</span></span>|<span data-ttu-id="2f995-171">Unicode の可変長 `character` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-171">Unicode variable-length `character` data type.</span></span>|  
|<span data-ttu-id="2f995-172">SRVTEXT</span><span class="sxs-lookup"><span data-stu-id="2f995-172">SRVTEXT</span></span>|`text`|<span data-ttu-id="2f995-173">`text` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-173">`text` data type.</span></span>|  
|<span data-ttu-id="2f995-174">SRVVARBINARY</span><span class="sxs-lookup"><span data-stu-id="2f995-174">SRVVARBINARY</span></span>|`varbinary`|<span data-ttu-id="2f995-175">可変長 `binary` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-175">Variable-length `binary` data type.</span></span>|  
|<span data-ttu-id="2f995-176">SRVVARCHAR</span><span class="sxs-lookup"><span data-stu-id="2f995-176">SRVVARCHAR</span></span>|`varchar`|<span data-ttu-id="2f995-177">可変長 `character` データ型。</span><span class="sxs-lookup"><span data-stu-id="2f995-177">Variable-length `character` data type.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2f995-178">拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f995-178">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="2f995-179">セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2f995-179">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
