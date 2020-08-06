---
title: 'レッスン 2: ループの追加 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 01f2ed61-1e5a-4ec6-b6a6-2bd070c64077
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 65efb84b4e50b470470e396bbe5681ce4b5dfac3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633895"
---
# <a name="lesson-2-adding-looping"></a><span data-ttu-id="3f13c-102">レッスン 2: ループの追加</span><span class="sxs-lookup"><span data-stu-id="3f13c-102">Lesson 2: Adding Looping</span></span>
  <span data-ttu-id="3f13c-103">「[レッスン 1: プロジェクトと基本パッケージの作成](lesson-1-create-a-project-and-basic-package-with-ssis.md)」では、単一のフラットファイルソースからデータを抽出し、参照変換を使用してデータを変換した後、最後にデータを**AdventureWorksDW2012**サンプルデータベースの**FactCurrency**ファクトテーブルに読み込むパッケージを作成しました。</span><span class="sxs-lookup"><span data-stu-id="3f13c-103">In [Lesson 1: Creating the Project and Basic Package](lesson-1-create-a-project-and-basic-package-with-ssis.md), you created a package that extracted data from a single flat file source, transformed the data using Lookup transformations, and finally loaded the data into the **FactCurrency** fact table of the **AdventureWorksDW2012** sample database.</span></span>  
  
 <span data-ttu-id="3f13c-104">しかし、抽出、変換、読み込み (ETL) プロセスでフラット ファイルを 1 つだけ使用することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="3f13c-104">However, it is rare for an extract, transform, and load (ETL) process to use a single flat file.</span></span> <span data-ttu-id="3f13c-105">通常の ETL プロセスでは、複数のフラット ファイル ソースからデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="3f13c-105">A typical ETL process would extract data from multiple flat file sources.</span></span> <span data-ttu-id="3f13c-106">複数のソースからデータを抽出するには、反復型の制御フローが必要となります。</span><span class="sxs-lookup"><span data-stu-id="3f13c-106">Extracting data from multiple sources requires an iterative control flow.</span></span> <span data-ttu-id="3f13c-107">の最も期待される機能の1つ [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、繰り返しまたはループをパッケージに簡単に追加できることです。</span><span class="sxs-lookup"><span data-stu-id="3f13c-107">One of the most anticipated features of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is the ability to easily add iteration or looping to packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="3f13c-108">には、パッケージ全体をループさせる 2 種類のコンテナーがあります。1 つは Foreach ループ コンテナー、もう 1 つは For ループ コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="3f13c-108">provides two types of containers for looping through packages: the Foreach Loop container and the For Loop container.</span></span> <span data-ttu-id="3f13c-109">Foreach ループ コンテナーが列挙子を使用してループを実行するのに対し、For ループ コンテナーは、通常、変数式を使用します。</span><span class="sxs-lookup"><span data-stu-id="3f13c-109">The Foreach Loop container uses an enumerator to perform the looping, whereas the For Loop container typically uses a variable expression.</span></span> <span data-ttu-id="3f13c-110">このレッスンでは Foreach ループ コンテナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="3f13c-110">This lesson uses the Foreach Loop container.</span></span>  
  
 <span data-ttu-id="3f13c-111">パッケージで Foreach ループ コンテナーを使用すれば、指定した列挙子の各メンバーについて、制御フローを繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="3f13c-111">The Foreach Loop container enables a package to repeat the control flow for each member of a specified enumerator.</span></span> <span data-ttu-id="3f13c-112">Foreach ループ コンテナーでは、次のものを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="3f13c-112">With the Foreach Loop container, you can enumerate:</span></span>  
  
-   <span data-ttu-id="3f13c-113">ADO レコードセット行</span><span class="sxs-lookup"><span data-stu-id="3f13c-113">ADO recordset rows</span></span>  
  
-   <span data-ttu-id="3f13c-114">ADO .Net スキーマ情報</span><span class="sxs-lookup"><span data-stu-id="3f13c-114">ADO .Net schema information</span></span>  
  
-   <span data-ttu-id="3f13c-115">ファイル構造とディレクトリ構造</span><span class="sxs-lookup"><span data-stu-id="3f13c-115">File and directory structures</span></span>  
  
-   <span data-ttu-id="3f13c-116">システム変数、パッケージ変数、ユーザー変数</span><span class="sxs-lookup"><span data-stu-id="3f13c-116">System, package and user variables</span></span>  
  
-   <span data-ttu-id="3f13c-117">変数に含まれる列挙可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="3f13c-117">Enumerable objects contained in a variable</span></span>  
  
-   <span data-ttu-id="3f13c-118">コレクション内のアイテム</span><span class="sxs-lookup"><span data-stu-id="3f13c-118">Items in a collection</span></span>  
  
-   <span data-ttu-id="3f13c-119">XML パス言語 (XPath) 式内のノード</span><span class="sxs-lookup"><span data-stu-id="3f13c-119">Nodes in an XML Path Language (XPath) expression</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="3f13c-120">管理オブジェクト (SMO)</span><span class="sxs-lookup"><span data-stu-id="3f13c-120">Management Objects (SMO)</span></span>  
  
 <span data-ttu-id="3f13c-121">このレッスンでは、レッスン 1 で作成した単純な ETL パッケージを修正し、Foreach ループ コンテナーの機能を活用します。</span><span class="sxs-lookup"><span data-stu-id="3f13c-121">In this lesson, you will modify the simple ETL package created in Lesson 1 to take advantage of the Foreach Loop container.</span></span> <span data-ttu-id="3f13c-122">また、ユーザー定義のパッケージ変数を設定し、フォルダー内のすべてのフラット ファイルに対し、チュートリアル パッケージが反復処理を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3f13c-122">You will also set user-defined package variables to enable the tutorial package to iterate through all the flat files in the folder.</span></span> <span data-ttu-id="3f13c-123">前のレッスンを完了していない場合は、チュートリアルに含まれている、レッスン 1 を完了した状態のパッケージをコピーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3f13c-123">If you have not completed the previous lesson, you can also copy the completed Lesson 1 package that is included with the tutorial.</span></span>  
  
 <span data-ttu-id="3f13c-124">このレッスンでは、データ フローは変更せずに、制御フローのみを変更します。</span><span class="sxs-lookup"><span data-stu-id="3f13c-124">In this lesson, you will not modify the data flow, only the control flow.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3f13c-125">このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="3f13c-125">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="3f13c-126">**AdventureWorksDW2012**をインストールして配置する方法の詳細については、 [CodePlex での Reporting Services 製品サンプル](https://go.microsoft.com/fwlink/p/?LinkID=526910)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f13c-126">For more information about how to install and deploy **AdventureWorksDW2012**, see [Reporting Services Product Samples on CodePlex](https://go.microsoft.com/fwlink/p/?LinkID=526910).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="3f13c-127">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="3f13c-127">Lesson Tasks</span></span>  
 <span data-ttu-id="3f13c-128">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f13c-128">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="3f13c-129">手順 1:レッスン 1 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="3f13c-129">Step 1: Copying the Lesson 1 Package</span></span>](lesson-2-1-copying-the-lesson-1-package.md)  
  
-   [<span data-ttu-id="3f13c-130">手順 2:Foreach ループ コンテナーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="3f13c-130">Step 2: Adding and Configuring the Foreach Loop Container</span></span>](lesson-2-2-adding-and-configuring-the-foreach-loop-container.md)  
  
-   [<span data-ttu-id="3f13c-131">手順 3:フラット ファイル接続マネージャーの変更</span><span class="sxs-lookup"><span data-stu-id="3f13c-131">Step 3: Modifying the Flat File Connection Manager</span></span>](lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
-   [<span data-ttu-id="3f13c-132">手順 4:レッスン 2 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="3f13c-132">Step 4: Testing the Lesson 2 Tutorial Package</span></span>](lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="3f13c-133">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="3f13c-133">Start the Lesson</span></span>  
 [<span data-ttu-id="3f13c-134">手順 1:レッスン 1 のパッケージのコピー</span><span class="sxs-lookup"><span data-stu-id="3f13c-134">Step 1: Copying the Lesson 1 Package</span></span>](lesson-2-1-copying-the-lesson-1-package.md)  
  
## <a name="see-also"></a><span data-ttu-id="3f13c-135">参照</span><span class="sxs-lookup"><span data-stu-id="3f13c-135">See Also</span></span>  
 [<span data-ttu-id="3f13c-136">For ループ コンテナー</span><span class="sxs-lookup"><span data-stu-id="3f13c-136">For Loop Container</span></span>](control-flow/for-loop-container.md)  
  
  
