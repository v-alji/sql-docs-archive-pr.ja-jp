---
title: SQL Server PowerShell のヘルプの参照 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f1d97a3b694eebb924f9e1ff228d4d38da4f45ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716610"
---
# <a name="get-help-sql-server-powershell"></a><span data-ttu-id="28938-102">Get Help SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="28938-102">Get Help SQL Server PowerShell</span></span>
  <span data-ttu-id="28938-103">Windows PowerShell 用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーおよびコマンドレットの使用方法に関していくつかの情報源が用意されています。</span><span class="sxs-lookup"><span data-stu-id="28938-103">There are several sources of information about using the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell and cmdlets.</span></span> <span data-ttu-id="28938-104">これには、Windows PowerShell 環境で参照できるヘルプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="28938-104">This includes the help that is available in the Windows PowerShell environment.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="28938-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="28938-105">Before You Begin</span></span>  
 <span data-ttu-id="28938-106">Windows PowerShell について学習するには、「 [Windows PowerShell ファースト ステップ ガイド](https://technet.microsoft.com/library/hh857337.aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="28938-106">To learn about Windows PowerShell, see [Windows PowerShell Getting Started Guide](https://technet.microsoft.com/library/hh857337.aspx).</span></span>  
  
 <span data-ttu-id="28938-107">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コマンドレットおよびプロバイダーの概要については、「 [SQL Server PowerShell](../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28938-107">For an overview of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets and provider, see [SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="help-in-the-windows-powershell-environment"></a><span data-ttu-id="28938-108">Windows PowerShell 環境でのヘルプ</span><span class="sxs-lookup"><span data-stu-id="28938-108">Help in the Windows PowerShell Environment</span></span>  
 <span data-ttu-id="28938-109">Windows PowerShell 環境でヘルプを参照するには、 **Get-Help** コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="28938-109">Use the **Get-Help** cmdlet to get help in the Windows PowerShell environment.</span></span> <span data-ttu-id="28938-110">**Get-Help** では、Windows PowerShell 言語および Windows PowerShell で使用できるさまざまなコマンドレットやプロバイダーの基本的なヘルプが提供されます。</span><span class="sxs-lookup"><span data-stu-id="28938-110">**Get-Help** provides basic help for the Windows PowerShell language and the various cmdlets and providers available in Windows PowerShell.</span></span>  
  
 <span data-ttu-id="28938-111">**Get-Help**の使用方法の詳細については、「 [ヘルプの表示: Get-Help](https://go.microsoft.com/fwlink/?LinkId=102136)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28938-111">For more information on the ways you can use **Get-Help**, see [Get-Help: Getting Help](https://go.microsoft.com/fwlink/?LinkId=102136).</span></span>  
  
### <a name="sql-server-powershell-provider-help"></a><span data-ttu-id="28938-112">SQL Server PowerShell プロバイダーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="28938-112">SQL Server PowerShell Provider Help</span></span>  
 <span data-ttu-id="28938-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell プロバイダーは、SQLSERVER:\SQL、SQLSERVER:\DAC フォルダーなど、SQLSERVER 仮想ドライブ上のいくつかのフォルダーを実装します。</span><span class="sxs-lookup"><span data-stu-id="28938-113">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider implements several folders on a SQLSERVER virtual drive, such as the SQLSERVER:\SQL and SQLSERVER:\DAC folders.</span></span> <span data-ttu-id="28938-114">各フォルダーは、SQL Server 管理オブジェクト モデルの 1 つに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="28938-114">Each folder is associated with one of the SQL Server manageability object models.</span></span> <span data-ttu-id="28938-115">SQL Server パスの各ノードに関連付けられているメソッドとプロパティを一覧表示することはできますが、PowerShell 環境でそれらのヘルプを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="28938-115">While you can list the methods and properties associated with each node in a SQL Server path, you cannot get help for them in the PowerShell environment.</span></span> <span data-ttu-id="28938-116">フォルダーと、関連するプログラミング リファレンスへのリンクの表については、「 [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="28938-116">For a table of the folders with links to the associated programming reference, see [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).</span></span>  
  
### <a name="invoke-sqlcmd-help"></a><span data-ttu-id="28938-117">Invoke-Sqlcmd のヘルプ</span><span class="sxs-lookup"><span data-stu-id="28938-117">Invoke-Sqlcmd Help</span></span>  
 <span data-ttu-id="28938-118">**Invoke-Sqlcmd** コマンドレットは、 **sqlcmd** ユーティリティで実行できる任意のクエリまたはスクリプト ファイルを入力として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="28938-118">The **Invoke-Sqlcmd** cmdlet takes as input any query or script file that can be run by the **sqlcmd** utility.</span></span> <span data-ttu-id="28938-119">**Get-Help** を使用すると **Invoke-Sqlcmd** とそのパラメーターに関する情報を取得できますが、 **sqlcmd** クエリは **Get-Help** に対応していません。</span><span class="sxs-lookup"><span data-stu-id="28938-119">You can use **Get-Help** to get information about **Invoke-Sqlcmd** and its parameters, but there is no **Get-Help** coverage for the **sqlcmd** queries.</span></span>  
  
 <span data-ttu-id="28938-120">*-Query* または *-QueryFromFile* の入力には以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="28938-120">The *-Query* or *-QueryFromFile* input can contain:</span></span>  
  
-   <span data-ttu-id="28938-121">**sqlcmd** の変数とコマンド。</span><span class="sxs-lookup"><span data-stu-id="28938-121">**sqlcmd** variables and commands.</span></span> <span data-ttu-id="28938-122">これらの変数とコマンドについては、「 [sqlcmd Utility](../tools/sqlcmd-utility.md)」の「解説」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="28938-122">For information about these variables and commands, see the Remarks section of [sqlcmd Utility](../tools/sqlcmd-utility.md).</span></span>  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="28938-123">ステートメント。</span><span class="sxs-lookup"><span data-stu-id="28938-123">statements.</span></span> <span data-ttu-id="28938-124">[!INCLUDE[tsql](../includes/tsql-md.md)] 言語の詳細については、「[TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;](/sql/t-sql/language-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28938-124">For more information about the [!INCLUDE[tsql](../includes/tsql-md.md)] language, see [Transact-SQL Reference &#40;Database Engine&#41;](/sql/t-sql/language-reference).</span></span>  
  
-   <span data-ttu-id="28938-125">XQuery ステートメント。</span><span class="sxs-lookup"><span data-stu-id="28938-125">XQuery statements.</span></span> <span data-ttu-id="28938-126">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でサポートされる XQuery 言語の詳細については、「[XQuery 言語リファレンス &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28938-126">For more information about the XQuery language supported by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [XQuery Language Reference &#40;SQL Server&#41;](/sql/xquery/xquery-language-reference-sql-server).</span></span>  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a><span data-ttu-id="28938-127">SQL Server コマンドレットのヘルプの参照</span><span class="sxs-lookup"><span data-stu-id="28938-127">Get Help for a SQL Server cmdlet</span></span>  
 <span data-ttu-id="28938-128">**コマンドレットのヘルプを取得するには**</span><span class="sxs-lookup"><span data-stu-id="28938-128">**To get help for a cmdlet**</span></span>  
  
-   <span data-ttu-id="28938-129">コマンドレットの名前と返されるヘルプのレベルを指定して、Get-Help を実行します。</span><span class="sxs-lookup"><span data-stu-id="28938-129">Run Get-Help specifying the name of the cmdlet and the level of help to be returned.</span></span>  
  
### <a name="example-cmdlet-get-help"></a><span data-ttu-id="28938-130">例: コマンドレット Get-Help</span><span class="sxs-lookup"><span data-stu-id="28938-130">Example: cmdlet Get-Help</span></span>  
 <span data-ttu-id="28938-131">次の例は、 **Invoke-Sqlcmd**のさまざまなレベルのヘルプを返します:</span><span class="sxs-lookup"><span data-stu-id="28938-131">The following examples return various levels of help for **Invoke-Sqlcmd**:</span></span>  
  
```powershell
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd -Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd -Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd -Syntax  
```  
  
## <a name="get-a-list-of-providers"></a><span data-ttu-id="28938-132">プロバイダーの一覧の取得</span><span class="sxs-lookup"><span data-stu-id="28938-132">Get a List of Providers</span></span>  

### <a name="to-get-a-list-of-active-providers"></a><span data-ttu-id="28938-133">アクティブ プロバイダーの一覧を取得するには</span><span class="sxs-lookup"><span data-stu-id="28938-133">To get a list of active providers</span></span>
  
1.  <span data-ttu-id="28938-134">プロバイダーのカテゴリを指定して、Get-Help を実行します。</span><span class="sxs-lookup"><span data-stu-id="28938-134">Run Get-Help specifying the provider category.</span></span>  
  
 <span data-ttu-id="28938-135">Windows PowerShell でプロバイダーのヘルプを参照する方法の詳細については、「 [ドライブとプロバイダー](https://go.microsoft.com/fwlink/?LinkId=102137)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="28938-135">For more information about getting provider help in Windows PowerShell, see [Drives and Providers](https://go.microsoft.com/fwlink/?LinkId=102137).</span></span>  
  
### <a name="example-get-a-list-of-providers"></a><span data-ttu-id="28938-136">例: プロバイダーの一覧の取得</span><span class="sxs-lookup"><span data-stu-id="28938-136">Example: Get a List of Providers</span></span>  
 <span data-ttu-id="28938-137">次のコードは、Windows PowerShell セッションで現在有効になっているプロバイダーの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="28938-137">This code returns a list of the providers currently enabled in your Windows PowerShell session:</span></span>  
  
```powershell
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a><span data-ttu-id="28938-138">SQL Server プロバイダーのヘルプの参照</span><span class="sxs-lookup"><span data-stu-id="28938-138">Get Help About the SQL Server Provider</span></span>  
 <span data-ttu-id="28938-139">**プロバイダーのヘルプを参照するには**</span><span class="sxs-lookup"><span data-stu-id="28938-139">**To get help about the provider**</span></span>  
  
1.  <span data-ttu-id="28938-140">名前を SQLServer と指定して、Get-Help を実行します。</span><span class="sxs-lookup"><span data-stu-id="28938-140">Run Get-Help specifying the name SQLServer</span></span>  
  
### <a name="example-get-sql-server-provider-help"></a><span data-ttu-id="28938-141">例: SQL Server プロバイダーのヘルプの参照</span><span class="sxs-lookup"><span data-stu-id="28938-141">Example: Get SQL Server Provider Help</span></span>  
 <span data-ttu-id="28938-142">この例は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダーに関する基本的な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="28938-142">This example returns basic information about the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider:</span></span>  
  
```powershell
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a><span data-ttu-id="28938-143">メソッドとプロパティの一覧表示</span><span class="sxs-lookup"><span data-stu-id="28938-143">List Methods and Properties</span></span>  
 <span data-ttu-id="28938-144">**SQL Server プロバイダーのパス内のノードのメソッドとプロパティを一覧表示するには**</span><span class="sxs-lookup"><span data-stu-id="28938-144">**To list the methods and properties for a node in a SQL Server provider path**</span></span>  
  
1.  <span data-ttu-id="28938-145">SQL Server パスのノードに CD するか、その場所を設定された変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="28938-145">Either CD to a node in the SQL Server path, or create a variable set to that location.</span></span>  
  
2.  <span data-ttu-id="28938-146">-Type パラメーターをメソッドまたはプロパティのいずれかに設定して、 **Get Member**コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="28938-146">Run the **Get-Member** cmdlet with the -Type parameter set to either Methods or Properties</span></span>  
  
### <a name="examples-listing-methods-and-properties"></a><span data-ttu-id="28938-147">例: メソッドとプロパティの一覧表示</span><span class="sxs-lookup"><span data-stu-id="28938-147">Examples: Listing Methods and Properties</span></span>  
 <span data-ttu-id="28938-148">この例は、Databases ノードでサポートされているメソッドを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="28938-148">This example lists the methods supported for the Databases node:</span></span>  
  
```powershell
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 <span data-ttu-id="28938-149">この例は、SMO Table オブジェクトに設定されている変数のプロパティを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="28938-149">This example lists the properties for a variable that has been set to an SMO Table object:</span></span>  
  
```powershell
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a><span data-ttu-id="28938-150">参照</span><span class="sxs-lookup"><span data-stu-id="28938-150">See Also</span></span>  
 <span data-ttu-id="28938-151">[SQL Server PowerShell プロバイダー](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="28938-151">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="28938-152">データベース エンジン コマンドレットの使用</span><span class="sxs-lookup"><span data-stu-id="28938-152">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
