---
title: レポート パーツのパブリッシュおよび再パブリッシュ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 92dce484-f39b-403c-9caf-d8772bc3aca3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 95fd5e3f7519c6a0d4a6f08cb9bcbf2507d32aaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634840"
---
# <a name="publish-and-republish-report-parts-report-builder-and-ssrs"></a><span data-ttu-id="426af-102">レポート パーツのパブリッシュおよび再パブリッシュ (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="426af-102">Publish and Republish Report Parts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="426af-103">レポート パーツを既定の設定を使用して既定の場所でパブリッシュすることも、名前や説明などのレポート パーツのメタデータを編集し、レポート サーバー上に保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="426af-103">You can publish a report part with default settings in a default location, or you can edit report part metadata such as name and description, and save it somewhere else on a report server.</span></span> <span data-ttu-id="426af-104">適切な権限があれば、レポート サーバーと統合された SharePoint サイトに保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="426af-104">You can also save it to a SharePoint site that is integrated with a report server if you have the correct permissions.</span></span>  
  
 <span data-ttu-id="426af-105">依存データセットが埋め込まれたレポート パーツのみをパブリッシュすることも、データセットを個別にパブリッシュすることもできます。</span><span class="sxs-lookup"><span data-stu-id="426af-105">You can publish just the report part, with the dataset that it depends on embedded in it, or you can publish the dataset separately.</span></span> <span data-ttu-id="426af-106">データセットを個別にパブリッシュすると、共有データセットになり、レポート パーツからのリンクが作成されます。</span><span class="sxs-lookup"><span data-stu-id="426af-106">If you publish the dataset separately, it becomes a shared dataset, and the report part links to it.</span></span> <span data-ttu-id="426af-107">詳細については、「 [レポート ビルダーのレポート パーツおよびデータセット](../report-data/report-parts-and-datasets-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="426af-107">For more information, see [Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md).</span></span>  
  
 <span data-ttu-id="426af-108">既存のレポート パーツを再パブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="426af-108">You can republish an existing report part.</span></span> <span data-ttu-id="426af-109">権限があれば、自分が作成していなくてもサーバー上のレポート パーツの元のインスタンスに上書き保存できます。</span><span class="sxs-lookup"><span data-stu-id="426af-109">If you have permissions, you can save over the original instance of the report part on the server, even if you didn't create it.</span></span> <span data-ttu-id="426af-110">新しいレポート パーツとしてパブリッシュし、任意の場所に保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="426af-110">You can also publish it as a new report part and save it either in the same or a different location.</span></span>  
  
### <a name="to-publish-a-report-part"></a><span data-ttu-id="426af-111">レポート パーツをパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="426af-111">To publish a report part</span></span>  
  
1.  <span data-ttu-id="426af-112">[レポート ビルダー] メニューの **[レポート パーツのパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426af-112">On the Report Builder menu, click **Publish Report Parts**.</span></span>  
  
     <span data-ttu-id="426af-113">レポート サーバーに接続していない場合は、接続するように求められます。</span><span class="sxs-lookup"><span data-stu-id="426af-113">If you are not connected to a report server, you will be prompted to connect.</span></span> <span data-ttu-id="426af-114">レポート サーバーに接続できないと、レポート パーツをパブリッシュできません。</span><span class="sxs-lookup"><span data-stu-id="426af-114">If you cannot connect to a report server, you cannot publish report parts.</span></span>  
  
2.  <span data-ttu-id="426af-115">レポート パーツを既定の設定を使用して既定の場所に保存するには、 **[既定の設定を使用してすべてのレポート パーツをパブリッシュする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426af-115">To save your report parts with default settings to the default location, click **Publish all report parts with default settings**.</span></span>  
  
     <span data-ttu-id="426af-116">それ以外の場合は、 **[パブリッシュする前にレポート パーツを確認および変更する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426af-116">Otherwise, click **Review and modify report parts before publishing**.</span></span>  
  
3.  <span data-ttu-id="426af-117">レポート パーツの名前と説明を編集します。名前をダブルクリックして編集し、 **[説明]** フィールドをクリックして説明を追加します。</span><span class="sxs-lookup"><span data-stu-id="426af-117">Edit the report part name and description: Double-click the name to edit it and click in the **Description** field to add a description.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="426af-118">検索時に識別しやすいように、レポート パーツの名前と説明を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="426af-118">It is a good idea to give the report part name and description, to help people identify it when searching.</span></span> <span data-ttu-id="426af-119">レポート パーツの名前の最大文字数は、サーバー上のフォルダーの名前とその後に続くレポート パーツの実際の名前を含め、パス全体で 260 文字です。</span><span class="sxs-lookup"><span data-stu-id="426af-119">The maximum length for the name of a report part is 260 characters for the entire path, including the names of the folders on the server, followed by the actual name of the report part.</span></span>  
  
4.  <span data-ttu-id="426af-120">既定以外のフォルダーにレポート パーツを保存するには、 **[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="426af-120">To save your report part to a folder other than the default, click the **Browse** button.</span></span>  
  
5.  <span data-ttu-id="426af-121">レポートのすべてのレポート パーツのオプションを設定したら、 **[パブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426af-121">When you have set the options for all the report parts in the report, click **Publish**.</span></span>  
  
     <span data-ttu-id="426af-122">レポート パーツをパブリッシュすると、ダイアログ ボックスには各レポート パーツが正常にパブリッシュされたかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="426af-122">After you publish the report parts, the dialog box shows which were successfully published and which were not.</span></span> <span data-ttu-id="426af-123">パブリッシュされなかったレポート パーツに関する詳細が、 **[レポート パーツのパブリッシュ]** ダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="426af-123">You can view details in the **Publish Report Parts** dialog box for the report parts that failed to publish.</span></span>  
  
6.  <span data-ttu-id="426af-124">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="426af-124">Click **Close**.</span></span>  
  
### <a name="to-republish-a-report-part"></a><span data-ttu-id="426af-125">レポート パーツを再パブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="426af-125">To republish a report part</span></span>  
  
1.  <span data-ttu-id="426af-126">前の手順の説明に従ってレポート パーツをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="426af-126">Follow the previous procedure for publishing a report part.</span></span>  
  
2.  <span data-ttu-id="426af-127">**[レポート パーツのパブリッシュ]** ダイアログ ボックスで、 **[レポート パーツの新しいコピーとしてパブリッシュする]** をクリックすると、レポート ビルダーによって、サーバー上の既存のレポート パーツは上書き保存されませんが、代わりに別のレポート パーツが作成されます。</span><span class="sxs-lookup"><span data-stu-id="426af-127">In the **Publish Report Parts** dialog box, if you click **Publish as a New Copy of the Report Part**, Report Builder will not save over the existing report part on the server, but will create another report part instead.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="426af-128">新しいレポート パーツとしてパブリッシュすると、新しい一意の ID が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="426af-128">If you publish it as a new report part, it will have a new unique ID.</span></span> <span data-ttu-id="426af-129">元のレポート パーツが変更されても、更新されません。</span><span class="sxs-lookup"><span data-stu-id="426af-129">It will no longer receive updates if the original report part changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="426af-130">参照</span><span class="sxs-lookup"><span data-stu-id="426af-130">See Also</span></span>  
 <span data-ttu-id="426af-131">[レポートパーツ &#40;レポートビルダーと SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="426af-131">[Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="426af-132">[レポートビルダー内のレポートパーツとデータセット](../report-data/report-parts-and-datasets-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="426af-132">[Report Parts and Datasets in Report Builder](../report-data/report-parts-and-datasets-in-report-builder.md) </span></span>  
 <span data-ttu-id="426af-133">[レポートパーツ &#40;レポートビルダーと SSRS&#41;のトラブルシューティング](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="426af-133">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="426af-134">[更新プログラムを確認するか、&#40;レポートビルダーおよび SSRS&#41;の更新プログラムを無効にする](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="426af-134">[Check for Updates or Turn Updates Off &#40;Report Builder and SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="426af-135">レポート パーツの参照と既定のフォルダーの設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="426af-135">Browse for Report Parts and Set a Default Folder &#40;Report Builder and SSRS&#41;</span></span>](browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md)  
  
  
