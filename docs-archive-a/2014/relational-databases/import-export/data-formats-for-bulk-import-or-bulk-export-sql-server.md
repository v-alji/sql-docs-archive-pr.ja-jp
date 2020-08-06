---
title: 一括インポートまたは一括エクスポートのデータ形式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], choosing
- bulk importing [SQL Server], data formats
ms.assetid: 73fe6741-9437-4b26-b030-28b863e74399
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b92ac8c038362ff18a1459a8bf3c55b6b596a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631017"
---
# <a name="data-formats-for-bulk-import-or-bulk-export-sql-server"></a><span data-ttu-id="23419-102">一括インポートまたは一括エクスポートのデータ形式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="23419-102">Data Formats for Bulk Import or Bulk Export (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="23419-103">では、データを文字データ形式でもネイティブ バイナリ データ形式でも受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="23419-103">can accept data in character data format or native binary data format.</span></span> <span data-ttu-id="23419-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と別のアプリケーション ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel など) または別のデータベース サーバー (Oracle や [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]など) との間でデータを移動するときは、文字形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="23419-104">Use character format when you move data between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and another application (such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel) or another database server (such as Oracle or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]).</span></span> <span data-ttu-id="23419-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス間でデータを転送する場合にのみ、ネイティブ形式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="23419-105">You can use native format only when you transfer data between instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="23419-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="23419-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="23419-107">一括インポートまたは一括エクスポートのデータ形式</span><span class="sxs-lookup"><span data-stu-id="23419-107">Data Formats for Bulk Import or Export</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="23419-108">関連タスク</span><span class="sxs-lookup"><span data-stu-id="23419-108">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="data-formats-for-bulk-import-or-export"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="23419-109">一括インポートまたは一括エクスポートのデータ形式</span><span class="sxs-lookup"><span data-stu-id="23419-109">Data Formats for Bulk Import or Export</span></span>  
 <span data-ttu-id="23419-110">次の表は、データの表現方法や転送元または転送先に基づいて、一般的にどのデータ形式を使用するのが適切かを示しています。</span><span class="sxs-lookup"><span data-stu-id="23419-110">The following table indicates what data format is generally appropriate to use depending on how the data is represented and the source or target of the operation.</span></span>  
  
|<span data-ttu-id="23419-111">Operation</span><span class="sxs-lookup"><span data-stu-id="23419-111">Operation</span></span>|<span data-ttu-id="23419-112">ネイティブ</span><span class="sxs-lookup"><span data-stu-id="23419-112">Native</span></span>|<span data-ttu-id="23419-113">Unicode ネイティブ</span><span class="sxs-lookup"><span data-stu-id="23419-113">Unicode native</span></span>|<span data-ttu-id="23419-114">文字</span><span class="sxs-lookup"><span data-stu-id="23419-114">Character</span></span>|<span data-ttu-id="23419-115">Unicode 文字</span><span class="sxs-lookup"><span data-stu-id="23419-115">Unicode character</span></span>|  
|---------------|------------|--------------------|---------------|-----------------------|  
|<span data-ttu-id="23419-116">拡張文字や 2 バイト文字セット (DBCS) の文字を含まないデータ ファイルを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送します。</span><span class="sxs-lookup"><span data-stu-id="23419-116">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that does not contain any extended or double-byte character set (DBCS) characters.</span></span> <span data-ttu-id="23419-117">フォーマット ファイルを使用する場合を除いて、これらのテーブルは同じように定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="23419-117">Unless a format file is used, these tables must be identically defined.</span></span>|<span data-ttu-id="23419-118">可<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="23419-118">Yes<sup>1</sup></span></span>|-|-|-|  
|<span data-ttu-id="23419-119">文字形式や Unicode 形式とは異なり、ネイティブ データ形式では各 `sql_variant` 値のメタデータが保持されるので、`sql_variant` 列ではネイティブ データ形式を使用することが最も適しています。</span><span class="sxs-lookup"><span data-stu-id="23419-119">For `sql_variant` columns, use of native data format is best, because native data format preserves the metadata for each `sql_variant` value, unlike character or Unicode formats.</span></span>|<span data-ttu-id="23419-120">はい</span><span class="sxs-lookup"><span data-stu-id="23419-120">Yes</span></span>|-|-|-|  
|<span data-ttu-id="23419-121">拡張文字や DBCS 文字を含むデータ ファイルを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送します。</span><span class="sxs-lookup"><span data-stu-id="23419-121">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains extended or DBCS characters.</span></span>|-|<span data-ttu-id="23419-122">はい</span><span class="sxs-lookup"><span data-stu-id="23419-122">Yes</span></span>|-|-|  
|<span data-ttu-id="23419-123">別のプログラムで生成されたテキスト ファイルからデータを一括インポートします。</span><span class="sxs-lookup"><span data-stu-id="23419-123">Bulk import of data from a text file that is generated by another program.</span></span>|-|-|<span data-ttu-id="23419-124">はい</span><span class="sxs-lookup"><span data-stu-id="23419-124">Yes</span></span>|-|  
|<span data-ttu-id="23419-125">別のプログラムで使用するテキスト ファイルにデータを一括エクスポートします。</span><span class="sxs-lookup"><span data-stu-id="23419-125">Bulk export of data to a text file that is to be used in another program.</span></span>|-|-|<span data-ttu-id="23419-126">はい</span><span class="sxs-lookup"><span data-stu-id="23419-126">Yes</span></span>|-|  
|<span data-ttu-id="23419-127">Unicode データを含み、拡張文字や DBCS 文字は含まないデータ ファイルを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の複数のインスタンス間でデータを一括転送します。</span><span class="sxs-lookup"><span data-stu-id="23419-127">Bulk transfers of data between multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by using a data file that contains Unicode data and does not contain any extended or DBCS characters.</span></span>|-|-|-|<span data-ttu-id="23419-128">はい</span><span class="sxs-lookup"><span data-stu-id="23419-128">Yes</span></span>|  
  
 <span data-ttu-id="23419-129"><sup>1</sup> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **bcp**を使用するときに、からデータを一括エクスポートする最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="23419-129"><sup>1</sup> Fastest method for the bulk export of data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] when using **bcp**.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="23419-130">関連タスク</span><span class="sxs-lookup"><span data-stu-id="23419-130">Related Tasks</span></span>  
  
-   [<span data-ttu-id="23419-131">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="23419-131">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="23419-132">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="23419-132">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="23419-133">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="23419-133">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="23419-134">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="23419-134">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="23419-135">以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート</span><span class="sxs-lookup"><span data-stu-id="23419-135">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="23419-136">参照</span><span class="sxs-lookup"><span data-stu-id="23419-136">See Also</span></span>  
 <span data-ttu-id="23419-137">[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="23419-137">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 [<span data-ttu-id="23419-138">bcp を使用した互換性のためのデータ形式の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="23419-138">Specify Data Formats for Compatibility when Using bcp &#40;SQL Server&#41;</span></span>](specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)  
  
  
