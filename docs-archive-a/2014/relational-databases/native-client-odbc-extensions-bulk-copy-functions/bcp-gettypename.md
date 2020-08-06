---
title: bcp_gettypename |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: rothja
ms.author: jroth
ms.openlocfilehash: b2d92498b9d863fa2cb700ec4d88868c0984c4d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634517"
---
# <a name="bcp_gettypename"></a><span data-ttu-id="21e47-102">bcp_gettypename</span><span class="sxs-lookup"><span data-stu-id="21e47-102">bcp_gettypename</span></span>
  <span data-ttu-id="21e47-103">指定された BCP 型トークンの SQL 型名を返します。</span><span class="sxs-lookup"><span data-stu-id="21e47-103">Returns the SQL type name for a specified BCP type token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e47-104">構文</span><span class="sxs-lookup"><span data-stu-id="21e47-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="21e47-105">引数</span><span class="sxs-lookup"><span data-stu-id="21e47-105">Arguments</span></span>  
 <span data-ttu-id="21e47-106">*token*</span><span class="sxs-lookup"><span data-stu-id="21e47-106">*token*</span></span>  
 <span data-ttu-id="21e47-107">BCP 型トークンを示す値です。</span><span class="sxs-lookup"><span data-stu-id="21e47-107">A value indicating a BCP type token.</span></span>  
  
 <span data-ttu-id="21e47-108">*分野*</span><span class="sxs-lookup"><span data-stu-id="21e47-108">*field*</span></span>  
 <span data-ttu-id="21e47-109">要求されたトークンが max 型かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="21e47-109">Indicates if token requested is a max type.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="21e47-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="21e47-110">Returns</span></span>  
 <span data-ttu-id="21e47-111">BCP 型に対応する SQL 型名を含む文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="21e47-111">A string containing the SQL type name corresponding to the BCP type.</span></span> <span data-ttu-id="21e47-112">無効な BCP 型が指定されると、空文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="21e47-112">If an invalid BCP type is specified, an empty string is returned..</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21e47-113">解説</span><span class="sxs-lookup"><span data-stu-id="21e47-113">Remarks</span></span>  
 <span data-ttu-id="21e47-114">BCP 型トークンは、sqlncli.h ヘッダー ファイルと sqlncli11.lib ライブラリで定義されています。</span><span class="sxs-lookup"><span data-stu-id="21e47-114">The BCP type tokens are defined in the sqlncli.h header file and the sqlncli11.lib library.</span></span>  
  
 <span data-ttu-id="21e47-115">次の表では、指定できる BCP 型、それらの BCP 型が max 型かどうか、および予想される出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="21e47-115">The table below specifies the possible BCP types, whether or not they are max types, and the expected output.</span></span>  
  
|<span data-ttu-id="21e47-116">BCP 型名</span><span class="sxs-lookup"><span data-stu-id="21e47-116">BCP type name</span></span>|<span data-ttu-id="21e47-117">MaxType</span><span class="sxs-lookup"><span data-stu-id="21e47-117">MaxType</span></span>|<span data-ttu-id="21e47-118">出力</span><span class="sxs-lookup"><span data-stu-id="21e47-118">Output</span></span>|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|<span data-ttu-id="21e47-119">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-119">Either</span></span>|<span data-ttu-id="21e47-120">**decimal**</span><span class="sxs-lookup"><span data-stu-id="21e47-120">**decimal**</span></span>|  
|`SQLNUMERIC`|<span data-ttu-id="21e47-121">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-121">Either</span></span>|<span data-ttu-id="21e47-122">**numeric**</span><span class="sxs-lookup"><span data-stu-id="21e47-122">**numeric**</span></span>|  
|`SQLINT1`|<span data-ttu-id="21e47-123">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-123">Either</span></span>|<span data-ttu-id="21e47-124">**tinyint**</span><span class="sxs-lookup"><span data-stu-id="21e47-124">**tinyint**</span></span>|  
|`SQLINT2`|<span data-ttu-id="21e47-125">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-125">Either</span></span>|<span data-ttu-id="21e47-126">**smallint**</span><span class="sxs-lookup"><span data-stu-id="21e47-126">**smallint**</span></span>|  
|`SQLINT4`|<span data-ttu-id="21e47-127">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-127">Either</span></span>|<span data-ttu-id="21e47-128">**int**</span><span class="sxs-lookup"><span data-stu-id="21e47-128">**int**</span></span>|  
|`SQLMONEY`|<span data-ttu-id="21e47-129">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-129">Either</span></span>|<span data-ttu-id="21e47-130">**money**</span><span class="sxs-lookup"><span data-stu-id="21e47-130">**money**</span></span>|  
|`SQLFLT8`|<span data-ttu-id="21e47-131">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-131">Either</span></span>|<span data-ttu-id="21e47-132">**float**</span><span class="sxs-lookup"><span data-stu-id="21e47-132">**float**</span></span>|  
|`SQLDATETIME`|<span data-ttu-id="21e47-133">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-133">Either</span></span>|<span data-ttu-id="21e47-134">**datetime**</span><span class="sxs-lookup"><span data-stu-id="21e47-134">**datetime**</span></span>|  
|`SQLBITN`|<span data-ttu-id="21e47-135">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-135">Either</span></span>|<span data-ttu-id="21e47-136">**bit-null**</span><span class="sxs-lookup"><span data-stu-id="21e47-136">**bit-null**</span></span>|  
|`SQLBIT`|<span data-ttu-id="21e47-137">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-137">Either</span></span>|<span data-ttu-id="21e47-138">**bit**</span><span class="sxs-lookup"><span data-stu-id="21e47-138">**bit**</span></span>|  
|`SQLBIGCHAR`|<span data-ttu-id="21e47-139">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-139">No</span></span>|<span data-ttu-id="21e47-140">**char**</span><span class="sxs-lookup"><span data-stu-id="21e47-140">**char**</span></span>|  
|`SQLCHARACTER`|<span data-ttu-id="21e47-141">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-141">No</span></span>|<span data-ttu-id="21e47-142">**char**</span><span class="sxs-lookup"><span data-stu-id="21e47-142">**char**</span></span>|  
|`SQLBIGVARCHAR`|<span data-ttu-id="21e47-143">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-143">No</span></span>|<span data-ttu-id="21e47-144">**varchar**</span><span class="sxs-lookup"><span data-stu-id="21e47-144">**varchar**</span></span>|  
|`SQLVARCHAR`|<span data-ttu-id="21e47-145">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-145">No</span></span>|<span data-ttu-id="21e47-146">**varchar**</span><span class="sxs-lookup"><span data-stu-id="21e47-146">**varchar**</span></span>|  
|`SQLTEXT`|<span data-ttu-id="21e47-147">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-147">Either</span></span>|<span data-ttu-id="21e47-148">**text**</span><span class="sxs-lookup"><span data-stu-id="21e47-148">**text**</span></span>|  
|`SQLBIGBINARY`|<span data-ttu-id="21e47-149">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-149">No</span></span>|<span data-ttu-id="21e47-150">**[バイナリ]**</span><span class="sxs-lookup"><span data-stu-id="21e47-150">**binary**</span></span>|  
|`SQLBINARY`|<span data-ttu-id="21e47-151">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-151">No</span></span>|<span data-ttu-id="21e47-152">**Binary**</span><span class="sxs-lookup"><span data-stu-id="21e47-152">**Binary**</span></span>|  
|`SQLBIGVARBINARY`|<span data-ttu-id="21e47-153">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-153">No</span></span>|<span data-ttu-id="21e47-154">**可変長**</span><span class="sxs-lookup"><span data-stu-id="21e47-154">**Varbinary**</span></span>|  
|`SQLVARBINARY`|<span data-ttu-id="21e47-155">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-155">No</span></span>|<span data-ttu-id="21e47-156">**可変長**</span><span class="sxs-lookup"><span data-stu-id="21e47-156">**Varbinary**</span></span>|  
|`SQLIMAGE`|<span data-ttu-id="21e47-157">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-157">Either</span></span>|<span data-ttu-id="21e47-158">**イメージ**</span><span class="sxs-lookup"><span data-stu-id="21e47-158">**Image**</span></span>|  
|`SQLINTN`|<span data-ttu-id="21e47-159">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-159">Either</span></span>|<span data-ttu-id="21e47-160">**int-null**</span><span class="sxs-lookup"><span data-stu-id="21e47-160">**int-null**</span></span>|  
|`SQLDATETIMN`|<span data-ttu-id="21e47-161">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-161">Either</span></span>|<span data-ttu-id="21e47-162">**datetime-null**</span><span class="sxs-lookup"><span data-stu-id="21e47-162">**datetime-null**</span></span>|  
|`SQLMONEYN`|<span data-ttu-id="21e47-163">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-163">Either</span></span>|<span data-ttu-id="21e47-164">**money-null**</span><span class="sxs-lookup"><span data-stu-id="21e47-164">**money-null**</span></span>|  
|`SQLFLTN`|<span data-ttu-id="21e47-165">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-165">Either</span></span>|<span data-ttu-id="21e47-166">**float-null**</span><span class="sxs-lookup"><span data-stu-id="21e47-166">**float-null**</span></span>|  
|`SQLAOPSUM`|<span data-ttu-id="21e47-167">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-167">Either</span></span>|<span data-ttu-id="21e47-168">**SUM**</span><span class="sxs-lookup"><span data-stu-id="21e47-168">**Sum**</span></span>|  
|`SQLAOPAVG`|<span data-ttu-id="21e47-169">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-169">Either</span></span>|<span data-ttu-id="21e47-170">**Avg**</span><span class="sxs-lookup"><span data-stu-id="21e47-170">**Avg**</span></span>|  
|`SQLAOPCNT`|<span data-ttu-id="21e47-171">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-171">Either</span></span>|<span data-ttu-id="21e47-172">**Count**</span><span class="sxs-lookup"><span data-stu-id="21e47-172">**Count**</span></span>|  
|`SQLAOPMIN`|<span data-ttu-id="21e47-173">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-173">Either</span></span>|<span data-ttu-id="21e47-174">**」**</span><span class="sxs-lookup"><span data-stu-id="21e47-174">**Min**</span></span>|  
|`SQLAOPMAX`|<span data-ttu-id="21e47-175">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-175">Either</span></span>|<span data-ttu-id="21e47-176">**制限**</span><span class="sxs-lookup"><span data-stu-id="21e47-176">**Max**</span></span>|  
|`SQLDATETIM4`|<span data-ttu-id="21e47-177">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-177">Either</span></span>|<span data-ttu-id="21e47-178">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="21e47-178">**smalldatetime**</span></span>|  
|`SQLMONEY4`|<span data-ttu-id="21e47-179">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-179">Either</span></span>|<span data-ttu-id="21e47-180">**Smallmoney**</span><span class="sxs-lookup"><span data-stu-id="21e47-180">**Smallmoney**</span></span>|  
|`SQLFLT4`|<span data-ttu-id="21e47-181">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-181">Either</span></span>|<span data-ttu-id="21e47-182">**本当の**</span><span class="sxs-lookup"><span data-stu-id="21e47-182">**Real**</span></span>|  
|`SQLUNIQUEID`|<span data-ttu-id="21e47-183">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-183">Either</span></span>|<span data-ttu-id="21e47-184">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="21e47-184">**uniqueidentifier**</span></span>|  
|`SQLNCHAR`|<span data-ttu-id="21e47-185">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-185">No</span></span>|<span data-ttu-id="21e47-186">**Nchar**</span><span class="sxs-lookup"><span data-stu-id="21e47-186">**Nchar**</span></span>|  
|`SQLNVARCHAR`|<span data-ttu-id="21e47-187">いいえ</span><span class="sxs-lookup"><span data-stu-id="21e47-187">No</span></span>|<span data-ttu-id="21e47-188">**Nvarchar**</span><span class="sxs-lookup"><span data-stu-id="21e47-188">**Nvarchar**</span></span>|  
|`SQLNTEXT`|<span data-ttu-id="21e47-189">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-189">Either</span></span>|<span data-ttu-id="21e47-190">**Ntext**</span><span class="sxs-lookup"><span data-stu-id="21e47-190">**Ntext**</span></span>|  
|`SQLVARIANT`|<span data-ttu-id="21e47-191">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-191">Either</span></span>|<span data-ttu-id="21e47-192">**sql_variant**</span><span class="sxs-lookup"><span data-stu-id="21e47-192">**sql_variant**</span></span>|  
|`SQLINT8`|<span data-ttu-id="21e47-193">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-193">Either</span></span>|<span data-ttu-id="21e47-194">**Bigint**</span><span class="sxs-lookup"><span data-stu-id="21e47-194">**Bigint**</span></span>|  
|`SQLCHARACTER`|<span data-ttu-id="21e47-195">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-195">Yes</span></span>|<span data-ttu-id="21e47-196">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-196">**varchar(max)**</span></span>|  
|`SQLBIGCHAR`|<span data-ttu-id="21e47-197">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-197">Yes</span></span>|<span data-ttu-id="21e47-198">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-198">**varchar(max)**</span></span>|  
|`SQLBIGVARCHAR`|<span data-ttu-id="21e47-199">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-199">Yes</span></span>|<span data-ttu-id="21e47-200">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-200">**varchar(max)**</span></span>|  
|`SQLVARCHAR`|<span data-ttu-id="21e47-201">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-201">Yes</span></span>|<span data-ttu-id="21e47-202">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-202">**varchar(max)**</span></span>|  
|`SQLBINARY`|<span data-ttu-id="21e47-203">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-203">Yes</span></span>|<span data-ttu-id="21e47-204">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-204">**varbinary(max)**</span></span>|  
|`SQLBIGBINARY`|<span data-ttu-id="21e47-205">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-205">Yes</span></span>|<span data-ttu-id="21e47-206">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-206">**varbinary(max)**</span></span>|  
|`SQLBIGVARBINARY`|<span data-ttu-id="21e47-207">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-207">Yes</span></span>|<span data-ttu-id="21e47-208">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-208">**varbinary(max)**</span></span>|  
|`SQLVARBINARY`|<span data-ttu-id="21e47-209">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-209">Yes</span></span>|<span data-ttu-id="21e47-210">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-210">**varbinary(max)**</span></span>|  
|`SQLNCHAR`|<span data-ttu-id="21e47-211">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-211">Yes</span></span>|<span data-ttu-id="21e47-212">**nvarchar(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-212">**nvarchar(max)**</span></span>|  
|`SQLNVARCHAR`|<span data-ttu-id="21e47-213">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-213">Yes</span></span>|<span data-ttu-id="21e47-214">**nvarchar(max)**</span><span class="sxs-lookup"><span data-stu-id="21e47-214">**nvarchar(max)**</span></span>|  
|`SQLXML`|<span data-ttu-id="21e47-215">はい</span><span class="sxs-lookup"><span data-stu-id="21e47-215">Yes</span></span>|<span data-ttu-id="21e47-216">**Xml**</span><span class="sxs-lookup"><span data-stu-id="21e47-216">**Xml**</span></span>|  
|`SQLUDT`|<span data-ttu-id="21e47-217">接続前/接続後</span><span class="sxs-lookup"><span data-stu-id="21e47-217">Either</span></span>|<span data-ttu-id="21e47-218">**Udt**</span><span class="sxs-lookup"><span data-stu-id="21e47-218">**Udt**</span></span>|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="21e47-219">bcp_gettypename による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="21e47-219">bcp_gettypename Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="21e47-220">日付/時刻型のトークンパラメーター値については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付と時刻の型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21e47-220">The token parameter values for date/time types are described in the "Type in sqlncli.h" column of the table in [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span> <span data-ttu-id="21e47-221">返される値は、対応する行の "ファイル ストレージ型" 列に示されています。</span><span class="sxs-lookup"><span data-stu-id="21e47-221">The returned value is in the corresponding row of the "File storage type" column.</span></span>  
  
 <span data-ttu-id="21e47-222">詳細については、「[日付と時刻の機能強化 &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21e47-222">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e47-223">参照</span><span class="sxs-lookup"><span data-stu-id="21e47-223">See Also</span></span>  
 [<span data-ttu-id="21e47-224">一括コピー関数</span><span class="sxs-lookup"><span data-stu-id="21e47-224">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
