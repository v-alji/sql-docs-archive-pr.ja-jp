---
title: 90互換モードでテーブルヒントを使用する場合は、WITH キーワードを指定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH keyword
- table hints [SQL Server]
ms.assetid: 7636cc85-5155-44db-baf6-df807761adb8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0ecd13475395cef4257d97eb7480f32420932e22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640410"
---
# <a name="specify-the-with-keyword-when-using-table-hints-in-90-compatibility-mode"></a><span data-ttu-id="2fca6-102">互換性モード 90 ではテーブル ヒントを使用するときに WITH キーワードを指定する</span><span class="sxs-lookup"><span data-stu-id="2fca6-102">Specify the WITH keyword when using table hints in 90 compatibility mode</span></span>
  <span data-ttu-id="2fca6-103">例外がいくつかありますが、テーブル ヒントは WITH キーワードを使用して指定された場合のみクエリの FROM 句でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2fca6-103">With some exceptions, table hints are supported in the FROM clause of a query only when the hints are specified by using the WITH keyword.</span></span> <span data-ttu-id="2fca6-104">詳細については、[!INCLUDE[tsql](../../includes/tsql-md.md)] オンライン ブックの「FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])」および「テーブル ヒント ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fca6-104">For more information, see the topics "FROM ([!INCLUDE[tsql](../../includes/tsql-md.md)])" and "Table Hint ([!INCLUDE[tsql](../../includes/tsql-md.md)])" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="component"></a><span data-ttu-id="2fca6-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="2fca6-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="2fca6-106">修正措置</span><span class="sxs-lookup"><span data-stu-id="2fca6-106">Corrective Action</span></span>  
 <span data-ttu-id="2fca6-107">テーブル ヒントの前に WITH キーワードを含めることによって、テーブル ヒントを FROM 句に含めてクエリを変更します。</span><span class="sxs-lookup"><span data-stu-id="2fca6-107">Modify queries that include table hints in the FROM clause by including the WITH keyword before the table hints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fca6-108">参照</span><span class="sxs-lookup"><span data-stu-id="2fca6-108">See Also</span></span>  
 <span data-ttu-id="2fca6-109">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="2fca6-109">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="2fca6-110">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="2fca6-110">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
