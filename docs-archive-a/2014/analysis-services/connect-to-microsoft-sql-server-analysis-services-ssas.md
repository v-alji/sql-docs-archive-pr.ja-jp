---
title: Microsoft SQL Server Analysis Services への接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserveras.f1
ms.assetid: 7f3244ee-b690-471c-893d-68e361c2d416
author: minewiskan
ms.author: owend
ms.openlocfilehash: 984979480e3ea54c86c986fa6dd9771aaf879cb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633456"
---
# <a name="connect-to-microsoft-sql-server-analysis-services-ssas"></a><span data-ttu-id="b88da-102">[Microsoft SQL Server Analysis Service への接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b88da-102">Connect to Microsoft SQL Server Analysis Services (SSAS)</span></span>
  <span data-ttu-id="b88da-103">**テーブルのインポートウィザード**のこのページを使用すると、SharePoint でホストされている Microsoft SQL Server Analysis Services キューブまたは PowerPivot ブックからデータをインポートするための設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b88da-103">This page of the **Table Import Wizard** enables you to specify settings to import data from a Microsoft SQL Server Analysis Services cube or a PowerPivot workbook that is hosted on SharePoint.</span></span> <span data-ttu-id="b88da-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b88da-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b88da-105">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b88da-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b88da-106">このページでデータベースを選択する際には、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b88da-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="b88da-107">ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="b88da-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b88da-108">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="b88da-108">UI element list</span></span>  
 <span data-ttu-id="b88da-109">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="b88da-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="b88da-110">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b88da-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="b88da-111">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="b88da-111">This is a required field.</span></span>  
  
 <span data-ttu-id="b88da-112">**サーバー名またはファイル名**</span><span class="sxs-lookup"><span data-stu-id="b88da-112">**Server or File Name**</span></span>  
 <span data-ttu-id="b88da-113">次のいずれかを入力します。</span><span class="sxs-lookup"><span data-stu-id="b88da-113">Enter one of the following:</span></span>  
  
-   <span data-ttu-id="b88da-114">SQL Server Analysis Services サーバーが接続に使用する名前または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="b88da-114">Type the name or IP address of the SQL Server Analysis Services server to connect to.</span></span>  
  
     <span data-ttu-id="b88da-115">ピリオド (.)、(local)、または localhost を使用すると、ローカル サーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b88da-115">You can use a period (.), (local), or localhost to indicate the local server.</span></span>  
  
-   <span data-ttu-id="b88da-116">SharePoint にパブリッシュする PowerPivot ブックの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="b88da-116">Type the URL of a PowerPivot workbook that is published to SharePoint.</span></span>  
  
 <span data-ttu-id="b88da-117">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="b88da-117">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="b88da-118">SQL Server Analysis Services サーバーへの接続に Windows 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b88da-118">Specify whether Windows Authentication is used to connect to a SQL Server Analysis Services server.</span></span>  
  
 <span data-ttu-id="b88da-119">Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="b88da-119">Windows Authentication mode enables a user to connect through a Windows user account.</span></span> <span data-ttu-id="b88da-120">可能であれば、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="b88da-120">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="b88da-121">Windows 認証を使用した場合、[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際に、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b88da-121">When Windows Authentication is used, the credentials of the current user are used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="b88da-122">データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b88da-122">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="b88da-123">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="b88da-123">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="b88da-124">SQL Server Analysis Services サーバーへの接続に SQL Server 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b88da-124">Specify whether SQL Server Authentication is used to connect to a SQL Server Analysis Services server.</span></span>  
  
 <span data-ttu-id="b88da-125">SQL Server 認証の場合、SQL Server は、SQL Server ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。</span><span class="sxs-lookup"><span data-stu-id="b88da-125">With SQL Server Authentication, SQL Server performs the authentication itself by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span>  
  
 <span data-ttu-id="b88da-126">SQL Server 認証は、データ ソースの接続文字列を構築するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b88da-126">SQL Server Authentication is used to construct the connection string for the data source.</span></span> <span data-ttu-id="b88da-127">[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b88da-127">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="b88da-128">データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b88da-128">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="b88da-129">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="b88da-129">**User name**</span></span>  
 <span data-ttu-id="b88da-130">データベース接続に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b88da-130">Specify a user name for the database connection.</span></span> <span data-ttu-id="b88da-131">このオプションは、Windows 認証を使用した接続を選択した場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b88da-131">This option is only available if you have selected to connect using Windows Authentication.</span></span>  
  
 <span data-ttu-id="b88da-132">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="b88da-132">**Password**</span></span>  
 <span data-ttu-id="b88da-133">データベース接続に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b88da-133">Specify a password for the database connection.</span></span> <span data-ttu-id="b88da-134">このオプションは、SQL Server 認証を使用した接続を選択した場合にのみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="b88da-134">This option is only editable if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b88da-135">**パスワードを保存する**</span><span class="sxs-lookup"><span data-stu-id="b88da-135">**Save my password**</span></span>  
 <span data-ttu-id="b88da-136">**[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b88da-136">Specify whether the password you have entered in the **Password** box is stored.</span></span> <span data-ttu-id="b88da-137">このオプションは、SQL Server 認証を使用した接続を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b88da-137">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b88da-138">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="b88da-138">**Database name**</span></span>  
 <span data-ttu-id="b88da-139">データベースを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="b88da-139">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="b88da-140">**詳細**</span><span class="sxs-lookup"><span data-stu-id="b88da-140">**Advanced**</span></span>  
 <span data-ttu-id="b88da-141">**[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b88da-141">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="b88da-142">詳細については、「[[詳細プロパティの設定] (SSAS)](set-advanced-properties-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b88da-142">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="b88da-143">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="b88da-143">**Test Connection**</span></span>  
 <span data-ttu-id="b88da-144">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="b88da-144">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="b88da-145">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b88da-145">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
