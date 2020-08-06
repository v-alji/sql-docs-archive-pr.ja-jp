---
title: Azure SQL Database への接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlazure.f1
ms.assetid: 4e0344e9-1822-4698-ad22-05f1f341ced7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 91ae6f0f5ab95d3013b6348bd43ddb746fff1c22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633469"
---
# <a name="connect-to-an-azure-sql-database-ssas"></a><span data-ttu-id="38383-102">Azure SQL データベースへの接続 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="38383-102">Connect to an Azure SQL Database (SSAS)</span></span>
  <span data-ttu-id="38383-103">**テーブルのインポート ウィザード** のこのページを使用すると、 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]に接続できます。</span><span class="sxs-lookup"><span data-stu-id="38383-103">This page of the **Table Import Wizard** enables you to connect to a [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)].</span></span> <span data-ttu-id="38383-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38383-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38383-105">Azure DataMarket データセットに接続している場合は、「[レポートまたはデータ フィードへの接続 (SSAS)](connect-to-a-report-or-data-feed-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38383-105">If you are connecting to an Azure DataMarket dataset, see [Connect to a Report or Data Feed &#40;SSAS&#41;](connect-to-a-report-or-data-feed-ssas.md).</span></span>  
  
 <span data-ttu-id="38383-106">[!INCLUDE[ssSDS](../includes/sssds-md.md)] は、SQL Server 認証を使用して接続するホスト型のリレーショナル データベースです。</span><span class="sxs-lookup"><span data-stu-id="38383-106">The [!INCLUDE[ssSDS](../includes/sssds-md.md)] is a hosted, relational database that you connect to by using SQL Server Authentication.</span></span> <span data-ttu-id="38383-107">[!INCLUDE[ssSDS](../includes/sssds-md.md)]の詳細については、 [SQL データベース](https://go.microsoft.com/fwlink/?LinkID=157856)の Web サイトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="38383-107">For more information about [!INCLUDE[ssSDS](../includes/sssds-md.md)], see the web site [SQL Database](https://go.microsoft.com/fwlink/?LinkID=157856).</span></span> <span data-ttu-id="38383-108">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="38383-108">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="38383-109">このページでデータベースを選択する際には、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="38383-109">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="38383-110">ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="38383-110">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="38383-111">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="38383-111">UI element list</span></span>  
 <span data-ttu-id="38383-112">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="38383-112">**Friendly connection name**</span></span>  
 <span data-ttu-id="38383-113">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="38383-113">Type a unique name for this data source connection.</span></span> <span data-ttu-id="38383-114">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="38383-114">This is a required field.</span></span>  
  
 <span data-ttu-id="38383-115">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="38383-115">**Server name**</span></span>  
 <span data-ttu-id="38383-116">接続するサーバーの名前または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="38383-116">Type the name, or IP address, of the server to connect to.</span></span>  
  
 <span data-ttu-id="38383-117">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="38383-117">**User name**</span></span>  
 <span data-ttu-id="38383-118">データベース接続に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="38383-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="38383-119">このユーザー名は、データ ソースの接続文字列を構築するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="38383-119">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="38383-120">[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="38383-120">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="38383-121">データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="38383-121">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="38383-122">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="38383-122">**Password**</span></span>  
 <span data-ttu-id="38383-123">データベース接続に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="38383-123">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="38383-124">**パスワードを保存する**</span><span class="sxs-lookup"><span data-stu-id="38383-124">**Save my password**</span></span>  
 <span data-ttu-id="38383-125">**[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="38383-125">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="38383-126">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="38383-126">**Database name**</span></span>  
 <span data-ttu-id="38383-127">データベースを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="38383-127">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="38383-128">**詳細**</span><span class="sxs-lookup"><span data-stu-id="38383-128">**Advanced**</span></span>  
 <span data-ttu-id="38383-129">**[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="38383-129">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="38383-130">詳細については、「[[詳細プロパティの設定] (SSAS)](set-advanced-properties-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38383-130">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="38383-131">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="38383-131">**Test Connection**</span></span>  
 <span data-ttu-id="38383-132">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="38383-132">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="38383-133">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="38383-133">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
