---
title: インデックスのディスク領域の例 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- online index disk space
- disk space [SQL Server], indexes
- index disk space [SQL Server]
- space [SQL Server], indexes
- indexes [SQL Server], disk space requirements
- offline index disk space [SQL Server]
ms.assetid: e5c71f55-0be3-4c93-97e9-7b3455c8f581
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4a30c6ce986095496a11c41f3102d095e8c632b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640940"
---
# <a name="index-disk-space-example"></a><span data-ttu-id="6ba90-102">インデックスのディスク領域の例</span><span class="sxs-lookup"><span data-stu-id="6ba90-102">Index Disk Space Example</span></span>
  <span data-ttu-id="6ba90-103">インデックスを作成、再構築、または削除する場合は、古い (基になる) 構造と新しい (対象となる) 構造の両方を格納するディスク領域が、それぞれ適切なファイルとファイル グループで必要になります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-103">Whenever an index is created, rebuilt, or dropped, disk space for both the old (source) and new (target) structures is required in their appropriate files and filegroups.</span></span> <span data-ttu-id="6ba90-104">古い構造の割り当ては、インデックス作成トランザクションがコミットされるまで解除されません。</span><span class="sxs-lookup"><span data-stu-id="6ba90-104">The old structure is not deallocated until the index creation transaction commits.</span></span> <span data-ttu-id="6ba90-105">並べ替え操作用に一時ディスク領域が追加で必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-105">Additional temporary disk space for sorting operations may also be needed.</span></span> <span data-ttu-id="6ba90-106">詳細については、「 [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="6ba90-106">For more information, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
 <span data-ttu-id="6ba90-107">この例では、クラスター化インデックスを作成するために必要なディスク領域を判断します。</span><span class="sxs-lookup"><span data-stu-id="6ba90-107">In this example, disk space requirements to create a clustered index are determined.</span></span>  
  
 <span data-ttu-id="6ba90-108">ここでは、クラスター化インデックスを作成する前の状態が、以下のとおりであるとします。</span><span class="sxs-lookup"><span data-stu-id="6ba90-108">Assume the following conditions are true before creating the clustered index:</span></span>  
  
-   <span data-ttu-id="6ba90-109">既存のテーブル (ヒープ) には、100 万行が含まれている。</span><span class="sxs-lookup"><span data-stu-id="6ba90-109">The existing table (heap) contains 1 million rows.</span></span> <span data-ttu-id="6ba90-110">各行の長さは 200 バイトである。</span><span class="sxs-lookup"><span data-stu-id="6ba90-110">Each row is 200 bytes long.</span></span>  
  
-   <span data-ttu-id="6ba90-111">非クラスター化インデックス A には、100 万行が含まれている。</span><span class="sxs-lookup"><span data-stu-id="6ba90-111">Nonclustered index A contains 1 million rows.</span></span> <span data-ttu-id="6ba90-112">各行の長さは 50 バイトである。</span><span class="sxs-lookup"><span data-stu-id="6ba90-112">Each row is 50 bytes long.</span></span>  
  
-   <span data-ttu-id="6ba90-113">非クラスター化インデックス B には、100 万行が含まれている。</span><span class="sxs-lookup"><span data-stu-id="6ba90-113">Nonclustered index B contains 1 million rows.</span></span> <span data-ttu-id="6ba90-114">各行の長さは 80 バイトである。</span><span class="sxs-lookup"><span data-stu-id="6ba90-114">Each row is 80 bytes long.</span></span>  
  
-   <span data-ttu-id="6ba90-115">index create memory オプションは、2 MB に設定されている。</span><span class="sxs-lookup"><span data-stu-id="6ba90-115">The index create memory option is set to 2 MB.</span></span>  
  
-   <span data-ttu-id="6ba90-116">既存のインデックスと新しいインデックスのすべてに、FILL FACTOR 値として 80 が使用される。</span><span class="sxs-lookup"><span data-stu-id="6ba90-116">A fill factor value of 80 is used for all existing and new indexes.</span></span> <span data-ttu-id="6ba90-117">つまり、ページの使用率が 80% になります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-117">This means the pages are 80 percent full.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6ba90-118">クラスター化インデックスを作成した結果、行インジケーターを新しいクラスター化インデックス キーに置き換えるために、2 つの非クラスター化インデックスを再構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-118">As a result of creating a clustered index, the two nonclustered indexes must be rebuilt to replace the row indicator with the new clustered index key.</span></span>  
  
## <a name="disk-space-calculations-for-an-offline-index-operation"></a><span data-ttu-id="6ba90-119">オフライン インデックス操作に必要なディスク領域の計算</span><span class="sxs-lookup"><span data-stu-id="6ba90-119">Disk Space Calculations for an Offline Index Operation</span></span>  
 <span data-ttu-id="6ba90-120">以下の手順では、インデックス操作中に使用する一時ディスク領域と、新しいインデックスを格納する永続的なディスク領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="6ba90-120">In the following steps, both temporary disk space to be used during the index operation and permanent disk space to store the new indexes are calculated.</span></span> <span data-ttu-id="6ba90-121">ここでの計算は概算です。結果は切り上げ、インデックスのリーフ レベルのサイズしか計算しません。</span><span class="sxs-lookup"><span data-stu-id="6ba90-121">The calculations shown are approximate; results are rounded up and consider only the size of index leaf level.</span></span> <span data-ttu-id="6ba90-122">概算値には、チルダ (~) を付けています。</span><span class="sxs-lookup"><span data-stu-id="6ba90-122">The tilde (~) is used to indicate approximate calculations.</span></span>  
  
1.  <span data-ttu-id="6ba90-123">基になる構造のサイズを判断します。</span><span class="sxs-lookup"><span data-stu-id="6ba90-123">Determine the size of the source structures.</span></span>  
  
     <span data-ttu-id="6ba90-124">ヒープ : 100 万行 \* 200 バイト ~ 200 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-124">Heap: 1 million \* 200 bytes ~ 200 MB</span></span>  
  
     <span data-ttu-id="6ba90-125">非クラスター化インデックス A : 100 万行 \* 50 バイト / 80% ~ 63 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-125">Nonclustered index A: 1 million \* 50 bytes / 80% ~ 63 MB</span></span>  
  
     <span data-ttu-id="6ba90-126">非クラスター化インデックス B : 100 万行 \* 80 バイト / 80% ~ 100 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-126">Nonclustered index B: 1 million \* 80 bytes / 80% ~ 100 MB</span></span>  
  
     <span data-ttu-id="6ba90-127">既存の構造の合計サイズ : 363 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-127">Total size of existing structures: 363 MB</span></span>  
  
2.  <span data-ttu-id="6ba90-128">対象となるインデックス構造のサイズを判断します。</span><span class="sxs-lookup"><span data-stu-id="6ba90-128">Determine the size of the target index structures.</span></span> <span data-ttu-id="6ba90-129">新しいクラスター化キーは、uniqueifier も含めて 24 バイトとします。</span><span class="sxs-lookup"><span data-stu-id="6ba90-129">Assume that the new clustered key is 24 bytes long including a uniqueifier.</span></span> <span data-ttu-id="6ba90-130">どちらの非クラスター化インデックスの行インジケーター (8 バイト長) も、このクラスター化キーに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="6ba90-130">The row indicator (8 bytes long) in both nonclustered indexes will be replaced by this clustered key.</span></span>  
  
     <span data-ttu-id="6ba90-131">クラスター化インデックス : 100 万行 \* 200 バイト / 80% ~ 250 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-131">Clustered index: 1 million \* 200 bytes / 80% ~ 250 MB</span></span>  
  
     <span data-ttu-id="6ba90-132">非クラスター化インデックス A : 100 万行 \* (50 - 8 + 24) バイト / 80% ~ 83 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-132">Nonclustered index A: 1 million \* (50 - 8 + 24) bytes / 80% ~ 83 MB</span></span>  
  
     <span data-ttu-id="6ba90-133">非クラスター化インデックス B : 100 万行 \* (80 - 8 + 24) バイト / 80% ~ 120 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-133">Nonclustered index B: 1 million \* (80 - 8 + 24) bytes / 80% ~ 120 MB</span></span>  
  
     <span data-ttu-id="6ba90-134">新しい構造の合計サイズ : 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-134">Total size of new structures: 453 MB</span></span>  
  
     <span data-ttu-id="6ba90-135">基になる構造と対象の構造の両方をサポートするために、インデックス操作中に必要な合計のディスク領域は、816 MB (363 + 453) です。</span><span class="sxs-lookup"><span data-stu-id="6ba90-135">Total disk space required to support both the source and target structures for the duration of the index operation is 816 MB (363 + 453).</span></span> <span data-ttu-id="6ba90-136">現在基になる構造に割り当てられている領域は、インデックス操作がコミットされると、割り当てが解除されます</span><span class="sxs-lookup"><span data-stu-id="6ba90-136">The space currently allocated to the source structures will be deallocated after the index operation is committed.</span></span>  
  
3.  <span data-ttu-id="6ba90-137">並べ替え用の追加の一時ディスク領域を判断します。</span><span class="sxs-lookup"><span data-stu-id="6ba90-137">Determine additional temporary disk space for sorting.</span></span>  
  
     <span data-ttu-id="6ba90-138">**tempdb** での並べ替え (SORT_IN_TEMPDB を ON に設定) と、対象の場所での並べ替え (SORT_IN_TEMPDB を OFF に設定) に必要な領域を示します。</span><span class="sxs-lookup"><span data-stu-id="6ba90-138">Space requirements are shown for sorting in **tempdb** (with SORT_IN_TEMPDB set to ON) and sorting in the target location (with SORT_IN_TEMPDB set to OFF).</span></span>  
  
    1.  <span data-ttu-id="6ba90-139">SORT_IN_TEMPDB が ON の場合、 **tempdb** には最大のインデックス (100 万行 \* 200 バイト ～ 200 MB) を格納できるだけのディスク領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="6ba90-139">When SORT_IN_TEMPDB is set to ON, **tempdb** must have sufficient disk space to hold the largest index (1 million \* 200 bytes ~ 200 MB).</span></span> <span data-ttu-id="6ba90-140">並べ替え操作では、FILL FACTOR については考慮されません。</span><span class="sxs-lookup"><span data-stu-id="6ba90-140">Fill factor is not considered in the sorting operation.</span></span>  
  
         <span data-ttu-id="6ba90-141">追加のディスク領域 ( **tempdb** の場所内) は [index create memory サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) の値 (= 2 MB) と同じです。</span><span class="sxs-lookup"><span data-stu-id="6ba90-141">Additional disk space (in the **tempdb** location) equal to the [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) value = 2 MB.</span></span>  
  
         <span data-ttu-id="6ba90-142">SORT_IN_TEMPDB が ON の場合の一時ディスク領域の合計サイズは ~ 202 MB です。</span><span class="sxs-lookup"><span data-stu-id="6ba90-142">Total size of temporary disk space with SORT_IN_TEMPDB set to ON ~ 202 MB.</span></span>  
  
    2.  <span data-ttu-id="6ba90-143">SORT_IN_TEMPDB が OFF (既定値) の場合、手順 2. で新しいインデックス用に算出した 250 MB のディスク領域が、並べ替えに使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ba90-143">When SORT_IN_TEMPDB is set to OFF (default), the 250 MB of disk space already considered for the new index in step 2 is used for sorting.</span></span>  
  
         <span data-ttu-id="6ba90-144">追加のディスク領域 (対象の場所内) は [index create memory サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) の値 (= 2 MB) と同じです。</span><span class="sxs-lookup"><span data-stu-id="6ba90-144">Additional disk space (in the target location) equal to the [Configure the index create memory Server Configuration Option](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md) value = 2 MB.</span></span>  
  
         <span data-ttu-id="6ba90-145">SORT_IN_TEMPDB が OFF の場合の一時ディスク領域の合計サイズは 2 MB です。</span><span class="sxs-lookup"><span data-stu-id="6ba90-145">Total size of temporary disk space with SORT_IN_TEMPDB set to OFF = 2 MB.</span></span>  
  
 <span data-ttu-id="6ba90-146">**tempdb**を使用すると、合計で 1,018 MB (816 + 202) がクラスター化インデックスと非クラスター化インデックスの作成用に必要になります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-146">Using **tempdb**, a total of 1018 MB (816 + 202) would be needed to create the clustered and nonclustered indexes.</span></span> <span data-ttu-id="6ba90-147">**tempdb** を使用することで、インデックスの作成に使用する一時ディスク領域は増えますが、 **tempdb** がユーザー データベースとは異なるディスク セットにある場合、インデックスの作成に必要な時間を短縮できることがあります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-147">Although using **tempdb** increases the amount of temporary disk space used to create an index, it may reduce the time that is required to create an index when **tempdb** is on a different set of disks than the user database.</span></span> <span data-ttu-id="6ba90-148">**tempdb**の使用の詳細については、「 [インデックスの SORT_IN_TEMPDB オプション](indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ba90-148">For more information about using **tempdb**, see [SORT_IN_TEMPDB Option For Indexes](indexes.md).</span></span>  
  
 <span data-ttu-id="6ba90-149">**tempdb**を使用しない場合は、合計で 818 MB (816 + 2) がクラスター化インデックスと非クラスター化インデックスの作成に必要になります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-149">Without using **tempdb**, a total of 818 MB (816+ 2) would be needed to create the clustered and nonclustered indexes.</span></span>  
  
## <a name="disk-space-calculations-for-an-online-clustered-index-operation"></a><span data-ttu-id="6ba90-150">オンライン クラスター化インデックス操作に必要なディスク領域の計算</span><span class="sxs-lookup"><span data-stu-id="6ba90-150">Disk Space Calculations for an Online Clustered Index Operation</span></span>  
 <span data-ttu-id="6ba90-151">クラスター化インデックスをオンラインで作成、削除、または再構築する場合、一時マッピング インデックスを構築および保持するために追加のディスク領域が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-151">When you create, drop, or rebuild a clustered index online, additional disk space is required to build and maintain a temporary mapping index.</span></span> <span data-ttu-id="6ba90-152">一時マッピング インデックスには、テーブルの行ごとに 1 つのレコードが格納されます。レコードの内容は、古いブックマーク列と新しいブックマーク列を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="6ba90-152">This temporary mapping index contains one record for each row in the table, and its contents are the union of the old and new bookmark columns.</span></span>  
  
 <span data-ttu-id="6ba90-153">オンライン クラスター化インデックス操作に必要なディスク領域を計算するには、上記のオフライン インデックス操作用の手順を実行し、その結果と次の手順で得られる結果とを加算します。</span><span class="sxs-lookup"><span data-stu-id="6ba90-153">To calculate the disk space needed for an online clustered index operation, follow the steps shown for an offline index operation and add those results to the results of the following step.</span></span>  
  
-   <span data-ttu-id="6ba90-154">一時マッピング インデックスに必要な領域を判断します。</span><span class="sxs-lookup"><span data-stu-id="6ba90-154">Determine space for the temporary mapping index.</span></span>  
  
     <span data-ttu-id="6ba90-155">この例では、古いブックマークはヒープの行 ID (RID) (8 バイト) で、新しいブックマークはクラスター化キー (を含む24バイト) です `uniqueifier` 。</span><span class="sxs-lookup"><span data-stu-id="6ba90-155">In this example, the old bookmark is the row ID (RID) of the heap (8 bytes) and the new bookmark is the clustering key (24 bytes including a `uniqueifier`).</span></span> <span data-ttu-id="6ba90-156">古いブックマークと新しいブックマーク間で重複する列はありません。</span><span class="sxs-lookup"><span data-stu-id="6ba90-156">There are no overlapping columns between the old and new bookmarks.</span></span>  
  
     <span data-ttu-id="6ba90-157">一時マッピング インデックスのサイズは、100 万行 \* (8 バイト + 24 バイト) / 80% ~ 40 MB です。</span><span class="sxs-lookup"><span data-stu-id="6ba90-157">Temporary mapping index size = 1 million \* (8 bytes + 24 bytes) / 80% ~ 40 MB.</span></span>  
  
     <span data-ttu-id="6ba90-158">SORT_IN_TEMPDB が OFF の場合は対象となる場所に必要なディスク領域に、SORT_IN_TEMPDB が ON の場合は **tempdb** に必要なディスク領域に、このディスク領域を加算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ba90-158">This disk space must be added to the required disk space in the target location if SORT_IN_TEMPDB is set to OFF, or to **tempdb** if SORT_IN_TEMPDB is set to ON.</span></span>  
  
 <span data-ttu-id="6ba90-159">一時マッピング インデックスの詳細については、「 [インデックス DDL 操作に必要なディスク領域](disk-space-requirements-for-index-ddl-operations.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="6ba90-159">For more information about the temporary mapping index, see [Disk Space Requirements for Index DDL Operations](disk-space-requirements-for-index-ddl-operations.md).</span></span>  
  
## <a name="disk-space-summary"></a><span data-ttu-id="6ba90-160">ディスク領域のまとめ</span><span class="sxs-lookup"><span data-stu-id="6ba90-160">Disk Space Summary</span></span>  
 <span data-ttu-id="6ba90-161">次の表は、ディスク領域の計算結果をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="6ba90-161">The following table summarizes the results of the disk space calculations.</span></span>  
  
|<span data-ttu-id="6ba90-162">インデックス操作</span><span class="sxs-lookup"><span data-stu-id="6ba90-162">Index operation</span></span>|<span data-ttu-id="6ba90-163">構造の場所と必要なディスク領域</span><span class="sxs-lookup"><span data-stu-id="6ba90-163">Disk space requirements for the locations of the following structures</span></span>|  
|---------------------|---------------------------------------------------------------------------|  
|<span data-ttu-id="6ba90-164">SORT_IN_TEMPDB = ON に設定されたオフライン インデックス操作</span><span class="sxs-lookup"><span data-stu-id="6ba90-164">Offline index operation with SORT_IN_TEMPDB = ON</span></span>|<span data-ttu-id="6ba90-165">操作中の合計領域: 1018 MB:</span><span class="sxs-lookup"><span data-stu-id="6ba90-165">Total space during the operation: 1018 MB:</span></span><br /><br /> <span data-ttu-id="6ba90-166">\- 既存のテーブルとインデックス: 363 MB\*</span><span class="sxs-lookup"><span data-stu-id="6ba90-166">-Existing table and indexes: 363 MB\*</span></span><br /><br /> -<br />                    <span data-ttu-id="6ba90-167">**tempdb**: 202 MB\*</span><span class="sxs-lookup"><span data-stu-id="6ba90-167">**tempdb**: 202 MB\*</span></span><br /><br /> <span data-ttu-id="6ba90-168">\- 新しいインデックス: 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-168">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="6ba90-169">操作の完了後に必要な領域の合計サイズ: 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-169">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="6ba90-170">SORT_IN_TEMPDB = OFF に設定されたオフライン インデックス操作</span><span class="sxs-lookup"><span data-stu-id="6ba90-170">Offline index operation with SORT_IN_TEMPDB = OFF</span></span>|<span data-ttu-id="6ba90-171">操作中の合計領域: 816 MB:</span><span class="sxs-lookup"><span data-stu-id="6ba90-171">Total space during the operation: 816 MB:</span></span><br /><br /> <span data-ttu-id="6ba90-172">\- 既存のテーブルとインデックス: 363 MB\*</span><span class="sxs-lookup"><span data-stu-id="6ba90-172">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="6ba90-173">\- 新しいインデックス: 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-173">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="6ba90-174">操作の完了後に必要な領域の合計サイズ: 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-174">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="6ba90-175">SORT_IN_TEMPDB = ON に設定されたオンライン インデックス操作</span><span class="sxs-lookup"><span data-stu-id="6ba90-175">Online index operation with SORT_IN_TEMPDB = ON</span></span>|<span data-ttu-id="6ba90-176">操作中の合計領域: 1058 MB:</span><span class="sxs-lookup"><span data-stu-id="6ba90-176">Total space during the operation: 1058 MB:</span></span><br /><br /> <span data-ttu-id="6ba90-177">\- 既存のテーブルとインデックス: 363 MB\*</span><span class="sxs-lookup"><span data-stu-id="6ba90-177">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="6ba90-178">-**tempdb** (マッピングインデックスを含む): 242 MB \*</span><span class="sxs-lookup"><span data-stu-id="6ba90-178">-**tempdb** (includes mapping index): 242 MB\*</span></span><br /><br /> <span data-ttu-id="6ba90-179">\- 新しいインデックス: 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-179">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="6ba90-180">操作の完了後に必要な領域の合計サイズ: 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-180">Total space required after the operation: 453 MB</span></span>|  
|<span data-ttu-id="6ba90-181">SORT_IN_TEMPDB = OFF に設定されたオンライン インデックス操作</span><span class="sxs-lookup"><span data-stu-id="6ba90-181">Online index operation with SORT_IN_TEMPDB = OFF</span></span>|<span data-ttu-id="6ba90-182">操作中の合計領域: 856 MB:</span><span class="sxs-lookup"><span data-stu-id="6ba90-182">Total space during the operation: 856 MB:</span></span><br /><br /> <span data-ttu-id="6ba90-183">\- 既存のテーブルとインデックス: 363 MB\*</span><span class="sxs-lookup"><span data-stu-id="6ba90-183">-Existing table and indexes: 363 MB\*</span></span><br /><br /> <span data-ttu-id="6ba90-184">\- 一時マッピング インデックス: 40 MB\*</span><span class="sxs-lookup"><span data-stu-id="6ba90-184">-Temporary mapping index: 40 MB\*</span></span><br /><br /> <span data-ttu-id="6ba90-185">\- 新しいインデックス: 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-185">-New indexes: 453 MB</span></span><br /><br /> <span data-ttu-id="6ba90-186">操作の完了後に必要な領域の合計サイズ: 453 MB</span><span class="sxs-lookup"><span data-stu-id="6ba90-186">Total space required after the operation: 453 MB</span></span>|  
  
 <span data-ttu-id="6ba90-187">\*この領域は、インデックス操作がコミットされると、割り当てが解除されます。</span><span class="sxs-lookup"><span data-stu-id="6ba90-187">\*This space is deallocated after the index operation is committed.</span></span>  
  
 <span data-ttu-id="6ba90-188">この例では、同時実行ユーザーの更新操作や削除操作により作成されるバージョン レコード用に **tempdb** に必要な追加の一時ディスク領域については、計算していません。</span><span class="sxs-lookup"><span data-stu-id="6ba90-188">This example does not consider any additional temporary disk space required in **tempdb** for version records created by concurrent user update and delete operations.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="6ba90-189">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="6ba90-189">Related Content</span></span>  
 [<span data-ttu-id="6ba90-190">Disk Space Requirements for Index DDL Operations</span><span class="sxs-lookup"><span data-stu-id="6ba90-190">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="6ba90-191">インデックス操作用のトランザクション ログのディスク領域</span><span class="sxs-lookup"><span data-stu-id="6ba90-191">Transaction Log Disk Space for Index Operations</span></span>](transaction-log-disk-space-for-index-operations.md)  
  
  
