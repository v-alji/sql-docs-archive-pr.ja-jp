---
title: Management Studio | で Analysis Services スクリプトを作成するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services objects, scripts
- objects [Analysis Services], scripts
- scripts [Analysis Services], objects
ms.assetid: 4f1b965c-9ca6-427b-8f4d-0ce1eea7c0fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: bb380e271510ea5a35860d4850bfaeed3aad8cf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714762"
---
# <a name="create-analysis-services-scripts-in-management-studio"></a><span data-ttu-id="aedd8-102">Management Studio での Analysis Services スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="aedd8-102">Create Analysis Services Scripts in Management Studio</span></span>
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="aedd8-103">には、スクリプトの生成機能、テンプレート、および Analysis Services オブジェクトとタスクのスクリプトを作成するために使用できるエディターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aedd8-103">includes script generation features, templates, and editors that you can use to script Analysis Services objects and tasks.</span></span>  
  
## <a name="script-analysis-services-tasks-in-management-studio"></a><span data-ttu-id="aedd8-104">Management Studio で Analysis Services タスクのスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="aedd8-104">Script Analysis Services Tasks in Management Studio</span></span>  
 <span data-ttu-id="aedd8-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のタスクのスクリプト作成は、タスク指向のダイアログ ボックスで、いずれかのスクリプト オプションをクリックすることで実現します。</span><span class="sxs-lookup"><span data-stu-id="aedd8-105">Scripting tasks in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by clicking one of the Script options in a task-oriented dialog box.</span></span> <span data-ttu-id="aedd8-106">バックアップやデータベースの復元、オブジェクトの処理、集計のデザインなどのタスクを実行するために使用するすべてのダイアログ ボックスには、ダイアログ ボックスの上部にスクリプト オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="aedd8-106">All of the dialog boxes that you use to perform tasks such as backup or restore database, process an object, or design an aggregation, include a Script option at the top of the dialog box.</span></span> <span data-ttu-id="aedd8-107">これらのオプションのいずれかを選択すると、ダイアログ ボックス内の情報と設定に基づいて、XMLA スクリプトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-107">Selecting one of these options generates an XMLA script based on the information and settings in the dialog box.</span></span>  
  
 <span data-ttu-id="aedd8-108">既定では、スクリプトが生成され、XMLA クエリ エディター内に配置されますが、スクリプト オプション リストを拡張して、Windows クリップボードやファイルにスクリプトを出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-108">By default, the script is generated and placed in an XMLA query editor, but you can also expand the Script option list to direct the script to the Windows Clipboard or a file.</span></span>  
  
#### <a name="to-script-an-analysis-services-task"></a><span data-ttu-id="aedd8-109">Analysis Services タスクのスクリプトを作成するには</span><span class="sxs-lookup"><span data-stu-id="aedd8-109">To script an Analysis Services task</span></span>  
  
1.  <span data-ttu-id="aedd8-110">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="aedd8-110">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="aedd8-111">データベースを右クリックし、 **[バックアップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aedd8-111">Right-click a database and click **Backup**.</span></span> <span data-ttu-id="aedd8-112">[データベースのバックアップ] ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-112">This opens the Backup Database dialog box.</span></span> <span data-ttu-id="aedd8-113">バックアップのファイル名を指定し、このバックアップに必要なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="aedd8-113">Specify a backup file name and choose the options you want for this backup.</span></span>  
  
3.  <span data-ttu-id="aedd8-114">ダイアログ ボックスの上部にある **[スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aedd8-114">Click **Script** at the top of the dialog box.</span></span> <span data-ttu-id="aedd8-115">スクリプト機能は、Management Studio 内のすべてのタスク ベースのダイアログ ボックスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="aedd8-115">The Script feature is part of all task-based dialog boxes in Management Studio.</span></span> <span data-ttu-id="aedd8-116">これには、次のオプションがあります。 **[スクリプト操作を新規クエリ ウィンドウに保存]** は、クエリ エディター ウィンドウを開き、 **[スクリプト操作をファイルに保存]** は、XMLA スクリプトをファイルに保存し、 **[スクリプト操作をクリップボードに保存]** は、XMLA スクリプトをクリップボードに保存します。</span><span class="sxs-lookup"><span data-stu-id="aedd8-116">It has the following options: **Script Action to New Query Window** to open the query editor window, **Script Action to File** to save the XMLA script to a file, or **Script Action to Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
     <span data-ttu-id="aedd8-117">Management Studio でスクリプト オプションとして表示される **[スクリプト操作をジョブに保存]** オプションは、Analysis Services スクリプトではサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aedd8-117">Note that the **Script Action to Job** option that is listed as a script option in Management Studio is not supported for Analysis Services scripts.</span></span>  
  
4.  <span data-ttu-id="aedd8-118">既定のオプションである **[スクリプト操作を新規クエリ ウィンドウに保存]** を選択すると、生成されたスクリプトは、XMLA クエリ ウィンドウに配置されます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-118">If you select the default option, **Script Action to New Query Window**, a generated script is placed in an XMLA query window.</span></span>  
  
     <span data-ttu-id="aedd8-119">[データベースのバックアップ] ダイアログ ボックスを閉じて、XMLA スクリプトを直接、編集または実行できます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-119">You can now close the Backup Database dialog box and edit or run the XMLA script directly.</span></span>  
  
## <a name="script-analysis-services-objects-in-management-studio"></a><span data-ttu-id="aedd8-120">Management Studio で Analysis Services オブジェクトのスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="aedd8-120">Script Analysis Services Objects in Management Studio</span></span>  
 <span data-ttu-id="aedd8-121">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクトを右クリックし、 **[CREATE]**、 **[ALTER]**、または **[DELETE]** を選択して、オブジェクトのスクリプト作成を実行します。</span><span class="sxs-lookup"><span data-stu-id="aedd8-121">Scripting objects in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is accomplished by right-clicking an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and selecting either **Create to**, **Alter to**, or **Delete to**.</span></span> <span data-ttu-id="aedd8-122">これらの各オプションは、ウィンドウまたはファイルに出力できますが、スクリプトの出力先に関係なく、XMLA ラッパーの DDL スクリプトの形式で出力されます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-122">Each of these options can be directed to a window or a file, but regardless of where the script is directed to, it will come in the form of a DDL script in an XMLA wrapper.</span></span> <span data-ttu-id="aedd8-123">このようなスクリプトは、指定するどのサーバーに対しても実行できるという大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="aedd8-123">One great advantage to such scripts is that they can be run against any server you point them at.</span></span> <span data-ttu-id="aedd8-124">また、スクリプトの名前は変更可能で、オブジェクトの大量作成、変更、または削除を反復的に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-124">Also, names in the scripts can be changed and run on an iterative basis for mass construction, alteration, or deletion of objects.</span></span>  
  
 <span data-ttu-id="aedd8-125">スクリプトを作成できるオブジェクトには、データ ソース、データ ソース ビュー、キューブ、ディメンション、マイニング構造、およびロールを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-125">Objects that you can script include the elements of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, including data sources, data source views, cubes, dimensions, mining structures, and roles.</span></span>  
  
 <span data-ttu-id="aedd8-126">前提条件として XML for Analysis (XMLA) を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="aedd8-126">Prerequisites include an understanding of XML for Analysis (XMLA).</span></span> <span data-ttu-id="aedd8-127">しかし、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] には、キューブなどのオブジェクトの作成に必要な XMLA スクリプトを自動的に作成する機能があります。</span><span class="sxs-lookup"><span data-stu-id="aedd8-127">Fortunately, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] has a feature that automatically creates the XMLA script required to create objects, such as cubes.</span></span> <span data-ttu-id="aedd8-128">この自動化機能により、XMLA の習得の必要性が緩和されます。</span><span class="sxs-lookup"><span data-stu-id="aedd8-128">This automation feature helps reduce the learning curve for XMLA.</span></span> <span data-ttu-id="aedd8-129">XMLA の使用方法の詳細については、「 [Analysis Services での XMLA による開発](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aedd8-129">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span> <span data-ttu-id="aedd8-130">XMLA の使用方法の詳細については、「 [Analysis Services での XMLA による開発](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aedd8-130">For more information about how to use XMLA, see [Developing with XMLA in Analysis Services](../multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="aedd8-131">Role オブジェクトのスクリプトを作成する場合、セキュリティ権限はオブジェクトが関連付けられているセキュリティ ロールではなく、オブジェクト自体に含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aedd8-131">When scripting the Role Object, be aware that security permissions are contained by the objects they secure rather than with the security role with which they are associated.</span></span>  
  
#### <a name="to-script-analysis-services-objects"></a><span data-ttu-id="aedd8-132">Analysis Services オブジェクトのスクリプトを作成するには</span><span class="sxs-lookup"><span data-stu-id="aedd8-132">To script Analysis Services objects</span></span>  
  
1.  <span data-ttu-id="aedd8-133">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="aedd8-133">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="aedd8-134">オブジェクトの作成、変更、削除のいずれかを行うスクリプトを作成するオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="aedd8-134">Locate the object for which you want to create a script that either creates, alters, or deletes objects.</span></span>  
  
3.  <span data-ttu-id="aedd8-135">オブジェクトを右クリックし、 **[キューブをスクリプト化]** をポイントしてから、 **[CREATE]**、 **[ALTER]**、 **[DELETE]** のいずれかをポイントし、クエリ エディター ウィンドウを開くには **[新しいクエリ エディター ウィンドウ]** を、XMLA スクリプトをファイルに保存するには **[ファイル]** を、XMLA スクリプトをクリップボードに保存するには **[クリップボード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aedd8-135">Right-click the object, point to **Script Cube as**, point to **CREATE To**, **ALTER To**, or **Delete To**, and then click one of the following options: **New Query Editor Window** to open the query editor window, **File** to save the XMLA script to a file, or **Clipboard** to save the XMLA script to the Clipboard.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="aedd8-136">通常、複数の異なるバージョンのファイルを作成する場合は、 **[ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="aedd8-136">Typically, you would select **File** if you want to create multiple different versions of the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedd8-137">参照</span><span class="sxs-lookup"><span data-stu-id="aedd8-137">See Also</span></span>  
 <span data-ttu-id="aedd8-138">[Analysis Services での管理タスクのスクリプト作成](../script-administrative-tasks-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="aedd8-138">[Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="aedd8-139">XMLA クエリ エディター (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="aedd8-139">XMLA Query Editor &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../xmla-query-editor-analysis-services-multidimensional-data.md)  
  
  
