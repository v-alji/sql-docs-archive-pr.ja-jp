---
title: ナレッジ ベースの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 27f306f4-d67c-47f5-b35c-4260cc5d36e3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cc5fdd87ddb3ea687db10a29d7001564fd8ff107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644649"
---
# <a name="manage-a-knowledge-base"></a><span data-ttu-id="40e94-102">ナレッジ ベースの管理</span><span class="sxs-lookup"><span data-stu-id="40e94-102">Manage a Knowledge Base</span></span>
  <span data-ttu-id="40e94-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のナレッジ ベースに対して管理機能を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40e94-103">This topic describes how to perform management functions on a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="40e94-104">ナレッジ ベースの削除、ロック解除、作業の破棄、名前の変更、およびプロパティの表示を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="40e94-104">You can delete a knowledge base, unlock it, discard your work on it, rename it, and display its properties.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="40e94-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="40e94-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="40e94-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="40e94-106">Prerequisites</span></span>  
 <span data-ttu-id="40e94-107">ナレッジ ベースを管理するには、ナレッジ ベースが既に作成されていて、発行済みであるか (他のユーザーが作成した場合) または閉じられている (自分で作成した場合) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="40e94-107">To manage a knowledge base, the knowledge base must have already been created, and either published (if another person created it) or have been closed (if you created it).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="40e94-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="40e94-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="40e94-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="40e94-109">Permissions</span></span>  
 <span data-ttu-id="40e94-110">ナレッジ ベースを開くには、DQS_MAIN データベースの dqs_kb_editor ロールまたは dqs_administrator ロールを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="40e94-110">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to open a knowledge base.</span></span>  
  
##  <a name="manage-a-knowledge-base"></a><a name="Manage"></a><span data-ttu-id="40e94-111">ナレッジベースの管理</span><span class="sxs-lookup"><span data-stu-id="40e94-111">Manage a Knowledge Base</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="40e94-112">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="40e94-112">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="40e94-113">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[ナレッジ ベースを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40e94-113">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base**.</span></span>  
  
3.  <span data-ttu-id="40e94-114">ナレッジ ベース テーブル内のナレッジ ベースを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="40e94-114">Right-click a knowledge base in the knowledge base table.</span></span>  
  
4.  <span data-ttu-id="40e94-115">コンテキスト メニューでは、以下の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="40e94-115">In the context menu, you can do the following:</span></span>  
  
    1.  <span data-ttu-id="40e94-116">**[開く]**: クリックすると、 **[アクティビティの選択]** ペインで選択したアクティビティでナレッジ ベースが開きます。</span><span class="sxs-lookup"><span data-stu-id="40e94-116">**Open**: Click to open the knowledge base in the activity selected in the **Select Activity** pane.</span></span>  
  
    2.  <span data-ttu-id="40e94-117">**[ロック解除]**: ドメイン管理、ナレッジ検出、およびポリシー照合の各アクティビティのいずれかの手順でナレッジ ベースを操作していて、それを閉じたユーザーである場合は、ナレッジ ベースのロックを解除できます。</span><span class="sxs-lookup"><span data-stu-id="40e94-117">**Unlock**: You can unlock the knowledge base if you are the user who was working on the knowledge base in one of the steps of domain management, knowledge discovery, and the matching policy activity, and closed it.</span></span> <span data-ttu-id="40e94-118">ナレッジ ベースをアンロードすると、別のユーザーがナレッジ ベースを開いて操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40e94-118">If you unload the knowledge base, another person will be able to open it and work on it.</span></span> <span data-ttu-id="40e94-119">このコマンドは、ナレッジ ベースがアクティビティの状態でない場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="40e94-119">This command is not available if the knowledge base is not in a state of an activity.</span></span> <span data-ttu-id="40e94-120">詳細については、「 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40e94-120">For more information, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    3.  <span data-ttu-id="40e94-121">**[作業の破棄]**: ナレッジ ベースが作業中の状態になっている場合にクリックします。ナレッジ ベースの状態は、テーブルの [状態] フィールドのエントリで示されます。</span><span class="sxs-lookup"><span data-stu-id="40e94-121">**Discard work**: Click when the knowledge base is in a state of being worked on, as shown with an entry in the State field in the table.</span></span> <span data-ttu-id="40e94-122">このコマンドは、ナレッジ ベースがアクティビティの状態でない場合、およびナレッジ ベースがロックされている場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="40e94-122">This command is not available if the knowledge base is not in a state of an activity, and it is not available if the knowledge base is locked.</span></span> <span data-ttu-id="40e94-123">詳細については、「 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40e94-123">For more information, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
    4.  <span data-ttu-id="40e94-124">**[名前の変更]**: クリックすると、右クリックしたナレッジ ベースについて、テーブルの [ナレッジ ベース] フィールドが編集可能になります。</span><span class="sxs-lookup"><span data-stu-id="40e94-124">**Rename**: Click to make the Knowledge Base field of the table editable for the knowledge base that you right-clicked on.</span></span> <span data-ttu-id="40e94-125">名前を変更し、そのナレッジ ベースとフィールド内の別のナレッジ ベースをクリックして名前の変更を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="40e94-125">Change the name, and then click on that knowledge base and another one in the field to accept the name change.</span></span>  
  
    5.  <span data-ttu-id="40e94-126">**[削除]**: クリックすると、 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]の DQS_MAIN データベースからナレッジ ベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="40e94-126">**Delete**: Click to remove the knowledge base from the DQS_MAIN database on [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
    6.  <span data-ttu-id="40e94-127">**[プロパティ]**: クリックすると、データベースのプロパティを読み取り専用で表示します。</span><span class="sxs-lookup"><span data-stu-id="40e94-127">**Properties**: Click to display properties for the database in a read-only display.</span></span>  
  
        1.  <span data-ttu-id="40e94-128">**[ソース ナレッジ ベース]**: このデータベースの基になっているナレッジ ベースです。</span><span class="sxs-lookup"><span data-stu-id="40e94-128">**Source Knowledge Base**: the knowledge base that this database was based on.</span></span> <span data-ttu-id="40e94-129">これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="40e94-129">This is optional.</span></span>  
  
        2.  <span data-ttu-id="40e94-130">**[状態]**: ナレッジ ベースの状態が **[作業中]** になっているかどうか、および特定のナレッジ マネージメント アクティビティになっているかどうかを示します。ナレッジ ベースの状態は、ナレッジ ベースが最後に閉じられたときに決定されます。</span><span class="sxs-lookup"><span data-stu-id="40e94-130">**State**: Indicates if the knowledge base is **In Work** and if it is in a specific knowledge management activity, as determined when it was last closed.</span></span> <span data-ttu-id="40e94-131">状態は、 **[作業中]**(ナレッジ ベースはナレッジ マネージメント セッションで開かれていますが、特定のアクティビティになっていません) または **[作業中]** かつナレッジ マネージメント アクティビティ (ナレッジ ベースはナレッジ マネージメント セッションで開かれていて、特定のアクティビティになっています) のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="40e94-131">The state can be **In Work**, in which the knowledge base is opened in a knowledge management session, but not in a specific activity, or **In Work** plus a knowledge management activity, in which the knowledge base is opened in a knowledge management session, and in a specific activity.</span></span>  
  
        3.  <span data-ttu-id="40e94-132">**[ロック]**: ナレッジ ベースがロックされている場合は **[True]** 、ロックされていない場合は **[False]**</span><span class="sxs-lookup"><span data-stu-id="40e94-132">**Is Locked**: **True** if the knowledge base was locked, **False** if not</span></span>  
  
        4.  <span data-ttu-id="40e94-133">**[発行されていないコンテンツを含む]**: ナレッジ ベースが発行によって保存されていないコンテンツを含んでいる場合は [True]、含んでいない場合は [False]</span><span class="sxs-lookup"><span data-stu-id="40e94-133">**Contains unpublished content**: True if the knowledge base contains content that has not been saved by publishing, False if not</span></span>  
  
        5.  <span data-ttu-id="40e94-134">**[ロックしているユーザー]**: ナレッジ ベースを閉じてロックしたユーザーの名前</span><span class="sxs-lookup"><span data-stu-id="40e94-134">**Locked By**: the name of the user who closed the knowledge base, locking it</span></span>  
  
        6.  <span data-ttu-id="40e94-135">**[ロックされた日付]**: ロックされた日付</span><span class="sxs-lookup"><span data-stu-id="40e94-135">**Locked Date**: date when locked</span></span>  
  
        7.  <span data-ttu-id="40e94-136">**[作成者]**: ナレッジ ベースを作成したユーザーの名前とそのユーザーが属しているネットワーク</span><span class="sxs-lookup"><span data-stu-id="40e94-136">**Created By**: the name of the user who created the knowledge base, with the network that he or she belongs to</span></span>  
  
        8.  <span data-ttu-id="40e94-137">**[作成日]**: 作成された日付</span><span class="sxs-lookup"><span data-stu-id="40e94-137">**Created Date**: date when created</span></span>  
  
##  <a name="follow-up-after-managing-a-knowledge-base"></a><a name="FollowUp"></a><span data-ttu-id="40e94-138">補足情報: ナレッジベースを管理した後</span><span class="sxs-lookup"><span data-stu-id="40e94-138">Follow Up: After Managing a Knowledge Base</span></span>  
 <span data-ttu-id="40e94-139">ナレッジ ベースを管理した後の次の手順は、ナレッジ ベースに対して実行したアクションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="40e94-139">After you manage a knowledge base, your next step depends upon the action you took on the knowledge base:</span></span>  
  
-   <span data-ttu-id="40e94-140">ナレッジ ベースを開いた場合は、選択したアクティビティで続行します。</span><span class="sxs-lookup"><span data-stu-id="40e94-140">If you opened the knowledge base, you will continue in the activity that you selected.</span></span>  
  
-   <span data-ttu-id="40e94-141">ナレッジ ベースのロックを解除した場合は、別のユーザーがそのナレッジ ベースを示された状態で開いて作業できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40e94-141">If you unlocked it, it will be available for another person to open and work on, in the state indicated.</span></span>  
  
-   <span data-ttu-id="40e94-142">ナレッジ ベースに対する作業を破棄した場合、ナレッジ ベースは最後に発行された状態で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40e94-142">If you discarded the work on it, the knowledge base will be available in its last published state.</span></span>  
  
-   <span data-ttu-id="40e94-143">ナレッジ ベースの名前を変更した場合は、名前を変更したナレッジ ベースを開いて作業する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40e94-143">If you renamed it, you will have to open the renamed knowledge base to work on it.</span></span>  
  
-   <span data-ttu-id="40e94-144">ナレッジ ベースを削除した場合は、別のナレッジ ベースを選択して作業するか、新しいナレッジ ベースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40e94-144">If you delete it, you will have to select another knowledge base to work on, or create a new one.</span></span>  
  
  
