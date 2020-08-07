---
title: Management Studio へのカスタム レポートの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07263edfb9b255257e0c79733c2c34b279b61cd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630775"
---
# <a name="add-a-custom-report-to-management-studio"></a><span data-ttu-id="c54a1-102">Management Studio へのカスタム レポートの追加</span><span class="sxs-lookup"><span data-stu-id="c54a1-102">Add a Custom Report to Management Studio</span></span>
  <span data-ttu-id="c54a1-103">ここでは、簡単な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを作成し、.rdl ファイルとして保存した後、そのファイルを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にカスタム レポートとして追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c54a1-103">This topic describes how to create a simple [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that is saved as an .rdl file, and then add that rdl file to [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] as a custom report.</span></span> [!INCLUDE[ssRS](../../includes/ssrs.md)] <span data-ttu-id="c54a1-104">では、さまざまな高度なレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c54a1-104">can create a wide variety of sophisticated reports.</span></span> <span data-ttu-id="c54a1-105">このトピックを使用してレポートを作成するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54a1-105">To create a report by using this topic, you must have [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] installed on the computer.</span></span> <span data-ttu-id="c54a1-106">[!INCLUDE[ssRS](../../includes/ssrs.md)] を使用してカスタム レポートを実行する場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]をインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c54a1-106">You do not have to install [!INCLUDE[ssRS](../../includes/ssrs.md)] on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to run a custom report using [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
  
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a><span data-ttu-id="c54a1-107">簡単なレポートを作成し、.rdl ファイルとして保存するには</span><span class="sxs-lookup"><span data-stu-id="c54a1-107">To create a simple report saved as an .rdl file</span></span>  
  
1.  <span data-ttu-id="c54a1-108">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントし、 **[SQL Server データ ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-108">Click **Start**, point to **Programs**, point to **Microsoft SQL Server**, and then click **SQL Server Data Tools**.</span></span>  
  
2.  <span data-ttu-id="c54a1-109">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-109">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="c54a1-110">**[プロジェクトの種類]** ボックスの一覧で、 **[ビジネス インテリジェンス プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-110">In the **Project Types** list, click **Business Intelligence Projects**.</span></span>  
  
4.  <span data-ttu-id="c54a1-111">**[テンプレート]** ボックスの一覧で、 **[レポート サーバー プロジェクト ウィザード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-111">In the **Templates** list, click **Report Server Project Wizard**.</span></span>  
  
5.  <span data-ttu-id="c54a1-112">**[名前]** に **「ConnectionsReport**」と入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-112">In **Name**, type **ConnectionsReport**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="c54a1-113">**レポート ウィザード** の最初のページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-113">On the **Report Wizard** introduction page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="c54a1-114">**[データ ソースを選択します]** ページの [名前] ボックスに、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]への接続で使用する名前を入力し、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-114">On the **Select the Data Source** page, in the Name box type a name for this connection to your [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Edit**.</span></span>  
  
8.  <span data-ttu-id="c54a1-115">**[接続プロパティ]** ダイアログ ボックスの **[サーバー名]** ボックスに、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c54a1-115">In the **Connection Properties** dialog box, in the **Server name** box, type the name of your instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
9. <span data-ttu-id="c54a1-116">**[データベース名の選択または入力]** ボックスに、任意の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースの名前 (「 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]」など) を入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-116">In the **Select or enter a database name** box, type the name of any database on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], such as [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], and then click **OK**.</span></span>  
  
10. <span data-ttu-id="c54a1-117">**[データ ソースを選択します]** ページで、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-117">On the **Select the Data Source** page, click **Next**.</span></span>  
  
11. <span data-ttu-id="c54a1-118">**[クエリのデザイン]** ページの **[クエリ文字列]** ボックスに、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを入力して、 [!INCLUDE[ssDE](../../includes/ssde-md.md)][次へ] **をクリックします。これは**への現在の接続一覧を表示するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c54a1-118">On the **Design the Query** page, in the **Query string** box, type the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that lists the current connections to your [!INCLUDE[ssDE](../../includes/ssde-md.md)], and then click **Next**.</span></span> <span data-ttu-id="c54a1-119">レポート ウィザードの [クエリ文字列] ボックスにレポート パラメーターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="c54a1-119">The Report Wizard Query string box will not accept report parameters.</span></span> <span data-ttu-id="c54a1-120">複雑なカスタム レポートは、手動で作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54a1-120">More complex custom reports must be created manually.</span></span>  
  
     `SELECT session_id, net_transport FROM sys.dm_exec_connections;`  
  
12. <span data-ttu-id="c54a1-121">**[レポートの種類を選択します]** ページで **[テーブル]** を選択して、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-121">On the **Select the Report Type** page, select **Tabular**, and then click **Finish**.</span></span>  
  
13. <span data-ttu-id="c54a1-122">**[ウィザードの完了]** ページの **[レポート名]** ボックスに「 **ConnectionsReport**」と入力し、 **[完了]** をクリックすると、レポートが作成され、保存されます。</span><span class="sxs-lookup"><span data-stu-id="c54a1-122">On the **Completing the Wizard** page, in the **Report name** box, type **ConnectionsReport**, and then click **Finish** to create and save the report.</span></span>  
  
14. <span data-ttu-id="c54a1-123">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を終了します。</span><span class="sxs-lookup"><span data-stu-id="c54a1-123">Close [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span>  
  
15. <span data-ttu-id="c54a1-124">データベース サーバー上でカスタム レポート用に作成したフォルダーに、 **ConnectionsReport.rdl** をコピーします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-124">Copy **ConnectionsReport.rdl** to a folder that you created on the database server for custom reports.</span></span>  
  
### <a name="to-add-a-report-to-management-studio"></a><span data-ttu-id="c54a1-125">レポートを Management Studio に追加するには</span><span class="sxs-lookup"><span data-stu-id="c54a1-125">To add a report to Management Studio</span></span>  
  
-   <span data-ttu-id="c54a1-126">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]のオブジェクト エクスプローラーでノードを右クリックし、 **[レポート]** をポイントして、 **[カスタム レポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-126">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], right-click a node in Object Explorer, point to **Reports**, click **Custom Reports**.</span></span> <span data-ttu-id="c54a1-127">**[ファイルを開く]** ダイアログ ボックスで、カスタム レポート フォルダーに移動し、 **ConnectionsReport.rdl** ファイルを選択して、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-127">In the **Open File** dialog box, locate the custom reports folder and select the **ConnectionsReport.rdl** file, and then click **Open**.</span></span>  
  
     <span data-ttu-id="c54a1-128">新しいカスタム レポートは、初めてオブジェクト エクスプローラーのノードから開いたときに、最近使用した一覧に追加されます。この一覧はノードのショートカット メニューの **[カスタム レポート]** の下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c54a1-128">When a new custom report is first opened from an Object Explorer node, the custom report is added to the most recently used list under **Custom Reports** on the shortcut menu of that node.</span></span> <span data-ttu-id="c54a1-129">標準レポートも、初めて開いたときに **[カスタム レポート]** の下の最近使用した一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c54a1-129">When a standard report is opened for the first time, it will also appear on the most recently used list under **Custom Reports**.</span></span> <span data-ttu-id="c54a1-130">カスタム レポート ファイルを削除した場合は、次にそのアイテムを選択したときに、最近使用した一覧からアイテムを削除するというプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c54a1-130">If a custom report file is deleted, the next time that the item is selected, a prompt will appear to delete the item from the most recently used list.</span></span>  
  
    1.  <span data-ttu-id="c54a1-131">最近使用した一覧の表示ファイル数を変更するには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[環境]** フォルダーを展開して **[全般]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c54a1-131">To change the number of files that are displayed on the recently used list, on the **Tools** menu, click **Options,** expand the **Environment** folder, and then click **General**.</span></span>  
  
    2.  <span data-ttu-id="c54a1-132">**[最近使用したファイルの一覧]** の数を調整します。</span><span class="sxs-lookup"><span data-stu-id="c54a1-132">Adjust the number for **Display files in recently used list**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c54a1-133">参照</span><span class="sxs-lookup"><span data-stu-id="c54a1-133">See Also</span></span>  
 <span data-ttu-id="c54a1-134">[Management Studio のカスタムレポート](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="c54a1-134">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="c54a1-135">[オブジェクトエクスプローラーノードのプロパティでカスタムレポートを使用する](use-custom-reports-with-object-explorer-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c54a1-135">[Use Custom Reports with Object Explorer Node Properties](use-custom-reports-with-object-explorer-node-properties.md) </span></span>  
 <span data-ttu-id="c54a1-136">[抑制カスタムレポートの実行に関する警告](unsuppress-run-custom-report-warnings.md) </span><span class="sxs-lookup"><span data-stu-id="c54a1-136">[Unsuppress Run Custom Report Warnings](unsuppress-run-custom-report-warnings.md) </span></span>  
 [<span data-ttu-id="c54a1-137">Reporting Services &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="c54a1-137">Reporting Services &#40;SSRS&#41;</span></span>](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
