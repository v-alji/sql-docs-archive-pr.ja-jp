---
title: Data Profile Viewer | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profile Viewer [Integration Services]
- Data Profiling task [Integration Services], output viewer
ms.assetid: b9043428-ce26-45bb-910c-588d07579565
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e82aae19525625d966bdd01334eca07a1c4c68f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641814"
---
# <a name="data-profile-viewer"></a><span data-ttu-id="1d367-102">Data Profile Viewer (Data Profile Viewer)</span><span class="sxs-lookup"><span data-stu-id="1d367-102">Data Profile Viewer</span></span>
  <span data-ttu-id="1d367-103">データのプロファイル処理では、次に、データ プロファイルを表示して分析します。</span><span class="sxs-lookup"><span data-stu-id="1d367-103">Viewing and analyzing the data profiles is the next step in the data profiling process.</span></span> <span data-ttu-id="1d367-104">このプロファイルは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージ内でデータ プロファイル タスクを実行してデータ プロファイルを計算した後に表示できます。</span><span class="sxs-lookup"><span data-stu-id="1d367-104">You can view these profiles after you have run the Data Profiling task inside an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package and computed the data profiles.</span></span> <span data-ttu-id="1d367-105">データ プロファイル タスクの設定方法および実行方法の詳細については、「 [データ プロファイル タスクのセットアップ](data-profiling-task.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d367-105">For more information about how to set up and run the Data Profiling tasks, see [Setup of the Data Profiling Task](data-profiling-task.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1d367-106">出力ファイルには、データベースに関する機密データやデータベースに格納されているデータが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1d367-106">The output file might contain sensitive data about your database and the data that database contains.</span></span> <span data-ttu-id="1d367-107">このファイルの安全性を高める方法の推奨事項については、「 [パッケージで使用されるファイルへのアクセス](../access-to-files-used-by-packages.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d367-107">For suggestions on how to make this file more secure, see [Access to Files Used by Packages](../access-to-files-used-by-packages.md).</span></span>  
  
## <a name="data-profiles"></a><span data-ttu-id="1d367-108">データのプロファイル</span><span class="sxs-lookup"><span data-stu-id="1d367-108">Data Profiles</span></span>  
 <span data-ttu-id="1d367-109">データ プロファイルを表示するには、出力をファイルに送信するようにデータ プロファイル タスクを構成し、スタンドアロンの Data Profile Viewer を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d367-109">To view the data profiles, you configure the Data Profiling task to send its output to a file, and then you use the stand-alone Data Profile Viewer.</span></span> <span data-ttu-id="1d367-110">Data Profile Viewer を開くには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="1d367-110">To open the Data Profile Viewer, do one of the following.</span></span>  
  
-   <span data-ttu-id="1d367-111">**デザイナーの** [データ プロファイル] [!INCLUDE[ssIS](../../includes/ssis-md.md)] でタスクを右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d367-111">Right-click the **Data Profiling** task in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, and then click **Edit**.</span></span> <span data-ttu-id="1d367-112">**データ プロファイル タスク エディター** の **[全般]** ページで、 **[プロファイル ビューアーを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1d367-112">Click **Open Profile Viewer** on the **General** page of the **Data Profiling Task Editor**.</span></span>  
  
-   <span data-ttu-id="1d367-113">*\<drive>* :\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn フォルダーの DataProfileViewer.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="1d367-113">In the folder, *\<drive>*:\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn, run DataProfileViewer.exe.</span></span>  
  
 <span data-ttu-id="1d367-114">このビューアーでは、複数のペインを使用して、要求したプロファイルと計算結果が表示されます。また、詳細情報を表示するための機能やドリル ダウン機能をオプションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="1d367-114">The viewer uses multiple panes to display the profiles that you requested and the computed results, with optional details and drilldown capability:</span></span>  
  
 <span data-ttu-id="1d367-115">**[プロファイル]** ペイン</span><span class="sxs-lookup"><span data-stu-id="1d367-115">**Profiles** pane</span></span>  
 <span data-ttu-id="1d367-116">**[プロファイル]** ペインには、データ プロファイル タスクで要求されたプロファイルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-116">The **Profiles** pane displays the profiles that were requested in the Data Profile task.</span></span> <span data-ttu-id="1d367-117">**[プロファイル]** ペインでプロファイルを選択すると、プロファイルの計算結果がビューアーの他のペインに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-117">To view the computed results for the profile, select the profile in the **Profiles** pane and the results will appear in the other panes of the viewer.</span></span>  
  
 <span data-ttu-id="1d367-118">**[結果]** ペイン</span><span class="sxs-lookup"><span data-stu-id="1d367-118">**Results** pane</span></span>  
 <span data-ttu-id="1d367-119">**[結果]** ペインでは、プロファイルの計算結果が 1 行にまとめられます。</span><span class="sxs-lookup"><span data-stu-id="1d367-119">The **Results** pane uses a single row to summarize the computed results of the profile.</span></span> <span data-ttu-id="1d367-120">たとえば、 **[列長分布プロファイル]** を要求すると、この行には最小長、最大長、および行数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-120">For example, if you request a **Column Length Distribution Profile**, this row includes the minimum and maximum length, and the row count.</span></span> <span data-ttu-id="1d367-121">ほとんどのプロファイルでは、 **[結果]** ペインでこの行を選択すると、オプションの **[詳細]** ペインに追加の詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="1d367-121">For most profiles, you can select this row in the **Results** pane to see additional detail in the optional **Details** pane.</span></span>  
  
 <span data-ttu-id="1d367-122">**[詳細]** ペイン</span><span class="sxs-lookup"><span data-stu-id="1d367-122">**Details** pane</span></span>  
 <span data-ttu-id="1d367-123">ほとんどの種類のプロファイルの **[詳細]** ペインには、 **[結果]** ペインで選択したプロファイルの結果に関する追加情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-123">For most profile types, the **Details** pane displays additional information about the profile results selected in the **Results** pane.</span></span> <span data-ttu-id="1d367-124">たとえば、 **[列長分布プロファイル]** を要求すると、 **[詳細]** ペインには検出された各列の長さが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-124">For example, if you request a **Column Length Distribution Profile**, the **Details** pane displays each column length that was found.</span></span> <span data-ttu-id="1d367-125">また、列の値の長さがこのペインに表示された列の長さである行の数および割合も表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-125">The pane also displays the number and percentage of rows in which the column value has that column length.</span></span>  
  
 <span data-ttu-id="1d367-126">複数の列に対して計算される 3 種類のプロファイル (候補キー、機能依存、および値包含) の **[詳細]** ペインには、想定されているリレーションシップの違反が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-126">For the three profile types that are computed against more than one column (Candidate Key, Functional Dependency, and Value Inclusion), the **Details** pane displays violations of the expected relationship.</span></span> <span data-ttu-id="1d367-127">たとえば、[候補キー プロファイル] を要求すると、[詳細] ペインには候補キーの一意性に違反している重複値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-127">For example, if you request a Candidate Key Profile, the Details pane displays duplicate values that violate the uniqueness of the candidate key.</span></span>  
  
 <span data-ttu-id="1d367-128">プロファイルの計算に使用したデータ ソースが使用可能な場合、 **[詳細]** ペインの行をダブルクリックすると、 **[ドリル ダウン]** ペインに、一致するデータ行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="1d367-128">If the data source that is used to compute the profile is available, you can double-click a row in the **Details** pane to see the matching rows of data in the **Drilldown** pane.</span></span>  
  
 <span data-ttu-id="1d367-129">**[ドリル ダウン]** ペイン</span><span class="sxs-lookup"><span data-stu-id="1d367-129">**Drilldown** pane</span></span>  
 <span data-ttu-id="1d367-130">次の条件に当てはまる場合、 **[詳細]** ペインの行をダブルクリックすると、 **[ドリル ダウン]** ペインに、一致するデータ行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="1d367-130">You can double-click a row in the **Details** pane to see the matching rows of data in the **Drilldown** pane when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="1d367-131">計算に使用したデータ ソースが利用可能であること。</span><span class="sxs-lookup"><span data-stu-id="1d367-131">The data source that is used to compute the profile is available.</span></span>  
  
-   <span data-ttu-id="1d367-132">データを表示する権限があること。</span><span class="sxs-lookup"><span data-stu-id="1d367-132">You have permission to view the data.</span></span>  
  
 <span data-ttu-id="1d367-133">Data Profile Viewer では、ドリル ダウン要求のためのソース データベースへの接続に、Windows 認証と現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d367-133">To connect to the source database for a drilldown request, the Data Profile Viewer uses Windows Authentication and the credentials of the current user.</span></span> <span data-ttu-id="1d367-134">データ プロファイル タスクを実行したパッケージに格納されている接続情報は使用されません。</span><span class="sxs-lookup"><span data-stu-id="1d367-134">The Data Profile Viewer does not use the connection information that is stored in the package that ran the Data Profiling task.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="1d367-135">Data Profile Viewer に用意されているドリル ダウン機能は、元のデータ ソースにライブ クエリを送信します。</span><span class="sxs-lookup"><span data-stu-id="1d367-135">The drilldown capability that is available in the Data Profile Viewer sends live queries to the original data source.</span></span> <span data-ttu-id="1d367-136">これらのクエリは、サーバーのパフォーマンスに悪影響を及ぼす場合があります。</span><span class="sxs-lookup"><span data-stu-id="1d367-136">These queries may have a negative impact on the performance of the server.</span></span>  
>   
>  <span data-ttu-id="1d367-137">最近作成されたものではない出力ファイルからドリル ダウンした場合、ドリルダウン クエリは、元の出力の計算に使用された行セットとは異なる行セットを返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="1d367-137">If you drill down from an output file that was not created recently, the drilldown queries might return a different set of rows than those on which the original output was calculated.</span></span>  
  
 <span data-ttu-id="1d367-138">Data Profile Viewer のユーザー インターフェイスの詳細については、「 [Data Profile Viewer の F1 ヘルプ](../data-profile-viewer-f1-help.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d367-138">For more information about the user interface of the Data Profile Viewer, see [Data Profile Viewer F1 Help](../data-profile-viewer-f1-help.md).</span></span>  
  
  
