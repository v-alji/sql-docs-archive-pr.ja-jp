---
title: 手順 2:ログ機能の追加と設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0f2cdce6f34a19e22830d357d20f5d99cff8c14f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715562"
---
# <a name="step-2-adding-and-configuring-logging"></a><span data-ttu-id="c0058-102">手順 2:ログ機能の追加と設定</span><span class="sxs-lookup"><span data-stu-id="c0058-102">Step 2: Adding and Configuring Logging</span></span>
  <span data-ttu-id="c0058-103">ここでは、Lesson 3.dtsx パッケージのデータ フローのログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c0058-103">In this task, you will enable logging for the data flow in the Lesson 3.dtsx package.</span></span> <span data-ttu-id="c0058-104">次に、PipelineExecutionPlan イベントと PipelineExecuteTrees イベントを記録するテキスト ファイル ログ プロバイダーを構成します。</span><span class="sxs-lookup"><span data-stu-id="c0058-104">Then, you will configure a Text File log provider to log the PipelineExecutionPlan and PipelineExecuteTrees events.</span></span> <span data-ttu-id="c0058-105">テキスト ファイル ログ プロバイダーは、表示や移行が容易なログを作成します。</span><span class="sxs-lookup"><span data-stu-id="c0058-105">The Text Files log provider creates logs that are easy to view and easily transportable.</span></span> <span data-ttu-id="c0058-106">パッケージの基本テスト段階では、この簡潔なログ ファイルは特に便利です。</span><span class="sxs-lookup"><span data-stu-id="c0058-106">The simplicity of these log files makes these files especially useful during the basic testing phase of a package.</span></span> <span data-ttu-id="c0058-107">ログ エントリは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの [ログ イベント] ウィンドウでも確認できます。</span><span class="sxs-lookup"><span data-stu-id="c0058-107">You can also view the log entries in the Log Events window of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
### <a name="to-add-logging-to-the-package"></a><span data-ttu-id="c0058-108">パッケージにログ機能を追加するには</span><span class="sxs-lookup"><span data-stu-id="c0058-108">To add logging to the package</span></span>  
  
1.  <span data-ttu-id="c0058-109">次に、 **[SSIS]** メニューの **[ログ記録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0058-109">On the **SSIS** menu, click **Logging**.</span></span>  
  
2.  <span data-ttu-id="c0058-110">**[SSIS ログの構成]** ダイアログ ボックスの **[コンテナー]** ペインで、一番上のパッケージ オブジェクト (Lesson 3) が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c0058-110">In the **Configure SSIS Logs** dialog box, in the **Containers** pane, make sure that the topmost object, which represents the Lesson 3 package, is selected.</span></span>  
  
3.  <span data-ttu-id="c0058-111">**[プロバイダーとログ]** タブで、 **[プロバイダーの種類]** ボックスの一覧から **[テキスト ファイルの SSIS ログ プロバイダー]** を選択し、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0058-111">On the **Providers and Logs** tab, in the **Provider type** box, select **SSIS log provider for Text files**, and then click **Add**.</span></span>  
  
     <span data-ttu-id="c0058-112">新しいテキストファイルログプロバイダーをパッケージに追加します。既定の名前は、[**テキストファイルの SSIS ログプロバイダー**] です。 Integration Services</span><span class="sxs-lookup"><span data-stu-id="c0058-112">Integration Services adds a new Text File log provider to the package with the default name **SSIS log provider for text files**.</span></span> <span data-ttu-id="c0058-113">次に、この新しいログ プロバイダーを構成します。</span><span class="sxs-lookup"><span data-stu-id="c0058-113">You can now configure the new log provider.</span></span>  
  
4.  <span data-ttu-id="c0058-114">[**名前**] 列に「」と入力 `Lesson 3 Log File` します。</span><span class="sxs-lookup"><span data-stu-id="c0058-114">In the **Name** column, type `Lesson 3 Log File`.</span></span>  
  
5.  <span data-ttu-id="c0058-115">必要に応じて、 **[説明]** の内容を修正します。</span><span class="sxs-lookup"><span data-stu-id="c0058-115">Optionally, modify the **Description**.</span></span>  
  
6.  <span data-ttu-id="c0058-116">**[構成]** 列で **\<New Connection>** をクリックし、ログ情報を書き込む場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="c0058-116">In the **Configuration** column, click **\<New Connection>** to specify the destination to which the log information is written.</span></span>  
  
     <span data-ttu-id="c0058-117">**[ファイル接続マネージャー エディター]** ダイアログ ボックスで、 **[使用法の種類]** ボックスの一覧から **[ファイルの作成]** を選択し、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0058-117">In the **File Connection Manager Editor** dialog box, for **Usage type**, select **Create file**, and then click **Browse**.</span></span> <span data-ttu-id="c0058-118">既定では、 **[ファイルの選択]** ダイアログ ボックスにこのプロジェクトのフォルダーが表示されますが、ログ情報を別の場所に保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="c0058-118">By default, the **Select File** dialog box opens the project folder, but you can save log information to any location.</span></span>  
  
7.  <span data-ttu-id="c0058-119">[**ファイルの選択**] ダイアログボックスの [**ファイル名**] ボックスに、「」と入力し、 `TutorialLog.log` [**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0058-119">In the **Select File** dialog box, in the **File name** box type `TutorialLog.log`, and click **Open**.</span></span>  
  
8.  <span data-ttu-id="c0058-120">**[OK]** をクリックして、 **[ファイル接続マネージャー エディター]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c0058-120">Click **OK** to close the **File Connection Manager Editor** dialog box.</span></span>  
  
9. <span data-ttu-id="c0058-121">**[コンテナー]** ペインで、パッケージ コンテナー階層のすべてのノードを展開します。次に、 **[Extract Sample Currency Data]** チェック ボックスも含めすべてのチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="c0058-121">In the **Containers** pane, expand all nodes of the package container hierarchy, and then clear all check boxes, including the **Extract Sample Currency Data** check box.</span></span> <span data-ttu-id="c0058-122">次に、このノードのイベントのみを取得するため、 **[Extract Sample Currency Data]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c0058-122">Now select the check box for **Extract Sample Currency Data** to get only the events for this node.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="c0058-123">**[Extract Sample Currency Data]** チェック ボックスがオフの状態で淡色表示になっている場合は、親コンテナーのログ設定が使用され、この作業用にログ イベントを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c0058-123">If the state of the **Extract Sample Currency Data** check box is dimmed instead of selected, the task uses the log settings of the parent container and you cannot enable the log events that are specific to the task.</span></span>  
  
10. <span data-ttu-id="c0058-124">**[詳細]** タブの **[イベント]** 列で、 **[PipelineExecutionPlan]** イベントと **[PipelineExecutionTrees]** イベントのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c0058-124">On the **Details** tab, in the **Events** column, select the **PipelineExecutionPlan** and **PipelineExecutionTrees** events.</span></span>  
  
11. <span data-ttu-id="c0058-125">**[詳細設定]** をクリックし、各イベントについて書き込まれるログ情報の詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="c0058-125">Click **Advanced** to review the details that the log provider will write to the log for each event.</span></span> <span data-ttu-id="c0058-126">既定では、指定したイベントについて、すべての情報カテゴリが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="c0058-126">By default, all information categories are automatically selected for the events you specify.</span></span>  
  
12. <span data-ttu-id="c0058-127">**[標準]** をクリックして、情報カテゴリを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="c0058-127">Click **Basic** to hide the information categories.</span></span>  
  
13. <span data-ttu-id="c0058-128">[**プロバイダーとログ**] タブの [**名前**] 列で、[] を選択し `Lesson 3 Log File` ます。</span><span class="sxs-lookup"><span data-stu-id="c0058-128">On the **Provider and Logs** tab, in the **Name** column, select `Lesson 3 Log File`.</span></span> <span data-ttu-id="c0058-129">目的のパッケージのログ プロバイダーを作成したら、必要に応じてログの記録を一時的にオフにすることができます。ログ プロバイダーを削除したり、再作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c0058-129">Once you have created a log provider for your package, you can optionally deselect it to temporarily turn off logging, without having to delete and re-create a log provider.</span></span>  
  
14. <span data-ttu-id="c0058-130">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0058-130">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c0058-131">次の手順</span><span class="sxs-lookup"><span data-stu-id="c0058-131">Next Steps</span></span>  
 [<span data-ttu-id="c0058-132">手順 3:レッスン 3 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="c0058-132">Step 3: Testing the Lesson 3 Tutorial Package</span></span>](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
  
