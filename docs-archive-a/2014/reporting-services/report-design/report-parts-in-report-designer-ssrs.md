---
title: レポート デザイナーでのレポート パーツ (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.components.f1
ms.assetid: 0c34311d-05d6-4bd2-b452-545fa95f8e7f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7535c5c2c514bc32a11a5fc0d97c6aee1cf5f2d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631545"
---
# <a name="report-parts-in-report-designer-ssrs"></a><span data-ttu-id="b856c-102">レポート デザイナーでのレポート パーツ (SSRS)</span><span class="sxs-lookup"><span data-stu-id="b856c-102">Report Parts in Report Designer (SSRS)</span></span>
  <span data-ttu-id="b856c-103">レポート デザイナーで、プロジェクトのテーブル、グラフ、および他のレポート アイテムを作成した後、それらを *レポート パーツ* として、レポート サーバーまたはレポート サーバーと統合されている SharePoint サイトにパブリッシュできます。これにより、自分や他のユーザーが、それらのレポート パーツを別のレポートで再利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b856c-103">In Report Designer, after you create tables, charts, and other report items in a project, you can publish them as *report parts* to a report server or SharePoint site integrated with a report server so that you and others can reuse them in other reports.</span></span>  
  
 <span data-ttu-id="b856c-104">通常、レポート パーツはレポート デザイナーおよびレポート ビルダーで同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="b856c-104">In general, report parts function the same way in Report Designer and in Report Builder.</span></span> <span data-ttu-id="b856c-105">基本的な機能については、msdn.microsoft.com のレポートビルダーに関する[ドキュメント](https://go.microsoft.com/fwlink/?LinkId=154494)の「[レポートパーツ &#40;レポートビルダーと SSRS&#41;](../report-parts-report-builder-and-ssrs.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b856c-105">To read about basic functionality, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="b856c-106">ただし、レポート デザイナーでのレポート パーツの機能の仕方には、大きく異なる点があります。</span><span class="sxs-lookup"><span data-stu-id="b856c-106">There are fundamental differences in the way report parts work in Report Designer.</span></span> <span data-ttu-id="b856c-107">主な違いはワークフローです。</span><span class="sxs-lookup"><span data-stu-id="b856c-107">A main difference is the work flow.</span></span> <span data-ttu-id="b856c-108">レポート ビルダーでは、コラボレーションによる作成が可能です。つまり、あるユーザーがレポート パーツを作成してパブリッシュすると、</span><span class="sxs-lookup"><span data-stu-id="b856c-108">Report Builder enables collaborative authoring: I create a report part and publish it.</span></span> <span data-ttu-id="b856c-109">別のユーザーがそのパーツを再利用して変更し、再パブリッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="b856c-109">You can reuse, modify, and republish it.</span></span> <span data-ttu-id="b856c-110">レポート デザイナーでは、パブリッシュは一方向です。つまり、あるユーザーがレポート デザイナーからレポート パーツをパブリッシュすることができ、別のユーザーはそれを再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="b856c-110">In Report Designer, publishing is one-way: I can publish a report part from Report Designer, and you can reuse it.</span></span> <span data-ttu-id="b856c-111">しかし、既存のレポート パーツを、レポート デザイナーでレポートに再利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b856c-111">But I cannot reuse an existing report part in a report in Report Designer.</span></span> <span data-ttu-id="b856c-112">このトピックでは、レポート パーツの概要について説明した後、これらの違いについて詳述します。</span><span class="sxs-lookup"><span data-stu-id="b856c-112">This topic elaborates on these differences, after a quick overview of report parts.</span></span>  
  
##  <a name="life-cycle-of-report-part-publishing"></a><a name="ComponentWorkflow"></a> <span data-ttu-id="b856c-113">レポート パーツ パブリッシュのライフ サイクル</span><span class="sxs-lookup"><span data-stu-id="b856c-113">Life Cycle of Report Part Publishing</span></span>  
 <span data-ttu-id="b856c-114">![rs_ComponentCreation](../media/rs-componentcreation.gif "rs_ComponentCreation")</span><span class="sxs-lookup"><span data-stu-id="b856c-114">![rs_ComponentCreation](../media/rs-componentcreation.gif "rs_ComponentCreation")</span></span>  
  
1.  <span data-ttu-id="b856c-115">レポート デザイナーで、ユーザー A が埋め込みデータセットに依存するグラフを含むレポートのプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b856c-115">In Report Designer, Person A creates a project that contains a report with a chart that depends on an embedded dataset.</span></span>  
  
2.  <span data-ttu-id="b856c-116">ユーザー A は、埋め込みデータセットを含むグラフに、パブリッシュのフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="b856c-116">Person A flags the chart with its embedded dataset for publishing.</span></span> <span data-ttu-id="b856c-117">すると、レポート デザイナーによって、そのグラフに一意の ID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b856c-117">Report Designer assigns it a unique ID.</span></span> <span data-ttu-id="b856c-118">次に、ユーザー A はそのレポートをレポート サーバーに配置します。</span><span class="sxs-lookup"><span data-stu-id="b856c-118">Person A then deploys the report to the report server.</span></span> <span data-ttu-id="b856c-119">この結果、レポート デザイナーによって、グラフがパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="b856c-119">Report Designer publishes the chart.</span></span>  
  
3.  <span data-ttu-id="b856c-120">ユーザー B は、レポート ビルダーで空白のレポートを作成し、パブリッシュされたグラフをそのレポートに追加します。</span><span class="sxs-lookup"><span data-stu-id="b856c-120">Person B creates a blank report in Report Builder and adds the chart to it.</span></span> <span data-ttu-id="b856c-121">グラフと埋め込みデータセットは、ユーザー B のレポートの一部になります。</span><span class="sxs-lookup"><span data-stu-id="b856c-121">The chart is now part of Person B's report, along with the embedded dataset.</span></span> <span data-ttu-id="b856c-122">ユーザー B はレポート内のグラフとデータセットのインスタンスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="b856c-122">Person B can modify the instances of the chart and dataset that are in the report.</span></span> <span data-ttu-id="b856c-123">これは、レポート サーバー上のグラフとデータセットのインスタンスに影響することも、レポート内のインスタンスとレポート サーバー上のインスタンスの間のリレーションシップを壊すこともありません。</span><span class="sxs-lookup"><span data-stu-id="b856c-123">This will have no effect on the instances of the chart and dataset on the report server, nor will it break the relationship between the instances in the report and on the report server.</span></span>  
  
     <span data-ttu-id="b856c-124">![rs_BIDScomponentupdate](../media/rs-bidscomponentupdate.gif "rs_BIDScomponentupdate")</span><span class="sxs-lookup"><span data-stu-id="b856c-124">![rs_BIDScomponentupdate](../media/rs-bidscomponentupdate.gif "rs_BIDScomponentupdate")</span></span>  
  
4.  <span data-ttu-id="b856c-125">レポート デザイナーで、ユーザー A が元のレポートのグラフに変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="b856c-125">In Report Designer, Person A modifies the chart in the original report.</span></span>  
  
5.  <span data-ttu-id="b856c-126">ユーザー A はレポートを再配置します。これにより、グラフがサーバーに再パブリッシュされ、サーバー上のグラフが更新されます。</span><span class="sxs-lookup"><span data-stu-id="b856c-126">Person A redeploys the report, which republishes the chart to the server, thus updating the chart on the server.</span></span>  
  
6.  <span data-ttu-id="b856c-127">レポート ビルダーで、ユーザー B は、サーバーから更新されたグラフを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="b856c-127">In Report Builder, Person B accepts the updated chart from the server.</span></span> <span data-ttu-id="b856c-128">これにより、ユーザー B が自分のレポート内のグラフに対して行った変更が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="b856c-128">This overwrites the changes that Person B had made to the chart in Person B's report.</span></span>  
  
##  <a name="publishing-report-parts"></a><a name="PublishingComponents"></a> <span data-ttu-id="b856c-129">レポート パーツのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="b856c-129">Publishing Report Parts</span></span>  
 <span data-ttu-id="b856c-130">レポート パーツをパブリッシュすると、レポート デザイナーによってレポート パーツに一意の ID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b856c-130">When you publish a report part, Report Designer assigns it a unique ID.</span></span> <span data-ttu-id="b856c-131">それ以降、レポート パーツにどのような変更が加えられても、その ID が維持されます。</span><span class="sxs-lookup"><span data-stu-id="b856c-131">From then on, it maintains that ID, no matter what else you change about it.</span></span> <span data-ttu-id="b856c-132">ID は、レポート内の元のレポート アイテムをレポート パーツにリンクします。</span><span class="sxs-lookup"><span data-stu-id="b856c-132">The ID links the original report item in your report to the report part.</span></span> <span data-ttu-id="b856c-133">他のレポート作成者がレポート ビルダーでレポート パーツを再利用すると、この ID によって、別のレポートで再利用されたレポート パーツと元のレポート パーツの間もリンクされます。</span><span class="sxs-lookup"><span data-stu-id="b856c-133">When other report authors reuse the report part in Report Builder, the ID also links the report part in their report to the report part.</span></span>  
  
 <span data-ttu-id="b856c-134">以下に、レポート パーツとしてパブリッシュできるレポート アイテムを示します。</span><span class="sxs-lookup"><span data-stu-id="b856c-134">These are the report items you can publish as report parts:</span></span>  
  
-   <span data-ttu-id="b856c-135">グラフ</span><span class="sxs-lookup"><span data-stu-id="b856c-135">Charts</span></span>  
  
-   <span data-ttu-id="b856c-136">ゲージ</span><span class="sxs-lookup"><span data-stu-id="b856c-136">Gauges</span></span>  
  
-   <span data-ttu-id="b856c-137">画像と埋め込み画像</span><span class="sxs-lookup"><span data-stu-id="b856c-137">Images and embedded images</span></span>  
  
-   <span data-ttu-id="b856c-138">マップ</span><span class="sxs-lookup"><span data-stu-id="b856c-138">Maps</span></span>  
  
-   <span data-ttu-id="b856c-139">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b856c-139">Parameters</span></span>  
  
-   <span data-ttu-id="b856c-140">四角形</span><span class="sxs-lookup"><span data-stu-id="b856c-140">Rectangles</span></span>  
  
-   <span data-ttu-id="b856c-141">テーブル</span><span class="sxs-lookup"><span data-stu-id="b856c-141">Tables</span></span>  
  
-   <span data-ttu-id="b856c-142">マトリックス</span><span class="sxs-lookup"><span data-stu-id="b856c-142">Matrices</span></span>  
  
-   <span data-ttu-id="b856c-143">リスト</span><span class="sxs-lookup"><span data-stu-id="b856c-143">Lists</span></span>  
  
 <span data-ttu-id="b856c-144">テーブル、マトリックス、グラフなどのデータを表示するレポート パーツをパブリッシュする場合、レポート パーツのベースに共有データセットを使用することができます。共有データセットを使用しない場合、レポート パーツをパブリッシュする際、レポート パーツが依存するデータセットは埋め込みデータセットとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="b856c-144">If you are publishing a report part that displays data, such as a table, matrix, or chart, you can base it on a shared dataset; otherwise, when you publish the report part, the dataset that it depends on is saved as an embedded dataset.</span></span> <span data-ttu-id="b856c-145">埋め込みデータセットのベースに、埋め込みデータ ソースを使用することはできますが、埋め込みデータ ソースには資格情報が保存されていません。</span><span class="sxs-lookup"><span data-stu-id="b856c-145">Embedded datasets can be based on embedded data sources, but credentials are not stored in embedded data sources.</span></span> <span data-ttu-id="b856c-146">したがって、レポート パーツが、埋め込みデータ ソースを使用する埋め込みデータセットに依存する場合、このレポート パーツを再利用するユーザーは、埋め込みデータ ソースの資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b856c-146">Thus, if your report part depends on an embedded dataset that uses an embedded data source, anyone who reuses this report part will need to provide the credentials for the embedded data source.</span></span> <span data-ttu-id="b856c-147">これを避けるには、埋め込みデータセットおよび共有データセットのベースとして、資格情報が保存された共有データ ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="b856c-147">To avoid this, base your embedded and shared datasets on shared data sources with stored credentials.</span></span> <span data-ttu-id="b856c-148">詳細については、msdn.microsoft.com の[レポートビルダーに関するドキュメント](https://go.microsoft.com/fwlink/?LinkId=154494)の「[レポートビルダーのレポートパーツとデータセット](../report-data/report-parts-and-datasets-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b856c-148">For more information, see [Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) in the [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
 <span data-ttu-id="b856c-149">レポート デザイナーでレポート パーツをパブリッシュするには、次の 2 つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b856c-149">Publishing a report part in Report Designer is a two-step process:</span></span>  
  
1.  <span data-ttu-id="b856c-150">**[レポート パーツのパブリッシュ]** ダイアログ ボックスで、パブリッシュするレポート アイテムにフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="b856c-150">Flag the report items that you want to publish in the **Publish Report Parts** dialog box.</span></span>  
  
2.  <span data-ttu-id="b856c-151">レポートを配置します。</span><span class="sxs-lookup"><span data-stu-id="b856c-151">Deploy the report.</span></span>  
  
 <span data-ttu-id="b856c-152">レポートを配置すると、レポート パーツは SharePoint サイトまたはレポート サーバーにパブリッシュされ、他のユーザーが再利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b856c-152">When you deploy the report, the report part is published to a SharePoint site or report server, and others can reuse it.</span></span> <span data-ttu-id="b856c-153">レポート パーツをパブリッシュするには、レポートを配置する際に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバーに接続でき、そのレポート サーバーに対する十分な権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b856c-153">To publish a report part, you must have a connection to and sufficient permissions on a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] report server when you deploy the report.</span></span>  
  
  
##  <a name="reusing-report-parts"></a><a name="SearchReuseComponents"></a> <span data-ttu-id="b856c-154">レポート パーツの再利用</span><span class="sxs-lookup"><span data-stu-id="b856c-154">Reusing Report Parts</span></span>  
 <span data-ttu-id="b856c-155">レポート ビルダーとは異なり、レポート パーツの作成元ではないプロジェクトから、そのレポート パーツを検索および再利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b856c-155">Unlike in Report Builder, you cannot search for and reuse a report part in a project other than the one in which it was created.</span></span>  
  
 <span data-ttu-id="b856c-156">レポート ビルダーで作業を行うレポート作成者は、自分が作成するレポートで、他のユーザーがパブリッシュするレポート パーツを検索および再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="b856c-156">Report authors working in Report Builder can search for and reuse report parts that you publish in reports that they create.</span></span>  
  
##  <a name="republishing-report-parts"></a><a name="RepublishingComponents"></a> <span data-ttu-id="b856c-157">レポート パーツの再パブリッシュ</span><span class="sxs-lookup"><span data-stu-id="b856c-157">Republishing Report Parts</span></span>  
 <span data-ttu-id="b856c-158">レポート デザイナーでは、レポート パーツを作成したレポート内から、既存のレポート パーツを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b856c-158">In Report Designer, you should update an existing report part from within the report in which you created it.</span></span> <span data-ttu-id="b856c-159">レポート ビルダーでは、レポート作成者はレポート パーツを再利用し、新しいレポート パーツとしてパブリッシュできます。パブリッシュ済みのレポート パーツを新しいものに置き換える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b856c-159">In Report Builder, report authors can reuse the report part, and publish it as a new report part without replacing the report part that you published.</span></span> <span data-ttu-id="b856c-160">十分な権限を持つレポート作成者は、他のユーザーによってパブリッシュされたレポート パーツを更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="b856c-160">If they have sufficient permissions they can also update the report part that you published.</span></span> <span data-ttu-id="b856c-161">サイトまたはサーバー上のフォルダーに対する十分な権限を持つユーザーは、フォルダーに保存されているレポート パーツを更新できます。</span><span class="sxs-lookup"><span data-stu-id="b856c-161">Anyone with sufficient permissions for a folder on a site or server can update the report parts stored there.</span></span> <span data-ttu-id="b856c-162">最新の更新で、以前の更新内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="b856c-162">The last update overwrites previous updates.</span></span>  
  
 <span data-ttu-id="b856c-163">レポート パーツに変更を加えた後、そのレポート パーツをサイトまたはサーバーに再パブリッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="b856c-163">You can modify and then republish the report part to the site or server.</span></span> <span data-ttu-id="b856c-164">レポート ビルダーのレポート作成者がそのレポート パーツを含むレポートを次回開くと、変更が通知され、</span><span class="sxs-lookup"><span data-stu-id="b856c-164">Report Builder report authors who have added that report part to a report are informed of the change the next time they open that report.</span></span> <span data-ttu-id="b856c-165">変更を受け入れるかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="b856c-165">They can choose to accept your changes or not.</span></span>  
  
 <span data-ttu-id="b856c-166">既にパブリッシュ済みのレポートを、新しいレポートとしてパブリッシュすることを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="b856c-166">You can also choose to publish as new a report that you have already published.</span></span> <span data-ttu-id="b856c-167">[レポート パーツのパブリッシュ] ダイアログ ボックスで、[新しいレポート パーツとしてパブリッシュ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b856c-167">In the Publish Report Parts dialog box, click the Publish as a new report part.</span></span> <span data-ttu-id="b856c-168">この新しいレポート パーツには新しい一意の ID が付いており、古いレポート パーツとのリレーションシップはありません。</span><span class="sxs-lookup"><span data-stu-id="b856c-168">This new report part has a new unique ID and no relationship to the old report part.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="b856c-169">参照</span><span class="sxs-lookup"><span data-stu-id="b856c-169">See Also</span></span>  
 [<span data-ttu-id="b856c-170">レポート パーツの管理</span><span class="sxs-lookup"><span data-stu-id="b856c-170">Managing Report Parts</span></span>](managing-report-parts.md)  
  
  
