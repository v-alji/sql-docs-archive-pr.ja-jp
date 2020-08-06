---
title: 'チュートリアル: OData ソースの使用 [SSIS] |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2c64cf8b-5edb-48df-8ffe-697096258f71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a13b04494ed00251774b490b1cc929769a869acb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644039"
---
# <a name="tutorial-using-the-odata-source-ssis"></a><span data-ttu-id="3a3b6-102">チュートリアル: OData ソースの使用 [SSIS]</span><span class="sxs-lookup"><span data-stu-id="3a3b6-102">Tutorial: Using the OData Source [SSIS]</span></span>
  <span data-ttu-id="3a3b6-103">このチュートリアルでは、サンプルの **Northwind** OData サービス (http://services.odata.org/V3/Northwind/Northwind.svc/) ) から **Employees** (従業員) コレクションを抽出し、フラット ファイルに読み込むプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-103">This tutorial walks you through the process to extract the **Employees** collection from the sample **Northwind** OData service (http://services.odata.org/V3/Northwind/Northwind.svc/), and then load it into a flat file.</span></span>  
  
## <a name="1-create-an-integration-services-project"></a><span data-ttu-id="3a3b6-104">1.Integration Services プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="3a3b6-104">1. Create an Integration Services Project</span></span>  
  
1.  <span data-ttu-id="3a3b6-105">**SQL Server Data Tools** または [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を起動します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-105">Launch **SQL Server Data Tools** or [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
2.  <span data-ttu-id="3a3b6-106">**[ファイル]** をクリックし、 **[新規作成]** をポイントして、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-106">Click **File**, point to **New**, and click **Project**.</span></span>  
  
3.  <span data-ttu-id="3a3b6-107">**[新しいプロジェクト]** ダイアログ ボックスで **[インストール済み]** 、 **[テンプレート]** 、 **[ビジネス インテリジェンス]** の順に展開し、 **[Integration Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-107">In the **New Project** dialog box, expand **Installed**, expand **Templates**, expand **Business Intelligence**, and click **Integration Services**.</span></span>  
  
4.  <span data-ttu-id="3a3b6-108">プロジェクトの種類として、 **[Integration Services プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-108">Select **Integration Services Project** for the type of project.</span></span>  
  
5.  <span data-ttu-id="3a3b6-109">プロジェクトの **[名前]** を入力し、 **[場所]** を選択して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-109">Enter a **name** and select a **location** for the project, and click **OK**.</span></span>  
  
## <a name="2-add-and-configure-odata-source-to-the-ssis-package"></a><span data-ttu-id="3a3b6-110">2.SSIS パッケージへの OData ソースの追加と構成</span><span class="sxs-lookup"><span data-stu-id="3a3b6-110">2. Add and Configure OData Source to the SSIS Package</span></span>  
  
1.  <span data-ttu-id="3a3b6-111">**[SSIS ツールボックス]** の **[データ フロー タスク]** を、SSIS パッケージの制御フロー デザイン画面にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-111">Drag-drop a **Data Flow Task** from the **SSIS Toolbox** on to the control flow design surface of your SSIS package.</span></span>  
  
2.  <span data-ttu-id="3a3b6-112">**[データ フロー]** タブをクリックするか、新しく追加した **[データ フロー タスク]** をダブルクリックして、 **[データ フロー]** デザイン画面を起動します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-112">Click the **Data Flow** tab, or double click on the newly added **Data Flow Task** to launch the **Data Flow design surface**.</span></span>  
  
3.  <span data-ttu-id="3a3b6-113">**[SSIS ツールボックス]** の **[共通]** から **[OData ソース]** をドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-113">Drag-drop **OData Source** from the **Common** group in the **SSIS Toolbox**.</span></span> <span data-ttu-id="3a3b6-114">**OData ソース** を最初にインストールするときに、OData ソースは **[SSIS ツールボックス]** の **[共通]** グループの下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-114">When the **OData Source** is first installed, it will appear under the **Common** group in the **SSIS Toolbox**.</span></span>  
  
4.  <span data-ttu-id="3a3b6-115">**OData ソース** コンポーネントをダブルクリックして、 **[OData ソース エディター]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-115">Double click the **OData Source** component to launch the **OData Source Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="3a3b6-116">**[新規]** をクリックし、新しい OData 接続マネージャーを追加します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-116">Click **New...** to add a new OData Connection Manager.</span></span>  
  
6.  <span data-ttu-id="3a3b6-117">**[サービス ドキュメントの場所]** に対応する OData サービスの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-117">Enter the OData service URL for **Service document location**.</span></span> <span data-ttu-id="3a3b6-118">サービス ドキュメントに対応する URL、または特定のフィードかエンティティに対応する URL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-118">This can be the URL to the service document, or to a specific feed or entity.</span></span> <span data-ttu-id="3a3b6-119">このチュートリアルでは、「」と入力 [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/) します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-119">For the purpose of this tutorial, type [http://services.odata.org/V3/Northwind/Northwind.svc/](http://services.odata.org/V3/Northwind/Northwind.svc/).</span></span>  
  
7.  <span data-ttu-id="3a3b6-120">OData サービスにアクセスするために、 **[認証]** で **[Windows 認証]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-120">Confirm that **Windows Authentication** is selected for the **authentication** to use to access the OData Service.</span></span> <span data-ttu-id="3a3b6-121">既定では、**[Windows 認証]** が選択されています。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-121">**Windows Authentication** is selected by default.</span></span> <span data-ttu-id="3a3b6-122">基本認証を使用するには、 **[次のユーザー名とパスワードを使用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-122">To use basic authentication, select **Use this user name and password**.</span></span>  
  
8.  <span data-ttu-id="3a3b6-123">接続に対応する **[接続テスト]** をクリックし、 **[OK]** をクリックして OData 接続マネージャーのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-123">Click **Test Connection** to the connection, and click **OK** to create an instance of OData Connection Manager.</span></span>  
  
9. <span data-ttu-id="3a3b6-124">**[OData ソース エディター]** ダイアログ ボックスの **[リソースのパスでコレクションを使用する]** オプションで **[コレクション]** が選択されていること確認します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-124">In the **OData Source Editor** Dialog Box, confirm that **Collection** is selected for **Use collection on resource path** option.</span></span>  
  
10. <span data-ttu-id="3a3b6-125">**[コレクション]** ドロップダウン リストで、 **[Employees]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-125">From the **Collection** drop down list, select **Employees**.</span></span>  
  
11. <span data-ttu-id="3a3b6-126">**[クエリ オプション]** で、追加の OData クエリ オプションまたはフィルターを入力します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-126">Enter any additional OData query options or filters for **Query Options**.</span></span> <span data-ttu-id="3a3b6-127">例:</span><span class="sxs-lookup"><span data-stu-id="3a3b6-127">Ex.</span></span> <span data-ttu-id="3a3b6-128">$orderby=CompanyName&$top=100.</span><span class="sxs-lookup"><span data-stu-id="3a3b6-128">$orderby=CompanyName&$top=100.</span></span> <span data-ttu-id="3a3b6-129">このチュートリアルでは、「 **$top=5**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-129">For the purpose of this tutorial, enter **$top=5**.</span></span>  
  
12. <span data-ttu-id="3a3b6-130">**[プレビュー]** をクリックして、データをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-130">Click **Preview** to preview the data.</span></span>  
  
13. <span data-ttu-id="3a3b6-131">左側のナビゲーション ウィンドウで **[列]** をクリックし、 **[列]** ページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-131">Click **Columns** in the left navigation pane to switch to the **Columns** page.</span></span>  
  
14. <span data-ttu-id="3a3b6-132">**[使用できる外部列]** で **[EmployeeID]**、 **[FirstName]** 、 **[LastName]** の各チェック ボックスをオンにし、これらを選択します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-132">Select **EmployeeID**, **FirstName**, and **LastName** from **Available External Columns** by checking the check boxes.</span></span>  
  
15. <span data-ttu-id="3a3b6-133">**[OK]** をクリックし、 **[OData ソース エディター]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-133">Click **OK** to close the **OData Source Editor** dialog box.</span></span>  
  
## <a name="3-add-flat-file-destination-and-test-the-solution"></a><span data-ttu-id="3a3b6-134">3.フラット ファイル変換先の追加とソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="3a3b6-134">3. Add Flat File Destination and Test the Solution</span></span>  
  
1.  <span data-ttu-id="3a3b6-135">今度は、 **[SSIS ツールボックス]** の **[フラット ファイル変換先]** を、 **[OData ソース]** コンポーネントの下にある [データ フロー] デザイン画面にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-135">Now, drag-drop a **Flat File Destination** from **SSIS Toolbox** to the Data Flow design surface below the **OData Source** component.</span></span>  
  
2.  <span data-ttu-id="3a3b6-136">青い矢印を使用して、 **[OData ソース]** コンポーネントを **[フラット ファイル変換先]** コンポーネントに接続します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-136">Connect **OData Source** component with the **Flat File Destination** component using blue arrow.</span></span>  
  
3.  <span data-ttu-id="3a3b6-137">**[フラット ファイル変換先]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-137">Double-click on **Flat File Destination**.</span></span> <span data-ttu-id="3a3b6-138">**[フラット ファイル変換先エディター]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-138">You should see the **Flat File Destination Editor** dialog box.</span></span>  
  
4.  <span data-ttu-id="3a3b6-139">**[フラット ファイル変換先エディター]** ダイアログ ボックスで **[新規]** をクリックし、新しいフラット ファイル接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-139">In the **Flat File Destination Editor** dialog box, click **New** to create a new flat file connection manager.</span></span>  
  
5.  <span data-ttu-id="3a3b6-140">**[フラット ファイル形式]** ダイアログ ボックスで、 **[区切り記号]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-140">In the **Flat File Format** dialog box, select **Delimited**.</span></span> <span data-ttu-id="3a3b6-141">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-141">You should see the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
6.  <span data-ttu-id="3a3b6-142">**[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスの **[ファイル名]** で、「 **c:\Employees.txt**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-142">In the **Flat File Connection Manager Editor** dialog box, for the **File name**, enter **c:\Employees.txt**.</span></span>  
  
7.  <span data-ttu-id="3a3b6-143">左側のナビゲーション ウィンドウで、 **[列]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-143">In the left navigation pane, click **Columns**.</span></span> <span data-ttu-id="3a3b6-144">このページで、データをプレビューできます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-144">You can preview the data on this page.</span></span>  
  
8.  <span data-ttu-id="3a3b6-145">**[OK]** をクリックして、[ファイル接続マネージャー エディター] ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-145">Click OK to close the **Flat File Connection Manager** Editor dialog box.</span></span>  
  
9. <span data-ttu-id="3a3b6-146">**[フラット ファイル変換先エディター]** ダイアログ ボックスにある左側のナビゲーション ウィンドウで **[マッピング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-146">In the **Flat File Destination Editor** dialog box, click **Mappings** in the left navigation pane.</span></span> <span data-ttu-id="3a3b6-147">マッピングを確認します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-147">Review the mappings.</span></span>  
  
10. <span data-ttu-id="3a3b6-148">[OK] をクリックして、 **[フラット ファイル変換先エディター]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-148">Click OK to close the **Flat File Destination Editor** dialog box.</span></span>  
  
11. <span data-ttu-id="3a3b6-149">SSIS パッケージをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-149">Compile and execute the SSIS package.</span></span> <span data-ttu-id="3a3b6-150">OData フィードから得られた 5 人の従業員の ID、名、姓を使用して出力ファイルが作成されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3a3b6-150">Verify that the output file is created with ID, First Name, and Last Name for 5 employees from the OData feed.</span></span>  
  
  
