---
title: PowerPivot からのインポート (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importfromppt.f1
ms.assetid: ac1a6a79-bda3-4122-a717-8b1e2f77da02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 581259d79e5d84bd558ca3f13519fbf4dc0ba52f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712497"
---
# <a name="import-from-powerpivot-ssas-tabular"></a><span data-ttu-id="1aaba-102">PowerPivot からのインポート (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="1aaba-102">Import from PowerPivot (SSAS Tabular)</span></span>
  <span data-ttu-id="1aaba-103">このトピックでは、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の PowerPivot からのインポート プロジェクト テンプレートを使用して PowerPivot ブックからメタデータおよびデータをインポートし、新しい表形式モデル プロジェクトを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1aaba-103">This topic describes how to create a new tabular model project by importing the metadata and data from a PowerPivot workbook by using the Import from PowerPivot project template in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="create-a-new-tabular-model-from-a-powerpivot-for-excel-file"></a><span data-ttu-id="1aaba-104">Excel ファイルの PowerPivot から表形式の新しいモデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="1aaba-104">Create a new Tabular Model from a PowerPivot for Excel file</span></span>  
 <span data-ttu-id="1aaba-105">PowerPivot ブックからのインポートにより新しいテーブル モデル プロジェクトを作成すると、ブックの構造を定義するメタデータが使用され、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] にテーブル モデルの構造が作成および定義されます。</span><span class="sxs-lookup"><span data-stu-id="1aaba-105">When creating a new tabular model project by importing from a PowerPivot workbook, the metadata that defines the structure of the workbook is used to create and define the structure of the tabular model project in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="1aaba-106">テーブル、列、メジャー、リレーションシップなどのオブジェクトは、PowerPivot ブックにあるとおりにテーブル モデル プロジェクトで保持および表示されます。</span><span class="sxs-lookup"><span data-stu-id="1aaba-106">Objects such as tables, columns, measures, and relationships are retained and will appear in the tabular model project as they are in the PowerPivot workbook.</span></span> <span data-ttu-id="1aaba-107">.xlsx ブック ファイルに対する変更は行われません。</span><span class="sxs-lookup"><span data-stu-id="1aaba-107">No changes are made to the .xlsx workbook file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1aaba-108">リンク テーブルは、テーブル モデルではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1aaba-108">Tabular models do not support linked tables.</span></span> <span data-ttu-id="1aaba-109">リンク テーブルを含む PowerPivot ブックからインポートするとき、リンク テーブル データはコピー/貼り付けデータとして取り扱われ、Model.bim ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="1aaba-109">When importing from a PowerPivot workbook that contains a linked table, linked table data is treated as copy\pasted data and stored in the Model.bim file.</span></span> <span data-ttu-id="1aaba-110">コピー/貼り付けテーブルのプロパティを表示するとき、 **ソース データ** プロパティは無効であり、 **[テーブル]** メニューの **[テーブルのプロパティ]** ダイアログは無効です。</span><span class="sxs-lookup"><span data-stu-id="1aaba-110">When viewing properties for a copy\pasted table, the **Source Data** property is disabled and the **Table Properties** dialog on the **Table** menu is disabled.</span></span>  
>   
>  <span data-ttu-id="1aaba-111">モデルに埋め込まれているデータに追加できる行数は 10,000 行に制限されています。</span><span class="sxs-lookup"><span data-stu-id="1aaba-111">There is a limit of 10,000 rows that can be added to the data embedded in the model.</span></span> <span data-ttu-id="1aaba-112">PowerPivot からモデルをインポートして、"データが切り捨てられました。</span><span class="sxs-lookup"><span data-stu-id="1aaba-112">If you import a model from PowerPivot and see the error, "Data was truncated.</span></span> <span data-ttu-id="1aaba-113">貼り付けられたテーブルに1万行を超える値を含めることはできません。 PowerPivot モデルを修正するには、埋め込みデータを SQL Server のテーブルなどの別のデータソースに移動し、再インポートしてください。</span><span class="sxs-lookup"><span data-stu-id="1aaba-113">Pasted tables cannot contain more than 10000 rows" you should revise the PowerPivot model by moving the embedded data into another data source, such as a table in SQL Server, and then re-import.</span></span>  
  
 <span data-ttu-id="1aaba-114">ワークスペース データベースが、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と同じコンピューター (ローカル) の Analysis Services インスタンスにあるか、リモートの Analysis Services インスタンスにあるかにより、特に注意する点が変わります。</span><span class="sxs-lookup"><span data-stu-id="1aaba-114">There are special considerations depending on whether or not the workspace database is on an Analysis Services instance on the same computer (local) as [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or is on a remote Analysis Services instance..</span></span>  
  
 <span data-ttu-id="1aaba-115">ワークスペース データベースが、Analysis Services のローカル インスタンスにある場合は、メタデータとデータの両方を PowerPivot ブックからインポートできます。</span><span class="sxs-lookup"><span data-stu-id="1aaba-115">If the workspace database is on a local instance of Analysis Services, you can import both the metadata and data from the PowerPivot workbook.</span></span> <span data-ttu-id="1aaba-116">メタデータはブックからコピーされて、テーブル モデル プロジェクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1aaba-116">The metadata is copied from the workbook and used to create the tabular model project.</span></span> <span data-ttu-id="1aaba-117">その後、データはブックからコピーされ、プロジェクトのワークスペースデータベースに格納されます (コピー/貼り付けデータは、モデルの bim ファイルに格納されます)。</span><span class="sxs-lookup"><span data-stu-id="1aaba-117">The data is then copied from the workbook and stored in the project's workspace database (except for copy/pasted data, which is stored in the Model.bim file).</span></span>  
  
 <span data-ttu-id="1aaba-118">ワークスペース データベースが、Analysis Services のリモート インスタンスにある場合は、PowerPivot for Excel ブックからデータをインポートできません。</span><span class="sxs-lookup"><span data-stu-id="1aaba-118">If the workspace database is on a remote Analysis Services instance, you cannot import data from a PowerPivot for Excel workbook.</span></span> <span data-ttu-id="1aaba-119">ブックのメタデータはインポートできますが、インポートすると、スクリプトがリモートの Analysis Services インスタンスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="1aaba-119">You can still import the workbook metadata; however, this will cause a script to be run on the remote Analysis Services instance.</span></span> <span data-ttu-id="1aaba-120">信頼できる PowerPivot ブックからのみメタデータをインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aaba-120">You should only import metadata from a trusted PowerPivot workbook.</span></span> <span data-ttu-id="1aaba-121">データは、データ ソース接続に定義されたソースからインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aaba-121">Data must be imported from sources defined in the data source connections.</span></span> <span data-ttu-id="1aaba-122">PowerPivot ブックのコピー/貼り付けデータとリンク テーブル データは、テーブル モデル プロジェクトにコピーして貼り付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="1aaba-122">Copy/pasted and linked table data in the PowerPivot workbook must be copied and pasted into the tabular model project.</span></span>  
  
#### <a name="to-create-a-new-tabular-model-project-from-a-powerpivot-for-excel-file"></a><span data-ttu-id="1aaba-123">PowerPivot for Excel ファイルから新しいテーブル モデル プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="1aaba-123">To create a new tabular model project from a PowerPivot for Excel file</span></span>  
  
1.  <span data-ttu-id="1aaba-124">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[ファイル]** メニューの **[新規作成]** をクリックし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aaba-124">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="1aaba-125">[**新しいプロジェクト**] ダイアログボックスの [**インストールされているテンプレート**] で [**ビジネスインテリジェンス**] をクリックし、[ **PowerPivot からのインポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aaba-125">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, and then click **Import from PowerPivot**.</span></span>  
  
3.  <span data-ttu-id="1aaba-126">[**名前**] にプロジェクトの名前を入力し、場所とソリューション名を指定して、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aaba-126">In  **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="1aaba-127">**[ファイルを開く]** ダイアログ ボックスで、インポートするモデル メタデータおよびデータを含む [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] ファイルを選択し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1aaba-127">In the **Open** dialog box, select the [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] file that contains the model metadata and data you want to import, and then click **Open**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aaba-128">参照</span><span class="sxs-lookup"><span data-stu-id="1aaba-128">See Also</span></span>  
 <span data-ttu-id="1aaba-129">[ワークスペースデータベース &#40;SSAS 表形式&#41;](workspace-database-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="1aaba-129">[Workspace Database &#40;SSAS Tabular&#41;](workspace-database-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="1aaba-130">データのコピーと貼り付け &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="1aaba-130">Copy and Paste Data &#40;SSAS Tabular&#41;</span></span>](../copy-and-paste-data-ssas-tabular.md)  
  
  
