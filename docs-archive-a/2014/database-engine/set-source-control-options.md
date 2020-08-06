---
title: ソース管理オプションの設定 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Source_Control.Visual_SourceSafe
- VS.ToolsOptionsPages.Source_Control.General
- VS.ToolsOptionsPages.Source_Control.Environment
helpviewer_keywords:
- source controls [SQL Server Management Studio], options
ms.assetid: b2c6ca00-46f0-4f86-b067-07bae779c147
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d4ca19180a7291763780f300172bb2292a98c8c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632082"
---
# <a name="set-source-control-options"></a><span data-ttu-id="54645-102">ソース管理のオプションの設定</span><span class="sxs-lookup"><span data-stu-id="54645-102">Set Source Control Options</span></span>
  <span data-ttu-id="54645-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に組み込まれているソース管理機能を使用する前に、さまざまな作業環境に合わせて、ソース管理のオプションを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54645-103">Before you take advantage of the source control features built into [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], you should configure your source control options for the various environments in which you work.</span></span>  
  
 <span data-ttu-id="54645-104">ソース管理のオプションを構成するには、[**オプション**] ダイアログボックスを使用して、1つまたは複数のソース管理ロールを構成します。</span><span class="sxs-lookup"><span data-stu-id="54645-104">You configure source control options by using the **Options** dialog box to configure one or more source control roles.</span></span> <span data-ttu-id="54645-105">ロールは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用する際の設定を示す一般的な説明と、その設定に関連付けられたソース管理オプションから構成されています。</span><span class="sxs-lookup"><span data-stu-id="54645-105">A role consists of a general description of the setting in which you use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], and the source control options associated with that setting.</span></span>  
  
 <span data-ttu-id="54645-106">たとえば、個人データベース開発者であれば、ファイルをチェックインした後でチェックアウト状態にしておくことで、通常は他のユーザーとの競合を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="54645-106">For example, if you are an independent database developer, you generally do not create conflicts with other users by keeping files checked out after you check them in.</span></span> <span data-ttu-id="54645-107">そのため、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] では個人開発者ロールが定義されています。</span><span class="sxs-lookup"><span data-stu-id="54645-107">Consequently, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] defines an Independent Developer role.</span></span> <span data-ttu-id="54645-108">このロールの場合、[チェックイン [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] **するときに項目をチェックアウトする**] オプションが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="54645-108">For this role, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] automatically selects the **Keep items checked out when checking in** option.</span></span>  
  
 <span data-ttu-id="54645-109">ロールは定義およびカスタマイズできるため、1 つの設定から別の設定に移動するたびにソース管理を完全に再設定する必要はなく、さまざまな環境設定で作業できます。</span><span class="sxs-lookup"><span data-stu-id="54645-109">Because you can define and customize roles, you can work in varying development settings without having to completely reconfigure source control every time you move from one setting to another.</span></span>  
  
### <a name="to-set-source-control-options"></a><span data-ttu-id="54645-110">ソース管理のオプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="54645-110">To set source control options</span></span>  
  
1.  <span data-ttu-id="54645-111">**[ツール]** メニューの **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="54645-111">On the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="54645-112">[**オプション**] ダイアログボックスで、[**ソース管理**] を展開し、[**プラグインの選択**] ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="54645-112">In the **Options** dialog box, expand **Source Control**, and then click the **Plug-in Selection** page.</span></span>  
  
     <span data-ttu-id="54645-113">**[現在のソース管理プラグイン]**</span><span class="sxs-lookup"><span data-stu-id="54645-113">**Current source control plug-in**</span></span>  
     <span data-ttu-id="54645-114">この一覧から、使用するソース管理を選択します。</span><span class="sxs-lookup"><span data-stu-id="54645-114">Select the source control you want to use from this list.</span></span> <span data-ttu-id="54645-115">ソース管理製品クライアントを一覧表示するには、このコンピューターにクライアントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="54645-115">The source control product client must be installed on this computer to appear on the list.</span></span> <span data-ttu-id="54645-116">ソース管理クライアントがコンピューターにインストールされていない場合、選択できるのは [なし] だけです。</span><span class="sxs-lookup"><span data-stu-id="54645-116">If no source control clients are installed on the computer, the only selection available will be None.</span></span> <span data-ttu-id="54645-117">Microsoft Source Safe がインストールされている場合は、次のプラグインが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54645-117">If you have installed Microsoft Source Safe, then the following plug ins are displayed:</span></span>  
  
    -   <span data-ttu-id="54645-118">Microsoft Visual SourceSafe</span><span class="sxs-lookup"><span data-stu-id="54645-118">Microsoft Visual SourceSafe</span></span>  
  
    -   <span data-ttu-id="54645-119">Microsoft Visual SourceSafe (インターネット)</span><span class="sxs-lookup"><span data-stu-id="54645-119">Microsoft Visual SourceSafe(Internet)</span></span>  
  
3.  <span data-ttu-id="54645-120">使用するソース管理ロールのログイン資格情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="54645-120">Set login credentials for each source control role that you want to use.</span></span> <span data-ttu-id="54645-121">このページは、ソース管理プラグインがインストールされている場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="54645-121">This page is only available if a source control plug-in is installed.</span></span>  
  
     <span data-ttu-id="54645-122">**ロールの説明**</span><span class="sxs-lookup"><span data-stu-id="54645-122">**Role Description**</span></span>  
     <span data-ttu-id="54645-123">いずれかのロールを選択すると、適切なソース管理オプションが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="54645-123">Selecting one of these roles causes the appropriate source control options to be selected automatically.</span></span>  
  
    |<span data-ttu-id="54645-124">Role</span><span class="sxs-lookup"><span data-stu-id="54645-124">Role</span></span>|<span data-ttu-id="54645-125">説明</span><span class="sxs-lookup"><span data-stu-id="54645-125">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="54645-126">**Visual SourceSafe**</span><span class="sxs-lookup"><span data-stu-id="54645-126">**Visual SourceSafe**</span></span>|<span data-ttu-id="54645-127">Visual SourceSafe ユーザーが最もよく使用する設定を使用することを指定し [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="54645-127">Specifies that you want to use the settings most commonly used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe users.</span></span>|  
    |<span data-ttu-id="54645-128">**[個人開発者]**</span><span class="sxs-lookup"><span data-stu-id="54645-128">**Independent Developer**</span></span>|<span data-ttu-id="54645-129">独立して作業していることを指定します。</span><span class="sxs-lookup"><span data-stu-id="54645-129">Specifies that you are working independently.</span></span>|  
    |<span data-ttu-id="54645-130">**カスタム**</span><span class="sxs-lookup"><span data-stu-id="54645-130">**Custom**</span></span>|<span data-ttu-id="54645-131">ロールの設定を変更したことを指定します。</span><span class="sxs-lookup"><span data-stu-id="54645-131">Specifies that you have modified the settings for a role.</span></span>|  
  
     <span data-ttu-id="54645-132">**[バックグラウンドで状態の更新]**</span><span class="sxs-lookup"><span data-stu-id="54645-132">**Perform background status updates**</span></span>  
     <span data-ttu-id="54645-133">ソリューション エクスプローラーのソース管理シグナル アイコンを、項目のステータス変更に応じて自動的に更新します。</span><span class="sxs-lookup"><span data-stu-id="54645-133">Automatically updates the source control signal icons in Solution Explorer as an item's status changes.</span></span> <span data-ttu-id="54645-134">サーバーに負荷が集中する操作の実行時の遅延、特にソリューションまたはプロジェクトをソース管理から開く場合の遅延については、このチェック ボックスをオフにすることにより、パフォーマンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="54645-134">If you experience delays when performing server-intensive operations, especially when opening a solution or project from source control, clearing this check box could improve performance.</span></span>  
  
     <span data-ttu-id="54645-135">**Login ID**</span><span class="sxs-lookup"><span data-stu-id="54645-135">**Login ID**</span></span>  
     <span data-ttu-id="54645-136">ソース管理プロバイダーへのログインに使用されるユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="54645-136">Specifies the user name to use to log in to the source control provider.</span></span> <span data-ttu-id="54645-137">ソース管理プロバイダーでサポートされている場合、この名前は、ソース管理サーバーに接続するために、[**ログイン**] ダイアログボックスに自動的に入力されます。</span><span class="sxs-lookup"><span data-stu-id="54645-137">If supported by your source control provider, this name will be filled in automatically in the **Login** dialog box to reach your source control server.</span></span> <span data-ttu-id="54645-138">このオプションを有効にするには、ソース管理プロバイダーの管理者プログラムを使用して自動ユーザー ログインを無効にしてから、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を再起動します。</span><span class="sxs-lookup"><span data-stu-id="54645-138">To make this option active, disable automatic user logins by using your source control provider's administrator program, and then restart [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="54645-139">**詳細**</span><span class="sxs-lookup"><span data-stu-id="54645-139">**Advanced**</span></span>  
     <span data-ttu-id="54645-140">ソース管理に項目を追加するための追加オプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="54645-140">Displays additional options for adding items to source control.</span></span> <span data-ttu-id="54645-141">これらのオプションは、ソース管理プロバイダーに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="54645-141">These options vary depending on your source control provider.</span></span> <span data-ttu-id="54645-142">これらのオプションのヘルプは、ソース管理プログラムによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="54645-142">Help for these options is provided by the source control program.</span></span>  
  
4.  <span data-ttu-id="54645-143">[**環境**] ページを選択します。</span><span class="sxs-lookup"><span data-stu-id="54645-143">Select the **Environment** page.</span></span>  
  
5.  <span data-ttu-id="54645-144">[**ソース管理の環境設定**] ボックスで、ソース管理オプションを設定するロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="54645-144">In the **Source Control Environment Settings** box, select the role on which you want to set source control options.</span></span>  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="54645-145">によって、選択したロールに対する既定のソース管理オプションが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="54645-145">automatically selects the default source control options for the role you have selected.</span></span> <span data-ttu-id="54645-146">既定のオプションをすべてオフにした場合、[**ソース管理の環境設定**] ボックスには、最初に選択したロールをカスタマイズしたことを示す**カスタム**オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54645-146">If you clear any of the default options, the **Source Control Environment Settings** box displays the **Custom** option to indicate that you have customized the originally selected role.</span></span>  
  
     <span data-ttu-id="54645-147">**[ソース管理の設定]**</span><span class="sxs-lookup"><span data-stu-id="54645-147">**Source Control Environment Settings**</span></span>  
     <span data-ttu-id="54645-148">使用するロールを指定します。</span><span class="sxs-lookup"><span data-stu-id="54645-148">Specifies the role that you want to use.</span></span> [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="54645-149">では、次のロールが定義されています。</span><span class="sxs-lookup"><span data-stu-id="54645-149">defines the following roles.</span></span>  
  
    |<span data-ttu-id="54645-150">Role</span><span class="sxs-lookup"><span data-stu-id="54645-150">Role</span></span>|<span data-ttu-id="54645-151">説明</span><span class="sxs-lookup"><span data-stu-id="54645-151">Description</span></span>|  
    |----------|-----------------|  
    |<span data-ttu-id="54645-152">**Visual SourceSafe**</span><span class="sxs-lookup"><span data-stu-id="54645-152">**Visual SourceSafe**</span></span>|<span data-ttu-id="54645-153">Visual SourceSafe ユーザーが最もよく使用する設定を使用することを指定し [!INCLUDE[msCoName](../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="54645-153">Specifies that you want to use the settings most commonly used by [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe users.</span></span>|  
    |<span data-ttu-id="54645-154">**[個人開発者]**</span><span class="sxs-lookup"><span data-stu-id="54645-154">**Independent Developer**</span></span>|<span data-ttu-id="54645-155">独立して作業していることを指定します。</span><span class="sxs-lookup"><span data-stu-id="54645-155">Specifies that you are working independently.</span></span>|  
    |<span data-ttu-id="54645-156">**カスタム**</span><span class="sxs-lookup"><span data-stu-id="54645-156">**Custom**</span></span>|<span data-ttu-id="54645-157">ロールの設定を変更したことを指定します。</span><span class="sxs-lookup"><span data-stu-id="54645-157">Specifies that you have modified the settings for a role.</span></span>|  
  
     <span data-ttu-id="54645-158">いずれかのロールを選択すると、適切なソース管理オプションが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="54645-158">Selecting one of these roles causes the appropriate source control options to be selected automatically.</span></span>  
  
     <span data-ttu-id="54645-159">**[チェックインするときに項目のチェックアウト状態を保持]**</span><span class="sxs-lookup"><span data-stu-id="54645-159">**Keep items checked out when checking in**</span></span>  
     <span data-ttu-id="54645-160">ソース管理ストアを更新するために項目をチェックインするときに項目がチェックアウト状態を保つようにすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="54645-160">Specifies that when you check in items to update the source control store, the items should remain checked out to you.</span></span> <span data-ttu-id="54645-161">特定のチェックインに対してこのオプションを変更する場合は、[**チェックイン**] ダイアログボックスの [**オプション**] 矢印をクリックし、[**チェックアウト**したままにする] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="54645-161">If you want to change this option for a specific check-in, click the **Options** arrow in the **Check in** dialog box, and then clear the **Keep checked out** check box.</span></span>  
  
     <span data-ttu-id="54645-162">**[チェックイン項目]**</span><span class="sxs-lookup"><span data-stu-id="54645-162">**Checked-in items**</span></span>  
     <span data-ttu-id="54645-163">チェックアウトされて [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] いない項目を編集しようとしたときの動作を指定するオプションの一覧を表示します。次の表では、使用可能なオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="54645-163">Displays a list of options that specify how [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] should behave when you attempt to edit an item that is not checked out. The following tables describe the available options.</span></span>  
  
     <span data-ttu-id="54645-164">**Saving**</span><span class="sxs-lookup"><span data-stu-id="54645-164">**Saving**</span></span>  
  
    |<span data-ttu-id="54645-165">アクション</span><span class="sxs-lookup"><span data-stu-id="54645-165">Action</span></span>|<span data-ttu-id="54645-166">説明</span><span class="sxs-lookup"><span data-stu-id="54645-166">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="54645-167">**[チェックアウトを確認する]**</span><span class="sxs-lookup"><span data-stu-id="54645-167">**Prompt for check out**</span></span>|<span data-ttu-id="54645-168">[**チェックアウト**] ダイアログボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="54645-168">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="54645-169">**[自動的にチェックアウトする]**</span><span class="sxs-lookup"><span data-stu-id="54645-169">**Check out automatically**</span></span>|<span data-ttu-id="54645-170">[チェックアウト] ダイアログボックスを表示せ**ずに項目**をチェックアウトします。</span><span class="sxs-lookup"><span data-stu-id="54645-170">Checks out the item without displaying the **Check Out** dialog box.</span></span> <span data-ttu-id="54645-171">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="54645-171">This is the default option.</span></span>|  
    |<span data-ttu-id="54645-172">**名前を付けて保存**</span><span class="sxs-lookup"><span data-stu-id="54645-172">**Save as**</span></span>|<span data-ttu-id="54645-173">新しいファイルとして保存します。</span><span class="sxs-lookup"><span data-stu-id="54645-173">Saves as a new file.</span></span>|  
  
     <span data-ttu-id="54645-174">**編集**</span><span class="sxs-lookup"><span data-stu-id="54645-174">**Editing**</span></span>  
  
    |<span data-ttu-id="54645-175">アクション</span><span class="sxs-lookup"><span data-stu-id="54645-175">Action</span></span>|<span data-ttu-id="54645-176">説明</span><span class="sxs-lookup"><span data-stu-id="54645-176">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="54645-177">**[チェックアウトを確認する]**</span><span class="sxs-lookup"><span data-stu-id="54645-177">**Prompt for check out**</span></span>|<span data-ttu-id="54645-178">[**チェックアウト**] ダイアログボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="54645-178">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="54645-179">**[排他的チェックアウトを確認する]**</span><span class="sxs-lookup"><span data-stu-id="54645-179">**Prompt for exclusive checkouts**</span></span>|<span data-ttu-id="54645-180">[**チェックアウト**] ダイアログボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="54645-180">Displays the **Check Out** dialog box.</span></span>|  
    |<span data-ttu-id="54645-181">**[自動的にチェックアウトする]**</span><span class="sxs-lookup"><span data-stu-id="54645-181">**Check out automatically**</span></span>|<span data-ttu-id="54645-182">[チェックアウト] ダイアログボックスを表示せ**ずに項目**をチェックアウトします。</span><span class="sxs-lookup"><span data-stu-id="54645-182">Checks out the item without displaying the **Check Out** dialog box.</span></span> <span data-ttu-id="54645-183">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="54645-183">This is the default option.</span></span>|  
    |<span data-ttu-id="54645-184">**何もしない**</span><span class="sxs-lookup"><span data-stu-id="54645-184">**Do nothing**</span></span>|<span data-ttu-id="54645-185">ファイルをチェックアウトしません。</span><span class="sxs-lookup"><span data-stu-id="54645-185">Does not check out the file.</span></span>|  
  
     <span data-ttu-id="54645-186">**[チェックインしてある項目の編集を許可]**</span><span class="sxs-lookup"><span data-stu-id="54645-186">**Allow checked-in items to be edited**</span></span>  
     <span data-ttu-id="54645-187">チェックインされている項目をメモリ内で編集できることを指定します。</span><span class="sxs-lookup"><span data-stu-id="54645-187">Specifies that items that are checked in can be edited in memory.</span></span> <span data-ttu-id="54645-188">このチェックボックスをオンにすると、チェックインした項目を編集しようとしたときに **[チェックアウト] ダイアログボックス**に [**編集**] ボタンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54645-188">If you select this check box, an **Edit** button appears in the **Check Out** dialog box when you attempt to edit a checked-in item.</span></span> <span data-ttu-id="54645-189">このボタンをクリックすると、項目を編集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="54645-189">After clicking this button, you can edit the item.</span></span> <span data-ttu-id="54645-190">項目を保存する場合は、チェックアウトするか、別の場所に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54645-190">If you attempt to save the item, you must check it out or save it to a different location.</span></span>  
  
     <span data-ttu-id="54645-191">**リセット**</span><span class="sxs-lookup"><span data-stu-id="54645-191">**Reset**</span></span>  
     <span data-ttu-id="54645-192">ソース管理確認ダイアログ ボックスを既定の設定にリセットします。</span><span class="sxs-lookup"><span data-stu-id="54645-192">Resets source control confirmation dialog boxes to their default settings.</span></span> <span data-ttu-id="54645-193">たとえば、[ソース管理] ダイアログボックスで [**今後、このダイアログを表示しない**] チェックボックスをオンにした場合は、[**リセット**] オプションを選択すると、その操作が元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="54645-193">For example, if you have selected the **Don't show this dialog again** check box in a source control dialog box, selecting the **Reset** option reverses that action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54645-194">参照</span><span class="sxs-lookup"><span data-stu-id="54645-194">See Also</span></span>  
 <span data-ttu-id="54645-195">[ソース管理の基礎](../../2014/database-engine/source-control-basics.md) </span><span class="sxs-lookup"><span data-stu-id="54645-195">[Source Control Basics](../../2014/database-engine/source-control-basics.md) </span></span>  
 <span data-ttu-id="54645-196">[ソース管理接続の変更](../../2014/database-engine/change-source-control-connections.md) </span><span class="sxs-lookup"><span data-stu-id="54645-196">[Change Source Control Connections](../../2014/database-engine/change-source-control-connections.md) </span></span>  
 [<span data-ttu-id="54645-197">ソース管理からのファイルの除外</span><span class="sxs-lookup"><span data-stu-id="54645-197">Exclude Files from Source Control</span></span>](../../2014/database-engine/exclude-files-from-source-control.md)  
  
  
