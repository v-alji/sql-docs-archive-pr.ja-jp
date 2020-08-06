---
title: データベース ミラーリング セッションの手動フェールオーバー (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 4ecf9c63-b3a4-4c54-b553-5bc37973232b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7f7f4547058b2dfd4229142dca73a7d9b4bdb239
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742557"
---
# <a name="manually-fail-over-a-database-mirroring-session-sql-server-management-studio"></a><span data-ttu-id="36cc6-102">データベース ミラーリング セッションの手動フェールオーバー (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="36cc6-102">Manually Fail Over a Database Mirroring Session (SQL Server Management Studio)</span></span>
  <span data-ttu-id="36cc6-103">ミラー化されたデータベースが同期されている場合 (つまり、データベースが SYNCHRONIZED 状態である場合)、データベース所有者はミラー サーバーに対して手動フェールオーバーを開始できます。</span><span class="sxs-lookup"><span data-stu-id="36cc6-103">When the mirrored database is synchronized (that is, when the database is in the SYNCHRONIZED state), the database owner can initiate manual failover to the mirror server.</span></span>  
  
 <span data-ttu-id="36cc6-104">手動フェールオーバー中、フェールオーバーが発生するデータベースに対するプリンシパル サーバーとミラー サーバーのロールが切り替わります。</span><span class="sxs-lookup"><span data-stu-id="36cc6-104">During a manual failover, the principal and mirror server roles are swapped for the database on which the failover occurs.</span></span> <span data-ttu-id="36cc6-105">その結果、ミラー データベースがプリンシパル データベースになり、プリンシパル データベースがミラー データベースになります。</span><span class="sxs-lookup"><span data-stu-id="36cc6-105">The mirror database becomes the principal database and the principal database becomes the mirror.</span></span> <span data-ttu-id="36cc6-106">次の表は、 `SQLDBENGINE0_1` と `SQLDBENGINE0_2`という 2 つのミラーリング パートナーを例にとって、そのロールが手動フェールオーバーによってどのように切り替わるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="36cc6-106">For example, the following table shows the how a manual failover swaps the roles of two mirroring partners: `SQLDBENGINE0_1` and `SQLDBENGINE0_2`.</span></span>  
  
|<span data-ttu-id="36cc6-107">サーバー</span><span class="sxs-lookup"><span data-stu-id="36cc6-107">Server</span></span>|<span data-ttu-id="36cc6-108">フェールオーバー前</span><span class="sxs-lookup"><span data-stu-id="36cc6-108">Before failover</span></span>|<span data-ttu-id="36cc6-109">フェールオーバー後</span><span class="sxs-lookup"><span data-stu-id="36cc6-109">After failover</span></span>|  
|------------|---------------------|--------------------|  
|`SQLDBENGINE0_1`|<span data-ttu-id="36cc6-110">PRINCIPAL</span><span class="sxs-lookup"><span data-stu-id="36cc6-110">PRINCIPAL</span></span>|<span data-ttu-id="36cc6-111">MIRROR</span><span class="sxs-lookup"><span data-stu-id="36cc6-111">MIRROR</span></span>|  
|`SQLDBENGINE0_2`|<span data-ttu-id="36cc6-112">MIRROR</span><span class="sxs-lookup"><span data-stu-id="36cc6-112">MIRROR</span></span>|<span data-ttu-id="36cc6-113">PRINCIPAL</span><span class="sxs-lookup"><span data-stu-id="36cc6-113">PRINCIPAL</span></span>|  
  
 <span data-ttu-id="36cc6-114">その他のデータベース ミラーリング セッションに対するサーバーのロールは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="36cc6-114">Note that the server roles for other database mirroring sessions are not affected.</span></span> <span data-ttu-id="36cc6-115">詳細については、「 [データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="36cc6-115">For more information, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
### <a name="to-manually-fail-over-database-mirroring"></a><span data-ttu-id="36cc6-116">データベース ミラーリングを手動でフェールオーバーするには</span><span class="sxs-lookup"><span data-stu-id="36cc6-116">To manually fail over database mirroring</span></span>  
  
1.  <span data-ttu-id="36cc6-117">プリンシパル サーバー インスタンスに接続し、 **[オブジェクト エクスプローラー]** ペインでサーバー名をクリックして、サーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="36cc6-117">Connect to the principal server instance and, in the **Object Explorer** pane, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="36cc6-118">**[データベース]** を展開し、フェールオーバー先のデータベースをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cc6-118">Expand **Databases**, and select the database to be failed over.</span></span>  
  
3.  <span data-ttu-id="36cc6-119">データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cc6-119">Right-click the database, select **Tasks**, and then click **Mirror**.</span></span> <span data-ttu-id="36cc6-120">**[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="36cc6-120">This opens the **Mirroring** page of the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="36cc6-121">**[フェールオーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36cc6-121">Click **Failover**.</span></span>  
  
     <span data-ttu-id="36cc6-122">確認のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="36cc6-122">A confirmation box appears.</span></span>  <span data-ttu-id="36cc6-123">Windows 認証を使用してミラー サーバーに接続しようとすると、プリンシパル サーバーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="36cc6-123">The principal server begins by trying to connect to the mirror server by using Windows Authentication.</span></span> <span data-ttu-id="36cc6-124">Windows 認証が機能しない場合は、プリンシパル サーバーに **[サーバーへの接続]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="36cc6-124">If Windows Authentication does not work, the principal server displays the **Connect to Server** dialog box.</span></span> <span data-ttu-id="36cc6-125">ミラー サーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、 **[認証]** ボックスで **[SQL Server 認証]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="36cc6-125">If the mirror server uses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, select **SQL Server Authentication** in the **Authentication** box.</span></span> <span data-ttu-id="36cc6-126">**[ログイン]** テキスト ボックスで、ミラー サーバー上で接続するログイン アカウントを指定し、 **[パスワード]** テキスト ボックスで、そのアカウントのパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="36cc6-126">In the **Login** text box, specify the login account to connect with on the mirror server, and in the **Password** text box, specify the password for that account.</span></span>  
  
     <span data-ttu-id="36cc6-127">フェールオーバーに成功すると、 **[データベースのプロパティ]** ダイアログ ボックスが閉じます。</span><span class="sxs-lookup"><span data-stu-id="36cc6-127">If failover succeeds, the **Database Properties** dialog box closes.</span></span> <span data-ttu-id="36cc6-128">その結果、ミラー データベースがプリンシパル データベースになり、プリンシパル データベースがミラー データベースになります。</span><span class="sxs-lookup"><span data-stu-id="36cc6-128">The mirror database becomes the principal database and the principal database becomes the mirror.</span></span>  
  
     <span data-ttu-id="36cc6-129">フェールオーバーに失敗すると、エラー メッセージが表示され、ダイアログ ボックスが開いたままになります。</span><span class="sxs-lookup"><span data-stu-id="36cc6-129">If failover fails, an error message is displayed and the dialog box remains open.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="36cc6-130">**[ミラーリング]** ページを開いた後でプロパティを変更した場合、それらの変更内容は保存されません。</span><span class="sxs-lookup"><span data-stu-id="36cc6-130">If you have modified any properties since opening the **Mirroring** page, those changes will not be saved.</span></span>  
  
     <span data-ttu-id="36cc6-131">ダイアログ ボックスが自動的に閉じられます。</span><span class="sxs-lookup"><span data-stu-id="36cc6-131">The dialog box closes automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cc6-132">参照</span><span class="sxs-lookup"><span data-stu-id="36cc6-132">See Also</span></span>  
 <span data-ttu-id="36cc6-133">[データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span><span class="sxs-lookup"><span data-stu-id="36cc6-133">[Database Properties &#40;Mirroring Page&#41;](../../relational-databases/databases/database-properties-mirroring-page.md) </span></span>  
 <span data-ttu-id="36cc6-134">[データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36cc6-134">[Database Mirroring &#40;SQL Server&#41;](database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="36cc6-135">[データベース ミラーリング セッションを手動でフェールオーバーする &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="36cc6-135">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md) </span></span>  
 <span data-ttu-id="36cc6-136">[データベース ミラーリング セッションを一時停止または再開する &#40;Transact-SQL&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="36cc6-136">[Pause or Resume a Database Mirroring Session &#40;SQL Server&#41;](pause-or-resume-a-database-mirroring-session-sql-server.md) </span></span>  
 [<span data-ttu-id="36cc6-137">データベース ミラーリングを削除する &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="36cc6-137">Remove Database Mirroring &#40;SQL Server&#41;</span></span>](remove-database-mirroring-sql-server.md)  
  
  
