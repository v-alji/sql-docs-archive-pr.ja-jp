---
title: '[ログ ファイルの表示] を開く | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Log File Viewer, opening
ms.assetid: a86b89cb-0432-4648-895a-05ecc5450e45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269ff10275f7463a8a85249a2a0f06fe9bde364a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639496"
---
# <a name="open-log-file-viewer"></a><span data-ttu-id="ac9bc-102">[ログ ファイルの表示] を開く</span><span class="sxs-lookup"><span data-stu-id="ac9bc-102">Open Log File Viewer</span></span>
  <span data-ttu-id="ac9bc-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の [ログ ファイルの表示] を使用すると、次のログに記録されたエラーおよびイベントに関する情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-103">You can use Log File Viewer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to access information about errors and events that are captured in the following logs:</span></span>  
  
-   <span data-ttu-id="ac9bc-104">監査コレクション</span><span class="sxs-lookup"><span data-stu-id="ac9bc-104">Audit Collection</span></span>  
  
-   <span data-ttu-id="ac9bc-105">データ収集</span><span class="sxs-lookup"><span data-stu-id="ac9bc-105">Data Collection</span></span>  
  
-   <span data-ttu-id="ac9bc-106">データベース メール</span><span class="sxs-lookup"><span data-stu-id="ac9bc-106">Database Mail</span></span>  
  
-   <span data-ttu-id="ac9bc-107">ジョブ履歴</span><span class="sxs-lookup"><span data-stu-id="ac9bc-107">Job History</span></span>  
  
-   <span data-ttu-id="ac9bc-108">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ac9bc-108">SQL Server</span></span>  
  
-   <span data-ttu-id="ac9bc-109">SQL Server エージェント</span><span class="sxs-lookup"><span data-stu-id="ac9bc-109">SQL Server Agent</span></span>  
  
-   <span data-ttu-id="ac9bc-110">Windows イベント (イベント ビューアーからもアクセス可能)</span><span class="sxs-lookup"><span data-stu-id="ac9bc-110">Windows events (These Windows events can also be accessed from Event Viewer.)</span></span>  
  
 <span data-ttu-id="ac9bc-111">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降では、登録済みサーバーを使用して、ローカルまたはリモートの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログ ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-111">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], you can use Registered Servers to view [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files from local or remote instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ac9bc-112">登録済みサーバーを使用すると、インスタンスがオンラインでもオフラインでも、ログ ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-112">By using Registered Servers, you can view the log files when the instances are either online or offline.</span></span> <span data-ttu-id="ac9bc-113">オンライン アクセスの詳細については、このトピックで後述する「登録済みサーバーからオンラインのログ ファイルを参照するには」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-113">For more information about online access, see the procedure "To view online log files from Registered Servers" later in this topic.</span></span> <span data-ttu-id="ac9bc-114">オフラインの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ ファイルへのアクセス方法の詳細については、「 [オフライン ログ ファイルの表示](view-offline-log-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-114">For more information about how to access offline [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log files, see [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
 <span data-ttu-id="ac9bc-115">[ログ ファイルの表示] は、表示する情報に応じていくつかの方法で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-115">You can open Log File Viewer in several ways, depending on the information that you want to view.</span></span>  
  
##  <a name="permissions"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="ac9bc-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="ac9bc-116">Permissions</span></span>  
 <span data-ttu-id="ac9bc-117">オンラインの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのログ ファイルにアクセスするには、securityadmin 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-117">To access log files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are online, this requires membership in the securityadmin fixed server role.</span></span>  
  
 <span data-ttu-id="ac9bc-118">オフラインの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのログ ファイルにアクセスするには、 **Root\Microsoft\SqlServer\ComputerManagement10** WMI 名前空間、およびログ ファイルの保存されているフォルダーの両方に対する読み取りアクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-118">To access log files for instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are offline, you must have read access to both the **Root\Microsoft\SqlServer\ComputerManagement10** WMI namespace, and to the folder where the log files are stored.</span></span> <span data-ttu-id="ac9bc-119">詳細については、「 [オフライン ログ ファイルの表示](view-offline-log-files.md)」トピックの「セキュリティ」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-119">For more information, see the Security section of the topic [View Offline Log Files](view-offline-log-files.md).</span></span>  
  
### <a name="security"></a><span data-ttu-id="ac9bc-120">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="ac9bc-120">Security</span></span>  
 <span data-ttu-id="ac9bc-121">securityadmin 固定サーバー ロールのメンバーシップが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-121">Requires membership in the securityadmin fixed server role.</span></span>  
  
### <a name="view-log-files"></a><span data-ttu-id="ac9bc-122">ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="ac9bc-122">View Log Files</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-general-sql-server-activity"></a><span data-ttu-id="ac9bc-123">SQL Server の一般的な動作に関連するログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ac9bc-123">To view logs that are related to general SQL Server activity</span></span>  
  
1.  <span data-ttu-id="ac9bc-124">オブジェクト エクスプローラーで、 **[管理]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-124">In Object Explorer, expand **Management**.</span></span>  
  
2.  <span data-ttu-id="ac9bc-125">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-125">Do either of the following:</span></span>  
  
    -   <span data-ttu-id="ac9bc-126">**[SQL Server ログ]** を右クリックし、 **[表示]** をポイントして、 **[SQL Server ログ]** または **[SQL Server および Windows ログ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-126">Right-click **SQL Server Logs**, point to **View**, and then click either **SQL Server Log** or **SQL Server and Windows Log**.</span></span>  
  
    -   <span data-ttu-id="ac9bc-127">**[SQL Server ログ]** を展開し、任意のログ ファイルを右クリックして **[SQL Server ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-127">Expand **SQL Server Logs**, right-click any log file, and then click **View SQL Server Log**.</span></span> <span data-ttu-id="ac9bc-128">任意のログ ファイルをダブルクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-128">You can also double-click any log file.</span></span>  
  
     <span data-ttu-id="ac9bc-129">ログには、 **データベース メール**、 **SQL Server**、 **SQL Server エージェント**、および **Windows NT**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-129">The logs include **Database Mail**, **SQL Server**, **SQL Server Agent**, and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-jobs"></a><span data-ttu-id="ac9bc-130">ジョブに関連するログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ac9bc-130">To view logs that are related to jobs</span></span>  
  
-   <span data-ttu-id="ac9bc-131">オブジェクト エクスプローラーで **[SQL Server エージェント]** を展開し、 **[ジョブ]** を右クリックして **[履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-131">In Object Explorer, expand **SQL Server Agent**, right-click **Jobs**, and then click **View History**.</span></span>  
  
     <span data-ttu-id="ac9bc-132">ログには、 **データベース メール**、 **ジョブ履歴**、および **SQL Server エージェント**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-132">The logs include **Database Mail**, **Job History**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-maintenance-plans"></a><span data-ttu-id="ac9bc-133">メンテナンス プランに関連するログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ac9bc-133">To view logs that are related to maintenance plans</span></span>  
  
-   <span data-ttu-id="ac9bc-134">オブジェクト エクスプローラーで **[管理]** を展開し、 **[メンテナンス プラン]** を右クリックして **[履歴の表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-134">In Object Explorer, expand **Management**, right-click **Maintenance Plans**, and then click **View History**.</span></span>  
  
     <span data-ttu-id="ac9bc-135">ログには、 **データベース メール**、 **ジョブ履歴**、 **メンテナンス プラン**、 **リモート メンテナンス プラン**、および **SQL Server エージェント**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-135">The logs include **Database Mail**, **Job History**, **Maintenance Plans**, **Remote Maintenance Plans**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-data-collection"></a><span data-ttu-id="ac9bc-136">データ コレクションに関連するログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ac9bc-136">To view logs that are related to Data Collection</span></span>  
  
-   <span data-ttu-id="ac9bc-137">オブジェクト エクスプローラーで **[管理]** を展開し、 **[データ コレクション]** を右クリックして **[ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-137">In Object Explorer, expand **Management**, right-click **Data Collection**, and then click **View Logs**.</span></span>  
  
     <span data-ttu-id="ac9bc-138">ログには、 **データ コレクション**、 **ジョブ履歴**、および **SQL Server エージェント**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-138">The logs include **Data Collection**, **Job History**, and **SQL Server Agent**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-database-mail"></a><span data-ttu-id="ac9bc-139">データベース メールに関連するログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ac9bc-139">To view logs that are related to Database Mail</span></span>  
  
-   <span data-ttu-id="ac9bc-140">オブジェクト エクスプローラーで、 **[管理]** を展開し、 **[データベース メール]** を右クリックし、 **[データベース メール ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-140">In Object Explorer, expand **Management**, right-click **Database Mail**, and then click **View Database Mail Log**.</span></span>  
  
     <span data-ttu-id="ac9bc-141">ログには、 **データベース メール、ジョブ履歴**、 **メンテナンス プラン**、 **リモート メンテナンス プラン**、 **SQL Server**、 **SQL Server エージェント**、および **Windows NT**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-141">The logs include **Database Mail, Job History**, **Maintenance Plans**, **Remote Maintenance Plans**, **SQL Server**, **SQL Server Agent**, and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a><span data-ttu-id="ac9bc-142">監査コレクションに関連するログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ac9bc-142">To view logs that are related to audits collections</span></span>  
  
-   <span data-ttu-id="ac9bc-143">オブジェクト エクスプローラーで、 **[セキュリティ]** 、 **[監査]** の順に展開し、監査を右クリックして **[監査ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-143">In Object Explorer, expand **Security**, expand **Audits**, right-click an audit, and then click **View Audit Logs**.</span></span>  
  
     <span data-ttu-id="ac9bc-144">ログには、 **監査コレクション** と **Windows NT**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-144">The logs include **Audit Collection** and **Windows NT**.</span></span>  
  
##### <a name="to-view-logs-that-are-related-to-audits-collections"></a><span data-ttu-id="ac9bc-145">監査コレクションに関連するログを表示するには</span><span class="sxs-lookup"><span data-stu-id="ac9bc-145">To view logs that are related to audits collections</span></span>  
  
-   <span data-ttu-id="ac9bc-146">オブジェクト エクスプローラーで、 **[セキュリティ]** 、 **[監査]** の順に展開し、監査を右クリックして **[監査ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-146">In Object Explorer, expand **Security**, expand **Audits**, right-click an audit, and then click **View Audit Logs**.</span></span>  
  
     <span data-ttu-id="ac9bc-147">ログには、 **監査コレクション** と **Windows NT**が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ac9bc-147">The logs include **Audit Collection** and **Windows NT**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac9bc-148">参照</span><span class="sxs-lookup"><span data-stu-id="ac9bc-148">See Also</span></span>  
 <span data-ttu-id="ac9bc-149">[ログ ファイルの表示](log-file-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="ac9bc-149">[Log File Viewer](log-file-viewer.md) </span></span>  
 <span data-ttu-id="ac9bc-150">[SQL Server Audit &#40;データベース エンジン&#41;](../security/auditing/sql-server-audit-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="ac9bc-150">[SQL Server Audit &#40;Database Engine&#41;](../security/auditing/sql-server-audit-database-engine.md) </span></span>  
 [<span data-ttu-id="ac9bc-151">オフライン ログ ファイルの表示</span><span class="sxs-lookup"><span data-stu-id="ac9bc-151">View Offline Log Files</span></span>](view-offline-log-files.md)  
  
  
