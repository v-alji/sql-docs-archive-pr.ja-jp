---
title: 参照データを使用する DQS の構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.rds.f1
- sql12.dqs.administration.rdsconfiguration.f1
- sql12.dqs.administration.configuration.createDirectRDS.f1
ms.assetid: fae745e7-57a7-4cbc-8979-56ea8e392e4e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 670e984c2afabb70dece75d94701d7a3a03c95bf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712413"
---
# <a name="configure-dqs-to-use-reference-data"></a><span data-ttu-id="a7a08-102">参照データを使用する DQS の構成</span><span class="sxs-lookup"><span data-stu-id="a7a08-102">Configure DQS to Use Reference Data</span></span>
  <span data-ttu-id="a7a08-103">このトピックでは、データのクレンジングに参照データを使用するように [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-103">This topic describes how to configure [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) to use reference data for cleansing your data.</span></span> <span data-ttu-id="a7a08-104">Azure Marketplace またはダイレクトオンラインサードパーティ参照データプロバイダーから参照データを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a7a08-104">You could either use reference data from Azure Marketplace or from direct online third-party reference data providers.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="a7a08-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="a7a08-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="a7a08-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="a7a08-106">Prerequisites</span></span>  
 <span data-ttu-id="a7a08-107">Marketplace の参照データを使用するには、Marketplace の有効なアカウント キーを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7a08-107">To use reference data from Marketplace, you must have a valid Marketplace account key.</span></span> <span data-ttu-id="a7a08-108">Marketplace アカウントキーの作成の詳細については、「[アカウントの作成](https://go.microsoft.com/fwlink/?LinkId=212936)」 (を参照してください https://go.microsoft.com/fwlink/?LinkId=212936) 。</span><span class="sxs-lookup"><span data-stu-id="a7a08-108">For detailed information about creating a Marketplace account key, see [Create Your Account](https://go.microsoft.com/fwlink/?LinkId=212936) (https://go.microsoft.com/fwlink/?LinkId=212936).</span></span> <span data-ttu-id="a7a08-109">Marketplace のアカウント キーは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 内で作成することもできます。 **のホーム画面で、** [管理] **の下の** [構成] [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] をクリックし、 **[参照データ]** タブの **[DataMarket のアカウント ID を作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7a08-109">You can also create a Marketplace account key from within [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] by clicking **Configuration** under **Administration** in the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, and then clicking **Create a DataMarket Account ID** under the **Reference Data** tab.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a7a08-110">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a7a08-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a7a08-111">Permissions</span><span class="sxs-lookup"><span data-stu-id="a7a08-111">Permissions</span></span>  
 <span data-ttu-id="a7a08-112">DQS で参照データ サービス設定を構成するには、DQS_MAIN データベースの dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="a7a08-112">You must have the dqs_administrator role on the DQS_MAIN database to configure reference data service settings in DQS.</span></span>  
  
##  <a name="configure-dqs-to-use-reference-data-from-marketplace"></a><a name="Marketplace"></a> <span data-ttu-id="a7a08-113">Marketplace の参照データを使用する DQS の構成</span><span class="sxs-lookup"><span data-stu-id="a7a08-113">Configure DQS to Use Reference Data from Marketplace</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="a7a08-114">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-114">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="a7a08-115">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[管理]** の下の **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7a08-115">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Administration**, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="a7a08-116">組織でインターネットへの接続にプロキシ サーバーを使用している場合には、 **[参照データ]** タブの **[ネットワークの設定]** の下の **[プロキシ サーバー]** と **[ポート]** ボックスに適切な値を入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-116">In the **Reference Data** tab, under the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** boxes if you or your organization uses proxy server to connect to the Internet.</span></span>  
  
4.  <span data-ttu-id="a7a08-117">**[DataMarket のアカウント ID]** ボックスに Marketplace のアカウント キーを指定し、 **[DataMarket のアカウント ID を検証]** アイコンをクリックしてアカウント キーを検証します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-117">Specify the Marketplace account key in the **DataMarket Account ID** box, and click the **Validate DataMarket Account ID** icon to validate the account key.</span></span> <span data-ttu-id="a7a08-118">指定した Marketplace アカウント キーが有効かどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a08-118">A message appears to display whether the specified Marketplace account key is valid.</span></span>  
  
 <span data-ttu-id="a7a08-119">指定した Marketplace のアカウント キーによってサブスクライブされた Marketplace の参照データ サービスを、DQS で使用する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="a7a08-119">You are now ready to use the reference data services from Marketplace in DQS that are subscribed for the specified Marketplace account key.</span></span>  
  
##  <a name="configure-dqs-to-use-reference-data-from-direct-online-third-party-reference-data-providers"></a><a name="ThirdParty"></a> <span data-ttu-id="a7a08-120">ダイレクト オンライン サード パーティ参照データ プロバイダーの参照データを使用する DQS の構成</span><span class="sxs-lookup"><span data-stu-id="a7a08-120">Configure DQS to Use Reference Data from Direct Online Third-Party Reference Data Providers</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="a7a08-121">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="a7a08-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で、 **[管理]** の下の **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7a08-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, under **Administration**, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="a7a08-123">組織でインターネットへの接続にプロキシ サーバーを使用している場合には、 **[参照データ]** タブの **[ネットワークの設定]** の下の **[プロキシ サーバー]** と **[ポート]** ボックスに適切な値を入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-123">In the **Reference Data** tab, under the **Network Settings** area, type appropriate values in the **Proxy Server** and **Port** boxes if you or your organization uses proxy server to connect to the Internet.</span></span>  
  
4.  <span data-ttu-id="a7a08-124">**[ダイレクト オンライン サード パーティの参照データ サービス プロバイダーの設定]** 領域の **[新しい参照データ サービス プロバイダーの追加]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a7a08-124">In the **Direct Online 3rd Party Reference Data Service Settings** area, click the **Add new reference data service provider** icon.</span></span>  
  
5.  <span data-ttu-id="a7a08-125">**[新しいダイレクト オンライン サード パーティの参照データ サービス プロバイダーを作成]** ダイアログ ボックスで次の詳細情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-125">In the **Create New Direct Online 3rd Party Reference Data Service Provider** dialog box, specify the following details:</span></span>  
  
    1.  <span data-ttu-id="a7a08-126">**[名前]** ボックスに、新しいダイレクト参照データ サービス プロバイダーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-126">In the **Name** box, type a name of the new direct reference data service provider.</span></span>  
  
    2.  <span data-ttu-id="a7a08-127">(省略可) **[説明]** ボックスに、新しいダイレクト参照データ サービス プロバイダーの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-127">(Optional) In the **Description** box, type a description of the new direct reference data service provider.</span></span>  
  
    3.  <span data-ttu-id="a7a08-128">**[カテゴリ]** ボックスに、新しいダイレクト参照データ サービス プロバイダーによって提供されるデータのカテゴリを入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-128">In the **Category** box, type the category of the data provided by the new direct reference data service provider.</span></span>  
  
    4.  <span data-ttu-id="a7a08-129">[スキーマ] ボックスに、ダイレクト参照データ サービス プロバイダーが使用するフィールドの文字列 (列名) を定義するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-129">In the Schema box, specify the schema that defines the string of fields (column names) to be used from the direct reference data service provider.</span></span> <span data-ttu-id="a7a08-130">フィールド名にスペースを含めることはできず、フィールドはコンマで区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7a08-130">A field name should not contain a space, and the fields should be separated by commas.</span></span> <span data-ttu-id="a7a08-131">(例: `FirstName, LastName, City, State`)。</span><span class="sxs-lookup"><span data-stu-id="a7a08-131">For example: `FirstName, LastName, City, State`.</span></span>  
  
    5.  <span data-ttu-id="a7a08-132">**[URI]** ボックスに、ダイレクト参照データ サービス プロバイダーの URI を入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-132">In the **URI** box, type the URI of the direct reference data service provider.</span></span> <span data-ttu-id="a7a08-133">DQS ではセキュリティで保護された URI ("https://" で始まるアドレス) だけが使用できます。</span><span class="sxs-lookup"><span data-stu-id="a7a08-133">Only secure URIs (address starting with "https://") are allowed in DQS.</span></span>  
  
    6.  <span data-ttu-id="a7a08-134">**[最大バッチ サイズ]** ボックスに、クレンジングのために参照データ サービス プロバイダーに送られるバッチごとのレコードの最大数を入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-134">In the **Max Batch Size** box, type the maximum number of records per batch that will be sent to the reference data service provider for cleansing.</span></span> <span data-ttu-id="a7a08-135">クレンジング アクティビティ用に、最大で 100 のバッチごとのレコード数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7a08-135">A maximum of 100 records per batch can be specified for the cleansing activity.</span></span>  
  
    7.  <span data-ttu-id="a7a08-136">**[アカウント ID]** ボックスに、参照データ サービス プロバイダーのサブスクライバーのアカウント ID を入力します。</span><span class="sxs-lookup"><span data-stu-id="a7a08-136">In the **Account ID** box, type the account ID of the subscriber with the reference data service provider.</span></span>  
  
6.  <span data-ttu-id="a7a08-137">**[OK]** をクリックしてデータを保存し、 **[新しいダイレクト オンライン サード パーティの参照データ サービス プロバイダーを作成]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a7a08-137">Click **OK** to save the data, and close the **Create New Direct Online 3rd Party Reference Data Service Provider** dialog box.</span></span> <span data-ttu-id="a7a08-138">新しく追加されたダイレクト オンライン サード パーティの参照データ プロバイダーが DQS の **[ダイレクト参照データ サービス プロバイダー グリッド]** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a7a08-138">The newly added direct online third party reference data provider becomes available in the **Direct Reference Data Service Providers Grid** in DQS.</span></span>  
  
 <span data-ttu-id="a7a08-139">新しく構成されたダイレクト オンライン サード パーティ参照データ サービス プロバイダーの参照データ サービスを DQS で使用する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="a7a08-139">You are now ready to use the reference data services from the newly configured direct online third-party reference data service provider in DQS.</span></span>  
  
##  <a name="follow-up-after-configuring-dqs-to-use-reference-data"></a><a name="FollowUp"></a><span data-ttu-id="a7a08-140">補足情報: 参照データを使用するように DQS を構成した後</span><span class="sxs-lookup"><span data-stu-id="a7a08-140">Follow Up: After Configuring DQS to use Reference Data</span></span>  
 <span data-ttu-id="a7a08-141">必要なナレッジ ベース ドメインを、構成したデータ プロバイダーから提供される参照データにマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7a08-141">You must now map the required knowledge base domains to the reference data available from the data providers you just configured.</span></span> <span data-ttu-id="a7a08-142">これを行うには、「[参照データへのドメインまたは複合ドメインのアタッチ](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7a08-142">To do so, see [Attach a Domain or Composite Domain to Reference Data](../../2014/data-quality-services/attach-a-domain-or-composite-domain-to-reference-data.md).</span></span>  
  
  
