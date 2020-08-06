---
title: プロジェクトまたはソリューションとしてスクリプトを保存する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 72dfd37f-dbe7-4d1d-bda6-7eb54c7922d3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9fade3900c8859f211bb0c66820dc97792262481
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717132"
---
# <a name="save-scripts-as-projects-or-solutions"></a><span data-ttu-id="50f7d-102">プロジェクトまたはソリューションとしてスクリプトを保存する</span><span class="sxs-lookup"><span data-stu-id="50f7d-102">Save Scripts as Projects or Solutions</span></span>
  <span data-ttu-id="50f7d-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio を使い慣れている開発者であれば、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のソリューション エクスプローラーにもすぐに慣れることができます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-103">Developers familiar with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio will welcome Solution Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="50f7d-104">業務を支援するスクリプトはスクリプト プロジェクトにグループ化することができ、スクリプト プロジェクトはソリューションとしてまとめて管理できます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-104">The scripts that support your business can be grouped into script projects, and the script projects can be managed together as a solution.</span></span> <span data-ttu-id="50f7d-105">スクリプト プロジェクトまたはソリューションに格納したスクリプトは、グループとして一括して開けるほか、Visual SourceSafe などのソース管理製品にまとめて保存することができます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-105">When scripts are placed in script projects and solutions they can be opened together as a group, or saved together to a source control product such as Visual SourceSafe.</span></span> <span data-ttu-id="50f7d-106">スクリプト プロジェクトは、スクリプトを適切に実行するための接続情報を保持し、テキスト ファイルなどの非スクリプト ファイルを保持することもできます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-106">Script projects include the connection information for the scripts to execute properly, and can include non-script files such as a supporting text file.</span></span>  
  
 <span data-ttu-id="50f7d-107">次の実習では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースにクエリを実行する短いスクリプトを作成し、スクリプト プロジェクトとソリューションに格納します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-107">The following practice creates a short script that queries the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, placed in a script project and solution.</span></span>  
  
## <a name="using-script-projects-and-solutions"></a><span data-ttu-id="50f7d-108">スクリプト プロジェクトとソリューションの使用</span><span class="sxs-lookup"><span data-stu-id="50f7d-108">Using Script Projects and Solutions</span></span>  
  
#### <a name="to-create-a-script-project-and-solution"></a><span data-ttu-id="50f7d-109">スクリプト プロジェクトとソリューションを作成するには</span><span class="sxs-lookup"><span data-stu-id="50f7d-109">To create a script project and solution</span></span>  
  
1.  <span data-ttu-id="50f7d-110">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を開き、オブジェクト エクスプローラーを使用してサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-110">Open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], and connect to a server with Object Explorer.</span></span>  
  
2.  <span data-ttu-id="50f7d-111">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f7d-111">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="50f7d-112">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="50f7d-113">**[名前]** ボックスに「 **StatusCheck**」と入力し、 **[テンプレート]** で **[SQL Server スクリプト]** をクリックして、 **[OK]** をクリックします。新しいソリューションとスクリプト プロジェクトが開きます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-113">In the **Name** text box, type **StatusCheck**, click **SQL Server Scripts** in **Templates**, and then click **OK** to open a new solution and script project.</span></span>  
  
4.  <span data-ttu-id="50f7d-114">ソリューション エクスプローラーで **[接続]** を右クリックし、 **[新しい接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f7d-114">In Solution Explorer, right-click **Connections**, and then click **New Connection**.</span></span> <span data-ttu-id="50f7d-115">**[サーバーへの接続]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-115">The **Connect to Server** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="50f7d-116">**[サーバー名]** ボックスにサーバー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-116">In the **Server name** list box, type the name of your server.</span></span>  
  
6.  <span data-ttu-id="50f7d-117">**[オプション]** をクリックし、 **[接続プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f7d-117">Click **Options**, and then click the **Connection Properties** tab.</span></span>  
  
7.  <span data-ttu-id="50f7d-118">**[データベースへの接続]** ボックスで [サーバーの参照] をクリックし、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースを選択して、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f7d-118">In the **Connect to database** box, browse the server, select the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database, and then click **Connect**.</span></span> <span data-ttu-id="50f7d-119">指定したデータベースを含む接続情報がプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-119">The connection information including the database is added to the project.</span></span>  
  
8.  <span data-ttu-id="50f7d-120">[プロパティ] ウィンドウが表示されない場合は、ソリューション エクスプローラーで新しい接続をクリックし、F4 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-120">If the Properties window is not displayed, click the new connection in Solution Explorer, and then press F4.</span></span> <span data-ttu-id="50f7d-121">接続のプロパティが表示され、 **初期データベース** が [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]であることなどの接続情報が示されます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-121">The properties for the connection appear, and show information about the connection including the **Initial Database** as [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
9. <span data-ttu-id="50f7d-122">ソリューション エクスプローラーで接続を右クリックし、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f7d-122">In Solution Explorer, right-click the connection, and then click **New Query**.</span></span> <span data-ttu-id="50f7d-123">**SQLQuery1.sql** という名前の新しいクエリが作成され、サーバー上の [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースに接続されます。さらに、スクリプト プロジェクトにこのクエリが追加されます。</span><span class="sxs-lookup"><span data-stu-id="50f7d-123">A new query called **SQLQuery1.sql** is created, connected to the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database on your server, and added to your script project.</span></span>  
  
10. <span data-ttu-id="50f7d-124">クエリ エディターに次のクエリを入力します。ここでは、期限が設けられており、まだ開始日に至っていない作業命令の数を調べます</span><span class="sxs-lookup"><span data-stu-id="50f7d-124">In Query Editor, type the following query to determine how many work orders have due dates, before the work order starting dates.</span></span> <span data-ttu-id="50f7d-125">(チュートリアル ウィンドウからコードをコピーして、貼り付けることができます)。</span><span class="sxs-lookup"><span data-stu-id="50f7d-125">(You can copy and paste the code from the Tutorial window.)</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT COUNT(WorkOrderID)  
    FROM Production.WorkOrder  
    WHERE DueDate < StartDate;  
  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="50f7d-126">クエリを入力するスペースが足りない場合は、Shift + Alt + Enter キーを押して全画面モードに切り替えてください。</span><span class="sxs-lookup"><span data-stu-id="50f7d-126">If you need more room to type your query, press SHIFT+ALT+ENTER, to switch to full-screen mode.</span></span>  
  
11. <span data-ttu-id="50f7d-127">ソリューション エクスプローラーで **SQLQuery1**を右クリックし、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f7d-127">In Solution Explorer, right-click **SQLQuery1**, and then click **Rename**.</span></span> <span data-ttu-id="50f7d-128">クエリの新しい名前として「 **Check workorders.sql」** 」と入力し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="50f7d-128">Type **Check Workorders.sql** as the new name for the query and press ENTER.</span></span>  
  
12. <span data-ttu-id="50f7d-129">ソリューションとスクリプト プロジェクトを保存するには、 **[ファイル]** メニューの **[すべてを保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50f7d-129">To save your solution and script project, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="50f7d-130">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="50f7d-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="50f7d-131">概要: ソリューションおよびスクリプト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="50f7d-131">Summary: Solutions and Script Projects</span></span>](lesson-3-4-summary-solutions-and-script-projects.md)  
  
  
