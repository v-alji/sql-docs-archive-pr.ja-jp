---
title: '[データベースのプロパティ] ([ファイル グループ] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.filegroups.f1
ms.assetid: 8d06e859-73dd-4019-b6e8-99c5c5297697
author: stevestein
ms.author: sstein
ms.openlocfilehash: d0546a17491ed5d3b36890a605c5faa922c24fe6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640063"
---
# <a name="database-properties-filegroups-page"></a><span data-ttu-id="bc536-102">[データベースのプロパティ] ([ファイル グループ] ページ)</span><span class="sxs-lookup"><span data-stu-id="bc536-102">Database Properties (Filegroups Page)</span></span>
  <span data-ttu-id="bc536-103">このページを使用すると、ファイル グループを表示したり、選択したデータベースに新しいファイル グループを追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="bc536-103">Use this page to view the filegroups or add a new filegroup to the selected database.</span></span> <span data-ttu-id="bc536-104">ファイル グループの種類は、 *Row* ファイル グループ、FILESTREAM データ、およびメモリ最適化ファイル グループに分けられます。</span><span class="sxs-lookup"><span data-stu-id="bc536-104">Filegroup types are separated into *row* filegroups, FILESTREAM data, and memory-optimized filegroups.</span></span>  
  
 <span data-ttu-id="bc536-105">ROW ファイル グループには、通常のデータおよびログ ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bc536-105">Row filegroups contain regular data and log files.</span></span> <span data-ttu-id="bc536-106">FILESTREAM データ ファイル グループには、FILESTREAM データ ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bc536-106">FILESTREAM data filegroups contain FILESTREAM data files.</span></span> <span data-ttu-id="bc536-107">これらのデータ ファイルには、FILESTREAM ストレージを使用する場合に、バイナリ ラージ オブジェクト (BLOB) データをファイル システムに対してどのように格納するかという情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="bc536-107">These data files store information about how binary large object (BLOB) data is stored on the file system when you are using FILESTREAM storage.</span></span> <span data-ttu-id="bc536-108">どちらのファイル グループもオプションは同じです。</span><span class="sxs-lookup"><span data-stu-id="bc536-108">The options are the same for both types of filegroups.</span></span>  
  
 <span data-ttu-id="bc536-109">FILESTREAM が有効になっていない場合、 **Filestream** のセクションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="bc536-109">If FILESTREAM is not enabled, the **Filestream** section will not be available.</span></span> <span data-ttu-id="bc536-110">FILESTREAM ストレージを有効にするには、 [[サーバーのプロパティ] ([詳細設定] ページ)](../../database-engine/configure-windows/server-properties-advanced-page.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc536-110">You can enable FILESTREAM storage by using [Server Properties (Advanced Page)](../../database-engine/configure-windows/server-properties-advanced-page.md).</span></span>  
  
 <span data-ttu-id="bc536-111">ROW ファイル グループが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でどのように使用されるかについては、「 [データベース ファイルとファイル グループ](database-files-and-filegroups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc536-111">For information about how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses row filegroups, see [Database Files and Filegroups](database-files-and-filegroups.md).</span></span> <span data-ttu-id="bc536-112">FILESTREAM データおよびファイル グループの詳細については、「[FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc536-112">For more information about FILESTREAM data and filegroups, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="bc536-113">データベースに 1 つ以上のメモリ最適化テーブルを含めるには、メモリ最適化ファイル グループが必要です。</span><span class="sxs-lookup"><span data-stu-id="bc536-113">Memory-optimized file groups are required for a database to contain one or more memory-optimized tables.</span></span>  
  
## <a name="row-and-filestream-data-filegroup-options"></a><span data-ttu-id="bc536-114">ROW および FILESTREAM データ ファイル グループのオプション</span><span class="sxs-lookup"><span data-stu-id="bc536-114">Row and FILESTREAM Data Filegroup Options</span></span>  
 <span data-ttu-id="bc536-115">**名前**</span><span class="sxs-lookup"><span data-stu-id="bc536-115">**Name**</span></span>  
 <span data-ttu-id="bc536-116">ファイル グループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bc536-116">Enter the name of the filegroup.</span></span>  
  
 <span data-ttu-id="bc536-117">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="bc536-117">**Files**</span></span>  
 <span data-ttu-id="bc536-118">ファイル グループ内のファイルの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="bc536-118">Displays the count of files in the filegroup.</span></span>  
  
 <span data-ttu-id="bc536-119">**読み取り専用です。**</span><span class="sxs-lookup"><span data-stu-id="bc536-119">**Read-only**</span></span>  
 <span data-ttu-id="bc536-120">ファイル グループを読み取り専用ステータスに設定します。</span><span class="sxs-lookup"><span data-stu-id="bc536-120">Select to set the filegroup to a read-only status.</span></span>  
  
 <span data-ttu-id="bc536-121">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="bc536-121">**Default**</span></span>  
 <span data-ttu-id="bc536-122">このファイル グループを既定のファイル グループにします。</span><span class="sxs-lookup"><span data-stu-id="bc536-122">Select to make this filegroup the default filegroup.</span></span> <span data-ttu-id="bc536-123">行と FILESTREAM データに対して、既定のファイル グループをそれぞれ 1 つずつ指定できます。</span><span class="sxs-lookup"><span data-stu-id="bc536-123">You can have one default filegroup for rows and one default filegroup for FILESTREAM data.</span></span>  
  
 <span data-ttu-id="bc536-124">**追加**</span><span class="sxs-lookup"><span data-stu-id="bc536-124">**Add**</span></span>  
 <span data-ttu-id="bc536-125">データベースのファイル グループを一覧表示するグリッドに、新しい空の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="bc536-125">Adds a new blank row to the grid listing filegroups for the database.</span></span>  
  
 <span data-ttu-id="bc536-126">**Remove**</span><span class="sxs-lookup"><span data-stu-id="bc536-126">**Remove**</span></span>  
 <span data-ttu-id="bc536-127">選択されたファイル グループ行をグリッドから削除します。</span><span class="sxs-lookup"><span data-stu-id="bc536-127">Removes the selected filegroup row from the grid.</span></span>  
  
## <a name="memory-optimized-data-filegroup-options"></a><span data-ttu-id="bc536-128">メモリ最適化データ ファイル グループのオプション</span><span class="sxs-lookup"><span data-stu-id="bc536-128">Memory-Optimized Data Filegroup Options</span></span>  
 <span data-ttu-id="bc536-129">**名前**</span><span class="sxs-lookup"><span data-stu-id="bc536-129">**Name**</span></span>  
 <span data-ttu-id="bc536-130">メモリ最適化ファイル グループの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bc536-130">Enter the name of the memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="bc536-131">**[FILESTREAM ファイル]**</span><span class="sxs-lookup"><span data-stu-id="bc536-131">**Filestream Files**</span></span>  
 <span data-ttu-id="bc536-132">メモリ最適化データ ファイル グループのファイル (コンテナー) の数を表示します。</span><span class="sxs-lookup"><span data-stu-id="bc536-132">Displays the number of files (containers) in the memory-optimized data filegroup.</span></span> <span data-ttu-id="bc536-133">**[ファイル]** ページでコンテナーを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="bc536-133">You can add containers in the **Files** page.</span></span>  
  
 <span data-ttu-id="bc536-134">**追加**</span><span class="sxs-lookup"><span data-stu-id="bc536-134">**Add**</span></span>  
 <span data-ttu-id="bc536-135">データベースのファイル グループを一覧表示するグリッドに、新しい空の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="bc536-135">Adds a new blank row to the grid listing filegroups for the database.</span></span>  
  
 <span data-ttu-id="bc536-136">**Remove**</span><span class="sxs-lookup"><span data-stu-id="bc536-136">**Remove**</span></span>  
 <span data-ttu-id="bc536-137">選択されたファイル グループ行をグリッドから削除します。</span><span class="sxs-lookup"><span data-stu-id="bc536-137">Removes the selected filegroup row from the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc536-138">参照</span><span class="sxs-lookup"><span data-stu-id="bc536-138">See Also</span></span>  
 <span data-ttu-id="bc536-139">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="bc536-139">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="bc536-140">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="bc536-140">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
