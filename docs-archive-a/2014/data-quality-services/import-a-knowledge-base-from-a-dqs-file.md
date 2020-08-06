---
title: .dqs ファイルからのナレッジ ベースのインポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 9b9786fe-9e80-429a-afcb-dc3b3dd6f0b0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 522c5f6d8f962cef77e215c21133927e8da4d04f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716882"
---
# <a name="import-a-knowledge-base-from-a-dqs-file"></a><span data-ttu-id="ac6c3-102">.dqs ファイルからのナレッジ ベースのインポート</span><span class="sxs-lookup"><span data-stu-id="ac6c3-102">Import a Knowledge Base from a .dqs File</span></span>
  <span data-ttu-id="ac6c3-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) で .dqs データ ファイルからナレッジ ベース全体をインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-103">This topic describes how to import an entire knowledge base from a .dqs data file in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="ac6c3-104">データ ファイルは、既存のナレッジ ベースを [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションでエクスポートすることによって作成します (「 [ナレッジ ベースを .dqs ファイルにエクスポート](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-104">You create the data file by exporting an existing knowledge base from within the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application (see [Export a Knowledge Base to a .dqs File](../../2014/data-quality-services/export-a-knowledge-base-to-a-dqs-file.md)).</span></span>  
  
 <span data-ttu-id="ac6c3-105">.dqs データ ファイルを使用してナレッジ ベースのコンテンツをエクスポートし、後でそのコンテンツを同じ [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] の別のナレッジ ベースや異なる [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] にインポートすることで、ナレッジの生成処理を簡略化し、時間と労力を節約します。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-105">Using a .dqs data file to export the contents of a knowledge base and then import the contents into another knowledge base on the same [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] or a different [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] simplifies the knowledge generation process, saving time and effort.</span></span> <span data-ttu-id="ac6c3-106">ナレッジ ベースやその中のナレッジを他のユーザーと共有でき、他のユーザーの時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-106">It enables you to share a knowledge base and its knowledge with others, saving them time.</span></span> <span data-ttu-id="ac6c3-107">.dqs ファイルには、ドメインや照合ポリシーを含むナレッジ ベースのすべての情報が含まれます。ただし、アタッチされた参照データ情報は含まれません。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-107">The .dqs file will contain all knowledge base information, including domains and the matching policy, except for the attached reference data information.</span></span> <span data-ttu-id="ac6c3-108">発行済みのデータと発行されていないデータがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-108">Published and unpublished data will be imported.</span></span>  
  
 <span data-ttu-id="ac6c3-109">.dqs データ ファイルは、表示できないように暗号化されています。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-109">A .dqs data file is encrypted, so cannot be viewed.</span></span>  
  
 <span data-ttu-id="ac6c3-110">ナレッジ ベースをインポートする際に同じ名前を使用できますが、クライアント アプリケーションにそのナレッジ ベースの名前が既に存在する場合は名前を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-110">When you import a knowledge base, you can use the same name, unless the knowledge base name already exists in the client application, in which case you must rename it.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ac6c3-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="ac6c3-111">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="ac6c3-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="ac6c3-112">Prerequisites</span></span>  
 <span data-ttu-id="ac6c3-113">ナレッジ ベースを .dqs ファイルからインポートするには、事前にナッレジ ベースを .dqs ファイルにエクスポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-113">To import a knowledge base from a .dqs file, you must have already exported the knowledge base into the .dqs file.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="ac6c3-114">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ac6c3-114">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="ac6c3-115">Permissions</span><span class="sxs-lookup"><span data-stu-id="ac6c3-115">Permissions</span></span>  
 <span data-ttu-id="ac6c3-116">ナレッジ ベースを .dqs データ ファイルからインポートするには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-116">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to import a knowledge base from a .dqs data file.</span></span>  
  
##  <a name="import-a-knowledge-base-from-a-dqs-file"></a><a name="Import"></a><span data-ttu-id="ac6c3-117">Dqs ファイルからナレッジベースをインポートする</span><span class="sxs-lookup"><span data-stu-id="ac6c3-117">Import a knowledge base from a .dqs file</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="ac6c3-118">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-118">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="ac6c3-119">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[新しいナレッジ ベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-119">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="ac6c3-120">ナレッジ ベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-120">Enter a name for the knowledge base.</span></span>  
  
4.  <span data-ttu-id="ac6c3-121">**[次の場所からナレッジ ベースを作成]** の下矢印をクリックし、 **[DQS ファイルからインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-121">Click the down arrow for **Create knowledge base from**, and then select **Import from DQS file**.</span></span>  
  
5.  <span data-ttu-id="ac6c3-122">**[データ ファイルの選択]** で **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-122">For **Select data file**, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="ac6c3-123">**[データ ファイルからインポート]** ダイアログ ボックスで、インポートする .dqs ファイルを含むフォルダーに移動してファイル名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-123">In the **Import from Data File** dialog box, move to the folder that contains the .dqs file that you want to import, and then click the name of the file.</span></span> <span data-ttu-id="ac6c3-124">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-124">Click **Open**.</span></span>  
  
7.  <span data-ttu-id="ac6c3-125">正しいナレッジ ベースとドメインが **[ドメイン]** リストに表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-125">Verify that the correct knowledge base and domains are displayed in the **Domain** list.</span></span>  
  
8.  <span data-ttu-id="ac6c3-126">実行するアクティビティを選択して **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-126">Select the activity that you want to perform, and then click **Create**.</span></span>  
  
9. <span data-ttu-id="ac6c3-127">**[ナレッジ ベースのインポート]** ダイアログ ボックスで、ステータス行にインポートの完了が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-127">In the **Import Knowledge Base** dialog box, verify that the status line indicates that the import completed.</span></span> <span data-ttu-id="ac6c3-128">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-128">Click **OK**.</span></span>  
  
10. <span data-ttu-id="ac6c3-129">必要なナレッジ検出、ドメイン管理、または照合ポリシー タスクを実行し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-129">Complete the knowledge discovery, domain management, or matching policy tasks that you need to perform, and then click **Finish**.</span></span>  
  
11. <span data-ttu-id="ac6c3-130">ナレッジ ベースのナレッジを発行する場合は **[発行]** をクリックし、発行しない場合は **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-130">Click **Publish** to publish the knowledge in the knowledge base, or **No** not to.</span></span>  
  
12. <span data-ttu-id="ac6c3-131">ナレッジ ベースを発行した場合は **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-131">If you published the knowledge base, click **OK**.</span></span>  
  
13. <span data-ttu-id="ac6c3-132">Data Quality Services のホーム ページで、 **[最近使用したナレッジ ベース]** の下にナレッジ ベースが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-132">In the Data Quality Services home page, verify that the knowledge base is listed under **Recent knowledge bases**.</span></span>  
  
##  <a name="follow-up-after-importing-a-knowledge-base-from-a-dqs-file"></a><a name="FollowUp"></a> <span data-ttu-id="ac6c3-133">補足情報: .dqs ファイルからナレッジ ベースをインポートした後</span><span class="sxs-lookup"><span data-stu-id="ac6c3-133">Follow Up: After Importing a Knowledge Base from a .dqs File</span></span>  
 <span data-ttu-id="ac6c3-134">.dqs ファイルからナレッジ ベースをインポートした後で、ナレッジ ベースのコンテンツに応じてナレッジをナレッジ ベースに追加したり、ナレッジ ベースをクレンジング プロジェクトや照合プロジェクトで使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-134">After you import a knowledge base from a .dqs file, you can add knowledge to the knowledge base or use the knowledge base in a cleansing or matching project, depending on the contents of the knowledge base.</span></span> <span data-ttu-id="ac6c3-135">詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、「[複合ドメインの管理](../../2014/data-quality-services/managing-a-composite-domain.md)」、「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」、「[データ クレンジング](../../2014/data-quality-services/data-cleansing.md)」、または「[データ照合](../../2014/data-quality-services/data-matching.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ac6c3-135">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), [Managing a Composite Domain](../../2014/data-quality-services/managing-a-composite-domain.md), [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md), [Data Cleansing](../../2014/data-quality-services/data-cleansing.md), or [Data Matching](../../2014/data-quality-services/data-matching.md).</span></span>  
  
  
