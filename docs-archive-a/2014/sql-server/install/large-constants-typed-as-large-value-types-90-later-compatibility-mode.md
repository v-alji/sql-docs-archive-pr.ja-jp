---
title: 90以降の互換性モードでは、大きな定数が大きな値の型として型指定されています。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- binary constants
- CHARINDEX function
- constants
- character string constants
- PATINDEX function
ms.assetid: 6e309fa0-5fb9-45a1-9739-f13fae525bfe
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58acde8aaebdcac629463edcfb565eed13355ad4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632277"
---
# <a name="large-constants-are-typed-as-large-value-types-in-90-or-later-compatibility-modes"></a><span data-ttu-id="4af0a-102">90 以上の互換性モードでは大きな定数が大きな値の型として指定される</span><span class="sxs-lookup"><span data-stu-id="4af0a-102">Large constants are typed as large-value types in 90 or later compatibility modes</span></span>
  <span data-ttu-id="4af0a-103">アップグレード アドバイザーは、大きな定数の存在を検出しました。</span><span class="sxs-lookup"><span data-stu-id="4af0a-103">Upgrade Advisor detected the presence of large constants.</span></span> <span data-ttu-id="4af0a-104">サイズが 8,000 バイトを超える文字列定数とバイナリ定数は、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ではラージ オブジェクト データ型として扱われます。</span><span class="sxs-lookup"><span data-stu-id="4af0a-104">Character string constants and binary constants that are more than 8,000 bytes in size are treated as large object data types in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="4af0a-105">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、大きなサイズの文字定数、Unicode 定数、およびバイナリ定数が大きな値の型として指定されます。</span><span class="sxs-lookup"><span data-stu-id="4af0a-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, large character, Unicode, and binary constants, are typed as large-value types.</span></span>  
  
## <a name="component"></a><span data-ttu-id="4af0a-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4af0a-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="4af0a-107">説明</span><span class="sxs-lookup"><span data-stu-id="4af0a-107">Description</span></span>  
 <span data-ttu-id="4af0a-108">CHARINDEX や PATINDEX などの文字列関数が 8,000 バイトを超える文字列定数またはバイナリ定数と共に使用されると、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] はエラー番号 8116 を返し、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンはエラー番号 8152 を返します。</span><span class="sxs-lookup"><span data-stu-id="4af0a-108">When string functions, such as CHARINDEX and PATINDEX, are used with string or binary constants that exceed 8,000 bytes, [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] returns error number 8116, and [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions return error number 8152.</span></span>  
  
 <span data-ttu-id="4af0a-109">[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、文字列関数を `text`、`ntext`、および `image` データ型と共に使用した場合に、文字列関数がエラー 8116 を返します。</span><span class="sxs-lookup"><span data-stu-id="4af0a-109">In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], the string functions return error 8116 when they are used with the `text`, `ntext`, and `image` data types.</span></span>  
  
 <span data-ttu-id="4af0a-110">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、大きな定数はそれぞれが `varchar(max)`、`nvarchar(max)`、および `varbinary(max)` データ型として扱われます。</span><span class="sxs-lookup"><span data-stu-id="4af0a-110">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, the large constants are treated as `varchar(max)`, `nvarchar(max)`, and `varbinary(max)` data types, respectively.</span></span> <span data-ttu-id="4af0a-111">これらのデータ型は文字列関数と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="4af0a-111">These data types are compatible with string functions.</span></span>  
  
 <span data-ttu-id="4af0a-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、CHARINDEX や PATINDEX などの文字列関数は、検出される文字シーケンスを含む文字列が 8,000 バイト未満であると想定しています。</span><span class="sxs-lookup"><span data-stu-id="4af0a-112">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later versions, string functions, such as CHARINDEX and PATINDEX, assume the string that contains the sequence of characters to be found is less than 8,000 bytes.</span></span> <span data-ttu-id="4af0a-113">このため、CHARINDEX や PATINDEX に対してエラー 8152 が発生します。</span><span class="sxs-lookup"><span data-stu-id="4af0a-113">This is why error 8152 is raised for CHARINDEX and PATINDEX.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af0a-114">参照</span><span class="sxs-lookup"><span data-stu-id="4af0a-114">See Also</span></span>  
 <span data-ttu-id="4af0a-115">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="4af0a-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="4af0a-116">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="4af0a-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
