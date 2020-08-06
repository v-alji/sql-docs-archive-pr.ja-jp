---
title: 方法:カスタム アセンブリをデバッグする | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b5f9f5a4595d59cce98da4f753422cd07529926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717534"
---
# <a name="how-to-debug-custom-assemblies"></a><span data-ttu-id="a26b9-102">方法:カスタム アセンブリをデバッグする</span><span class="sxs-lookup"><span data-stu-id="a26b9-102">How to: Debug Custom Assemblies</span></span>
  <span data-ttu-id="a26b9-103">には、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] カスタムアセンブリコードを分析してエラーを見つけるのに役立つ、いくつかのデバッグツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a26b9-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides several debugging tools that can help you analyze your custom assembly code and locate errors in it.</span></span> <span data-ttu-id="a26b9-104">どのツールが最適であるかは、何を実行するかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a26b9-104">The best tool to use will depend on what you are trying to accomplish.</span></span> <span data-ttu-id="a26b9-105">この例では、[!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-105">This example uses [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)].</span></span>  
  
 <span data-ttu-id="a26b9-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のカスタム アセンブリの設計、開発、およびテストに関して推奨する方法は、テスト レポートおよびカスタム アセンブリを含むソリューションを作成することです。</span><span class="sxs-lookup"><span data-stu-id="a26b9-106">The recommended way to design, develop, and test custom assemblies for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is to create a solution that contains both your test reports and your custom assembly.</span></span>  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a><span data-ttu-id="a26b9-107">Visual Studio の 1 つのインスタンスを使用してアセンブリをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="a26b9-107">To debug assemblies using a single instance of Visual Studio</span></span>  
  
1.  <span data-ttu-id="a26b9-108">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を使用して新しいレポート プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-108">Create a new report project using [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
     <span data-ttu-id="a26b9-109">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] でレポート プロジェクトを作成すると、そのプロジェクトを格納するソリューションも作成されます。</span><span class="sxs-lookup"><span data-stu-id="a26b9-109">At the time you create a report project, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] also creates a solution to contain it.</span></span>  
  
2.  <span data-ttu-id="a26b9-110">新しいクラス ライブラリ プロジェクトを既存のソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-110">Add a new Class Library project to the existing solution.</span></span> <span data-ttu-id="a26b9-111">レポート プロジェクトがスタートアップ プロジェクトとして設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-111">Make sure that the report project is set as the startup project.</span></span> <span data-ttu-id="a26b9-112">この方法の詳細については、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a26b9-112">For more information about how to accomplish this, see your [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
3.  <span data-ttu-id="a26b9-113">ソリューション エクスプローラーで、ソリューションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-113">In Solution Explorer, select the solution.</span></span>  
  
4.  <span data-ttu-id="a26b9-114">**[表示]** メニューの **[プロパティ ページ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a26b9-114">On the **View** menu, click **Property Pages**.</span></span>  
  
     <span data-ttu-id="a26b9-115">**[ソリューション プロパティ ページ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="a26b9-115">The **Solution Property Pages** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="a26b9-116">必要に応じて、左側のペインで **[共通プロパティ]** を展開し、**[プロジェクトの依存関係]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a26b9-116">In the left pane, expand **Common Properties** if necessary, and click **Project Dependencies**.</span></span> <span data-ttu-id="a26b9-117">**[プロジェクト]** ドロップダウン リストからレポート プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-117">Select the report project from the **Project** drop-down list.</span></span> <span data-ttu-id="a26b9-118">**[依存先]** の一覧でアセンブリ プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-118">Select your assembly project in the **Depends On** list.</span></span>  
  
6.  <span data-ttu-id="a26b9-119">**[OK]** をクリックして変更内容を保存し、**[プロパティ ページ]** ダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a26b9-119">Click **OK** to save the changes, and close the **Property Pages** dialog.</span></span>  
  
7.  <span data-ttu-id="a26b9-120">ソリューション エクスプローラーで、カスタム アセンブリ プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-120">In Solution Explorer, select your custom assembly project.</span></span>  
  
8.  <span data-ttu-id="a26b9-121">**[表示]** メニューの **[プロパティ ページ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a26b9-121">On the **View** menu, click **Property Pages**.</span></span>  
  
     <span data-ttu-id="a26b9-122">**[プロジェクト プロパティ ページ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="a26b9-122">The **Project Property Pages** dialog box opens.</span></span>  
  
9. <span data-ttu-id="a26b9-123">C# プロジェクトの場合は **[ビルド]** タブをクリックし、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] プロジェクトの場合は **[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a26b9-123">Click the **Build** tab if you're in a C# project or the **Compile** tab if you're in a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] project.</span></span>  
  
10. <span data-ttu-id="a26b9-124">[**ビルド** / **コンパイル**] ページで、レポートデザイナーフォルダーへのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-124">On the **Build**/**Compile** page, enter the path to the Report Designer folder.</span></span> <span data-ttu-id="a26b9-125">既定では、**[出力パス]** テキスト ボックスの C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE になります。</span><span class="sxs-lookup"><span data-stu-id="a26b9-125">By default, this is C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE) in the **Output Path** text box.</span></span> <span data-ttu-id="a26b9-126">これにより、レポートの実行前に、更新されたカスタム アセンブリのバージョンがレポート デザイナーに直接構築、配置されます。</span><span class="sxs-lookup"><span data-stu-id="a26b9-126">This builds and deploys an updated version of your custom assembly directly to Report Designer before your report is executed.</span></span>  
  
11. <span data-ttu-id="a26b9-127">レポートを設計してカスタム アセンブリを開発したら、カスタム アセンブリ コードにブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-127">Once you have designed your report and developed your custom assembly, set breakpoints in your custom assembly code.</span></span>  
  
12. <span data-ttu-id="a26b9-128">F5 キーを押して、**[DebugLocal]** モードでレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-128">Run the report under **DebugLocal** mode by pressing the F5 key.</span></span> <span data-ttu-id="a26b9-129">ポップアップ プレビュー ウィンドウでレポートを実行すると、デバッガーはアセンブリの実行可能コードに対応するブレークポイントに到達します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-129">When the report executes in the pop-up preview window, the debugger hits any breakpoints that correspond to executable code in your assembly.</span></span> <span data-ttu-id="a26b9-130">F11&lt;/localizedText&gt; キーを使用して、カスタム アセンブリ コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-130">Use F11 to step through your custom assembly code.</span></span>  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a><span data-ttu-id="a26b9-131">Visual Studio の 2 つのインスタンスを使用してアセンブリをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="a26b9-131">To debug assemblies using two instances of Visual Studio</span></span>  
  
1.  <span data-ttu-id="a26b9-132">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を起動して、カスタム アセンブリ プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a26b9-132">Start [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] and open your custom assembly project.</span></span>  
  
2.  <span data-ttu-id="a26b9-133">プロジェクトを構築し、カスタム アセンブリと付随する .pdb ファイルをレポート デザイナーに配置します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-133">Build the project, and deploy your custom assembly and the accompanying .pdb file to the Report Designer.</span></span> <span data-ttu-id="a26b9-134">配置の詳細については、「[カスタム アセンブリの配置](deploying-a-custom-assembly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a26b9-134">For more information about deployment, see [Deploying a Custom Assembly](deploying-a-custom-assembly.md).</span></span>  
  
3.  <span data-ttu-id="a26b9-135">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の別のインスタンスでカスタム アセンブリ コードを開いた状態で、カスタム アセンブリを使用するレポート プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a26b9-135">Open up a report project that uses your custom assembly while leaving your custom assembly code open in a separate instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].</span></span>  
  
4.  <span data-ttu-id="a26b9-136">カスタム アセンブリ プロジェクトを含む [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のインスタンスに移動し、コードに複数のブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-136">Navigate to the instance of [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] that contains your custom assembly project and set some break points in your code.</span></span>  
  
5.  <span data-ttu-id="a26b9-137">カスタム アセンブリ プロジェクトのウィンドウを開いたまま、**[デバッグ]** メニューの **[プロセスにアタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a26b9-137">With the custom assembly project still the active window, click **Attach to Process** on the **Debug** menu.</span></span>  
  
     <span data-ttu-id="a26b9-138">**[プロセスにアタッチ]** ダイアログが開きます。</span><span class="sxs-lookup"><span data-stu-id="a26b9-138">The **Attach to Process** dialog opens.</span></span>  
  
6.  <span data-ttu-id="a26b9-139">プロセスの一覧から、レポート プロジェクトに対応する devenv.exe プロセスを選択して、**[アタッチ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a26b9-139">From the list of processes, select the devenv.exe process that corresponds to your Report Project and click **Attach**.</span></span>  
  
7.  <span data-ttu-id="a26b9-140">カスタム アセンブリのレポートで使用する式を定義し、レポートを設計します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-140">Define the expressions that you will use in your report from your custom assembly and design your report.</span></span>  
  
8.  <span data-ttu-id="a26b9-141">レポートの設計が完了したら、**[プレビュー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a26b9-141">When you are finished designing your report, click the **Preview** tab.</span></span>  
  
     <span data-ttu-id="a26b9-142">レポートが実行され、カスタム アセンブリ コードが定義済みのブレークポイントで停止します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-142">The report executes, and the custom assembly code should break at your predefined break points.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a26b9-143">**[プレビュー]** タブを使用すると、アセンブリのコード アクセス許可が適用されません。</span><span class="sxs-lookup"><span data-stu-id="a26b9-143">Using the **Preview** tab does not enforce code permissions for the assembly.</span></span> <span data-ttu-id="a26b9-144">コード アクセス セキュリティのエラーを含む完全なテストを行う場合は、**[DebugLocal]** 構成設定のレポート プロジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-144">For a complete test, which includes any code access security errors, start the report project under the **DebugLocal** configuration setting.</span></span>  
  
9. <span data-ttu-id="a26b9-145">F11 キーを使用してコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="a26b9-145">Step through your code using the F11 key.</span></span> <span data-ttu-id="a26b9-146">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を使用したデバッグの詳細については、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a26b9-146">For more information about debugging using [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], see the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26b9-147">参照</span><span class="sxs-lookup"><span data-stu-id="a26b9-147">See Also</span></span>  
 [<span data-ttu-id="a26b9-148">レポートでのカスタム アセンブリの使用</span><span class="sxs-lookup"><span data-stu-id="a26b9-148">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
