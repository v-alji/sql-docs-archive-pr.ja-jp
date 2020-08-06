---
title: アセンブリに関する情報の取得 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], metadata
- status information [SQL Server], assemblies
- metadata [SQL Server], assemblies
ms.assetid: 6aa7f18e-baad-4481-9777-8c3b230b392f
author: rothja
ms.author: jroth
ms.openlocfilehash: ec559ba5ccbb53dd92f3a5e1175a10a59fbaf43c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720072"
---
# <a name="getting-information-about-assemblies"></a><span data-ttu-id="c72a2-102">アセンブリについての情報の取得</span><span class="sxs-lookup"><span data-stu-id="c72a2-102">Getting Information About Assemblies</span></span>
  <span data-ttu-id="c72a2-103">次のカタログ ビューや関数により、アセンブリに関するメタデータにクエリを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c72a2-103">The following catalog views and functions can be queried for metadata about assemblies.</span></span>  
  
 <span data-ttu-id="c72a2-104">**個別のアセンブリに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="c72a2-104">**To get information about individual assemblies**</span></span>  
  
-   [<span data-ttu-id="c72a2-105">ASSEMBLYPROPERTY &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a2-105">ASSEMBLYPROPERTY &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/assemblyproperty-transact-sql)  
  
 <span data-ttu-id="c72a2-106">**データベース内のすべてのアセンブリに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="c72a2-106">**To get information about all assemblies in the database**</span></span>  
  
-   [<span data-ttu-id="c72a2-107">アセンブリ &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a2-107">sys.assemblies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assemblies-transact-sql)  
  
 <span data-ttu-id="c72a2-108">**アセンブリのバイナリ、ソース ファイル、デバッグ ファイルなど、アセンブリ ファイルに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="c72a2-108">**To get information about assembly files, including assembly binaries, source files, and debug files**</span></span>  
  
-   [<span data-ttu-id="c72a2-109">assembly_files &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a2-109">sys.assembly_files &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-files-transact-sql)  
  
 <span data-ttu-id="c72a2-110">**アセンブリ間の参照に関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="c72a2-110">**To get information about cross-assembly references**</span></span>  
  
-   [<span data-ttu-id="c72a2-111">assembly_references &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a2-111">sys.assembly_references &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-references-transact-sql)  
  
 <span data-ttu-id="c72a2-112">**ユーザー定義型に関するアセンブリ情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="c72a2-112">**To get assembly information about user-defined types**</span></span>  
  
-   [<span data-ttu-id="c72a2-113">assembly_types &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a2-113">sys.assembly_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-types-transact-sql)  
  
-   [<span data-ttu-id="c72a2-114">sys.types &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a2-114">sys.types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-types-transact-sql)  
  
 <span data-ttu-id="c72a2-115">**CLR (共通言語ランタイム) ストアド プロシージャ、トリガー、および関数に関するアセンブリ情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="c72a2-115">**To get assembly information about common language runtime (CLR) stored procedures, triggers, and functions**</span></span>  
  
-   [<span data-ttu-id="c72a2-116">sys.assembly_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a2-116">sys.assembly_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-assembly-modules-transact-sql)  
  
 <span data-ttu-id="c72a2-117">**CLR 以外のオブジェクトに関する情報を取得するには**</span><span class="sxs-lookup"><span data-stu-id="c72a2-117">**To get information about non-CLR objects**</span></span>  
  
-   [<span data-ttu-id="c72a2-118">sys.sql_modules &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c72a2-118">sys.sql_modules &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="c72a2-119">参照</span><span class="sxs-lookup"><span data-stu-id="c72a2-119">See Also</span></span>  
 <span data-ttu-id="c72a2-120">[アセンブリ &#40;データベースエンジン&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="c72a2-120">[Assemblies &#40;Database Engine&#41;](../../relational-databases/clr-integration/assemblies-database-engine.md) </span></span>  
 <span data-ttu-id="c72a2-121">[アセンブリのデザイン](../../relational-databases/clr-integration/assemblies-designing.md) </span><span class="sxs-lookup"><span data-stu-id="c72a2-121">[Designing Assemblies](../../relational-databases/clr-integration/assemblies-designing.md) </span></span>  
 [<span data-ttu-id="c72a2-122">アセンブリの実装</span><span class="sxs-lookup"><span data-stu-id="c72a2-122">Implementing Assemblies</span></span>](assemblies-implementing.md)  
  
  
