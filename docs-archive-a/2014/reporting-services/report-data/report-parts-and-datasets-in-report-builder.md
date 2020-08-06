---
title: レポート ビルダーのレポート パーツおよびデータセット | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1fe86481-9c41-4535-a4b7-c7c4d780cab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ad592561fa8d1ee7a57bc83eb89d9aec1ba6f6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742857"
---
# <a name="report-parts-and-datasets-in-report-builder"></a><span data-ttu-id="47d22-102">レポート ビルダーのレポート パーツおよびデータセット</span><span class="sxs-lookup"><span data-stu-id="47d22-102">Report Parts and Datasets in Report Builder</span></span>
  <span data-ttu-id="47d22-103">レポート ビルダーでレポートにデータを含める最も簡単な方法は、レポート パーツ ギャラリーからレポート パーツを追加することです。</span><span class="sxs-lookup"><span data-stu-id="47d22-103">In Report Builder, the easiest way to include data in a report is to add report parts from the Report Part Gallery.</span></span> <span data-ttu-id="47d22-104">レポート パーツには、そのレポート パーツが依存するデータセットが含まれており、 *依存データセット*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="47d22-104">Report parts contain the datasets that they depend on, which are known as *dependent datasets*.</span></span> <span data-ttu-id="47d22-105">依存データセットは共有データ ソースに基づいており、埋め込みデータセットまたは共有データセットのどちらかにすることができます。</span><span class="sxs-lookup"><span data-stu-id="47d22-105">Dependent datasets are based on shared data sources and can be either embedded datasets or shared datasets.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
 <span data-ttu-id="47d22-106">レポートにデータを含めるもう 1 つの簡単な方法は、共有データセットを使用することです。</span><span class="sxs-lookup"><span data-stu-id="47d22-106">Another easy way to include data in a report is to use a shared dataset.</span></span> <span data-ttu-id="47d22-107">詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="47d22-107">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="adding-a-report-part-with-dependent-datasets-to-your-report"></a><a name="Adding"></a><span data-ttu-id="47d22-108">依存データセットを含むレポートパーツをレポートに追加する</span><span class="sxs-lookup"><span data-stu-id="47d22-108">Adding a Report Part with Dependent Datasets to Your Report</span></span>  
 <span data-ttu-id="47d22-109">レポート パーツをレポートに追加すると、そのレポート パーツに含まれている依存データセットもレポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="47d22-109">When you add a report part to your report, the dependent datasets that it contains are also added to your report.</span></span> <span data-ttu-id="47d22-110">レポート パーツ内の四角形に、その他の多くのレポート アイテムが含まれている場合があるため、複数の依存データセットがレポートに追加される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="47d22-110">Because a report part might include a rectangle that contains many other report items, it can add multiple dependent datasets to your report.</span></span> <span data-ttu-id="47d22-111">各共有データセットは独立参照であるため、依存先の共有データ ソースはレポートに追加されません。</span><span class="sxs-lookup"><span data-stu-id="47d22-111">Each shared dataset is an independent reference; the shared data source that it depends on is not added to your report.</span></span> <span data-ttu-id="47d22-112">また、各埋め込みデータセットでは、依存先の埋め込みデータ ソースまたは共有データ ソースが追加されます。</span><span class="sxs-lookup"><span data-stu-id="47d22-112">Each embedded dataset also adds the embedded or shared data source that it depends on.</span></span>  
  
 <span data-ttu-id="47d22-113">埋め込みデータ ソースの資格情報は、レポート パーツの一部として保存されません。</span><span class="sxs-lookup"><span data-stu-id="47d22-113">The credentials for an embedded data source are not saved as part of the report part.</span></span> <span data-ttu-id="47d22-114">埋め込みデータ ソースがレポートに追加されると、レポートの実行時に資格情報が要求されます。</span><span class="sxs-lookup"><span data-stu-id="47d22-114">If an embedded data source is added to your report, you will be prompted for credentials when you run the report.</span></span> <span data-ttu-id="47d22-115">資格情報の指定手順を省略するには、資格情報が保存されている共有データ ソースに基づいたレポート パーツを使用します。</span><span class="sxs-lookup"><span data-stu-id="47d22-115">To avoid being prompted for credentials, use report parts that are based on shared data sources with stored credentials.</span></span>  
  
 <span data-ttu-id="47d22-116">レポート パーツをレポートに追加した後は、追加したデータセットと作成した埋め込みデータセットまたは共有データセットに違いはありません。</span><span class="sxs-lookup"><span data-stu-id="47d22-116">After you add a report part to your report, the added datasets are no different than embedded or shared datasets that you create.</span></span> <span data-ttu-id="47d22-117">追加したデータセットはレポート データ ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="47d22-117">You can view the additional datasets in the Report Data pane.</span></span> <span data-ttu-id="47d22-118">埋め込みデータセットは対応する共有データ ソースに表示され、共有データセットは Shared Datasets フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="47d22-118">Embedded datasets appear under the corresponding shared data source and shared datasets appear under the Shared Datasets folder.</span></span>  
  
  
##  <a name="customizing-dependent-datasets"></a><a name="Customizing"></a><span data-ttu-id="47d22-119">依存データセットのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="47d22-119">Customizing Dependent Datasets</span></span>  
 <span data-ttu-id="47d22-120">レポート パーツをレポートに追加した後、プレビューして、データを一部変更することができます。</span><span class="sxs-lookup"><span data-stu-id="47d22-120">After you add report parts to your report, you might preview it and decide to make some changes to the data.</span></span> <span data-ttu-id="47d22-121">変更できる内容は、操作対象のデータセットの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="47d22-121">What you can change depends on the type of dataset that you are working with.</span></span>  
  
 <span data-ttu-id="47d22-122">埋め込みデータセットのデータおよびデータ オプションを変更するには、データセットを作成した場合と同様に、クエリなどのデータセット プロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="47d22-122">To change data and data options for an embedded dataset, you can edit the dataset properties, including the query, just as if you had created the dataset yourself.</span></span>  
  
 <span data-ttu-id="47d22-123">共有データセットのデータおよびデータ オプションを変更する場合は、十分な権限があるレポート サーバーでのみ共有データセットの定義を変更できます。</span><span class="sxs-lookup"><span data-stu-id="47d22-123">To change a data and data options for a shared dataset, you can change the shared dataset definition on the report server only you have sufficient permissions.</span></span> <span data-ttu-id="47d22-124">また、レポート内の共有データセットのインスタンスについても、フィルターを追加し、計算フィールドを追加し、大文字と小文字の区別などのデータ オプションを変更して、カスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="47d22-124">You can also customize the instance of the shared dataset in your report by adding filters, adding calculated fields, and changing data options such as case sensitivity.</span></span> <span data-ttu-id="47d22-125">詳細については、「[埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47d22-125">For more information, see [Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;](embedded-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="47d22-126">共有データセットの定義を変更する方法、またはレポート内の共有データセットに対する最新のデータ変更内容を表示する方法の詳細については、「[共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)」および「[レポート データ ペインでのフィールドの追加、編集、更新 (レポート ビルダーおよび SSRS)](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47d22-126">For more information about how to change the definition of a shared dataset or how to show the latest data changes for a shared dataset in your report, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) and [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md).</span></span>  
  
  
##  <a name="publishing-dependent-datasets-as-shared-datasets"></a><a name="Publishing"></a><span data-ttu-id="47d22-127">共有データセットとしての依存データセットのパブリッシュ</span><span class="sxs-lookup"><span data-stu-id="47d22-127">Publishing Dependent Datasets as Shared Datasets</span></span>  
 <span data-ttu-id="47d22-128">依存データセットを持つレポート アイテムをパブリッシュする場合は、共有データセットとして、またはレポート アイテムに埋め込まれたままの埋め込みデータセットとして各データセットをパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="47d22-128">When you publish a report item that has dependent datasets, you have the option to publish each dataset as a shared dataset or as an embedded dataset that remains embedded in the report item.</span></span>  
  
 <span data-ttu-id="47d22-129">共有データセット オプションを選択した場合、データセットは共有データセット定義としてレポート サーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="47d22-129">When you select the shared dataset option, the dataset is saved to the report server as a shared dataset definition.</span></span> <span data-ttu-id="47d22-130">レポートでは、そのデータセットを使用するすべてのレポート アイテムが、現在レポート サーバー上に存在する共有データセットを指すように更新されます。</span><span class="sxs-lookup"><span data-stu-id="47d22-130">In your report, every report item that uses that dataset is updated to point to the shared dataset that is now on the report server.</span></span> <span data-ttu-id="47d22-131">その結果、次の 2 つの処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="47d22-131">Two things happen as a result:</span></span>  
  
1.  <span data-ttu-id="47d22-132">[パブリッシュ] ダイアログ ボックスでは、パブリッシュされた各共有データセットがパブリッシュ可能なアイテムのリストから削除されます。</span><span class="sxs-lookup"><span data-stu-id="47d22-132">In the Publish dialog box, each shared dataset that has been published is removed from the list of items that are available to publish.</span></span>  
  
2.  <span data-ttu-id="47d22-133">レポート ビルダーを終了したり、新規レポートを開始したりすると、レポートを保存するように求められます。</span><span class="sxs-lookup"><span data-stu-id="47d22-133">When you exit Report Builder or start a new report, you are prompted to save your report.</span></span> <span data-ttu-id="47d22-134">レポートを保存しない場合、次にこのレポートを開き、レポート アイテムをパブリッシュするときに、同じデータセットの新しいコピーをパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="47d22-134">If you do not save your report, the next time you open this report and publish report items, you might publish new copies of the same datasets.</span></span> <span data-ttu-id="47d22-135">レポート サーバーに共有データセットの複数のコピーを保存したくない場合は、レポートを保存することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="47d22-135">To prevent saving multiple copies of shared datasets to the report server, we recommend that you save the report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47d22-136">共有データセットから継続して正常にデータを使用するには、レポート アイテムのセキュリティ保護の背景にある原則を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47d22-136">To ensure that you and others can continue to successfully use data from a shared dataset, you must understand the principles behind securing report items.</span></span> <span data-ttu-id="47d22-137">詳細については、「 [共有データセット アイテムをセキュリティで保護する](../security/secure-shared-dataset-items.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47d22-137">For more information, see [Secure Shared Dataset Items](../security/secure-shared-dataset-items.md).</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="47d22-138">参照</span><span class="sxs-lookup"><span data-stu-id="47d22-138">See Also</span></span>  
 <span data-ttu-id="47d22-139">[レポートデザインビュー &#40;レポートビルダー&#41;](../report-builder/report-design-view-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="47d22-139">[Report Design View &#40;Report Builder&#41;](../report-builder/report-design-view-report-builder.md) </span></span>  
 <span data-ttu-id="47d22-140">[セキュリティ &#40;レポートビルダー&#41;](../report-builder/security-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="47d22-140">[Security &#40;Report Builder&#41;](../report-builder/security-report-builder.md) </span></span>  
 <span data-ttu-id="47d22-141">[レポートパーツ &#40;レポートビルダーと SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="47d22-141">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="47d22-142">レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="47d22-142">Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  
