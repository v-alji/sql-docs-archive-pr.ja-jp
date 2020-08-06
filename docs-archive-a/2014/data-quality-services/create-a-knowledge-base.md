---
title: ナレッジ ベースの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.selectkb.f1
- sql12.dqs.kb.newkb.f1
ms.assetid: 2733a284-975f-4650-abcc-cc2aad074cab
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 281fa663362cc4462cd4e32839c1eaf6908394e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632724"
---
# <a name="create-a-knowledge-base"></a><span data-ttu-id="a097b-102">ナレッジ ベースの作成</span><span class="sxs-lookup"><span data-stu-id="a097b-102">Create a Knowledge Base</span></span>
  <span data-ttu-id="a097b-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) でナレッジ ベースを作成し、ドメイン管理、ナレッジ検出、または照合ポリシーの追加の準備を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a097b-103">This topic describes how to create a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS), and prepare it for domain management, knowledge discovery, or adding a matching policy.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a097b-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="a097b-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a097b-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="a097b-105">Prerequisites</span></span>  
 <span data-ttu-id="a097b-106">ナレッジ ベースを作成するには、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] と [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]をインストールしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a097b-106">To create a knowledge base, you must have installed [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a097b-107">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a097b-107">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a097b-108">Permissions</span><span class="sxs-lookup"><span data-stu-id="a097b-108">Permissions</span></span>  
 <span data-ttu-id="a097b-109">ナレッジ ベースを作成するには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="a097b-109">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a knowledge base.</span></span>  
  
##  <a name="create-a-knowledge-base"></a><a name="Createaknowledgebase"></a><span data-ttu-id="a097b-110">ナレッジベースの作成</span><span class="sxs-lookup"><span data-stu-id="a097b-110">Create a knowledge base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="a097b-111">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="a097b-111">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="a097b-112">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[新しいナレッジ ベース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a097b-112">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **New knowledge base**.</span></span>  
  
3.  <span data-ttu-id="a097b-113">新しいナレッジ ベースの名前と説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="a097b-113">Enter a name and description for the new knowledge base.</span></span>  
  
4.  <span data-ttu-id="a097b-114">**[次の場所からナレッジ ベースを作成]** で、ナレッジ ベースを作成する際に基にするナレッジ ベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="a097b-114">In **Create knowledge base from**, select what to base the knowledge base on:</span></span>  
  
    -   <span data-ttu-id="a097b-115">新しいナレッジ ベースを作成する際に既存のナレッジ ベースまたはデータ ファイルを基にしない場合は、 **[なし]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a097b-115">Select **None** if you do not want to base the new knowledge base on an existing knowledge base or data file.</span></span>  
  
    -   <span data-ttu-id="a097b-116">新しいナレッジ ベースを作成する際に、 **で既に作成されているナレッジ ベースまたは既定のナレッジ ベースを基にする場合は、** [既存のナレッジ ベース] [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]を選択します。</span><span class="sxs-lookup"><span data-stu-id="a097b-116">Select **Existing Knowledge Base** to base the new knowledge base on a knowledge base that has already been created on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], or on the default knowledge base.</span></span> <span data-ttu-id="a097b-117">**[ナレッジ ベースの選択]** ボックスの一覧でナレッジ ベースを選択するか、 **[参照]** をクリックして **[ナレッジ ベースの選択]** ダイアログ ボックスを表示し、新しいナレッジ ベースを作成する際に基にする既存のナレッジ ベースを選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a097b-117">Select the knowledge base from the **Select Knowledge Base** drop-down list, or click **Browse** to display the **Select a Knowledge Base** dialog box, select an existing knowledge base to base the new knowledge base on, and then click **OK**.</span></span> <span data-ttu-id="a097b-118">ナレッジ ベースをタブレットから選択する場合は、ナレッジ ベースのドメインと照合ルールがダイアログ ボックスの右側のペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a097b-118">When you select a knowledge base from the tablet, the domains and matching rules in the knowledge base will be displayed in the right-hand pane of the dialog box.</span></span> <span data-ttu-id="a097b-119">**[DQS データ]** ナレッジ ベースを選択することもできます。これは、米国の企業、住所、および関係者のデータに関連する、追加設定なしで使用できる一般的なドメインおよびナレッジを含む既定のナレッジ ベースです。</span><span class="sxs-lookup"><span data-stu-id="a097b-119">You can also select the **DQS Data** knowledge base, which is the default knowledge base that contains common out-of-the-box domains and knowledge related to U.S. company, address, and party data.</span></span>  
  
    -   <span data-ttu-id="a097b-120">新しいナレッジ ベースを作成する際に **の DQS ファイルを基にする場合は、** [DQS ファイルからインポート] [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]を選択します。</span><span class="sxs-lookup"><span data-stu-id="a097b-120">Select **Import from DQS File** to base the new knowledge base on a DQS file on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span> <span data-ttu-id="a097b-121">**[参照]** をクリックし、拡張子が .dqs の DQS データ ファイルを選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a097b-121">Click **Browse**, select a DQS data file with an extension of .dqs, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="a097b-122">**[アクティビティの選択]** で、新しいナレッジ ベースに対して実行するアクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="a097b-122">In **Select Activity**, select the activity that you want to perform on the new knowledge base:</span></span>  
  
    -   <span data-ttu-id="a097b-123">**[ドメイン管理]** を選択すると、ナレッジ ベースが作成され、ナレッジ ベースのドメインを変更するための画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a097b-123">Select **Domain Management** to create the knowledge base and enter the screens that you use to modify the domains in the knowledge base.</span></span>  
  
    -   <span data-ttu-id="a097b-124">**[ナレッジ検出]** を選択すると、ナレッジ ベースが作成され、データ サンプルを分析して結果をナレッジ ベースのドメインに設定するためのウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a097b-124">Select **Knowledge Discovery** to create the knowledge base and enter the wizard that you use to analyze a data sample and populate the domains of the knowledge base with the results.</span></span>  
  
    -   <span data-ttu-id="a097b-125">**[照合ポリシー]** を選択すると、照合ポリシーを作成してナレッジ ベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="a097b-125">Select **Matching Policy** to create a matching policy and add it to the knowledge base.</span></span>  
  
6.  <span data-ttu-id="a097b-126">**Create** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="a097b-126">Click **Create**.</span></span>  
  
##  <a name="follow-up-after-creating-a-knowledge-base"></a><a name="FollowUp"></a><span data-ttu-id="a097b-127">補足情報: ナレッジベースを作成した後</span><span class="sxs-lookup"><span data-stu-id="a097b-127">Follow Up: After Creating a Knowledge Base</span></span>  
 <span data-ttu-id="a097b-128">ナレッジ ベースを作成した後は、ナレッジ検出を実行するためのウィザード、照合ポリシーを作成するためのウィザード、またはドメイン管理を実行するためのページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a097b-128">After you create a knowledge base, you are presented with a wizard that you can use to perform knowledge discovery, a wizard to create a matching policy, or pages to perform domain management.</span></span> <span data-ttu-id="a097b-129">ナレッジ検出、ドメイン管理、または照合ポリシーについて詳しくは、「[ナレッジ検出の実行](../../2014/data-quality-services/perform-knowledge-discovery.md)」、「[ドメインの管理](../../2014/data-quality-services/managing-a-domain.md)」、または「[照合ポリシーの作成](../../2014/data-quality-services/create-a-matching-policy.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a097b-129">For more information about the knowledge discovery, domain management, or matching policy, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
