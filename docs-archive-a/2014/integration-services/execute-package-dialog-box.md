---
title: '[パッケージの実行] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.ispackageexecute.f1
- sql12.ssis.ssms.executepackage.f1
ms.assetid: 4f7a806d-4867-4d1f-bc65-b00c1caee7b6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b60381054c781cd59f0a9d434710663b72d616c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641761"
---
# <a name="execute-package-dialog-box"></a><span data-ttu-id="83f86-102">Execute Package Dialog Box</span><span class="sxs-lookup"><span data-stu-id="83f86-102">Execute Package Dialog Box</span></span>
  <span data-ttu-id="83f86-103">**[パッケージの実行]** ダイアログ ボックスでは、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに格納されているパッケージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="83f86-103">Use the **Execute Package** dialog box to run a package that is stored on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
 <span data-ttu-id="83f86-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージには、値が環境変数に格納されているパラメーターが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="83f86-104">An [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package may contain parameters that values stored in environment variables.</span></span> <span data-ttu-id="83f86-105">こうしたパッケージを実行するには、環境変数の値の提供に使用する環境を事前に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83f86-105">Before executing such a package, you must specify which environment will be used to provide the environment variable values.</span></span> <span data-ttu-id="83f86-106">プロジェクトには複数の環境を含めることができますが、実行時に環境変数の値をバインドするのに使用できる環境は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="83f86-106">A project may contain multiple environments, but only one environment can be used for binding environment variable values at the time of execution.</span></span> <span data-ttu-id="83f86-107">パッケージで環境変数が使用されない場合、環境は不要です。</span><span class="sxs-lookup"><span data-stu-id="83f86-107">If no environment variables are used in the package, an environment is not required.</span></span>  
  
 <span data-ttu-id="83f86-108">目的に合ったトピックをクリックしてください</span><span class="sxs-lookup"><span data-stu-id="83f86-108">What do you want to do?</span></span>  
  
-   <span data-ttu-id="83f86-109">[[パッケージの実行] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="83f86-109">[Open the Execute Package dialog box](#open_dialog)</span></span>  
  
-   <span data-ttu-id="83f86-110">[[全般] ページのオプションの設定](#general)</span><span class="sxs-lookup"><span data-stu-id="83f86-110">[Set the Options on the General page](#general)</span></span>  
  
-   <span data-ttu-id="83f86-111">[[パラメーター] タブのオプションの設定](#parameters)</span><span class="sxs-lookup"><span data-stu-id="83f86-111">[Set the Options on the Parameters tab](#parameters)</span></span>  
  
-   <span data-ttu-id="83f86-112">[[接続マネージャー] タブのオプションの設定](#connection)</span><span class="sxs-lookup"><span data-stu-id="83f86-112">[Set the Options on the Connection Managers tab](#connection)</span></span>  
  
-   <span data-ttu-id="83f86-113">[[詳細設定] タブのオプションの設定](#advanced)</span><span class="sxs-lookup"><span data-stu-id="83f86-113">[Set the Options on the Advanced tab](#advanced)</span></span>  
  
-   <span data-ttu-id="83f86-114">[[パッケージの実行] ダイアログ ボックスのオプションのスクリプト作成](#script)</span><span class="sxs-lookup"><span data-stu-id="83f86-114">[Scripting the Options in the Execute Package Dialog Box](#script)</span></span>  
  
##  <a name="open-the-execute-package-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="83f86-115">[パッケージの実行] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="83f86-115">Open the Execute Package dialog box</span></span>  
  
1.  <span data-ttu-id="83f86-116">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]から [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="83f86-116">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span>  
  
     <span data-ttu-id="83f86-117">SSISDB データベースをホストする [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="83f86-117">You're connecting to the instance of the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] that hosts the SSISDB database.</span></span>  
  
2.  <span data-ttu-id="83f86-118">オブジェクト エクスプローラーで、ツリーを展開して、 **[Integration Services カタログ]** ノードを表示します。</span><span class="sxs-lookup"><span data-stu-id="83f86-118">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="83f86-119">**[SSISDB]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="83f86-119">Expand the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="83f86-120">実行するパッケージを含むフォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="83f86-120">Expand the folder that contains the package you want to run.</span></span>  
  
5.  <span data-ttu-id="83f86-121">パッケージを右クリックし、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83f86-121">Right-click the package, and then click **Execute**.</span></span>  
  
##  <a name="set-the-options-on-the-general-page"></a><a name="general"></a> <span data-ttu-id="83f86-122">[全般] ページのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="83f86-122">Set the Options on the General page</span></span>  
 <span data-ttu-id="83f86-123">**[環境]** を選択して、実行するパッケージに適用される環境を指定します。</span><span class="sxs-lookup"><span data-stu-id="83f86-123">Select **Environment** to specify the environment that is applied with the package is run.</span></span>  
  
##  <a name="set-the-options-on-the-parameters-tab"></a><a name="parameters"></a> <span data-ttu-id="83f86-124">[パラメーター] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="83f86-124">Set the Options on the Parameters tab</span></span>  
 <span data-ttu-id="83f86-125">**[パラメーター]** タブを使用して、パッケージの実行時に使用するパラメーターの値を変更します。</span><span class="sxs-lookup"><span data-stu-id="83f86-125">Use the **Parameters** tab to modify the parameter values that are used when the package runs.</span></span>  
  
##  <a name="set-the-options-on-the-connection-managers-tab"></a><a name="connection"></a> <span data-ttu-id="83f86-126">[接続マネージャー] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="83f86-126">Set the Options on the Connection Managers tab</span></span>  
 <span data-ttu-id="83f86-127">[接続マネージャー] タブを使用して、パッケージの接続マネージャーのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="83f86-127">Use the Connection Managers tab to set the properties of the package connection manager(s).</span></span>  
  
##  <a name="set-the-options-on-the-advanced-tab"></a><a name="advanced"></a> <span data-ttu-id="83f86-128">[詳細設定] タブのオプションの設定</span><span class="sxs-lookup"><span data-stu-id="83f86-128">Set the Options on the Advanced tab</span></span>  
 <span data-ttu-id="83f86-129">[詳細設定] タブを使用して、プロパティとその他のパッケージの設定を管理します。</span><span class="sxs-lookup"><span data-stu-id="83f86-129">Use the Advanced tab to manage properties and other package settings.</span></span>  
  
 <span data-ttu-id="83f86-130">**[追加]** 、 **[編集]** 、 **[削除]**</span><span class="sxs-lookup"><span data-stu-id="83f86-130">**Add**, **Edit**, **Remove**</span></span>  
 <span data-ttu-id="83f86-131">クリックしてプロパティを追加、編集、または削除します。</span><span class="sxs-lookup"><span data-stu-id="83f86-131">Click to add, edit, or remove a property.</span></span>  
  
 <span data-ttu-id="83f86-132">**ログ記録レベル**</span><span class="sxs-lookup"><span data-stu-id="83f86-132">**Logging level**</span></span>  
 <span data-ttu-id="83f86-133">パッケージ実行のログ記録レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="83f86-133">Select the logging level for the package execution.</span></span> <span data-ttu-id="83f86-134">詳細については、「[catalog.set_execution_parameter_value (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83f86-134">For more information, see [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database).</span></span>  
  
 <span data-ttu-id="83f86-135">**エラー時にダンプする**</span><span class="sxs-lookup"><span data-stu-id="83f86-135">**Dump on errors**</span></span>  
 <span data-ttu-id="83f86-136">パッケージの実行中にエラーが発生した場合にダンプ ファイルを作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="83f86-136">Specify whether a dump file is created when errors occur during the package execution.</span></span> <span data-ttu-id="83f86-137">詳細については、「 [パッケージ実行用のダンプ ファイルを生成する](troubleshooting/generating-dump-files-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83f86-137">For more information, see [Generating Dump Files for Package Execution](troubleshooting/generating-dump-files-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="83f86-138">**32 ビット ランタイム**</span><span class="sxs-lookup"><span data-stu-id="83f86-138">**32-bit runtime**</span></span>  
 <span data-ttu-id="83f86-139">パッケージが 32 ビット システムで実行されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="83f86-139">Specify that the package will execute on a 32-bit system.</span></span>  
  
##  <a name="scripting-the-options-in-the-execute-package-dialog-box"></a><a name="script"></a> <span data-ttu-id="83f86-140">[パッケージの実行] ダイアログ ボックスのオプションのスクリプト作成</span><span class="sxs-lookup"><span data-stu-id="83f86-140">Scripting the Options in the Execute Package Dialog Box</span></span>  
 <span data-ttu-id="83f86-141">**[パッケージの実行]** ダイアログ ボックスが表示されているときに、ツール バーの **[スクリプト]** を使用すると、 [!INCLUDE[tsql](../includes/tsql-md.md)] コードを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="83f86-141">While you are in the **Execute Package** dialog box, you can also use the **Script** button on the toolbar to write [!INCLUDE[tsql](../includes/tsql-md.md)] code for you.</span></span> <span data-ttu-id="83f86-142">生成されたスクリプトからは、 **[パッケージの実行]** ダイアログ ボックスで選択したのと同じオプションを指定したストアド プロシージャ [catalog.start_execution (SSISDB データベース)](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="83f86-142">The generated script calls the stored procedures [catalog.start_execution &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) with the same options that you have selected in the **Execute Package** dialog box.</span></span> <span data-ttu-id="83f86-143">このスクリプトは、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]の新しいスクリプト ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="83f86-143">The script appears in a new script window in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span>  
  
  
