---
title: レポート (SharePoint 統合モードの Reporting Services) で Office データ接続 (.odc) を使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Office Data Connection (.odc) files
- SharePoint integration [Reporting Services], shared data sources
- .odc files
ms.assetid: e8d6896d-f886-4390-8b5d-96f0a50c250c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d795c46f46b45511079ac03add2d18214ac54489
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631565"
---
# <a name="use-an-office-data-connection-odc-with-reports-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="bbc38-102">レポートで Office Data Connection (.odc) を使用する (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="bbc38-102">Use an Office Data Connection (.odc) with Reports (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="bbc38-103">限られたシナリオでは、既存の Office データ接続 (.odc) ファイルを使用して、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートに接続情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-103">For limited scenarios, you can use an existing Office Data Connection (.odc) file to provide connection information to a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.</span></span> <span data-ttu-id="bbc38-104">共有データ ソースの作成時には、.rsds ファイルの代わりに .odc ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-104">An .odc file can be used in place of an .rsds file when you create a shared data source.</span></span> <span data-ttu-id="bbc38-105">レポート サーバーでは、.rsds ファイルの場合と同様に .odc ファイルを使用して、データ ソースの種類、接続文字列、および資格情報をファイルから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-105">The report server uses an .odc file in the same way it uses an .rsds file; it reads the file for the data source type, a connection string, and credential information.</span></span>  
  
 <span data-ttu-id="bbc38-106">すべての .odc ファイルが [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートで使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-106">Not all .odc files can be used with a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report.</span></span> <span data-ttu-id="bbc38-107">.odc ファイルを使用できるかどうかは、次に示すデータ処理拡張機能や、レポートおよび .odc ファイルの特性によって決まります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-107">The data processing extension and characteristics of the report and .odc file determine whether an .odc can be used:</span></span>  
  
-   <span data-ttu-id="bbc38-108">レポートは、OLE DB または ODBC データ プロバイダーと連携できるように設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-108">The report must be designed to work with an OLE DB or ODBC data provider.</span></span> <span data-ttu-id="bbc38-109">他のデータ処理拡張機能を使用してレポートを作成した場合、レポートとそのクエリには OLE DB または ODBC データ プロバイダーでサポートされていない機能が含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-109">If you used a different data processing extension to create the report, the report or its queries might include functionality that is not supported by the OLE DB or ODBC data provider.</span></span>  
  
-   <span data-ttu-id="bbc38-110">.odc ファイルには所定の要素と構造が求められます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-110">The .odc file must have the expected elements and structure.</span></span> <span data-ttu-id="bbc38-111">このファイルには、レポート サーバーで読み取ることができるように、データ プロバイダーと資格情報に関する設定を明示的に記述しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-111">The data provider and credential settings must be set explicitly in the file so that they can be read by the report server.</span></span> <span data-ttu-id="bbc38-112">これらの値を設定するのに最も適した方法は、.odc ファイルを SharePoint ライブラリにアップロードする前にエクスポートすることです。</span><span class="sxs-lookup"><span data-stu-id="bbc38-112">The best way to set these values is to export the .odc file before uploading it to the SharePoint library.</span></span>  
  
-   <span data-ttu-id="bbc38-113">.odc ファイルには、接続の種類として OLE DB または ODBC を指定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-113">The .odc file must specify a connection type of OLE DB or ODBC.</span></span>  
  
-   <span data-ttu-id="bbc38-114">.odc ファイルには、接続文字列を指定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-114">The .odc file must specify a connection string.</span></span>  
  
-   <span data-ttu-id="bbc38-115">資格情報は、[`None`]、[`Stored`]、または [`Integrated`] に設定できます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-115">Credentials can be set to `None`, `Stored`, or `Integrated`.</span></span> <span data-ttu-id="bbc38-116">資格情報の使用方法が [`Stored`] に設定されている場合、レポート サーバーでは保存されている資格情報を使用せず、ユーザーに資格情報を指定するように求めます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-116">If the credentials method is set to `Stored`, the report server will prompt the user for credentials instead of using the stored credentials.</span></span> <span data-ttu-id="bbc38-117">レポート サーバーでは、.odc ファイルに定義されている保存済みの資格情報を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-117">The report server cannot use stored credentials as defined in the .odc file.</span></span>  
  
-   <span data-ttu-id="bbc38-118">データ ソースのスキーマは、レポートの作成に使用されたスキーマと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-118">The data source must have schema that is identical to the one used to create the report.</span></span> <span data-ttu-id="bbc38-119">データ構造が異なる場合は、レポートが実行されません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-119">If the data structures are different, the report will not run.</span></span>  
  
-   <span data-ttu-id="bbc38-120">.odc ファイルは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007 で作成する必要があります (これより古いバージョンの .odc ファイルはレポート定義ファイルとの互換性がありません)。</span><span class="sxs-lookup"><span data-stu-id="bbc38-120">The .odc file must be created in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office 2007 (older versions of .odc are not compatible with report definition files).</span></span>  
  
 <span data-ttu-id="bbc38-121">.odc データ ソースの種類が、サポートされているデータ ソースの種類に似ていても、レポート サーバーで処理できないデータ ソースへの接続が指定された .odc ファイルを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-121">You cannot use .odc files that specify connections to data sources that cannot be processed on a report server, even if the .odc data source types look similar to supported data source types.</span></span> <span data-ttu-id="bbc38-122">具体的には、Microsoft Access、Web、またはテキスト ファイルからデータを取得する .odc ファイルを Microsoft Excel 2007 で作成した場合、その .odc ファイルを使用してレポートにデータを提供することはできません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-122">Specifically, if you created an .odc file in Microsoft Excel 2007 that retrieves data from Microsoft Access, the Web, or a text file, you cannot use that .odc file to provide data to a report.</span></span>  
  
 <span data-ttu-id="bbc38-123">レポート ビルダーのレポートとモデルには、.odc ファイルを連携させることができません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-123">Report Builder reports and models do not work with .odc file.</span></span> <span data-ttu-id="bbc38-124">.odc ファイルを使用してモデルを生成することはできません。また、.odc ファイルにリンクする共有データ ソースが使用されるようにモデルを構成することもできません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-124">You cannot use an .odc file to generate a model, and you cannot configure the model to use a shared data source that links to an .odc file.</span></span>  
  
 <span data-ttu-id="bbc38-125">.odc ファイルに関する知識があまりなくても、次の手順を使用して .odc ファイルを作成およびエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-125">If you are not familiar with .odc files, you can use the following instructions to create and export one.</span></span> <span data-ttu-id="bbc38-126">OLE DB データ ソース用に .odc ファイルを作成する簡単な方法の 1 つは、Excel 2007 とデータ接続ウィザードを使用することです。</span><span class="sxs-lookup"><span data-stu-id="bbc38-126">One easy way to create an .odc file for an OLE DB data source is to use Excel 2007 and the Data Connection Wizard.</span></span> <span data-ttu-id="bbc38-127">ただし、このウィザードではデータ ソースが作成されないので、定義済みの外部データ ソースを用意しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-127">Note that the wizard does not create a data source; you must have an external data source that is already defined.</span></span>  
  
 <span data-ttu-id="bbc38-128">既存の .odc ファイルは、レポートやクエリと完全な互換性がある場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="bbc38-128">An existing .odc file should only be used if it is fully compatible with the report and queries.</span></span> <span data-ttu-id="bbc38-129">レポートまたは .odc ファイルに対して大幅な変更が必要になるようなエラーが発生する場合は、レポート用に .rsds ファイルを新しく作成します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-129">If you run into errors that require significant modifications to either the report or to the .odc file, you should create a new .rsds file for the report.</span></span> <span data-ttu-id="bbc38-130">.rsds ファイルを使用する共有データ ソースを作成する方法の詳細については、「[共有データ ソースを作成および管理する (Reporting Services の SharePoint 統合モード)](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbc38-130">For more information about how to create a shared data source that uses an .rsds file, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md).</span></span>  
  
### <a name="to-create-and-export-an-odc-file"></a><span data-ttu-id="bbc38-131">.odc ファイルを作成してエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="bbc38-131">To create and export an .odc file</span></span>  
  
1.  <span data-ttu-id="bbc38-132">Excel 2007 を起動します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-132">Start Excel 2007.</span></span>  
  
2.  <span data-ttu-id="bbc38-133">**[データ]** タブで、 **[外部データの取り込み]** グループの **[その他のデータ ソース]** をクリックし、 **[データ接続ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-133">On the **Data** tab, in the **Get External Data** group, click **From Other Sources**, and then click **From Data Connection Wizard**.</span></span>  
  
3.  <span data-ttu-id="bbc38-134">**[その他/詳細]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-134">Select **Other/Advanced**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="bbc38-135">**[Microsoft OLE DB Provider for SQL Server]** を選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-135">Select **Microsoft OLE DB Provider for SQL Server**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="bbc38-136">サーバー名 (既定ではコンピューターのネットワーク名)、および有効なログインとデータベース権限が与えられたユーザー アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-136">Enter the name of the server (by default, it is the network name of the computer) and a user account that has a valid login and database permissions.</span></span> <span data-ttu-id="bbc38-137">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-137">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="bbc38-138">データベースを選択して **[OK]** をクリックし、 **[データ リンク]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-138">Select a database, and then click **OK** to close the **Data Link** dialog box.</span></span>  
  
7.  <span data-ttu-id="bbc38-139">**[指定したテーブルに接続]** チェック ボックスは既定でオンになっています。</span><span class="sxs-lookup"><span data-stu-id="bbc38-139">The **Connect to specific table** check box is selected by default.</span></span> <span data-ttu-id="bbc38-140">このオプションは、特定のテーブルからデータを取得する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-140">It is used to retrieve data from a specific table.</span></span> <span data-ttu-id="bbc38-141">レポート サーバーでは .odc ファイル内のすべてのクエリが無視されるので、このチェック ボックスはオンとオフのどちらになっていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="bbc38-141">The report server ignores all queries in an .odc file, so it does not matter whether you select or clear the check box.</span></span> <span data-ttu-id="bbc38-142">レポートのデータを取得するクエリは、外部ファイルではなくレポート定義ファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="bbc38-142">Queries that retrieve data for a report are included in a report definition file and not in external files.</span></span>  
  
8.  <span data-ttu-id="bbc38-143">接続が開いている間は、プロパティを編集してエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-143">While the connection is open, you can edit properties and export it.</span></span> <span data-ttu-id="bbc38-144">**[データ]** タブで、 **[接続]** グループの **[プロパティ]** をクリックし、接続名の隣にある **[接続のプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-144">On the **Data** tab, in the **Connections** group, click **Properties**, and then click the **Connection Properties** button next to the connection name.</span></span>  
  
9. <span data-ttu-id="bbc38-145">**[定義]** タブで、 **[接続ファイルのエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-145">On the **Definition** tab, click **Export Connection File**.</span></span>  
  
10. <span data-ttu-id="bbc38-146">ファイル名を入力し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-146">Enter a name for the file, and then click **Save**.</span></span> <span data-ttu-id="bbc38-147">アプリケーションと開いているすべてのファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-147">Close the application and all open files.</span></span>  
  
### <a name="to-upload-and-use-an-odc-file"></a><span data-ttu-id="bbc38-148">.odc ファイルをアップロードして使用するには</span><span class="sxs-lookup"><span data-stu-id="bbc38-148">To upload and use an .odc file</span></span>  
  
1.  <span data-ttu-id="bbc38-149">接続ファイルのアップロード先となるライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-149">Open the library into which you want to upload the connection file.</span></span>  
  
2.  <span data-ttu-id="bbc38-150">**[アップロード]** メニューの **[ドキュメントのアップロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-150">On the **Upload** menu, click **Upload document**.</span></span>  
  
3.  <span data-ttu-id="bbc38-151">**[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-151">Click **Browse**.</span></span>  
  
4.  <span data-ttu-id="bbc38-152">作成した .odc ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-152">Select the .odc file you created.</span></span> <span data-ttu-id="bbc38-153">既定では、.odc ファイルは [マイ ドキュメント] フォルダーの [My Data Sources] にあります。</span><span class="sxs-lookup"><span data-stu-id="bbc38-153">By default, the .odc file is in the My Documents folder, in My Data Sources.</span></span>  
  
5.  <span data-ttu-id="bbc38-154">**[開く]** をクリックしてファイルを選択し、 **[OK]** をクリックして選択したファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-154">Click **Open** to select the file, click **OK** to save the selection.</span></span> <span data-ttu-id="bbc38-155">新しいアイテムのプロパティ ページが自動的に開きます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-155">The properties page for the new item opens automatically.</span></span>  
  
6.  <span data-ttu-id="bbc38-156">[コンテンツ タイプ] で **[レポート データ ソース]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-156">In Content Type, select **Report Data Source**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="bbc38-157">レポートをポイントします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-157">Point to a report.</span></span>  
  
8.  <span data-ttu-id="bbc38-158">下矢印をクリックし、 **[データ ソースの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-158">Click the down arrow, and select **Manage Data Sources**.</span></span>  
  
9. <span data-ttu-id="bbc38-159">データ ソース名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-159">Click the data source name.</span></span>  
  
10. <span data-ttu-id="bbc38-160">レポートでカスタム データ ソース情報を使用する場合は、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-160">If the report uses custom data source information, click **Shared**.</span></span>  
  
11. <span data-ttu-id="bbc38-161">**[データ ソース リンク]** で、参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbc38-161">In **Data Source Link**, click the browse (**...**) button.</span></span>  
  
12. <span data-ttu-id="bbc38-162">アップロードする .odc ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-162">Select the .odc file you just uploaded.</span></span>  
  
13. <span data-ttu-id="bbc38-163">**[OK]** をクリックしてファイルを選択し、 **[OK]** をクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="bbc38-163">Click **OK** to select the file, and then click **OK** to save your changes.</span></span>  
  
     <span data-ttu-id="bbc38-164">[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースおよびサンプル レポートで上記の手順を行う場合、追加設定なしで .odc ファイルと連携して動作するのは Company Sales レポートのみであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bbc38-164">If you are trying these steps with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] sample database and sample reports, be aware that only the Company Sales report will work out-of-the-box with an .odc file.</span></span> <span data-ttu-id="bbc38-165">他のサンプル レポートには、OLE DB プロバイダーと互換性のないクエリ パラメーターや機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bbc38-165">The other sample reports contain query parameters and features that do not work with the OLE DB provider.</span></span> <span data-ttu-id="bbc38-166">ただし、レポート デザイナーでレポートを変更しておくことにより、レポートを OLE DB プロバイダーと連携させることもできます。</span><span class="sxs-lookup"><span data-stu-id="bbc38-166">However, you can make the reports work with the OLE DB provider if you modify them first in Report Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc38-167">参照</span><span class="sxs-lookup"><span data-stu-id="bbc38-167">See Also</span></span>  
 [<span data-ttu-id="bbc38-168">共有データ ソースを作成、変更、および削除する &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="bbc38-168">Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;</span></span>](create-modify-and-delete-shared-data-sources-ssrs.md)  
  
  
