---
title: サポートされるデータ型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a7dda500486c39a66f871d5934f957028fc51e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740985"
---
# <a name="supported-data-types"></a><span data-ttu-id="d6acd-102">サポートされるデータ型</span><span class="sxs-lookup"><span data-stu-id="d6acd-102">Supported Data Types</span></span>
  <span data-ttu-id="d6acd-103">メモリ最適化テーブルとネイティブコンパイルストアドプロシージャでは、次のデータ型がサポートされ**て**います。</span><span class="sxs-lookup"><span data-stu-id="d6acd-103">The following data types are **supported** in memory-optimized tables and natively compiled stored procedures:</span></span>  
  
 <span data-ttu-id="d6acd-104">**数値のデータ型**</span><span class="sxs-lookup"><span data-stu-id="d6acd-104">**Numeric Data Types**</span></span>  
  
|<span data-ttu-id="d6acd-105">データ型</span><span class="sxs-lookup"><span data-stu-id="d6acd-105">Data type</span></span>|<span data-ttu-id="d6acd-106">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d6acd-106">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="d6acd-107">INT</span><span class="sxs-lookup"><span data-stu-id="d6acd-107">int</span></span>|[<span data-ttu-id="d6acd-108">int、bigint、smallint、tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-108">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="d6acd-109">bigint</span><span class="sxs-lookup"><span data-stu-id="d6acd-109">bigint</span></span>|[<span data-ttu-id="d6acd-110">int、bigint、smallint、tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-110">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="d6acd-111">smallint</span><span class="sxs-lookup"><span data-stu-id="d6acd-111">smallint</span></span>|[<span data-ttu-id="d6acd-112">int、bigint、smallint、tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-112">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="d6acd-113">tinyint</span><span class="sxs-lookup"><span data-stu-id="d6acd-113">tinyint</span></span>|[<span data-ttu-id="d6acd-114">int、bigint、smallint、tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-114">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="d6acd-115">decimal</span><span class="sxs-lookup"><span data-stu-id="d6acd-115">decimal</span></span>|[<span data-ttu-id="d6acd-116">decimal 型と numeric 型 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-116">decimal and numeric &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|<span data-ttu-id="d6acd-117">numeric</span><span class="sxs-lookup"><span data-stu-id="d6acd-117">numeric</span></span>|[<span data-ttu-id="d6acd-118">decimal 型と numeric 型 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-118">decimal and numeric &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|<span data-ttu-id="d6acd-119">float</span><span class="sxs-lookup"><span data-stu-id="d6acd-119">float</span></span>|[<span data-ttu-id="d6acd-120">float と real &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-120">float and real &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|<span data-ttu-id="d6acd-121">real</span><span class="sxs-lookup"><span data-stu-id="d6acd-121">real</span></span>|[<span data-ttu-id="d6acd-122">float と real &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-122">float and real &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|<span data-ttu-id="d6acd-123">money</span><span class="sxs-lookup"><span data-stu-id="d6acd-123">money</span></span>|[<span data-ttu-id="d6acd-124">money および smallmoney &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-124">money and smallmoney &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|<span data-ttu-id="d6acd-125">smallmoney</span><span class="sxs-lookup"><span data-stu-id="d6acd-125">smallmoney</span></span>|[<span data-ttu-id="d6acd-126">money および smallmoney &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-126">money and smallmoney &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 <span data-ttu-id="d6acd-127">**文字列データ型**</span><span class="sxs-lookup"><span data-stu-id="d6acd-127">**String Data Types**</span></span>  
  
|<span data-ttu-id="d6acd-128">データ型</span><span class="sxs-lookup"><span data-stu-id="d6acd-128">Data type</span></span>|<span data-ttu-id="d6acd-129">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d6acd-129">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="d6acd-130">char(n)</span><span class="sxs-lookup"><span data-stu-id="d6acd-130">char(n)</span></span>|[<span data-ttu-id="d6acd-131">char および varchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-131">char and varchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|<span data-ttu-id="d6acd-132">varchar (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d6acd-132">varchar(n) <sup>1</sup></span></span>|[<span data-ttu-id="d6acd-133">char および varchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-133">char and varchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|<span data-ttu-id="d6acd-134">nchar(n)</span><span class="sxs-lookup"><span data-stu-id="d6acd-134">nchar(n)</span></span>|[<span data-ttu-id="d6acd-135">nchar および nvarchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-135">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|<span data-ttu-id="d6acd-136">nvarchar (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d6acd-136">nvarchar(n) <sup>1</sup></span></span>|[<span data-ttu-id="d6acd-137">nchar および nvarchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-137">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|<span data-ttu-id="d6acd-138">sysname</span><span class="sxs-lookup"><span data-stu-id="d6acd-138">sysname</span></span>|[<span data-ttu-id="d6acd-139">nchar および nvarchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-139">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <span data-ttu-id="d6acd-140"><sup>1</sup>行の合計で8060バイトの制限があり、可変長型の場合はカウント (n) です。</span><span class="sxs-lookup"><span data-stu-id="d6acd-140"><sup>1</sup> Limitation is 8060 bytes per row total, counting (n) in variable-length types.</span></span>  
  
 <span data-ttu-id="d6acd-141">サポートされている照合順序の詳細については、「[照合順序とコードページ](../../database-engine/collations-and-code-pages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6acd-141">For information about supported collations, see [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).</span></span>  
  
 <span data-ttu-id="d6acd-142">**日付および時刻のデータ型**</span><span class="sxs-lookup"><span data-stu-id="d6acd-142">**Date and Time Data Types**</span></span>  
  
|<span data-ttu-id="d6acd-143">データ型</span><span class="sxs-lookup"><span data-stu-id="d6acd-143">Data type</span></span>|<span data-ttu-id="d6acd-144">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d6acd-144">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="d6acd-145">date</span><span class="sxs-lookup"><span data-stu-id="d6acd-145">date</span></span>|[<span data-ttu-id="d6acd-146">date &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-146">date &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/date-transact-sql)|  
|<span data-ttu-id="d6acd-147">time</span><span class="sxs-lookup"><span data-stu-id="d6acd-147">time</span></span>|[<span data-ttu-id="d6acd-148">time &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-148">time &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/time-transact-sql)|  
|<span data-ttu-id="d6acd-149">DATETIME</span><span class="sxs-lookup"><span data-stu-id="d6acd-149">datetime</span></span>|[<span data-ttu-id="d6acd-150">datetime &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-150">datetime &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/datetime-transact-sql)|  
|<span data-ttu-id="d6acd-151">datetime2</span><span class="sxs-lookup"><span data-stu-id="d6acd-151">datetime2</span></span>|[<span data-ttu-id="d6acd-152">datetime2 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-152">datetime2 &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/datetime2-transact-sql)|  
|<span data-ttu-id="d6acd-153">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="d6acd-153">smalldatetime</span></span>|[<span data-ttu-id="d6acd-154">smalldatetime &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-154">smalldatetime &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 <span data-ttu-id="d6acd-155">**バイナリ データ型**</span><span class="sxs-lookup"><span data-stu-id="d6acd-155">**Binary Data Types**</span></span>  
  
|<span data-ttu-id="d6acd-156">データ型</span><span class="sxs-lookup"><span data-stu-id="d6acd-156">Data type</span></span>|<span data-ttu-id="d6acd-157">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d6acd-157">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="d6acd-158">bit</span><span class="sxs-lookup"><span data-stu-id="d6acd-158">bit</span></span>|[<span data-ttu-id="d6acd-159">bit &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-159">bit &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/bit-transact-sql)|  
|<span data-ttu-id="d6acd-160">binary(n)</span><span class="sxs-lookup"><span data-stu-id="d6acd-160">binary(n)</span></span>|[<span data-ttu-id="d6acd-161">binary と varbinary &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-161">binary and varbinary &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|<span data-ttu-id="d6acd-162">varbinary (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d6acd-162">varbinary(n) <sup>1</sup></span></span>|[<span data-ttu-id="d6acd-163">binary と varbinary &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-163">binary and varbinary &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <span data-ttu-id="d6acd-164"><sup>1</sup>行の合計で8060バイトの制限があり、可変長型の場合はカウント (n) です。</span><span class="sxs-lookup"><span data-stu-id="d6acd-164"><sup>1</sup> Limitation is 8060 bytes per row total, counting (n) in variable-length types.</span></span>  
  
 <span data-ttu-id="d6acd-165">**その他のデータ型**</span><span class="sxs-lookup"><span data-stu-id="d6acd-165">**Other data types**</span></span>  
  
|<span data-ttu-id="d6acd-166">データ型</span><span class="sxs-lookup"><span data-stu-id="d6acd-166">Data type</span></span>|<span data-ttu-id="d6acd-167">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d6acd-167">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="d6acd-168">UNIQUEIDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="d6acd-168">uniqueidentifier</span></span>|[<span data-ttu-id="d6acd-169">一意識別子 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d6acd-169">uniqueidentifier &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 <span data-ttu-id="d6acd-170">**サポートされていないデータ型**</span><span class="sxs-lookup"><span data-stu-id="d6acd-170">**Unsupported Data Types**</span></span>  
  
 <span data-ttu-id="d6acd-171">次のデータ型はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d6acd-171">The following data types are not supported:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="d6acd-172">DATETIMEOFFSET</span><span class="sxs-lookup"><span data-stu-id="d6acd-172">DATETIMEOFFSET</span></span>|<span data-ttu-id="d6acd-173">GEOGRAPHY</span><span class="sxs-lookup"><span data-stu-id="d6acd-173">GEOGRAPHY</span></span>|<span data-ttu-id="d6acd-174">GEOMETRY</span><span class="sxs-lookup"><span data-stu-id="d6acd-174">GEOMETRY</span></span>|  
|<span data-ttu-id="d6acd-175">HIERARCHYID</span><span class="sxs-lookup"><span data-stu-id="d6acd-175">HIERARCHYID</span></span>|<span data-ttu-id="d6acd-176">ラージ オブジェクト (LOB)。</span><span class="sxs-lookup"><span data-stu-id="d6acd-176">Large Objects (LOBs).</span></span> <span data-ttu-id="d6acd-177">例: varchar(max)、nvarchar(max)、varbinary(max)、image、xml、text、ntext。</span><span class="sxs-lookup"><span data-stu-id="d6acd-177">For example, varchar(max), nvarchar(max), varbinary(max), image, xml, text, and ntext.</span></span>|<span data-ttu-id="d6acd-178">ROWVERSION</span><span class="sxs-lookup"><span data-stu-id="d6acd-178">ROWVERSION</span></span>|  
|<span data-ttu-id="d6acd-179">sql_variant</span><span class="sxs-lookup"><span data-stu-id="d6acd-179">sql_variant</span></span>|<span data-ttu-id="d6acd-180">CLR 関数</span><span class="sxs-lookup"><span data-stu-id="d6acd-180">CLR functions</span></span>|<span data-ttu-id="d6acd-181">UDT (ユーザー定義型)</span><span class="sxs-lookup"><span data-stu-id="d6acd-181">User-defined types (UDTs)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6acd-182">参照</span><span class="sxs-lookup"><span data-stu-id="d6acd-182">See Also</span></span>  
 <span data-ttu-id="d6acd-183">[Transact-SQL によるインメモリ OLTP のサポート](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="d6acd-183">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="d6acd-184">[メモリ最適化テーブルへの LOB 列の実装](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md) </span><span class="sxs-lookup"><span data-stu-id="d6acd-184">[Implementing LOB Columns in a Memory-Optimized Table](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md) </span></span>  
 [<span data-ttu-id="d6acd-185">メモリ最適化テーブルへの SQL_VARIANT の実装</span><span class="sxs-lookup"><span data-stu-id="d6acd-185">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
