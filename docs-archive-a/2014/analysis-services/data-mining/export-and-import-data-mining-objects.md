---
title: データマイニングオブジェクトのエクスポートとインポート |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- exporting mining models
- exporting mining structures
- mining structures [Analysis Services], creating
- mining structures [DMX], exporting
- mining models [Analysis Services], migration
ms.assetid: 10a83b13-2640-4ff5-80c8-a35e1d692908
author: minewiskan
ms.author: owend
ms.openlocfilehash: 01e8651dd7e9d59012b0ba065bccb9ea62a1ee54
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643017"
---
# <a name="export-and-import-data-mining-objects"></a><span data-ttu-id="112ab-102">データ マイニング オブジェクトのエクスポートおよびインポート</span><span class="sxs-lookup"><span data-stu-id="112ab-102">Export and Import Data Mining Objects</span></span>
  <span data-ttu-id="112ab-103">SQL Server データ マイニングでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されている、ソリューションをバックアップ、復元、および移行するための機能に加えて、データ マイニング拡張機能 (DMX) を使用して異なるサーバー間でデータ マイニング構造およびデータ マイニング モデルをすばやく転送する機能を提供しています。</span><span class="sxs-lookup"><span data-stu-id="112ab-103">In addition to the functionality provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for backing up, restoring, and migrating solutions, SQL Server Data Mining provides the ability to quickly transfer data mining structures and models between different servers by using Data Mining Extensions (DMX).</span></span>  
  
 <span data-ttu-id="112ab-104">データ マイニング ソリューションで多次元データベースではなくリレーショナル データを使用している場合は、データベースの復元を使用したりソリューション全体を配置したりするよりも、`EXPORT` と `IMPORT` を使用した方がすばやく簡単にモデルを転送できます。</span><span class="sxs-lookup"><span data-stu-id="112ab-104">If your data mining solution uses relational data instead of a multidimensional database, transferring models by using `EXPORT` and `IMPORT` is much faster and easier than either using database restore or deploying an entire solution.</span></span>  
  
 <span data-ttu-id="112ab-105">このセクションでは、DMX ステートメントを使用してデータ マイニング構造およびデータ マイニング モデルを転送する方法の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="112ab-105">This section provides an overview of how to transfer data mining structures and models by using DMX statements.</span></span> <span data-ttu-id="112ab-106">構文の詳細と例については、「[EXPORT (DMX)](/sql/dmx/export-dmx)」および「[IMPORT (DMX)](/sql/dmx/import-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="112ab-106">For details of the syntax, together with examples, see [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx) and [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="112ab-107">Microsoft SQL Server Analysis Services データベースからオブジェクトをエクスポートまたはインポートするには、データベースまたはサーバーの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="112ab-107">You must be a database or server administrator to export or import objects from a Microsoft SQL Server Analysis Services database.</span></span>  
  
## <a name="exporting-data-mining-structures"></a><span data-ttu-id="112ab-108">データ マイニング構造のエクスポート</span><span class="sxs-lookup"><span data-stu-id="112ab-108">Exporting Data Mining Structures</span></span>  
 <span data-ttu-id="112ab-109">マイニング構造をエクスポートすると、EXPORT ステートメントによって関連するすべてのモデルが自動的にエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="112ab-109">When you export a mining structure, the EXPORT statement automatically exports all associated models.</span></span> <span data-ttu-id="112ab-110">エクスポートするオブジェクトを制御する場合は、各オブジェクトの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112ab-110">If you want to control the objects that are exported, you must specify each object by name.</span></span>  
  
 <span data-ttu-id="112ab-111">マイニング構造が処理されて結果がキャッシュされた場合 (既定の動作) に、マイニング構造をエクスポートすると、定義には、構造の基になっているデータの概要が含まれます。</span><span class="sxs-lookup"><span data-stu-id="112ab-111">If the mining structure has been processed and the results have been cached, which is the default behavior, when you export the mining structure, the definition contains a summary of the data on which the structure is based.</span></span> <span data-ttu-id="112ab-112">この概要を削除するには、`Process Clear Structure` 操作を実行して、マイニング構造に関連するキャッシュを消去する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112ab-112">To remove this summary, you must clear the cache associated with the mining structure by performing a `Process Clear Structure` operation.</span></span> <span data-ttu-id="112ab-113">詳細については、「 [マイニング構造の処理](process-a-mining-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="112ab-113">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
### <a name="exporting-data-mining-models"></a><span data-ttu-id="112ab-114">データ マイニング モデルのエクスポート</span><span class="sxs-lookup"><span data-stu-id="112ab-114">Exporting Data Mining Models</span></span>  
 <span data-ttu-id="112ab-115">`WITH DEPENDENCIES` キーワードを使用すると、マイニング モデルとその構造と共に、データ ソース定義およびデータ ソース ビュー定義をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="112ab-115">You can use the `WITH DEPENDENCIES` keyword to export the data source and data source view definition together with the mining model and its structure.</span></span>  
  
 <span data-ttu-id="112ab-116">依存関係をエクスポートせずにマイニング モデルをエクスポートすると、EXPORT ステートメントによってマイニング モデルとそのマイニング構造の定義がエクスポートされますが、データ ソースの定義はエクスポートされません。</span><span class="sxs-lookup"><span data-stu-id="112ab-116">When you export a mining model without exporting its dependencies, the EXPORT statement will export the definition of the mining model and its mining structure, but does not export the definition of the data sources.</span></span> <span data-ttu-id="112ab-117">そのため、モデルのインポート後は、直ちにモデルを参照できますが、ターゲット サーバーでマイニング モデルを再処理する場合や、基になるデータに対してクエリを実行する場合は、宛先サーバーに、対応するデータ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112ab-117">As a consequence, after you import the model you will be able to browse the model immediately, but if you want to reprocess the mining model on the target server, or run queries against the underlying data, you must create a corresponding data source on the destination server.</span></span>  
  
## <a name="importing-data-mining-structures-and-models"></a><span data-ttu-id="112ab-118">データ マイニング構造とデータ マイニング モデルのインポート</span><span class="sxs-lookup"><span data-stu-id="112ab-118">Importing Data Mining Structures and Models</span></span>  
 <span data-ttu-id="112ab-119">データ マイニング オブジェクトをインポートする場合、IMPORT ステートメントの実行時に接続しているサーバーまたはデータベースにオブジェクトがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="112ab-119">When you import a data mining object, the object is imported to the server and database to which you are connected when you execute the IMPORT statement.</span></span> <span data-ttu-id="112ab-120">サーバー上に存在しないデータベースがインポート ファイルに含まれている場合は、そのデータベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="112ab-120">If the import file includes a database that does not exist on the server, the database will be created.</span></span>  
  
 <span data-ttu-id="112ab-121">`Restore` コマンドを使用して、マイニング構造またはマイニング モデルをインポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="112ab-121">You can also import a mining structure or mining model by using the `Restore` command.</span></span> <span data-ttu-id="112ab-122">モデルや構造は、エクスポート元のデータベースと同じ名前のデータベースに復元されます。</span><span class="sxs-lookup"><span data-stu-id="112ab-122">Your models or structures will be restored into the database that has the same name as the database from which they were exported.</span></span> <span data-ttu-id="112ab-123">詳細については、「 [復元オプション](../multidimensional-models/restore-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="112ab-123">For more information, see [Restore Options](../multidimensional-models/restore-options.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="112ab-124">解説</span><span class="sxs-lookup"><span data-stu-id="112ab-124">Remarks</span></span>  
 <span data-ttu-id="112ab-125">同じ名前のモデルや構造がインポート先のサーバーに既に存在する場合は、モデルや構造をインポートできません。</span><span class="sxs-lookup"><span data-stu-id="112ab-125">You cannot import a model or structure to a server if a model or structure of the same name already exists on that server.</span></span> <span data-ttu-id="112ab-126">また、データ マイニング オブジェクトをエクスポートしてから、エクスポート ファイルに含まれるオブジェクトの名前を変更することもできません。</span><span class="sxs-lookup"><span data-stu-id="112ab-126">Also, you cannot export a data mining object and then modify the name of that object in the export file.</span></span> <span data-ttu-id="112ab-127">したがって、名前の競合が予想される場合は、ターゲット サーバー上のデータ マイニング オブジェクトを削除するか、定義をエクスポートする前にデータ マイニング オブジェクトの名前を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112ab-127">Therefore, if you anticipate naming conflicts, you should either delete the data mining object on the target server, or rename the data mining object before you export the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="112ab-128">参照</span><span class="sxs-lookup"><span data-stu-id="112ab-128">See Also</span></span>  
 [<span data-ttu-id="112ab-129">データ マイニング ソリューションおよびオブジェクトの管理</span><span class="sxs-lookup"><span data-stu-id="112ab-129">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  
