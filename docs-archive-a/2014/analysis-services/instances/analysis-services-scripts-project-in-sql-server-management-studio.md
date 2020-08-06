---
title: SQL Server Management Studio | の Analysis Services Scripts プロジェクトMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [Analysis Services]
- scripts [Analysis Services], projects
- projects [Analysis Services], Analysis Server Scripts project
- projects [Analysis Services], creating
- Analysis Server Scripts project
- items [Analysis Services]
ms.assetid: c4f5a06b-e2e4-4660-a3a8-6fd356742c02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3dc10280e2ee957cd2245bb6a4993d7dcf536680
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641361"
---
# <a name="analysis-services-scripts-project-in-sql-server-management-studio"></a><span data-ttu-id="f0856-102">SQL Server Management Studio での Analysis Services スクリプト プロジェクト</span><span class="sxs-lookup"><span data-stu-id="f0856-102">Analysis Services Scripts Project in SQL Server Management Studio</span></span>
  <span data-ttu-id="f0856-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] に Analysis Services スクリプト プロジェクトを作成し、開発、管理、およびソース管理の目的のために、関連するスクリプトをグループにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="f0856-103">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can create an Analysis Server Scripts project in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to group related scripts together for development, management, and source control purposes.</span></span> <span data-ttu-id="f0856-104">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に読み込まれているソリューションがない場合は、新しい Analysis Services スクリプト プロジェクトを作成すると自動的に新しいソリューションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f0856-104">If no solution is currently loaded in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], creating a new Analysis Server Scripts project automatically creates a new solution.</span></span> <span data-ttu-id="f0856-105">ソリューションが SQL Server Management Studio に読み込まれている場合は、既存のソリューションに新しい Analysis Services スクリプト プロジェクトを追加するか、または新しいソリューションで Analysis Services スクリプト プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f0856-105">Otherwise, the new Analysis Server Scripts project can be added to the existing solution or created in a new solution.</span></span>  
  
 <span data-ttu-id="f0856-106">次の基本的な手順を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で Analysis Services スクリプト プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f0856-106">You use the following basic steps to create an Analysis Server Scripts project in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:</span></span>  
  
1.  <span data-ttu-id="f0856-107">[ファイル] メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f0856-107">On the File menu, point to **New**, and then click **Project**.</span></span>  
  
     <span data-ttu-id="f0856-108">**[Analysis Services スクリプト]** プロジェクト テンプレートをクリックし、新しいプロジェクトの名前と場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0856-108">Select **Analysis Server Scripts** project template and then specify a name and location for the new project.</span></span>  
  
2.  <span data-ttu-id="f0856-109">**[接続]** を右クリックし、ソリューション エクスプローラーの Analysis Services スクリプト プロジェクトの [接続] フォルダーに新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="f0856-109">Right-click **Connections** to create a new connection in the Connections folder of the Analysis Server Scripts project in Solution Explorer.</span></span>  
  
     <span data-ttu-id="f0856-110">このフォルダーには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスへの接続文字列が含まれます。このインスタンスに対して Analysis Services スクリプト プロジェクトに含まれるスクリプトを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f0856-110">This folder contains connection strings to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instances, against which the scripts contained by the Analysis Server Scripts project can be executed.</span></span> <span data-ttu-id="f0856-111">Analysis Services スクリプト プロジェクトには複数の接続を含めることができ、プロジェクトに含まれているスクリプトをどの接続に対して実行するかを実行時に選択できます。</span><span class="sxs-lookup"><span data-stu-id="f0856-111">You can have multiple connections in an Analysis Server Scripts project, and you can choose a connection against which to run a script contained by the project at the time of execution.</span></span>  
  
3.  <span data-ttu-id="f0856-112">**[クエリ]** を右クリックし、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、および XML for Analysis (XMLA) スクリプトを、ソリューション エクスプローラーの Analysis Services スクリプト プロジェクトの [スクリプト] フォルダーに作成します。</span><span class="sxs-lookup"><span data-stu-id="f0856-112">Right-click **Queries** to create Multidimensional Expressions (MDX), Data Mining Extensions (DMX), and XML for Analysis (XMLA) scripts in the Scripts folder of the Analysis Server Scripts project in Solution Explorer.</span></span> <span data-ttu-id="f0856-113">詳細については、「 [Analysis Services の管理タスクのスクリプト作成](../script-administrative-tasks-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0856-113">For more information, see [Script Administrative Tasks in Analysis Services](../script-administrative-tasks-in-analysis-services.md).</span></span>  
  
4.  <span data-ttu-id="f0856-114">プロジェクトを右クリックし、 **[追加]** をポイントします。次に、 **[既存の項目]** をクリックしてプロジェクトの注釈が書かれているテキスト ファイルなどのその他のファイルを、ソリューション エクスプローラーの Analysis Services スクリプト プロジェクトの **[その他]** フォルダーに追加します。</span><span class="sxs-lookup"><span data-stu-id="f0856-114">Right-click on the project, point to **Add**, and then select **Existing Item** to add miscellaneous files, such as text files that contain notes on the project, in the **Miscellaneous** folder of the Analysis Server Scripts project in Solution Explorer.</span></span> <span data-ttu-id="f0856-115">これらのファイルは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では無視されます。</span><span class="sxs-lookup"><span data-stu-id="f0856-115">These files are ignored by [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="file-types"></a><span data-ttu-id="f0856-116">ファイルの種類</span><span class="sxs-lookup"><span data-stu-id="f0856-116">File Types</span></span>  
 <span data-ttu-id="f0856-117">1 つの [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ソリューションで、複数のファイルの種類を使用できます。ファイルの種類は、ソリューションに含まれるプロジェクトおよびそのソリューションの各プロジェクトに含まれるアイテムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f0856-117">A [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution can contain several file types, depending on what projects you included in the solution and what items you included in each project for that solution.</span></span> <span data-ttu-id="f0856-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でのソリューション用のファイルの種類については、「 [ソリューションとプロジェクトを管理するためのファイル](../../ssms/solution/files-that-manage-solutions-and-projects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0856-118">For more information about file types for solutions in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], see [Files That Manage Solutions and Projects](../../ssms/solution/files-that-manage-solutions-and-projects.md).</span></span> <span data-ttu-id="f0856-119">通常、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ソリューションの各プロジェクトのファイルは、ソリューションのフォルダー内でプロジェクト別に異なるフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="f0856-119">Typically, the files for each project in a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] solution are stored in the solution folder, in a separate folder for each project.</span></span>  
  
 <span data-ttu-id="f0856-120">Analysis Services スクリプト プロジェクトのプロジェクト フォルダーには、次の表に示す種類のファイルを格納できます。</span><span class="sxs-lookup"><span data-stu-id="f0856-120">The project folder for an Analysis Server Scripts project can contain the file types listed in the following table.</span></span>  
  
|<span data-ttu-id="f0856-121">ファイルの種類</span><span class="sxs-lookup"><span data-stu-id="f0856-121">File type</span></span>|<span data-ttu-id="f0856-122">説明</span><span class="sxs-lookup"><span data-stu-id="f0856-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0856-123">Analysis Services スクリプト プロジェクト定義ファイル (.ssmsasproj)</span><span class="sxs-lookup"><span data-stu-id="f0856-123">Analysis Server Scripts project definition file (.ssmsasproj)</span></span>|<span data-ttu-id="f0856-124">ソリューション エクスプローラーに表示されるフォルダーに関するメタデータ、およびプロジェクトに含まれるファイルをどのフォルダーが表示するかを示す情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f0856-124">Contains metadata about the folders shown in Solution Explorer, as well as information that indicates which folders should display files included in the project.</span></span><br /><br /> <span data-ttu-id="f0856-125">また、プロジェクトに含まれる [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続のメタデータ、およびプロジェクトに含まれるスクリプト ファイルに接続を関連付けるメタデータも含まれます。</span><span class="sxs-lookup"><span data-stu-id="f0856-125">The project definition file also contains the metadata for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connections contained in the project, as well as metadata that associates connections with script files included in the project.</span></span>|  
|<span data-ttu-id="f0856-126">DMX スクリプト ファイル (.dmx)</span><span class="sxs-lookup"><span data-stu-id="f0856-126">DMX script file (.dmx)</span></span>|<span data-ttu-id="f0856-127">プロジェクトに含まれている DMX スクリプトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f0856-127">Contains a DMX script included in the project.</span></span>|  
|<span data-ttu-id="f0856-128">MDX スクリプト ファイル (.mdx)</span><span class="sxs-lookup"><span data-stu-id="f0856-128">MDX script file (.mdx)</span></span>|<span data-ttu-id="f0856-129">プロジェクトに含まれている MDX スクリプトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f0856-129">Contains an MDX script included in the project.</span></span>|  
|<span data-ttu-id="f0856-130">XMLA スクリプト ファイル (.xmla)</span><span class="sxs-lookup"><span data-stu-id="f0856-130">XMLA script file (.xmla)</span></span>|<span data-ttu-id="f0856-131">プロジェクトに含まれている XMLA スクリプトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f0856-131">Contains an XMLA script included in the project.</span></span>|  
  
## <a name="analysis-services-templates"></a><span data-ttu-id="f0856-132">Analysis Services テンプレート</span><span class="sxs-lookup"><span data-stu-id="f0856-132">Analysis Services Templates</span></span>  
 <span data-ttu-id="f0856-133">新しい MDX、DMX、または XMLA スクリプトを Analysis Services スクリプト プロジェクトに追加する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] テンプレートの参照にテンプレート エクスプローラーを必要に応じて使用してください。このテンプレートは、具体的なアクションの実行方法を例示した事前定義済みのスクリプトまたはステートメントのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="f0856-133">When adding new MDX, DMX, or XMLA scripts to an Analysis Server Scripts project, you have the option of using Template Explorer to locate [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] templates, which are a collection of predefined scripts or statements that demonstrate how to perform a specified action.</span></span> <span data-ttu-id="f0856-134">テンプレートエクスプローラーは、[**表示**] メニューにあり、、、およびのテンプレートが含まれてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="f0856-134">Template Explorer is available on the **View** menu and includes templates for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and [!INCLUDE[ssEW](../../includes/ssew-md.md)].</span></span> <span data-ttu-id="f0856-135">詳細については、「 [SQL Server Management Studio での Analysis Services テンプレートの使用](use-analysis-services-templates-in-sql-server-management-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0856-135">For more information, see [Use Analysis Services Templates in SQL Server Management Studio](use-analysis-services-templates-in-sql-server-management-studio.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0856-136">参照</span><span class="sxs-lookup"><span data-stu-id="f0856-136">See Also</span></span>  
 <span data-ttu-id="f0856-137">[SQL Server Data Tools &#40;SSDT&#41;を使用した多次元モデルの作成](../multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="f0856-137">[Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;](../multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md) </span></span>  
 <span data-ttu-id="f0856-138">[MDX&#41; 参照 &#40;多次元式](/sql/mdx/multidimensional-expressions-mdx-reference) </span><span class="sxs-lookup"><span data-stu-id="f0856-138">[Multidimensional Expressions &#40;MDX&#41; Reference](/sql/mdx/multidimensional-expressions-mdx-reference) </span></span>  
 <span data-ttu-id="f0856-139">[DMX&#41; リファレンス &#40;データマイニング拡張機能](/sql/dmx/data-mining-extensions-dmx-reference) </span><span class="sxs-lookup"><span data-stu-id="f0856-139">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference) </span></span>  
 <span data-ttu-id="f0856-140">[Analysis Services スクリプト言語 &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span><span class="sxs-lookup"><span data-stu-id="f0856-140">[Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) </span></span>  
 [<span data-ttu-id="f0856-141">Analysis Services スクリプト言語 &#40;ASSL&#41; リファレンス</span><span class="sxs-lookup"><span data-stu-id="f0856-141">Analysis Services Scripting Language &#40;ASSL&#41; Reference</span></span>](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)  
  
  