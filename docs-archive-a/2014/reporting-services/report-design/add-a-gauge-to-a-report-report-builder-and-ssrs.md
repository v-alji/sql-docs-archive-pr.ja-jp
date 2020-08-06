---
title: レポートへのゲージの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 45da4fef-2b02-40e1-977c-f8f80d87155e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7125080d95e9c7b882df8d715cce5c6cf8aa6344
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738005"
---
# <a name="add-a-gauge-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="59b09-102">レポートへのゲージの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="59b09-102">Add a Gauge to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="59b09-103">データをビジュアル形式でまとめるにはゲージ データ領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="59b09-103">When you want to summarize data in a visual format, you can use a Gauge data region.</span></span> <span data-ttu-id="59b09-104">ゲージ データ領域をデザイン画面に追加すると、ゲージのデータ ペインにレポート データセット フィールドをドラッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="59b09-104">After you add a Gauge data region to the design surface, you can drag report dataset fields to a data pane on the gauge.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-gauge-to-your-report"></a><span data-ttu-id="59b09-105">レポートにゲージを追加するには</span><span class="sxs-lookup"><span data-stu-id="59b09-105">To add a gauge to your report</span></span>  
  
1.  <span data-ttu-id="59b09-106">レポートを作成するか、既存のレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="59b09-106">Create a report or open an existing report.</span></span>  
  
2.  <span data-ttu-id="59b09-107">[挿入] タブの [ゲージ] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="59b09-107">On the Insert tab, double-click Gauge.</span></span> <span data-ttu-id="59b09-108">**[ゲージの種類の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="59b09-108">The **Select Gauge Type** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="59b09-109">追加するゲージの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="59b09-109">Select the type of gauge you want to add.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  <span data-ttu-id="59b09-110">グラフと異なり、ゲージの種類は線形と放射状だけです。</span><span class="sxs-lookup"><span data-stu-id="59b09-110">Unlike Chart, Gauge has only two types: linear and radial.</span></span> <span data-ttu-id="59b09-111">**[ゲージの種類の選択]** ダイアログ ボックスには、この 2 種類のゲージがテンプレートとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="59b09-111">The available gauges in the **Select a Gauge Type** dialog box are templates for these two types of gauges.</span></span> <span data-ttu-id="59b09-112">そのため、ゲージをレポートに追加した後にゲージの種類を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="59b09-112">For this reason, you cannot change the gauge type after you add the gauge to your report.</span></span> <span data-ttu-id="59b09-113">ゲージの種類を変更するには、一度ゲージを削除してから再度追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59b09-113">You must delete and re-add a gauge to change its type.</span></span>  
  
     <span data-ttu-id="59b09-114">レポートにデータ ソースとデータセットがない場合は、 **[データ ソースのプロパティ]** ダイアログ ボックスが表示され、手順に従ってそれらの両方を作成できます。</span><span class="sxs-lookup"><span data-stu-id="59b09-114">If the report has no data source and dataset the **Data Source Properties** dialog box opens and takes you through the steps to create both.</span></span> <span data-ttu-id="59b09-115">詳細については、「[データ接続またはデータソースの追加と検証 &#40;レポートビルダーと SSRS&#41;](../report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59b09-115">For more information see, [Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](../report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).</span></span>  
  
     <span data-ttu-id="59b09-116">レポートにデータ ソースがありデータセットがない場合は、 **[データセットのプロパティ]** ダイアログ ボックスが表示され、手順に従ってデータセットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="59b09-116">If the report has a data source, but no dataset the **Dataset Properties** dialog box opens and takes you through the steps to create one.</span></span> <span data-ttu-id="59b09-117">詳細については、「 [共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)](../report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59b09-117">For more information, see [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="59b09-118">ゲージをクリックしてデータ ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="59b09-118">Click the gauge to display the data pane.</span></span> <span data-ttu-id="59b09-119">既定では、1 つの値に対応する単一のポインターが存在します。</span><span class="sxs-lookup"><span data-stu-id="59b09-119">By default, a gauge has one pointer corresponding to one value.</span></span> <span data-ttu-id="59b09-120">必要に応じて、ポインターを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="59b09-120">You can add additional pointers.</span></span>  
  
5.  <span data-ttu-id="59b09-121">1 つのフィールドをデータセットからデータ フィールドのドロップ ゾーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="59b09-121">Add one field from the dataset to the data field drop-zone.</span></span> <span data-ttu-id="59b09-122">追加できるフィールドは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="59b09-122">You can add only one field.</span></span> <span data-ttu-id="59b09-123">複数のフィールドを表示する場合は、各フィールドに 1 つずつポインターを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59b09-123">If you want to display multiple fields, you must add additional pointers, one for each field.</span></span>  
  
     <span data-ttu-id="59b09-124">ゲージ スケールを右クリックし、 **[スケールのプロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="59b09-124">Right-click the gauge scale, and select **Scale Properties**.</span></span> <span data-ttu-id="59b09-125">スケールの **[最小]** および **[最大]** の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="59b09-125">Type a value for the **Minimum** and **Maximum** of the scale.</span></span> <span data-ttu-id="59b09-126">詳細については、「[ゲージへの最小値または最大値の設定 &#40;レポート ビルダーおよび SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59b09-126">For more information, see [Set a Minimum or Maximum on a Gauge &#40;Report Builder and SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b09-127">参照</span><span class="sxs-lookup"><span data-stu-id="59b09-127">See Also</span></span>  
 <span data-ttu-id="59b09-128">[入れ子になったデータ領域 (レポート ビルダーおよび SSRS)](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="59b09-128">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="59b09-129">ゲージ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="59b09-129">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
