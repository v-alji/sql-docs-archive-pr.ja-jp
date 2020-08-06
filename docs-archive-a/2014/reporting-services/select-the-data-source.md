---
title: データソースを選択してください |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 641aa04f7fe658123aa21cc1bd21264ec0ee28ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713754"
---
# <a name="select-the-data-source"></a><span data-ttu-id="778c2-102">データ ソースを選択します</span><span class="sxs-lookup"><span data-stu-id="778c2-102">Select the Data Source</span></span>
  <span data-ttu-id="778c2-103">レポート ウィザードのこのページでは、レポートのデータ ソースを定義できます。</span><span class="sxs-lookup"><span data-stu-id="778c2-103">Use this page of the Report Wizard to define a data source for the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="778c2-104">Options</span><span class="sxs-lookup"><span data-stu-id="778c2-104">Options</span></span>  
 <span data-ttu-id="778c2-105">**共有データソース**</span><span class="sxs-lookup"><span data-stu-id="778c2-105">**Shared data source**</span></span>  
 <span data-ttu-id="778c2-106">使用するデータ ソース接続情報が既に指定されている、定義済みの共有データ ソースを使用する場合に、 **[共有データ ソース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="778c2-106">Select **Shared Data Source** to use a predefined shared data source that already has the data source connection information you want to use.</span></span> <span data-ttu-id="778c2-107">一覧に、プロジェクトに含まれているすべての共有データ ソースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="778c2-107">The list contains all shared data sources that are included in the project.</span></span>  
  
 <span data-ttu-id="778c2-108">**新しいデータ ソース**</span><span class="sxs-lookup"><span data-stu-id="778c2-108">**New data source**</span></span>  
 <span data-ttu-id="778c2-109">新しいデータ ソースを定義する場合は **[新しいデータ ソース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="778c2-109">Select **New data source** to define a new data source.</span></span> <span data-ttu-id="778c2-110">データ ソースの情報は現在のレポートでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="778c2-110">The data source information will be used only with the current report.</span></span>  
  
 <span data-ttu-id="778c2-111">**名前**</span><span class="sxs-lookup"><span data-stu-id="778c2-111">**Name**</span></span>  
 <span data-ttu-id="778c2-112">データ ソースに対する接続の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="778c2-112">Type a name for the connection to the data source.</span></span> <span data-ttu-id="778c2-113">データ ソース名はレポート内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="778c2-113">The data source name must be unique within the report.</span></span>  
  
 <span data-ttu-id="778c2-114">**Type**</span><span class="sxs-lookup"><span data-stu-id="778c2-114">**Type**</span></span>  
 <span data-ttu-id="778c2-115">使用しているデータソースの種類を選択します (たとえば、データベースを使用している場合は、を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 選択し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ます)。</span><span class="sxs-lookup"><span data-stu-id="778c2-115">Select the type of data source you are using (for example, if you are using a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, choose [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).</span></span>  
  
 <span data-ttu-id="778c2-116">**接続文字列**</span><span class="sxs-lookup"><span data-stu-id="778c2-116">**Connection string**</span></span>  
 <span data-ttu-id="778c2-117">データ ソースの接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="778c2-117">Type a connection string for the data source.</span></span> <span data-ttu-id="778c2-118">接続文字列の詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="778c2-118">For more information about connection strings, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="778c2-119">**[編集]** をクリックし、 **[接続プロパティ]** ダイアログ ボックスを使用してデータ ソース サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="778c2-119">Click **Edit** to specify the data source server in the **Connection Properties** dialog box.</span></span> <span data-ttu-id="778c2-120">ローカルまたはリモートのデータ ソースを指定できます。</span><span class="sxs-lookup"><span data-stu-id="778c2-120">You can specify a local or remote data source.</span></span>  
  
 <span data-ttu-id="778c2-121">**[資格情報]** をクリックして、データベースの資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="778c2-121">Click **Credentials** to supply database credentials.</span></span> <span data-ttu-id="778c2-122">少なくとも、レポートをデザインする目的でデータ ソースに接続するために、十分な資格情報を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="778c2-122">At a minimum, the credentials you specify must be sufficient for you to connect to the data source for report design purposes.</span></span> <span data-ttu-id="778c2-123">レポートがレポート サーバーに置かれている場合、データベース資格情報を使用してレポートのすべてのユーザーに対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="778c2-123">When the report is deployed on a report server, the database credentials must accommodate all users of the report.</span></span> <span data-ttu-id="778c2-124">たとえば、すべてのレポート ユーザーが各自の資格情報を使用してデータ ソースに接続するようにするには、 **[Windows 認証 (統合セキュリティ) を使用する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="778c2-124">For example, if you want all report users to connect to the data source using their credentials, choose **Use Windows Authentication (Integrated Security)**.</span></span> <span data-ttu-id="778c2-125">指定する資格情報は、データ ソースで有効である必要があります。そのため、Windows 認証を選択する場合には、そのレポートを実行するすべてのユーザー アカウントによるデータ ソースへの接続が許可されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="778c2-125">The credentials you specify must be valid for the data source, so if you choose Windows Authentication, be sure that the data source accepts connections from all user accounts that will be running the report.</span></span> <span data-ttu-id="778c2-126">データベース資格情報は、レポートとは別に管理できます。</span><span class="sxs-lookup"><span data-stu-id="778c2-126">Database credentials can be managed separately from the report.</span></span> <span data-ttu-id="778c2-127">詳細については、「 [レポートのデータ ソースの管理](report-data/manage-report-data-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="778c2-127">For more information, see [Manage Report Data Sources](report-data/manage-report-data-sources.md).</span></span>  
  
 <span data-ttu-id="778c2-128">**[共有データ ソースとして使用する]**</span><span class="sxs-lookup"><span data-stu-id="778c2-128">**Make this a shared data source**</span></span>  
 <span data-ttu-id="778c2-129">データ ソースをレポートではなく、共有データ ソースとしてプロジェクトに保存します。</span><span class="sxs-lookup"><span data-stu-id="778c2-129">Select this option to store the data source in the project as a shared data source, instead of in the report.</span></span> <span data-ttu-id="778c2-130">こうすることで、そのデータ ソースをプロジェクト内の他のレポートにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="778c2-130">That way, you can use it as the data source for other reports in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="778c2-131">参照</span><span class="sxs-lookup"><span data-stu-id="778c2-131">See Also</span></span>  
 <span data-ttu-id="778c2-132">[埋め込みデータ接続または共有データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="778c2-132">[Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="778c2-133">[レポート データ ソースに関する資格情報と接続情報を指定する](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span><span class="sxs-lookup"><span data-stu-id="778c2-133">[Specify Credential and Connection Information for Report Data Sources](report-data/specify-credential-and-connection-information-for-report-data-sources.md) </span></span>  
 <span data-ttu-id="778c2-134">[レポートサーバーの Reporting Services](../../2014/reporting-services/reporting-services-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="778c2-134">[Reporting Services Report Server](../../2014/reporting-services/reporting-services-report-server.md) </span></span>  
 <span data-ttu-id="778c2-135">[RSReportDesigner 構成ファイル](report-server/rsreportdesigner-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="778c2-135">[RSReportDesigner Configuration File](report-server/rsreportdesigner-configuration-file.md) </span></span>  
 <span data-ttu-id="778c2-136">[Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="778c2-136">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="778c2-137">レポート ウィザードのヘルプ</span><span class="sxs-lookup"><span data-stu-id="778c2-137">Report Wizard Help</span></span>](../../2014/reporting-services/report-wizard-help.md)  
  
  
