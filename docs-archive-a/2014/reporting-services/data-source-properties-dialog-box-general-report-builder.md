---
title: '[全般] ([データソースのプロパティ] ダイアログボックス) (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10018"
ms.assetid: b956f43a-8426-4679-acc1-00f405d5ff5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dcfba8346a3519817a36c21b24be1a91a613e098
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631660"
---
# <a name="data-source-properties-dialog-box-general-report-builder"></a><span data-ttu-id="73272-102">[全般] ([データ ソースのプロパティ] ダイアログ ボックス) (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="73272-102">Data Source Properties Dialog Box, General (Report Builder)</span></span>
  <span data-ttu-id="73272-103">レポート サーバーから共有データ ソースを選択する場合や、レポートに埋め込まれたデータ ソースの接続情報を作成または変更する場合は、 **[データ ソースのプロパティ]** ダイアログ ボックスの **[全般]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="73272-103">Select **General** on the **Data Source Properties** dialog box to select a shared data source from a report server or to create or modify connection information for a data source embedded in the report.</span></span>  
  
 <span data-ttu-id="73272-104">データ ソースへの接続に使用される資格情報の種類は、データ ソースのプロパティで指定します。</span><span class="sxs-lookup"><span data-stu-id="73272-104">The type of credentials used to connect to a data source is specified in the data source properties.</span></span> <span data-ttu-id="73272-105">レポート サーバーからレポートを開く場合、データ ソースのプロパティに指定された実行時の資格情報は、クエリの作成やレポートのプレビューなどのデザイン時のタスクでは有効でない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="73272-105">When you open a report from the report server, the run-time credentials, specified in the data source properties, might not work for design time tasks such as creating queries and previewing reports.</span></span> <span data-ttu-id="73272-106">たとえば、データ ソースで、自分以外の Windows 資格情報や知らないユーザーのユーザー名とパスワードが使用されることがあります。</span><span class="sxs-lookup"><span data-stu-id="73272-106">For example, the data source might use Windows credentials other than yours or a user name and password that are unknown to you.</span></span>  
  
 <span data-ttu-id="73272-107">レポート ビルダーでは、データ ソースのプロパティに指定された資格情報を使用してデータ ソースに接続できない場合、 **[データ ソースの資格情報の入力]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="73272-107">Report Builder opens the **Enter Data Source Credentials** dialog box when it is unable to connect to the data source using the credentials provided in the data source properties.</span></span> <span data-ttu-id="73272-108">通常、これは次の場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="73272-108">Typically this happens when:</span></span>  
  
-   <span data-ttu-id="73272-109">データ ソースが資格情報を要求するように構成されている。</span><span class="sxs-lookup"><span data-stu-id="73272-109">The data source is configured to prompt for credentials.</span></span>  
  
-   <span data-ttu-id="73272-110">データ ソースが、保存されている資格情報を使用するように構成されている。</span><span class="sxs-lookup"><span data-stu-id="73272-110">The data source is configured to use stored credentials.</span></span>  <span data-ttu-id="73272-111">潜在的なセキュリティ上の脅威を最小限に抑えるために、レポート ビルダーは、サーバー上に保存された資格情報を取得しないように設計されています。</span><span class="sxs-lookup"><span data-stu-id="73272-111">To minimize potential security threats, Report Builder is designed to not retrieve credentials stored on the server.</span></span>  
  
 <span data-ttu-id="73272-112">**[データ ソースの資格情報の入力]** ダイアログ ボックスを使用すると、デザイン時にレポート ビルダーによって使用された資格情報を変更して、現在の Windows ユーザーとしてデータ ソースに接続したり、ユーザー名とパスワードを入力したりできます。</span><span class="sxs-lookup"><span data-stu-id="73272-112">You can use the **Enter Data Source Credentials** dialog box to change the credentials used by Report Builder at design time to connect to the data source as the current Windows user or provide a user name and password.</span></span> <span data-ttu-id="73272-113">ユーザー名とパスワードを入力する場合、それらを Windows 資格情報として使用するかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="73272-113">If you provide a user name and password you can indicate whether they are used as Windows credentials.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73272-114">クエリ デザイナーではデザイン時の資格情報に別の種類の資格情報を指定できますが、レポートのプレビューではデータ ソースに指定されている既存の資格情報オプションのユーザー名とパスワードしか入力できません。</span><span class="sxs-lookup"><span data-stu-id="73272-114">Although the query designers allow you to specify other another credentials type for design-time credentials, report preview only allows you to enter the user name and password for the existing credentials options specified in the data source.</span></span>  
  
 <span data-ttu-id="73272-115">**[接続テスト]** をクリックすると、データ ソースのプロパティの [資格情報] ページで指定された資格情報を使用して、データ ソースへの接続がテストされます。</span><span class="sxs-lookup"><span data-stu-id="73272-115">When you click **Test Connection**, the connection to the data source is tested using the credentials specified in the data source properties credentials page.</span></span> <span data-ttu-id="73272-116">埋め込みデータ ソースと共有データ ソースへの接続をテストできます。</span><span class="sxs-lookup"><span data-stu-id="73272-116">You can test connections to embedded and shared data sources.</span></span>  
  
 <span data-ttu-id="73272-117">パスワードが必要など、指定された資格情報が不完全な場合、レポート ビルダーでは、データ ソースへの接続が必要なときに、実行時の資格情報の入力を再度要求します。</span><span class="sxs-lookup"><span data-stu-id="73272-117">If the credentials specified are incomplete (for example, a password is required), Report Builder prompts you again for run-time credentials when it needs to connect the data source.</span></span> <span data-ttu-id="73272-118">デザイン時の資格情報は保存されるため、入力を再度要求されることはありません。</span><span class="sxs-lookup"><span data-stu-id="73272-118">The design-time credentials are stored and you are not prompted again.</span></span>  
  
## <a name="options"></a><span data-ttu-id="73272-119">Options</span><span class="sxs-lookup"><span data-stu-id="73272-119">Options</span></span>  
 <span data-ttu-id="73272-120">**名前**</span><span class="sxs-lookup"><span data-stu-id="73272-120">**Name**</span></span>  
 <span data-ttu-id="73272-121">データ ソースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="73272-121">Type the name of the data source.</span></span> <span data-ttu-id="73272-122">データ ソース名はレポート内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="73272-122">The data source name must be unique within the report.</span></span> <span data-ttu-id="73272-123">既定では、DataSource1 または DataSource2 などの一般的な名前がデータ ソースに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="73272-123">By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.</span></span>  
  
 <span data-ttu-id="73272-124">**[共有接続を使用する]**</span><span class="sxs-lookup"><span data-stu-id="73272-124">**Use a shared connection**</span></span>  
 <span data-ttu-id="73272-125">レポート サーバーにパブリッシュされた共有データ ソースを参照する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="73272-125">Select this option to browse to a shared data source that has been published to a report server.</span></span>  
  
 <span data-ttu-id="73272-126">レポート サーバーからデータ ソースを選択した後は、レポート ビルダーによってこのレポート サーバーへの接続が維持されます。</span><span class="sxs-lookup"><span data-stu-id="73272-126">After you select a data source from a report server, Report Builder maintains a connection to this report server.</span></span>  
  
 <span data-ttu-id="73272-127">**[レポートに埋め込まれた接続を使用する]**</span><span class="sxs-lookup"><span data-stu-id="73272-127">**Use a connection embedded in my report**</span></span>  
 <span data-ttu-id="73272-128">このレポートでのみ使用されるデータ ソースを作成する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="73272-128">Select this option to create a data source that is used only by this report.</span></span>  
  
 <span data-ttu-id="73272-129">**Type**</span><span class="sxs-lookup"><span data-stu-id="73272-129">**Type**</span></span>  
 <span data-ttu-id="73272-130">データ処理拡張機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="73272-130">Select a data processing extension.</span></span> <span data-ttu-id="73272-131">一覧には、登録されているすべての拡張機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="73272-131">The list displays all registered extensions.</span></span>  
  
 <span data-ttu-id="73272-132">**接続文字列**</span><span class="sxs-lookup"><span data-stu-id="73272-132">**Connection string**</span></span>  
 <span data-ttu-id="73272-133">データ ソースの接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="73272-133">Enter a connection string for the data source.</span></span> <span data-ttu-id="73272-134">**[構築]** をクリックして、 **[接続のプロパティ]** ダイアログ ボックスで接続文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="73272-134">Click **Build** to build the connection string using the **Connection Properties** dialog box.</span></span> <span data-ttu-id="73272-135">式を編集するには、 **式** (*[fx]*) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="73272-135">Click the **Expressions** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="73272-136">**[クエリの処理時に単一のトランザクションを使用する]**</span><span class="sxs-lookup"><span data-stu-id="73272-136">**Use a single transaction when processing the queries**</span></span>  
 <span data-ttu-id="73272-137">このデータ ソースを使用するデータセットが、データベースに対する単一のトランザクションで処理されるように指定する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="73272-137">Select this option to indicate that datasets that use this data source are run in a single transaction against the database.</span></span> <span data-ttu-id="73272-138">同じデータ ソースを使用するサブレポートのトランザクションを含めるには、そのサブレポートを選択し、[プロパティ] ペインで **[MergeTransactions]** を **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="73272-138">To include transactions for subreports that use the same data source, select the subreport, and in the Properties pane, set **MergeTransactions** to **True**.</span></span>  
  
 <span data-ttu-id="73272-139">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="73272-139">**Test Connection**</span></span>  
 <span data-ttu-id="73272-140">指定された資格情報を使用してデータ ソースに接続できるかどうかを確認する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="73272-140">Click to verify that the data source connection works by using the specified credentials.</span></span> <span data-ttu-id="73272-141">接続できない場合は、資格情報と、サーバーが使用できるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73272-141">If the connection cannot be made, you need to verify your credentials and the server availability.</span></span> <span data-ttu-id="73272-142">埋め込みデータ ソースと共有データ ソースへのデータ ソース接続をテストできます。</span><span class="sxs-lookup"><span data-stu-id="73272-142">You can test data source connections for embedded and shared data sources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73272-143">参照</span><span class="sxs-lookup"><span data-stu-id="73272-143">See Also</span></span>  
 <span data-ttu-id="73272-144">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="73272-144">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="73272-145">[データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;に追加して検証する](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="73272-145">[Add and Verify a Data Connection or Data Source &#40;Report Builder and SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="73272-146">[レポートビルダーのデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="73272-146">[Data Connections, Data Sources, and Connection Strings in Report Builder](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md) </span></span>  
 <span data-ttu-id="73272-147">[[データソースのプロパティ] ダイアログボックスの [資格情報 &#40;レポートビルダー&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="73272-147">[Data Source Properties Dialog Box, Credentials &#40;Report Builder&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) </span></span>  
 [<span data-ttu-id="73272-148">レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ</span><span class="sxs-lookup"><span data-stu-id="73272-148">Report Builder Help for Dialog Boxes, Panes, and Wizards</span></span>](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
