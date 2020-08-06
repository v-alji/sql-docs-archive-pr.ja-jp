---
title: このブックには外部データを更新する 1 つ以上のクエリが含まれています。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25b2095e13d6151c68eb4a3507400dfdb1739564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640273"
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a><span data-ttu-id="55ca0-103">このブックには外部データを更新する 1 つ以上のクエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55ca0-103">This workbook contains one or more queries that refresh external data.</span></span>
  <span data-ttu-id="55ca0-104">PowerPivot データが含まれる Excel ブックの場合、Excel Services は接続情報が検出されるとこの警告を表示し、このブックのクエリを有効にするか無効にするかを確認するプロンプトを表示します。</span><span class="sxs-lookup"><span data-stu-id="55ca0-104">For Excel workbooks that contain PowerPivot data, Excel Services shows this warning when it detects connection information and prompts you to enable or disable queries for this workbook.</span></span>  
  
## <a name="details"></a><span data-ttu-id="55ca0-105">詳細</span><span class="sxs-lookup"><span data-stu-id="55ca0-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55ca0-106">製品名</span><span class="sxs-lookup"><span data-stu-id="55ca0-106">Product Name</span></span>|<span data-ttu-id="55ca0-107">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="55ca0-107">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="55ca0-108">製品バージョン</span><span class="sxs-lookup"><span data-stu-id="55ca0-108">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="55ca0-109">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55ca0-109">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="55ca0-110">原因</span><span class="sxs-lookup"><span data-stu-id="55ca0-110">Cause</span></span>|<span data-ttu-id="55ca0-111">Excel Services がデータ更新時に警告を表示するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="55ca0-111">Excel Services is configured to warn on data refresh.</span></span>|  
|<span data-ttu-id="55ca0-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="55ca0-112">Message Text</span></span>|<span data-ttu-id="55ca0-113">このブックには外部データを更新する 1 つ以上のクエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55ca0-113">This workbook contains one or more queries that refresh external data.</span></span> <span data-ttu-id="55ca0-114">悪意のあるユーザーは資格情報にアクセスし、他のユーザーに配布したり、他の有害なアクションを実行するようにクエリを書き換えることがあります。</span><span class="sxs-lookup"><span data-stu-id="55ca0-114">A malicious user can design a query to access confidential information and distribute it to other users or perform other harmful actions.</span></span><br /><br /> <span data-ttu-id="55ca0-115">このブックのソースを信頼できる場合は、[はい] をクリックしてこのブックの外部データに対するクエリを有効にします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-115">If you trust the source of this workbook, click Yes to enable queries to external data in this workbook.</span></span> <span data-ttu-id="55ca0-116">信頼できるかどうかが不明である場合は、[いいえ] をクリックして変更がブックに適用されないようにします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-116">If you are not sure, click No so that changes are not applied to your workbook.</span></span><br /><br /> <span data-ttu-id="55ca0-117">このブックの外部データへのクエリを有効にしますか?</span><span class="sxs-lookup"><span data-stu-id="55ca0-117">Do you want to enable queries to external data in this workbook?</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="55ca0-118">説明</span><span class="sxs-lookup"><span data-stu-id="55ca0-118">Explanation</span></span>  
 <span data-ttu-id="55ca0-119">PowerPivot ブックに、データの読み込みと計算を行う外部 PowerPivot サーバーと通信する Excel で使用される埋め込みデータ接続文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="55ca0-119">PowerPivot workbooks contain embedded data connection strings that are used by Excel to communicate with an external PowerPivot server that loads and calculates the data.</span></span> <span data-ttu-id="55ca0-120">[データ更新に関する警告を表示する] が有効になっている場合、Excel Services はこの接続文字列を検出し、ユーザーにその旨を警告します。</span><span class="sxs-lookup"><span data-stu-id="55ca0-120">When warn on data refresh is enabled, Excel Services detects this connection string and warns the user accordingly.</span></span>  
  
 <span data-ttu-id="55ca0-121">ブックの PowerPivot データをフィルターおよびスライスする場合は、クエリを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ca0-121">To filter and slice PowerPivot data in the workbook, queries must be enabled.</span></span> <span data-ttu-id="55ca0-122">信頼できる PowerPivot ブックのクエリのみを有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="55ca0-122">Be sure that you enable queries for only those PowerPivot workbooks that you trust.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="55ca0-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="55ca0-123">User Action</span></span>  
 <span data-ttu-id="55ca0-124">**[はい]** をクリックしてクエリを有効にします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-124">Click **Yes** to enable queries.</span></span>  
  
 <span data-ttu-id="55ca0-125">また、構成設定を変更して、更新時に警告が表示されないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="55ca0-125">You can also change the configuration settings so that warn on refresh no longer occurs:</span></span>  
  
1.  <span data-ttu-id="55ca0-126">サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-126">In Central Administration, in Application Management, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="55ca0-127">**[Excel Services アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-127">Click **Excel Services Application**.</span></span>  
  
3.  <span data-ttu-id="55ca0-128">**[信頼できるファイル保存場所]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-128">Click **Trusted File Location**.</span></span>  
  
4.  <span data-ttu-id="55ca0-129">**[http://]** または構成する場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-129">Click **http://** or the location you want to configure.</span></span>  
  
5.  <span data-ttu-id="55ca0-130">[外部データ] で、 **[データ更新に関する警告を表示する]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-130">In External Data, clear the checkbox for **Warn on data refresh**.</span></span>  
  
6.  <span data-ttu-id="55ca0-131">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55ca0-131">Click **OK**.</span></span>  
  
 <span data-ttu-id="55ca0-132">または、PowerPivot ブックが含まれるサイト用に新しく信頼できる場所を作成し、そのサイトの構成設定だけを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="55ca0-132">Alternatively, you can create a new trusted location for sites that contain PowerPivot workbooks, and then modify the configuration settings for just that site.</span></span> <span data-ttu-id="55ca0-133">詳細については、「 [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55ca0-133">For more information, see [Create a trusted location for PowerPivot sites in Central Administration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).</span></span>  
  
  
