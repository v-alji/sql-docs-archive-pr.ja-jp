---
title: '手順 4: レッスン 6 のパッケージの展開 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b613cef7-7993-4d89-a429-a8251d74d435
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c5109dc96af138bbd0c8c0087e8b73cf3bac435
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645747"
---
# <a name="step-4-deploying-the-lesson-6-package"></a><span data-ttu-id="772ef-102">手順 4:レッスン 6 のパッケージの展開</span><span class="sxs-lookup"><span data-stu-id="772ef-102">Step 4: Deploying the Lesson 6 Package</span></span>
  <span data-ttu-id="772ef-103">パッケージを配置するには、SQL Server インスタンスの Integration Services の SSISDB カタログにパッケージを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="772ef-103">Deploying the package involves adding the package to the SSISDB catalog in Integration Services on an instance of SQL Server.</span></span> <span data-ttu-id="772ef-104">このレッスンでは、SSISDB カタログへのレッスン 6 パッケージの追加、パラメーターの設定、パッケージの実行を行います。</span><span class="sxs-lookup"><span data-stu-id="772ef-104">In this lesson you will add the Lesson 6 package to the SSISDB catalog, set the parameter, and execute the package.</span></span> <span data-ttu-id="772ef-105">このレッスンでは、SQL Server Management Studio を使用して SSISDB カタログにレッスン 6 パッケージを追加し、パッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="772ef-105">For this lesson you will use SQL Server Management Studio to add the Lesson 6 package to the SSISDB catalog, and deploy the package.</span></span> <span data-ttu-id="772ef-106">パッケージを配置したら、新しい場所を指すようにパラメーターを変更し、パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="772ef-106">After deploying the package you will modify the parameter to point to a new location then execute the package.</span></span>  
  
 <span data-ttu-id="772ef-107">このレッスンの内容</span><span class="sxs-lookup"><span data-stu-id="772ef-107">In this lesson you will:</span></span>  
  
-   <span data-ttu-id="772ef-108">SQL Server の SSIS ノードの SSISDB カタログにパッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="772ef-108">Add the package to the SSISDB catalog in the SSIS node in SQL Server.</span></span>  
  
-   <span data-ttu-id="772ef-109">パッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="772ef-109">Deploy the package.</span></span>  
  
-   <span data-ttu-id="772ef-110">パッケージ パラメーターの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="772ef-110">Set the package parameter value.</span></span>  
  
-   <span data-ttu-id="772ef-111">SSMS でパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="772ef-111">Execute the package in SSMS.</span></span>  
  
### <a name="to-locate-or-add-the-ssisdb-catalog"></a><span data-ttu-id="772ef-112">SSISDB カタログを検索または追加するには</span><span class="sxs-lookup"><span data-stu-id="772ef-112">To Locate or add the SSISDB catalog</span></span>  
  
1.  <span data-ttu-id="772ef-113">[スタート] ボタンをクリックし、[すべてのプログラム]、[Microsoft SQL Server] の順にポイントし、[SQL Server Management Studio] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-113">Click Start, point to All Programs, point to Microsoft SQL Server 2012, and then click SQL Management Studio.</span></span>  
  
2.  <span data-ttu-id="772ef-114">[サーバーへの接続] ダイアログ ボックスで既定の設定を確認し、[接続] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-114">On the Connect to Server dialog box, verify the default settings, and then click Connect.</span></span> <span data-ttu-id="772ef-115">接続を確立するには、[サーバー名] ボックスに、SQL Server がインストールされているコンピューターの名前が入力されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="772ef-115">To connect, the Server name box must contain the name of the computer where SQL Server is installed.</span></span> <span data-ttu-id="772ef-116">データベース エンジンが名前付きインスタンスの場合は、[サーバー名] ボックスに、<computer_name>\\<instance_name> 形式でインスタンス名も指定します。</span><span class="sxs-lookup"><span data-stu-id="772ef-116">If the Database Engine is a named instance, the Server name box should also contain the instance name in the format <computer_name>\\<instance_name>.</span></span>  
  
3.  <span data-ttu-id="772ef-117">オブジェクト エクスプ ローラーで、[Integration Services カタログ] を展開します。</span><span class="sxs-lookup"><span data-stu-id="772ef-117">In Object Explorer expand Integration Services Catalogs.</span></span>  
  
4.  <span data-ttu-id="772ef-118">[Integration Services カタログ] の下にカタログが表示されない場合は、SSISDB カタログを追加します。</span><span class="sxs-lookup"><span data-stu-id="772ef-118">If there are no catalogs listed under Integration Services Catalogs then add the SSISDB catalog.</span></span>  
  
5.  <span data-ttu-id="772ef-119">SSISDB カタログを追加するには、[Integration Services カタログ] を右クリックし、[カタログの作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-119">To Add the SSISDB catalog, right-click Integration Services Catalogs and click Create Catalog.</span></span>  
  
6.  <span data-ttu-id="772ef-120">[カタログの作成] ダイアログ ボックスで、[CLR 統合を有効にする] を選択します。</span><span class="sxs-lookup"><span data-stu-id="772ef-120">On the Create Catalog dialog box select Enable CLR Integration.</span></span>  
  
7.  <span data-ttu-id="772ef-121">[パスワード] ボックスに新しいパスワードを入力し、[パスワードの再入力] ボックスにもう一度入力します。</span><span class="sxs-lookup"><span data-stu-id="772ef-121">In the Password box, type a new password then type it again in the Retype Password box.</span></span> <span data-ttu-id="772ef-122">入力したパスワードを忘れないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="772ef-122">Be sure to remember the password you type.</span></span>  
  
8.  <span data-ttu-id="772ef-123">[OK] をクリックして SSISDB カタログを追加します。</span><span class="sxs-lookup"><span data-stu-id="772ef-123">Click OK to add the SSISDB catalog.</span></span>  
  
### <a name="to-add-the-package-to-the-ssisdb-catalog"></a><span data-ttu-id="772ef-124">SSISDB カタログにパッケージを追加するには</span><span class="sxs-lookup"><span data-stu-id="772ef-124">To add the package to the SSISDB catalog</span></span>  
  
1.  <span data-ttu-id="772ef-125">オブジェクト エクスプ ローラーで、[SSISDB] を右クリックし、[フォルダーの作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-125">In Object Explorer, right-click SSISDB and click Create Folder.</span></span>  
  
2.  <span data-ttu-id="772ef-126">[フォルダーの作成] ダイアログ ボックスで、[フォルダー名] ボックスに「SSIS Tutorial」と入力し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-126">In the Create Folder dialog box type SSIS Tutorial in the Folder name box and click OK.</span></span>  
  
3.  <span data-ttu-id="772ef-127">SSIS Tutorial フォルダーを展開し、[プロジェクト] を右クリックし、[パッケージのインポート] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-127">Expand the SSIS Tutorial folder, right-click Projects, and click Import Packages.</span></span>  
  
4.  <span data-ttu-id="772ef-128">[Integration Services プロジェクトの変換ウィザードの概要] ページで、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-128">On the Integration Services Project Conversion Wizard Introduction page click Next.</span></span>  
  
5.  <span data-ttu-id="772ef-129">[パッケージの検索] ページの [ソース] の一覧で、ファイル システムが選択されていることを確認し、[参照] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-129">On the Locate Packages page, ensure that File system is selected in the Source list, then click Browse.</span></span>  
  
6.  <span data-ttu-id="772ef-130">[フォルダーの参照] ダイアログ ボックスで、SSIS Tutorial プロジェクトを含むフォルダーに移動し、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-130">On the Browse For Folder dialog box, browse to the folder containing the SSIS Tutorial project, then click OK.</span></span>  
  
7.  <span data-ttu-id="772ef-131">[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-131">Click Next.</span></span>  
  
8.  <span data-ttu-id="772ef-132">[パッケージの選択] ページに SSIS Tutorial の 6 つパッケージがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="772ef-132">On the Select Packages page you should see all six packages from the SSIS Tutorial.</span></span> <span data-ttu-id="772ef-133">[パッケージ] の一覧で、[Lesson 6.dtsx] を選択し、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-133">In the Packages list, select Lesson 6.dtsx, then click Next.</span></span>  
  
9. <span data-ttu-id="772ef-134">[Select Destination (出力先の選択)] ページで、[プロジェクト名] ボックスに「SSIS Tutorial Deployment」と入力し、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-134">On the Select Destination page, type SSIS Tutorial Deployment in the Project Name box then click Next.</span></span>  
  
10. <span data-ttu-id="772ef-135">残りのウィザードの各ページで [次へ] をクリックし、[確認] ページまで進みます。</span><span class="sxs-lookup"><span data-stu-id="772ef-135">Click Next on each of the remaining wizard pages until you get to the Review page.</span></span>  
  
11. <span data-ttu-id="772ef-136">[確認] ページで [変換] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-136">On the Review page, click Convert.</span></span>  
  
12. <span data-ttu-id="772ef-137">変換が完了したら、[閉じる] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-137">When the conversion completes, click Close.</span></span>  
  
 <span data-ttu-id="772ef-138">Integration Services プロジェクトの変換ウィザードを閉じると、Integration Services 配置ウィザードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="772ef-138">When you close the Integration Services Project Conversion Wizard, SSIS displays the Integration Services Deployment Wizard.</span></span> <span data-ttu-id="772ef-139">次に、このウィザードを使用してレッスン 6 パッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="772ef-139">You will use this wizard now to deploy the Lesson 6 package.</span></span>  
  
1.  <span data-ttu-id="772ef-140">[Integration Services 配置ウィザードの概要] ページで、プロジェクトを配置する手順を確認し、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-140">On the Integration Services Deployment Wizard Introduction page, review the steps for deploying the project, then click Next.</span></span>  
  
2.  <span data-ttu-id="772ef-141">[Select Destination (出力先の選択)] ページで、サーバー名が SSISDB カタログを含む SQL Server のインスタンスであることと、パスが SSIS Tutorial Deployment を示していることを確認し、[次へ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-141">On the Select Destination page verify that the server name is the instance of SQL Server containing the SSISDB catalog and that the path shows SSIS Tutorial Deployment, then click Next.</span></span>  
  
3.  <span data-ttu-id="772ef-142">[確認] ページで概要を確認し、[配置] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-142">On the Review page, review the Summary then click Deploy.</span></span>  
  
4.  <span data-ttu-id="772ef-143">配置が完了したら、[閉じる] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-143">When the deployment completes, click Close.</span></span>  
  
5.  <span data-ttu-id="772ef-144">オブジェクト エクスプ ローラーで、[Integration Services カタログ] を右クリックし、[更新] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-144">In Object Explorer, right-click Integration Services Catalogs and click Refresh.</span></span>  
  
6.  <span data-ttu-id="772ef-145">[Integration Services カタログ] を展開し、[SSISDB] を展開します。</span><span class="sxs-lookup"><span data-stu-id="772ef-145">Expand Integration Services Catalogs then expand SSISDB.</span></span> <span data-ttu-id="772ef-146">プロジェクトが完全に展開されるまで、SSIS Tutorial の下のツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="772ef-146">Continue to Expand the tree under SSIS Tutorial until you have completely expanded the project.</span></span> <span data-ttu-id="772ef-147">SSIS Tutorial Deployment ノードのパッケージ ノードの下に Lesson 6.dtsx が表示されます。</span><span class="sxs-lookup"><span data-stu-id="772ef-147">You should see Lesson 6.dtsx under the Packages node of the SSIS Tutorial Deployment node.</span></span>  
  
 <span data-ttu-id="772ef-148">パッケージが完了したことを確認するには、[Lesson 6.dtsx] を右クリックし、[構成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-148">To verify that the package is complete, right-click Lesson 6.dtsx and click Configure.</span></span> <span data-ttu-id="772ef-149">[構成] ダイアログ ボックスで [パラメーター] を選択し、[コンテナー] に Lesson 6.dtsx のエントリ、[名前] に VarFolderName、[値] に新しいサンプル データへのパスがあることを確認し、[閉じる] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-149">On the Configure dialog box, select Parameters and verify that there is an entry with Lesson 6.dtsx as the Container, VarFolderName as the Name and the path to New Sample Data as the value, then click Close.</span></span>  
  
 <span data-ttu-id="772ef-150">新しいサンプル データ フォルダーを作成する前に、「Sample Data Two」という名前のフォルダーを作成し、元のサンプル ファイルのうち 3 つをここにコピーします。</span><span class="sxs-lookup"><span data-stu-id="772ef-150">Before continuing create a new sample data folder, name it Sample Data Two, and copy any three of the original sample files into it.</span></span>  
  
### <a name="to-create-and-populate-a-new-sample-data-folder"></a><span data-ttu-id="772ef-151">新しいサンプル データ フォルダーを作成して、データを取り込むには</span><span class="sxs-lookup"><span data-stu-id="772ef-151">To create and populate a new sample data folder</span></span>  
  
1.  <span data-ttu-id="772ef-152">Windows エクスプローラーで、ドライブのルート レベル (C:\\など) に新しいフォルダーを作成します。このフォルダーには "Sample Data Two" という名前を付けてください。</span><span class="sxs-lookup"><span data-stu-id="772ef-152">In Windows Explorer, at the root level of your drive (for example, C:\\), create a new folder named Sample Data Two.</span></span>  
  
2.  <span data-ttu-id="772ef-153">C:\Program Files\Microsoft SQL Server\110\Samples\Integration Services\Tutorial\Creating a Simple ETL Package\Sample Data フォルダーを開き、このフォルダーから任意の 3 つのサンプル ファイルをコピーします。</span><span class="sxs-lookup"><span data-stu-id="772ef-153">Open the c:\Program Files\Microsoft SQL Server\110\Samples\Integration Services\Tutorial\Creating a Simple ETL Package\Sample Data folder and then copy any three of the sample files from the folder.</span></span>  
  
3.  <span data-ttu-id="772ef-154">コピーしたファイルを New Sample Data フォルダーに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="772ef-154">In the New Sample Data folder, paste the copied files.</span></span>  
  
### <a name="to-change-the-package-parameter-to-point-to-the-new-sample-data"></a><span data-ttu-id="772ef-155">新しいサンプル データを指すようにパッケージ パラメーターを変更するには</span><span class="sxs-lookup"><span data-stu-id="772ef-155">To change the package parameter to point to the new sample data</span></span>  
  
1.  <span data-ttu-id="772ef-156">オブジェクト エクスプ ローラーで、[Lesson 6.dtsx] を右クリックし、[構成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-156">In Object Explorer, right click Lesson 6.dtsx and click Configure.</span></span>  
  
2.  <span data-ttu-id="772ef-157">[構成] ダイアログ ボックスで、パラメーター値を Sample Data Two へのパスに変更します。</span><span class="sxs-lookup"><span data-stu-id="772ef-157">On the Configure dialog box, change the parameter value to the path to Sample Data Two.</span></span> <span data-ttu-id="772ef-158">たとえば、C ドライブのルート フォルダーに新しいフォルダーを配置した場合は、C:\Sample Data Two となります。</span><span class="sxs-lookup"><span data-stu-id="772ef-158">For example C:\Sample Data Two if you placed the new folder in the root folder on the C drive.</span></span>  
  
3.  <span data-ttu-id="772ef-159">[OK] をクリックして [構成] ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="772ef-159">Click OK to close the Configure dialog box.</span></span>  
  
### <a name="to-test-the-lesson-6-package-deployment"></a><span data-ttu-id="772ef-160">レッスン 6 パッケージの配置をテストするには</span><span class="sxs-lookup"><span data-stu-id="772ef-160">To test the Lesson 6 package deployment</span></span>  
  
1.  <span data-ttu-id="772ef-161">オブジェクト エクスプ ローラーで、[Lesson 6.dtsx] を右クリックし、[実行] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-161">In Object Explorer, right click Lesson 6.dtsx and click Execute.</span></span>  
  
2.  <span data-ttu-id="772ef-162">[パッケージの実行] ダイアログ ボックスで、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="772ef-162">On the Execute Package dialog box, click OK.</span></span>  
  
3.  <span data-ttu-id="772ef-163">[メッセージ] ダイアログ ボックスで [はい] をクリックし、[概要レポート] を開きます。</span><span class="sxs-lookup"><span data-stu-id="772ef-163">On the message dialog box click Yes to open Overview Report.</span></span>  
  
 <span data-ttu-id="772ef-164">パッケージの概要レポートには、パッケージの名前と状態の概要が表示されています。</span><span class="sxs-lookup"><span data-stu-id="772ef-164">The Overview report for the package is displayed showing the name of the package and a status summary.</span></span> <span data-ttu-id="772ef-165">[実行の概要] セクションはパッケージの各タスクの結果を示し、[使用されたパラメーター] セクションはパッケージの実行で使用されたすべてのパラメーターの名前と値を示します (VarFolderName など)。</span><span class="sxs-lookup"><span data-stu-id="772ef-165">The Execution Overview section shows the result from each task in the package and the Parameters Used section shows the names and values of all parameters used in the package execution, including VarFolderName.</span></span>  
  
  
