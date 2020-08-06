---
title: URN から SQL Server プロバイダー パスへの変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 56c2fdb5f84e57fe3f34348108f14418785659a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641229"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a><span data-ttu-id="90075-102">URN から SQL Server プロバイダー パスへの変換</span><span class="sxs-lookup"><span data-stu-id="90075-102">Convert URNs to SQL Server Provider Paths</span></span>
  <span data-ttu-id="90075-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) モデルでは、オブジェクトに対して URN (Uniform Resource Name) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="90075-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object model (SMO) builds Uniform Resource Names (URN) for its objects.</span></span> <span data-ttu-id="90075-104">各 URN によって、SMO オブジェクトが一意に識別されます。また、`Convert-UrnToPath` コマンドレットを使用して、URN を SQL Server PowerShell プロバイダーのパスに変換できます。</span><span class="sxs-lookup"><span data-stu-id="90075-104">Each URN uniquely identifies a SMO object, and can be converted to a SQL Server PowerShell provider path by using the `Convert-UrnToPath` cmdlet.</span></span>  
  
## <a name="converting-urns-to-paths"></a><span data-ttu-id="90075-105">パスへの URN の変換</span><span class="sxs-lookup"><span data-stu-id="90075-105">Converting URNs to Paths</span></span>  
 <span data-ttu-id="90075-106">各 URN に含まれる情報はオブジェクトへのパスと同じですが、形式が異なります。</span><span class="sxs-lookup"><span data-stu-id="90075-106">Each URN has the same information as a path to the object, but in a different form.</span></span> <span data-ttu-id="90075-107">たとえば、テーブルへのパスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="90075-107">For example, this is the path to a table:</span></span>  
  
 <span data-ttu-id="90075-108">SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address</span><span class="sxs-lookup"><span data-stu-id="90075-108">SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address</span></span>  
  
 <span data-ttu-id="90075-109">これと同じオブジェクトへの URN は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="90075-109">And this is the URN to the same object:</span></span>  
  
 <span data-ttu-id="90075-110">Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']</span><span class="sxs-lookup"><span data-stu-id="90075-110">Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']</span></span>  
  
 <span data-ttu-id="90075-111">PowerShell スクリプトで SMO オブジェクトを作成した場合は、`Urn` プロパティを参照してそのオブジェクトの URN を取得し、`Convert-UrnToPath` コマンドレットを使用して SMO URN 文字列を Windows PowerShell パスに変換できます。</span><span class="sxs-lookup"><span data-stu-id="90075-111">If you have created a SMO object in a PowerShell script, you can reference the `Urn` property to get the URN for the object, and then use the `Convert-UrnToPath` cmdlet to convert the SMO URN string to a Windows PowerShell path.</span></span> <span data-ttu-id="90075-112">次に、プロバイダーを使用して、パス上の別の場所に移動できます。</span><span class="sxs-lookup"><span data-stu-id="90075-112">You can then use the provider to navigate to different locations on the path.</span></span>  
  
 <span data-ttu-id="90075-113">Windows PowerShell パス名でサポートされない拡張文字がノード名に含まれている場合、`Convert-UrnToPath` はそれらの文字を 16 進数表記でエンコードします。</span><span class="sxs-lookup"><span data-stu-id="90075-113">If node names contain extended characters that are not supported in Windows PowerShell path names, `Convert-UrnToPath` encodes them in their hexadecimal representation.</span></span> <span data-ttu-id="90075-114">たとえば、"My:Table" は "My%3ATable" として返されます。</span><span class="sxs-lookup"><span data-stu-id="90075-114">For example "My:Table" is returned as "My%3ATable".</span></span>  
  
 <span data-ttu-id="90075-115">このコマンドレットの使用例については、Windows PowerShell で次を実行してください。</span><span class="sxs-lookup"><span data-stu-id="90075-115">For examples of using the cmdlet, in Windows PowerShell, run:</span></span>  
  
```powershell
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a><span data-ttu-id="90075-116">参照</span><span class="sxs-lookup"><span data-stu-id="90075-116">See Also</span></span>  
 <span data-ttu-id="90075-117">[クエリ式と Uniform Resource Name](../powershell/query-expressions-and-uniform-resource-names.md) </span><span class="sxs-lookup"><span data-stu-id="90075-117">[Query Expressions and Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md) </span></span>  
 <span data-ttu-id="90075-118">[SQL Server PowerShell プロバイダー](../powershell/sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="90075-118">[SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="90075-119">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="90075-119">SQL Server PowerShell</span></span>](../powershell/sql-server-powershell.md)  
