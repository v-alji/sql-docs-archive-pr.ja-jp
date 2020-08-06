---
title: Sp_helptrigger の出力の新しい列がアプリケーションに影響を与える可能性があります |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sp_helptrigger
ms.assetid: b7c42a8f-f2e0-4fa3-b046-3cf39c854c47
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b1f5e936843ed84a5c6b88e2f3685e7a4272bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644776"
---
# <a name="new-column-in-output-of-sp_helptrigger-may-impact-applications"></a><span data-ttu-id="249b9-102">sp_helptrigger 出力の新しい列がアプリケーションに影響を与える可能性がある</span><span class="sxs-lookup"><span data-stu-id="249b9-102">New column in output of sp_helptrigger may impact applications</span></span>
  <span data-ttu-id="249b9-103">sp_helptrigger システムストアドプロシージャによって返される結果セットの最後の列を trigger_schemaias します。</span><span class="sxs-lookup"><span data-stu-id="249b9-103">trigger_schemaias the last column in the result set returned by the sp_helptrigger system stored procedure.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<span data-ttu-id="249b9-104">特定のテーブルで定義されるトリガーに関する情報を入手するには、sys.triggers カタログ ビューをクエリしてください。</span><span class="sxs-lookup"><span data-stu-id="249b9-104">To obtain information about triggers defined on a particular table, query the sys.triggers catalog view.</span></span>  
  
## <a name="component"></a><span data-ttu-id="249b9-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="249b9-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="249b9-106">修正措置</span><span class="sxs-lookup"><span data-stu-id="249b9-106">Corrective Action</span></span>  
 <span data-ttu-id="249b9-107">アプリケーションで sp_helptrigger の使用を確認してください。</span><span class="sxs-lookup"><span data-stu-id="249b9-107">Review the use of sp_helptrigger in applications.</span></span> <span data-ttu-id="249b9-108">また、追加列に対応するようにアプリケーションを変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="249b9-108">You may need to modify your applications to accommodate the additional column.</span></span> <span data-ttu-id="249b9-109">代わりに、sys.triggers カタログ ビューを使用できます。</span><span class="sxs-lookup"><span data-stu-id="249b9-109">Alternatively, you can use the sys.triggers catalog view instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="249b9-110">参照</span><span class="sxs-lookup"><span data-stu-id="249b9-110">See Also</span></span>  
 <span data-ttu-id="249b9-111">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="249b9-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="249b9-112">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="249b9-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
