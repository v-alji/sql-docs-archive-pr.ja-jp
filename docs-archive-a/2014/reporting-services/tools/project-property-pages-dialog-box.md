---
title: '[プロパティ ページ] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rpt.rptdesigner.projectpropertypages.general.f1
helpviewer_keywords:
- Project Property Pages dialog box
ms.assetid: 209d9e22-37fc-418f-8739-83adcf447d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ae5ab7c68c9a95759d27ca2785f99377c98942a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716006"
---
# <a name="project-property-pages-dialog-box"></a><span data-ttu-id="c3207-102">[プロパティ ページ] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="c3207-102">Project Property Pages Dialog Box</span></span>
  <span data-ttu-id="c3207-103">プロジェクトのプロパティ ページを使用すると、レポート サーバー プロジェクトの配置プロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c3207-103">Use the project property pages to configure deployment properties for a Report Server project.</span></span> <span data-ttu-id="c3207-104">このダイアログボックスを開くには、[**プロジェクト**] メニューの [プロパティ] をクリックし _\<Report Project Name>_ **Properties**ます。</span><span class="sxs-lookup"><span data-stu-id="c3207-104">To open this dialog box, from the **Project** menu, click _\<Report Project Name>_**Properties**.</span></span>  
  
 <span data-ttu-id="c3207-105">構成プロパティを定義した後は、ツール バーの **[ソリューション構成]** ボックスの一覧から構成を選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c3207-105">After you define configuration properties, you can select a configuration from the **Solution Configurations** drop-down list on the toolbar.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c3207-106">Options</span><span class="sxs-lookup"><span data-stu-id="c3207-106">Options</span></span>  
 <span data-ttu-id="c3207-107">**構成**</span><span class="sxs-lookup"><span data-stu-id="c3207-107">**Configuration**</span></span>  
 <span data-ttu-id="c3207-108">編集する構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="c3207-108">Select the configuration to edit.</span></span> <span data-ttu-id="c3207-109">初期状態で使用できる構成は、 **[Debug]**、 **[DebugLocal]**、および **[Release]** です。</span><span class="sxs-lookup"><span data-stu-id="c3207-109">Initially, the following configurations are available: **Debug**, **DebugLocal**, and **Release**.</span></span> <span data-ttu-id="c3207-110">アクティブな構成が、 **Active(Debug)** のように最初に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c3207-110">The active configuration appears first, for example, **Active(Debug)**.</span></span>  
  
 <span data-ttu-id="c3207-111">複数の構成のプロパティを同時に表示するには、 **[すべての構成]** または **[複数の構成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c3207-111">To see properties for more than one configuration at the same time, select **All Configurations** or **Multiple Configurations**.</span></span>  
  
 <span data-ttu-id="c3207-112">新しく構成を作成するには、ツール バーの **[構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c3207-112">To create additional configurations, click **Configuration Manager** on the toolbar.</span></span>  
  
 <span data-ttu-id="c3207-113">**構成マネージャー**</span><span class="sxs-lookup"><span data-stu-id="c3207-113">**Configuration Manager**</span></span>  
 <span data-ttu-id="c3207-114">ソリューション全体の構成を管理するか、さらに構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="c3207-114">Manage configurations for the entire solution or to add additional configurations.</span></span> <span data-ttu-id="c3207-115">詳細については、のドキュメントを参照してください [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c3207-115">For more information, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="c3207-116">**OutputPath**</span><span class="sxs-lookup"><span data-stu-id="c3207-116">**OutputPath**</span></span>  
 <span data-ttu-id="c3207-117">ビルドの検証、配置、およびレポートのプレビューで使用されるレポート定義の保存先のパスを入力するか、貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c3207-117">Type or paste the path to store the report definition used in build verification, deployment, and preview of reports.</span></span> <span data-ttu-id="c3207-118">このパスは、プロジェクトに使用するパス、およびプロジェクトのパスの下にある子フォルダーの相対パスとは異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3207-118">The path must be different than the path that you use for the project and a relative path that is a child folder under the path of the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c3207-119">複数の構成を使用して、実行するタスクに応じてパスを切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="c3207-119">You can use multiple configurations to switch among paths depending on the task you perform.</span></span>  
  
 <span data-ttu-id="c3207-120">**ErrorLevel**</span><span class="sxs-lookup"><span data-stu-id="c3207-120">**ErrorLevel**</span></span>  
 <span data-ttu-id="c3207-121">エラーとしてレポートされるビルドの問題の重大度を入力します。</span><span class="sxs-lookup"><span data-stu-id="c3207-121">Type the severity of the build issues that are reported as errors.</span></span> <span data-ttu-id="c3207-122">**[ErrorLevel]** の値以下の重大度レベルを持つ問題は、エラーとしてレポートされます。それ以外の問題は、警告としてレポートされます。</span><span class="sxs-lookup"><span data-stu-id="c3207-122">Issues with severity levels less than or equal to the value of **ErrorLevel** are reported as errors; otherwise, the issues are reported as warnings.</span></span> <span data-ttu-id="c3207-123">エラーが発生すると、ビルド タスクが失敗する原因になります。</span><span class="sxs-lookup"><span data-stu-id="c3207-123">Any error will cause the build task to fail.</span></span> <span data-ttu-id="c3207-124">有効な重大度レベルは、0 ～ 4 の範囲です。</span><span class="sxs-lookup"><span data-stu-id="c3207-124">The valid severity levels are 0 through 4 inclusively.</span></span> <span data-ttu-id="c3207-125">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="c3207-125">The default value is 2.</span></span>  
  
 <span data-ttu-id="c3207-126">**[StartItem]**</span><span class="sxs-lookup"><span data-stu-id="c3207-126">**StartItem**</span></span>  
 <span data-ttu-id="c3207-127">プロジェクトがレポート サーバーにパブリッシュされた後に Web ブラウザーに表示されるレポート、またはローカルでプロジェクトを実行するときにプレビュー ウィンドウに表示されるレポートを選択します。</span><span class="sxs-lookup"><span data-stu-id="c3207-127">Select the report that is displayed in the Web browser after the project is published to the report server or in the preview window when the project is run locally.</span></span> <span data-ttu-id="c3207-128">開始アイテムは、プロジェクトをビルドしても配置しない構成の場合、および **[Debug]** コマンド (**F5**) を使用する場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="c3207-128">A start item is required for configurations that build but do not deploy the project and for using the **Debug** command (**F5**).</span></span> <span data-ttu-id="c3207-129">このアイテムは、プロジェクトを配置する構成では必須です。</span><span class="sxs-lookup"><span data-stu-id="c3207-129">It is required for configurations that deploy the project.</span></span>  
  
 <span data-ttu-id="c3207-130">**[OverwriteDataSources]**</span><span class="sxs-lookup"><span data-stu-id="c3207-130">**OverwriteDataSources**</span></span>  
 <span data-ttu-id="c3207-131">レポートのパブリッシュ時に、サーバー上のデータ ソースをプロジェクト内のデータ ソースで上書きする場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c3207-131">Select **True** to overwrite the data source on the server with the data source in the project when the reports are published.</span></span> <span data-ttu-id="c3207-132">サーバー上の既存のデータ ソースを残す場合は、 **[False]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c3207-132">Select **False** to leave the existing data source on the server.</span></span>  
  
 <span data-ttu-id="c3207-133">**[TargetServerVersion]**</span><span class="sxs-lookup"><span data-stu-id="c3207-133">**TargetServerVersion**</span></span>  
 <span data-ttu-id="c3207-134">またはのいずれか [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] のバージョンを選択 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] するか、[**バージョンの検出**] を選択して、 **TargetServer URL**プロパティで識別されるサーバーにインストールされているバージョンを自動的に判別します。</span><span class="sxs-lookup"><span data-stu-id="c3207-134">Select either the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or select **Detect Version** to automatically determine the version installed on the server identified by the **TargetServer URL** property.</span></span> <span data-ttu-id="c3207-135">既定値は**SQL Server 2008 R2**です。</span><span class="sxs-lookup"><span data-stu-id="c3207-135">The default value is **SQL Server 2008 R2**.</span></span>  
  
 <span data-ttu-id="c3207-136">**[TargetDataSourceFolder]**</span><span class="sxs-lookup"><span data-stu-id="c3207-136">**TargetDataSourceFolder**</span></span>  
 <span data-ttu-id="c3207-137">パブリッシュした共有データ ソースを保存するフォルダーの名前です。</span><span class="sxs-lookup"><span data-stu-id="c3207-137">The name of the folder in which to store the published shared data sources.</span></span> <span data-ttu-id="c3207-138">フォルダーを指定しない場合、レポートと同じフォルダーにデータ ソースがパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="c3207-138">If you do not specify a folder, the data source is published to the same folder as the report.</span></span> <span data-ttu-id="c3207-139">フォルダーがレポート サーバー上に存在しない場合は、レポートのパブリッシュ時に、レポート デザイナーによってフォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3207-139">If the folder does not exist on the report server, Report Designer creates the folder when the reports are published.</span></span>  
  
 <span data-ttu-id="c3207-140">ネイティブ モードで実行されているレポート サーバーにパブリッシュする場合は、フォルダー階層の完全なパスをルートから指定します。</span><span class="sxs-lookup"><span data-stu-id="c3207-140">When publishing to a report server running in native mode, specify the full path of the folder hierarchy starting at the root.</span></span> <span data-ttu-id="c3207-141">たとえば、「Folder1/Folder2/Folder3」のように指定します。</span><span class="sxs-lookup"><span data-stu-id="c3207-141">For example, Folder1/Folder2/Folder3.</span></span>  
  
 <span data-ttu-id="c3207-142">SharePoint 統合モードで実行されているレポート サーバーにパブリッシュする場合は、SharePoint ライブラリの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3207-142">When publishing to a report server running in SharePoint integrated mode, use a URL to the SharePoint library.</span></span> <span data-ttu-id="c3207-143">たとえば、http:// *\<servername>/\<site>* /documents/myfolder</span><span class="sxs-lookup"><span data-stu-id="c3207-143">For example, http://*\<servername>/\<site>*/Documents/MyFolder.</span></span>  
  
 <span data-ttu-id="c3207-144">**[TargetReportFolder]**</span><span class="sxs-lookup"><span data-stu-id="c3207-144">**TargetReportFolder**</span></span>  
 <span data-ttu-id="c3207-145">パブリッシュしたレポートを保存するフォルダーの名前です。</span><span class="sxs-lookup"><span data-stu-id="c3207-145">The name of the folder in which to store the published reports.</span></span> <span data-ttu-id="c3207-146">既定値は、レポート プロジェクトの名前です。</span><span class="sxs-lookup"><span data-stu-id="c3207-146">By default, this is the name of the report project.</span></span> <span data-ttu-id="c3207-147">フォルダーがレポート サーバー上に存在しない場合は、レポートのパブリッシュ時に、レポート デザイナーによってフォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c3207-147">If the folder does not exist on the report server, Report Designer creates the folder when the reports are published.</span></span>  
  
 <span data-ttu-id="c3207-148">ネイティブ モードで実行されているレポート サーバーにパブリッシュする場合は、フォルダー階層の完全なパスをルートから指定します。</span><span class="sxs-lookup"><span data-stu-id="c3207-148">When publishing to a report server running in native mode, specify the full path of the folder hierarchy starting at the root.</span></span> <span data-ttu-id="c3207-149">フォルダーが別の場所に存在する場合は、フォルダーへのパスをルートから指定します。たとえば、「Folder1/Folder2/Folder3」のように指定します。</span><span class="sxs-lookup"><span data-stu-id="c3207-149">If a folder is located within another folder, include a path to the folder starting at the root, such as Folder1/Folder2/Folder3.</span></span>  
  
 <span data-ttu-id="c3207-150">SharePoint 統合モードで実行されているレポート サーバーにパブリッシュする場合は、SharePoint ライブラリの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3207-150">When publishing to a report server running in SharePoint integrated mode, use a URL to SharePoint library.</span></span> <span data-ttu-id="c3207-151">たとえば、http:// *\<servername>* / *\<site>* /documents/myfolder</span><span class="sxs-lookup"><span data-stu-id="c3207-151">For example, http://*\<servername>*/*\<site>*/Documents/MyFolder.</span></span>  
  
 <span data-ttu-id="c3207-152">**[TargetServerURL]**</span><span class="sxs-lookup"><span data-stu-id="c3207-152">**TargetServerURL**</span></span>  
 <span data-ttu-id="c3207-153">対象レポート サーバーの URL です。</span><span class="sxs-lookup"><span data-stu-id="c3207-153">The URL of the target report server.</span></span> <span data-ttu-id="c3207-154">レポートをパブリッシュする前に、このプロパティを有効なレポート サーバーの URL に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3207-154">Before you publish a report, you must set this property to a valid report server URL.</span></span>  
  
 <span data-ttu-id="c3207-155">ネイティブ モードで実行されているレポート サーバーにパブリッシュする場合は、レポート サーバーの仮想ディレクトリの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="c3207-155">When publishing to a report server running in native mode, use the URL of the virtual directory of the report server.</span></span> <span data-ttu-id="c3207-156">たとえば、http://のように \<server> します。</span><span class="sxs-lookup"><span data-stu-id="c3207-156">For example, http://\<server>/reportserver.</span></span> <span data-ttu-id="c3207-157">これは、レポート マネージャーではなく、レポート サーバーの仮想ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="c3207-157">This is the virtual directory of the report server, not Report Manager.</span></span> <span data-ttu-id="c3207-158">既定では、レポート サーバーは、"reportserver" という名前の仮想ディレクトリにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c3207-158">By default, the report server is installed in a virtual directory named "reportserver".</span></span>  
  
 <span data-ttu-id="c3207-159">SharePoint 統合モードで動作しているレポート サーバーにパブリッシュする場合は、SharePoint トップレベル サイトまたはサブサイトの URL を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3207-159">When publishing to a report server running in SharePoint integrated mode, use a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="c3207-160">サイトを指定しなかった場合は、既定のトップレベル サイトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c3207-160">If you do not specify a site, the default top-level site is used.</span></span> <span data-ttu-id="c3207-161">たとえば、http:// \<*servername> *、http://<* servername */\<*site>* または http://\* のように \<*servername> */\<*site>* / \<*subsite> なります。</span><span class="sxs-lookup"><span data-stu-id="c3207-161">For example, http://\<*servername>*, http://<* servername*/\<*site>* or http://\<*servername>*/\<*site>*/\<*subsite>\*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3207-162">参照</span><span class="sxs-lookup"><span data-stu-id="c3207-162">See Also</span></span>  
 <span data-ttu-id="c3207-163">[レポートのパブリッシュ](../publish-reports.md) </span><span class="sxs-lookup"><span data-stu-id="c3207-163">[Publish Reports](../publish-reports.md) </span></span>  
 <span data-ttu-id="c3207-164">[SharePoint ライブラリへのレポートのパブリッシュ](../reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="c3207-164">[Publish a Report to a SharePoint Library](../reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="c3207-165">[展開プロパティを設定 &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="c3207-165">[Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) </span></span>  
 [<span data-ttu-id="c3207-166">レポート デザイナーの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="c3207-166">Report Designer F1 Help</span></span>](report-designer-f1-help.md)  
  
  
