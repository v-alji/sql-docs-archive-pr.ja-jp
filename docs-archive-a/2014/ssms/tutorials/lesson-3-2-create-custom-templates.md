---
title: カスタム テンプレートの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 771547b9c47672d2c075b5e7215d78744fe5f18e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717139"
---
# <a name="create-custom-templates"></a><span data-ttu-id="a3e39-102">カスタム テンプレートの作成</span><span class="sxs-lookup"><span data-stu-id="a3e39-102">Create Custom Templates</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a3e39-103">一般的な作業のためのテンプレートが多数用意されていますが、テンプレートの真価は、頻繁に作成する複雑なスクリプトに適したカスタム テンプレートを作成できる点にあります。</span><span class="sxs-lookup"><span data-stu-id="a3e39-103">comes with templates for many common tasks, but the real power of templates lies in the ability to create a custom template for a complex script that you must create frequently.</span></span> <span data-ttu-id="a3e39-104">この演習では、2 ～ 3 のパラメーターを使用した簡単なスクリプトを作成しますが、規模が大きく、反復的なスクリプトを作成する場合にもテンプレートが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a3e39-104">In this practice you will create a simple script with few parameters, but templates are useful for long, repetitive scripts, too.</span></span>  
  
## <a name="using-custom-templates"></a><span data-ttu-id="a3e39-105">カスタム テンプレートの使用</span><span class="sxs-lookup"><span data-stu-id="a3e39-105">Using Custom Templates</span></span>  
  
#### <a name="to-create-a-custom-template"></a><span data-ttu-id="a3e39-106">カスタム テンプレートを作成するには</span><span class="sxs-lookup"><span data-stu-id="a3e39-106">To create a custom template</span></span>  
  
1.  <span data-ttu-id="a3e39-107">テンプレート エクスプローラーで **[SQL Server テンプレート]** を展開します。 **[Stored Procedure]** を右クリックし、 **[新規作成]** をポイントして **[フォルダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e39-107">In Template Explorer, expand **SQL Server Templates**, right-click **Stored Procedure**, point to **New**, and then click **Folder**.</span></span>  
  
2.  <span data-ttu-id="a3e39-108">新しいテンプレート フォルダーの名前として「 **Custom** 」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a3e39-108">Type **Custom** as the name of your new template folder, and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="a3e39-109">**[Custom]** を右クリックし、 **[新規作成]** をポイントして **[テンプレート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e39-109">Right-click **Custom**, point to **New**, and then click **Template**.</span></span>  
  
4.  <span data-ttu-id="a3e39-110">新しいテンプレートの名前として「 **WorkOrdersProc** 」と入力し、 **Enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a3e39-110">Type **WorkOrdersProc** as the name of your new template, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="a3e39-111">**[WorkOrdersProc]** を右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e39-111">Right-click **WorkOrdersProc**, and then click **Edit**.</span></span>  
  
6.  <span data-ttu-id="a3e39-112">**[データベース エンジンへの接続]** ダイアログ ボックスで接続情報を確認し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e39-112">In the **Connect to Database Engine** dialog box, verify the connection information and then click **Connect**.</span></span>  
  
7.  <span data-ttu-id="a3e39-113">クエリ エディターに次のスクリプトを入力し、特定の部分 (この例では Blade) の命令を検索するストアド プロシージャを作成します</span><span class="sxs-lookup"><span data-stu-id="a3e39-113">In Query Editor, type the following script to create a stored procedure that looks up orders for a particular part, in this case the Blade.</span></span> <span data-ttu-id="a3e39-114">(チュートリアル ウィンドウからコードをコピーして、貼り付けることができます)。</span><span class="sxs-lookup"><span data-stu-id="a3e39-114">(You can copy and paste the code from the Tutorial window.)</span></span>  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  <span data-ttu-id="a3e39-115">F5 キーを押してこのスクリプトを実行し、 **WorkOrdersForBlade** プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3e39-115">Press F5 to execute this script, creating the **WorkOrdersForBlade** procedure.</span></span>  
  
9. <span data-ttu-id="a3e39-116">オブジェクト エクスプローラーでサーバーを右クリックし、 **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e39-116">In Object Explorer, right-click your server, and then click **New Query**.</span></span> <span data-ttu-id="a3e39-117">新しいクエリ エディター ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="a3e39-117">A new Query Editor window opens.</span></span>  
  
10. <span data-ttu-id="a3e39-118">クエリ エディターに「 **EXECUTE dbo.WorkOrdersForBlade**」と入力し、F5 キーを押してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a3e39-118">In Query Editor, type **EXECUTE dbo.WorkOrdersForBlade**, and then press F5 to execute the query.</span></span> <span data-ttu-id="a3e39-119">**結果**ペインに、ブレードに対する作業命令の一覧が返されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a3e39-119">Confirm that the **Results** pane returns a list of work orders for blades.</span></span>  
  
11. <span data-ttu-id="a3e39-120">テンプレートスクリプト (手順7で作成したスクリプト) を編集し、product name ブレードを、 <strong> *<* </strong> `nvarchar(50)` 4 つの場所にあるパラメーター product_name、<strong>名前 *>* </strong>に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a3e39-120">Edit the template script (the script in step 7), replacing the product name Blade with the parameter <strong>*<* product_name</strong>, `nvarchar(50)`, <strong>name*>*</strong>, in four places.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a3e39-121">パラメーターには、置き換えるパラメーターの名前、パラメーターのデータ型、パラメーターの既定値の 3 つの要素が必要です。</span><span class="sxs-lookup"><span data-stu-id="a3e39-121">Parameters require three elements: the name of the parameter that you want to replace, the data type of the parameter, and a default value for the parameter.</span></span>  
  
12. <span data-ttu-id="a3e39-122">スクリプトは以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="a3e39-122">Now the script should look like:</span></span>  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. <span data-ttu-id="a3e39-123">**[ファイル]** メニューの **[WorkOrdersProc.sql の保存]** をクリックし、テンプレートを保存します。</span><span class="sxs-lookup"><span data-stu-id="a3e39-123">On the **File** menu, click **Save WorkOrdersProc.sql** to save your template.</span></span>  
  
#### <a name="to-test-the-custom-template"></a><span data-ttu-id="a3e39-124">カスタム テンプレートをテストするには</span><span class="sxs-lookup"><span data-stu-id="a3e39-124">To test the custom template</span></span>  
  
1.  <span data-ttu-id="a3e39-125">テンプレート エクスプローラーで **[Stored Procedure]**、 **[Custom]** の順に展開し、 **[WorkOrderProc]** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e39-125">In Template Explorer, expand **Stored Procedure**, expand **Custom**, and then double-click **WorkOrderProc**.</span></span>  
  
2.  <span data-ttu-id="a3e39-126">**[データベース エンジンへの接続]** ダイアログ ボックスで接続情報を指定し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e39-126">In the **Connect to Database Engine** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="a3e39-127">新しいクエリ エディター ウィンドウが開き、 **WorkOrderProc** テンプレートの内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e39-127">A new Query Editor window opens, containing the contents of the **WorkOrderProc** template.</span></span>  
  
3.  <span data-ttu-id="a3e39-128">**[クエリ]** メニューの **[テンプレート パラメーターの値の指定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e39-128">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
4.  <span data-ttu-id="a3e39-129">[**テンプレートパラメーターの置換**] ダイアログボックスで、値として `product_name` 「 **freewheel** 」と入力し (既定の内容を上書きします)、[ **OK** ] をクリックして [**テンプレートパラメーターの置換**] ダイアログボックスを閉じ、クエリエディターでスクリプトを変更します。</span><span class="sxs-lookup"><span data-stu-id="a3e39-129">In the **Replace Template Parameters** dialog box, for the `product_name` value, type **FreeWheel** (overwriting the default contents), and then click **OK** to close the **Replace Template Parameters** dialog box and modify the script in the Query Editor.</span></span>  
  
5.  <span data-ttu-id="a3e39-130">F5&lt;/localizedText&gt; キーを押してクエリを実行し、プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3e39-130">Press F5 to execute the query, creating the procedure.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a3e39-131">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="a3e39-131">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a3e39-132">プロジェクトまたはソリューションとしてスクリプトを保存する</span><span class="sxs-lookup"><span data-stu-id="a3e39-132">Save Scripts as Projects or Solutions</span></span>](lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
