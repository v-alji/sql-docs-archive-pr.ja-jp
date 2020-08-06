---
title: Sysperfinfo から bigint 値を期待するようにアプリケーションを変更します。 cntr_value |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 108a9b981debc95e182b16847c39a03d4b242088
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740697"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntr_value"></a><span data-ttu-id="d66c4-102">sysperfinfo.cntr_value から bigint 型の値を受け取れるようにアプリケーションを変更する</span><span class="sxs-lookup"><span data-stu-id="d66c4-102">Modify applications to expect bigint values from sysperfinfo.cntr_value</span></span>
  <span data-ttu-id="d66c4-103">sysperfinfo は `bigint` 、cntr_value 列の値を返します。</span><span class="sxs-lookup"><span data-stu-id="d66c4-103">sysperfinfo returns a `bigint` value for the cntr_value column.</span></span>  
  
## <a name="component"></a><span data-ttu-id="d66c4-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d66c4-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="d66c4-105">修正措置</span><span class="sxs-lookup"><span data-stu-id="d66c4-105">Corrective Action</span></span>  
 <span data-ttu-id="d66c4-106">cntr_value 列の `bigint` 型の値を確実に処理できるように、sysperfinfo を使用するアプリケーションを変更してください。</span><span class="sxs-lookup"><span data-stu-id="d66c4-106">Modify applications that use sysperfinfo to ensure that they can handle the `bigint` values of the cntr_value column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d66c4-107">sysperfinfo は互換性ビューです。</span><span class="sxs-lookup"><span data-stu-id="d66c4-107">sysperfinfo is a compatibility view.</span></span> <span data-ttu-id="d66c4-108">代わりに、sys.dm_os_performance_counter 動的管理ビューを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d66c4-108">You should use the sys.dm_os_performance_counter dynamic management view instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66c4-109">参照</span><span class="sxs-lookup"><span data-stu-id="d66c4-109">See Also</span></span>  
 <span data-ttu-id="d66c4-110">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d66c4-110">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d66c4-111">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="d66c4-111">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
