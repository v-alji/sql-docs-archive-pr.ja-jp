---
title: '[データベースのプロパティ] ([トランザクション ログの配布] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
author: stevestein
ms.author: sstein
ms.openlocfilehash: dd36b3bc56bcd48c53871c9bc1e334d72c80ac78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742226"
---
# <a name="database-properties-transaction-log-shipping-page"></a><span data-ttu-id="75165-102">[データベースのプロパティ] ([トランザクション ログの配布] ページ)</span><span class="sxs-lookup"><span data-stu-id="75165-102">Database Properties (Transaction Log Shipping Page)</span></span>
  <span data-ttu-id="75165-103">このページを使用すると、データベースのログ配布のプロパティを構成および変更できます。</span><span class="sxs-lookup"><span data-stu-id="75165-103">Use this page to configure and modify the properties of log shipping for a database.</span></span>  
  
 <span data-ttu-id="75165-104">ログ配布の概念については、「 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75165-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="75165-105">Options</span><span class="sxs-lookup"><span data-stu-id="75165-105">Options</span></span>  
 <span data-ttu-id="75165-106">**[ログ配布構成のプライマリ データベースとして有効にする]**</span><span class="sxs-lookup"><span data-stu-id="75165-106">**Enable this as a primary database in a log shipping configuration**</span></span>  
 <span data-ttu-id="75165-107">このデータベースをログ配布のプライマリ データベースとして有効にします。</span><span class="sxs-lookup"><span data-stu-id="75165-107">Enables this database as a log shipping primary database.</span></span> <span data-ttu-id="75165-108">オンにした場合は、このページの残りのオプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="75165-108">Select it and then configure the remaining options on this page.</span></span> <span data-ttu-id="75165-109">このチェック ボックスをオフにした場合、このデータベースのログ配布構成は削除されます。</span><span class="sxs-lookup"><span data-stu-id="75165-109">If you clear this check box, the log shipping configuration will be dropped for this database.</span></span>  
  
 <span data-ttu-id="75165-110">**[バックアップの設定]**</span><span class="sxs-lookup"><span data-stu-id="75165-110">**Backup Settings**</span></span>  
 <span data-ttu-id="75165-111">**[バックアップの設定]** をクリックすると、バックアップ スケジュール、場所、警告、およびアーカイブ パラメーターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="75165-111">Click **Backup Settings** to configure backup schedule, location, alert, and archiving parameters.</span></span>  
  
 <span data-ttu-id="75165-112">**[バックアップ スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="75165-112">**Backup schedule**</span></span>  
 <span data-ttu-id="75165-113">プライマリ データベースに対して現在選択されているバックアップ スケジュールを表示します。</span><span class="sxs-lookup"><span data-stu-id="75165-113">Shows the currently selected backup schedule for the primary database.</span></span> <span data-ttu-id="75165-114">これらの設定を変更するには、 **[バックアップの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75165-114">Click **Backup Settings** to modify these settings.</span></span>  
  
 <span data-ttu-id="75165-115">**[最後に作成したバックアップ]**</span><span class="sxs-lookup"><span data-stu-id="75165-115">**Last backup created**</span></span>  
 <span data-ttu-id="75165-116">プライマリ データベースの最新のトランザクション ログ バックアップの作成日付を示します。</span><span class="sxs-lookup"><span data-stu-id="75165-116">Indicates the time and date of the last transaction log backup of the primary database.</span></span>  
  
 <span data-ttu-id="75165-117">**[セカンダリ サーバー インスタンスとデータベース]**</span><span class="sxs-lookup"><span data-stu-id="75165-117">**Secondary server instances and databases**</span></span>  
 <span data-ttu-id="75165-118">このプライマリ データベースに対して現在構成されているセカンダリ サーバーおよびセカンダリ データベースを表示します。</span><span class="sxs-lookup"><span data-stu-id="75165-118">Lists the currently configured secondary servers and databases for this primary database.</span></span> <span data-ttu-id="75165-119">セカンダリ データベースに関連付けられているパラメーターを変更するには、データベースを強調表示し、 **[...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75165-119">Highlight a database, and then click **...** to modify the parameters associated with that secondary database.</span></span>  
  
 <span data-ttu-id="75165-120">**追加**</span><span class="sxs-lookup"><span data-stu-id="75165-120">**Add**</span></span>  
 <span data-ttu-id="75165-121">このプライマリ データベースのログ配布構成にセカンダリ データベースを追加するには、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75165-121">Click **Add** to add a secondary database to the log shipping configuration for this primary database.</span></span>  
  
 <span data-ttu-id="75165-122">**Remove**</span><span class="sxs-lookup"><span data-stu-id="75165-122">**Remove**</span></span>  
 <span data-ttu-id="75165-123">選択されているデータベースをこのログ配布構成から削除します。</span><span class="sxs-lookup"><span data-stu-id="75165-123">Removes a selected database from this log shipping configuration.</span></span> <span data-ttu-id="75165-124">データベースを選択してから、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75165-124">Select the database first and then click **Remove**.</span></span>  
  
 <span data-ttu-id="75165-125">**[監視サーバー インスタンスを使用する]**</span><span class="sxs-lookup"><span data-stu-id="75165-125">**Use a monitor server instance**</span></span>  
 <span data-ttu-id="75165-126">このログ配布構成に対して監視サーバー インスタンスを設定します。</span><span class="sxs-lookup"><span data-stu-id="75165-126">Sets up a monitor server instance for this log shipping configuration.</span></span> <span data-ttu-id="75165-127">監視サーバー インスタンスを指定するには、 **[監視サーバー インスタンスを使用する]** チェック ボックスをオンにし、 **[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75165-127">Select the **Use a monitor server instance** check box and then click **Settings** to specify the monitor server instance.</span></span>  
  
 <span data-ttu-id="75165-128">**[監視サーバー インスタンス]**</span><span class="sxs-lookup"><span data-stu-id="75165-128">**Monitor server instance**</span></span>  
 <span data-ttu-id="75165-129">このログ配布構成に対して現在構成されている監視サーバー インスタンスを示します。</span><span class="sxs-lookup"><span data-stu-id="75165-129">Indicates the currently configured monitor server instance for this log shipping configuration.</span></span>  
  
 <span data-ttu-id="75165-130">**設定**</span><span class="sxs-lookup"><span data-stu-id="75165-130">**Settings**</span></span>  
 <span data-ttu-id="75165-131">ログ配布構成に対して監視サーバー インスタンスを構成します。</span><span class="sxs-lookup"><span data-stu-id="75165-131">Configures the monitor server instance for a log shipping configuration.</span></span> <span data-ttu-id="75165-132">この監視サーバー インスタンスを構成するには、 **[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="75165-132">Click **Settings** to configure this monitor server instance.</span></span>  
  
 <span data-ttu-id="75165-133">**[スクリプトの構成]**</span><span class="sxs-lookup"><span data-stu-id="75165-133">**Script Configuration**</span></span>  
 <span data-ttu-id="75165-134">選択されているパラメーターを使用して、ログ配布を構成するためのスクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="75165-134">Generates a script for configuring log shipping with the parameters you have selected.</span></span> <span data-ttu-id="75165-135">**[スクリプトの構成]** をクリックし、スクリプトの出力先を選択します。</span><span class="sxs-lookup"><span data-stu-id="75165-135">Click **Script Configuration**, and then choose an output destination for the script.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="75165-136">セカンダリ データベースの設定スクリプトを生成するには、 **[セカンダリ データベースの設定]** ダイアログ ボックスを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="75165-136">Before scripting settings for a secondary database, you must invoke the **Secondary Database Settings** dialog box.</span></span> <span data-ttu-id="75165-137">このダイアログ ボックスを呼び出すことにより、セカンダリ サーバーに接続して、スクリプトの生成に必要なセカンダリ データベースの現在の設定を取得できます。</span><span class="sxs-lookup"><span data-stu-id="75165-137">Invoking this dialog box connects you to the secondary server and retrieves the current settings of the secondary database that are needed to generate the script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75165-138">参照</span><span class="sxs-lookup"><span data-stu-id="75165-138">See Also</span></span>  
 <span data-ttu-id="75165-139">[ログ配布ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="75165-139">[Log Shipping Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql) </span></span>  
 [<span data-ttu-id="75165-140">ログ配布テーブル &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="75165-140">Log Shipping Tables &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/log-shipping-tables-transact-sql)  
  
  
