---
title: '[全般] プロパティページ、レポート (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 66c99d28-ab41-45f0-bf02-ed560293595d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d241b618634cdb898f53aa4357b22fae24918625
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632988"
---
# <a name="general-properties-page-reports-report-manager"></a><span data-ttu-id="2b02a-102">[全般] プロパティ ページ、レポート (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="2b02a-102">General Properties Page, Reports (Report Manager)</span></span>
  <span data-ttu-id="2b02a-103">レポートの [全般] プロパティ ページでは、レポート定義の名前変更、削除、移動、または置換を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-103">Use the General properties page for reports to rename, delete, move, or replace the report definition.</span></span> <span data-ttu-id="2b02a-104">また、このページを使用して、リンク レポートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-104">You can also use this page to create a linked report.</span></span> <span data-ttu-id="2b02a-105">レポートの作成者または変更者、および変更日時の詳細がページの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-105">Details about who created or modified the report and when the changes took place are indicated at the top of the page.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="2b02a-106">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="2b02a-106">Navigation</span></span>  
 <span data-ttu-id="2b02a-107">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2b02a-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a><span data-ttu-id="2b02a-108">レポートの [全般] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="2b02a-108">To open the General properties page for a report</span></span>  
  
1.  <span data-ttu-id="2b02a-109">レポート マネージャーを開き、プロパティを表示または構成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="2b02a-109">Open Report Manager, and locate the report for which you want to view or configure properties.</span></span>  
  
2.  <span data-ttu-id="2b02a-110">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b02a-110">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="2b02a-111">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b02a-111">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="2b02a-112">この操作により、レポートの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-112">This opens the General properties page for the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2b02a-113">Options</span><span class="sxs-lookup"><span data-stu-id="2b02a-113">Options</span></span>  
 <span data-ttu-id="2b02a-114">**Name**</span><span class="sxs-lookup"><span data-stu-id="2b02a-114">**Name**</span></span>  
 <span data-ttu-id="2b02a-115">レポートの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b02a-115">Specify a name for the report.</span></span> <span data-ttu-id="2b02a-116">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b02a-116">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="2b02a-117">また、スペースおよび特定の記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-117">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="2b02a-118">名前を指定するときに、; ?</span><span class="sxs-lookup"><span data-stu-id="2b02a-118">Do not use the characters ; ?</span></span> <span data-ttu-id="2b02a-119">: \@ & = +、$ \*\< ></span><span class="sxs-lookup"><span data-stu-id="2b02a-119">: \@ & = + , $ \* \< ></span></span>  
  
 <span data-ttu-id="2b02a-120">" / を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="2b02a-120">" or / when specifying a name.</span></span>  
  
 <span data-ttu-id="2b02a-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="2b02a-121">**Description**</span></span>  
 <span data-ttu-id="2b02a-122">レポートの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="2b02a-122">Type a description of the report.</span></span> <span data-ttu-id="2b02a-123">この説明は、レポートへのアクセス権を持っているユーザーの [コンテンツ] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-123">This description appears in the Contents page to users who have permission to access the report.</span></span>  
  
 <span data-ttu-id="2b02a-124">**[リスト ビューで非表示にする]**</span><span class="sxs-lookup"><span data-stu-id="2b02a-124">**Hide in list view**</span></span>  
 <span data-ttu-id="2b02a-125">このオプションをオンにすると、レポート マネージャーでリスト ビュー モードを使用しているユーザーにレポートを表示しません。</span><span class="sxs-lookup"><span data-stu-id="2b02a-125">Select this option to hide the report from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="2b02a-126">リスト ビュー モードは、レポート サーバー フォルダー階層を参照するときの既定のビュー形式です。</span><span class="sxs-lookup"><span data-stu-id="2b02a-126">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="2b02a-127">リスト ビューでは、アイテム名および説明がページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-127">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="2b02a-128">別の形式として詳細ビューがあります。</span><span class="sxs-lookup"><span data-stu-id="2b02a-128">The alternate format is details view.</span></span> <span data-ttu-id="2b02a-129">詳細ビューでは説明が省略されますが、そのアイテムに関するその他の情報は含まれます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-129">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="2b02a-130">リスト ビューのアイテムは非表示にできますが、詳細ビューのアイテムは非表示にできません。</span><span class="sxs-lookup"><span data-stu-id="2b02a-130">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="2b02a-131">アイテムへのアクセスを制限する場合は、ロールの割り当てを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b02a-131">If you want to restrict access to an item, you must create a role assignment.</span></span>  
  
 <span data-ttu-id="2b02a-132">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="2b02a-132">**Apply**</span></span>  
 <span data-ttu-id="2b02a-133">変更を保存する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b02a-133">Click to save your changes.</span></span>  
  
 <span data-ttu-id="2b02a-134">**削除**</span><span class="sxs-lookup"><span data-stu-id="2b02a-134">**Delete**</span></span>  
 <span data-ttu-id="2b02a-135">レポート サーバー データベースからレポートを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b02a-135">Click to remove the report from the report server database.</span></span> <span data-ttu-id="2b02a-136">レポートを削除すると、関連するすべてのレポート履歴、およびレポート固有のスケジュールとサブスクリプションが削除されます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-136">Deleting a report deletes all associated report history and report-specific schedules and subscriptions.</span></span> <span data-ttu-id="2b02a-137">レポートがリンク レポートに関連付けられると、リンク レポートは無効になります。</span><span class="sxs-lookup"><span data-stu-id="2b02a-137">If the report is associated with linked reports, the linked reports are invalidated.</span></span>  
  
 <span data-ttu-id="2b02a-138">**移動**</span><span class="sxs-lookup"><span data-stu-id="2b02a-138">**Move**</span></span>  
 <span data-ttu-id="2b02a-139">レポート サーバーのフォルダー階層内でレポートを再配置する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b02a-139">Click to relocate a report within the report server folder hierarchy.</span></span> <span data-ttu-id="2b02a-140">このボタンをクリックすると、アイテムの移動ページが表示され、フォルダーを参照して新しい場所を選択できます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-140">Clicking this button opens the Move Items page, on which you can browse through folders for a new folder location.</span></span> <span data-ttu-id="2b02a-141">詳細については、「[[アイテムの移動] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/move-items-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b02a-141">For more information, see [Move Items Page &#40;Report Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="2b02a-142">**[リンク レポートの作成]**</span><span class="sxs-lookup"><span data-stu-id="2b02a-142">**Create Linked Report**</span></span>  
 <span data-ttu-id="2b02a-143">クリックすると、[新しいリンク レポート] ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-143">Click to open the New Linked Report page.</span></span> <span data-ttu-id="2b02a-144">このページとリンクレポートの詳細については、「[[新しいリンクレポート] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b02a-144">For more information about this page and linked reports, see [New Linked Report Page &#40;Report Manager&#41;](../../2014/reporting-services/new-linked-report-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="2b02a-145">**保存**</span><span class="sxs-lookup"><span data-stu-id="2b02a-145">**Save**</span></span>  
 <span data-ttu-id="2b02a-146">レポート定義の読み取り専用コピーを抽出する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b02a-146">Click to extract a read-only copy of the report definition.</span></span> <span data-ttu-id="2b02a-147">このファイルは、コンピューターに定義されているファイルの関連付けに応じて、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] または他のアプリケーションで開きます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-147">Depending on the file associations defined on your computer, the file will open in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or a different application.</span></span> <span data-ttu-id="2b02a-148">ほとんどの場合、レポートは XML ファイルとして開きます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-148">In most cases, the report opens as an XML file.</span></span>  
  
 <span data-ttu-id="2b02a-149">開くコピーは、最初にレポート サーバーにパブリッシュされた元のレポート定義と同一です。</span><span class="sxs-lookup"><span data-stu-id="2b02a-149">The copy that you open is identical to the original report definition that was initially published to the report server.</span></span> <span data-ttu-id="2b02a-150">レポートのパブリッシュ後にレポートに設定されたプロパティ (パラメーターやデータ ソースのプロパティなど) は、開くファイルに反映されません。</span><span class="sxs-lookup"><span data-stu-id="2b02a-150">Any properties that were set on the report after it was published (such as parameters and data source properties) are not reflected in the file that you open.</span></span>  
  
 <span data-ttu-id="2b02a-151">レポート定義を変更して、新しいファイルとして共有フォルダーに保存し、そのレポート定義を新しいアイテムとしてレポート サーバーにアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-151">You can modify the report definition and save it as a new file in a shared folder, and upload the report definition to the report server as a new item.</span></span> <span data-ttu-id="2b02a-152">レポート定義を [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (または他のアプリケーション) で開いているときに加えた変更は、レポート サーバーには直接保存されません。</span><span class="sxs-lookup"><span data-stu-id="2b02a-152">Modifications that you make to the report definition while it is open in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (or another application) are not saved directly to the report server.</span></span> <span data-ttu-id="2b02a-153">変更したレポートをレポート サーバーにパブリッシュするには、ファイルをアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b02a-153">You must upload the file to publish the modified report to the report server.</span></span>  
  
 <span data-ttu-id="2b02a-154">**Replace**</span><span class="sxs-lookup"><span data-stu-id="2b02a-154">**Replace**</span></span>  
 <span data-ttu-id="2b02a-155">現在のレポートに使用されているレポート定義をファイル システム上の .rdl ファイルに記述された別のレポート定義に置き換える場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b02a-155">Click to replace the report definition that is used in the current report with a different one from an .rdl file located on the file system.</span></span> <span data-ttu-id="2b02a-156">レポート定義を更新する場合、更新の完了後にデータ ソースの設定を再設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b02a-156">If you update a report definition, you must reset the data source settings after the update is complete.</span></span>  
  
 <span data-ttu-id="2b02a-157">**[リンクの変更]**</span><span class="sxs-lookup"><span data-stu-id="2b02a-157">**Change Link**</span></span>  
 <span data-ttu-id="2b02a-158">リンク レポートに別のレポート定義を選択する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b02a-158">Click to select a different report definition for the linked report.</span></span> <span data-ttu-id="2b02a-159">このオプションは、レポートがリンク レポートである場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-159">This option appears if the report is a linked report.</span></span> <span data-ttu-id="2b02a-160">レポートがリンク レポートの場合、このプロパティを設定してレポート定義を置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="2b02a-160">If the report is a linked report, you can set this property to replace the report definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b02a-161">参照</span><span class="sxs-lookup"><span data-stu-id="2b02a-161">See Also</span></span>  
 <span data-ttu-id="2b02a-162">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="2b02a-162">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="2b02a-163">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="2b02a-163">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
