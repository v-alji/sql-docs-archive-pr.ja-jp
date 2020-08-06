---
title: Microsoft SQL Server データベースへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connsqlserverdb.f1
ms.assetid: 6ebfe029-dbba-4f0d-a556-328e79ef629f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 64267cd65836cf8e6c8d8b26a177de595894b601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633479"
---
# <a name="connect-to-a-microsoft-sql-server-database-ssas"></a><span data-ttu-id="b8a8b-102">[Microsoft SQL Server データベースへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b8a8b-102">Connect to a Microsoft SQL Server Database (SSAS)</span></span>
  <span data-ttu-id="b8a8b-103">**テーブルのインポート ウィザード** のこのページを使用すると、Microsoft SQL Server データベースに接続するための設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft SQL Server database.</span></span> <span data-ttu-id="b8a8b-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b8a8b-105">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8a8b-106">このページでデータベースを選択する際には、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="b8a8b-107">ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b8a8b-108">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="b8a8b-108">UI element list</span></span>  
 <span data-ttu-id="b8a8b-109">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="b8a8b-110">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="b8a8b-111">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-111">This is a required field.</span></span>  
  
 <span data-ttu-id="b8a8b-112">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-112">**Server name**</span></span>  
 <span data-ttu-id="b8a8b-113">接続する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前を選択するか、名前または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-113">Select the name, or type the name or IP address, of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance to connect to.</span></span>  
  
 <span data-ttu-id="b8a8b-114">ピリオド (.)、(local)、または localhost を使用すると、ローカル サーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-114">You can use a period (.), (local), or localhost to indicate the local server.</span></span>  
  
 <span data-ttu-id="b8a8b-115">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-115">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="b8a8b-116">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスへの接続に Windows 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-116">Specify whether Windows Authentication is used to connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b8a8b-117">Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-117">Windows Authentication mode enables a user to connect by using a Windows user account.</span></span> <span data-ttu-id="b8a8b-118">可能であれば、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-118">Whenever possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="b8a8b-119">Windows 認証を使用した場合、[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際に、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-119">When Windows Authentication is used, the credentials of the current user are used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="b8a8b-120">データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-120">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation information page are used instead.</span></span>  
  
 <span data-ttu-id="b8a8b-121">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-121">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="b8a8b-122">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスへの接続に SQL Server 認証を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-122">Specify whether SQL Server Authentication is used to connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b8a8b-123">SQL Server 認証の場合、SQL Server は、SQL Server ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-123">With SQL Server Authentication, SQL Server performs the authentication itself by checking to see if a SQL Server login account has been set up and if the specified password matches the one previously recorded.</span></span>  
  
 <span data-ttu-id="b8a8b-124">SQL Server 認証は、データ ソースの接続文字列を構築するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-124">SQL Server Authentication is used to construct the connection string for the data source.</span></span> <span data-ttu-id="b8a8b-125">[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-125">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="b8a8b-126">データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-126">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="b8a8b-127">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-127">**User name**</span></span>  
 <span data-ttu-id="b8a8b-128">データベース接続に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-128">Specify a user name for the database connection.</span></span> <span data-ttu-id="b8a8b-129">このオプションは、SQL Server 認証を使用した接続を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-129">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b8a8b-130">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-130">**Password**</span></span>  
 <span data-ttu-id="b8a8b-131">データベース接続に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-131">Specify a password for the database connection.</span></span> <span data-ttu-id="b8a8b-132">このオプションは、SQL Server 認証を使用した接続を選択した場合にのみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-132">This option is only editable if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b8a8b-133">**パスワードを保存する**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-133">**Save my password**</span></span>  
 <span data-ttu-id="b8a8b-134">**[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-134">Specify whether the password you have entered in the **Password** box is stored.</span></span> <span data-ttu-id="b8a8b-135">このオプションは、SQL Server 認証を使用した接続を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-135">This option is only available if you have selected to connect using SQL Server Authentication.</span></span>  
  
 <span data-ttu-id="b8a8b-136">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-136">**Database name**</span></span>  
 <span data-ttu-id="b8a8b-137">データベースを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-137">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="b8a8b-138">**詳細**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-138">**Advanced**</span></span>  
 <span data-ttu-id="b8a8b-139">**[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-139">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="b8a8b-140">詳細については、「[[詳細プロパティの設定] (SSAS)](set-advanced-properties-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-140">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="b8a8b-141">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="b8a8b-141">**Test Connection**</span></span>  
 <span data-ttu-id="b8a8b-142">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-142">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="b8a8b-143">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8a8b-143">A message is displayed indicating whether the connection was successful.</span></span>  
  
  
