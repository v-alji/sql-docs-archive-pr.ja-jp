---
title: '[データベースのプロパティ] ダイアログボックス (SSAS-多次元) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.databaseproperties.f1
ms.assetid: 70f000b7-917f-4699-b142-7a0d13ff767c
author: minewiskan
ms.author: owend
ms.openlocfilehash: a465c333557f19e9572cd9c2b1f7c80aaf4ab5bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711133"
---
# <a name="database-properties-dialog-box-ssas---multidimensional"></a><span data-ttu-id="1232c-102">[データベースのプロパティ] ダイアログ ボックス (SSAS - 多次元)</span><span class="sxs-lookup"><span data-stu-id="1232c-102">Database Properties Dialog Box (SSAS - Multidimensional)</span></span>
  <span data-ttu-id="1232c-103">**の** [データベースのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="1232c-103">Use the **Database Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to set the properties of a database in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="1232c-104">**[データベースのプロパティ]** ダイアログ ボックスを表示するには、オブジェクト エクスプローラーでデータベースを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1232c-104">You can display the **Database Properties** dialog box by right-clicking a database in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1232c-105">Options</span><span class="sxs-lookup"><span data-stu-id="1232c-105">Options</span></span>  
  
|<span data-ttu-id="1232c-106">期間</span><span class="sxs-lookup"><span data-stu-id="1232c-106">Term</span></span>|<span data-ttu-id="1232c-107">定義</span><span class="sxs-lookup"><span data-stu-id="1232c-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="1232c-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="1232c-108">**Name**</span></span>|<span data-ttu-id="1232c-109">データベースの名前を変更するときに、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="1232c-109">Type to change the name of the database.</span></span>|  
|<span data-ttu-id="1232c-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="1232c-110">**ID**</span></span>|<span data-ttu-id="1232c-111">データベースの ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1232c-111">Displays the identifier of the database.</span></span>|  
|<span data-ttu-id="1232c-112">**説明**</span><span class="sxs-lookup"><span data-stu-id="1232c-112">**Description**</span></span>|<span data-ttu-id="1232c-113">データベースの説明を変更するときに、説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="1232c-113">Type to change the description of the database.</span></span>|  
|<span data-ttu-id="1232c-114">**[タイムスタンプの作成]**</span><span class="sxs-lookup"><span data-stu-id="1232c-114">**Create Timestamp**</span></span>|<span data-ttu-id="1232c-115">データベースが作成された日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1232c-115">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="1232c-116">**[スキーマの最終更新]**</span><span class="sxs-lookup"><span data-stu-id="1232c-116">**Last Schema Update**</span></span>|<span data-ttu-id="1232c-117">データベースのメタデータが最後に更新されたときの日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1232c-117">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="1232c-118">**[最終更新]**</span><span class="sxs-lookup"><span data-stu-id="1232c-118">**Last Update**</span></span>|<span data-ttu-id="1232c-119">データベースのデータが最後に更新されたときの日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1232c-119">Displays the date and time the data for the database was last updated.</span></span>|  
|<span data-ttu-id="1232c-120">**[データ ソースの権限借用情報]**</span><span class="sxs-lookup"><span data-stu-id="1232c-120">**Data Source Impersonation Info**</span></span>|<span data-ttu-id="1232c-121">データベースに含まれているデータ ソースに接続したり操作したりするときに、データベースで使用される権限借用情報を選択します。</span><span class="sxs-lookup"><span data-stu-id="1232c-121">Select the impersonation information used by the database when connecting to and interacting with data sources contained by the database.</span></span> <span data-ttu-id="1232c-122">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1232c-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1232c-123">**ImpersonateAccount** (特定の Windows ユーザー名とパスワードを使用します)。</span><span class="sxs-lookup"><span data-stu-id="1232c-123">**ImpersonateAccount** (use a specific Windows user name and password).</span></span><br /><br /> <span data-ttu-id="1232c-124">**ImpersonateService** (サービス アカウントを使用します)。</span><span class="sxs-lookup"><span data-stu-id="1232c-124">**ImpersonateService** (use the service account).</span></span><br /><br /> <span data-ttu-id="1232c-125">**ImpersonateCurrentUser** (現在のユーザーの資格情報を使用します)。</span><span class="sxs-lookup"><span data-stu-id="1232c-125">**ImpersonateCurrentUser** (use the credentials of the current user).</span></span><br /><br /> <span data-ttu-id="1232c-126">**Default** (MOLAP 操作にはサービス アカウントを使用し、データ マイニングには現在のユーザーを使用します)。</span><span class="sxs-lookup"><span data-stu-id="1232c-126">**Default** (use the service account for MOLAP operations and current user for data mining).</span></span><br /><br /> <span data-ttu-id="1232c-127">データベース レベルでデータ ソースの権限借用の設定を行えますが、そのように設定すると、権限借用の設定に対して **[継承]** を指定しているデータ ソースだけが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="1232c-127">Although you can set data source impersonation settings at the database level, doing so will only affect those data sources that specify **Inherit** for their impersonation settings.</span></span> <span data-ttu-id="1232c-128">データ ソースで直接指定された権限借用の設定は、常に、データベース レベルで指定されている設定をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="1232c-128">Impersonation settings specified directly on the data source will always override any settings that are specified at the database level.</span></span><br /><br /> <span data-ttu-id="1232c-129">権限借用のオプションを選択するときは、サポートされる必要のある操作の種類を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="1232c-129">When choosing an impersonation option, consider the types of operations that will need to be supported.</span></span> <span data-ttu-id="1232c-130">処理などの一部の操作は実行できません。</span><span class="sxs-lookup"><span data-stu-id="1232c-130">Some operations, such as processing, cannot be performed by</span></span>|  
|<span data-ttu-id="1232c-131">**[最終処理]**</span><span class="sxs-lookup"><span data-stu-id="1232c-131">**Last Processed**</span></span>|<span data-ttu-id="1232c-132">データベースが最後に処理された日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1232c-132">Displays the date and time the database was last processed.</span></span>|  
|<span data-ttu-id="1232c-133">**[推定サイズ]**</span><span class="sxs-lookup"><span data-stu-id="1232c-133">**Estimated Size**</span></span>|<span data-ttu-id="1232c-134">データベースの推定サイズが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1232c-134">Displays the estimated size of the database.</span></span>|  
|<span data-ttu-id="1232c-135">**ストレージの場所**</span><span class="sxs-lookup"><span data-stu-id="1232c-135">**Storage Location**</span></span>|<span data-ttu-id="1232c-136">データベースの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="1232c-136">Specifies the location of the database.</span></span> <span data-ttu-id="1232c-137">データベースが既定のデータ ディレクトリにある場合は、この値は空になります。</span><span class="sxs-lookup"><span data-stu-id="1232c-137">If the database is located in the default Data directory, this value will be empty.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1232c-138">参照</span><span class="sxs-lookup"><span data-stu-id="1232c-138">See Also</span></span>  
 <span data-ttu-id="1232c-139">[多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="1232c-139">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="1232c-140">多次元モデル データベース &#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="1232c-140">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  