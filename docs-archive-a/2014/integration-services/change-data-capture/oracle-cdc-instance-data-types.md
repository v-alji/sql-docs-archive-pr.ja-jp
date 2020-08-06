---
title: Oracle CDC インスタンスのデータ型 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 71d4ce02db89c1bfd11fe9a3a3535fc92fbc49fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712274"
---
# <a name="oracle-cdc-instance-data-types"></a><span data-ttu-id="555ec-102">Oracle CDC インスタンスのデータ型</span><span class="sxs-lookup"><span data-stu-id="555ec-102">Oracle CDC Instance Data Types</span></span>
  <span data-ttu-id="555ec-103">Oracle CDC インスタンスでは、ほとんどの Oracle データ型がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="555ec-103">The Oracle CDC Instance supports most Oracle data types.</span></span> <span data-ttu-id="555ec-104">次のセクションでは、サポートされるデータ型とサポートされないデータ型について説明します。</span><span class="sxs-lookup"><span data-stu-id="555ec-104">The following sections describe the supported data types and the non-supported data types.</span></span>  
  
## <a name="supported-data-types"></a><span data-ttu-id="555ec-105">サポートされるデータ型</span><span class="sxs-lookup"><span data-stu-id="555ec-105">Supported Data Types</span></span>  
 <span data-ttu-id="555ec-106">次の表では、キャプチャできる Oracle データ型と、変更テーブルの SQL Server データ型に対する既定のマッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="555ec-106">The following table describes the Oracle data types that can be captured and their default mapping to SQL Server data types in the change tables.</span></span> <span data-ttu-id="555ec-107">ソース Oracle テーブルにキャプチャ インスタンスを追加するときは、これらのマッピングをオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="555ec-107">When adding a capture instance for a source Oracle table, you can override some of these mappings.</span></span>  
  
|<span data-ttu-id="555ec-108">Oracle データベース データ型</span><span class="sxs-lookup"><span data-stu-id="555ec-108">Oracle Database Data Type</span></span>|<span data-ttu-id="555ec-109">SQL Server データ型</span><span class="sxs-lookup"><span data-stu-id="555ec-109">SQL Server Data Type</span></span>|  
|-------------------------------|--------------------------|  
|<span data-ttu-id="555ec-110">BINARY_FLOAT</span><span class="sxs-lookup"><span data-stu-id="555ec-110">BINARY_FLOAT</span></span>|<span data-ttu-id="555ec-111">real</span><span class="sxs-lookup"><span data-stu-id="555ec-111">REAL</span></span>|  
|<span data-ttu-id="555ec-112">BINARY_DOUBLE</span><span class="sxs-lookup"><span data-stu-id="555ec-112">BINARY_DOUBLE</span></span>|<span data-ttu-id="555ec-113">FLOAT</span><span class="sxs-lookup"><span data-stu-id="555ec-113">FLOAT</span></span>|  
|<span data-ttu-id="555ec-114">CHAR</span><span class="sxs-lookup"><span data-stu-id="555ec-114">CHAR</span></span>|<span data-ttu-id="555ec-115">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="555ec-115">NVARCHAR</span></span>|  
|<span data-ttu-id="555ec-116">DATE</span><span class="sxs-lookup"><span data-stu-id="555ec-116">DATE</span></span>|<span data-ttu-id="555ec-117">DATETIME</span><span class="sxs-lookup"><span data-stu-id="555ec-117">DATETIME</span></span>|  
|<span data-ttu-id="555ec-118">FLOAT</span><span class="sxs-lookup"><span data-stu-id="555ec-118">FLOAT</span></span>|<span data-ttu-id="555ec-119">FLOAT</span><span class="sxs-lookup"><span data-stu-id="555ec-119">FLOAT</span></span>|  
|<span data-ttu-id="555ec-120">INT</span><span class="sxs-lookup"><span data-stu-id="555ec-120">INT</span></span>|<span data-ttu-id="555ec-121">NUMERIC (38)</span><span class="sxs-lookup"><span data-stu-id="555ec-121">NUMERIC (38)</span></span>|  
|<span data-ttu-id="555ec-122">INTERVAL</span><span class="sxs-lookup"><span data-stu-id="555ec-122">INTERVAL</span></span>|<span data-ttu-id="555ec-123">DATETIME</span><span class="sxs-lookup"><span data-stu-id="555ec-123">DATETIME</span></span>|  
|<span data-ttu-id="555ec-124">NCHAR</span><span class="sxs-lookup"><span data-stu-id="555ec-124">NCHAR</span></span>|<span data-ttu-id="555ec-125">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="555ec-125">NVARCHAR</span></span>|  
|<span data-ttu-id="555ec-126">NUMBER</span><span class="sxs-lookup"><span data-stu-id="555ec-126">NUMBER</span></span>|<span data-ttu-id="555ec-127">FLOAT</span><span class="sxs-lookup"><span data-stu-id="555ec-127">FLOAT</span></span>|  
|<span data-ttu-id="555ec-128">NAVARCHAR2</span><span class="sxs-lookup"><span data-stu-id="555ec-128">NAVARCHAR2</span></span>|<span data-ttu-id="555ec-129">NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="555ec-129">NVARCHAR</span></span>|  
|<span data-ttu-id="555ec-130">RAW</span><span class="sxs-lookup"><span data-stu-id="555ec-130">RAW</span></span>|<span data-ttu-id="555ec-131">VARBINARY</span><span class="sxs-lookup"><span data-stu-id="555ec-131">VARBINARY</span></span>|  
|<span data-ttu-id="555ec-132">real</span><span class="sxs-lookup"><span data-stu-id="555ec-132">REAL</span></span>|<span data-ttu-id="555ec-133">FLOAT</span><span class="sxs-lookup"><span data-stu-id="555ec-133">FLOAT</span></span>|  
|<span data-ttu-id="555ec-134">timestamp</span><span class="sxs-lookup"><span data-stu-id="555ec-134">TIMESTAMP</span></span>|<span data-ttu-id="555ec-135">DATETIME2</span><span class="sxs-lookup"><span data-stu-id="555ec-135">DATETIME2</span></span>|  
|<span data-ttu-id="555ec-136">TIMESTAMP WITH TIME ZONE</span><span class="sxs-lookup"><span data-stu-id="555ec-136">TIMESTAMP WITH TIME ZONE</span></span>|<span data-ttu-id="555ec-137">VARCHAR (37)</span><span class="sxs-lookup"><span data-stu-id="555ec-137">VARCHAR (37)</span></span>|  
|<span data-ttu-id="555ec-138">TIMESTAMP WITH LOCAL TIME ZONE</span><span class="sxs-lookup"><span data-stu-id="555ec-138">TIMESTAMP WITH LOCAL TIME ZONE</span></span>|<span data-ttu-id="555ec-139">VARCHAR (37)</span><span class="sxs-lookup"><span data-stu-id="555ec-139">VARCHAR (37)</span></span>|  
|<span data-ttu-id="555ec-140">VARCHAR2</span><span class="sxs-lookup"><span data-stu-id="555ec-140">VARCHAR2</span></span>|<span data-ttu-id="555ec-141">VARCHAR</span><span class="sxs-lookup"><span data-stu-id="555ec-141">VARCHAR</span></span>|  
|<span data-ttu-id="555ec-142">XMLTYPE</span><span class="sxs-lookup"><span data-stu-id="555ec-142">XMLTYPE</span></span>|<span data-ttu-id="555ec-143">NVARCHAR (MAX)</span><span class="sxs-lookup"><span data-stu-id="555ec-143">NVARCHAR (MAX)</span></span>|  
  
## <a name="non-supported-data-types"></a><span data-ttu-id="555ec-144">サポートされないデータ型</span><span class="sxs-lookup"><span data-stu-id="555ec-144">Non-Supported Data Types</span></span>  
 <span data-ttu-id="555ec-145">次の Oracle データ型の列を含むソース Oracle テーブルはキャプチャできません。</span><span class="sxs-lookup"><span data-stu-id="555ec-145">Source Oracle tables with columns of the following Oracle data types cannot be captured.</span></span> <span data-ttu-id="555ec-146">これらのデータ型を含むキャプチャ対象列は NULL として表示されます。ただし、これらの値の変更は、キャプチャ対象テーブルの変更マスクに示されます。</span><span class="sxs-lookup"><span data-stu-id="555ec-146">Captured columns with these data types will show as null; however, a change in their value is indicated in the change mask of the captured tables.</span></span>  
  
-   <span data-ttu-id="555ec-147">LONG</span><span class="sxs-lookup"><span data-stu-id="555ec-147">LONG</span></span>  
  
-   <span data-ttu-id="555ec-148">XMLTYPE</span><span class="sxs-lookup"><span data-stu-id="555ec-148">XMLTYPE</span></span>  
  
-   <span data-ttu-id="555ec-149">BLOB</span><span class="sxs-lookup"><span data-stu-id="555ec-149">BLOB</span></span>  
  
-   <span data-ttu-id="555ec-150">CLOB</span><span class="sxs-lookup"><span data-stu-id="555ec-150">CLOB</span></span>  
  
 <span data-ttu-id="555ec-151">次の Oracle データ型の列を含むソース Oracle テーブルはキャプチャできません。</span><span class="sxs-lookup"><span data-stu-id="555ec-151">Source Oracle tables with columns of the following Oracle data types cannot be captured.</span></span>  
  
-   <span data-ttu-id="555ec-152">BFILE</span><span class="sxs-lookup"><span data-stu-id="555ec-152">BFILE</span></span>  
  
-   <span data-ttu-id="555ec-153">ROWID</span><span class="sxs-lookup"><span data-stu-id="555ec-153">ROWID</span></span>  
  
-   <span data-ttu-id="555ec-154">REF</span><span class="sxs-lookup"><span data-stu-id="555ec-154">REF</span></span>  
  
-   <span data-ttu-id="555ec-155">UROWID</span><span class="sxs-lookup"><span data-stu-id="555ec-155">UROWID</span></span>  
  
-   <span data-ttu-id="555ec-156">入れ子になったテーブル</span><span class="sxs-lookup"><span data-stu-id="555ec-156">Nested Table</span></span>  
  
 <span data-ttu-id="555ec-157">テーブルに次のデータ型が存在する場合、LogMinder はそのテーブルの列のデータを取得できません。</span><span class="sxs-lookup"><span data-stu-id="555ec-157">If the following data types are present in a table they will prevent the LogMinder from getting any data for any column of the table:</span></span>  
  
-   <span data-ttu-id="555ec-158">ユーザー定義データ型</span><span class="sxs-lookup"><span data-stu-id="555ec-158">User-defined data types</span></span>  
  
-   <span data-ttu-id="555ec-159">VARRAY</span><span class="sxs-lookup"><span data-stu-id="555ec-159">VARRAY</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="555ec-160">参照</span><span class="sxs-lookup"><span data-stu-id="555ec-160">See Also</span></span>  
 <span data-ttu-id="555ec-161">[Attunity の Change Data Capture Designer for Oracle](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="555ec-161">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="555ec-162">Oracle CDC インスタンス</span><span class="sxs-lookup"><span data-stu-id="555ec-162">The Oracle CDC Instance</span></span>](the-oracle-cdc-instance.md)  
  
  
