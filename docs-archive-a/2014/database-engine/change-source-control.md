---
title: ソース管理の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- IDD_SCC_CONNECTION_DIALOG
helpviewer_keywords:
- Change Source Control dialog box
ms.assetid: e6a5d83c-5809-4c56-907a-73d0c7ccdd7a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 55831529243608e8c71972a31009e5672fb0234f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642329"
---
# <a name="change-source-control"></a><span data-ttu-id="a055b-102">ソース管理の変更</span><span class="sxs-lookup"><span data-stu-id="a055b-102">Change Source Control</span></span>
  <span data-ttu-id="a055b-103">ローカルに保存されたソリューションまたはプロジェクトを、ソース管理データベース フォルダーに関連付ける、接続とバインドの作成と管理を行います。</span><span class="sxs-lookup"><span data-stu-id="a055b-103">Creates and manages the connections and bindings that link a locally saved solution or project to a source control database folder.</span></span>  
  
## <a name="dialog-box-access"></a><span data-ttu-id="a055b-104">ダイアログ ボックスの表示</span><span class="sxs-lookup"><span data-stu-id="a055b-104">Dialog Box Access</span></span>  
 <span data-ttu-id="a055b-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のソリューション エクスプローラーで、項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="a055b-105">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], select an item in Solution Explorer.</span></span> <span data-ttu-id="a055b-106">[**ファイル**] メニューの [**ソース管理**] をクリックし、[**ソース管理の変更**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a055b-106">On the **File** menu, click **Source Control**, and then **Change Source Control**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a055b-107">ソリューション エクスプローラーで項目を右クリックしても、このダイアログ ボックスを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a055b-107">This dialog box is also available by right-clicking the item in Solution Explorer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a055b-108">Options</span><span class="sxs-lookup"><span data-stu-id="a055b-108">Options</span></span>  
 <span data-ttu-id="a055b-109">**束縛**</span><span class="sxs-lookup"><span data-stu-id="a055b-109">**Bind**</span></span>  
 <span data-ttu-id="a055b-110">指定したソース管理サーバーの場所に、選択した項目を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="a055b-110">Associate selected items with a specified source control server location.</span></span> <span data-ttu-id="a055b-111">たとえば、このボタンを使用して、最後に認識したソース管理サーバーのフォルダーとデータベースにバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="a055b-111">For example, you can use this button to bind to the last known source control server folder and database.</span></span> <span data-ttu-id="a055b-112">最近使用したサーバーのフォルダーやデータベースが見つからない場合、別のものを指定するように求めるメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a055b-112">If a recent server folder or database cannot be found, you are prompted to specify another.</span></span>  
  
 <span data-ttu-id="a055b-113">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="a055b-113">**Browse**</span></span>  
 <span data-ttu-id="a055b-114">指定した項目に適用する、新しいソース管理サーバーの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="a055b-114">Navigate to a new source control server location for the specified item.</span></span>  
  
 <span data-ttu-id="a055b-115">**[列]**</span><span class="sxs-lookup"><span data-stu-id="a055b-115">**Columns**</span></span>  
 <span data-ttu-id="a055b-116">表示する列とその表示順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="a055b-116">Identify columns to display and the order in which they are displayed.</span></span>  
  
 <span data-ttu-id="a055b-117">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="a055b-117">**Connect**</span></span>  
 <span data-ttu-id="a055b-118">選択した項目とソース管理サーバーの間に接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="a055b-118">Create a connection between selected items and the source control server.</span></span>  
  
 <span data-ttu-id="a055b-119">**接続済み**</span><span class="sxs-lookup"><span data-stu-id="a055b-119">**Connected**</span></span>  
 <span data-ttu-id="a055b-120">選択したソリューションまたはプロジェクトの接続状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a055b-120">Displays the connection status of a selected solution or project.</span></span>  
  
 <span data-ttu-id="a055b-121">**Disconnect (切断)**</span><span class="sxs-lookup"><span data-stu-id="a055b-121">**Disconnect**</span></span>  
 <span data-ttu-id="a055b-122">コンピューター上のソリューションまたはプロジェクトのローカル コピーと、データベース上のマスター コピーとの接続を解除します。</span><span class="sxs-lookup"><span data-stu-id="a055b-122">Disconnect the local copy of a solution or project on your computer from its master copy in the database.</span></span> <span data-ttu-id="a055b-123">たとえばラップトップを使用してオフラインで作業しているときなど、コンピューターとソース管理サーバーの接続を解除する前にこのコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a055b-123">Use this command before disconnecting your computer from the source control server, for example, when working offline on your laptop.</span></span>  
  
 <span data-ttu-id="a055b-124">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="a055b-124">**OK**</span></span>  
 <span data-ttu-id="a055b-125">このダイアログ ボックスで加えた変更が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a055b-125">Accept changes made in the dialog box.</span></span>  
  
 <span data-ttu-id="a055b-126">**プロバイダー**</span><span class="sxs-lookup"><span data-stu-id="a055b-126">**Provider**</span></span>  
 <span data-ttu-id="a055b-127">ソース管理プラグインの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a055b-127">Displays the name of your source control plug-in.</span></span>  
  
 <span data-ttu-id="a055b-128">**[更新]**</span><span class="sxs-lookup"><span data-stu-id="a055b-128">**Refresh**</span></span>  
 <span data-ttu-id="a055b-129">このダイアログ ボックスに表示されている、すべてのプロジェクトの接続情報を更新します。</span><span class="sxs-lookup"><span data-stu-id="a055b-129">Refreshes the connection information for all projects listed in this dialog box.</span></span>  
  
 <span data-ttu-id="a055b-130">**[サーバー バインド]**</span><span class="sxs-lookup"><span data-stu-id="a055b-130">**Server Binding**</span></span>  
 <span data-ttu-id="a055b-131">ソース管理サーバーへの項目のバインドを示します。</span><span class="sxs-lookup"><span data-stu-id="a055b-131">Indicates the item's binding to a source control server.</span></span>  
  
 <span data-ttu-id="a055b-132">**[サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="a055b-132">**Server Name**</span></span>  
 <span data-ttu-id="a055b-133">対応するソリューションまたはプロジェクトがバインドされているソース管理サーバーの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a055b-133">Displays the name of the source control server to which the corresponding solution or project is bound.</span></span>  
  
 <span data-ttu-id="a055b-134">**[ソリューション/プロジェクト]**</span><span class="sxs-lookup"><span data-stu-id="a055b-134">**Solution/Project**</span></span>  
 <span data-ttu-id="a055b-135">現在の選択における各ソリューションおよびプロジェクトの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a055b-135">Displays the name of each solution and project in the current selection.</span></span>  
  
 <span data-ttu-id="a055b-136">**Sort**</span><span class="sxs-lookup"><span data-stu-id="a055b-136">**Sort**</span></span>  
 <span data-ttu-id="a055b-137">表示される列の順序を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="a055b-137">Sort the order of displayed columns.</span></span>  
  
 <span data-ttu-id="a055b-138">**状態**</span><span class="sxs-lookup"><span data-stu-id="a055b-138">**Status**</span></span>  
 <span data-ttu-id="a055b-139">項目のバインドと接続の状態を示します。</span><span class="sxs-lookup"><span data-stu-id="a055b-139">Identifies the binding and connection status of an item.</span></span> <span data-ttu-id="a055b-140">選択可能なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a055b-140">Possible options are:</span></span>  
  
|<span data-ttu-id="a055b-141">**オプション**</span><span class="sxs-lookup"><span data-stu-id="a055b-141">**Option**</span></span>|<span data-ttu-id="a055b-142">**説明**</span><span class="sxs-lookup"><span data-stu-id="a055b-142">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="a055b-143">有効</span><span class="sxs-lookup"><span data-stu-id="a055b-143">Valid</span></span>|<span data-ttu-id="a055b-144">項目は、その項目が属するサーバー フォルダーに正しくバインドされ、接続されています。</span><span class="sxs-lookup"><span data-stu-id="a055b-144">The item is correctly bound and connected to the server folder to which it belongs.</span></span>|  
|<span data-ttu-id="a055b-145">無効</span><span class="sxs-lookup"><span data-stu-id="a055b-145">Invalid</span></span>|<span data-ttu-id="a055b-146">項目は、その項目が属するフォルダーに正しくバインドされていないか、接続が切断されています。</span><span class="sxs-lookup"><span data-stu-id="a055b-146">The item is incorrectly bound to or disconnected from the folder to which it belongs.</span></span> <span data-ttu-id="a055b-147">この項目には、[**バインド**] ではなく [**ソース管理に追加**] コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a055b-147">Use the **Add to Source Control** command instead of **Bind** for this item.</span></span>|  
|<span data-ttu-id="a055b-148">Unknown</span><span class="sxs-lookup"><span data-stu-id="a055b-148">Unknown</span></span>|<span data-ttu-id="a055b-149">ソース管理下にある項目の状態がまだ決定されていません。</span><span class="sxs-lookup"><span data-stu-id="a055b-149">The status of the item under source control has not yet been determined.</span></span>|  
|<span data-ttu-id="a055b-150">[制御しない]</span><span class="sxs-lookup"><span data-stu-id="a055b-150">Not Controlled</span></span>|<span data-ttu-id="a055b-151">項目がソース管理下にありません。</span><span class="sxs-lookup"><span data-stu-id="a055b-151">The item has not been placed under source control.</span></span>|  
  
 <span data-ttu-id="a055b-152">**バインドの解除**</span><span class="sxs-lookup"><span data-stu-id="a055b-152">**Unbind**</span></span>  
 <span data-ttu-id="a055b-153">[**ソース管理**] ダイアログボックスを表示して、ソース管理から選択した項目を削除したり、その項目と現在のフォルダーとの関連付けを完全に解除したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a055b-153">Display the **Source Control** dialog box to allow you to remove selected items from source control and permanently disassociate the items from their present folders.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a055b-154">参照</span><span class="sxs-lookup"><span data-stu-id="a055b-154">See Also</span></span>  
 [<span data-ttu-id="a055b-155">ソリューション エクスプローラーのソース管理</span><span class="sxs-lookup"><span data-stu-id="a055b-155">Solution Explorer Source Control</span></span>](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
