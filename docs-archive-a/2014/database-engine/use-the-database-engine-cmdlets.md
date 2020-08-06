---
title: データベース エンジン コマンドレットの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 015500c7c985f9f1a1d190954406844f3b184932
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632051"
---
# <a name="use-the-database-engine-cmdlets"></a><span data-ttu-id="1a5b3-102">データベース エンジン コマンドレットの使用</span><span class="sxs-lookup"><span data-stu-id="1a5b3-102">Use the Database Engine cmdlets</span></span>
  <span data-ttu-id="1a5b3-103"> Windows PowerShell コマンドレットは、単一の機能を実現するコマンドで、通常は **Get-Help** や **Set-MachineName** のように動詞と名詞を組み合わせた名前付け規則に従います。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-103">Windows PowerShell cmdlets are single-function commands that typically have a verb-noun naming convention, such as **Get-Help** or **Set-MachineName**.</span></span> <span data-ttu-id="1a5b3-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 固有のコマンドレットは、Windows PowerShell 用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]プロバイダーによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-104">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provider for Windows PowerShell supplies cmdlets specific to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="database-engine-cmdlets"></a><span data-ttu-id="1a5b3-105">データベース エンジンのコマンドレット</span><span class="sxs-lookup"><span data-stu-id="1a5b3-105">Database Engine cmdlets</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="1a5b3-106">では、 [!INCLUDE[ssDE](../includes/ssde-md.md)]用の少数のコマンドレットが実装されます。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-106">implements a small number of cmdlets for the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="1a5b3-107">これらのコマンドレットは、主に新しい PowerShell スクリプトからの既存の Transact-SQL スクリプトの実行、ポリシー ベースの管理ポリシーの評価、および SQL Server プロバイダー パスでの SQL Server 識別子の指定の支援に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-107">These cmdlets are primarily used to run existing Transact-SQL scripts from new PowerShell scripts, evaluate policy-based management policies, and aid in specifying SQL Server identifiers in SQL Server Provider paths.</span></span>  
  
 <span data-ttu-id="1a5b3-108">Windows PowerShell スクリプトの多くは、SQL Server PowerShell プロバイダーおよび SQL Server 管理オブジェクト モデルを使用して、 [!INCLUDE[ssDE](../includes/ssde-md.md)] と共に動作します。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-108">Most Windows PowerShell scripts work with the [!INCLUDE[ssDE](../includes/ssde-md.md)] by using the SQL Server PowerShell provider and the SQL Server manageability object models.</span></span> <span data-ttu-id="1a5b3-109">詳細については、「[SQL Server PowerShell](../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-109">For more information, see [SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="get-cmdlet-help"></a><span data-ttu-id="1a5b3-110">コマンドレットのヘルプの利用</span><span class="sxs-lookup"><span data-stu-id="1a5b3-110">Get Cmdlet Help</span></span>  
 <span data-ttu-id="1a5b3-111">Windows PowerShell 環境では、 **Get-Help** コマンドレットを使用して各コマンドレットのヘルプ情報を参照できます。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-111">In the Windows PowerShell environment, the **Get-Help** cmdlet provides help information for each cmdlet.</span></span> <span data-ttu-id="1a5b3-112">**Get-Help** を実行すると、構文、パラメーター定義、入力と出力の種類、コマンドレットで実行される処理の説明などの情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-112">**Get-Help** returns information such as the syntax, parameter definitions, input and output types, and a description of the action performed by the cmdlet.</span></span> <span data-ttu-id="1a5b3-113">詳細については、「 [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-113">For more information, see [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md).</span></span>  
  
### <a name="partial-parameter-names"></a><span data-ttu-id="1a5b3-114">部分的なパラメーター名</span><span class="sxs-lookup"><span data-stu-id="1a5b3-114">Partial Parameter Names</span></span>  
 <span data-ttu-id="1a5b3-115">コマンドレット パラメーターの完全な名前を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-115">You do not have to specify the entire name of a cmdlet parameter.</span></span> <span data-ttu-id="1a5b3-116">そのコマンドレットでサポートされている他のパラメーターと区別するのに足りる名前の一部のみを指定するだけでかまいません。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-116">You only have to specify enough of the name to uniquely separate it from the other parameters that are supported by the cmdlet.</span></span> <span data-ttu-id="1a5b3-117">たとえば、次の例は、 **Invoke-Sqlcmd -QueryTimeout** パラメーターを指定する 3 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-117">For example, these examples show three ways of specifying the **Invoke-Sqlcmd -QueryTimeout** parameter:</span></span>  
  
```powershell
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a><span data-ttu-id="1a5b3-118">データベース エンジン コマンドレットのタスク</span><span class="sxs-lookup"><span data-stu-id="1a5b3-118">Database Engine cmdlet Tasks</span></span>  
  
|<span data-ttu-id="1a5b3-119">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="1a5b3-119">Task Description</span></span>|<span data-ttu-id="1a5b3-120">トピック</span><span class="sxs-lookup"><span data-stu-id="1a5b3-120">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="1a5b3-121">**Invoke-Sqlcmd** の使用による、 **または XQuery ステートメントを含む** sqlcmd [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプトやコマンドの実行について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-121">Describes using **Invoke-Sqlcmd** to run **sqlcmd** scripts or commands that contain [!INCLUDE[tsql](../includes/tsql-md.md)] or XQuery statements.</span></span> <span data-ttu-id="1a5b3-122">**sqlcmd** の入力を、文字列の入力パラメーターとして、または開くスクリプト ファイルの名前として受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-122">It can accept the **sqlcmd** input as either a character string input parameter, or as the name of a script file to open.</span></span>|[<span data-ttu-id="1a5b3-123">Invoke-Sqlcmd コマンドレット</span><span class="sxs-lookup"><span data-stu-id="1a5b3-123">Invoke-Sqlcmd cmdlet</span></span>](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|<span data-ttu-id="1a5b3-124">**Invoke-PolicyEvaluation** の使用による、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトの対象セットがポリシー ベースの管理ポリシーに定義されている条件に準拠しているかどうかの報告について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-124">Describes using **Invoke-PolicyEvaluation** to report whether a target set of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] objects comply with the conditions that are defined in policy-based management policies.</span></span> <span data-ttu-id="1a5b3-125">必要に応じて、このコマンドレットを使用して、ポリシー条件に準拠していない対象オブジェクト内の設定可能なオプションを再構成することができます。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-125">Optionally, the cmdlet can be used to reconfigure any settable options in the target objects that do not comply with the policy conditions.</span></span>|[<span data-ttu-id="1a5b3-126">Invoke-PolicyEvaluation コマンドレット</span><span class="sxs-lookup"><span data-stu-id="1a5b3-126">Invoke-PolicyEvaluation cmdlet</span></span>](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
|<span data-ttu-id="1a5b3-127">`Encode-Sqlname` と `Decode-Sqlname` の使用による、Windows PowerShell パスではサポートされていない文字を含んだ SQL Server 識別子の処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-127">Describes using `Encode-Sqlname` and `Decode-Sqlname` to handle SQL Server identifiers that contain characters not supported in Windows PowerShell paths.</span></span>|[<span data-ttu-id="1a5b3-128">SQL Server 識別子のエンコードとデコード</span><span class="sxs-lookup"><span data-stu-id="1a5b3-128">Encode and Decode SQL Server Identifiers</span></span>](../powershell/encode-and-decode-sql-server-identifiers.md)|  
|<span data-ttu-id="1a5b3-129">`Convert-UrnToPath` の使用による、SQL Server 管理オブジェクト URN (Uniform Resource Name) から対応する SQL Server プロバイダー パスへの変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="1a5b3-129">Describes using `Convert-UrnToPath` to convert a SQL Server Manageability Object Uniform Resource Name (URN) to the equivalent SQL Server Provider path.</span></span>|[<span data-ttu-id="1a5b3-130">URN から SQL Server プロバイダー パスへの変換</span><span class="sxs-lookup"><span data-stu-id="1a5b3-130">Convert URNs to SQL Server Provider Paths</span></span>](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a><span data-ttu-id="1a5b3-131">参照</span><span class="sxs-lookup"><span data-stu-id="1a5b3-131">See Also</span></span>  
 <span data-ttu-id="1a5b3-132">[SQL Server PowerShell プロバイダー](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="1a5b3-132">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 <span data-ttu-id="1a5b3-133">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="1a5b3-133">[SQL Server PowerShell](../powershell/sql-server-powershell.md) </span></span>  
 [<span data-ttu-id="1a5b3-134">AlwaysOn 可用性グループ &#40;SQL Server の PowerShell コマンドレットの概要&#41;</span><span class="sxs-lookup"><span data-stu-id="1a5b3-134">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  
