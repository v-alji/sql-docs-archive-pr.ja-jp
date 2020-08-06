---
title: SQL Server データ ツールでのパッケージの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 330e0271421dc620f7c4fad9c6944331ebe94881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639569"
---
# <a name="create-packages-in-sql-server-data-tools"></a><span data-ttu-id="18b59-102">SQL Server データ ツールでのパッケージの作成</span><span class="sxs-lookup"><span data-stu-id="18b59-102">Create Packages in SQL Server Data Tools</span></span>
  <span data-ttu-id="18b59-103">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] デザイナーを使用して [!INCLUDE[ssIS](../includes/ssis-md.md)] で作成したパッケージは、ファイル システムに保存されます。</span><span class="sxs-lookup"><span data-stu-id="18b59-103">The packages that you create in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer are saved to the file system.</span></span> <span data-ttu-id="18b59-104">パッケージを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] またはパッケージ ストアに保存するには、パッケージのコピーを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18b59-104">To save a package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] or to the package store, you need to save a copy of the package.</span></span> <span data-ttu-id="18b59-105">詳細については、「 [パッケージのコピーを保存する](../../2014/integration-services/save-a-copy-of-a-package.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18b59-105">For more information, see [Save a Copy of a Package](../../2014/integration-services/save-a-copy-of-a-package.md).</span></span>  
  
 <span data-ttu-id="18b59-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で新しいパッケージを作成するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="18b59-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you can create a new package by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="18b59-107">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に含まれるパッケージ テンプレートを使用する。</span><span class="sxs-lookup"><span data-stu-id="18b59-107">Use the package template that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] includes.</span></span>  
  
-   <span data-ttu-id="18b59-108">カスタム テンプレートを使用する</span><span class="sxs-lookup"><span data-stu-id="18b59-108">Use a custom template</span></span>  
  
     <span data-ttu-id="18b59-109">新しいパッケージを作成するためのテンプレートとしてカスタム パッケージを使用する操作は簡単で、カスタム パッケージを DataTransformationItems フォルダーにコピーするだけです。</span><span class="sxs-lookup"><span data-stu-id="18b59-109">To use custom packages as templates for creating new packages, you simply copy them to the DataTransformationItems folder.</span></span> <span data-ttu-id="18b59-110">既定では、このフォルダーは、C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject にあります。</span><span class="sxs-lookup"><span data-stu-id="18b59-110">By default, this folder is in C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject.</span></span>  
  
-   <span data-ttu-id="18b59-111">既存のパッケージをコピーする。</span><span class="sxs-lookup"><span data-stu-id="18b59-111">Copy an existing package.</span></span>  
  
     <span data-ttu-id="18b59-112">再利用できる機能が既存のパッケージにある場合、既存のパッケージのオブジェクトをコピーして貼り付けることにより、新しいパッケージの制御フローとデータ フローをより短時間で構築できます。</span><span class="sxs-lookup"><span data-stu-id="18b59-112">If existing packages include functionality that you want to reuse, you can build the control flow and data flows in the new package more quickly by copying and pasting objects from other packages.</span></span> <span data-ttu-id="18b59-113">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトでコピーと貼り付けを使用する方法の詳細については、「 [パッケージ オブジェクトの再利用](reuse-of-package-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18b59-113">For more information about using copy and paste in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, see [Reuse of Package Objects](reuse-of-package-objects.md).</span></span>  
  
     <span data-ttu-id="18b59-114">新しいパッケージを作成する場合に、既存のパッケージをコピーするか、カスタム パッケージをテンプレートとして使用すると、既存のパッケージの名前と GUID もコピーされます。</span><span class="sxs-lookup"><span data-stu-id="18b59-114">If you create a new package by copying an existing package or by using a custom package as a template, the name and the GUID of the existing package are copied as well.</span></span> <span data-ttu-id="18b59-115">新しいパッケージの名前と GUID は、コピー元のパッケージと区別できるように更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18b59-115">You should update the name and the GUID of the new package to help differentiate it from the package from which it was copied.</span></span> <span data-ttu-id="18b59-116">たとえば、複数のパッケージに同じ GUID が使用されると、ログ データが所属するパッケージを特定することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="18b59-116">For example, if packages have the same GUID, it is more difficult to identify the package to which log data belongs.</span></span> <span data-ttu-id="18b59-117">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のプロパティ ウィンドウを使用することにより、`ID` プロパティの GUID を再生成して、`Name` プロパティの値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="18b59-117">You can regenerate the GUID in the `ID` property and update the value of the `Name` property by using the Properties window in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="18b59-118">詳細については、「 [パッケージのプロパティを設定する](set-package-properties.md) 」と「 [dtutil ユーティリティ](dtutil-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18b59-118">For more information, see [Set Package Properties](set-package-properties.md) and [dtutil Utility](dtutil-utility.md).</span></span>  
  
-   <span data-ttu-id="18b59-119">テンプレートとして指定したカスタム パッケージを使用する。</span><span class="sxs-lookup"><span data-stu-id="18b59-119">Use a custom package that you have designated as a template.</span></span>  
  
-   <span data-ttu-id="18b59-120">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを実行します。</span><span class="sxs-lookup"><span data-stu-id="18b59-120">Run the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard</span></span>  
  
     <span data-ttu-id="18b59-121">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードは、簡単なインポートまたはエクスポートに使用できる完成したパッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="18b59-121">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import and Export Wizard creates a complete package for a simple import or export.</span></span> <span data-ttu-id="18b59-122">このウィザードでは、インポートまたはエクスポートをすぐに実行できるように、接続、変換元、および変換先が構成され、必要なすべてのデータ変換が追加されます。</span><span class="sxs-lookup"><span data-stu-id="18b59-122">This wizard configures the connections, source, and destination, and adds any data transformations that are required to let you run the import or export immediately.</span></span> <span data-ttu-id="18b59-123">パッケージを後で再び実行したり [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]でパッケージを改良、強化するために、パッケージを保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="18b59-123">You can optionally save the package to run it again later, or to refine and enhance the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="18b59-124">ただし、パッケージを保存する場合は、パッケージを変更したり、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でパッケージを実行したりする前に、既存の [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]プロジェクトにパッケージを追加しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="18b59-124">However, if you save the package, you must add the package to an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project before you can change the package or run the package in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
 <span data-ttu-id="18b59-125">次の手順では、[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] のパッケージを作成または削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="18b59-125">The following procedures describe how to create or delete a package in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="18b59-126">既定のパッケージ テンプレートを使用して基本的なパッケージを作成する方法のデモ ビデオについては、「 [基本パッケージの作成 (SQL Server ビデオ)](https://go.microsoft.com/fwlink/?LinkId=131023)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18b59-126">For a video that demonstrates how to create a basic package using the default package template, see [Creating a Basic Package (SQL Server Video)](https://go.microsoft.com/fwlink/?LinkId=131023).</span></span>  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a><span data-ttu-id="18b59-127">パッケージ テンプレートを使用して SQL Server データ ツールでパッケージを作成するには</span><span class="sxs-lookup"><span data-stu-id="18b59-127">To create a package in SQL Server Data Tools using the Package Template</span></span>  
  
1.  <span data-ttu-id="18b59-128">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、パッケージを作成する [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="18b59-128">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in which you want to create a package.</span></span>  
  
2.  <span data-ttu-id="18b59-129">ソリューション エクスプローラーで、 **[SSIS パッケージ]** フォルダーを右クリックし、 **[新しい SSIS パッケージ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18b59-129">In Solution Explorer, right-click the **SSIS Packages** folder, and then click **New SSIS Package**.</span></span>  
  
3.  <span data-ttu-id="18b59-130">必要に応じて、制御フロー、データ フロー タスク、およびイベント ハンドラーをパッケージに追加します。</span><span class="sxs-lookup"><span data-stu-id="18b59-130">Optionally, add control flow, data flow tasks, and event handlers to the package.</span></span> <span data-ttu-id="18b59-131">詳細については、「[制御フロー](control-flow/control-flow.md)」、「[データ フロー](data-flow/data-flow.md)」、および「[Integration Services &#40;SSIS&#41; のイベント ハンドラー](integration-services-ssis-event-handlers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18b59-131">For more information, see [Control Flow](control-flow/control-flow.md), [Data Flow](data-flow/data-flow.md), and [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md).</span></span>  
  
4.  <span data-ttu-id="18b59-132">**[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックし、新しいパッケージを保存します。</span><span class="sxs-lookup"><span data-stu-id="18b59-132">On the **File** menu, click **Save Selected Items** to save the new package.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="18b59-133">空のパッケージも保存できます。</span><span class="sxs-lookup"><span data-stu-id="18b59-133">You can save an empty package.</span></span>  
  
  
