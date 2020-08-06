---
title: レポートまたはモデルを共有データ ソースにバインドする (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 596caba042d476173b3c49d1ad18e79d0827fe89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713881"
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a><span data-ttu-id="c09e5-102">レポートまたはモデルを共有データ ソースにバインドする (SSRS)</span><span class="sxs-lookup"><span data-stu-id="c09e5-102">Bind a Report or Model to a Shared Data Source (SSRS)</span></span>
  <span data-ttu-id="c09e5-103">レポートまたはモデルをテスト サーバーから実稼働サーバーに移動するときなど、ファイルをローカル コンピューターに保存した後で別のレポート サーバーにアップロードする操作が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c09e5-103">In some situations, such as when you move a report or model from a test server to a production server, you might want to save the file to your local computer and then upload it to a different report server.</span></span> <span data-ttu-id="c09e5-104">レポートまたはモデルを新しいサーバーにアップロードしたときは、新しいレポート サーバー上に格納されている共有データ ソースにレポートまたはモデルを再バインドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c09e5-104">When you upload the report or model to the new server, you need to rebind it to a shared data source that is stored on the new report server.</span></span> <span data-ttu-id="c09e5-105">レポートまたはモデルの再バインドを行わないと、レポートまたはモデルが新しいレポート サーバーからアクセスされたときに正常に動作しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c09e5-105">If you don't rebind the report or model, it will not work correctly when accessed from the new report server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c09e5-106">レポートまたはモデルを共有データ ソースに再バインドする前に、データ ソースがレポート サーバーまたは SharePoint ライブラリに存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c09e5-106">Before rebinding a report or model to a shared data source, the data source must already exist on the report server or SharePoint library.</span></span> <span data-ttu-id="c09e5-107">データ ソースの詳細については、「[共有データ ソースを作成、変更、および削除する (SSRS)](create-modify-and-delete-shared-data-sources-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c09e5-107">For more information about data sources, see [Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md).</span></span>  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a><span data-ttu-id="c09e5-108">ネイティブ モードで実行されているレポート サーバー上の共有データ ソースにレポートまたはモデルをバインドするには</span><span class="sxs-lookup"><span data-stu-id="c09e5-108">To bind a report or model to a shared data source on a report server running in native mode</span></span>  
  
1.  <span data-ttu-id="c09e5-109">**レポート マネージャー**で、サーバーにアップロードしたレポートまたはモデルの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-109">In **Report Manager**, click the name of the report or model that you uploaded to the server.</span></span>  
  
     <span data-ttu-id="c09e5-110">[プロパティ] タブが開きます。</span><span class="sxs-lookup"><span data-stu-id="c09e5-110">The Properties tab opens.</span></span>  
  
2.  <span data-ttu-id="c09e5-111">**[データ ソース]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-111">Click **Data Sources**.</span></span>  
  
3.  <span data-ttu-id="c09e5-112">**[参照]** をクリックし、レポートまたはモデルをバインドするデータ ソースを参照します。</span><span class="sxs-lookup"><span data-stu-id="c09e5-112">Click **Browse**, and then navigate to the data source to which you want to bind the report or model.</span></span>  
  
4.  <span data-ttu-id="c09e5-113">データ ソースを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-113">Select the data source and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c09e5-114">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-114">Click **Apply**.</span></span>  
  
     <span data-ttu-id="c09e5-115">選択したデータ ソースにレポートまたはモデルがバインドされます。</span><span class="sxs-lookup"><span data-stu-id="c09e5-115">The report or model is now bound to the data source that you selected.</span></span>  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a><span data-ttu-id="c09e5-116">SharePoint 統合モードで実行されているレポート サーバー上の共有データ ソースにレポートまたはモデルをバインドするには</span><span class="sxs-lookup"><span data-stu-id="c09e5-116">To bind a report or model to a shared data source on a report server running in SharePoint integrated mode</span></span>  
  
1.  <span data-ttu-id="c09e5-117">まだライブラリが開いていない場合は、クイック起動バーでライブラリの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-117">If the library is not already open, click its name on the Quick Launch bar.</span></span> <span data-ttu-id="c09e5-118">ライブラリの名前が表示されていない場合は、 **[すべてのサイト コンテンツの表示]** をクリックし、ライブラリの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-118">If the name of your library does not appear, click **View All Site Content**, and then click the name of your library.</span></span>  
  
2.  <span data-ttu-id="c09e5-119">レポートまたはモデルをポイントし、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-119">Point to the report or model and click the down arrow.</span></span>  
  
3.  <span data-ttu-id="c09e5-120">**[データ ソースの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-120">Click **Manage Data Sources**.</span></span>  
  
4.  <span data-ttu-id="c09e5-121">**[dataSource1]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-121">Click **dataSource1**.</span></span>  
  
5.  <span data-ttu-id="c09e5-122">**[接続の種類]** 領域で、 **[共有データ ソース]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c09e5-122">In the **Connection Type** area, verify that **Shared data source** is selected.</span></span>  
  
6.  <span data-ttu-id="c09e5-123">[**データソースリンク**] 領域で、省略記号ボタン ([...]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-123">In the **Data Source Link** area, click the ellipsis (...) button.</span></span>  
  
7.  <span data-ttu-id="c09e5-124">使用するデータ ソースを探します。</span><span class="sxs-lookup"><span data-stu-id="c09e5-124">Locate the data source you want to use.</span></span>  
  
8.  <span data-ttu-id="c09e5-125">データ ソースを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-125">Select the data source and **click OK**.</span></span>  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. <span data-ttu-id="c09e5-126">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c09e5-126">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09e5-127">参照</span><span class="sxs-lookup"><span data-stu-id="c09e5-127">See Also</span></span>  
 <span data-ttu-id="c09e5-128">[ファイルまたはレポートをアップロード &#40;レポートマネージャー&#41;](../reports/upload-a-file-or-report-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c09e5-128">[Upload a File or Report &#40;Report Manager&#41;](../reports/upload-a-file-or-report-report-manager.md) </span></span>  
 <span data-ttu-id="c09e5-129">[Sharepoint モードで Reporting Services &#40;ドキュメントを SharePoint ライブラリにアップロード&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="c09e5-129">[Upload Documents to a SharePoint Library &#40;Reporting Services in SharePoint Mode&#41;](../upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="c09e5-130">[SharePoint 統合モードで Reporting Services &#40;共有データソースを作成および管理&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md) </span><span class="sxs-lookup"><span data-stu-id="c09e5-130">[Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md) </span></span>  
 <span data-ttu-id="c09e5-131">[共有データソース &#40;レポートマネージャーの作成、削除、または変更&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c09e5-131">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="c09e5-132">[Reporting Services のデータ接続、データソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="c09e5-132">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="c09e5-133">Reporting Services でサポートされるデータ ソース (SSRS)</span><span class="sxs-lookup"><span data-stu-id="c09e5-133">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
