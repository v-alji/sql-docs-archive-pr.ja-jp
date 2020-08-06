---
title: データマイニングオブジェクトの移動 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], models
- data mining editor [Analysis Services]
- mining models [Analysis Services], managing
- Data Mining Designer
- mining models [Analysis Services], modifying
ms.assetid: bc108407-2603-4387-b930-b5bb9df78069
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2b10be3a79487376b173eab87059404b7f7a618e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712646"
---
# <a name="moving-data-mining-objects"></a><span data-ttu-id="6967d-102">データ マイニング オブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="6967d-102">Moving Data Mining Objects</span></span>
  <span data-ttu-id="6967d-103">データ マイニング オブジェクトを移動する最も一般的なシナリオは、テスト環境または分析環境から運用環境にモデルを配置する方法、または他のユーザーとモデルを共有する方法です。</span><span class="sxs-lookup"><span data-stu-id="6967d-103">The most common scenarios for moving data mining objects are to deploy a model from a testing or analysis environment to a production environment, or to share models with other users.</span></span>  
  
 <span data-ttu-id="6967d-104">このトピックでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で用意されている、データ マイニング オブジェクトを移動するためのツールおよびスクリプト言語の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6967d-104">This topic describes how you can use the tools and scripting languages provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], for moving data mining objects.</span></span>  
  
## <a name="moving-data-mining-objects-between-databases-or-servers"></a><span data-ttu-id="6967d-105">データベース間またはサーバー間でのデータ マイニング オブジェクトの移動</span><span class="sxs-lookup"><span data-stu-id="6967d-105">Moving Data Mining Objects between Databases or Servers</span></span>  
 <span data-ttu-id="6967d-106">次の方法で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース間または [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス間でデータ マイニング オブジェクトを移動できます。</span><span class="sxs-lookup"><span data-stu-id="6967d-106">You can move data mining objects between [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases or between instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in the following ways:</span></span>  
  
-   <span data-ttu-id="6967d-107">別のデータベースにソリューションを配置し直します。</span><span class="sxs-lookup"><span data-stu-id="6967d-107">Re-deploying the solution to a different database.</span></span>  
  
-   <span data-ttu-id="6967d-108">個々のオブジェクトのスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="6967d-108">Scripting individual objects.</span></span>  
  
-   <span data-ttu-id="6967d-109">データベースをバックアップしてからそのコピーを復元します。</span><span class="sxs-lookup"><span data-stu-id="6967d-109">Backing up and then restoring a copy of the database.</span></span>  
  
-   <span data-ttu-id="6967d-110">構造とモデルをエクスポートおよびインポートします。</span><span class="sxs-lookup"><span data-stu-id="6967d-110">Exporting and importing structures and models.</span></span>  
  
 <span data-ttu-id="6967d-111">次のセクションでは、これらのオプションについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="6967d-111">The following section explains these options in more detail.</span></span>  
  
### <a name="deploying"></a><span data-ttu-id="6967d-112">デプロイ中</span><span class="sxs-lookup"><span data-stu-id="6967d-112">Deploying</span></span>  
 <span data-ttu-id="6967d-113">ソリューションを別のサーバーまたはデータベースに配置するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を使用して作成されたソリューション ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="6967d-113">Deploying the solution to a different server or database requires that you have the solution file that was created by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6967d-114">Analysis Services ソリューションの配置の詳細については、「[Analysis Services プロジェクトの配置 &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6967d-114">For more information about deploying Analysis Services solutions, see [Deploy Analysis Services Projects &#40;SSDT&#41;](../multidimensional-models/deploy-analysis-services-projects-ssdt.md).</span></span>  
  
### <a name="scripting"></a><span data-ttu-id="6967d-115">スクリプト</span><span class="sxs-lookup"><span data-stu-id="6967d-115">Scripting</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="6967d-116">では、オブジェクトのスクリプト作成に使用できる言語がいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="6967d-116">provides several languages that you can use to script objects.</span></span>  
  
-   <span data-ttu-id="6967d-117">**XMLA:**[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でオブジェクトを右クリックして、XMLA を使用してオブジェクトのスクリプトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="6967d-117">**XMLA**: You can script objects using XMLA by right-clicking objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6967d-118">作成したスクリプトを実行するには、ターゲット サーバーの **XMLA クエリ** ウィンドウでスクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="6967d-118">To execute the script, open it in an **XMLA Query** window on the target server.</span></span>  
  
-   <span data-ttu-id="6967d-119">**DMX:**[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で用意されているテンプレートまたはいずれかのクエリ ビルダーを使用して、スクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6967d-119">**DMX**: You can create scripts by using templates or one of the query builders provided in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="6967d-120">ただし、スクリプト言語によって、実行できるタスクはそれぞれ異なります。</span><span class="sxs-lookup"><span data-stu-id="6967d-120">Note, however, that there are differences in the tasks that you can perform with each scripting language:</span></span>  
  
-   <span data-ttu-id="6967d-121">オブジェクトの説明やデータ バインドなどのプロパティは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 言語を使用した場合のみ作成または変更できます。DMX を使用した場合は作成および変更できません。</span><span class="sxs-lookup"><span data-stu-id="6967d-121">Properties such as the object description and data bindings can only by created or changed by using [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL languages, not by using DMX.</span></span>  
  
-   <span data-ttu-id="6967d-122">マイニング オブジェクトのインポートおよびエクスポートは、DMX でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6967d-122">Only DMX supports the import and export of mining objects.</span></span>  
  
-   <span data-ttu-id="6967d-123">PMML の生成または PMML からのモデル定義のインポートは、DMX でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6967d-123">Only DMX supports generating PMML or importing model definitions from PMML.</span></span>  
  
-   <span data-ttu-id="6967d-124">アプリケーション データを使用したモデルのトレーニングは、DMX でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6967d-124">Only DMX supports training a model with application data.</span></span> <span data-ttu-id="6967d-125">さらに、DMX INSERT INTO ステートメントでは、キー列の値を指定せずにモデルをトレーニングすることができます。</span><span class="sxs-lookup"><span data-stu-id="6967d-125">Moreover, the DMX INSERT INTO statement supports training a model without providing values for a key column.</span></span>  
  
 <span data-ttu-id="6967d-126">詳細については、「 [Analysis Services スクリプト言語 (ASSL) での開発](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6967d-126">For more information, see [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).</span></span>  
  
### <a name="backup-and-restore"></a><span data-ttu-id="6967d-127">バックアップと復元</span><span class="sxs-lookup"><span data-stu-id="6967d-127">Backup and Restore</span></span>  
 <span data-ttu-id="6967d-128">Analysis Services データベース全体のバックアップおよび復元は、データ マイニング ソリューションが OLAP オブジェクトに依存している場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="6967d-128">Backup and restore of an entire Analysis Services database is the method of choice if your data mining solution relies on OLAP objects.</span></span> [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="6967d-129">にはバックアップ/復元機能が用意されており、データベースをよりすばやく簡単にバックアップできます。</span><span class="sxs-lookup"><span data-stu-id="6967d-129">provides backup and restore functionality that makes database backups faster and easier.</span></span>  
  
 <span data-ttu-id="6967d-130">詳細については、「 [Analysis Services データベースのバックアップと復元](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6967d-130">For more information about backup, see [Backup and Restore of Analysis Services Databases](../multidimensional-models/backup-and-restore-of-analysis-services-databases.md).</span></span>  
  
### <a name="exporting-and-importing"></a><span data-ttu-id="6967d-131">エクスポートとインポート</span><span class="sxs-lookup"><span data-stu-id="6967d-131">Exporting and Importing</span></span>  
 <span data-ttu-id="6967d-132">DMX ステートメントを使用してマイニング モデルとマイニング構造をエクスポートし、インポートし直す方法は、リレーショナル データ マイニング オブジェクトを個別に移動したりバックアップしたりする場合に最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="6967d-132">Exporting and then re-importing mining models and structures by using DMX statements is the easiest way to move or back up individual relational data mining objects.</span></span> <span data-ttu-id="6967d-133">これらの操作の DMX 構文の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6967d-133">For more information about the DMX syntax for these operations, see the following topics:</span></span>  
  
-   [<span data-ttu-id="6967d-134">エクスポート &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6967d-134">EXPORT &#40;DMX&#41;</span></span>](/sql/dmx/export-dmx)  
  
-   [<span data-ttu-id="6967d-135">インポート &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="6967d-135">IMPORT &#40;DMX&#41;</span></span>](/sql/dmx/import-dmx)  
  
 <span data-ttu-id="6967d-136">INCLUDE DEPENDENCIES オプションを指定すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって必要なデータ ソース ビューの定義もエクスポートされます。この場合、モデルや構造をインポートすると、ターゲット サーバーにデータ ソース ビューが再作成されます。</span><span class="sxs-lookup"><span data-stu-id="6967d-136">If you specify the INCLUDE DEPENDENCIES option, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will also export the definition of any required data source views, and when you import the model or structure, it will re-create the data source view on the target server.</span></span> <span data-ttu-id="6967d-137">モデルのインポートが完了したら、オブジェクトに対して必要なマイニング権限を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6967d-137">After you have finished importing the model, make sure to set the necessary mining permissions on the object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6967d-138">DMX を使用して OLAP モデルをエクスポートおよびインポートすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6967d-138">You cannot export and import OLAP models by using DMX.</span></span> <span data-ttu-id="6967d-139">マイニング モデルが OLAP キューブに基づいている場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で用意されている、データベース全体をバックアップおよび復元する機能を使用するか、キューブとモデルを配置し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6967d-139">If your mining model is based on an OLAP cube, you must use the functionality provided by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] for backing up and restoring an entire database, or redeploy the cube and its models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6967d-140">参照</span><span class="sxs-lookup"><span data-stu-id="6967d-140">See Also</span></span>  
 [<span data-ttu-id="6967d-141">データ マイニング ソリューションおよびオブジェクトの管理</span><span class="sxs-lookup"><span data-stu-id="6967d-141">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  
