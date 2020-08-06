---
title: レポート パーツの参照と既定のフォルダーの設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6605a23732799ec07b3dbe8481e88c91b18ebe5d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632907"
---
# <a name="browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs"></a><span data-ttu-id="030e7-102">レポート パーツの参照と既定のフォルダーの設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="030e7-102">Browse for Report Parts and Set a Default Folder (Report Builder and SSRS)</span></span>
  <span data-ttu-id="030e7-103">レポートを作成する最も簡単な方法は、テーブルやグラフなどの既存のレポートパーツをレポートパーツギャラリーからレポートに追加することです。</span><span class="sxs-lookup"><span data-stu-id="030e7-103">The easiest way to create a report is to add existing report parts, such as tables and charts, to your report from the Report Part Gallery.</span></span> <span data-ttu-id="030e7-104">レポートにレポート パーツを追加すると、動作に必要なアイテムもすべて追加されます。</span><span class="sxs-lookup"><span data-stu-id="030e7-104">When you add a report part to your report, you are also adding everything it must have to work.</span></span> <span data-ttu-id="030e7-105">たとえば、データを表示するレポート パーツは、クエリやデータ ソースへの接続などのデータセットに依存しています。</span><span class="sxs-lookup"><span data-stu-id="030e7-105">For example, any report part that displays data depends on a dataset, that is, a query and a connection to a data source.</span></span> <span data-ttu-id="030e7-106">レポートにレポート パーツを追加した後、必要に応じてそのレポート パーツを変更できます。</span><span class="sxs-lookup"><span data-stu-id="030e7-106">After you add the report part to your report, you can modify it as much as you need.</span></span>  
  
 <span data-ttu-id="030e7-107">レポート サーバーや、レポート サーバーに統合されている SharePoint サイトにレポート パーツをパブリッシュするための既定のフォルダーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="030e7-107">You can set a default folder to publish report parts to the report server or SharePoint site integrated with a report server.</span></span>  
  
 <span data-ttu-id="030e7-108">詳細については、「 [レポート パーツ (レポート ビルダーおよび SSRS)](../report-parts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="030e7-108">For more information, see [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-browse-for-report-parts"></a><span data-ttu-id="030e7-109">レポート パーツを参照するには</span><span class="sxs-lookup"><span data-stu-id="030e7-109">To browse for report parts</span></span>  
  
1.  <span data-ttu-id="030e7-110">**[挿入]** メニューの **[レポート パーツ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="030e7-110">On the **Insert** menu, click **Report Parts**.</span></span>  
  
     <span data-ttu-id="030e7-111">まだ接続していない場合は、 **[レポート サーバーへの接続]** をクリックし、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="030e7-111">If you are not already connected, click **Connect to a report server**, and enter the name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="030e7-112">レポート パーツを参照するには、レポート サーバーに接続している必要があります。</span><span class="sxs-lookup"><span data-stu-id="030e7-112">You must be connected to a report server to browse for report parts.</span></span>  
  
2.  <span data-ttu-id="030e7-113">レポート パーツの詳細を指定して、検索を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="030e7-113">You can narrow your search by specifying details about the report part.</span></span> <span data-ttu-id="030e7-114">名前と説明のすべてまたは一部を **[検索]** ボックスに入力し、 **[抽出条件の追加]** をクリックして次のフィールドのいずれかまたはすべての値を追加します。</span><span class="sxs-lookup"><span data-stu-id="030e7-114">Type all or part of the name and description in the **Search** box, or click **Add Criteria** and add values for any or all of these fields:</span></span>  
  
    -   <span data-ttu-id="030e7-115">作成者</span><span class="sxs-lookup"><span data-stu-id="030e7-115">Created by</span></span>  
  
    -   <span data-ttu-id="030e7-116">作成日</span><span class="sxs-lookup"><span data-stu-id="030e7-116">Date created</span></span>  
  
    -   <span data-ttu-id="030e7-117">最終更新日</span><span class="sxs-lookup"><span data-stu-id="030e7-117">Date last modified</span></span>  
  
    -   <span data-ttu-id="030e7-118">最終更新元</span><span class="sxs-lookup"><span data-stu-id="030e7-118">Last modified by</span></span>  
  
    -   <span data-ttu-id="030e7-119">サーバー フォルダー</span><span class="sxs-lookup"><span data-stu-id="030e7-119">Server folder</span></span>  
  
    -   <span data-ttu-id="030e7-120">種類</span><span class="sxs-lookup"><span data-stu-id="030e7-120">Type</span></span>  
  
     <span data-ttu-id="030e7-121">たとえば、画像を検索するには、 **[条件の追加]** 、 **[種類]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="030e7-121">For example, to find an image, click **Add Criteria**, and then click **Type**.</span></span> <span data-ttu-id="030e7-122">ドロップダウン ボックスの **[画像]** チェック ボックスをオンにし、Enter キーを押してから、検索の虫眼鏡アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="030e7-122">In the dropdown box, select the **Image** check box, press ENTER, and then click the Search magnifying glass.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="030e7-123">**[作成者]** と **[最終更新元]** の値については、レポート サーバーを使用しているユーザー名を検索してください。</span><span class="sxs-lookup"><span data-stu-id="030e7-123">For the **Created by** and **Last modified by** values, search for the person's user name as it is represented on the report server.</span></span>  
  
### <a name="to-set-a-default-folder-for-report-parts"></a><span data-ttu-id="030e7-124">レポート パーツの既定のフォルダーを設定するには</span><span class="sxs-lookup"><span data-stu-id="030e7-124">To set a default folder for report parts</span></span>  
  
1.  <span data-ttu-id="030e7-125">**[レポート ビルダー]** をクリックし、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="030e7-125">Click **Report Builder**, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="030e7-126">**[オプション]** ダイアログ ボックスの **[設定]** タブで、 **[レポート パーツをパブリッシュする既定のフォルダー]** ボックスにフォルダー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="030e7-126">In the **Options** dialog box, on the **Settings** tab, type a folder name in the **Publish report parts to this folder by default** textbox.</span></span>  
  
 <span data-ttu-id="030e7-127">レポート サーバー上にフォルダーを作成する権限があり、このフォルダーが存在していない場合は、レポート ビルダーによってフォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="030e7-127">Report Builder will create this folder if you have permissions to create folders on the report server and the folder does not exist yet.</span></span>  
  
 <span data-ttu-id="030e7-128">この設定を有効にするためにレポート ビルダーを再起動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="030e7-128">You do not need to restart Report Builder for this setting to take effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030e7-129">参照</span><span class="sxs-lookup"><span data-stu-id="030e7-129">See Also</span></span>  
 <span data-ttu-id="030e7-130">[更新プログラムを確認するか、&#40;レポートビルダーおよび SSRS&#41;の更新プログラムを無効にする](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="030e7-130">[Check for Updates or Turn Updates Off &#40;Report Builder and SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="030e7-131">[レポート パーツ &#40;レポート ビルダーおよび SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="030e7-131">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="030e7-132">[レポート ビルダーのレポート パーツおよびデータセット](../report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="030e7-132">[Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 <span data-ttu-id="030e7-133">[レポートパーツ &#40;レポートビルダーと SSRS&#41;のトラブルシューティング](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="030e7-133">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="030e7-134">レポート パーツのパブリッシュおよび再パブリッシュ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="030e7-134">Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;</span></span>](publish-and-republish-report-parts-report-builder-and-ssrs.md)  
  
  
