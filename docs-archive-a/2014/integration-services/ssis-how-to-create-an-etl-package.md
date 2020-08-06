---
title: 'SSIS チュートリアル: 簡単な ETL パッケージの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS, tutorials
- packages [Integration Services], tutorials
- Integration Services, tutorials
- SQL Server Integration Services, tutorials
- logs [Integration Services], tutorials
- walkthroughs [Integration Services]
ms.assetid: d6d5bb1f-4cb1-4605-9cd6-f60b858382c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 780b008052a2ff64aa75b2036aa7202128f95ae2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718513"
---
# <a name="ssis-tutorial-creating-a-simple-etl-package"></a><span data-ttu-id="b29b4-102">SSIS チュートリアル:簡単な ETL パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="b29b4-102">SSIS Tutorial: Creating a Simple ETL Package</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="b29b4-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) は、データウェアハウスの抽出、変換、読み込み (ETL) パッケージを含む、高パフォーマンスのデータ統合ソリューションを構築するためのプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="b29b4-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (SSIS) is a platform for building high performance data integration solutions, including extraction, transformation, and load (ETL) packages for data warehousing.</span></span> <span data-ttu-id="b29b4-104">SSIS には、パッケージを作成およびデバッグするためのグラフィカルなツールやウィザード、FTP 操作などのワークフロー機能の実行、SQL ステートメントの実行、および電子メール メッセージの送信を実行するためのタスク、データの抽出や読み込みに使用するデータの変換元と変換先、データのクリーニング、集計、マージ、コピーを行う変換、パッケージの実行と保存を管理するための [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービス、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクト モデルをプログラミングするための API (アプリケーション プログラミング インターフェイス) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b29b4-104">SSIS includes graphical tools and wizards for building and debugging packages; tasks for performing workflow functions such as FTP operations, executing SQL statements, and sending e-mail messages; data sources and destinations for extracting and loading data; transformations for cleaning, aggregating, merging, and copying data; a management service, the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service for administering package execution and storage; and application programming interfaces (APIs) for programming the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object model.</span></span>  
  
 <span data-ttu-id="b29b4-105">このチュートリアルでは、デザイナーを使用して [!INCLUDE[ssIS](../includes/ssis-md.md)] 簡単なパッケージを作成する方法について説明し [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b29b4-105">In this tutorial, you will learn how to use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create a simple [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="b29b4-106">作成するパッケージは、フラット ファイルからデータを取得し、そのデータを変換した後で、ファクト テーブルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-106">The package that you create takes data from a flat file, reformats the data, and then inserts the reformatted data into a fact table.</span></span> <span data-ttu-id="b29b4-107">以降のレッスンでは、このパッケージを拡張して、ループ、パッケージ構成、ログ記録、およびエラー フローについて学習します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-107">In following lessons, the package is expanded to demonstrate looping, package configurations, logging and error flow.</span></span>  
  
 <span data-ttu-id="b29b4-108">チュートリアルで使用するサンプル データをインストールすると、チュートリアルの各レッスンで作成するパッケージの完了した状態のバージョンもインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b29b4-108">When you install the sample data that the tutorial uses, you also install the completed versions of the packages that you will create in each lesson of the tutorial.</span></span> <span data-ttu-id="b29b4-109">完了した状態のパッケージを使用すれば、手順をとばし、後のレッスンからチュートリアルを開始することができます。</span><span class="sxs-lookup"><span data-stu-id="b29b4-109">By using the completed packages, you can skip ahead and begin the tutorial at a later lesson if you like.</span></span> <span data-ttu-id="b29b4-110">パッケージまたは新しい開発環境を初めて使用する場合は、レッスン 1 から開始することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b29b4-110">If this is your first time working with packages or the new development environment, we recommend that you begin with Lesson1.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="b29b4-111">学習する内容</span><span class="sxs-lookup"><span data-stu-id="b29b4-111">What You Will Learn</span></span>  
 <span data-ttu-id="b29b4-112">で使用できる新しいツール、コントロール、および機能について理解を深めるには、それらを使用することをお勧めし [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b29b4-112">The best way to become acquainted with the new tools, controls and features available in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is to use them.</span></span> <span data-ttu-id="b29b4-113">このチュートリアルでは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用して、ループ、構成、エラー フロー ロジック、およびログの記録を含む簡単な ETL パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-113">This tutorial walks you through [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create a simple ETL package that includes looping, configurations, error flow logic and logging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b29b4-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="b29b4-114">Requirements</span></span>  
 <span data-ttu-id="b29b4-115">このチュートリアルは、データベースの基本的な操作に慣れているユーザーを対象としていますが、で利用できる新機能にはあまり影響を与えません [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b29b4-115">This tutorial is intended for users familiar with fundamental database operations, but who have limited exposure to the new features available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b29b4-116">このチュートリアルを使用するには、システムに次のコンポーネントがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b29b4-116">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="b29b4-117">および **AdventureWorksDW2012** データベース。</span><span class="sxs-lookup"><span data-stu-id="b29b4-117">with the **AdventureWorksDW2012** database.</span></span> <span data-ttu-id="b29b4-118">セキュリティ強化のため、既定ではサンプル データベースがインストールされません。</span><span class="sxs-lookup"><span data-stu-id="b29b4-118">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="b29b4-119">**AdventureWorksDW2012** データベースをダウンロードするには、「 [SQL Server 2012 用 Adventure Works](https://go.microsoft.com/fwlink/?LinkId=275026)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b29b4-119">To download the **AdventureWorksDW2012** database, see [Adventure Works for SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=275026).</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="b29b4-120">データベース (\*.mdf ファイル) をアタッチすると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] では、既定で .ldf ファイルが検索されます。</span><span class="sxs-lookup"><span data-stu-id="b29b4-120">When you attach the database (\*.mdf file), [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] will by default search for an .ldf file.</span></span> <span data-ttu-id="b29b4-121">**[データベースのインポート]** ダイアログ ボックスで [OK] をクリックする前に、.ldf ファイルを手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b29b4-121">You must manually remove the .ldf file before clicking OK in the **Attach Databases** dialog box.</span></span>  
    >   
    >  <span data-ttu-id="b29b4-122">データベースのインポートの詳細については、「 [データベースのインポート](../relational-databases/databases/attach-a-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b29b4-122">For more information about attaching databases, see [Attach a Database](../relational-databases/databases/attach-a-database.md).</span></span>  
  
-   <span data-ttu-id="b29b4-123">サンプル データ。</span><span class="sxs-lookup"><span data-stu-id="b29b4-123">Sample data.</span></span> <span data-ttu-id="b29b4-124">このサンプル データは、 [!INCLUDE[ssIS](../includes/ssis-md.md)] のレッスン パッケージに含まれています。</span><span class="sxs-lookup"><span data-stu-id="b29b4-124">The sample data is included with the [!INCLUDE[ssIS](../includes/ssis-md.md)] lesson packages.</span></span> <span data-ttu-id="b29b4-125">サンプル データとレッスン パッケージをダウンロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-125">To download the sample data and the lesson packages, do the following.</span></span>  
  
    1.  <span data-ttu-id="b29b4-126">「 [Integration Services 製品サンプル](https://go.microsoft.com/fwlink/?LinkId=275027)」に移動します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-126">Navigate to [Integration Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=275027)</span></span>  
  
    2.  <span data-ttu-id="b29b4-127">[**ダウンロード**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b29b4-127">Click the **DOWNLOADS** tab.</span></span>  
  
    3.  <span data-ttu-id="b29b4-128">SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b29b4-128">Click the SQL2012.Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip file.</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="b29b4-129">このチュートリアルで行うレッスン</span><span class="sxs-lookup"><span data-stu-id="b29b4-129">Lessons in This Tutorial</span></span>  
 [<span data-ttu-id="b29b4-130">レッスン 1:プロジェクトと基本パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="b29b4-130">Lesson 1: Creating the Project and Basic Package</span></span>](lesson-1-create-a-project-and-basic-package-with-ssis.md)  
 <span data-ttu-id="b29b4-131">このレッスンでは、簡単な ETL パッケージを作成します。パッケージの内容は、1 つのフラット ファイルからデータを抽出し、参照変換を使用してデータを変換し、最後に結果をファクト テーブルのディメンションに読み込ませるというものです。</span><span class="sxs-lookup"><span data-stu-id="b29b4-131">In this lesson, you will create a simple ETL package that extracts data from a single flat file, transforms the data using lookup transformations and finally loads the result into a fact table destination.</span></span>  
  
 [<span data-ttu-id="b29b4-132">レッスン 2: ループの追加</span><span class="sxs-lookup"><span data-stu-id="b29b4-132">Lesson 2: Adding Looping</span></span>](lesson-2-adding-looping-with-ssis.md)  
 <span data-ttu-id="b29b4-133">このレッスンでは、レッスン 1 で作成したパッケージを拡張し、新しいループ機能を活用して、複数のフラット ファイルを単一のデータ フロー プロセスに抽出するパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-133">In this lesson, you will expand the package you created in Lesson 1 to take advantage of new looping features to extract multiple flat files into a single data flow process.</span></span>  
  
 [<span data-ttu-id="b29b4-134">レッスン 3:ログ機能の追加</span><span class="sxs-lookup"><span data-stu-id="b29b4-134">Lesson 3: Adding Logging</span></span>](lesson-3-add-logging-with-ssis.md)  
 <span data-ttu-id="b29b4-135">このレッスンでは、レッスン 2 で作成したパッケージを拡張し、新しいログ機能を活用するパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-135">In this lesson, you will expand the package you created in Lesson 2 to take advantage of new logging features.</span></span>  
  
 [<span data-ttu-id="b29b4-136">レッスン 4:エラー フロー リダイレクトの追加</span><span class="sxs-lookup"><span data-stu-id="b29b4-136">Lesson 4: Adding Error Flow Redirection</span></span>](lesson-4-add-error-flow-redirection-with-ssis.md)  
 <span data-ttu-id="b29b4-137">このレッスンでは、レッスン 3 で作成したパッケージを拡張し、新しいエラー出力構成を活用するパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-137">In this lesson, you will expand the package you created in lesson 3 to take advantage of new error output configurations.</span></span>  
  
 [<span data-ttu-id="b29b4-138">レッスン 5: パッケージ配置モデルのパッケージ構成の追加</span><span class="sxs-lookup"><span data-stu-id="b29b4-138">Lesson 5: Adding Package Configurations for the Package Deployment Model</span></span>](lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md)  
 <span data-ttu-id="b29b4-139">このレッスンでは、レッスン 4 で作成したパッケージを拡張し、新しいパッケージ構成オプションを活用するパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-139">In this lesson, you will expand the package you created in Lesson 4 to take advantage of new package configuration options.</span></span>  
  
 [<span data-ttu-id="b29b4-140">レッスン 6: プロジェクト配置モデルを持つパラメーターを使用する</span><span class="sxs-lookup"><span data-stu-id="b29b4-140">Lesson 6: Using Parameters with the Project Deployment Model</span></span>](lesson-6-using-parameters-with-the-project-deployment-model-in-ssis.md)  
 <span data-ttu-id="b29b4-141">このレッスンでは、レッスン 5 で作成したパッケージを拡張し、プロジェクト配置モデルで新しいパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="b29b4-141">In this lesson, you will expand the package you created in Lesson 5 to take advantage of using new parameters with the project deployment model.</span></span>  
  
  
