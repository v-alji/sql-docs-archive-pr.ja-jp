---
title: Windows PowerShell を使用した PowerPivot の構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4d83e53e-04f1-417d-9039-d9e81ae0483d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83b42da3e676a291bb021c02ee52e9a810207397
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644162"
---
# <a name="powerpivot-configuration-using-windows-powershell"></a><span data-ttu-id="64ad1-102">Windows PowerShell を使用した PowerPivot の構成</span><span class="sxs-lookup"><span data-stu-id="64ad1-102">PowerPivot Configuration using Windows PowerShell</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="64ad1-103">には、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]のインストールを構成するために使用できる Windows PowerShell コマンドレットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="64ad1-103">includes Windows PowerShell cmdlets that you can use to configure an installation of [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].</span></span> <span data-ttu-id="64ad1-104">PowerShell によりインストールを完全に構成するには、SharePoint コマンドレットと PowerPivot for SharePoint コマンドレットの両方を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64ad1-104">To fully configure an installation with PowerShell requires the use of both SharePoint cmdlets and PowerPivot for SharePoint cmdlets.</span></span> <span data-ttu-id="64ad1-105">構成の大部分は [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ツールのいずれかを使用して実行することができます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-105">A majority of configuration can be completed using one of the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] tools.</span></span> <span data-ttu-id="64ad1-106">ツールの詳細については、「 [PowerPivot 構成ツール](power-pivot-configuration-tools.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64ad1-106">For more information on the tools, see [PowerPivot Configuration Tools](power-pivot-configuration-tools.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="64ad1-107">SharePoint 2010 ファームの場合、PowerPivot for SharePoint または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] データベース サーバーを使用する SharePoint ファームを構成する前に、SharePoint 2010 SP1 をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="64ad1-107">For a SharePoint 2010 farm, SharePoint 2010 SP1 must be installed before you can configure either PowerPivot for SharePoint, or a SharePoint farm that uses a [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] database server.</span></span> <span data-ttu-id="64ad1-108">サービス パックをインストールしていない場合は、サーバーの構成を始める前にインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="64ad1-108">If you have not yet installed the service pack, install it before you begin configuring the server.</span></span>  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-powershell"></a><span data-ttu-id="64ad1-109">PowerShell を使用して PowerPivot for SharePoint を構成する利点</span><span class="sxs-lookup"><span data-stu-id="64ad1-109">Benefits of Configuring PowerPivot for SharePoint Using PowerShell</span></span>  
 <span data-ttu-id="64ad1-110">Windows  PowerShell スクリプト (.ps1) ファイルを作成して構成タスクを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-110">You can build Windows PowerShell script (.ps1) files to automate configuration tasks.</span></span> <span data-ttu-id="64ad1-111">この方法は、任意のサーバーで実行できるスクリプト化されたインストール手順および構成手順が必要な場合に推奨されます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-111">This approach is recommended if you require scripted installation and configuration steps that you can run on any server.</span></span> <span data-ttu-id="64ad1-112">このようなスクリプトは、ハードウェア障害が発生したときにサーバーを再構築するディザスター リカバリー計画の一環として必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="64ad1-112">You might require such a script as part of a disaster recovery plan for rebuilding a server in the event of a hardware failure.</span></span>  
  
## <a name="view-a-list-of-the-powerpivot-cmdlets-on-a-server"></a><span data-ttu-id="64ad1-113">サーバーで PowerPivot コマンドレットの一覧を表示する</span><span class="sxs-lookup"><span data-stu-id="64ad1-113">View a list of the PowerPivot Cmdlets on a Server</span></span>  
 <span data-ttu-id="64ad1-114">コマンドレットの内容と例については [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、「 [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64ad1-114">To see content and examples of the [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cmdlets, see [PowerShell Reference for PowerPivot for SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint).</span></span>  
  
 <span data-ttu-id="64ad1-115">PowerShell を使用して PowerPivot コマンドレットの一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="64ad1-115">To use PowerShell to view a list of the PowerPivot cmdlets:</span></span>  
  
1.  <span data-ttu-id="64ad1-116">**[管理者として実行]** オプションを使用して SharePoint 管理シェルを開きます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-116">Open SharePoint Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="64ad1-117">次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="64ad1-117">Enter the following command:</span></span>  
  
    ```powershell
    Get-Help *powerpivot*  
    ```  
  
     <span data-ttu-id="64ad1-118">コマンドレット名に PowerPivot を含むコマンドレットの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-118">You should see a list of cmdlets that include PowerPivot in the cmdlet name.</span></span> <span data-ttu-id="64ad1-119">たとえば、「 `Get-PowerPivotServiceApplication` 」のように指定します。</span><span class="sxs-lookup"><span data-stu-id="64ad1-119">For example `Get-PowerPivotServiceApplication`.</span></span> <span data-ttu-id="64ad1-120">使用できるコマンドレットの数は、使用している Analysis Services のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="64ad1-120">The number of cmdlets available depends on the version of Analysis Services you are using.</span></span>  
  
    -   <span data-ttu-id="64ad1-121">SharePoint モードで構成された SQL Server 2012 SP1 Analysis Services サーバーおよび SharePoint 2013 では、10 個のコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-121">10 cmdlets with SQL Server 2012 SP1 Analysis Services server configured in SharePoint mode, and SharePoint 2013.</span></span> <span data-ttu-id="64ad1-122">2012 SP1 バージョンで使用される新しいアーキテクチャでは、分析サーバーを SharePoint ファームの外部で実行できるため、必要な管理 Windows PowerShell コマンドレットが少なくて済みます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-122">The 2012 SP1 version utilizes a new architecture that allows the Analysis Server to run outside the SharePoint farm and requires fewer management Windows PowerShell cmdlets.</span></span>  
  
    -   <span data-ttu-id="64ad1-123">SharePoint モードで構成された SQL Server 2012 Analysis Services サーバーおよび SharePoint 2010 では、17 個のコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-123">17 cmdlets with SQL Server 2012 Analysis Services server configured in SharePoint mode, and SharePoint 2010.</span></span>  
  
     <span data-ttu-id="64ad1-124">一覧にコマンドが返されない場合、または "" のようなエラーメッセージが表示される場合は `get-help could not find *powerpivot* in a help file in this session.` 、このトピックの次のセクションを参照して、サーバーで PowerPivot コマンドレットを有効にする方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="64ad1-124">If no commands are returned in the list or you see an error message similar to "`get-help could not find *powerpivot* in a help file in this session.`", see the next section in this topic for instructions on how to enable the PowerPivot cmdlets on the server.</span></span>  
  
     <span data-ttu-id="64ad1-125">すべてのコマンドレットに、オンライン ヘルプが用意されています。</span><span class="sxs-lookup"><span data-stu-id="64ad1-125">All cmdlets have online help.</span></span> <span data-ttu-id="64ad1-126">`New-PowerPivotServiceApplication` コマンドレットのオンライン ヘルプを表示する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="64ad1-126">The following example shows how to view the online help for the `New-PowerPivotServiceApplication` cmdlet:</span></span>  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Full  
    ```  
  
     <span data-ttu-id="64ad1-127">また、例のみを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="64ad1-127">Alternatively, to view just the examples, use the following syntax:</span></span>  
  
    ```powershell
    Get-Help new-powerpivotserviceapplication -Example  
    ```  
  
## <a name="enable-powerpivot-cmdlets-on-a-server"></a><span data-ttu-id="64ad1-128">サーバーで PowerPivot コマンドレットを有効にする</span><span class="sxs-lookup"><span data-stu-id="64ad1-128">Enable PowerPivot Cmdlets on a Server</span></span>  
 <span data-ttu-id="64ad1-129">PowerPivot コマンドレットは、PowerPivot for SharePoint のインストールとファーム ソリューションの配置が完了した後で利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="64ad1-129">PowerPivot cmdlets are available after you install PowerPivot for SharePoint and deploy the farm solution.</span></span> <span data-ttu-id="64ad1-130">ソリューションは、PowerPivot 構成ツールを実行すると配置されます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-130">The solutions are deployed when you ran the PowerPivot Configuration tool.</span></span> <span data-ttu-id="64ad1-131">コマンドレットの使用を有効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="64ad1-131">Follow these steps to enable the use of cmdlets:</span></span>  
  
1.  <span data-ttu-id="64ad1-132">**[管理者として実行]** オプションを使用して SharePoint 管理シェルを開きます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-132">Open SharePoint Management Shell using the **Run as Administrator** option.</span></span>  
  
2.  <span data-ttu-id="64ad1-133">最初のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="64ad1-133">Run the first cmdlet:</span></span>  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\110\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     <span data-ttu-id="64ad1-134">コマンドレットにより、ソリューション名、ソリューション ID、および Deployed=False が返されます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-134">The cmdlet returns the name of the solution, its solution ID, and Deployed=False.</span></span> <span data-ttu-id="64ad1-135">次の手順では、ソリューションを配置します。</span><span class="sxs-lookup"><span data-stu-id="64ad1-135">In the next step, you deploy the solution.</span></span>  
  
3.  <span data-ttu-id="64ad1-136">2 番目のコマンドレットを実行してソリューションを配置します。</span><span class="sxs-lookup"><span data-stu-id="64ad1-136">Run the second cmdlet to deploy the solution:</span></span>  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
4.  <span data-ttu-id="64ad1-137">ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-137">Close the window.</span></span> <span data-ttu-id="64ad1-138">**[管理者として実行]** を使用してもう一度ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="64ad1-138">Reopen it, again using the **Run as Administrator** option.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="64ad1-139">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="64ad1-139">Related Content</span></span>  
 [<span data-ttu-id="64ad1-140">サーバーの全体管理での PowerPivot サーバーの管理と構成</span><span class="sxs-lookup"><span data-stu-id="64ad1-140">PowerPivot Server Administration and Configuration in Central Administration</span></span>](power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
 [<span data-ttu-id="64ad1-141">PowerPivot Configuration Tools</span><span class="sxs-lookup"><span data-stu-id="64ad1-141">PowerPivot Configuration Tools</span></span>](power-pivot-configuration-tools.md)  
  
 [<span data-ttu-id="64ad1-142">PowerShell リファレンス (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="64ad1-142">PowerShell Reference for PowerPivot for SharePoint</span></span>](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
