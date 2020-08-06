---
title: データベース エンジン PowerShell リファレンス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3c379a43-c497-47dd-8e7d-2b015c068bb7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2d72f9fcedee02e475369c32a7c263578c9ff156
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641846"
---
# <a name="database-engine-powershell-reference"></a><span data-ttu-id="d4345-102">データベース エンジン PowerShell リファレンス</span><span class="sxs-lookup"><span data-stu-id="d4345-102">Database Engine PowerShell Reference</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="d4345-103">には、[!INCLUDE[ssDE](../includes/ssde-md.md)]で一般的な操作を実行するための一連の Windows PowerShell 2.0 コマンドレットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d4345-103">includes a set of Windows PowerShell 2.0 cmdlets for performing common actions in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="d4345-104">また、クエリ式と URN (Uniform Resource Name) は、SQL Server PowerShell パスに変換したり、 [!INCLUDE[ssDE](../includes/ssde-md.md)]で 1 つ以上のオブジェクトを指定するために使用したりできます。</span><span class="sxs-lookup"><span data-stu-id="d4345-104">In addition, Query Expressions and Uniform Resource Names (URN) can be converted to SQL Server PowerShell paths, or used to specify one or more objects in the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
## <a name="database-engine-cmdlets"></a><span data-ttu-id="d4345-105">データベース エンジンのコマンドレット</span><span class="sxs-lookup"><span data-stu-id="d4345-105">Database Engine Cmdlets</span></span>  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="d4345-106">に含まれている [!INCLUDE[ssDE](../includes/ssde-md.md)]用のコマンドレットは比較的少ないです。</span><span class="sxs-lookup"><span data-stu-id="d4345-106">includes relatively few cmdlets for the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span> <span data-ttu-id="d4345-107">[!INCLUDE[ssDE](../includes/ssde-md.md)] を操作する PowerShell スクリプトの多くは、SQL Server PowerShell プロバイダーおよび管理オブジェクト モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="d4345-107">Most PowerShell scripts working with the [!INCLUDE[ssDE](../includes/ssde-md.md)] use the SQL Server PowerShell provider and the manageability object models.</span></span> <span data-ttu-id="d4345-108">詳細については、「 [SQL Server PowerShell プロバイダー](../powershell/sql-server-powershell-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4345-108">For more information, see [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md).</span></span>  
  
 <span data-ttu-id="d4345-109">Windows PowerShell 環境で SQL Server コマンドレットに関するヘルプを参照する方法については、「 [SQL Server PowerShell のヘルプの参照](../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4345-109">To learn how to get help about the SQL Server cmdlets in a Windows PowerShell environment, see [Get Help SQL Server PowerShell](../powershell/sql-server-powershell.md).</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="d4345-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d4345-110">In This Section</span></span>  
 <span data-ttu-id="d4345-111">ここでは、これらのコマンドレットについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d4345-111">This section contains information about these cmdlets.</span></span>  
  
|<span data-ttu-id="d4345-112">説明</span><span class="sxs-lookup"><span data-stu-id="d4345-112">Description</span></span>|<span data-ttu-id="d4345-113">コマンドレット</span><span class="sxs-lookup"><span data-stu-id="d4345-113">Cmdlet</span></span>|  
|-----------------|------------|  
|<span data-ttu-id="d4345-114">`sqlcmd` ユーティリティを使用して実行できるスクリプトなど、Transact-SQL スクリプトと XQuery スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="d4345-114">Runs Transact-SQL and XQuery scripts, such as scripts that can be run using the `sqlcmd` utility.</span></span>|[<span data-ttu-id="d4345-115">Invoke-Sqlcmd コマンドレット</span><span class="sxs-lookup"><span data-stu-id="d4345-115">Invoke-Sqlcmd cmdlet</span></span>](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|<span data-ttu-id="d4345-116">データベース エンジン オブジェクトがポリシー ベースの管理ポリシーに準拠しているかどうかを評価します。</span><span class="sxs-lookup"><span data-stu-id="d4345-116">Evaluates whether a Database Engine object complies with a Policy-based Management policy.</span></span>|[<span data-ttu-id="d4345-117">Invoke-PolicyEvaluation コマンドレット</span><span class="sxs-lookup"><span data-stu-id="d4345-117">Invoke-PolicyEvaluation cmdlet</span></span>](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
  
### <a name="information-about-other-cmdlets"></a><span data-ttu-id="d4345-118">その他のコマンドレットに関する情報</span><span class="sxs-lookup"><span data-stu-id="d4345-118">Information About Other Cmdlets</span></span>  
 <span data-ttu-id="d4345-119">`Encode-Sqlname` コマンドレットと `Decode-Sqlname` コマンドレットでは、PowerShell パスではサポートされていない文字を含んだ SQL Server 識別子を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d4345-119">The `Encode-Sqlname` and `Decode-Sqlname` cmdlets help you specify SQL Server identifiers that contain characters not supported in PowerShell paths.</span></span> <span data-ttu-id="d4345-120">詳細については、「 [PowerShell での SQL Server 識別子](../powershell/sql-server-identifiers-in-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4345-120">For more information, see [SQL Server Identifiers in PowerShell](../powershell/sql-server-identifiers-in-powershell.md).</span></span>  
  
 <span data-ttu-id="d4345-121">`Convert-UrnToPath` コマンドレットを使用して、[!INCLUDE[ssDE](../includes/ssde-md.md)] オブジェクトの Unique Resource Name を SQL Server PowerShell プロバイダーのパスに変換します。</span><span class="sxs-lookup"><span data-stu-id="d4345-121">Use the `Convert-UrnToPath` cmdlet to convert a Unique Resource Name for a [!INCLUDE[ssDE](../includes/ssde-md.md)] object to a path for the SQL Server PowerShell provider.</span></span> <span data-ttu-id="d4345-122">詳細については、「 [URN から SQL Server プロバイダー パスへの変換](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4345-122">For more information, see [Convert URNs to SQL Server Provider Paths](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md).</span></span>  
  
## <a name="query-expressions-and-unique-resource-names"></a><span data-ttu-id="d4345-123">クエリ式および Unique Resource Name</span><span class="sxs-lookup"><span data-stu-id="d4345-123">Query Expressions and Unique Resource Names</span></span>  
 <span data-ttu-id="d4345-124">クエリ式は、オブジェクト モデル階層内の 1 つまたは複数のオブジェクトを列挙する条件のセットを指定するために XPath と同様の構文を使用する文字列です。</span><span class="sxs-lookup"><span data-stu-id="d4345-124">Query expressions are strings that use syntax similar to XPath to specify a set of criteria that enumerate one or more objects in an object model hierarchy.</span></span> <span data-ttu-id="d4345-125">URN (Unique Resource Name) は、単一のオブジェクトを一意に識別する特定の種類のクエリ式文字列です。</span><span class="sxs-lookup"><span data-stu-id="d4345-125">A Unique Resource Name (URN) is a specific type of query expression string that uniquely identifies a single object.</span></span> <span data-ttu-id="d4345-126">詳細については、「 [クエリ式と Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4345-126">For more information, see [Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4345-127">参照</span><span class="sxs-lookup"><span data-stu-id="d4345-127">See Also</span></span>  
 [<span data-ttu-id="d4345-128">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4345-128">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
  
  
