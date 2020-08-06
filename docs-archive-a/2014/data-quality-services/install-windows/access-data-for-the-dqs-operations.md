---
title: DQS 操作のためのデータへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 515b087a8d16e44314d1a21d3dfbd6f13c767f5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716881"
---
# <a name="access-data-for-the-dqs-operations"></a><span data-ttu-id="881a1-102">DQS 操作のためのデータへのアクセス</span><span class="sxs-lookup"><span data-stu-id="881a1-102">Access Data for the DQS Operations</span></span>
  <span data-ttu-id="881a1-103">[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 操作にソース データを使用し、処理後のデータをエクスポートするには、次のいずれかの方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="881a1-103">To use your source data for [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) operations, and export your processed data, you can do either of the following:</span></span>  
  
-   <span data-ttu-id="881a1-104">ソース データを DQS_STAGING_DATA データベース内のテーブル/ビューにコピーし、その後、それを DQS 操作に使用する。</span><span class="sxs-lookup"><span data-stu-id="881a1-104">Copy your source data to a table/view in the DQS_STAGING_DATA database, and then use it for DQS operations.</span></span> <span data-ttu-id="881a1-105">処理後のデータを、DQS_STAGING_DATA データベース内の新しいテーブルにエクスポートすることもできます。</span><span class="sxs-lookup"><span data-stu-id="881a1-105">You can also export the processed data to a new table in the DQS_STAGING_DATA database.</span></span> <span data-ttu-id="881a1-106">これを行うには、Windows ユーザー アカウントに DQS_STAGING_DATA データベースへの読み取り/書き込みアクセス権を与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="881a1-106">To do so, your Windows user account must be granted read/write access to the DQS_STAGING_DATA database.</span></span>  
  
-   <span data-ttu-id="881a1-107">DQS 操作のソース データと、処理後のデータのエクスポート先に、自分専用のデータベースを使用する。</span><span class="sxs-lookup"><span data-stu-id="881a1-107">Use your own database as the source data for the DQS operations, and destination for exporting the processed data.</span></span> <span data-ttu-id="881a1-108">これを行うには、自分のデータベースが、Data Quality Server データベースと同じ SQL Server インスタンス内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="881a1-108">To do so, ensure that your database is in the same SQL Server instance as the Data Quality Server databases.</span></span> <span data-ttu-id="881a1-109">それ以外の場合、DQS 操作を行うために Data Quality Client でデータベースを利用することはできません。</span><span class="sxs-lookup"><span data-stu-id="881a1-109">Otherwise, the database will not be available in the Data Quality Client for DQS operations.</span></span> <span data-ttu-id="881a1-110">また、Windows ユーザー アカウントには、照合結果をエクスポートする DQS_STAGING_DATA データベースへのアクセス権も付与する必要があります。これは、照合結果のエクスポートが、最初に照合結果が DQS_STAGING_DATA データベース内の一時テーブルにエクスポートされてから、エクスポート先データベース内のテーブルに移動されるという 2 段階で構成されるためです。</span><span class="sxs-lookup"><span data-stu-id="881a1-110">Also, your Windows user account must be granted access on the DQS_STAGING_DATA database for exporting the matching results because matching results are exported in two phases: first, the matching results are exported to the temporary tables in the DQS_STAGING_DATA database, and then moved to the table in your destination database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="881a1-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="881a1-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="881a1-112">DQSInstaller.exe ファイルを実行して [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] のインストールを完了しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="881a1-112">You must have completed the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="881a1-113">詳細については、「 [Data Quality Server のインストールを完了するための DQSInstaller.exe の実行](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="881a1-113">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
-   <span data-ttu-id="881a1-114">データベースの SQL ログインへのアクセスを付与または変更するには、Windows ユーザー アカウントがデータベース エンジン インスタンスの適切な固定サーバー ロール (securityadmin、serveradmin、sysadmin など) のメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="881a1-114">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) in the database engine instance to grant/modify access to SQL login on databases.</span></span>  
  
### <a name="to-grant-readwrite-access-to-a-user-on-the-dqs_staging_data-database"></a><span data-ttu-id="881a1-115">DQS_STAGING_DATA データベースへの読み取り/書き込みアクセス権をユーザーに付与するには</span><span class="sxs-lookup"><span data-stu-id="881a1-115">To grant read/write access to a User on the DQS_STAGING_DATA Database</span></span>  
  
1.  <span data-ttu-id="881a1-116">Microsoft SQL Server Management Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="881a1-116">Start Microsoft SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="881a1-117">Microsoft SQL Server Management Studio で、SQL Server インスタンスを展開し、 **[セキュリティ]** を展開し、 **[ログイン]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="881a1-117">In Microsoft SQL Server Management Studio, expand your SQL Server instance, and expand **Security**, and then expand **Logins**.</span></span>  
  
3.  <span data-ttu-id="881a1-118">SQL ログインを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="881a1-118">Right-click a SQL login, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="881a1-119">**[ログインのプロパティ]** ダイアログ ボックスの左ペインで **[ユーザー マッピング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="881a1-119">In the **Login Properties** dialog box, click the **User Mapping** page in the left pane.</span></span>  
  
5.  <span data-ttu-id="881a1-120">右ペインで、 **[DQS_STAGING_DATA]** データベースの **[マップ]** 列のチェック ボックスをオンにし、 **[DQS_STAGING_DATA のデータベース ロール メンバーシップ]** ペインで次のロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="881a1-120">In the right pane, select the check box under the **Map** column for the **DQS_STAGING_DATA** database, and then select the following roles in the **Database role membership for: DQS_STAGING_DATA** pane:</span></span>  
  
    -   <span data-ttu-id="881a1-121">**db_datareader**: テーブル/ビューからのデータの読み取り。</span><span class="sxs-lookup"><span data-stu-id="881a1-121">**db_datareader**: Read data from tables/views.</span></span>  
  
    -   <span data-ttu-id="881a1-122">**db_datawriter**: テーブル内のデータの追加、削除、または変更。</span><span class="sxs-lookup"><span data-stu-id="881a1-122">**db_datawriter**: Add, delete, or change data in tables.</span></span>  
  
    -   <span data-ttu-id="881a1-123">**db_ddladmin**: テーブル/ビューの作成、変更、または削除。</span><span class="sxs-lookup"><span data-stu-id="881a1-123">**db_ddladmin**: Create, modify, or delete tables/views.</span></span>  
  
6.  <span data-ttu-id="881a1-124">**[ログインのプロパティ]** ダイアログ ボックスで、 **[OK]** をクリックして変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="881a1-124">In the **Login Properties** dialog box, click **OK** to apply the changes.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="881a1-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="881a1-125">Next Steps</span></span>  
 <span data-ttu-id="881a1-126">DQS 操作のデータ ソースとしてデータベースにアクセスする DQS 操作を実行してから、処理後のデータをデータベースにエクスポートしてください。</span><span class="sxs-lookup"><span data-stu-id="881a1-126">Try performing DQS operations that accesses the database as data source for DQS operation, and then exports the processed data to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="881a1-127">参照</span><span class="sxs-lookup"><span data-stu-id="881a1-127">See Also</span></span>  
 [<span data-ttu-id="881a1-128">Data Quality Services のインストール</span><span class="sxs-lookup"><span data-stu-id="881a1-128">Install Data Quality Services</span></span>](install-data-quality-services.md)  
  
  
