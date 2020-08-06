---
title: 非クラスター化列ストアインデックスの使用 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c876eb6fdd466349ac369dcff8e292bc0839c669
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715682"
---
# <a name="using-nonclustered-columnstore-indexes"></a><span data-ttu-id="254d9-102">非クラスター化列ストア インデックスの使用</span><span class="sxs-lookup"><span data-stu-id="254d9-102">Using Nonclustered Columnstore Indexes</span></span>
  <span data-ttu-id="254d9-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブルの非クラスター化 columnstore インデックスを使用するキー タスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="254d9-103">Describes key tasks for using a nonclustered columnstore index on a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>

 <span data-ttu-id="254d9-104">列ストアインデックスの概要については、「[列ストアインデックス](../relational-databases/indexes/columnstore-indexes-described.md)の概要」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="254d9-104">For an overview of columnstore indexes, see [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).</span></span>

 <span data-ttu-id="254d9-105">クラスター化列ストアインデックスの詳細については、「[クラスター化列ストアインデックスの使用](../relational-databases/indexes/indexes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="254d9-105">For information about clustered columnstore indexes, see [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).</span></span>

## <a name="contents"></a><span data-ttu-id="254d9-106">内容</span><span class="sxs-lookup"><span data-stu-id="254d9-106">Contents</span></span>

-   [<span data-ttu-id="254d9-107">非クラスター化 Columnstore インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="254d9-107">Create a Nonclustered Columnstore Index</span></span>](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)

-   [<span data-ttu-id="254d9-108">非クラスター化列ストアインデックスのデータを変更する</span><span class="sxs-lookup"><span data-stu-id="254d9-108">Change the Data in a Nonclustered Columnstore Index</span></span>](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)

##  <a name="create-a-nonclustered-columnstore-index"></a><a name="load"></a><span data-ttu-id="254d9-109">非クラスター化列ストアインデックスを作成する</span><span class="sxs-lookup"><span data-stu-id="254d9-109">Create a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="254d9-110">データを非クラスター化列ストアインデックスに読み込むには、まず、ヒープまたはクラスター化インデックスとして格納されている従来の行ストアテーブルにデータを読み込み、次に[CREATE 列ストアインデックス &#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)を使用して列ストアインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="254d9-110">To load data into a nonclustered columnstore index, first load data into a traditional rowstore table stored as a heap or clustered index, and then use [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql) to create a columnstore index.</span></span>

 <span data-ttu-id="254d9-111">![列ストア インデックスへのデータの読み込み](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "列ストア インデックスへのデータの読み込み")</span><span class="sxs-lookup"><span data-stu-id="254d9-111">![Loading data into a columnstore index](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Loading data into a columnstore index")</span></span>

##  <a name="change-the-data-in-a-nonclustered-columnstore-index"></a><a name="change"></a><span data-ttu-id="254d9-112">非クラスター化列ストアインデックスのデータを変更する</span><span class="sxs-lookup"><span data-stu-id="254d9-112">Change the Data in a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="254d9-113">テーブルに非クラスター化列ストア インデックスを作成すると、そのテーブル内のデータは変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="254d9-113">Once you create a nonclustered columnstore index on a table, you cannot directly modify the data in that table.</span></span> <span data-ttu-id="254d9-114">INSERT、UPDATE、DELETE、または MERGE を使用するクエリは失敗し、エラーメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="254d9-114">A query with INSERT, UPDATE, DELETE, or MERGE will fail and return an error message.</span></span> <span data-ttu-id="254d9-115">そのテーブル内のデータを追加または変更するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="254d9-115">To add or modify the data in the table, you can do one of the following:</span></span>

-   <span data-ttu-id="254d9-116">列ストアインデックスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="254d9-116">Disable the columnstore index.</span></span> <span data-ttu-id="254d9-117">その後、テーブル内のデータを更新できます。</span><span class="sxs-lookup"><span data-stu-id="254d9-117">You can then update the data in the table.</span></span> <span data-ttu-id="254d9-118">列ストア インデックスを無効にした場合、データの更新の終了時に列ストア インデックスを再構築できます。</span><span class="sxs-lookup"><span data-stu-id="254d9-118">If you disable the columnstore index, you can rebuild the columnstore index when you finish updating the data.</span></span> <span data-ttu-id="254d9-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="254d9-119">For example:</span></span>

    ```
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;
    -- update mytable --
    ALTER INDEX mycolumnstoreindex on mytable REBUILD
    ```

-   <span data-ttu-id="254d9-120">列ストアインデックスを削除し、テーブルを更新してから、CREATE 列ストアインデックスを使用して列ストアインデックスを再作成します。</span><span class="sxs-lookup"><span data-stu-id="254d9-120">Drop the columnstore index, update the table, and then re-create the columnstore index with CREATE COLUMNSTORE INDEX.</span></span> <span data-ttu-id="254d9-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="254d9-121">For example:</span></span>

    ```
    DROP INDEX mycolumnstoreindex ON mytable
    -- update mytable --
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;

    ```

-   <span data-ttu-id="254d9-122">列ストア インデックスのないステージング テーブルにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="254d9-122">Load data into a staging table that does not have a columnstore index.</span></span> <span data-ttu-id="254d9-123">そのステージング テーブルに列ストア インデックスを構築します。</span><span class="sxs-lookup"><span data-stu-id="254d9-123">Build a columnstore index on the staging table.</span></span> <span data-ttu-id="254d9-124">そのステージング テーブルをメイン テーブルの空のパーティションに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="254d9-124">Switch the staging table into an empty partition of the main table.</span></span>

-   <span data-ttu-id="254d9-125">列ストア インデックスを持つテーブルから空のステージング テーブルにパーティションを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="254d9-125">Switch a partition from the table with the columnstore index into an empty staging table.</span></span> <span data-ttu-id="254d9-126">ステージング テーブルに列ストア インデックスがある場合は、列ストア インデックスを無効にします。</span><span class="sxs-lookup"><span data-stu-id="254d9-126">If there is a columnstore index on the staging table, disable the columnstore index.</span></span> <span data-ttu-id="254d9-127">更新を実行します。</span><span class="sxs-lookup"><span data-stu-id="254d9-127">Perform any updates.</span></span> <span data-ttu-id="254d9-128">列ストア インデックスを構築 (または再構築) します。</span><span class="sxs-lookup"><span data-stu-id="254d9-128">Build (or rebuild) the columnstore index.</span></span> <span data-ttu-id="254d9-129">ステージング テーブルを切り替えて、メイン テーブルの (空になった) パーティションに戻します。</span><span class="sxs-lookup"><span data-stu-id="254d9-129">Switch the staging table back into the (now empty) partition of the main table.</span></span>




