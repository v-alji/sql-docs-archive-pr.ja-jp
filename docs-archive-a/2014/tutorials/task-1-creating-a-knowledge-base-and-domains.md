---
title: 'タスク 1: ナレッジベースとドメインを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce1b22e3d677e831a1d518dacc1267ad0e6be236
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714926"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a><span data-ttu-id="bcaae-102">タスク 1: ナレッジ ベースとドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="bcaae-102">Task 1: Creating a Knowledge Base and Domains</span></span>
  <span data-ttu-id="bcaae-103">このタスクでは、**サプライヤー**ナレッジベースを作成し、データのクレンジングと照合データに使用されるドメインを作成して、重複部分を削除します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-103">In this task, you create the **Suppliers** knowledge base and create domains that is used for cleansing data and matching data to remove duplicates.</span></span>  
  
1.  <span data-ttu-id="bcaae-104">**Data Quality Client**を起動します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-104">Launch **Data Quality Client**.</span></span> <span data-ttu-id="bcaae-105">[**スタート**] をクリックし、[**すべてのプログラム**] をポイントし、[ **Microsoft SQL Server 2012**]、[ **Data Quality Services**]、[ **Data Quality Client**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="bcaae-105">Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2012**, click **Data Quality Services**, and then click **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="bcaae-106">[**サーバーへの接続**] ダイアログボックスで、DQS がインストールされているデータベースサーバーインスタンスを選択し、[**接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bcaae-106">In the **Connect to Server** dialog box, select the database server instance on which the DQS is installed, and click **Connect**.</span></span>  
  
     <span data-ttu-id="bcaae-107">![[サーバーへの接続] ダイアログボックス](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "[サーバーに接続] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="bcaae-107">![Connect to Server Dialog Box](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "Connect to Server Dialog Box")</span></span>  
  
3.  <span data-ttu-id="bcaae-108">Data Quality Client のホームページの [**ナレッジベース管理**] ウィンドウで、[**新しいナレッジベース**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bcaae-108">In the Data Quality Client home page, in the **Knowledge Base Management** pane, click **New Knowledge Base**.</span></span>  
  
     <span data-ttu-id="bcaae-109">![ナレッジ ベース管理 - 新しい KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "ナレッジ ベース管理 - 新しい KB")</span><span class="sxs-lookup"><span data-stu-id="bcaae-109">![Knowledge Base Management - New KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "Knowledge Base Management - New KB")</span></span>  
  
4.  <span data-ttu-id="bcaae-110">ナレッジベースの**名前**として「**仕入先**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-110">Enter **Suppliers** for **Name** of the knowledge base.</span></span>  
  
     <span data-ttu-id="bcaae-111">![新しいナレッジ ベース - ドメイン管理](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "新しいナレッジ ベース - ドメイン管理")</span><span class="sxs-lookup"><span data-stu-id="bcaae-111">![New Knowledge Base - Domain Management](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "New Knowledge Base - Domain Management")</span></span>  
  
5.  <span data-ttu-id="bcaae-112">**サプライヤー**ナレッジベースを最初から作成しているため、[フィールド**からナレッジベースを作成**する] が **[なし**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-112">Confirm that **Create Knowledge Base from** field is set to **None** since you are creating the **Suppliers** knowledge base from scratch.</span></span>  
  
6.  <span data-ttu-id="bcaae-113">**アクティビティ**の [**ドメイン管理**] が選択されていることを確認し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bcaae-113">Confirm that **Domain Management** is selected for the **Activity** and click **Next**.</span></span> <span data-ttu-id="bcaae-114">ドメイン管理アクティビティを使用すると、ナレッジ ベース内のドメインを作成および管理できます。</span><span class="sxs-lookup"><span data-stu-id="bcaae-114">The Domain Management activity lets you create and manage domains in the knowledge base.</span></span>  
  
7.  <span data-ttu-id="bcaae-115">[**ドメイン管理**] ウィンドウで、[ドメインの**作成**] ツールバーボタンをクリックして、ドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-115">In the **Domain Management** window, click **Create a domain** toolbar button to create a domain.</span></span>  
  
     <span data-ttu-id="bcaae-116">![[ドメインの作成] ツール バー ボタン](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "[ドメインの作成] ツール バー ボタン")</span><span class="sxs-lookup"><span data-stu-id="bcaae-116">![Create Domain Toolbar Button](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "Create Domain Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="bcaae-117">[**ドメインの作成**] ダイアログボックスで、**ドメイン名**として「 **Supplier ID** 」と入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bcaae-117">In the **Create Domain** dialog box, type **Supplier ID** for the **Domain Name**, and click **OK**.</span></span>  
  
     <span data-ttu-id="bcaae-118">![[ドメインの作成] ダイアログ ボックス](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "[ドメインの作成] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="bcaae-118">![Create Domain Dialog Box](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "Create Domain Dialog Box")</span></span>  
  
9. <span data-ttu-id="bcaae-119">前の手順を繰り返して、すべて既定の設定になっている次のドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-119">Repeat previous step to create the following domains with all the default settings.</span></span> <span data-ttu-id="bcaae-120">このチュートリアルを簡単にするために、すべてのドメインの**データ型**を**文字列**として設定します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-120">To keep the tutorial simple, you set the **Data Type** of all the domains as **String**.</span></span> <span data-ttu-id="bcaae-121">他に使用できるデータ型には、Integer、Decimal、および Date があります。</span><span class="sxs-lookup"><span data-stu-id="bcaae-121">The other allowed data types are: Integer, Decimal, and Date.</span></span> <span data-ttu-id="bcaae-122">[**先頭の値を使用**する] オプションが選択されている場合 (既定)、すべてのシノニムが出力のシノニムグループの先頭の値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="bcaae-122">When the **Use Leading Values** option is selected (default), all synonyms are replaced with the leading value of the synonym group in the output.</span></span> <span data-ttu-id="bcaae-123">**文字列の正規化**オプションを設定すると (既定)、ドメイン値の特殊文字は削除されます。</span><span class="sxs-lookup"><span data-stu-id="bcaae-123">Setting **Normalize String** option (default) removes any special characters in the domain values.</span></span> <span data-ttu-id="bcaae-124">[**形式の出力先**] オプションを使用すると、ドメイン内のデータ値が出力されるときに適用される書式設定を選択できます。</span><span class="sxs-lookup"><span data-stu-id="bcaae-124">The **Format Output to** option lets you select the formatting that is applied when the data values in the domain are output.</span></span> <span data-ttu-id="bcaae-125">ドメインの設定時にすべての文字列値に対してスペルチェックを実行するには、[**スペルチェックを有効**にする (既定)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-125">Select **Enable Speller** (default) to run Speller on all string values when populating the domain.</span></span> <span data-ttu-id="bcaae-126">[**言語**] 設定では、適用する**スペルチェック**の言語バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="bcaae-126">The **Language** setting specifies which language version of the **Speller** you want to apply.</span></span> <span data-ttu-id="bcaae-127">構文エラーの文字列値を確認せずにドメインを設定するには、[**構文エラーアルゴリズムを無効**にする] をオンにします。</span><span class="sxs-lookup"><span data-stu-id="bcaae-127">Select **Disable Syntax Error Algorithms** to populate the domain without checking string values for syntax errors.</span></span> <span data-ttu-id="bcaae-128">詳細については、MSDN ライブラリの「[ドメインの作成](https://msdn.microsoft.com/library/hh510401.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcaae-128">See [Create a Domain](https://msdn.microsoft.com/library/hh510401.aspx) topic in the MSDN library for more details.</span></span>  
  
    -   <span data-ttu-id="bcaae-129">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="bcaae-129">Supplier Name</span></span>  
  
    -   <span data-ttu-id="bcaae-130">連絡先のメール アドレス</span><span class="sxs-lookup"><span data-stu-id="bcaae-130">Contact Email</span></span>  
  
    -   <span data-ttu-id="bcaae-131">Address Line</span><span class="sxs-lookup"><span data-stu-id="bcaae-131">Address Line</span></span>  
  
    -   <span data-ttu-id="bcaae-132">City</span><span class="sxs-lookup"><span data-stu-id="bcaae-132">City</span></span>  
  
    -   <span data-ttu-id="bcaae-133">State</span><span class="sxs-lookup"><span data-stu-id="bcaae-133">State</span></span>  
  
    -   <span data-ttu-id="bcaae-134">国</span><span class="sxs-lookup"><span data-stu-id="bcaae-134">Country</span></span>  
  
    -   <span data-ttu-id="bcaae-135">Zip</span><span class="sxs-lookup"><span data-stu-id="bcaae-135">Zip</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="bcaae-136">次の手順</span><span class="sxs-lookup"><span data-stu-id="bcaae-136">Next Step</span></span>  
 [<span data-ttu-id="bcaae-137">タスク 2: ドメイン値を手動で追加する</span><span class="sxs-lookup"><span data-stu-id="bcaae-137">Task 2: Adding Domain Values Manually</span></span>](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
