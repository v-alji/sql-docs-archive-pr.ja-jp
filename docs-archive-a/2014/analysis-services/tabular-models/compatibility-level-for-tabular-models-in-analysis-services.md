---
title: 互換性レベル (SSAS 表形式 SP1) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2853cd5509b66dbfaadd78c578b9676399e81977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741333"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a><span data-ttu-id="6b271-102">互換性レベル (SSAS テーブル SP1)</span><span class="sxs-lookup"><span data-stu-id="6b271-102">Compatibility Level (SSAS Tabular SP1)</span></span>
  <span data-ttu-id="6b271-103">新しいテーブルモデルプロジェクトを作成するとき、既存のテーブルモデルプロジェクトをアップグレードするとき、既存の配置済みテーブルモデルデータベースをアップグレードするとき、または PowerPivot ブックをインポートするときに、*互換性レベル*を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6b271-103">You can specify *Compatibility Level* when creating new Tabular model projects, when upgrading existing Tabular model projects, when upgrading existing deployed Tabular model databases, or when importing PowerPivot workbooks.</span></span>  
  
## <a name="compatibility-level"></a><span data-ttu-id="6b271-104">互換性レベル</span><span class="sxs-lookup"><span data-stu-id="6b271-104">Compatibility Level</span></span>  
 <span data-ttu-id="6b271-105">通常は、実稼働コンピューターにインストールする前に、開発用コンピューターとテスト用コンピューターに新しいバージョンとサービス パックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="6b271-105">It is common to install new versions and service packs on development and test computers prior to installing on production computers.</span></span> <span data-ttu-id="6b271-106">このような場合は、新しいテーブル モデル プロジェクトと実稼働環境に既に配置されているテーブル モデル プロジェクトの両方に対する互換性レベルの設定について理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="6b271-106">In such cases, it is important to understand setting compatibility level for both new Tabular model projects as well as those that have already been deployed into a production environment.</span></span>  
  
 <span data-ttu-id="6b271-107">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] の Analysis Services インスタンスは、次の互換性レベル (データベース バージョン) をサポートします。</span><span class="sxs-lookup"><span data-stu-id="6b271-107">A [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Analysis Services instance supports the following compatibility levels (database version):</span></span>  
  
-   <span data-ttu-id="6b271-108">SQL Server 2012 (1100)</span><span class="sxs-lookup"><span data-stu-id="6b271-108">SQL Server 2012 (1100)</span></span>  
  
-   <span data-ttu-id="6b271-109">SQL Server 2012 SP1 (1103)</span><span class="sxs-lookup"><span data-stu-id="6b271-109">SQL Server 2012 SP1 (1103)</span></span>  
  
-   <span data-ttu-id="6b271-110">SQL Server 2014 (1103)</span><span class="sxs-lookup"><span data-stu-id="6b271-110">SQL Server 2014 (1103)</span></span>  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a><span data-ttu-id="6b271-111">新しいテーブル モデル プロジェクトを作成するときに互換性レベルを設定する</span><span class="sxs-lookup"><span data-stu-id="6b271-111">Set compatibility level when creating a new Tabular model project</span></span>  
 <span data-ttu-id="6b271-112">SQL Server Data Tools (SSDT) で新しいテーブルモデルプロジェクトを作成するときに、[**新しい表形式プロジェクトのオプション**] ダイアログで互換性レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6b271-112">When creating a new Tabular model project in SQL Server Data Tools (SSDT), on the **New Tabular project options** dialog you can specify the compatibility level.</span></span> <span data-ttu-id="6b271-113">作成した新しいプロジェクトの配置先として、[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降の Analysis Services インスタンス、または SQL Server 2012 Analysis Services インスタンス (Service Pack 1 なし) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="6b271-113">You can choose between creating a new project to be deployed to an [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later Analysis Services instance or to an SQL Server 2012 Analysis Services instance (without Service Pack 1).</span></span>  
  
 <span data-ttu-id="6b271-114">**[今後、このメッセージを表示しない]** オプションを選択することで、既定の互換性レベルを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="6b271-114">You can also specify a default compatibility level by selecting the **Do not show this message again** option.</span></span> <span data-ttu-id="6b271-115">以降、すべてのプロジェクトで、指定した互換性レベルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6b271-115">All subsequent projects will use the compatibility level you specified.</span></span> <span data-ttu-id="6b271-116">既定の互換性レベルは、SSDT の [オプション] で変更できます。</span><span class="sxs-lookup"><span data-stu-id="6b271-116">You can change the default compatibility level in SSDT in Options.</span></span>  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a><span data-ttu-id="6b271-117">既存のテーブル モデル プロジェクトを 1103 互換性レベルにアップグレードする</span><span class="sxs-lookup"><span data-stu-id="6b271-117">Upgrade an existing Tabular model project to 1103 compatibility level</span></span>  
 <span data-ttu-id="6b271-118">[ [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] モデルの**プロパティ**] ウィンドウの [**互換性レベル**] プロパティを使用して、1103以降をインストールする前に、SSDT で作成したテーブルモデルプロジェクトをアップグレードすることができます。</span><span class="sxs-lookup"><span data-stu-id="6b271-118">You can upgrade a Tabular model project created in SSDT prior to installing [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later to be database version 1103 compatible by using the **Compatibility Level** property in the model **Properties** window.</span></span> <span data-ttu-id="6b271-119">テーブル モデル プロジェクトをアップグレードするには、SSDT をインストールするコンピューターに [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降がインストールされ、ワークスペース データベースが存在する Analysis Services インスタンス上にも [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b271-119">In order to upgrade a Tabular model project, the computer on which SSDT is installed must have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed and the Analysis Services instance on which the workspace database resides must also have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed.</span></span> <span data-ttu-id="6b271-120">以前のバージョンにダウングレードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6b271-120">You cannot downgrade to an earlier version.</span></span>  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a><span data-ttu-id="6b271-121">配置済みテーブル モデル データベースを 1103 互換性レベルにアップグレードする</span><span class="sxs-lookup"><span data-stu-id="6b271-121">Upgrade a deployed Tabular model database to 1103 compatibility level</span></span>  
 <span data-ttu-id="6b271-122">**データベースプロパティ**の [**互換性レベル**] プロパティを使用すると、既存の配置済みテーブルモデルデータベースを SQL Server Management Studio (SSMS) で互換性のあるデータベースバージョン1103にアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="6b271-122">You can upgrade an existing deployed Tabular model database to database version 1103 compatible in SQL Server Management Studio (SSMS) by using the **Compatibility Level** property in **Database Properties**.</span></span> <span data-ttu-id="6b271-123">アップグレードするには、SQL Server Analysis Services インスタンスがインストールされるコンピューターに [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b271-123">In order to upgrade, the computer on which the SQL Server Analysis Services instance is installed must have [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] or later installed.</span></span> <span data-ttu-id="6b271-124">配置済みのテーブル モデル データベースを以前のバージョンのインスタンスにダウングレードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6b271-124">You cannot downgrade a deployed Tabular model database to an earlier version.</span></span>  
  
### <a name="import-from-powerpivot"></a><span data-ttu-id="6b271-125">PowerPivot からのインポート</span><span class="sxs-lookup"><span data-stu-id="6b271-125">Import from PowerPivot</span></span>  
 <span data-ttu-id="6b271-126">新しいテーブル モデル プロジェクトを PowerPivot からインポートすることで作成する場合は、互換性レベルを既定の互換性レベルにアップグレードする (SSDT で構成済みの場合) か、PowerPivot ワークブックに既に指定されている互換性のままにするかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6b271-126">When creating a new Tabular model project by importing from PowerPivot, you can specify if you want to upgrade the compatibility level to the default compatibility level (if previously configured in SSDT) or leave the compatibility level to that already specified in the PowerPivot workbook.</span></span>  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a><span data-ttu-id="6b271-127">SSMS のテーブル モデル データベースの互換性レベルを確認する</span><span class="sxs-lookup"><span data-stu-id="6b271-127">Check compatibility level for a Tabular model database in SSMS</span></span>  
 <span data-ttu-id="6b271-128">SSMS のテーブルモデルデータベースの互換性レベルを確認するには、[データベースのプロパティ] の [**互換性レベル**] プロパティを表示します (の新機能 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] )。 **Database Properties**</span><span class="sxs-lookup"><span data-stu-id="6b271-128">You can check the compatibility level for a Tabular model database in SSMS by viewing the **Compatibility Level** property (new in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Database Properties**.</span></span>  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a><span data-ttu-id="6b271-129">Analysis Services インスタンスでサポートされる互換性レベルを SSMS で確認する</span><span class="sxs-lookup"><span data-stu-id="6b271-129">Check supported compatibility level for an Analysis Services instance in SSMS</span></span>  
 <span data-ttu-id="6b271-130">SSMS でサポートされている互換性レベルを確認するには、Analysis Services のプロパティの**情報**ページ (の新機能) で [**サポートされている互換性レベル**] プロパティを表示し [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] ます。 **Analysis Services Properties**</span><span class="sxs-lookup"><span data-stu-id="6b271-130">You can check the supported compatibility level in SSMS by viewing the **Supported Compatibility Level** property on the **Information** page (new in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Analysis Services Properties**.</span></span> <span data-ttu-id="6b271-131">サポートされる互換性レベル 1103 は、SQL Server SP1 以降がインストールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="6b271-131">A supported compatibility level of 1103 indicates SQL Server SP1 or later is installed.</span></span> <span data-ttu-id="6b271-132">サポートされる互換性レベルは変更できません。</span><span class="sxs-lookup"><span data-stu-id="6b271-132">The supported compatibility level cannot be changed.</span></span>  
  
  
