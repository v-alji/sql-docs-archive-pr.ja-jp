---
title: スクリプトの生成
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9711c617-3c68-4e5a-aea3-befc64d51524
author: rothja
ms.author: jroth
ms.openlocfilehash: 199d5e0c98d220861ee0dfb48a44a71675d8ba87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644981"
---
# <a name="generate-scripts-sql-server-management-studio"></a><span data-ttu-id="9d53c-102">スクリプトの生成 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9d53c-102">Generate Scripts (SQL Server Management Studio)</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="9d53c-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを生成するための 2 つのメカニズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9d53c-103">provides two mechanisms for generating [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts.</span></span> <span data-ttu-id="9d53c-104">**スクリプトの生成とパブリッシュウィザード**を使用して、複数のオブジェクトのスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-104">You can create scripts for multiple objects by using the **Generate and Publish Scripts Wizard.**.</span></span> <span data-ttu-id="9d53c-105">また、個々のオブジェクトまたは複数のオブジェクト用のスクリプトを、 **オブジェクト エクスプローラー** の **[スクリプト化]** メニューを使用して生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-105">You can also generate a script for individual objects or multiple objects by using the **Script as** menu in **Object Explorer**.</span></span>  
  
1.  <span data-ttu-id="9d53c-106">**方法の選択:**  [スクリプトの生成とパブリッシュ ウィザード](#GenPubScriptWiz)、 [オブジェクト エクスプローラーの [スクリプト化] メニュー](#OEScriptAsMenu)</span><span class="sxs-lookup"><span data-stu-id="9d53c-106">**Choose a method:**  [Generate and Publish Scripts Wizard](#GenPubScriptWiz), [Object Explorer Script As Menu](#OEScriptAsMenu)</span></span>  
  
2.  <span data-ttu-id="9d53c-107">**[スクリプト化] メニューの使用方法:**  [単一オブジェクトのスクリプトの生成](#ScriptSingleObject)、 [オブジェクト エクスプローラーによる 2 つのオブジェクトのスクリプトの生成](#ScriptTwoObjectsOE)、 [[オブジェクト エクスプローラーの詳細] による 2 つのオブジェクトのスクリプトの生成](#ScriptTwoObjectsOED)</span><span class="sxs-lookup"><span data-stu-id="9d53c-107">**To use the Script As menu:**  [Script a Single Object](#ScriptSingleObject), [Script Two Objects Using Object Explorer](#ScriptTwoObjectsOE), [Script Two Objects Using Object Explorer Details](#ScriptTwoObjectsOED)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="9d53c-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="9d53c-108">Before You Begin</span></span>  
 <span data-ttu-id="9d53c-109">要件に最も適したメカニズムを選択します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-109">Choose the mechanism that best meets your requirements.</span></span>  
  
###  <a name="generate-and-publish-scripts-wizard"></a><a name="GenPubScriptWiz"></a> <span data-ttu-id="9d53c-110">スクリプトの生成とパブリッシュ ウィザード</span><span class="sxs-lookup"><span data-stu-id="9d53c-110">Generate and Publish Scripts Wizard</span></span>  
 <span data-ttu-id="9d53c-111">**スクリプトの生成とパブリッシュ ウィザード** を使用し、多数のオブジェクトの [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-111">Use the **Generate and Publish Scripts Wizard** to create a [!INCLUDE[tsql](../../includes/tsql-md.md)] script for many objects.</span></span> <span data-ttu-id="9d53c-112">このウィザードでは、データベース内の全オブジェクトのスクリプトを生成することも、選択したオブジェクトのサブセットのスクリプトを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-112">The wizard generates a script of all the objects in a database, or a subset of the objects that you select.</span></span> <span data-ttu-id="9d53c-113">ウィザードには、権限、照合順序、制約、その他を含めるかどうかなど、スクリプトのさまざまなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="9d53c-113">The wizard has many options for your scripts, such as whether to include permissions, collation, constraints, and so on.</span></span> <span data-ttu-id="9d53c-114">ウィザードの使用方法の詳細については、「 [スクリプトの生成とパブリッシュ ウィザード](generate-and-publish-scripts-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d53c-114">For instructions on using the wizard, see [Generate and Publish Scripts Wizard](generate-and-publish-scripts-wizard.md).</span></span>  
  
###  <a name="object-explorer-script-as-menu"></a><a name="OEScriptAsMenu"></a> <span data-ttu-id="9d53c-115">オブジェクト エクスプローラーの [スクリプト化] メニュー</span><span class="sxs-lookup"><span data-stu-id="9d53c-115">Object Explorer Script As Menu</span></span>  
 <span data-ttu-id="9d53c-116">オブジェクト エクスプローラーの **[スクリプト化]** メニューを使用し、単一オブジェクト、複数オブジェクト、または単一オブジェクトの複数のステートメントのスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-116">You can use the **Object Explorer Script as** menu to script a single object, script multiple objects, or script multible statements for a single objects.</span></span> <span data-ttu-id="9d53c-117">いずれか 1 つのスクリプト タイプを選択できます。たとえば、オブジェクトの作成、変更、削除を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-117">You can choose one of several types of scripts; for example to create, alter, or drop the object.</span></span> <span data-ttu-id="9d53c-118">スクリプトは、クエリ エディター ウィンドウ、ファイル、またはクリップボードに保存できます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-118">You can save the script in a Query Editor window, to a file, or to the Clipboard.</span></span> <span data-ttu-id="9d53c-119">スクリプトは Unicode 形式で作成されます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-119">The script is created in Unicode format.</span></span>  
  
##  <a name="to-generate-a-script-of-a-single-object"></a><a name="ScriptSingleObject"></a> <span data-ttu-id="9d53c-120">単一のオブジェクトのスクリプトを生成するには</span><span class="sxs-lookup"><span data-stu-id="9d53c-120">To generate a script of a single object</span></span>  
 <span data-ttu-id="9d53c-121">**単一のオブジェクトのスクリプトを生成するには**</span><span class="sxs-lookup"><span data-stu-id="9d53c-121">**To script a single object**</span></span>  
  
1.  <span data-ttu-id="9d53c-122">オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-122">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9d53c-123">**[データベース]** を展開し、スクリプト化するオブジェクトを含むデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-123">Expand **Databases**, and then expand the database containing the object to be scripted.</span></span>  
  
3.  <span data-ttu-id="9d53c-124">オブジェクトのカテゴリを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-124">Expand the category of the object.</span></span> <span data-ttu-id="9d53c-125">たとえば、 **[テーブル]** または **[ビュー]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-125">For example, expand the **Tables** or **Views** node.</span></span>  
  
4.  <span data-ttu-id="9d53c-126">オブジェクトを右クリックし、[スクリプト化] をポイントします。たとえば、[**テーブルをスクリプト**化] をポイントします。 \*\* \<object type> \*\*</span><span class="sxs-lookup"><span data-stu-id="9d53c-126">Right-click the object, point to **Script \<object type> as**, For example, point to **Script Table as**.</span></span>  
  
5.  <span data-ttu-id="9d53c-127">**[CREATE]** または **[ALTER]** などのスクリプト タイプをポイントします。</span><span class="sxs-lookup"><span data-stu-id="9d53c-127">Point to the script type, such as **Create to** or **Alter to**.</span></span>  
  
6.  <span data-ttu-id="9d53c-128">スクリプトを保存する場所を選択します。 **[新しいクエリ エディター ウィンドウ]** や **[クリップボード]** などを選択します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-128">Select the location to save the script, such as **New Query Editor Window** or **Clipboard**.</span></span>  
  
##  <a name="to-generate-a-script-of-two-objects-using-object-explorer"></a><a name="ScriptTwoObjectsOE"></a><span data-ttu-id="9d53c-129">オブジェクトエクスプローラーを使用して2つのオブジェクトのスクリプトを生成するには</span><span class="sxs-lookup"><span data-stu-id="9d53c-129">To generate a script of two objects using Object Explorer</span></span>  
 <span data-ttu-id="9d53c-130">**オブジェクト エクスプローラーで 2 つのオブジェクトのスクリプトを生成するには**</span><span class="sxs-lookup"><span data-stu-id="9d53c-130">**To script two objects using Object Explorer**</span></span>  
  
 <span data-ttu-id="9d53c-131">プロシージャを削除した後でプロシージャを作成したり、テーブルを作成した後でテーブルを変更するなど、1 つのスクリプトで複数のオプションを実行させたい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="9d53c-131">Sometimes you may want a script with multiple options, such as drop a procedure and then create a procedure, or create a table and then alter a table.</span></span> <span data-ttu-id="9d53c-132">テーブル、ビュー、ストアド プロシージャなど、異なる種類のオブジェクトを参照するスクリプトを作成する必要がある場合は、複数のオブジェクトのスクリプトを生成する次の手順を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-132">The processes below for generating scripts of multiple objects also work if you need to create a script that references different types of objects, such as tables, views, and stored procedures.</span></span>  
  
1.  <span data-ttu-id="9d53c-133">オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-133">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9d53c-134">**[データベース]** を展開し、スクリプト化するオブジェクトを含むデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-134">Expand **Databases**, and then expand the database containing the objects to be scripted.</span></span>  
  
3.  <span data-ttu-id="9d53c-135">スクリプト化する最初のオブジェクトを右クリックし、[**スクリプト \<object type> **] をポイントし、[**名前を付けて保存**] の選択項目で出力先として [**新しいクエリエディターウィンドウ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-135">Right-click the first object to be scripted, point to **Script \<object type> as**, and in the **Save as** selections chooses **New Query Editor Window** as the output destination.</span></span>  
  
4.  <span data-ttu-id="9d53c-136">スクリプトを作成する 2 番目のオブジェクトに移動します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-136">Navigate to the second object you want to script.</span></span>  
  
5.  <span data-ttu-id="9d53c-137">オブジェクトを右クリックし\*\* \<object type> て [スクリプト**化] をポイントし、[**名前を付けて保存**] の選択項目で出力先として [**クリップボード\*\*] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-137">Right-click the object, point to **Script \<object type> as**, and in the **Save as** selections chooses **Clipboard** as the output destination.</span></span>  
  
6.  <span data-ttu-id="9d53c-138">最初のオブジェクトで開いたクエリ エディター ウィンドウに、2 番目のオブジェクトのスクリプトをクリップボードから貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-138">In the Query Editor window opened for the first object, paste the script for the second object from the clipboard.</span></span>  
  
##  <a name="to-generate-a-script-of-two-objects-using-object-explorer-details"></a><a name="ScriptTwoObjectsOED"></a><span data-ttu-id="9d53c-139">オブジェクトエクスプローラーの詳細を使用して2つのオブジェクトのスクリプトを生成するには</span><span class="sxs-lookup"><span data-stu-id="9d53c-139">To generate a script of two objects using Object Explorer Details</span></span>  
 <span data-ttu-id="9d53c-140">**[オブジェクト エクスプローラーの詳細] で 2 つのオブジェクトのスクリプトを生成するには**</span><span class="sxs-lookup"><span data-stu-id="9d53c-140">**To script two objects using Object Explorer Details**</span></span>  
  
 <span data-ttu-id="9d53c-141">**[オブジェクト エクスプローラーの詳細]** ペインを使用し、同じカテゴリに含まれる複数のオブジェクトのスクリプトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-141">You can use the **Object Explorer Details** pane to generate a script for mutliple objects of the same category.</span></span>  
  
1.  <span data-ttu-id="9d53c-142">オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-142">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9d53c-143">**[データベース]** を展開し、スクリプト化するオブジェクトを含むデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-143">Expand **Databases**, and then expand the database containing the objects to be scripted.</span></span>  
  
3.  <span data-ttu-id="9d53c-144">スクリプトを作成するオブジェクトの種類のカテゴリ ノード ( **[テーブル]** ノードなど) を展開します。</span><span class="sxs-lookup"><span data-stu-id="9d53c-144">Expand the category node of the types of object you want to script, such as the **Tables** node.</span></span>  
  
4.  <span data-ttu-id="9d53c-145">**F7** キーを押すか、 **[表示]** メニューの **[オブジェクト エクスプローラーの詳細]** をクリックして、 **[オブジェクト エクスプローラーの詳細]** ペインを開きます。</span><span class="sxs-lookup"><span data-stu-id="9d53c-145">Open the **Object Explorer Details** pane by either selecting **F7**, or opening the **View** menu and selecting **Object Explorer Details**.</span></span>  
  
5.  <span data-ttu-id="9d53c-146">スクリプトを作成するオブジェクトのいずれかを左クリックします。</span><span class="sxs-lookup"><span data-stu-id="9d53c-146">Left-click one of the objects you want to script.</span></span>  
  
6.  <span data-ttu-id="9d53c-147">Ctrl</localizedText> キーを押しながら、スクリプトを作成する 2 番目のオブジェクトを左クリックします。</span><span class="sxs-lookup"><span data-stu-id="9d53c-147">Crtl + left-click the second object you want to script.</span></span>  
  
7.  <span data-ttu-id="9d53c-148">選択したオブジェクトの1つを右クリックし、[スクリプト化] を選択します。 \*\* \<object type> \*\*</span><span class="sxs-lookup"><span data-stu-id="9d53c-148">Right-click one of the selected objects, and select **Script \<object type> as**.</span></span>  
  
  
