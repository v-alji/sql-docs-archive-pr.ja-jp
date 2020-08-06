---
title: Informix データベースへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conninformixdb.f1
ms.assetid: b01d537c-1c04-4d7d-9146-051c249b08e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 35c7263ce9b0432802cd24b6df9165151b279d83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633473"
---
# <a name="connect-to-an-informix-database-ssas"></a><span data-ttu-id="73196-102">[Informix データベースへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="73196-102">Connect to an Informix Database (SSAS)</span></span>
  <span data-ttu-id="73196-103">**テーブルのインポート ウィザード** のこのページを使用すると、Informix データベースに接続するための設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="73196-103">This page of the **Table Import Wizard** enables you to specify settings to connect to an Informix database.</span></span> <span data-ttu-id="73196-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="73196-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="73196-105">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="73196-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="73196-106">このページでデータベースを選択する際には、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="73196-106">The credentials of the current user are used when selecting a database in this page.</span></span> <span data-ttu-id="73196-107">ただし、[権限借用情報] ページで指定されたユーザーに、選択したデータベースの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="73196-107">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected database.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="73196-108">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="73196-108">UI element list</span></span>  
 <span data-ttu-id="73196-109">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="73196-109">**Friendly connection name**</span></span>  
 <span data-ttu-id="73196-110">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="73196-110">Type a unique name for this data source connection.</span></span> <span data-ttu-id="73196-111">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="73196-111">This is a required field.</span></span>  
  
 <span data-ttu-id="73196-112">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="73196-112">**Server name**</span></span>  
 <span data-ttu-id="73196-113">接続するサーバー インスタンスの名前を入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="73196-113">Type or select the name of the server instance to connect to.</span></span>  
  
 <span data-ttu-id="73196-114">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="73196-114">**User name**</span></span>  
 <span data-ttu-id="73196-115">データベース接続に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="73196-115">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="73196-116">このユーザー名は、データ ソースの接続文字列を構築するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="73196-116">This user name is used when constructing the connection string for the data source.</span></span> <span data-ttu-id="73196-117">[テーブルのプロパティ] ウィンドウおよびインポート ウィザードでデータのプレビューまたはフィルター処理を行う際も、これらの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="73196-117">These credentials are also used when previewing and filtering data in the Table Properties window and in the Import Wizard.</span></span> <span data-ttu-id="73196-118">データをインポートまたは更新する際には、これらの資格情報は使用されず、[権限借用情報] ページで指定された Windows の資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="73196-118">These credentials are not used to import or refresh data; the Windows credentials specified on the Impersonation Information page are used instead.</span></span>  
  
 <span data-ttu-id="73196-119">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="73196-119">**Password**</span></span>  
 <span data-ttu-id="73196-120">データベース接続に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="73196-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="73196-121">**パスワードを保存する**</span><span class="sxs-lookup"><span data-stu-id="73196-121">**Save my password**</span></span>  
 <span data-ttu-id="73196-122">**[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="73196-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="73196-123">**詳細**</span><span class="sxs-lookup"><span data-stu-id="73196-123">**Advanced**</span></span>  
 <span data-ttu-id="73196-124">**[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="73196-124">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span> <span data-ttu-id="73196-125">詳細については、「[[詳細プロパティの設定] (SSAS)](set-advanced-properties-ssas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73196-125">For more information, see [Set Advanced Properties &#40;SSAS&#41;](set-advanced-properties-ssas.md).</span></span>  
  
 <span data-ttu-id="73196-126">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="73196-126">**Test Connection**</span></span>  
 <span data-ttu-id="73196-127">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="73196-127">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="73196-128">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="73196-128">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
