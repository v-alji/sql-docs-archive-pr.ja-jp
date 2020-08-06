---
title: WITH ROWS は、90以降の互換性モードの CREATE STATISTICS ステートメントではサポートされていません。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d28a05e7cd025e213e2cebdce9d582a9df446fea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640346"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a><span data-ttu-id="d573e-102">互換性モード 90 以上では CREATE STATISTICS ステートメントで WITH ROWS がサポートされない</span><span class="sxs-lookup"><span data-stu-id="d573e-102">WITH ROWS is not supported in CREATE STATISTICS statements in the compatibility mode of 90 or later</span></span>
  <span data-ttu-id="d573e-103">互換性モードが 90 以上に設定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、CREATE STATISTICS ステートメントに WITH ROWS を指定できません。</span><span class="sxs-lookup"><span data-stu-id="d573e-103">Specifying WITH ROWS in CREATE STATISTICS statements is not supported when you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] set to the compatibility mode of 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d573e-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d573e-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="d573e-105">修正措置</span><span class="sxs-lookup"><span data-stu-id="d573e-105">Corrective Action</span></span>  
 <span data-ttu-id="d573e-106">を使用する CREATE STATISTICS ステートメントを変更するには、WITH SAMPLE *number*行を指定するか、ドキュメント化された構文に準拠する他のオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d573e-106">Modify CREATE STATISTICS statements that include WITH ROWS by specifying WITH SAMPLE *number* ROWS, or by specifying other options that comply with the documented syntax.</span></span> <span data-ttu-id="d573e-107">詳細については、「SQL Server オンラインブックでの CREATE STATISTICS (Transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d573e-107">For more information, see the topic "CREATE STATISTICS (Transact-SQL) in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d573e-108">参照</span><span class="sxs-lookup"><span data-stu-id="d573e-108">See Also</span></span>  
 <span data-ttu-id="d573e-109">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d573e-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d573e-110">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="d573e-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
