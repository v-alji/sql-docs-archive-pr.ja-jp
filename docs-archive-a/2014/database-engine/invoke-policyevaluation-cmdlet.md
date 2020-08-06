---
title: Invoke-PolicyEvaluation コマンドレット | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, Invoke-PolicyEvaluation
- Policy-Based Management, PowerShell
- Invoke-PolicyEvaluation cmdlet
- Cmdlets [SQL Server], Invoke-PolicyEvaluation
- PowerShell [SQL Server], Invoke-PolicyEvaluation
ms.assetid: 3e6d4f5a-59b7-4203-b95a-f7e692c0f131
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 656fdffea191c9cf6fc42d860164bc5af1e04561
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714561"
---
# <a name="invoke-policyevaluation-cmdlet"></a><span data-ttu-id="269f1-102">Invoke-PolicyEvaluation コマンドレット</span><span class="sxs-lookup"><span data-stu-id="269f1-102">Invoke-PolicyEvaluation cmdlet</span></span>
  <span data-ttu-id="269f1-103">**Invoke-PolicyEvaluation** は、SQL Server オブジェクトの対象セットが 1 つまたは複数のポリシーベースの管理ポリシーに指定された条件に準拠しているかどうかを報告する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コマンドレットです。</span><span class="sxs-lookup"><span data-stu-id="269f1-103">**Invoke-PolicyEvaluation** is a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet that reports whether a target set of SQL Server objects complies with the conditions specified in one or more Policy-Based Management policies.</span></span>  
  
## <a name="using-invoke-policyevaluation"></a><span data-ttu-id="269f1-104">Invoke-PolicyEvaluation の使用</span><span class="sxs-lookup"><span data-stu-id="269f1-104">Using Invoke-PolicyEvaluation</span></span>  
 <span data-ttu-id="269f1-105">**Invoke-PolicyEvaluation** は、対象セットと呼ばれる SQL Server オブジェクトのセットに対し、1 つまたは複数のポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="269f1-105">**Invoke-PolicyEvaluation** evaluates one or more policies against a set of SQL Server objects called the target set.</span></span> <span data-ttu-id="269f1-106">対象オブジェクトのセットは、ターゲット サーバーから取得されます。</span><span class="sxs-lookup"><span data-stu-id="269f1-106">The set of target objects comes from a target server.</span></span> <span data-ttu-id="269f1-107">それぞれのポリシーにより、対象オブジェクトに許可される状態を示す条件が定義されます。</span><span class="sxs-lookup"><span data-stu-id="269f1-107">Each policy defines conditions, which are the allowed states for the target objects.</span></span> <span data-ttu-id="269f1-108">たとえば、 **Trustworthy Database** ポリシーは、Trustworthy データベース プロパティを OFF に設定する必要があることを表します。</span><span class="sxs-lookup"><span data-stu-id="269f1-108">For example, the **Trustworthy Database** policy states that the TRUSTWORTHY database property must be set to OFF.</span></span>  
  
 <span data-ttu-id="269f1-109">**-AdHocPolicyEvaluationMode** パラメーターは、実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="269f1-109">The **-AdHocPolicyEvaluationMode** parameter specifies the actions taken:</span></span>  
  
 <span data-ttu-id="269f1-110">○</span><span class="sxs-lookup"><span data-stu-id="269f1-110">Check</span></span>  
 <span data-ttu-id="269f1-111">現在のログインの資格情報を使用して、対象オブジェクトの準拠状態を報告します。</span><span class="sxs-lookup"><span data-stu-id="269f1-111">Report the compliance status of the target objects using the credentials of your current login.</span></span> <span data-ttu-id="269f1-112">オブジェクトの再構成は行いません。</span><span class="sxs-lookup"><span data-stu-id="269f1-112">Do no reconfigure any objects.</span></span> <span data-ttu-id="269f1-113">これが既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="269f1-113">This is the default setting.</span></span>  
  
 <span data-ttu-id="269f1-114">CheckSqlScriptAsProxy</span><span class="sxs-lookup"><span data-stu-id="269f1-114">CheckSqlScriptAsProxy</span></span>  
 <span data-ttu-id="269f1-115">**##MS_PolicyTSQLExecutionLogin##** プロキシ ログインの資格情報を使用して、対象オブジェクトの準拠状態を報告します。</span><span class="sxs-lookup"><span data-stu-id="269f1-115">Report the compliance status of the target objects using the credentials of the **##MS_PolicyTSQLExecutionLogin##** proxy login.</span></span> <span data-ttu-id="269f1-116">オブジェクトの再構成は行いません。</span><span class="sxs-lookup"><span data-stu-id="269f1-116">Do no reconfigure any objects.</span></span>  
  
 <span data-ttu-id="269f1-117">構成</span><span class="sxs-lookup"><span data-stu-id="269f1-117">Configure</span></span>  
 <span data-ttu-id="269f1-118">現在のログインの資格情報を使用して、対象オブジェクトの準拠状態を報告します。</span><span class="sxs-lookup"><span data-stu-id="269f1-118">Report the compliance status of the target objects using the credentials of your current login.</span></span> <span data-ttu-id="269f1-119">ポリシーに準拠していない、設定可能で決定的なオプションを再構成します。</span><span class="sxs-lookup"><span data-stu-id="269f1-119">Reconfigure any settable and deterministic options that are not in compliance with the policies.</span></span>  
  
## <a name="specifying-polices"></a><span data-ttu-id="269f1-120">ポリシーの指定</span><span class="sxs-lookup"><span data-stu-id="269f1-120">Specifying Polices</span></span>  
 <span data-ttu-id="269f1-121">ポリシーを指定する方法は、ポリシーがどこに格納されているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="269f1-121">How you specify a policy depends on where the policy is stored.</span></span> <span data-ttu-id="269f1-122">ポリシーは、次のように 2 つの形式で格納できます。</span><span class="sxs-lookup"><span data-stu-id="269f1-122">Policies can be stored in two formats:</span></span>  
  
-   <span data-ttu-id="269f1-123">ポリシー ストア (たとえばデータベース エンジンのインスタンス) に格納されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="269f1-123">They can be objects stored in a policy store, such as an instance of the Database Engine.</span></span> <span data-ttu-id="269f1-124">SQLSERVER:\SQLPolicy フォルダーを使用して、ポリシー ストア内のポリシーの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="269f1-124">You can use the SQLSERVER:\SQLPolicy folder to specify the location of policies in a policy store.</span></span> <span data-ttu-id="269f1-125">Windows PowerShell コマンドレットを使用して、入力ポリシーをそのプロパティに基づいてフィルター選択できます。たとえば、Where-Object を使用するとポリシーのカテゴリに基づいてフィルター処理でき、Get-Item を使用するとポリシー名に基づいてフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="269f1-125">You can use Windows PowerShell cmdlets to filter the input polices based on their properties, such as using Where-Object to filter on the policy category or Get-Item to filter on policy name.</span></span>  
  
-   <span data-ttu-id="269f1-126">ポリシーは、XML ファイルとしてエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="269f1-126">They can be exported as XML files.</span></span> <span data-ttu-id="269f1-127">ファイル システム ドライブ (たとえば D:) を使用して、XML ファイルの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="269f1-127">You can use a file system drive, such as D:, to specify the location of the XML files.</span></span> <span data-ttu-id="269f1-128">Where-Object などの Windows PowerShell コマンドレットを使用して、ファイル名などのファイル プロパティに基づいてポリシーをフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="269f1-128">You can use Windows PowerShell cmdlets such as Where-Object to filter the policies on their file properties, such as file name.</span></span>  
  
 <span data-ttu-id="269f1-129">ポリシーがポリシー ストアに格納されている場合は、評価するポリシーを示す PSObjects のセットを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="269f1-129">If the policies are stored in a policy store, you must pass in a set of PSObjects pointing to the policies to be evaluated.</span></span> <span data-ttu-id="269f1-130">そのためには、通常、Get-Item などのコマンドレットの出力をパイプして **Invoke-PolicyEvaluation**に渡します。 **-Policy** パラメーターを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="269f1-130">This is typically done by piping the output of a cmdlet such as Get-Item to **Invoke-PolicyEvaluation**, and does not require that you specify the **-Policy** parameter.</span></span> <span data-ttu-id="269f1-131">たとえば、マイクロソフトのベスト プラクティス ポリシーがデータベース エンジンのインスタンスにインポートされている場合、次のコマンドは、 **Database Status** ポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="269f1-131">For example, if you have imported the Microsoft Best Practices policies into your instance of the database engine, this command evaluates the **Database Status** policy:</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Get-Item "Database Status" | Invoke-PolicyEvaluation -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="269f1-132">この例では、Where-Object を使用して、ポリシー ストアの複数のポリシーを、 **PolicyCategory** プロパティに基づいてフィルター処理しています。</span><span class="sxs-lookup"><span data-stu-id="269f1-132">This example shows using Where-Object to filter multiple policies from a policy store based on their **PolicyCategory** property.</span></span> <span data-ttu-id="269f1-133">**Invoke-PolicyEvaluation** によって、 **Where-Object**のパイプ出力からのオブジェクトが消費されます。</span><span class="sxs-lookup"><span data-stu-id="269f1-133">The objects from the piped output of **Where-Object** is consumed by **Invoke-PolicyEvaluation**.</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
gci | Where-Object {$_.PolicyCategory -eq "Microsoft Best Practices: Maintenance"} | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
 <span data-ttu-id="269f1-134">ポリシーが XML ファイルとして格納されている場合は、 **-Policy** パラメーターを使用して各ポリシーのパスと名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="269f1-134">If the policies are stored as XML files, you must use the **-Policy** parameter to supply both the path and name for each policy.</span></span> <span data-ttu-id="269f1-135">**-Policy** パラメーターにパスを指定しなかった場合、 **Invoke-PolicyEvaulation** は、 **sqlps** パスの現在の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="269f1-135">If you do not specify a path in the **-Policy** parameter, **Invoke-PolicyEvaulation** uses the current setting of the **sqlps** path.</span></span> <span data-ttu-id="269f1-136">たとえば、次のコマンドは、SQL Server と共にインストールされたマイクロソフトのベスト プラクティス ポリシーの 1 つを、ログインの既定のデータベースに対して評価します。</span><span class="sxs-lookup"><span data-stu-id="269f1-136">For example, this command evaluates one of the Microsoft Best Practice policies installed with SQL Server against the default database for your login:</span></span>  
  
```powershell
Invoke-PolicyEvaluation -Policy "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033\Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="269f1-137">次のコマンドは同じ操作を実行しますが、現在の **sqlps** パスを使用して、ポリシー XML ファイルの場所を確立します。</span><span class="sxs-lookup"><span data-stu-id="269f1-137">This command does the same thing, only it uses the current **sqlps** path to establish the location of the policy XML file:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MYCOMPUTER"  
```  
  
 <span data-ttu-id="269f1-138">次の例では、 **Get-ChildItem** コマンドレットを使用して、複数のポリシー XML ファイルを取得し、パイプを使ってオブジェクトを **Invoke-PolicyEvaluation**に渡しています。</span><span class="sxs-lookup"><span data-stu-id="269f1-138">This example shows using the **Get-ChildItem** cmdlet to retrieve multiple policy XML files and pipe the objects into **Invoke-PolicyEvaluation**:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
gci "Database Status.xml", "Trustworthy Database.xml" | Invoke-PolicyEvaluation -TargetServer "MYCOMPUTER"  
```  
  
## <a name="specifying-the-target-set"></a><span data-ttu-id="269f1-139">対象セットの指定</span><span class="sxs-lookup"><span data-stu-id="269f1-139">Specifying the Target Set</span></span>  
 <span data-ttu-id="269f1-140">3 つのパラメーターを使用して、対象オブジェクトのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="269f1-140">Use three parameters to specify the set of target objects:</span></span>  
  
-   <span data-ttu-id="269f1-141">**-TargetServerName** は、対象オブジェクトを格納している SQL Server のインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="269f1-141">**-TargetServerName** specifies the instance of SQL Server containing the target objects.</span></span> <span data-ttu-id="269f1-142">情報は、 <xref:System.Data.SqlClient.SqlConnection> クラスの ConnectionString プロパティに定義されている形式を使用する文字列に指定できます。</span><span class="sxs-lookup"><span data-stu-id="269f1-142">You can specify the information in a string that uses the format defined for the ConnectionString property of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="269f1-143"><xref:System.Data.SqlClient.SqlConnectionStringBuilder> クラスを使用して、適切な形式の接続文字列を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="269f1-143">You can use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to build a correctly formatted connection string.</span></span> <span data-ttu-id="269f1-144">また、 <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> オブジェクトを作成し、それを **-TargetServer**のパイプ出力からのオブジェクトが消費されます。</span><span class="sxs-lookup"><span data-stu-id="269f1-144">You can also create a <xref:Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection> object and pass it to **-TargetServer**.</span></span> <span data-ttu-id="269f1-145">サーバー名のみの文字列を渡した場合、 **Invoke-PolicyEvaluation** は、Windows 認証を使用してサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="269f1-145">If you supply a string that has only the name of the server, **Invoke-PolicyEvaluation** uses Windows Authentication to connect to the server.</span></span>  
  
-   <span data-ttu-id="269f1-146">**-TargetObjects** は、1 つのオブジェクト、または対象セット内の SQL Server オブジェクトを表すオブジェクトの配列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="269f1-146">**-TargetObjects** takes an object or array of objects that represent the SQL Server objects in the target set.</span></span> <span data-ttu-id="269f1-147">たとえば、 <xref:Microsoft.SqlServer.Management.Smo.Database> クラス オブジェクトの配列を作成し、 **-TargetObjects**のパイプ出力からのオブジェクトが消費されます。</span><span class="sxs-lookup"><span data-stu-id="269f1-147">For example, you could create an array of <xref:Microsoft.SqlServer.Management.Smo.Database> class objects to pass in to **-TargetObjects**.</span></span>  
  
-   <span data-ttu-id="269f1-148">**-TargetExpressions** は、対象セット内のオブジェクトを指定するクエリ式が含まれた文字列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="269f1-148">**-TargetExpressions** takes a string containing a query expression that specifies the objects in the target set.</span></span> <span data-ttu-id="269f1-149">クエリ式には、ノードを '/' 文字で区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="269f1-149">The query expression is in the form of nodes separated by the '/' character.</span></span> <span data-ttu-id="269f1-150">各ノードは、ObjectType[Filter] 形式で記述します。</span><span class="sxs-lookup"><span data-stu-id="269f1-150">Each node is in the form ObjectType[Filter].</span></span> <span data-ttu-id="269f1-151">オブジェクトの種類は、SQL Server 管理オブジェクト (SMO) オブジェクト階層内のオブジェクトの1つです。</span><span class="sxs-lookup"><span data-stu-id="269f1-151">Object type is one of the objects in a SQL Server Management Object (SMO) object hierarchy.</span></span> <span data-ttu-id="269f1-152">Filter は、そのノードのオブジェクトをフィルター処理する式です。</span><span class="sxs-lookup"><span data-stu-id="269f1-152">Filter is an expression that filters for objects at that node.</span></span> <span data-ttu-id="269f1-153">詳細については、「 [クエリ式と Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="269f1-153">For more information, see [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).</span></span>  
  
 <span data-ttu-id="269f1-154">**-TargetObjects** または **-TargetExpression**のどちらか一方だけを指定します。</span><span class="sxs-lookup"><span data-stu-id="269f1-154">Specify either **-TargetObjects** or **-TargetExpression**, not both.</span></span>  
  
 <span data-ttu-id="269f1-155">次の例では、Sfc.SqlStoreConnection オブジェクトを使用して、ターゲット サーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="269f1-155">This example uses an Sfc.SqlStoreConnection object to specify the target server:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
$conn = New-Object Microsoft.SqlServer.Management.Sdk.Sfc.SqlStoreConnection("server='MYCOMPUTER';Trusted_Connection=True")  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName $conn  
```  
  
 <span data-ttu-id="269f1-156">次の例では、 **-TargetExpression** を使用して、評価する特定のデータベースを識別します。</span><span class="sxs-lookup"><span data-stu-id="269f1-156">This example uses **-TargetExpression** to identify the specific database to evaluate:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033"  
Invoke-PolicyEvaluation -Policy "Database Status.xml" -TargetServerName "MyComputer" -TargetExpression "Server[@Name='MYCOMPUTER']/Database[@Name='AdventureWorks2012']"  
```  
  
## <a name="evaluating-analysis-services-policies"></a><span data-ttu-id="269f1-157">Analysis Services ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="269f1-157">Evaluating Analysis Services Policies</span></span>  
 <span data-ttu-id="269f1-158">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに対してポリシーを評価するには、アセンブリを読み込んで PowerShell に登録します。次に、Analysis Services 接続オブジェクトを含む変数を作成し、その変数を **-TargetObject** パラメーターに渡します。</span><span class="sxs-lookup"><span data-stu-id="269f1-158">To evaluate policies against an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you must load and register an assembly into PowerShell, create a variable with an Analysis Services connection object, and pass the variable to the **-TargetObject** parameter.</span></span> <span data-ttu-id="269f1-159">次の例では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のベスト プラクティス セキュリティ構成ポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="269f1-159">This example shows evaluating the Best Practices surface area configuration policy for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\AnalysisServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.AnalysisServices")  
$SSASsvr = New-Object Microsoft.AnalysisServices.Server  
$SSASsvr.Connect("Data Source=Localhost")  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Analysis Services Features.xml" -TargetObject $SSASsvr  
```  
  
## <a name="evaluating-reporting-services-policies"></a><span data-ttu-id="269f1-160">Reporting Services ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="269f1-160">Evaluating Reporting Services Policies</span></span>  
 <span data-ttu-id="269f1-161">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ポリシーを評価するには、アセンブリを読み込んで PowerShell に登録します。次に、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 接続オブジェクトを含む変数を作成し、その変数を **-TargetObject** パラメーターに渡します。</span><span class="sxs-lookup"><span data-stu-id="269f1-161">To evaluate [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] policies, you must load and register an assembly into PowerShell, create a variable with a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] connection object, and pass the variable to the **-TargetObject** parameter.</span></span> <span data-ttu-id="269f1-162">次の例では、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]のベスト プラクティス セキュリティ構成ポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="269f1-162">This example shows evaluating the Best Practices surface area configuration policy for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]:</span></span>  
  
```powershell
sl "C:\Program Files\Microsoft SQL Server\120\Tools\Policies\ReportingServices\1033"  
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Dmf.Adapters")  
$SSRSsvr = new-object Microsoft.SqlServer.Management.Adapters.RSContainer('MyComputer')  
Invoke-PolicyEvaluation -Policy "Surface Area Configuration for Reporting Services 2008 Features.xml" -TargetObject $SSRSsvr  
```  
  
## <a name="formatting-output"></a><span data-ttu-id="269f1-163">出力の書式設定</span><span class="sxs-lookup"><span data-stu-id="269f1-163">Formatting Output</span></span>  
 <span data-ttu-id="269f1-164">既定では、 **Invoke-PolicyEvaluation** の出力は、人間が判読できる形式の簡潔なレポートとしてコマンド プロンプト ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="269f1-164">By default, the output of **Invoke-PolicyEvaluation** is displayed in the command prompt window as a concise report in human-readable format.</span></span> <span data-ttu-id="269f1-165">**-OutputXML** パラメーターを使用すると、詳細なレポートを XML ファイルとして生成できます。</span><span class="sxs-lookup"><span data-stu-id="269f1-165">You can use the **-OutputXML** parameter to specify that the cmdlet instead produce a detailed report as an XML file.</span></span> <span data-ttu-id="269f1-166">**Invoke-PolicyEvaluation** では、SML-IF (Systems Modeling Language Interchange Format) リーダーでファイルを読むことができるように、SML-IF スキーマが使用されます。</span><span class="sxs-lookup"><span data-stu-id="269f1-166">**Invoke-PolicyEvaluation** uses the Systems Modeling Language Interchange Format (SML-IF) schema so the file can be read by SML-IF readers.</span></span>  
  
```powershell
sl "SQLSERVER:\SQLPolicy\MyComputer\DEFAULT\Policies"  
Invoke-PolicyEvaluation -Policy "Datbase Status" -TargetServer "MYCOMPUTER" -OutputXML > C:\MyReports\DatabaseStatusReport.xml  
```  
  
## <a name="see-also"></a><span data-ttu-id="269f1-167">参照</span><span class="sxs-lookup"><span data-stu-id="269f1-167">See Also</span></span>  
 [<span data-ttu-id="269f1-168">データベース エンジン コマンドレットの使用</span><span class="sxs-lookup"><span data-stu-id="269f1-168">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
