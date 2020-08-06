---
title: DB2 データベースへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndb2db.f1
ms.assetid: eeef3697-a4fd-4263-ba7e-f86afa1f46cc
author: minewiskan
ms.author: owend
ms.openlocfilehash: f36a583956c1fe75bb0a6acd827d083a6c7562f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633485"
---
# <a name="connect-to-a-db2-database-ssas"></a><span data-ttu-id="02f62-102">[DB2 データベースへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="02f62-102">Connect to a DB2 Database (SSAS)</span></span>
  <span data-ttu-id="02f62-103">**テーブルのインポート ウィザード** のこのページを使用すると、DB2 データベースに接続するための設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="02f62-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a DB2 database.</span></span> <span data-ttu-id="02f62-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="02f62-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="02f62-105">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="02f62-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02f62-106">このページでデータベースを選択する際には、指定されたユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="02f62-106">When selecting a database in this page, the credentials of the user specified are used.</span></span> <span data-ttu-id="02f62-107">ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="02f62-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="02f62-108">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="02f62-108">UI element list</span></span>  
 <span data-ttu-id="02f62-109">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="02f62-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="02f62-110">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="02f62-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="02f62-111">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="02f62-111">This is a required field.</span></span>  
  
 <span data-ttu-id="02f62-112">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="02f62-112">**Server name**</span></span>  
 <span data-ttu-id="02f62-113">接続するサーバー インスタンスを入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="02f62-113">Type or select the server instance to connect to.</span></span>  
  
 <span data-ttu-id="02f62-114">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="02f62-114">**User name**</span></span>  
 <span data-ttu-id="02f62-115">データベース接続に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="02f62-115">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="02f62-116">このユーザー名は、データ ソースの接続文字列を構築するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="02f62-116">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="02f62-117">[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="02f62-117">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="02f62-118">データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="02f62-118">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="02f62-119">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="02f62-119">**Password**</span></span>  
 <span data-ttu-id="02f62-120">データベース接続に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="02f62-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="02f62-121">**パスワードを保存する**</span><span class="sxs-lookup"><span data-stu-id="02f62-121">**Save my password**</span></span>  
 <span data-ttu-id="02f62-122">**[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="02f62-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="02f62-123">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="02f62-123">**Database name**</span></span>  
 <span data-ttu-id="02f62-124">データベースを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="02f62-124">Select a database from the list of databases.</span></span>  
  
 <span data-ttu-id="02f62-125">**[パッケージ コレクション]**</span><span class="sxs-lookup"><span data-stu-id="02f62-125">**Package Collection**</span></span>  
 <span data-ttu-id="02f62-126">DB2 パッケージのコレクションの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="02f62-126">Specify the name of the collection for the DB2 packages.</span></span> <span data-ttu-id="02f62-127">プロバイダーはパッケージを使用して SQL ステートメントを発行し、ストアド プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="02f62-127">A provider uses packages to issue SQL statements and call stored procedures.</span></span>  
  
 <span data-ttu-id="02f62-128">**[既定のスキーマ]**</span><span class="sxs-lookup"><span data-stu-id="02f62-128">**Default Schema**</span></span>  
 <span data-ttu-id="02f62-129">選択したデータベースの既定のスキーマの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="02f62-129">Specify the name of the default schema for the selected database.</span></span>  
  
 <span data-ttu-id="02f62-130">**詳細**</span><span class="sxs-lookup"><span data-stu-id="02f62-130">**Advanced**</span></span>  
 <span data-ttu-id="02f62-131">**[詳細プロパティの設定**] ダイアログボックスを使用して、追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="02f62-131">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="02f62-132">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="02f62-132">**Test Connection**</span></span>  
 <span data-ttu-id="02f62-133">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="02f62-133">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="02f62-134">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="02f62-134">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
