---
title: Excel でのテーブルモデルの分析 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
author: minewiskan
ms.author: owend
ms.openlocfilehash: fae542ffb5b470d23d9cf27fcc11367f571e7cec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643490"
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a><span data-ttu-id="0d3f4-102">Excel でのテーブル モデルの分析 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="0d3f4-102">Analyze a Tabular Model in Excel (SSAS Tabular)</span></span>
  <span data-ttu-id="0d3f4-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の [Excel で分析] 機能によって Microsoft Excel が開き、モデル ワークスペース データベースへのデータ ソース接続が作成され、ピボットテーブルがワークシートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-103">The Analyze in Excel feature in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] opens Microsoft Excel, creates a data source connection to the model workspace database, and adds a PivotTable to the worksheet.</span></span> <span data-ttu-id="0d3f4-104">モデル オブジェクト (テーブル、列、メジャー、階層、および KPI) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-104">Model objects (tables, columns, measures, hierarchies, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d3f4-105">[Excel で分析] 機能を使用するには、レポート デザイナーがインストールされているコンピューターに Microsoft Office 2003 以降が [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]と同じコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-105">To use the Analyze in Excel feature, you must have Microsoft Office 2003 or later installed on the same computer as [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="0d3f4-106">Office が同じコンピューターにインストールされていない場合は、別のコンピューターの Excel を使用して、データ ソースとしてモデル ワークスペース データベースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-106">If Office is not installed on the same computer, you can use Excel on another computer and connect to the model workspace database as a data source.</span></span> <span data-ttu-id="0d3f4-107">これにより、ピボットテーブルをワークシートに手動で追加することができます。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-107">You can then manually add a PivotTable to the worksheet.</span></span> <span data-ttu-id="0d3f4-108">モデル オブジェクト (テーブル、列、メジャー、および KPI) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-108">Model objects (tables, columns, measures, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="0d3f4-109">タスク</span><span class="sxs-lookup"><span data-stu-id="0d3f4-109">Tasks</span></span>  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a><span data-ttu-id="0d3f4-110">[Excel で分析] 機能を使用してテーブル モデル プロジェクトを分析するには</span><span class="sxs-lookup"><span data-stu-id="0d3f4-110">To analyze a tabular model project by using the Analyze in Excel feature</span></span>  
  
1.  <span data-ttu-id="0d3f4-111">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-111">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="0d3f4-112">**[資格情報とパースペクティブの選択]** ダイアログ ボックスで、モデル ワークスペース データ ソースに接続するための次のいずれかの資格情報オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-112">In the **Choose Credential and Perspective** dialog box, select one of the following credential options to connect to the model workspace data source:</span></span>  
  
    -   <span data-ttu-id="0d3f4-113">現在のユーザー アカウントを使用するには、 **[現在の Windows ユーザー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-113">To use the current user account, select **Current Windows User**.</span></span>  
  
    -   <span data-ttu-id="0d3f4-114">別のユーザー アカウントを使用するには、 **[別の Windows ユーザー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-114">To use a different user account, select **Other Windows User**.</span></span>  
  
         <span data-ttu-id="0d3f4-115">通常、このユーザー アカウントはロールのメンバーになります。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-115">Typically, this user account will be a member of a role.</span></span> <span data-ttu-id="0d3f4-116">パスワードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-116">No password is required.</span></span> <span data-ttu-id="0d3f4-117">このアカウントを使用できるのは、ワークスペース データベースに Excel で接続している場合のみです。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-117">The account can only be used in the context of an Excel connection to the workspace database.</span></span>  
  
    -   <span data-ttu-id="0d3f4-118">セキュリティ ロールを使用するには、 **[ロール]** を選択して、一覧から 1 つ以上のロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-118">To use a security role, select **Role**, and then in the listbox, select one or more roles.</span></span>  
  
         <span data-ttu-id="0d3f4-119">セキュリティ ロールはロール マネージャーを使用して定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-119">Security roles must be defined using the Role Manager.</span></span> <span data-ttu-id="0d3f4-120">詳細については、「[ロールの作成および管理 (SSAS テーブル)](roles-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-120">For more information, see [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
3.  <span data-ttu-id="0d3f4-121">パースペクティブを使用するには、 **[パースペクティブ]** ボックスの一覧からパースペクティブを選択します。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-121">To use a perspective, in the **Perspective** listbox, select a perspective.</span></span>  
  
     <span data-ttu-id="0d3f4-122">パースペクティブ (既定値以外) は [パースペクティブ] ダイアログ ボックスを使用して定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-122">Perspectives (other than default) must be defined using the Perspectives dialog box.</span></span> <span data-ttu-id="0d3f4-123">詳細については、「 [SSAS テーブル&#41;&#40;パースペクティブの作成と管理](perspectives-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-123">For more information, see [Create and Manage Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0d3f4-124">Excel のピボットテーブルのフィールドの一覧は、モデル デザイナーでモデル プロジェクトに変更を加えても自動的に更新されません。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-124">The PivotTable Field List in Excel does not refresh automatically as you make changes to the model project in the model designer.</span></span> <span data-ttu-id="0d3f4-125">ピボットテーブルのフィールドの一覧を更新するには、Excel の **[オプション]** リボンで **[更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0d3f4-125">To refresh the PivotTable Field List, in Excel, on the **Options** ribbon, click **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d3f4-126">参照</span><span class="sxs-lookup"><span data-stu-id="0d3f4-126">See Also</span></span>  
 [<span data-ttu-id="0d3f4-127">Excel で分析 &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="0d3f4-127">Analyze in Excel &#40;SSAS Tabular&#41;</span></span>](analyze-in-excel-ssas-tabular.md)  
  
  
