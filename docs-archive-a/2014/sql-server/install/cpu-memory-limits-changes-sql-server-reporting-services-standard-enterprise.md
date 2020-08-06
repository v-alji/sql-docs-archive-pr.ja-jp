---
title: SQL Server Reporting Services Standard および Enterprise | の CPU とメモリの制限に対する変更Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: dd553715-2b95-4119-8f58-d01de388d9ab
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: bd889344f5b0bc72320ff8467ebd6ecc654872f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634236"
---
# <a name="changes-to-cpu-and-memory-limits-for-sql-server-reporting-services-standard-and-enterprise"></a><span data-ttu-id="83bc5-102">SQL Server Reporting Services Standard および Enterprise での CPU およびメモリの制限の変更点</span><span class="sxs-lookup"><span data-stu-id="83bc5-102">Changes to CPU and memory limits for SQL Server Reporting Services Standard and Enterprise</span></span>
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="83bc5-103">Reporting Services Standard Edition および Enterprise Edition では、最大 64 GB のシステム メモリがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="83bc5-103">Reporting Services Standard and Enterprise supports a maximum of 64 gigabytes of system memory.</span></span>  
  
## <a name="component"></a><span data-ttu-id="83bc5-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="83bc5-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
### <a name="description"></a><span data-ttu-id="83bc5-105">説明</span><span class="sxs-lookup"><span data-stu-id="83bc5-105">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="83bc5-106">Reporting Services Standard Edition および Enterprise Edition では、最大 64 GB のシステム メモリがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="83bc5-106">Reporting Services Standard and Enterprise supports a maximum of 64 gigabytes of system memory.</span></span> <span data-ttu-id="83bc5-107">必要に応じて、新しい制限に合うように現在のシステム設定を再構成してください。</span><span class="sxs-lookup"><span data-stu-id="83bc5-107">You may need to reconfigure your current system settings to align with the new limits.</span></span>  
  
 <span data-ttu-id="83bc5-108">の他のエディションの CPU およびメモリの制限の詳細について [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、「 [SQL Server のエディション別の計算容量制限](../compute-capacity-limits-by-edition-of-sql-server.md)」および「 [SQL Server の各エディションがサポートするメモリ](https://go.microsoft.com/fwlink/?LinkId=212633)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83bc5-108">For more information about CPU and memory limits for other editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Compute Capacity Limits by Edition of SQL Server](../compute-capacity-limits-by-edition-of-sql-server.md), and [Memory Supported by the Editions of SQL Server](https://go.microsoft.com/fwlink/?LinkId=212633).</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="83bc5-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="83bc5-109">Corrective Action</span></span>  
 <span data-ttu-id="83bc5-110">必要に応じて、新しい CPU およびメモリの制限に合うように現在のシステム設定を再構成してください。</span><span class="sxs-lookup"><span data-stu-id="83bc5-110">You may need to reconfigure your current system settings to align with the new CPU and memory limits.</span></span> <span data-ttu-id="83bc5-111">詳細については、「 [ALTER SERVER configuration &#40;transact-sql&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)」および「 [Server Memory サーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83bc5-111">For more information, see [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql), and [Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83bc5-112">参照</span><span class="sxs-lookup"><span data-stu-id="83bc5-112">See Also</span></span>  
 <span data-ttu-id="83bc5-113">[SQL Server 2014 の各エディションがサポートする機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="83bc5-113">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 [<span data-ttu-id="83bc5-114">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="83bc5-114">Backward Compatibility</span></span>](../../../2014/getting-started/backward-compatibility.md)  
  
  
