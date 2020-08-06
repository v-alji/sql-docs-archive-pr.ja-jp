---
title: Microsoft SQL Server Parallel Data Warehouse への接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlparadatawh.f1
ms.assetid: 98c879ee-7257-40c9-bc85-6766bd3b4885
author: minewiskan
ms.author: owend
ms.openlocfilehash: 082d6b34077d1bde11b527d3bfff907073eed16e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633472"
---
# <a name="connect-to-a-microsoft-sql-server-parallel-data-warehouse-ssas"></a><span data-ttu-id="5567c-102">[Microsoft SQL Server 並列データ ウェアハウスへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="5567c-102">Connect to a Microsoft SQL Server Parallel Data Warehouse (SSAS)</span></span>
  <span data-ttu-id="5567c-103">**テーブルのインポート ウィザード** のこのページを使用すると、Microsoft SQL Server 並列データ ウェアハウス (PDW) に接続するための設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5567c-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft SQL Server Parallel Data Warehouse (PDW).</span></span> <span data-ttu-id="5567c-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5567c-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="5567c-105">SQL Server PDW は、非常にスケーラブルなアプライアンスであり、超並列処理によって低コストで優れたパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5567c-105">SQL Server PDW is a highly scalable appliance that delivers performance at low cost through massively parallel processing.</span></span> <span data-ttu-id="5567c-106">SQL Server PDW の詳細については、Web サイト「 [SQL Server 2008 R2 並列データ ウェアハウス](https://go.microsoft.com/fwlink/?LinkId=150895)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5567c-106">For more information about SQL Server PDW, see the web site [SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).</span></span> <span data-ttu-id="5567c-107">データ ウェアハウスには、SQL Server 認証を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="5567c-107">You connect to the data warehouse by using SQL Server Authentication.</span></span> <span data-ttu-id="5567c-108">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5567c-108">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5567c-109">このページでデータベースを選択する際には、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5567c-109">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="5567c-110">ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="5567c-110">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="5567c-111">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="5567c-111">UI element list</span></span>  
 <span data-ttu-id="5567c-112">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="5567c-112">**Friendly connection name**</span></span>  
 <span data-ttu-id="5567c-113">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="5567c-113">Type a unique name for this data source connection.</span></span> <span data-ttu-id="5567c-114">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="5567c-114">This is a required field.</span></span>  
  
 <span data-ttu-id="5567c-115">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="5567c-115">**Server name**</span></span>  
 <span data-ttu-id="5567c-116">接続するサーバーの名前または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="5567c-116">Type the name, or IP address, of the server to connect to.</span></span>  
  
 <span data-ttu-id="5567c-117">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="5567c-117">**User name**</span></span>  
 <span data-ttu-id="5567c-118">データベース接続に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5567c-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="5567c-119">このユーザー名は、データ ソースの接続文字列を構築するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="5567c-119">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="5567c-120">[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5567c-120">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="5567c-121">データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5567c-121">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="5567c-122">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="5567c-122">**Password**</span></span>  
 <span data-ttu-id="5567c-123">データベース接続に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5567c-123">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="5567c-124">**パスワードを保存する**</span><span class="sxs-lookup"><span data-stu-id="5567c-124">**Save my password**</span></span>  
 <span data-ttu-id="5567c-125">**[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5567c-125">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="5567c-126">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="5567c-126">**Database name**</span></span>  
 <span data-ttu-id="5567c-127">データベースを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="5567c-127">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="5567c-128">**詳細**</span><span class="sxs-lookup"><span data-stu-id="5567c-128">**Advanced**</span></span>  
 <span data-ttu-id="5567c-129">**[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="5567c-129">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="5567c-130">詳細については、「[[詳細プロパティの設定] (SSAS)](set-advanced-properties-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5567c-130">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="5567c-131">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="5567c-131">**Test Connection**</span></span>  
 <span data-ttu-id="5567c-132">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="5567c-132">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="5567c-133">メッセージが表示され、接続に成功したかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="5567c-133">A message displays and indicates whether the connection is successful.</span></span>  
  
  
