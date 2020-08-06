---
title: データフィードライブラリの作成またはカスタマイズ (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data feed library
- data feeds [Analysis Services with SharePoint]
ms.assetid: 699fbeb9-42ab-436b-beba-214db51ea3dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: b86f63c1af094ea9e8a2a1149debeac387bccbf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714609"
---
# <a name="create-or-customize-a-data-feed-library-powerpivot-for-sharepoint"></a><span data-ttu-id="e9b68-102">データ フィード ライブラリの作成またはカスタマイズ (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="e9b68-102">Create or Customize a Data Feed Library (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="e9b68-103">*データ フィード ライブラリ* は、特殊な用途の SharePoint ライブラリです。このライブラリでは、Atom データ サービス ドキュメント (.atomsvc) を登録して共有できます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-103">A *data feed library* is a special-purpose SharePoint library that enables you to register and share Atom data service documents (.atomsvc).</span></span> <span data-ttu-id="e9b68-104">これらのドキュメントは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックまたは Atom データ フィード形式をサポートするその他のクライアント アプリケーションに XML データ フィードを提供します。</span><span class="sxs-lookup"><span data-stu-id="e9b68-104">These documents provide XML data feeds to [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks or other client applications that support the Atom data feed format.</span></span> <span data-ttu-id="e9b68-105">データ フィード ライブラリは、以下を実行できる点で他の SharePoint ライブラリとは異なります。</span><span class="sxs-lookup"><span data-stu-id="e9b68-105">A data feed library is different from other SharePoint libraries because it gives you the ability to:</span></span>

-   <span data-ttu-id="e9b68-106">特定のフィードへの HTTP 接続を指定するために使用される *データ サービス ドキュメント*を作成または編集できます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-106">Create or edit a *data service document*, used to specify an HTTP connection to a specific feed.</span></span>

-   <span data-ttu-id="e9b68-107">集中管理された場所でデータ サービス ドキュメントを共有および管理できます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-107">Share and manage data service documents in a central location.</span></span>

-   <span data-ttu-id="e9b68-108">データサービスドキュメントをアイコンで視覚的に識別し、同じライブラリに格納されている他のドキュメントとサービスドキュメントを簡単に区別できるようにします。 ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")</span><span class="sxs-lookup"><span data-stu-id="e9b68-108">Visually identify data service documents by an icon, so that you can easily distinguish service documents from other documents stored in the same library: ![GMNI_IconDataFeed](../media/gmni-icondatafeed.gif "GMNI_IconDataFeed")</span></span>

 <span data-ttu-id="e9b68-109">データ フィード ライブラリには、データ フィード自体ではなく、常にデータ サービス ドキュメント (.atomsvc) ファイルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-109">A data feed library always contains data service document (.atomsvc) files, and never the data feed itself.</span></span> <span data-ttu-id="e9b68-110">静的な XML データで構成されるデータ フィードとは異なり、データ サービス ドキュメントでは、要求時にフィードを生成するサービスまたはアプリケーションの URL を指定します。そのため、反復可能なインポート操作で接続情報を再利用できます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-110">Unlike a data feed, which consists of static XML data, the data service document specifies a URL to a service or application that generates a feed upon request, providing reusable connection information for repeatable import operations.</span></span>

 <span data-ttu-id="e9b68-111">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="e9b68-111">This topic contains the following sections:</span></span>

 [<span data-ttu-id="e9b68-112">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e9b68-112">Prerequisites</span></span>](#prereq)

 [<span data-ttu-id="e9b68-113">新しいデータ フィード ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="e9b68-113">Create a New Data Feed Library</span></span>](#createlib)

 [<span data-ttu-id="e9b68-114">任意のライブラリへのデータ フィード コンテンツ タイプの追加</span><span class="sxs-lookup"><span data-stu-id="e9b68-114">Add the Data Feed Content Type to Any Library</span></span>](#addtolib)

##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="e9b68-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="e9b68-115">Prerequisites</span></span>
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] <span data-ttu-id="e9b68-116">機能の統合を、データ フィード ライブラリを作成するサイトに対してアクティブ化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9b68-116">feature integration must be activated for the sites for which you are creating the data feed library.</span></span> <span data-ttu-id="e9b68-117">データ フィード ライブラリ テンプレート タイプが使用できない場合、この前提条件を満たしていないことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-117">If the data feed library template type is not available, the most likely cause is that this prerequisite has not been met.</span></span> <span data-ttu-id="e9b68-118">詳細については、「[サーバーの全体管理でサイトコレクションの PowerPivot 機能の統合をアクティブ化](activate-power-pivot-integration-for-site-collections-in-ca.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9b68-118">For more information, see [Activate PowerPivot Feature Integration for Site Collections in Central Administration](activate-power-pivot-integration-for-site-collections-in-ca.md).</span></span>

 <span data-ttu-id="e9b68-119">ライブラリを作成するには、サイト所有者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9b68-119">You must be a site owner to create the library.</span></span>

##  <a name="create-a-new-data-feed-library"></a><a name="createlib"></a><span data-ttu-id="e9b68-120">新しいデータフィードライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="e9b68-120">Create a New Data Feed Library</span></span>
 <span data-ttu-id="e9b68-121">[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックのデータ フィードを有効にするには、最初にデータ フィード ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9b68-121">Creating a data feed library is the first step to enabling data feeds for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] workbooks.</span></span> <span data-ttu-id="e9b68-122">データ サービス ドキュメントのアプリケーション ページと管理ページはデータ フィード ライブラリによって提供されるため、新しいドキュメントを作成する前にこのライブラリを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9b68-122">Because a data feed library provides application and management pages for data service documents, you must have this library in place before you can create a new document.</span></span>

 <span data-ttu-id="e9b68-123">データ フィード ライブラリは、組み込みのテンプレートと、データ サービス ドキュメントのプロパティと動作を定義する事前に構成された *データ サービス ドキュメントのコンテンツのタイプ* に基づきます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-123">A data feed library is based on a built-in template and a preconfigured *data service document content type* that defines properties and behaviors for a data service document.</span></span>

1.  <span data-ttu-id="e9b68-124">ページの左上にある **[サイトの操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-124">Click **Site Actions** at the top left corner of the page.</span></span>

2.  <span data-ttu-id="e9b68-125">[**その他のオプション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-125">Click **More Options**...</span></span>

3.  <span data-ttu-id="e9b68-126">[ライブラリ] の **[データ フィード ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-126">Under Libraries, click **Data Feed Library**.</span></span>

4.  <span data-ttu-id="e9b68-127">名前、説明、起動、およびバージョン設定を入力します。</span><span class="sxs-lookup"><span data-stu-id="e9b68-127">Type the name, description, launch, and version preferences.</span></span> <span data-ttu-id="e9b68-128">このライブラリがデータ サービス ドキュメントのストレージであることがユーザーにわかるように説明情報を入力してください。</span><span class="sxs-lookup"><span data-stu-id="e9b68-128">Include descriptive information to help users identify this library as storage for data service documents.</span></span>

5.  <span data-ttu-id="e9b68-129">**Create** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="e9b68-129">Click **Create**.</span></span>

 <span data-ttu-id="e9b68-130">データ フィード ライブラリへのリンクが、現在のサイトのナビゲーションのクイック起動ペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-130">A link to the data feed library will appear in the navigation Quick Launch pane for the current site.</span></span>

 <span data-ttu-id="e9b68-131">ライブラリを作成した後、そのライブラリを使用してデータ サービス ドキュメントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-131">After you create a library, you can use it to create data service documents.</span></span> <span data-ttu-id="e9b68-132">詳細については、「[データフィードの使用 &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9b68-132">For more information, see [Use Data Feeds &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md).</span></span>

##  <a name="add-the-data-feed-content-type-to-any-library"></a><a name="addtolib"></a><span data-ttu-id="e9b68-133">任意のライブラリへのデータフィードコンテンツタイプの追加</span><span class="sxs-lookup"><span data-stu-id="e9b68-133">Add the Data Feed Content Type to Any Library</span></span>
 <span data-ttu-id="e9b68-134">専用のデータ フィード ライブラリは作成せずに、SharePoint サイトからデータ サービス ドキュメントを作成して管理する場合は、データ サービス ドキュメント (.atomsvc) ファイルの共有に使用する任意のライブラリ用にデータ サービス ドキュメント コンテンツ タイプを手動で追加して構成できます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-134">If you do not want to create a dedicated data feed library, but you still want to create and manage data service documents from a SharePoint site, you can manually add and configure the data service document content type for any library that you will use to share data service document (.atomsvc) files.</span></span>

 <span data-ttu-id="e9b68-135">コンテンツ タイプを追加および構成するには、管理リスト権限以上の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="e9b68-135">You must have at least the Manage Lists permission to add and configure a content type.</span></span> <span data-ttu-id="e9b68-136">この権限は、デザイン権限レベル以上の権限に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="e9b68-136">This permission is built into the Design permission level and above.</span></span>

 <span data-ttu-id="e9b68-137">データ フィード登録ドキュメントを作成または編集するライブラリごとに、次の手順を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9b68-137">The following steps must be repeated for each library in which you want to create or edit data feed registration documents.</span></span>

#### <a name="step-1-enable-content-type-management"></a><span data-ttu-id="e9b68-138">手順 1: コンテンツ タイプを管理できるようにする</span><span class="sxs-lookup"><span data-stu-id="e9b68-138">Step 1: Enable Content Type Management</span></span>

1.  <span data-ttu-id="e9b68-139">複数のコンテンツ タイプを有効にする対象のドキュメント ライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-139">Open the document library for which you want to enable multiple content types.</span></span>

2.  <span data-ttu-id="e9b68-140">SharePoint リボンで、[ライブラリ ツール] の **[ライブラリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-140">On the SharePoint ribbon, in Library Tools, click **Library**.</span></span>

3.  <span data-ttu-id="e9b68-141">**[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-141">Click **Settings**.</span></span>

4.  <span data-ttu-id="e9b68-142">**[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-142">Click **Library Settings**.</span></span>

5.  <span data-ttu-id="e9b68-143">[全般設定] の **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-143">In General Settings, click **Advanced settings**.</span></span>

6.  <span data-ttu-id="e9b68-144">[コンテンツ タイプ] の [コンテンツ タイプの管理を許可する]</span><span class="sxs-lookup"><span data-stu-id="e9b68-144">In Content Types, in the "Allow management of content types?"</span></span> <span data-ttu-id="e9b68-145">セクションで **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-145">section, click **Yes**.</span></span>

7.  <span data-ttu-id="e9b68-146">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-146">Click **OK**.</span></span>

#### <a name="step-2-add-the-data-service-document-content-type"></a><span data-ttu-id="e9b68-147">手順 2: データ サービス ドキュメント コンテンツ タイプを追加する</span><span class="sxs-lookup"><span data-stu-id="e9b68-147">Step 2: Add the Data Service Document Content Type</span></span>

1.  <span data-ttu-id="e9b68-148">[コンテンツ タイプ] セクションの **[既存のサイト コンテンツ タイプから追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-148">In the Content Types section, click **Add from existing site content types**.</span></span> <span data-ttu-id="e9b68-149">このページが表示されない場合は、サイトに戻って [ライブラリ ツール] の **[ライブラリ]** をクリックし、 **[ライブラリの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-149">If you do not see this page, go back to the site, click **Library** in Library Tools, and then click **Library Settings**.</span></span>

2.  <span data-ttu-id="e9b68-150">[コンテンツ タイプ] の **[既存のサイト コンテンツ タイプから追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-150">In Content Types, click **Add from existing site content types**.</span></span>

3.  <span data-ttu-id="e9b68-151">[サイト コンテンツ タイプの選択元] で **[ビジネス インテリジェンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-151">In Select site content types from:, select **Business Intelligence**.</span></span>

4.  <span data-ttu-id="e9b68-152">[利用可能なサイト コンテンツ タイプ] で **[データ サービス ドキュメント]** をクリックしてから **[追加]** をクリックし、選択したコンテンツ タイプを [追加するコンテンツ タイプ] ボックスの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="e9b68-152">In Available Site Content Types, click **Data Service Document**, and then click **Add** to move the selected content type to the Content types to add list.</span></span>

5.  <span data-ttu-id="e9b68-153">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-153">Click **OK**.</span></span>

#### <a name="step-3-verify-data-service-document-configuration"></a><span data-ttu-id="e9b68-154">手順 3: データ サービス ドキュメントの構成を確認する</span><span class="sxs-lookup"><span data-stu-id="e9b68-154">Step 3: Verify Data Service Document Configuration</span></span>

1.  <span data-ttu-id="e9b68-155">サイトのホーム ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-155">Open the site home page.</span></span>

2.  <span data-ttu-id="e9b68-156">ライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-156">Open the library.</span></span>

3.  <span data-ttu-id="e9b68-157">SharePoint リボンで、 **[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-157">On the SharePoint ribbon, click **Documents**.</span></span>

4.  <span data-ttu-id="e9b68-158">[新しいドキュメント] の下矢印をクリックし、 **[データ サービス ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9b68-158">Click the down arrow on New Document, and select **Data Service Document**.</span></span> <span data-ttu-id="e9b68-159">[新しいデータ サービス ドキュメント] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e9b68-159">The New Data Service Document page should appear.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9b68-160">参照</span><span class="sxs-lookup"><span data-stu-id="e9b68-160">See Also</span></span>
 <span data-ttu-id="e9b68-161">[データフィードの使用 &#40;PowerPivot for SharePoint](use-data-feeds-power-pivot-for-sharepoint.md) [Powerpivot データフィードライブラリの削除](delete-a-power-pivot-data-feed-library.md)&#41;サーバーの[全体管理での Powerpivot サーバーの管理と構成](power-pivot-server-administration-and-configuration-in-central-administration.md)powerpivot[データフィード](power-pivot-data-feeds.md)</span><span class="sxs-lookup"><span data-stu-id="e9b68-161">[Use Data Feeds &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md) [Delete a PowerPivot Data Feed Library](delete-a-power-pivot-data-feed-library.md) [PowerPivot Server Administration and Configuration in Central Administration](power-pivot-server-administration-and-configuration-in-central-administration.md) [PowerPivot Data Feeds](power-pivot-data-feeds.md)</span></span>


