---
title: '[全般] プロパティページ、モデル (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.general.f1
ms.assetid: 7ad59850-8135-4c4d-95e9-6d705b6d77a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0fbd96392716c63fb739c6455bb1eac04912b93f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644853"
---
# <a name="general-properties-page-models-report-manager"></a><span data-ttu-id="2beb0-102">[全般] プロパティ ページ、モデル (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="2beb0-102">General Properties Page, Models (Report Manager)</span></span>
  <span data-ttu-id="2beb0-103">モデル定義 (.smdl) ファイルの名前変更、削除、移動、または置換を行うには、レポート モデルの [全般] プロパティ ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="2beb0-103">Use the General properties page for report models to rename, delete, move, or replace the model definition (.smdl) file.</span></span> <span data-ttu-id="2beb0-104">モデルの作成者または変更者、および変更日時の詳細がページの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-104">Details about who created or modified the model and when the changes took place are indicated at the top of the page.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="2beb0-105">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="2beb0-105">Navigation</span></span>  
 <span data-ttu-id="2beb0-106">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2beb0-106">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-model"></a><span data-ttu-id="2beb0-107">モデルの [全般] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="2beb0-107">To open the General properties page for a model</span></span>  
  
1.  <span data-ttu-id="2beb0-108">レポート マネージャーを開き、プロパティを表示または構成するモデルを探します。</span><span class="sxs-lookup"><span data-stu-id="2beb0-108">Open Report Manager, and locate the model for which you want to view or configure properties.</span></span>  
  
2.  <span data-ttu-id="2beb0-109">モデルの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2beb0-109">Hover over the model, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="2beb0-110">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2beb0-110">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="2beb0-111">この操作により、モデルの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-111">This opens the General properties page for the model.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2beb0-112">Options</span><span class="sxs-lookup"><span data-stu-id="2beb0-112">Options</span></span>  
 <span data-ttu-id="2beb0-113">**名前**</span><span class="sxs-lookup"><span data-stu-id="2beb0-113">**Name**</span></span>  
 <span data-ttu-id="2beb0-114">モデルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2beb0-114">Specifies the name of the model.</span></span> <span data-ttu-id="2beb0-115">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2beb0-115">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="2beb0-116">また、スペースおよびいくつかの記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-116">It can also include spaces and some symbols.</span></span> <span data-ttu-id="2beb0-117">名前を指定するときに使用できない記号は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2beb0-117">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="2beb0-118">; ?</span><span class="sxs-lookup"><span data-stu-id="2beb0-118">; ?</span></span> <span data-ttu-id="2beb0-119">: \@ & = +、$/\* \< > |" /</span><span class="sxs-lookup"><span data-stu-id="2beb0-119">: \@ & = + , $ / \* \< > | " /</span></span>  
  
 <span data-ttu-id="2beb0-120">**説明**</span><span class="sxs-lookup"><span data-stu-id="2beb0-120">**Description**</span></span>  
 <span data-ttu-id="2beb0-121">モデルの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="2beb0-121">Type a description of the model.</span></span> <span data-ttu-id="2beb0-122">この説明は、モデルへのアクセス権を持つユーザーの [コンテンツ] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-122">This description appears in the Contents page to users who have permission to access the modelt.</span></span>  
  
 <span data-ttu-id="2beb0-123">**[リスト ビューで非表示にする]**</span><span class="sxs-lookup"><span data-stu-id="2beb0-123">**Hidden in list view**</span></span>  
 <span data-ttu-id="2beb0-124">このチェック ボックスをオンにすると、フォルダーがリスト ビューに設定された場合にアイテムが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="2beb0-124">Select this check box to hide the item when the folder is set in list view.</span></span> <span data-ttu-id="2beb0-125">リスト ビューは、レポート マネージャーでサポートされているフォルダーの内容を表示するモードです。</span><span class="sxs-lookup"><span data-stu-id="2beb0-125">List view is a mode for viewing folder contents that is supported in Report Manager.</span></span> <span data-ttu-id="2beb0-126">[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] でこのオプションを設定することで、レポート マネージャーにおけるこのアイテムの表示方法を定義できます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-126">You can set this option in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] to define how this item is viewed in Report Manager.</span></span> <span data-ttu-id="2beb0-127">レポートマネージャーの表示モードの詳細については、 [&#41;レポートマネージャー [コンテンツ] ページ &#40;](../../2014/reporting-services/contents-page-report-manager.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2beb0-127">For more information about view modes in Report Manager, see [Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="2beb0-128">**[適用]**</span><span class="sxs-lookup"><span data-stu-id="2beb0-128">**Apply**</span></span>  
 <span data-ttu-id="2beb0-129">変更を保存する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2beb0-129">Click to save your changes.</span></span>  
  
 <span data-ttu-id="2beb0-130">**削除**</span><span class="sxs-lookup"><span data-stu-id="2beb0-130">**Delete**</span></span>  
 <span data-ttu-id="2beb0-131">レポート サーバー データベースからモデルを削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2beb0-131">Click to remove the model from the report server database.</span></span> <span data-ttu-id="2beb0-132">モデルを削除しても、接続情報を提供している依存共有データ ソースは削除されません。また、そのモデルをデータ ソースとして使用しているレポートも削除されません。</span><span class="sxs-lookup"><span data-stu-id="2beb0-132">Deleting a model does not delete the dependent shared data source that provides connection information, nor does it delete reports that use the model as a data source.</span></span> <span data-ttu-id="2beb0-133">ただし、モデルを削除した後は、そのモデルを使用するレポートを実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2beb0-133">However, after the model is deleted, reports that use the model will no longer run.</span></span>  
  
 <span data-ttu-id="2beb0-134">**移動**</span><span class="sxs-lookup"><span data-stu-id="2beb0-134">**Move**</span></span>  
 <span data-ttu-id="2beb0-135">レポート サーバーのフォルダー階層内でモデルを再配置する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2beb0-135">Click to relocate a model within the report server folder hierarchy.</span></span> <span data-ttu-id="2beb0-136">このボタンをクリックすると、アイテムの移動ページが表示され、フォルダーを参照して新しい場所を選択できます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-136">Clicking this button opens the Move Items page, on which you can browse through folders for a new folder location.</span></span> <span data-ttu-id="2beb0-137">詳細については、「[[アイテムの移動] ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/move-items-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2beb0-137">For more information, see [Move Items Page &#40;Report Manager&#41;](../../2014/reporting-services/move-items-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="2beb0-138">**および**</span><span class="sxs-lookup"><span data-stu-id="2beb0-138">**Save**</span></span>  
 <span data-ttu-id="2beb0-139">モデル定義の読み取り専用コピーを保存する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2beb0-139">Click to save a read-only copy of the model definition.</span></span> <span data-ttu-id="2beb0-140">このファイルは、コンピューターに定義されているファイルの関連付けに応じて、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] または他のアプリケーションで開きます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-140">Depending on the file associations defined on your computer, the file will open in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or a different application.</span></span> <span data-ttu-id="2beb0-141">ほとんどの場合、モデルは XML ファイルとして開きます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-141">In most cases, the model opens as an XML file.</span></span>  
  
 <span data-ttu-id="2beb0-142">開くコピーは、最初にレポート サーバーにパブリッシュされた元のモデル定義と同一です。</span><span class="sxs-lookup"><span data-stu-id="2beb0-142">The copy that you open is identical to the original model definition that was initially published to the report server.</span></span> <span data-ttu-id="2beb0-143">モデルのパブリッシュ後にモデルに設定されたプロパティ (データ ソースのプロパティなど) は、開くファイルに反映されません。</span><span class="sxs-lookup"><span data-stu-id="2beb0-143">Any properties that were set on the model after it was published (such as data source properties) are not reflected in the file that you open.</span></span>  
  
 <span data-ttu-id="2beb0-144">モデル定義を変更して、新しいファイルとして共有フォルダーに保存し、そのモデル定義を新しいアイテムとしてレポート サーバーにアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-144">You can modify the model definition and save it as a new file in a shared folder, and upload the model definition to the report server as a new item.</span></span> <span data-ttu-id="2beb0-145">モデル定義を [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (または他のアプリケーション) で開いているときに加えた変更は、レポート サーバーには直接保存されません。</span><span class="sxs-lookup"><span data-stu-id="2beb0-145">Modifications that you make to the model definition while it is open in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (or another application) are not saved directly to the report server.</span></span> <span data-ttu-id="2beb0-146">変更したモデルをレポート サーバーにパブリッシュするには、ファイルをアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2beb0-146">You must upload the file to publish the modified model to the report server.</span></span>  
  
 <span data-ttu-id="2beb0-147">レポート モデルをモデル デザイナーで開くには、モデルを .smdl ファイルとして保存し、その .smdl ファイルをモデル デザイナーのプロジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2beb0-147">Note that if you want to open the report model in Model Designer, you should save the model as .smdl file, and then add the .smdl file to a project in Model Designer.</span></span>  
  
 <span data-ttu-id="2beb0-148">**Replace**</span><span class="sxs-lookup"><span data-stu-id="2beb0-148">**Replace**</span></span>  
 <span data-ttu-id="2beb0-149">モデル定義をファイル システム上の .smdl ファイルに記述された別のモデル定義に置き換える場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2beb0-149">Click to replace the model definition with a different one from an .smdl file located on the file system.</span></span> <span data-ttu-id="2beb0-150">モデル定義を更新する場合、更新の完了後に共有データ ソースの設定を再設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2beb0-150">If you update a model definition, you must reset the shared data source settings after the update is complete.</span></span>  
  
 <span data-ttu-id="2beb0-151">**[モデルの再生成]**</span><span class="sxs-lookup"><span data-stu-id="2beb0-151">**Regenerate Model**</span></span>  
 <span data-ttu-id="2beb0-152">現在のバージョンを置き換える既定のモデルを再生成する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2beb0-152">Click to regenerate a default model that replaces the current version.</span></span> <span data-ttu-id="2beb0-153">このオプションは、モデルの生成後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-153">This option appears after the model is generated.</span></span> <span data-ttu-id="2beb0-154">生成されるモデルは、共有データ ソースに基づいています。</span><span class="sxs-lookup"><span data-stu-id="2beb0-154">The generated model is based on the shared data source.</span></span> <span data-ttu-id="2beb0-155">生成前にカスタマイズすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2beb0-155">It cannot be customized before it is generated.</span></span> <span data-ttu-id="2beb0-156">生成後は、 **[編集]** をクリックしてモデル定義を開き、ファイル システムに保存して、モデル デザイナーのプロジェクトに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-156">However, after you generate it, you can click **Edit** to open the model definition, save it to the file system, and then add it to a project in Model Designer.</span></span> <span data-ttu-id="2beb0-157">モデルの調整を終えたら、新しいアイテムとしてレポート サーバーにアップロードできます。また、このページの **[更新]** をクリックすると、生成されたモデルを、モデル デザイナーで変更したバージョンに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="2beb0-157">After you refine the model, you can upload it to the report server as a new item, or click **Update** on this page to replace the generated model with the version you revised in Model Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2beb0-158">参照</span><span class="sxs-lookup"><span data-stu-id="2beb0-158">See Also</span></span>  
 <span data-ttu-id="2beb0-159">[レポートまたはモデルの共有データソースへのバインド &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2beb0-159">[Bind a Report or Model to a Shared Data Source &#40;SSRS&#41;](report-data/bind-a-report-or-model-to-a-shared-data-source-ssrs.md) </span></span>  
 [<span data-ttu-id="2beb0-160">Management Studio のレポート サーバーの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="2beb0-160">Report Server in Management Studio F1 Help</span></span>](tools/report-server-in-management-studio-f1-help.md)  
  
  
