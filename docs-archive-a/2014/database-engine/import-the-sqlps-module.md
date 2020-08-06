---
title: SQLPS モジュールのインポート | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 37e66db05615ce8a285a80e5ac26b0cae411abeb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718704"
---
# <a name="import-the-sqlps-module"></a><span data-ttu-id="88b75-102">SQLPS モジュールのインポート</span><span class="sxs-lookup"><span data-stu-id="88b75-102">Import the SQLPS Module</span></span>
  <span data-ttu-id="88b75-103">PowerShell から [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を管理する方法としては、`sqlps` モジュールを Windows PowerShell 2.0 環境にインポートする方法を推奨します。</span><span class="sxs-lookup"><span data-stu-id="88b75-103">The recommended way to manage [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] from PowerShell is to import the `sqlps` module into a Windows PowerShell 2.0 environment.</span></span> <span data-ttu-id="88b75-104">このモジュールによって、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のスナップインと管理アセンブリが読み込まれ、登録されます。</span><span class="sxs-lookup"><span data-stu-id="88b75-104">The module loads and registers the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins and manageability assemblies.</span></span>  
  
1.  <span data-ttu-id="88b75-105">**作業を開始する準備:**  [セキュリティ](#Security)</span><span class="sxs-lookup"><span data-stu-id="88b75-105">**Before You Begin:**  [Security](#Security)</span></span>  
  
2.  <span data-ttu-id="88b75-106">**モジュールを読み込むには:**  [sqlps モジュールの読み込み](#LoadSqlps)</span><span class="sxs-lookup"><span data-stu-id="88b75-106">**To load the module:**  [Load the sqlps Module](#LoadSqlps)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="88b75-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="88b75-107">Before You Begin</span></span>  
 <span data-ttu-id="88b75-108">`sqlps` モジュールを Windows PowerShell にインポートした後は、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="88b75-108">After importing the `sqlps` module into Windows PowerShell, you can then:</span></span>  
  
-   <span data-ttu-id="88b75-109">Windows PowerShell コマンドを対話的に実行する。</span><span class="sxs-lookup"><span data-stu-id="88b75-109">Interactively run Windows PowerShell commands.</span></span>  
  
-   <span data-ttu-id="88b75-110">Windows PowerShell スクリプト ファイルを実行する。</span><span class="sxs-lookup"><span data-stu-id="88b75-110">Run Windows PowerShell script files.</span></span>  
  
-   <span data-ttu-id="88b75-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コマンドレットを実行する。</span><span class="sxs-lookup"><span data-stu-id="88b75-111">Run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlets.</span></span>  
  
-   <span data-ttu-id="88b75-112">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロバイダー パスを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの階層内を移動する。</span><span class="sxs-lookup"><span data-stu-id="88b75-112">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider paths to navigate through the hierarchy of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
-   <span data-ttu-id="88b75-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の管理オブジェクト モデル (Microsoft.SqlServer.Management.Smo など) を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のオブジェクトを管理する。</span><span class="sxs-lookup"><span data-stu-id="88b75-113">Use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] manageability object models (such as Microsoft.SqlServer.Management.Smo) to manage [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="88b75-114">2 つの SQL Server コマンドレット (`Encode-Sqlname` および `Decode-Sqlname`) の名前で使用されている動詞は、Windows PowerShell 2.0 で承認されている動詞と一致しません。</span><span class="sxs-lookup"><span data-stu-id="88b75-114">The verbs used in the names of two SQL Server cmdlets (`Encode-Sqlname` and `Decode-Sqlname`) do not match the approved verbs for Windows PowerShell 2.0.</span></span> <span data-ttu-id="88b75-115">このことは、コマンドレットの操作には影響しませんが、`sqlps` モジュールがセッションにインポートされるときに、Windows PowerShell による警告が発生します。</span><span class="sxs-lookup"><span data-stu-id="88b75-115">This has no effect on their operation, but Windows PowerShell raises a warning when the `sqlps` module is imported to a session.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="88b75-116">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="88b75-116">Security</span></span>  
 <span data-ttu-id="88b75-117">既定では、Windows PowerShell 実行時のスクリプト実行ポリシーは **[Restricted]** に設定されます。これにより、Windows PowerShell スクリプトの実行が防止されます。</span><span class="sxs-lookup"><span data-stu-id="88b75-117">By default, Windows PowerShell runs with the scripting execution policy set to **Restricted**, which prevents running any Windows PowerShell scripts.</span></span> <span data-ttu-id="88b75-118">`sqlps` モジュールを読み込む際は、`Set-ExecutionPolicy` コマンドレットを使用すると、署名されたスクリプトまたは任意のスクリプトの実行を有効化できます。</span><span class="sxs-lookup"><span data-stu-id="88b75-118">To load the `sqlps` module, you can use the `Set-ExecutionPolicy` cmdlet to enable running signed scripts, or any scripts.</span></span> <span data-ttu-id="88b75-119">信頼できるソースからのスクリプト以外は実行しないでください。また、適切な NTFS 権限を使用して、すべての入力ファイルと出力ファイルのセキュリティを保護してください。</span><span class="sxs-lookup"><span data-stu-id="88b75-119">Only run scripts from trusted sources, and secure all input and output files using the appropriate NTFS permissions.</span></span> <span data-ttu-id="88b75-120">Windows PowerShell スクリプトの有効化の詳細については、「 [Windows PowerShell スクリプトの実行](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88b75-120">For more information about enabling Windows PowerShell scripts, see [Running Windows PowerShell Scripts](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows).</span></span>  
  
##  <a name="load-the-sqlps-module"></a><a name="LoadSqlps"></a><span data-ttu-id="88b75-121">Sqlps モジュールを読み込む</span><span class="sxs-lookup"><span data-stu-id="88b75-121">Load the sqlps Module</span></span>  

### <a name="to-load-the-sqlps-module-in-windows-powershell"></a><span data-ttu-id="88b75-122">Windows PowerShell に sqlps モジュールを読み込むには</span><span class="sxs-lookup"><span data-stu-id="88b75-122">To load the sqlps module in Windows PowerShell</span></span>
  
1.  <span data-ttu-id="88b75-123">適切なスクリプト実行ポリシーを設定するには、`Set-ExecutionPolicy` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="88b75-123">Use the `Set-ExecutionPolicy` cmdlet to set the appropriate script execution policy.</span></span>  
  
2.  <span data-ttu-id="88b75-124">sqlps モジュールをインポートするには、`Import-Module` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="88b75-124">Use the `Import-Module` cmdlet to import the sqlps module.</span></span> <span data-ttu-id="88b75-125">`DisableNameChecking` および `Encode-Sqlname` についての警告を抑制する場合は、`Decode-Sqlname` パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="88b75-125">Specify the `DisableNameChecking` parameter if you want to suppress the warning about `Encode-Sqlname` and `Decode-Sqlname`.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="88b75-126">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="88b75-126">Example (PowerShell)</span></span>  
 <span data-ttu-id="88b75-127">この例は `sqlps` モジュールを読み込み、名前のチェックを無効にします。</span><span class="sxs-lookup"><span data-stu-id="88b75-127">This example loads the `sqlps` module with name checking turned off.</span></span>  
  
```powershell
## Import the SQL Server Module.  
  
Import-Module "sqlps" -DisableNameChecking  
```  

## <a name="see-also"></a><span data-ttu-id="88b75-128">参照</span><span class="sxs-lookup"><span data-stu-id="88b75-128">See Also</span></span>  
 <span data-ttu-id="88b75-129">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="88b75-129">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span></span>  
 <span data-ttu-id="88b75-130">[SQL Server PowerShell プロバイダー](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="88b75-130">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="88b75-131">データベース エンジン コマンドレットの使用</span><span class="sxs-lookup"><span data-stu-id="88b75-131">Use the Database Engine cmdlets</span></span>](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
