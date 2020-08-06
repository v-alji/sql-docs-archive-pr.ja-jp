---
title: SharePoint ライブラリへのドキュメントのアップロード (SharePoint モードの Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- SharePoint integration [Reporting Services], content management
- uploading reports [Reporting Services]
ms.assetid: 93bd1b19-061b-409f-8dc2-ec416b2f4b39
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 74b39f90cd90dc8a92a5f10168d98f165c211c51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737783"
---
# <a name="upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="84f0f-102">SharePoint ライブラリへのドキュメントのアップロード (Reporting Services の SharePoint モード)</span><span class="sxs-lookup"><span data-stu-id="84f0f-102">Upload Documents to a SharePoint Library (Reporting Services in SharePoint Mode)</span></span>
  <span data-ttu-id="84f0f-103">レポート定義やレポート モデルを SharePoint ライブラリにアップロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-103">You can upload report definitions and report models to a SharePoint library.</span></span> <span data-ttu-id="84f0f-104">レポート サーバー アイテムをアップロードするときには、ライブラリまたはライブラリ内のフォルダーを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84f0f-104">When uploading a report server item, you must select a library or a folder within a library.</span></span> <span data-ttu-id="84f0f-105">レポート サーバー アイテムを一覧やページにアップロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="84f0f-105">You cannot upload a report server item to a list or page.</span></span>  
  
 <span data-ttu-id="84f0f-106">データ ソース (.rds) ファイルをアップロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="84f0f-106">You cannot upload a data source (.rds) file.</span></span> <span data-ttu-id="84f0f-107">ただし、.rds ファイルをデザイン ツール (レポート デザイナーなど) から SharePoint ライブラリにパブリッシュすることはできます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-107">However, you can publish .rds files from a design tool, such as Report Designer, to a SharePoint library.</span></span> <span data-ttu-id="84f0f-108">パブリッシュ時に、ソリューション内の元の .rds ファイルから新しい .rsds ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-108">During publication, a new .rsds file is created from the original .rds file in the solution.</span></span> <span data-ttu-id="84f0f-109">SharePoint ライブラリに新しい .rsds ファイルを作成して、その新しい接続が使用されるように、アップロードしたレポートやモデルのデータ ソース接続プロパティを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-109">You can also create a new .rsds file in a SharePoint library and then set data source connection properties in the uploaded reports and models to use the new connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="84f0f-110">レポート サーバーは SharePoint モード用に構成しておく必要があります。また、SharePoint 製品のインスタンスに、SharePoint サイトからレポート サーバー アイテムを格納しレポート サーバー アイテムにアクセスするプログラム ファイルを提供する [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] アドインが必要です。</span><span class="sxs-lookup"><span data-stu-id="84f0f-110">The report server must be configured for SharePoint mode, and the instance of the SharePoint product must have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Add-in that provides program files for storing and accessing report server items from a SharePoint site.</span></span>  
  
 <span data-ttu-id="84f0f-111">ドキュメントをライブラリにアップロードするには、サイト レベルの "アイテムの追加" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="84f0f-111">To upload a document to a library, you must have the "Add Items" permission at the site level.</span></span> <span data-ttu-id="84f0f-112">既定のセキュリティ設定を使用している場合、この権限は、フル コントロール レベルの権限を持つ **所有者** グループおよび投稿レベルの権限を持つ **メンバー** グループのメンバーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-112">If you are using default security settings, this permission is granted to members of the **Owners** group who have the Full Control level of permission and to the **Members** group who have the Contribute level of permission.</span></span>  
  
### <a name="to-add-a-report-definition-or-report-model-to-a-library"></a><span data-ttu-id="84f0f-113">レポート定義またはレポート モデルをライブラリに追加するには</span><span class="sxs-lookup"><span data-stu-id="84f0f-113">To add a report definition or report model to a library</span></span>  
  
1.  <span data-ttu-id="84f0f-114">ライブラリまたはライブラリ内のフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-114">Open the library or a folder within a library.</span></span> <span data-ttu-id="84f0f-115">まだライブラリが開いていない場合は、サイド リンク バーでライブラリの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84f0f-115">If the library is not already open, click its name on the Quick Launch.</span></span> <span data-ttu-id="84f0f-116">ライブラリの名前が表示されていない場合は、 **[すべてのサイト コンテンツの表示]** をクリックし、ライブラリの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84f0f-116">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="84f0f-117">**[アップロード]** メニューの **[ドキュメントのアップロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84f0f-117">On the **Upload** menu, click **Upload document**.</span></span>  
  
3.  <span data-ttu-id="84f0f-118">1 つのレポート ファイルまたはレポート モデル ファイルをアップロードするには、レポート定義 (.rdl) ファイルまたはレポート モデル (.smdl) ファイルを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84f0f-118">To upload a single report or report model file, select a report definition (.rdl) or report model (.smdl) file and then click **OK**.</span></span>  
  
     <span data-ttu-id="84f0f-119">レポート定義で共有データ ソース (.rsds) ファイルを使用して接続情報を外部データ ソースに格納している場合は、.rdl ファイルと .rsds ファイルを同時にアップロードできます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-119">If the report definition uses a shared data source (.rsds) file to store connection information to an external data source, you can upload the .rdl and the .rsds file at the same time.</span></span> <span data-ttu-id="84f0f-120">これには、 **[複数のドキュメントのアップロード]** をクリックし、両方のファイルを指定して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84f0f-120">To do this, click **Upload Multiple Documents**, specify both files, and then click **OK**.</span></span>  
  
 <span data-ttu-id="84f0f-121">共有データ ソース、レポート モデル、またはサブレポートへの参照が含まれているレポートをアップロードすると、ファイルのアップロード時にレポート内で参照が破損します。</span><span class="sxs-lookup"><span data-stu-id="84f0f-121">If you upload a report that contains references to shared data sources, report models, or subreports, the references will be broken in the report when the files are uploaded.</span></span> <span data-ttu-id="84f0f-122">参照のリセット方法の詳細については、「[共有データ ソースを作成および管理する &#40;Reporting Services の SharePoint 統合モード&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84f0f-122">For more information about how to reset the references, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
 <span data-ttu-id="84f0f-123">レポートをアップロードした場合は、そのレポートを開くとレポートがオンデマンドで実行されて、データ ソースからライブ データが取得されます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-123">When you upload a report, it runs on demand when you open it, retrieving live data from the data source.</span></span> <span data-ttu-id="84f0f-124">スケジュールに基づいたデータ取得や、キャッシュされたデータの使用が行われるようにレポートを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-124">You can configure the report to retrieve data on a schedule or use cached data.</span></span> <span data-ttu-id="84f0f-125">詳細については、「[処理オプションの設定 &#40;Reporting Services の SharePoint 統合モード&#41;](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84f0f-125">For more information, see [Set Processing Options &#40;Reporting Services in SharePoint Integrated Mode&#41;](../../2014/reporting-services/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md).</span></span>  
  
 <span data-ttu-id="84f0f-126">レポートにパラメーターを含めると、ユーザーがデータをフィルター選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="84f0f-126">A report can contain parameters so that users can filter data.</span></span> <span data-ttu-id="84f0f-127">パラメーターは、特定の値を使用するように構成したり、表示方法を変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="84f0f-127">You can configure the parameters to use specific values or change how they appear to the user.</span></span> <span data-ttu-id="84f0f-128">詳細については、「[パブリッシュ済みレポートのパラメーターを設定する方法 &#40;Reporting Services の SharePoint 統合モード&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84f0f-128">For more information, see [Set Parameters on a Published Report &#40;Reporting Services in SharePoint Integrated Mode&#41;](report-design/set-parameters-on-a-published-report-sharepoint-integrated-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84f0f-129">参照</span><span class="sxs-lookup"><span data-stu-id="84f0f-129">See Also</span></span>  
 <span data-ttu-id="84f0f-130">[SharePoint ライブラリへのレポートのパブリッシュ](reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="84f0f-130">[Publish a Report to a SharePoint Library](reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="84f0f-131">[SharePoint ライブラリへの共有データソースのパブリッシュ](reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="84f0f-131">[Publish a Shared Data Source to a SharePoint Library](reports/publish-a-shared-data-source-to-a-sharepoint-library.md) </span></span>  
 [<span data-ttu-id="84f0f-132">SharePoint サイトのレポート サーバー アイテムに対する権限の付与</span><span class="sxs-lookup"><span data-stu-id="84f0f-132">Granting Permissions on Report Server Items on a SharePoint Site</span></span>](security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
  
  
