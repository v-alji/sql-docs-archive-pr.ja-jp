---
title: ナレッジ ベースを開く | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.openkb.f1
ms.assetid: a5f010a5-b762-41c9-881b-bf0c192dca83
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f727a5ab75a60d29c830403892c56c87fc6d4ebf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736786"
---
# <a name="open-a-knowledge-base"></a><span data-ttu-id="30839-102">ナレッジ ベースを開く</span><span class="sxs-lookup"><span data-stu-id="30839-102">Open a Knowledge Base</span></span>
  <span data-ttu-id="30839-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で既存のナレッジ ベースを開き、ドメイン管理、ナレッジ検出、または照合ポリシーの追加の準備を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="30839-103">This topic describes how to open an existing knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), and prepare it for domain management, knowledge discovery, or adding a matching policy.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="30839-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="30839-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="30839-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="30839-105">Prerequisites</span></span>  
 <span data-ttu-id="30839-106">ナレッジ ベースを開くには、ナレッジ ベースが既に作成されていて、発行済みであるか (他のユーザーが作成した場合) または閉じられている (自分で作成した場合) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="30839-106">To open a knowledge base, the knowledge base must have already been created, and either published (if another person created it) or have been closed (if you created it).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="30839-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="30839-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="30839-108">Permissions</span><span class="sxs-lookup"><span data-stu-id="30839-108">Permissions</span></span>  
 <span data-ttu-id="30839-109">ナレッジ ベースを開くには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="30839-109">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to open a knowledge base.</span></span>  
  
##  <a name="open-a-knowledge-base"></a><a name="Open"></a><span data-ttu-id="30839-110">ナレッジベースを開く</span><span class="sxs-lookup"><span data-stu-id="30839-110">Open a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="30839-111">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="30839-111">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="30839-112">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[ナレッジ ベースを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30839-112">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base**.</span></span>  
  
3.  <span data-ttu-id="30839-113">テーブル内のナレッジ ベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="30839-113">Select a knowledge base in the table.</span></span> <span data-ttu-id="30839-114">ナレッジ ベースのドメインと照合ルールがページの右側のペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="30839-114">The domains and matching rules in the knowledge base will be displayed in the right-hand pane of the page.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30839-115">テーブル内のナレッジ ベースを右クリックして、ナレッジ ベースに対する操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="30839-115">You can perform operations on a knowledge base by right-clicking it in the table.</span></span> <span data-ttu-id="30839-116">ナレッジ ベースを開く、別の名前を付けて保存、ロックの解除、変更の破棄、名前の変更、プロパティの表示などの操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="30839-116">You can open the knowledge base, save it with another name, unlock it, discard the work, rename it, or display its properties.</span></span>  
  
4.  <span data-ttu-id="30839-117">**[アクティビティの選択]** で、ナレッジ ベースに対して実行するアクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="30839-117">In **Select Activity**, select the activity that you want to perform on the knowledge base:</span></span>  
  
    -   <span data-ttu-id="30839-118">**[ドメイン管理]** を選択すると、ナレッジ ベースのドメインを変更するための画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="30839-118">Select **Domain Management** to enter the screens that you use to modify the domains in the knowledge base.</span></span>  
  
    -   <span data-ttu-id="30839-119">**[ナレッジ検出]** を選択すると、データ サンプルを分析して結果をナレッジ ベースのドメインに設定するためのウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30839-119">Select **Knowledge Discovery** to enter the wizard that you use to analyze a data sample and populate the domains of the knowledge base with the results.</span></span>  
  
    -   <span data-ttu-id="30839-120">**[照合ポリシー]** を選択すると、照合ポリシーを作成してナレッジ ベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="30839-120">Select **Matching Policy** to create a matching policy and add it to the knowledge base.</span></span>  
  
5.  <span data-ttu-id="30839-121">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30839-121">Click **Open**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30839-122">ナレッジ ベースを右クリックし、[開く] をクリックしてナレッジ ベースを開くこともできます。</span><span class="sxs-lookup"><span data-stu-id="30839-122">You can also open the knowledge base by right-clicking it, and then clicking Open.</span></span> <span data-ttu-id="30839-123">ショートカット メニューの他のコマンドでは、別の名前を付けて保存、ロックの解除、変更の破棄、名前の変更、プロパティの表示などの操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="30839-123">Other commands in the context menu enable you to save it with another name, unlock it, discard the work, rename it, or display its properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="30839-124">ナレッジ ベースがロックされていて開くことができない場合は、以下のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="30839-124">If you cannot open the knowledge base because it is locked, see the section below.</span></span>  
  
## <a name="open-a-recent-knowledge-base"></a><span data-ttu-id="30839-125">最近使用したナレッジ ベースを開く</span><span class="sxs-lookup"><span data-stu-id="30839-125">Open a Recent Knowledge Base</span></span>  
 <span data-ttu-id="30839-126">最近開いた 5 つのナレッジ ベースが DQS ホーム ページの **[最近使用したナレッジ ベース]** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="30839-126">The five most recently opened knowledge bases are displayed in the **Recent Knowledge Base** list in the DQS home page.</span></span> <span data-ttu-id="30839-127">これにより **[ナレッジ ベースを開く]** ページを経由せずに最近使用したナレッジ ベースを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="30839-127">This enables you to open a knowledge base that you recently worked on without going through the **Open Knowledge Base** page.</span></span>  
  
-   <span data-ttu-id="30839-128">[最近使用したナレッジ ベース] のロックされていないナレッジ ベースを開くには、ナレッジ ベースの右矢印をクリックし、ナレッジ ベースで開くアクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="30839-128">To open a knowledge base in the Recent list that is not locked, click the right arrow for the knowledge base, and then select the activity that you want to open the knowledge base in.</span></span>  
  
-   <span data-ttu-id="30839-129">[最近使用したナレッジ ベース] の自分でロックしたナレッジ ベースを開くには、ナレッジ ベースをクリックします。ナレッジ ベースがアクティビティで開き、ページがかっこの中に表示されます。</span><span class="sxs-lookup"><span data-stu-id="30839-129">To open a knowledge base in the Recent list that you locked, click the knowledge base and it will open in the activity and page indicated in parentheses.</span></span>  
  
-   <span data-ttu-id="30839-130">[最近使用したナレッジ ベース] の他のユーザーにロックされたナレッジ ベースを開くには、そのユーザーにナレッジ ベースのロック解除を依頼します。</span><span class="sxs-lookup"><span data-stu-id="30839-130">To open a knowledge base in the Recent list that has been locked by someone else, contact that person and have them unlock the knowledge base.</span></span>  
  
##  <a name="follow-up-after-opening-a-knowledge-base"></a><a name="FollowUp"></a><span data-ttu-id="30839-131">補足情報: ナレッジベースを開いた後</span><span class="sxs-lookup"><span data-stu-id="30839-131">Follow Up: After Opening a Knowledge Base</span></span>  
 <span data-ttu-id="30839-132">ナレッジ ベースを開くと、ナレッジ ベースはナレッジ ベース テーブルの [状態] 列に示される状態になります。</span><span class="sxs-lookup"><span data-stu-id="30839-132">After you open a knowledge base, the knowledge base is put into the state indicated in the State column of the Knowledge Base table.</span></span> <span data-ttu-id="30839-133">ナレッジ検出およびポリシー照合のアクティビティでは、ナレッジ ベースは特定のウィザード ページで開かれます。</span><span class="sxs-lookup"><span data-stu-id="30839-133">For the knowledge discovery and matching policy activities, the knowledge base will be opened in a specific wizard page.</span></span> <span data-ttu-id="30839-134">ドメイン管理アクティビティでは、ナレッジ ベースはドメイン管理ページで開かれます。</span><span class="sxs-lookup"><span data-stu-id="30839-134">For the domain management activity, the knowledge base will be opened in the domain management page.</span></span> <span data-ttu-id="30839-135">状態について詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、または「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="30839-135">For more information about the states, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="if-the-knowledge-base-is-locked"></a><a name="Locked"></a><span data-ttu-id="30839-136">ナレッジベースがロックされている場合</span><span class="sxs-lookup"><span data-stu-id="30839-136">If the knowledge base is locked</span></span>  
 <span data-ttu-id="30839-137">最初の列のロック アイコンは、ナレッジ ベースがロックされているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="30839-137">The lock icon in the first column shows whether the knowledge base is locked.</span></span> <span data-ttu-id="30839-138">ロックされたナレッジ ベースの名前は、赤いフォントで表示されます。</span><span class="sxs-lookup"><span data-stu-id="30839-138">The name of a locked knowledge base will be in red font.</span></span> <span data-ttu-id="30839-139">特定ユーザーによるナレッジ ベースのアクティビティによって変更中のナレッジ ベースは、[ロック済み] としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="30839-139">A knowledge base that is being modified by a specific user through a knowledge base activity is marked as Locked.</span></span> <span data-ttu-id="30839-140">ロックされているナレッジ ベースを他のユーザーが操作することはできません。</span><span class="sxs-lookup"><span data-stu-id="30839-140">A locked knowledge base cannot be worked on by a second user.</span></span> <span data-ttu-id="30839-141">ナレッジ ベースを操作しているユーザーは、[ナレッジ ベースを開く] ページのテーブル内でナレッジ ベースを右クリックし、 **[ロック解除]** をクリックするか、発行することにより、ロックを解除できます。</span><span class="sxs-lookup"><span data-stu-id="30839-141">The user who is working on the knowledge base can unlock it by right-clicking the knowledge base in the table on the Open Knowledge Base page, and clicking **Unlock**, or by publishing it.</span></span> <span data-ttu-id="30839-142">DQS では、ロックされたナレッジ ベースにカーソルが置かれているときに、そのナレッジ ベースをロックしたユーザーとロックした時間を示すヒントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30839-142">When the cursor is positioned on a locked knowledge base, DQS will display a hint showing who locked the knowledge base and when they locked it.</span></span>  
  
##  <a name="state-of-a-knowledge-base"></a><a name="State"></a><span data-ttu-id="30839-143">ナレッジベースの状態</span><span class="sxs-lookup"><span data-stu-id="30839-143">State of a Knowledge Base</span></span>  
 <span data-ttu-id="30839-144">[状態] フィールドは、ナレッジ ベースがアクティビティのどのステージにあるのかを示します。</span><span class="sxs-lookup"><span data-stu-id="30839-144">The State field indicates which stage of an activity the knowledge base is at.</span></span> <span data-ttu-id="30839-145">ナレッジ ベースを開くと、そのステージで開かれます。</span><span class="sxs-lookup"><span data-stu-id="30839-145">If you open the knowledge base, it will open to that stage.</span></span>  
  
-   <span data-ttu-id="30839-146">**\<Empty>**: ナレッジベースが発行されている場合は、ナレッジベースの [状態] フィールドが空になります。これには、ドメイン管理アクティビティの [**発行**] をクリックし、[**はい-ナレッジベースを発行して終了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="30839-146">**\<Empty>**: The State field is empty for a knowledge base if the knowledge base has been published by clicking **Publish** in the Domain Management activity, and clicking **Yes - Publish the knowledge base and exit**.</span></span>  
  
-   <span data-ttu-id="30839-147">**作業中**: ナレッジベースの作業は、ドメイン管理アクティビティの [**発行**] をクリックし、[**いいえ-作業内容をナレッジベースに保存**して終了] をクリックして保存されています。</span><span class="sxs-lookup"><span data-stu-id="30839-147">**In Work**: Work on the knowledge base has been saved by clicking **Publish** in the Domain Management activity, and clicking **No - Save the work on the knowledge base and exit**.</span></span>  
  
-   <span data-ttu-id="30839-148">**[ドメイン管理]**: ナレッジ ベースのドメインに対してデータが入力されましたが、ナレッジ ベースはまだ発行されていないため、作業内容はドメイン管理アクティビティに含まれたままです。</span><span class="sxs-lookup"><span data-stu-id="30839-148">**Domain Management**: Data has been entered for a domain in the knowledge base, but the knowledge base has not been published and the work remains in the Domain Management activity.</span></span> <span data-ttu-id="30839-149">ナレッジ検出アクティビティは使用できません。</span><span class="sxs-lookup"><span data-stu-id="30839-149">The Knowledge Discovery activity is not available.</span></span> <span data-ttu-id="30839-150">**[ドメイン管理]** 画面で **[閉じる]** をクリックした場合にこの状態になります。</span><span class="sxs-lookup"><span data-stu-id="30839-150">This occurs when you click **Close** in the **Domain Management** screen.</span></span>  
  
-   <span data-ttu-id="30839-151">**[検出 - マッピング]**: ナレッジ ベースは **[ナレッジ ベース管理: マッピング]** ページで閉じられました。</span><span class="sxs-lookup"><span data-stu-id="30839-151">**Discovery - Mapping**: The knowledge base was closed on the **Knowledge Base Management: Mapping** page.</span></span> <span data-ttu-id="30839-152">ナレッジ ベースがロックされていて、ドメイン管理アクティビティおよび照合アクティビティを使用できません。</span><span class="sxs-lookup"><span data-stu-id="30839-152">The knowledge base is locked, and the Domain Management and Matching activities are not available.</span></span>  
  
-   <span data-ttu-id="30839-153">**[検出 - 検出]**: ナレッジ ベースは **[ナレッジ ベース管理: 分析]** ページで閉じられました。</span><span class="sxs-lookup"><span data-stu-id="30839-153">**Discovery - Discover**: The knowledge base was closed on the **Knowledge Base Management: Analyze** page.</span></span> <span data-ttu-id="30839-154">ナレッジ ベースがロックされていて、ドメイン管理アクティビティを使用できません。</span><span class="sxs-lookup"><span data-stu-id="30839-154">The knowledge base is locked, and The Domain Management activity is not available.</span></span>  
  
-   <span data-ttu-id="30839-155">[**検出-値の管理**]: ナレッジベースは [**ナレッジベース管理: ドメイン用語の管理**] ページで閉じられました。</span><span class="sxs-lookup"><span data-stu-id="30839-155">**Discovery - Value Management**: The knowledge base was closed on the **Knowledge Base Management: Manage Domain Terms** page.</span></span> <span data-ttu-id="30839-156">ナレッジ ベースがロックされていて、ドメイン管理アクティビティを使用できません。</span><span class="sxs-lookup"><span data-stu-id="30839-156">The knowledge base is locked, and the Domain Management activity is not available.</span></span>  
  
-   <span data-ttu-id="30839-157">**ポリシー**照合ポリシーの照合: ナレッジベースは [ポリシーの照合 **-** ポリシーの照合] ページで閉じられました。</span><span class="sxs-lookup"><span data-stu-id="30839-157">**Matching Policy - Matching Policy**: The knowledge base was closed on the **Matching Policy - Matching Policy** page.</span></span> <span data-ttu-id="30839-158">ナレッジ ベースがロックされていて、ナレッジ検出アクティビティおよびドメイン管理アクティビティを使用できません。</span><span class="sxs-lookup"><span data-stu-id="30839-158">The knowledge base is locked, and the Knowledge Discovery and Domain Management activities are not available.</span></span>  
  
-   <span data-ttu-id="30839-159">**ポリシー照合結果の照合**: ナレッジベースは [ポリシーの照合**結果**] ページで閉じられました。</span><span class="sxs-lookup"><span data-stu-id="30839-159">**Matching Policy - Matching Results**: The knowledge base was closed on the **Matching Policy - Matching Results** page.</span></span> <span data-ttu-id="30839-160">ナレッジ ベースがロックされていて、ナレッジ検出アクティビティおよびドメイン管理アクティビティを使用できません。</span><span class="sxs-lookup"><span data-stu-id="30839-160">The knowledge base is locked, and the Knowledge Discovery and Domain Management activities are not available.</span></span>  
  
  
