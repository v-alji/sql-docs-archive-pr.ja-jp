---
title: SQL Server 識別子のエスケープ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1821187632aeeea0b7a18bf9c4d51d933e947d43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641021"
---
# <a name="escape-sql-server-identifiers"></a><span data-ttu-id="72276-102">SQL Server 識別子のエスケープ</span><span class="sxs-lookup"><span data-stu-id="72276-102">Escape SQL Server Identifiers</span></span>
  <span data-ttu-id="72276-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の区切れらた識別子には使用でき、Windows PowerShell パス名には使用できない文字をエスケープするためによく使用されるのが、Windows PowerShell のバック ティック エスケープ文字 (\`) です。</span><span class="sxs-lookup"><span data-stu-id="72276-103">You can often use the Windows PowerShell back-tick escape character (\`) to escape characters that are allowed in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] delimited identifiers but not Windows PowerShell path names.</span></span> <span data-ttu-id="72276-104">ただし、エスケープできない文字もあります。</span><span class="sxs-lookup"><span data-stu-id="72276-104">Some characters, however, cannot be escaped.</span></span> <span data-ttu-id="72276-105">たとえば、Windows PowerShell ではコロン文字 (:) をエスケープできません。</span><span class="sxs-lookup"><span data-stu-id="72276-105">For example, you cannot escape the colon character (:) in Windows PowerShell.</span></span> <span data-ttu-id="72276-106">この文字を含んだ識別子は、エンコードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="72276-106">Identifiers with that character must be encoded.</span></span> <span data-ttu-id="72276-107">エンコードは、すべての文字に有効であるため、エスケープよりも確実です。</span><span class="sxs-lookup"><span data-stu-id="72276-107">Encoding is more reliable than escaping because encoding works for all characters.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="72276-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="72276-108">Before You Begin</span></span>  
 <span data-ttu-id="72276-109">通常、バック ティック文字 (\`) のキーは、キーボード左上の Esc キーの下にあります (英語キーボードの場合)。</span><span class="sxs-lookup"><span data-stu-id="72276-109">The back-tick character (\`) is usually on the key in the upper left of the keyboard, under the ESC key.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="72276-110">例</span><span class="sxs-lookup"><span data-stu-id="72276-110">Examples</span></span>  
 <span data-ttu-id="72276-111">次に示すのは、# 文字をエスケープする例です。</span><span class="sxs-lookup"><span data-stu-id="72276-111">This is an example of escaping a # character:</span></span>  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 <span data-ttu-id="72276-112">次に示すのは、コンピューター名として (local) を指定する際に、かっこをエスケープする例です。</span><span class="sxs-lookup"><span data-stu-id="72276-112">This is an example of escaping the parenthesis when specifying (local) as a computer name:</span></span>  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a><span data-ttu-id="72276-113">参照</span><span class="sxs-lookup"><span data-stu-id="72276-113">See Also</span></span>  
 <span data-ttu-id="72276-114">[PowerShell での SQL Server 識別子](sql-server-identifiers-in-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="72276-114">[SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md) </span></span>  
 <span data-ttu-id="72276-115">[SQL Server PowerShell プロバイダー](sql-server-powershell-provider.md) </span><span class="sxs-lookup"><span data-stu-id="72276-115">[SQL Server PowerShell Provider](sql-server-powershell-provider.md) </span></span>  
 [<span data-ttu-id="72276-116">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="72276-116">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
  
  
