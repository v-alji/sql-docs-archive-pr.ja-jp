---
title: Analysis Services からのインポート (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9a21b23-3a06-4ef8-bc06-9c79cdc54870
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7d6c3d226e46cdb4101bc8db52830046d27b0706
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712506"
---
# <a name="import-from-analysis-services-ssas-tabular"></a><span data-ttu-id="97ab7-102">Analysis Services からのインポート (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="97ab7-102">Import from Analysis Services (SSAS Tabular)</span></span>
  <span data-ttu-id="97ab7-103">このトピックでは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のサーバーからインポート プロジェクト テンプレートを使用して既存の表形式モデルからメタデータをインポートし、新しい表形式モデル プロジェクトを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="97ab7-103">This topic describes how to create a new tabular model project by importing the metadata from an existing tabular model by using the Import from Server project template in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a><span data-ttu-id="97ab7-104">Analysis Services の既存のモデルからのメタデータのインポートによる新しいモデルの作成</span><span class="sxs-lookup"><span data-stu-id="97ab7-104">Create a new model by importing metadata from an existing model in Analysis Services</span></span>  
 <span data-ttu-id="97ab7-105">Analysis Services サーバーの既存のテーブル モデルからメタデータをコピーして、新しいテーブル モデル プロジェクトを作成するには、サーバーからインポート プロジェクト テンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="97ab7-105">You can use the Import from Server project template to create a new tabular model project by copying the metadata from an existing tabular model on an Analysis Services server.</span></span> <span data-ttu-id="97ab7-106">新しいプロジェクトは、インポート元のモデルと同じデータ ソース接続、テーブル、リレーションシップ、メジャー、KPI、ロール、階層、パースペクティブ、およびパーティションを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="97ab7-106">The new project will be created with the same data source connections, tables, relationships, measures, KPIs, roles, hierarchies, perspectives, and partitions as the model it was imported from.</span></span> <span data-ttu-id="97ab7-107">ただし、データは既存のモデルから新しいモデル ワークスペースにコピーされません。</span><span class="sxs-lookup"><span data-stu-id="97ab7-107">The data, however, is not copied from the existing model to the new model workspace.</span></span> <span data-ttu-id="97ab7-108">インポート プロセスが完了し、新しいモデル プロジェクトが作成された後、[すべて処理] を実行し、データ ソースから新しいモデル プロジェクト ワークスペース データベースにデータを読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="97ab7-108">Once the import process has completed, and the new model project created, you must run a Process All to load the data from the data sources into the new model project workspace database.</span></span>  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a><span data-ttu-id="97ab7-109">既存のモデルからのメタデータのインポートによって、新しいモデルを作成するには</span><span class="sxs-lookup"><span data-stu-id="97ab7-109">To create a new model by importing metadata from an existing model</span></span>  
  
1.  <span data-ttu-id="97ab7-110">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[ファイル]** メニューの **[新規作成]** をクリックし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97ab7-110">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], on the **File** menu, click **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="97ab7-111">**[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]** で **[ビジネス インテリジェンス]** をクリックし、 **[サーバーからインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97ab7-111">In the **New Project** dialog box, under **Installed Templates**, click **Business Intelligence**, and then click **Import from Server**.</span></span>  
  
3.  <span data-ttu-id="97ab7-112">**[名前]** でプロジェクトの名前を入力し、場所とソリューション名を指定してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97ab7-112">In **Name**, type a name for the project, then specify a location and solution name, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="97ab7-113">**[Analysis Services からのインポート]** ダイアログ ボックスの **[サーバー名]** で、インポートするモデル メタデータを含む Analysis Services サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="97ab7-113">In the **Import from Analysis Services** dialog box, in **Server Name**, specify the name of the Analysis Services server that contains the model metadata you want to import.</span></span>  
  
5.  <span data-ttu-id="97ab7-114">**[データベース名]** で、インポートするモデル メタデータを含むテーブル モデル データベースを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="97ab7-114">In **Database Name**, select the tabular model database that contains the model metadata you want to import, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97ab7-115">参照</span><span class="sxs-lookup"><span data-stu-id="97ab7-115">See Also</span></span>  
 [<span data-ttu-id="97ab7-116">プロジェクトのプロパティ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="97ab7-116">Project Properties &#40;SSAS Tabular&#41;</span></span>](properties-ssas-tabular.md)  
  
  
