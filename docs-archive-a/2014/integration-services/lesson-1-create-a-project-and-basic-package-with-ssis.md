---
title: 'レッスン 1: プロジェクトと基本パッケージの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 84d0b877-603f-4f8e-bb6b-671558ade5c2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1a9ddc36ef242cc4e4b146e90dfa9de470e68d83
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641084"
---
# <a name="lesson-1-creating-the-project-and-basic-package"></a><span data-ttu-id="ae3ad-102">レッスン 1:プロジェクトと基本パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="ae3ad-102">Lesson 1: Creating the Project and Basic Package</span></span>
  <span data-ttu-id="ae3ad-103">このレッスンでは、簡単な ETL パッケージを作成します。このパッケージは、1 つのフラット ファイル ソースからデータを抽出し、2 つの参照変換コンポーネントを使用してそのデータを変換します。さらに、変換したデータを、 **AdventureWorksDW2012** の **FactCurrency**ファクト テーブルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-103">In this lesson, you will create a simple ETL package that extracts data from a single flat file source, transforms the data using two lookup transformation components, and writes that data to the **FactCurrency** fact table in **AdventureWorksDW2012**.</span></span> <span data-ttu-id="ae3ad-104">ここでは、新しいパッケージを作成する方法、データの変換元と変換先の接続を追加、構成する方法、新しい制御フロー コンポーネントとデータ フロー コンポーネントを操作する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-104">As part of this lesson, you will learn how to create new packages, add and configure data source and destination connections, and work with new control flow and data flow components.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ae3ad-105">このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-105">This tutorial requires the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="ae3ad-106">**AdventureWorksDW2012**のインストールと展開の詳細については、「 [Microsoft SQL Server 製品サンプル: Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-106">For more information on installing and deploying **AdventureWorksDW2012**, see [Microsoft SQL Server Product Samples: Reporting Services](https://archive.codeplex.com/?p=msftrsprodsamples).</span></span>  
  
## <a name="understanding-the-package-requirements"></a><span data-ttu-id="ae3ad-107">パッケージ要件について</span><span class="sxs-lookup"><span data-stu-id="ae3ad-107">Understanding the Package Requirements</span></span>  
 <span data-ttu-id="ae3ad-108">このチュートリアルには、Microsoft SQL Server Data Tools が必要です。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-108">This tutorial requires Microsoft SQL Server Data Tools.</span></span>  
  
 <span data-ttu-id="ae3ad-109">SQL Server Data Tools のインストールの詳細については、「 [SQL Server Data Tools のダウンロード](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-109">For more information on installing the SQL Server Data Tools see [SQL Server Data Tools Download](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017).</span></span>  
  
 <span data-ttu-id="ae3ad-110">パッケージを作成する前に、ソース データの形式と変換先データの形式をよく理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-110">Before creating a package, you need a good understanding of the formatting used in both the source data and the destination.</span></span> <span data-ttu-id="ae3ad-111">両方のデータ形式を理解しておけば、ソース データを変換先にマップするための変換を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-111">Once you understand both of these data formats, you will be ready to define the transformations necessary to map the source data to the destination.</span></span>  
  
### <a name="looking-at-the-source"></a><span data-ttu-id="ae3ad-112">ソース データの確認</span><span class="sxs-lookup"><span data-stu-id="ae3ad-112">Looking at the Source</span></span>  
 <span data-ttu-id="ae3ad-113">このチュートリアルで使用するソース データは、フラット ファイル (SampleCurrencyData.txt) に保存されている通貨履歴データのセットです。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-113">For this tutorial, the source data is a set of historical currency data contained in the flat file, SampleCurrencyData.txt.</span></span> <span data-ttu-id="ae3ad-114">ソース データには、通貨の平均相場、通貨キー、日付キー、1 日の最終相場の 4 つの列があります。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-114">The source data has the following four columns: the average rate of the currency, a currency key, a date key, and the end-of-day rate.</span></span>  
  
 <span data-ttu-id="ae3ad-115">以下は、SampleCurrencyData.txt ファイルに保存されているソース データの例です。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-115">Here is an example of the source data contained in the SampleCurrencyData.txt file:</span></span>  
  
 `1.00070049USD9/3/05 0:001.001201442`  
  
 `1.00020004USD9/4/05 0:001`  
  
 `1.00020004USD9/5/05 0:001.001201442`  
  
 `1.00020004USD9/6/05 0:001`  
  
 `1.00020004USD9/7/05 0:001.00070049`  
  
 `1.00070049USD9/8/05 0:000.99980004`  
  
 `1.00070049USD9/9/05 0:001.001502253`  
  
 `1.00070049USD9/10/05 0:000.99990001`  
  
 `1.00020004USD9/11/05 0:001.001101211`  
  
 `1.00020004USD9/12/05 0:000.99970009`  
  
 <span data-ttu-id="ae3ad-116">フラット ファイル ソース データを操作する前に、フラット ファイル接続マネージャーがフラット ファイル データをどのように解釈するのかを理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-116">When working with flat file source data, it is important to understand how the Flat File connection manager interprets the flat file data.</span></span> <span data-ttu-id="ae3ad-117">フラット ファイル ソースが Unicode の場合、すべての列が [DT_WSTR] として定義され、既定の列幅 50 が設定されます。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-117">If the flat file source is Unicode, the Flat File connection manager defines all columns as [DT_WSTR] with a default column width of 50.</span></span> <span data-ttu-id="ae3ad-118">フラット ファイル ソースが ANSI エンコードの場合は、列が [DT_STR] として定義され、列幅が 50 になります。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-118">If the flat file source is ANSI-encoded, the columns are defined as [DT_STR] with a column width of 50.</span></span> <span data-ttu-id="ae3ad-119">これらの既定値を、使用中のデータに適した文字列型の列に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-119">You will probably have to change these defaults to make the string column types more appropriate for your data.</span></span> <span data-ttu-id="ae3ad-120">既定値を変更するには、データの書き込み先 (変換先) のデータ型を確認し、フラット ファイル接続マネージャーで適切なデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-120">To do this, you will need to look at the data type of the destination where the data will be written to and then choose the correct type within the Flat File connection manager.</span></span>  
  
### <a name="looking-at-the-destination"></a><span data-ttu-id="ae3ad-121">変換先の確認</span><span class="sxs-lookup"><span data-stu-id="ae3ad-121">Looking at the Destination</span></span>  
 <span data-ttu-id="ae3ad-122">ソース データの最終的な変換先は、 **AdventureWorksDW** の **FactCurrency**ファクト テーブルです。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-122">The ultimate destination for the source data is the **FactCurrency** fact table in **AdventureWorksDW**.</span></span> <span data-ttu-id="ae3ad-123">次の表に示すように、 **FactCurrency** ファクト テーブルには 4 つの列があり、さらに 2 つのディメンション テーブルへのリレーションシップがあります。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-123">The **FactCurrency** fact table has four columns, and has relationships to two dimension tables, as shown in the following table.</span></span>  
  
|<span data-ttu-id="ae3ad-124">列名</span><span class="sxs-lookup"><span data-stu-id="ae3ad-124">Column Name</span></span>|<span data-ttu-id="ae3ad-125">データ型</span><span class="sxs-lookup"><span data-stu-id="ae3ad-125">Data Type</span></span>|<span data-ttu-id="ae3ad-126">参照テーブル</span><span class="sxs-lookup"><span data-stu-id="ae3ad-126">Lookup Table</span></span>|<span data-ttu-id="ae3ad-127">参照列</span><span class="sxs-lookup"><span data-stu-id="ae3ad-127">Lookup Column</span></span>|  
|-----------------|---------------|------------------|-------------------|  
|<span data-ttu-id="ae3ad-128">AverageRate</span><span class="sxs-lookup"><span data-stu-id="ae3ad-128">AverageRate</span></span>|<span data-ttu-id="ae3ad-129">float</span><span class="sxs-lookup"><span data-stu-id="ae3ad-129">float</span></span>|<span data-ttu-id="ae3ad-130">なし</span><span class="sxs-lookup"><span data-stu-id="ae3ad-130">None</span></span>|<span data-ttu-id="ae3ad-131">なし</span><span class="sxs-lookup"><span data-stu-id="ae3ad-131">None</span></span>|  
|<span data-ttu-id="ae3ad-132">CurrencyKey</span><span class="sxs-lookup"><span data-stu-id="ae3ad-132">CurrencyKey</span></span>|<span data-ttu-id="ae3ad-133">int (FK)</span><span class="sxs-lookup"><span data-stu-id="ae3ad-133">int (FK)</span></span>|<span data-ttu-id="ae3ad-134">DimCurrency</span><span class="sxs-lookup"><span data-stu-id="ae3ad-134">DimCurrency</span></span>|<span data-ttu-id="ae3ad-135">CurrencyKey (PK)</span><span class="sxs-lookup"><span data-stu-id="ae3ad-135">CurrencyKey (PK)</span></span>|  
|<span data-ttu-id="ae3ad-136">DateKey</span><span class="sxs-lookup"><span data-stu-id="ae3ad-136">DateKey</span></span>|<span data-ttu-id="ae3ad-137">int (FK)</span><span class="sxs-lookup"><span data-stu-id="ae3ad-137">Int (FK)</span></span>|<span data-ttu-id="ae3ad-138">DimDate</span><span class="sxs-lookup"><span data-stu-id="ae3ad-138">DimDate</span></span>|<span data-ttu-id="ae3ad-139">DateKey (PK)</span><span class="sxs-lookup"><span data-stu-id="ae3ad-139">DateKey (PK)</span></span>|  
|<span data-ttu-id="ae3ad-140">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="ae3ad-140">EndOfDayRate</span></span>|<span data-ttu-id="ae3ad-141">float</span><span class="sxs-lookup"><span data-stu-id="ae3ad-141">float</span></span>|<span data-ttu-id="ae3ad-142">なし</span><span class="sxs-lookup"><span data-stu-id="ae3ad-142">None</span></span>|<span data-ttu-id="ae3ad-143">なし</span><span class="sxs-lookup"><span data-stu-id="ae3ad-143">None</span></span>|  
  
### <a name="mapping-source-data-to-be-compatible-with-the-destination"></a><span data-ttu-id="ae3ad-144">ソース データと変換先データのマッピング</span><span class="sxs-lookup"><span data-stu-id="ae3ad-144">Mapping Source Data to be Compatible with the Destination</span></span>  
 <span data-ttu-id="ae3ad-145">変換元と変換先のデータ形式を調べてみると、 **CurrencyKey** と **DateKey** の値については参照が必要であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-145">Analysis of the source and destination data formats indicates that lookups will be necessary for the **CurrencyKey** and **DateKey** values.</span></span> <span data-ttu-id="ae3ad-146">これらの参照を実行する変換では、 **DimCurrency** ディメンション テーブルと **DimDate** ディメンション テーブルの代替キーを使用することにより、 **CurrencyKey** と **DateKey** の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-146">The transformations that will perform these lookups will obtain the **CurrencyKey** and **DateKey** values by using the alternate keys from **DimCurrency** and **DimDate** dimension tables.</span></span>  
  
|<span data-ttu-id="ae3ad-147">フラット ファイルの列</span><span class="sxs-lookup"><span data-stu-id="ae3ad-147">Flat File Column</span></span>|<span data-ttu-id="ae3ad-148">テーブル名</span><span class="sxs-lookup"><span data-stu-id="ae3ad-148">Table Name</span></span>|<span data-ttu-id="ae3ad-149">列名</span><span class="sxs-lookup"><span data-stu-id="ae3ad-149">Column Name</span></span>|<span data-ttu-id="ae3ad-150">データ型</span><span class="sxs-lookup"><span data-stu-id="ae3ad-150">Data Type</span></span>|  
|----------------------|----------------|-----------------|---------------|  
|<span data-ttu-id="ae3ad-151">0</span><span class="sxs-lookup"><span data-stu-id="ae3ad-151">0</span></span>|<span data-ttu-id="ae3ad-152">AdventureWorksDW2012</span><span class="sxs-lookup"><span data-stu-id="ae3ad-152">FactCurrency</span></span>|<span data-ttu-id="ae3ad-153">AverageRate</span><span class="sxs-lookup"><span data-stu-id="ae3ad-153">AverageRate</span></span>|<span data-ttu-id="ae3ad-154">float</span><span class="sxs-lookup"><span data-stu-id="ae3ad-154">float</span></span>|  
|<span data-ttu-id="ae3ad-155">1</span><span class="sxs-lookup"><span data-stu-id="ae3ad-155">1</span></span>|<span data-ttu-id="ae3ad-156">DimCurrency</span><span class="sxs-lookup"><span data-stu-id="ae3ad-156">DimCurrency</span></span>|<span data-ttu-id="ae3ad-157">CurrencyAlternateKey</span><span class="sxs-lookup"><span data-stu-id="ae3ad-157">CurrencyAlternateKey</span></span>|<span data-ttu-id="ae3ad-158">nchar (3)</span><span class="sxs-lookup"><span data-stu-id="ae3ad-158">nchar (3)</span></span>|  
|<span data-ttu-id="ae3ad-159">2</span><span class="sxs-lookup"><span data-stu-id="ae3ad-159">2</span></span>|<span data-ttu-id="ae3ad-160">DimDate</span><span class="sxs-lookup"><span data-stu-id="ae3ad-160">DimDate</span></span>|<span data-ttu-id="ae3ad-161">FullDateAlternateKey</span><span class="sxs-lookup"><span data-stu-id="ae3ad-161">FullDateAlternateKey</span></span>|<span data-ttu-id="ae3ad-162">date</span><span class="sxs-lookup"><span data-stu-id="ae3ad-162">date</span></span>|  
|<span data-ttu-id="ae3ad-163">3</span><span class="sxs-lookup"><span data-stu-id="ae3ad-163">3</span></span>|<span data-ttu-id="ae3ad-164">AdventureWorksDW2012</span><span class="sxs-lookup"><span data-stu-id="ae3ad-164">FactCurrency</span></span>|<span data-ttu-id="ae3ad-165">EndOfDayRate</span><span class="sxs-lookup"><span data-stu-id="ae3ad-165">EndOfDayRate</span></span>|<span data-ttu-id="ae3ad-166">float</span><span class="sxs-lookup"><span data-stu-id="ae3ad-166">float</span></span>|  
  
## <a name="lesson-tasks"></a><span data-ttu-id="ae3ad-167">このレッスンの作業</span><span class="sxs-lookup"><span data-stu-id="ae3ad-167">Lesson Tasks</span></span>  
 <span data-ttu-id="ae3ad-168">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ae3ad-168">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="ae3ad-169">手順 1:新しい Integration Services プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="ae3ad-169">Step 1: Creating a New Integration Services Project</span></span>](lesson-1-1-creating-a-new-integration-services-project.md)  
  
-   [<span data-ttu-id="ae3ad-170">手順 2:フラット ファイル接続マネージャーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="ae3ad-170">Step 2: Adding and Configuring a Flat File Connection Manager</span></span>](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
-   [<span data-ttu-id="ae3ad-171">手順 3:OLE DB 接続マネージャーの追加と構成</span><span class="sxs-lookup"><span data-stu-id="ae3ad-171">Step 3: Adding and Configuring an OLE DB Connection Manager</span></span>](lesson-1-3-adding-and-configuring-an-ole-db-connection-manager.md)  
  
-   [<span data-ttu-id="ae3ad-172">手順 4:パッケージへのデータ フロー タスクの追加</span><span class="sxs-lookup"><span data-stu-id="ae3ad-172">Step 4: Adding a Data Flow Task to the Package</span></span>](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
-   [<span data-ttu-id="ae3ad-173">手順 5:フラット ファイル ソースの追加と構成</span><span class="sxs-lookup"><span data-stu-id="ae3ad-173">Step 5: Adding and Configuring the Flat File Source</span></span>](lesson-1-5-adding-and-configuring-the-flat-file-source.md)  
  
-   [<span data-ttu-id="ae3ad-174">手順 6:参照変換の追加と構成</span><span class="sxs-lookup"><span data-stu-id="ae3ad-174">Step 6: Adding and Configuring the Lookup Transformations</span></span>](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
-   [<span data-ttu-id="ae3ad-175">手順 7:OLE DB 変換先の追加と構成</span><span class="sxs-lookup"><span data-stu-id="ae3ad-175">Step 7: Adding and Configuring the OLE DB Destination</span></span>](lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
-   [<span data-ttu-id="ae3ad-176">手順 8:レッスン 1 のパッケージをわかりやすくする作業</span><span class="sxs-lookup"><span data-stu-id="ae3ad-176">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>](lesson-1-8-making-the-lesson-1-package-easier-to-understand.md)  
  
-   [<span data-ttu-id="ae3ad-177">手順 9:レッスン 1 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="ae3ad-177">Step 9: Testing the Lesson 1 Tutorial Package</span></span>](lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
## <a name="start-the-lesson"></a><span data-ttu-id="ae3ad-178">レッスンの開始</span><span class="sxs-lookup"><span data-stu-id="ae3ad-178">Start the Lesson</span></span>  
 [<span data-ttu-id="ae3ad-179">手順 1:新しい Integration Services プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="ae3ad-179">Step 1: Creating a New Integration Services Project</span></span>](lesson-1-1-creating-a-new-integration-services-project.md)  
  
  
