---
title: BI セマンティックモデル接続のコンテンツタイプをライブラリに追加する (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 145505ed-50bc-4528-912b-2a5cd2566011
author: minewiskan
ms.author: owend
ms.openlocfilehash: ecd40193b382aa692beeadd55ab8f9388c328620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644183"
---
# <a name="add-a-bi-semantic-model-connection-content-type-to-a-library-powerpivot-for-sharepoint"></a><span data-ttu-id="aca45-102">BI セマンティック モデル接続のコンテンツ タイプのライブラリへの追加 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="aca45-102">Add a BI Semantic Model Connection Content Type to a Library (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="aca45-103">BI セマンティック モデル接続は、SharePoint で作成され、ネットワーク サーバー上の PowerPivot ブックまたは Analysis Services テーブル モデル データベース内の Business Intelligence Semantic Model データへのリダイレクトを可能にします。</span><span class="sxs-lookup"><span data-stu-id="aca45-103">A BI semantic model connection is created in SharePoint and provides redirection to business intelligence semantic model data in a PowerPivot workbook or Analysis Services tabular model database on a network server.</span></span> <span data-ttu-id="aca45-104">SharePoint で BI セマンティック モデル接続を作成する前に、.bism ファイルの作成を許可するようにドキュメント ライブラリを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aca45-104">Before you can create a BI semantic model connection in SharePoint, you must extend a document library to allow the creation of a .bism file.</span></span> <span data-ttu-id="aca45-105">この手順はライブラリごとに 1 回だけ実行する必要があり、.bism ファイルを作成するすべてのライブラリに対してこの手順を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="aca45-105">This step only needs to be performed once for each library, but you will need to repeat it for any library from which you want to create .bism files.</span></span> <span data-ttu-id="aca45-106">ベスト プラクティスとして、権限を 1 か所で管理できるように、.bism ファイルを格納する単一のライブラリを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="aca45-106">Best practices recommend that you create a centralized library for storing .bism files so that you can manage permissions in one place.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aca45-107">既に SharePoint データ接続ライブラリを使用している場合、"BI セマンティック モデル接続" コンテンツ タイプがそのライブラリ テンプレートに自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="aca45-107">If you already use SharePoint Data Connection Libraries, the BI Semantic Model Connection content type is automatically added to that library template.</span></span> <span data-ttu-id="aca45-108">既に新しい BI セマンティック モデル接続ドキュメントの作成が許可されているデータ接続ライブラリを使用する場合は、このセクションの手順を省略できます。</span><span class="sxs-lookup"><span data-stu-id="aca45-108">You can skip the steps in this section if you use a data connection library that already lets you create new BI semantic model connection documents.</span></span>  
  
##  <a name="add-the-content-type-to-a-document-library"></a><a name="bkmk_addtype"></a> <span data-ttu-id="aca45-109">ドキュメント ライブラリへのコンテンツ タイプの追加</span><span class="sxs-lookup"><span data-stu-id="aca45-109">Add the content type to a document library</span></span>  
 <span data-ttu-id="aca45-110">コンテンツ タイプを追加および構成するには、管理リスト権限以上の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="aca45-110">You must have at least the Manage Lists permission to add and configure a content type.</span></span> <span data-ttu-id="aca45-111">この権限は、デザイン権限レベル以上の権限に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="aca45-111">This permission is built into the Design permission level and above.</span></span>  
  
 <span data-ttu-id="aca45-112">ドキュメント ライブラリがあるサイトでは、PowerPivot for SharePoint の機能のアクティブ化が必要です。</span><span class="sxs-lookup"><span data-stu-id="aca45-112">The site that contains the document library must have feature activation for PowerPivot for SharePoint.</span></span> <span data-ttu-id="aca45-113">詳細については、「[サーバーの全体管理でサイトコレクションの PowerPivot 機能の統合をアクティブ化](activate-power-pivot-integration-for-site-collections-in-ca.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aca45-113">For more information, see [Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).</span></span>  
  
1.  <span data-ttu-id="aca45-114">"BI セマンティック モデル接続" コンテンツ タイプを有効にする対象のドキュメント ライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="aca45-114">Open the document library for which you want to enable the BI Semantic Model Connection content type.</span></span>  
  
2.  <span data-ttu-id="aca45-115">SharePoint リボンで、[ライブラリ ツール] の **[ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-115">On the SharePoint ribbon, in Library Tools, click **Library**.</span></span>  
  
3.  <span data-ttu-id="aca45-116">**[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-116">Click **Library Settings**.</span></span>  
  
4.  <span data-ttu-id="aca45-117">[全般設定] の **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-117">In General Settings, click **Advanced settings**.</span></span>  
  
5.  <span data-ttu-id="aca45-118">[コンテンツ タイプ] の [コンテンツ タイプの管理を許可する]</span><span class="sxs-lookup"><span data-stu-id="aca45-118">In Content Types, in the "Allow management of content types?"</span></span> <span data-ttu-id="aca45-119">セクションで **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-119">section, click **Yes**.</span></span>  
  
6.  <span data-ttu-id="aca45-120">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-120">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="aca45-121">[コンテンツ タイプ] セクションの **[既存のサイト コンテンツ タイプから追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-121">In the Content Types section, click **Add from existing site content types**.</span></span> <span data-ttu-id="aca45-122">このページが表示されない場合は、サイトに戻って [ライブラリ ツール] の **[ライブラリ]** をクリックし、 **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-122">If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.</span></span>  
  
8.  <span data-ttu-id="aca45-123">[コンテンツ タイプ] の **[既存のサイト コンテンツ タイプから追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-123">In Content Types, click **Add from existing site content types**.</span></span>  
  
9. <span data-ttu-id="aca45-124">[サイト コンテンツ タイプの選択元] で **[ビジネス インテリジェンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-124">In Select site content types from:, select **Business Intelligence**.</span></span>  
  
10. <span data-ttu-id="aca45-125">[利用可能なサイト コンテンツ タイプ] で **[BI セマンティック モデル接続ファイル]** をクリックしてから **[追加]** をクリックし、選択したコンテンツ タイプを [追加するコンテンツ タイプ] ボックスの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="aca45-125">In Available Site Content Types, click **BI Semantic Model Connection File**, and then click **Add** to move the selected content type to the Content types to add list.</span></span>  
  
11. <span data-ttu-id="aca45-126">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-126">Click **OK**.</span></span>  
  
12. <span data-ttu-id="aca45-127">コンテンツ タイプを追加したことを確認するには、ライブラリに戻り、ライブラリ リボンのドキュメント領域で **[新しいドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aca45-127">To verify you added the content type, go back to the library and click **New Document** on the Documents area of the library ribbon.</span></span> <span data-ttu-id="aca45-128">[新しいドキュメント] ボックスの一覧に、 **[BI セマンティック モデル接続ファイル]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aca45-128">You should see **BI Semantic Model Connection File** in the New Documents list.</span></span>  
  
     <span data-ttu-id="aca45-129">![SharePoint ライブラリの [新しいドキュメント] サブメニュー](../media/ssas-bismconnection-new.gif "SharePoint ライブラリの [新しいドキュメント] サブメニュー")</span><span class="sxs-lookup"><span data-stu-id="aca45-129">![New Document submenu in a SharePoint library](../media/ssas-bismconnection-new.gif "New Document submenu in a SharePoint library")</span></span>  
  
 <span data-ttu-id="aca45-130">"BI セマンティック モデル接続" コンテンツ タイプをライブラリに対して有効にした後で、Excel または [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートで使用できるビジネス セマンティック モデル データへのリダイレクトを可能にする接続を作成できます。</span><span class="sxs-lookup"><span data-stu-id="aca45-130">After you enable the BI semantic model connection content type for a library, you can create a connection that provides redirection to business semantic model data that can be used by Excel or [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span> <span data-ttu-id="aca45-131">次のステップの詳細については、次のリンクから選択してください。</span><span class="sxs-lookup"><span data-stu-id="aca45-131">Choose from the following links to learn more about this next step:</span></span>  
  
 [<span data-ttu-id="aca45-132">PowerPivot ブックへの BI セマンティック モデル接続の作成</span><span class="sxs-lookup"><span data-stu-id="aca45-132">Create a BI Semantic Model Connection to a PowerPivot Workbook</span></span>](create-a-bi-semantic-model-connection-to-a-power-pivot-workbook.md)  
  
 [<span data-ttu-id="aca45-133">テーブル モデル データベースへの BI セマンティック モデル接続の作成</span><span class="sxs-lookup"><span data-stu-id="aca45-133">Create a BI Semantic Model Connection to a Tabular Model Database</span></span>](create-a-bi-semantic-model-connection-to-a-tabular-model-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="aca45-134">参照</span><span class="sxs-lookup"><span data-stu-id="aca45-134">See Also</span></span>  
 <span data-ttu-id="aca45-135">[PowerPivot BI セマンティックモデル接続 &#40;。 bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span><span class="sxs-lookup"><span data-stu-id="aca45-135">[PowerPivot BI Semantic Model Connection &#40;.bism&#41;](power-pivot-bi-semantic-model-connection-bism.md) </span></span>  
 [<span data-ttu-id="aca45-136">Excel または Reporting Services での BI セマンティック モデル接続の使用</span><span class="sxs-lookup"><span data-stu-id="aca45-136">Use a BI Semantic Model Connection in Excel or Reporting Services</span></span>](use-a-bi-semantic-model-connection-in-excel-or-reporting-services.md)  
  
  
