---
title: ウィザードを使用して拡張イベントセッションを作成する (オブジェクトエクスプローラー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- Sql12.ssms.XeWizard.Summary.f1
- Sql12.ssms.XeWizard.SetSessionProperties.f1
- Sql12.ssms.XeWizard.CaptureAddFields.f1
- Sql12.ssms.XeWizard.SelectEvents.f1
- Sql12.ssms.XeWizard.SpecifySessionTargets.f1
- Sql12.ssms.XeWizard.Welcome.f1
- sql12.ssms.XeWizard.Welcome.f1
- Sql12.ssms.XeWizard.ChooseTemplate.f1
- Sql12.ssms.XeWizard.SetSessionEventFilters.f1
- Sql12.ssms.XeWizard.Results.f1
helpviewer_keywords:
- Sql11.ssms.XeWizard.CaptureAddFields.f1
- Sql11.ssms.XeWizard.SetSessionEventFilters.f1
- Sql11.ssms.XeWizard.SpecifySessionTargets.f1
- Sql11.ssms.XeWizard.Results.f1
- Sql11.ssms.XeWizard.ChooseTemplate.f1
- Sql11.ssms.XeWizard.SetSessionProperties.f1
- Sql11.ssms.XeWizard.Welcome.f1
- Sql11.ssms.XeWizard.Summary.f1
- Sql11.ssms.XeWizard.SelectEvents.f1
ms.assetid: 80c0456f-17c0-41d8-b2aa-502a2f3bb6de
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cdfc9141b0b99d5b06fc73044b8f4fae623922b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641217"
---
# <a name="create-an-extended-events-session-using-the-wizard-object-explorer"></a><span data-ttu-id="4e3a1-102">ウィザードを使用した拡張イベント セッションの作成 (オブジェクト エクスプローラー)</span><span class="sxs-lookup"><span data-stu-id="4e3a1-102">Create an Extended Events Session Using the Wizard (Object Explorer)</span></span>
  <span data-ttu-id="4e3a1-103">サーバー上の特定のイベントを選んでキャプチャできるように、拡張イベントには、一連の手順に従って拡張イベント セッションを作成できる新規セッション ウィザードが導入されました。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-103">To help you select and capture events on your server, Extended Events includes a New Session Wizard that guides you through the steps to create an Extended Events session.</span></span> <span data-ttu-id="4e3a1-104">新しいセッション ウィザードでは、拡張イベントのほとんどの機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-104">The New Session Wizard exposes most of the Extended Events functionality.</span></span> <span data-ttu-id="4e3a1-105">[[新しいセッション] ダイアログ](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)では、データのキャプチャ、表示、および分析を行う拡張イベント セッションも定義できます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-105">The [New Session dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md) also lets you define an Extended Events session that captures, displays, and analyzes your data.</span></span> <span data-ttu-id="4e3a1-106">[新しいセッション] ダイアログでは、拡張イベントのすべての機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-106">The New Session dialog exposes all Extended Events functionality.</span></span>  
  
### <a name="to-open-the-new-session-wizard"></a><span data-ttu-id="4e3a1-107">新規セッション ウィザードを開くには</span><span class="sxs-lookup"><span data-stu-id="4e3a1-107">To open the New Session Wizard</span></span>  
  
1.  <span data-ttu-id="4e3a1-108">オブジェクト エクスプローラーで **[管理]** ノードを展開し、 **[拡張イベント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-108">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="4e3a1-109">**[セッション]** を右クリックし、 **[新規セッション ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-109">Right-click **Sessions**, and then click **New Session Wizard**.</span></span>  
  
### <a name="use-the-following-new-session-wizard-pages-to-create-an-event-session"></a><span data-ttu-id="4e3a1-110">新規セッション ウィザードの各ページを使用してイベント セッションを作成する</span><span class="sxs-lookup"><span data-stu-id="4e3a1-110">Use the following New Session Wizard pages to create an event session</span></span>  
  
-   [<span data-ttu-id="4e3a1-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="4e3a1-111">Introduction</span></span>](#BKMK_Welcome)  
  
-   [<span data-ttu-id="4e3a1-112">セッションのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="4e3a1-112">Set Session Properties</span></span>](#BKMK_SetSessionProperties)  
  
-   [<span data-ttu-id="4e3a1-113">テンプレートの選択</span><span class="sxs-lookup"><span data-stu-id="4e3a1-113">Choose Template</span></span>](#BKMK_ChooseTemplate)  
  
-   [<span data-ttu-id="4e3a1-114">キャプチャするイベントの選択</span><span class="sxs-lookup"><span data-stu-id="4e3a1-114">Select Events to Capture</span></span>](#BKMK_SelectEventsToCapture)  
  
-   [<span data-ttu-id="4e3a1-115">グローバル フィールドのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="4e3a1-115">Capture Global Fields</span></span>](#BKMK_CaptureGlobalFields)  
  
-   [<span data-ttu-id="4e3a1-116">セッション イベント フィルターの設定</span><span class="sxs-lookup"><span data-stu-id="4e3a1-116">Set Session Event Filters</span></span>](#BKMK_SetSessionEventFilters)  
  
-   [<span data-ttu-id="4e3a1-117">セッション データ ストレージの指定</span><span class="sxs-lookup"><span data-stu-id="4e3a1-117">Specify Session Data Storage</span></span>](#BKMK_SpecifySessionDataOutput)  
  
-   [<span data-ttu-id="4e3a1-118">要約</span><span class="sxs-lookup"><span data-stu-id="4e3a1-118">Summary</span></span>](#BKMK_Summary)  
  
-   [<span data-ttu-id="4e3a1-119">イベントセッションの作成</span><span class="sxs-lookup"><span data-stu-id="4e3a1-119">Create Event Session</span></span>](#BKMK_CreateEventSession)  
  
##  <a name="introduction"></a><a name="BKMK_Welcome"></a><span data-ttu-id="4e3a1-120">基礎</span><span class="sxs-lookup"><span data-stu-id="4e3a1-120">Introduction</span></span>  
 <span data-ttu-id="4e3a1-121">**[説明]** ページで、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-121">On the **Introduction** page, do the following:</span></span>  
  
-   <span data-ttu-id="4e3a1-122">新規セッション ウィザードの **[説明]** ページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-122">On the **Introduction** page of the New Session Wizard, click **Next**.</span></span>  
  
     <span data-ttu-id="4e3a1-123">このウィザードを複数回使用する場合で、なおかつウィザードの起動時に毎回同じ説明を読む必要がない場合は、**[次回からこのページを表示しない]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-123">Select the **Do not show this page again** check box if you will be using the wizard more than once and do not want to read the introduction each time the wizard is launched.</span></span>  
  
##  <a name="set-session-properties"></a><a name="BKMK_SetSessionProperties"></a><span data-ttu-id="4e3a1-124">セッションのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="4e3a1-124">Set Session Properties</span></span>  
 <span data-ttu-id="4e3a1-125">**[セッションのプロパティの設定]** ページで、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-125">On the **Set Session Properties** page, do the following:</span></span>  
  
-   <span data-ttu-id="4e3a1-126">**[セッション名]** ボックスに、イベント セッションのわかりやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-126">In the **Session name** box, type a meaningful name for the event session.</span></span>  
  
     <span data-ttu-id="4e3a1-127">サーバーの起動時にセッションを開始する場合は、 **[サーバーの起動時にイベント セッションを開始する]** チェック ボックスをオンにし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-127">If you want to start the session when you start the server, select the **Start the event session at server startup** check box, and then click **Next**.</span></span>  
  
##  <a name="choose-template"></a><a name="BKMK_ChooseTemplate"></a><span data-ttu-id="4e3a1-128">テンプレートの選択</span><span class="sxs-lookup"><span data-stu-id="4e3a1-128">Choose Template</span></span>  
 <span data-ttu-id="4e3a1-129">**[テンプレートの選択]** ページで、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-129">On the **Choose Template** page, do the following:</span></span>  
  
-   <span data-ttu-id="4e3a1-130">共通の問題を想定してあらかじめ構成された一連のテンプレートから選ぶには、 **[このイベント セッション テンプレートを使用する]** オプションをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-130">Select the **Use this event session template** option to select from a set of pre-configured templates designed for common problems.</span></span> <span data-ttu-id="4e3a1-131">使用するテンプレートをドロップダウン リストから選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-131">Select the template you want to use from the drop-down list, and then click **Next**.</span></span>  
  
     <span data-ttu-id="4e3a1-132">\- または -</span><span class="sxs-lookup"><span data-stu-id="4e3a1-132">-OR-</span></span>  
  
-   <span data-ttu-id="4e3a1-133">事前構成済みのテンプレートを使用しない場合は、 **[テンプレートを使用しない]** オプションをオンにして **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-133">Select the **Do not use a template** option if you do not want to use any pre-configured template, and then click **Next**.</span></span>  
  
##  <a name="select-events-to-capture"></a><a name="BKMK_SelectEventsToCapture"></a><span data-ttu-id="4e3a1-134">キャプチャするイベントの選択</span><span class="sxs-lookup"><span data-stu-id="4e3a1-134">Select Events to Capture</span></span>  
 <span data-ttu-id="4e3a1-135">**[キャプチャするイベントの選択]** ページで、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-135">On the **Select Events to Capture** page, do the following:</span></span>  
  
1.  <span data-ttu-id="4e3a1-136">キャプチャするイベントを **[イベント ライブラリ]** から選択し、右矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-136">Select the events you want to capture from the **Event library**, and then click the right arrow.</span></span> <span data-ttu-id="4e3a1-137">Shift キーまたは Ctrl キーを押しながらクリックすることにより、[イベント ライブラリ] で複数のイベントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-137">You can select multiple events in the Event Library by using either Shift+Click or Ctrl+Click.</span></span>  
  
     <span data-ttu-id="4e3a1-138">キャプチャするイベントの検索方法をドロップダウン リスト ボックスから選択できます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-138">You can select how you want to search for the events you want to capture from the drop-down list box.</span></span> <span data-ttu-id="4e3a1-139">たとえば、イベント名を検索する以外にも、イベント名とその説明を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-139">For example, you can search for event names or event names and their descriptions.</span></span> <span data-ttu-id="4e3a1-140">検索する文字列を **[イベント ライブラリ]** ボックスに入力することによって、テーブル内から任意の単語を検索できます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-140">You can search for any word in the table by entering the text you want to search for in the **Event library** box.</span></span> <span data-ttu-id="4e3a1-141">たとえば、 **lock_acquired**イベントを検索する場合は、「 **lock**」または「lock の**取得**」と入力できます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-141">For example, if you want to find the **lock_acquired** event, you can enter **lock**, or **lock acquire**.</span></span>  
  
     <span data-ttu-id="4e3a1-142">選択したイベントが **[選択したイベント]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-142">The events you select appear in the **Selected events** box.</span></span> <span data-ttu-id="4e3a1-143">**[選択したイベント]** ボックスからイベントを削除するには、左矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-143">To remove events from the **Selected events** box, click the left arrow.</span></span>  
  
2.  <span data-ttu-id="4e3a1-144">キャプチャするイベントを選択したら、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-144">After you select the events you want to capture, click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4e3a1-145">**[デバッグ]** チャネルのイベントは、既定では表示されません。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-145">Events from the **Debug** channel are hidden by default.</span></span> <span data-ttu-id="4e3a1-146">デバッグ イベントを表示するには、 **[チャネル]** ボックスの一覧の **[デバッグ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-146">To display debug events, select **Debug** from the **Channel** drop-down list.</span></span>  
  
##  <a name="capture-global-fields"></a><a name="BKMK_CaptureGlobalFields"></a><span data-ttu-id="4e3a1-147">グローバルフィールドのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="4e3a1-147">Capture Global Fields</span></span>  
 <span data-ttu-id="4e3a1-148">グローバル フィールドは "アクション" とも呼ばれ、選択したイベントに対し 1 つまたは複数のアクションを関連付ける目的で使用します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-148">You use global fields (also referred to as actions) to associate single or multiple actions for your selected events.</span></span> <span data-ttu-id="4e3a1-149">**[テンプレートの選択]** ページでテンプレートを選択した場合、そのテンプレートに定義されているすべてのグローバル フィールドがこのページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-149">If you selected a template on the **Choose Template** page, all of the global fields that are defined in the template are displayed on this page.</span></span>  
  
 <span data-ttu-id="4e3a1-150">**[グローバル フィールドのキャプチャ]** ページで、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-150">On the **Capture Global Fields** page, do the following:</span></span>  
  
-   <span data-ttu-id="4e3a1-151">イベント セッションに対してキャプチャするグローバル フィールドを選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-151">Select the global fields that you want to capture for the event session, and then click **Next**.</span></span>  
  
     <span data-ttu-id="4e3a1-152">グローバル フィールドは、その横にあるチェック ボックスをオンまたはオフにすることによって追加したり削除したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-152">You can remove or add global fields by selecting or clearing the check box next to the global field.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4e3a1-153">選択したアクションは **[名前]** で並べ替えられ、関連するアクションがアルファベット順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-153">The selected actions are sorted by **Name** enabling you to view the associated actions in alphabetical order.</span></span> <span data-ttu-id="4e3a1-154">フィールド名の横の列見出しをクリックすると、説明や有効/無効の状態で並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-154">You can sort by description or by the enable/disable status by clicking the column heading next to the field name.</span></span>  
  
##  <a name="set-session-event-filters"></a><a name="BKMK_SetSessionEventFilters"></a><span data-ttu-id="4e3a1-155">セッションイベントフィルターの設定</span><span class="sxs-lookup"><span data-stu-id="4e3a1-155">Set Session Event Filters</span></span>  
 <span data-ttu-id="4e3a1-156">キャプチャするイベントは、フィルターを適用することによって制限することができます。フィルターは "述語" と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-156">You can apply filters (also called predicates) to limit the events that you want to capture.</span></span> <span data-ttu-id="4e3a1-157">**[セッション イベント フィルターの設定]** ページで、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-157">On the **Set Session Event Filters** page, do the following:</span></span>  
  
1.  <span data-ttu-id="4e3a1-158">事前構成済みのテンプレートを使用していない場合は、フィルターの条件を自分で作成し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-158">If you are not using a pre-configured template, create your filter criteria, and then click **Next**.</span></span>  
  
     <span data-ttu-id="4e3a1-159">事前構成済みのテンプレートを使用している場合、 **[テンプレートのフィルター (読み取り専用)]** セクションには、そのテンプレートから作成されたフィルターが新規セッション ウィザードによって一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-159">If you are using a pre-configured template, in the **Filters from template (read-only)** section, the New Session Wizard lists filters already created from the template.</span></span>  
  
2.  <span data-ttu-id="4e3a1-160">**[追加のフィルター]** セクションでは、イベント セッション用に追加のフィルターを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-160">In the **Additional filters** section, you can configure additional filters for the event session.</span></span>  
  
     <span data-ttu-id="4e3a1-161">構成したフィルターは、選択したすべてのイベントに適用されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-161">The filters you configure apply to all selected events.</span></span> <span data-ttu-id="4e3a1-162">新規セッション ウィザードでは、イベントごとにフィルターを構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-162">The New Session Wizard does not support configuring filters for each event.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4e3a1-163">フィルターのグループ句を構成した場合、結果が保存された後で、冗長なかっこがフィルターから削除されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-163">When you configure a group clause for your filter, redundant parentheses are removed from the filter after the result is saved.</span></span> <span data-ttu-id="4e3a1-164">たとえば、 **Clause 1** と **Clause 2**をグループ化するフィルターを作成した場合、これらの句を囲むかっこが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-164">For example, if you create a filter grouping **Clause 1** and **Clause 2**, parentheses will appear around the clauses.</span></span> <span data-ttu-id="4e3a1-165">フィルターを保存すると、冗長なかっこが削除されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-165">After you save the filter, the redundant parentheses are removed.</span></span> <span data-ttu-id="4e3a1-166">かっこを削除しても、フィルターのロジックには影響しません。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-166">The removal of the parentheses does not affect the filter logic.</span></span>  
  
##  <a name="specify-session-data-storage"></a><a name="BKMK_SpecifySessionDataOutput"></a><span data-ttu-id="4e3a1-167">セッションデータストレージの指定</span><span class="sxs-lookup"><span data-stu-id="4e3a1-167">Specify Session Data Storage</span></span>  
 <span data-ttu-id="4e3a1-168">分析に必要なデータの収集方法は、 **[セッション データ ストレージの指定]** ページで指定します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-168">You use the **Specify Session Data Storage** page to specify how you want to collect your data for analysis.</span></span> <span data-ttu-id="4e3a1-169">SQL Server 拡張イベントでは、データの出力に "ターゲット" が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-169">SQL Server Extended Events uses targets for data output.</span></span> <span data-ttu-id="4e3a1-170">ターゲットは、イベント データを格納するほか、ファイルへの書き込み、イベント データの集計などの操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-170">Targets store event data and can perform actions such as writing to a file and aggregating event data.</span></span> <span data-ttu-id="4e3a1-171">分析に必要なデータの収集方法を決め、 **[セッション データ ストレージの指定]** ページで、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-171">Decide how you want to collect your data for analysis, and on the **Specify Session Data Storage** page, do the following:</span></span>  
  
1.  <span data-ttu-id="4e3a1-172">データセットが大きい場合や、履歴レコードを作成する場合は、 **[後で分析を行うためにデータをファイルに保存する]** チェック ボックスをオンにして、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-172">For large data sets and creating historical records, select the **Save data to a file for later analysis** check box, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="4e3a1-173">**[サーバー上のファイル名]** ボックスに、パスとファイル名を入力するか、 **[参照]** をクリックして、データの保存先のサーバー上にあるファイル ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-173">In the **File name on server** box, enter the path and file name, or click **Browse** to specify the file directory on the server where you want to save the data.</span></span>  
  
    2.  <span data-ttu-id="4e3a1-174">**[ファイルの最大サイズ]** ボックスに、ファイル ターゲットに使用するファイルの最大サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-174">In the **Maximum file size** box, specify the maximum file size to be used for the file target.</span></span> <span data-ttu-id="4e3a1-175">ファイルの最大サイズを指定しない場合、ファイルはディスクがいっぱいになるまで拡張されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-175">If you do not specify the maximum file size, the file will grow until the disk is full.</span></span> <span data-ttu-id="4e3a1-176">既定のファイル サイズは 1 GB です。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-176">The default file size is 1 gigabyte (GB).</span></span>  
  
    3.  <span data-ttu-id="4e3a1-177">ファイル ターゲットに対してファイル ロールオーバーを有効にするには、 **[ファイル ロールオーバーを有効にする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-177">Select the **Enable file rollover** check box to enable file rollover for the file target.</span></span>  
  
    4.  <span data-ttu-id="4e3a1-178">ファイル システムに保持する最大ファイル数を **[ファイルの最大数]** ボックスに指定します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-178">In the **Maximum number of files** box, specify the maximum number of files you want to retain in the file system.</span></span>  
  
2.  <span data-ttu-id="4e3a1-179">最新のデータを収集する場合は、 **[最新のデータのみを使用する (ring_buffer ターゲット)]** チェック ボックスをオンにして、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-179">For collecting recent data, select the **Work with only the most recent data (ring buffer target)** check box, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="4e3a1-180">**[保持するイベントの数]** ボックスで、保持するイベントの数を入力するか、上矢印と下矢印を使用して選択します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-180">In the **Number of events to keep** box, enter or select the number of events you want to keep by using the up and down arrows.</span></span>  
  
    2.  <span data-ttu-id="4e3a1-181">**[バッファー メモリの最大サイズ]** ボックスに、使用するバッファー メモリの最大サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-181">In the **Maximum buffer memory size** box, specify the maximum amount of buffer memory to use.</span></span> <span data-ttu-id="4e3a1-182">この値に達すると、既存のイベントが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-182">The existing events are dropped when this value is reached.</span></span>  
  
    3.  <span data-ttu-id="4e3a1-183">種類ごとに特定の数のイベントをバッファーに保持する場合は、 **[バッファーがいっぱいになったときには指定された数のイベント (種類ごと) を保持する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-183">If you want to keep a specific number of events of each type in the buffer, select the **Keep a specified number of events (per type) when the buffer is full** check box.</span></span>  
  
    4.  <span data-ttu-id="4e3a1-184">**[保持するイベントの数 (種類ごと)]** ボックスで、種類ごとに保持するイベントの数を入力するか、上矢印と下矢印を使用して選択します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-184">In the **Number of events to keep (per type)** box, enter or select the number of events (per type) that you want to keep by using the up and down arrows.</span></span>  
  
##  <a name="summary"></a><a name="BKMK_Summary"></a> <span data-ttu-id="4e3a1-185">まとめ</span><span class="sxs-lookup"><span data-stu-id="4e3a1-185">Summary</span></span>  
 <span data-ttu-id="4e3a1-186">**[概要]** ページで、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-186">On the **Summary** page, do the following:</span></span>  
  
1.  <span data-ttu-id="4e3a1-187">選択した内容が正しいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-187">Make sure that your selections are correct.</span></span> <span data-ttu-id="4e3a1-188">イベント セッション ノードを展開し、選択したすべての項目がイベント セッションへの追加対象になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-188">Expand the event session nodes to verify that all of your selections will be included in the event session.</span></span>  
  
2.  <span data-ttu-id="4e3a1-189">**[スクリプト]** をクリックして、新しいクエリ エディター ウィンドウにセッション作成スクリプトをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-189">Click **Script** to export the session creation script to a new Query Editor window.</span></span>  
  
3.  <span data-ttu-id="4e3a1-190">イベント セッションを作成するには、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-190">Click **Finish** to create the event session.</span></span>  
  
##  <a name="create-event-session"></a><a name="BKMK_CreateEventSession"></a><span data-ttu-id="4e3a1-191">イベントセッションの作成</span><span class="sxs-lookup"><span data-stu-id="4e3a1-191">Create Event Session</span></span>  
 <span data-ttu-id="4e3a1-192">イベント セッションが正常に作成されたら、 **[イベント セッションの作成]** ページで次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-192">On the **Create Event Session** page, after your event session has been successfully created, do the following:</span></span>  
  
1.  <span data-ttu-id="4e3a1-193">ウィザードの終了後にセッションを開始するには、 **[セッションの作成後すぐにイベント セッションを開始する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-193">Click **Start the event session immediately after session creation** to start the session after you close the wizard.</span></span> <span data-ttu-id="4e3a1-194">ライブ データを監視するには、セッションの作成後すぐにイベント セッションを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-194">You must start the event session immediately after you create the session to be able to watch live data.</span></span>  
  
2.  <span data-ttu-id="4e3a1-195">イベント セッションのライブ データを表示するには、 **[ライブ データのキャプチャ時に画面でライブ データを監視する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-195">Click **Watch live data on screen as it is captured** to view live data for your event session.</span></span> <span data-ttu-id="4e3a1-196">セッションの作成直後からライブ データにトレース結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e3a1-196">The live data will start displaying tracing immediately after the session is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3a1-197">参照</span><span class="sxs-lookup"><span data-stu-id="4e3a1-197">See Also</span></span>  
 <span data-ttu-id="4e3a1-198">[[新しいセッション] ダイアログを使用した拡張イベント セッションの作成](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)</span><span class="sxs-lookup"><span data-stu-id="4e3a1-198">[Create an Extended Events Session Using the New Session Dialog](../../2014/database-engine/create-an-extended-events-session-using-the-new-session-dialog.md)</span></span>  
  
  
