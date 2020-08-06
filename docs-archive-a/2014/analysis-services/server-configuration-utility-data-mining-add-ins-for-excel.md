---
title: サーバー構成ユーティリティ (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 28435f86-5cec-4a1e-9b7d-b2069c1ddddb
author: minewiskan
ms.author: owend
ms.openlocfilehash: f985338e44bf0f4b591fcb70a4e093901626149f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743510"
---
# <a name="server-configuration-utility-data-mining-add-ins-for-excel"></a><span data-ttu-id="80dc4-102">サーバー構成ユーティリティ (Excel 用のデータ マイニング アドイン)</span><span class="sxs-lookup"><span data-stu-id="80dc4-102">Server Configuration Utility (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="80dc4-103">Excel 用データマイニングアドインをインストールすると、サーバー構成ユーティリティもインストールされ、アドインを初めて開いたときに実行されます。このトピックでは、ユーティリティを使用してのインスタンスに接続 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] し、データマイニングモデルを操作するためのデータベースを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-103">When you install the Data Mining Add-ins for Excel, a Server Configuration Utility is also installed, and will run the first time you open the add-ins. This topic describes how to use the utility to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and set up a database for working with data mining models.</span></span>  
  

  
##  <a name="step-1-connect-to-analysis-services"></a><a name="bkmk_step1"></a><span data-ttu-id="80dc4-104">手順 1: Analysis Services に接続する</span><span class="sxs-lookup"><span data-stu-id="80dc4-104">Step 1: Connect to Analysis Services</span></span>  
 <span data-ttu-id="80dc4-105">データ マイニング アルゴリズムを提供し、データ マイニング モデルを格納する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-105">Choose the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that provides the data mining algorithms and stores your data mining models.</span></span>  
  
 <span data-ttu-id="80dc4-106">データ マイニング用の接続を作成する場合、データ マイニング モデルをテストできるサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-106">When you create a connection to enable data mining, you should choose a server where you can experiment with data mining models.</span></span> <span data-ttu-id="80dc4-107">サーバー上に新しいデータベースを作成し、その新しいデータベースをデータ マイニング専用にすることをお勧めします。または、自分用のデータ マイニング サーバーを準備するように管理者に依頼します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-107">We recommend that you create a new database on the server and dedicate the new database to data mining, or ask your administrator to prepare a data mining server for you.</span></span> <span data-ttu-id="80dc4-108">この方法で、他のサービスのパフォーマンスに影響を与えずに、モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-108">That way you can build models without affecting the performance of other services.</span></span>  
  
 <span data-ttu-id="80dc4-109">データ マイニングに使用する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーが、ソース データと同じサーバー上に存在する必要はないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="80dc4-109">Note that the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server that you use for data mining does not need to be on the same server as your source data.</span></span>  
  
 <span data-ttu-id="80dc4-110">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="80dc4-110">**Server name**</span></span>  
 <span data-ttu-id="80dc4-111">データ マイニングに使用する [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスが存在するサーバーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-111">Type the name of the server that contains the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you will use for data mining.</span></span>  
  
 <span data-ttu-id="80dc4-112">**認証**</span><span class="sxs-lookup"><span data-stu-id="80dc4-112">**Authentication**</span></span>  
 <span data-ttu-id="80dc4-113">認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-113">Specify the authentication methods.</span></span> <span data-ttu-id="80dc4-114">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]への接続に、管理者が HTTPPump を使用してサーバーへのアクセスを構成した場合以外は、Windows 認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="80dc4-114">Windows Authentication is required for connections to [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], unless your administrator has configured access to the server via the HTTPPump.</span></span>  
  
##  <a name="step-2-allow-temporary-models"></a><a name="bkmk_step2"></a><span data-ttu-id="80dc4-115">手順 2: 一時的なモデルを許可する</span><span class="sxs-lookup"><span data-stu-id="80dc4-115">Step 2: Allow Temporary Models</span></span>  
 <span data-ttu-id="80dc4-116">アドインを使用する前に、一時的なマイニング モデルの作成を許可するように [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のサーバー プロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80dc4-116">Before you can use the add-ins, an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server property must be changed to permit the creation of temporary mining models.</span></span>  
  
 <span data-ttu-id="80dc4-117">一時的なマイニングモデルは、*セッションモデル*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-117">Temporary mining models are also called *session models*.</span></span> <span data-ttu-id="80dc4-118">これは、現在のセッションが開いている間だけモデルを格納できるためです。</span><span class="sxs-lookup"><span data-stu-id="80dc4-118">This is because the models are stored only as long as your current session is open.</span></span> <span data-ttu-id="80dc4-119">サーバーへの接続を閉じると、セッションが終了し、セッション中に使用されたモデルはすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-119">When you close your connection to the server, the session is ended and any models used during the session are deleted.</span></span>  
  
 <span data-ttu-id="80dc4-120">セッションのマイニング モデルを使用しても、サーバー上の記憶領域が消費されることはありませんが、データ マイニング モデルの作成に伴うオーバーヘッドにより、サーバーのパフォーマンスが低下する可能性はあります。</span><span class="sxs-lookup"><span data-stu-id="80dc4-120">The use of session mining models does not affect storage space on the server, but the overhead involved in creating data mining models may affect the performance of the server.</span></span>  
  
 <span data-ttu-id="80dc4-121">ウィザードでは、最初に指定したサーバーの設定が検出されます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-121">The wizard first detects the settings on the server that you specified.</span></span> <span data-ttu-id="80dc4-122">サーバーで一時的なマイニングモデルが既に許可されている場合は、[**次へ**] をクリックして続行することができます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-122">If the server already allows temporary mining models, you can click **Next** to continue.</span></span> <span data-ttu-id="80dc4-123">ウィザードでは、指定した [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーで一時的なマイニング モデルを有効にする方法や、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 管理者に対して要求を行う方法に関する説明も表示されます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-123">The wizard also provides instructions for how to enable temporary mining models on the specified [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server, or how to make a request to your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] administrator.</span></span>  
  
##  <a name="step-3-create-database-for-add-in-users"></a><a name="bkmk_step3"></a><span data-ttu-id="80dc4-124">手順 3: アドインユーザー用のデータベースを作成する</span><span class="sxs-lookup"><span data-stu-id="80dc4-124">Step 3: Create Database for Add-in Users</span></span>  
 <span data-ttu-id="80dc4-125">セットアップおよび構成ウィザードのこのページでは、データ マイニング専用の新しいデータベースを作成すること、または既存の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-125">On this page of the setup and configuration wizard, you can create a new database that is dedicated to data mining, or select an existing [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="80dc4-126">データ マイニングには、多次元モードで実行されている [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="80dc4-126">Data mining requires an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that is running in multidimensional mode.</span></span> <span data-ttu-id="80dc4-127">テーブル モードでは、データ マイニングはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="80dc4-127">Tabular mode does not support data mining.</span></span>  
  
 <span data-ttu-id="80dc4-128">データ マイニング専用の別のデータベースを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="80dc4-128">We recommend that you create a separate database dedicated to data mining.</span></span> <span data-ttu-id="80dc4-129">この結果、他のソリューションのオブジェクトに影響を与えずにデータ マイニング モデルを試してみることができます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-129">This lets you experiment with data mining models without affecting other solution objects.</span></span>  
  
 <span data-ttu-id="80dc4-130">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンス上にある既存のデータベースを選択した場合は、アドインを使用してモデルを作成する際に、その名前のモデルが既に存在する状況では既存のモデルを上書きできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="80dc4-130">If you choose an existing database on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], note that it is possible to overwrite existing models if you use the add-ins to create a model and a model of that name already exists.</span></span>  
  
 <span data-ttu-id="80dc4-131">**新しいデータベースの作成**</span><span class="sxs-lookup"><span data-stu-id="80dc4-131">**Create new database**</span></span>  
 <span data-ttu-id="80dc4-132">選択したサーバーに新規データベースを作成する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-132">Select this option to create a new database on the selected server.</span></span> <span data-ttu-id="80dc4-133">データ マイニング データベースには、データ ソース、マイニング構造、およびマイニング モデルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-133">A data mining database will store your data sources, mining structures, and mining models.</span></span>  
  
 <span data-ttu-id="80dc4-134">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="80dc4-134">**Database name**</span></span>  
 <span data-ttu-id="80dc4-135">新規データベースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-135">Type the name of the new database.</span></span> <span data-ttu-id="80dc4-136">この名前がまだ使用されていない場合は、新規に作成されます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-136">If the name is not already in use, it will be created for you.</span></span>  
  
 <span data-ttu-id="80dc4-137">**[既存のデータベースを使用する]**</span><span class="sxs-lookup"><span data-stu-id="80dc4-137">**Use existing database**</span></span>  
 <span data-ttu-id="80dc4-138">既存の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースを使用する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-138">Select this option to use an existing [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="80dc4-139">**[データベース]**</span><span class="sxs-lookup"><span data-stu-id="80dc4-139">**Database**</span></span>  
 <span data-ttu-id="80dc4-140">既存のデータベースを使用するためにこのオプションを選択した場合は、一覧からデータベース名を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80dc4-140">If you chose the option to use an existing database, you must select the database name from the list.</span></span>  
  
##  <a name="step-4-give-add-in-users-appropriate-permissions"></a><a name="bkmk_step4"></a><span data-ttu-id="80dc4-141">手順 4: アドインユーザーに適切なアクセス許可を付与する</span><span class="sxs-lookup"><span data-stu-id="80dc4-141">Step 4: Give Add-in Users Appropriate Permissions</span></span>  
 <span data-ttu-id="80dc4-142">データ マイニング構造およびモデルを参照、編集、処理、または作成するために必要な権限を、自分 (またはアドインの他のユーザー) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80dc4-142">You must ensure that you (and any other users of the add-ins) have the necessary permissions to browse, edit, process, or create data mining structures and models.</span></span>  
  
 <span data-ttu-id="80dc4-143">既定では、アドインを使用するには統合 Windows 認証が必要です。</span><span class="sxs-lookup"><span data-stu-id="80dc4-143">By default, integrated Windows Authentication is required to use the add-ins.</span></span>  
  
 <span data-ttu-id="80dc4-144">**[アドイン ユーザーにデータベース管理権限を与える]**</span><span class="sxs-lookup"><span data-stu-id="80dc4-144">**Give add-in users database administration permissions**</span></span>  
 <span data-ttu-id="80dc4-145">一覧に表示されたユーザーにデータベースに対する管理アクセス権を付与するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-145">Select this option to give the listed users administrative access to the database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="80dc4-146">これらの権限は、[**データベース名**] ボックスに表示されているデータベースにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-146">These permissions apply only to the database listed in the **Database name** box.</span></span>  
  
 <span data-ttu-id="80dc4-147">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="80dc4-147">**Database name**</span></span>  
 <span data-ttu-id="80dc4-148">選択しているデータベースの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="80dc4-148">Displays the name of the selected database.</span></span>  
  
 <span data-ttu-id="80dc4-149">**[追加するユーザーまたはグループを指定します]**</span><span class="sxs-lookup"><span data-stu-id="80dc4-149">**Specify users or groups to add**</span></span>  
 <span data-ttu-id="80dc4-150">データ マイニングで使用するデータベースへのアクセスを許可するログインを選択します。</span><span class="sxs-lookup"><span data-stu-id="80dc4-150">Select the logins that will have access to the database used for data mining.</span></span>  
  
 <span data-ttu-id="80dc4-151">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="80dc4-151">**Add**</span></span>  
 <span data-ttu-id="80dc4-152">ダイアログ ボックスを開いてユーザーまたはグループを追加する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dc4-152">Click to open a dialog box and add users or groups.</span></span>  
  
 <span data-ttu-id="80dc4-153">**削除**</span><span class="sxs-lookup"><span data-stu-id="80dc4-153">**Remove**</span></span>  
 <span data-ttu-id="80dc4-154">選択したユーザーまたはグループを、管理権限を持つユーザーの一覧から削除する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="80dc4-154">Click to remove the selected user or group from the list of users with administration permissions.</span></span>  
  
  
