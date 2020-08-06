---
title: Microsoft Access データベースへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connaccessdb.f1
ms.assetid: 9fa81839-dd8b-41d3-915e-c774a707ed53
author: minewiskan
ms.author: owend
ms.openlocfilehash: fbb180a754b6bc276d588997117eb84fd1a5a873
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633480"
---
# <a name="connect-to-a-microsoft-access-database-ssas"></a><span data-ttu-id="46850-102">[Microsoft Access データベースへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="46850-102">Connect to a Microsoft Access Database (SSAS)</span></span>
  <span data-ttu-id="46850-103">**テーブルのインポート ウィザード** のこのページを使用すると、Microsoft Access データベースに接続するための設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="46850-103">This page of the **Table Import Wizard** enables you to specify settings to connect to a Microsoft Access database.</span></span> <span data-ttu-id="46850-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46850-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="46850-105">Microsoft Access データベースに接続するには、適切な ACE プロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="46850-105">To connect to a Microsoft Access database, you must have the appropriate ACE provider installed on your computer.</span></span> <span data-ttu-id="46850-106">詳細については、「[サポートされているデータ ソース &#40;SSAS テーブル&#41;](tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46850-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46850-107">このページでファイルを選択する際には、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="46850-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="46850-108">ただし、[権限借用情報] ページで指定されたユーザーに、選択したファイルの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="46850-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="46850-109">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="46850-109">UI element list</span></span>  
 <span data-ttu-id="46850-110">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="46850-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="46850-111">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="46850-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="46850-112">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="46850-112">This is a required field.</span></span>  
  
 <span data-ttu-id="46850-113">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="46850-113">**Database name**</span></span>  
 <span data-ttu-id="46850-114">Microsoft Access データベース ファイルの完全なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="46850-114">Specify the full path for a Microsoft Access database file.</span></span>  
  
 <span data-ttu-id="46850-115">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="46850-115">**Browse**</span></span>  
 <span data-ttu-id="46850-116">使用可能な Microsoft Access データベース ファイルがある場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="46850-116">Navigate to a location where a Microsoft Access database file is available.</span></span>  
  
 <span data-ttu-id="46850-117">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="46850-117">**User name**</span></span>  
 <span data-ttu-id="46850-118">データベース接続に使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="46850-118">Specify a user name for the database connection.</span></span>  
  
 <span data-ttu-id="46850-119">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="46850-119">**Password**</span></span>  
 <span data-ttu-id="46850-120">データベース接続に使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="46850-120">Specify a password for the database connection.</span></span>  
  
 <span data-ttu-id="46850-121">**パスワードを保存する**</span><span class="sxs-lookup"><span data-stu-id="46850-121">**Save my password**</span></span>  
 <span data-ttu-id="46850-122">**[パスワード]** ボックスに入力したパスワードを保存するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="46850-122">Specify whether the password you have entered in the **Password** box is stored.</span></span>  
  
 <span data-ttu-id="46850-123">**詳細**</span><span class="sxs-lookup"><span data-stu-id="46850-123">**Advanced**</span></span>  
 <span data-ttu-id="46850-124">**[詳細プロパティの設定]** ダイアログ ボックスを使用して追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="46850-124">Set additional connection properties by using the **Set Advanced Properties** dialog box.</span></span>  
  
 <span data-ttu-id="46850-125">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="46850-125">**Test Connection**</span></span>  
 <span data-ttu-id="46850-126">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="46850-126">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="46850-127">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="46850-127">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
