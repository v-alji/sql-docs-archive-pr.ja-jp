---
title: 最新バージョンとしてバージョンを指定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], latest version
- latest file version specified
- file versions [SQL Server]
ms.assetid: 407dffb1-3ecf-461e-835d-124781f26ee7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dafe4f757e33a5db63340c3d3cc7c9151871d438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632074"
---
# <a name="specify-a-version-as-the-latest-version"></a><span data-ttu-id="cb1c6-102">特定のバージョンを最新バージョンとして指定する</span><span class="sxs-lookup"><span data-stu-id="cb1c6-102">Specify a Version as the Latest Version</span></span>
  <span data-ttu-id="cb1c6-103">ソース管理にファイルをチェックインすると、そのバージョンが最新バージョンになります。つまり、その最新バージョンをチェックアウト (取得) するユーザーは、その最新項目のローカル コピーを受け取ることになります。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-103">When you check a file into source control, the version you check in becomes the latest version; users who check out or retrieve the latest version receive local copies of the item most recently checked in.</span></span>  
  
 <span data-ttu-id="cb1c6-104">ただし、古いバージョンの項目を最新バージョンとして指定したい状況もあります。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-104">However, in some situations, you may want to designate an earlier version of an item as the latest version.</span></span> <span data-ttu-id="cb1c6-105">たとえば、ファイルをチェックアウトし、そのファイルを修正してからチェックインした後に、</span><span class="sxs-lookup"><span data-stu-id="cb1c6-105">For example, you check out a file, modify the file, and then check the file in.</span></span> <span data-ttu-id="cb1c6-106">その修正内容を破棄することにしたとします。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-106">You later decide to discard your modifications.</span></span> <span data-ttu-id="cb1c6-107">既に項目をチェックインしているので、最初のチェックアウトを元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-107">Because you have checked in the item, undoing your original checkout is not an option.</span></span> <span data-ttu-id="cb1c6-108">この場合は、最初にチェックアウトしたバージョンを最新バージョンの項目として指定できます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-108">In this situation, you can designate the version you originally checked out as the latest version of the item.</span></span>  
  
 <span data-ttu-id="cb1c6-109">最新バージョンとして指定するには、以下の方法があります。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-109">You can designate the latest version by:</span></span>  
  
-   <span data-ttu-id="cb1c6-110">**バージョンをピン留め**します。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-110">**Pinning a version**.</span></span> <span data-ttu-id="cb1c6-111">ファイルのバージョンにピンを設定しても、そのバージョンよりも新しいバージョンが削除されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-111">When you pin a file version, versions that are more recent than the pinned version are not deleted.</span></span> <span data-ttu-id="cb1c6-112">ピンを設定したファイルのピンを解除することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-112">In addition, you can unpin a file that you have previously pinned.</span></span> <span data-ttu-id="cb1c6-113">ピンを解除すると、最後にチェックインしたバージョンのファイルが最新バージョンになります。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-113">When you do this, the most recently checked in version of the file becomes the latest version.</span></span> <span data-ttu-id="cb1c6-114">ただし、ピンを設定したファイルをチェックアウトすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-114">However, you cannot check out a pinned file.</span></span>  
  
-   <span data-ttu-id="cb1c6-115">**指定されたバージョンにロールバック**しています。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-115">**Rolling back to a specified version**.</span></span> <span data-ttu-id="cb1c6-116">あるバージョンにロールバックすると、そのバージョンよりも新しいバージョンはすべてソース管理から削除されます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-116">When you roll back to a version, all versions more recent than the one to which you have rolled back are deleted from source control.</span></span> <span data-ttu-id="cb1c6-117">その後、残っている最新バージョンをチェックアウトできます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-117">You can then check out the latest remaining version.</span></span>  
  
### <a name="to-pin-a-version"></a><span data-ttu-id="cb1c6-118">バージョンにピンを設定するには</span><span class="sxs-lookup"><span data-stu-id="cb1c6-118">To pin a version</span></span>  
  
1.  <span data-ttu-id="cb1c6-119">で、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-119">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the solution.</span></span>  
  
2.  <span data-ttu-id="cb1c6-120">ソリューション エクスプローラーで、最新バージョンとして指定するファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-120">In Solution Explorer, select the file that you want to specify as the latest version.</span></span>  
  
3.  <span data-ttu-id="cb1c6-121">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**参照] をクリックし**ます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-121">On the **File** menu, point to **Source Control** and click **ViewHistory**.</span></span>  
  
4.  <span data-ttu-id="cb1c6-122">[**履歴** \<file> ] ダイアログボックスで、最新バージョンとして指定するバージョンを選択し、[**ピン留め**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-122">In the **History of** \<file> dialog box, select the version that you want to specify as the latest, and click **Pin**.</span></span>  
  
     <span data-ttu-id="cb1c6-123">選択したバージョンの横に、それがファイルの最新バージョンであることを示すピンの記号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-123">A pin symbol appears next to the version you have selected, indicating that it is the current file version.</span></span> <span data-ttu-id="cb1c6-124">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に別のバージョンが読み込まれている場合は、ファイルの再読み込みのための画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-124">If you have a different version loaded in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you are prompted to reload the file.</span></span>  
  
### <a name="to-roll-back-to-a-version"></a><span data-ttu-id="cb1c6-125">特定のバージョンにロールバックするには</span><span class="sxs-lookup"><span data-stu-id="cb1c6-125">To roll back to a version</span></span>  
  
1.  <span data-ttu-id="cb1c6-126">で、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-126">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], open the solution.</span></span>  
  
2.  <span data-ttu-id="cb1c6-127">ソリューション エクスプローラーで、最新バージョンとして指定する項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-127">In Solution Explorer, select the item that you want to specify as the latest version.</span></span>  
  
3.  <span data-ttu-id="cb1c6-128">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**履歴**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-128">On the **File** menu, point to **Source Control** and click **History**.</span></span>  
  
4.  <span data-ttu-id="cb1c6-129">[**履歴オプション**] ダイアログボックスで、[ **OK** ] をクリックして、[**ファイルの履歴**] ダイアログボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-129">In the **History Options** dialog box, click **OK** to display the **History of File** dialog box.</span></span>  
  
5.  <span data-ttu-id="cb1c6-130">[**履歴ファイル**] ボックスで、最新バージョンとして指定するバージョンを選択し、[**ロールバック**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-130">In the **History of File** box, select the version you want to specify as the latest version, and click **Rollback**.</span></span>  
  
     <span data-ttu-id="cb1c6-131">選択したバージョンよりも新しいバージョンがすべて削除されることを知らせるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-131">A message appears notifying you that all versions subsequent to the one you have selected will be deleted.</span></span>  
  
6.  <span data-ttu-id="cb1c6-132">[**はい**] をクリックして、選択したバージョンにロールバックします。</span><span class="sxs-lookup"><span data-stu-id="cb1c6-132">Click **Yes** to roll back to the selected version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb1c6-133">参照</span><span class="sxs-lookup"><span data-stu-id="cb1c6-133">See Also</span></span>  
 <span data-ttu-id="cb1c6-134">[チェックインの管理](../../2014/database-engine/manage-checkins.md) </span><span class="sxs-lookup"><span data-stu-id="cb1c6-134">[Manage Checkins](../../2014/database-engine/manage-checkins.md) </span></span>  
 [<span data-ttu-id="cb1c6-135">ファイルのチェックイン</span><span class="sxs-lookup"><span data-stu-id="cb1c6-135">Check In Files</span></span>](../../2014/database-engine/check-in-files.md)  
  
  
