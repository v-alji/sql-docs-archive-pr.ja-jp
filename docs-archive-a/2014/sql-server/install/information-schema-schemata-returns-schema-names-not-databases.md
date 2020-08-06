---
title: INFORMATION_SCHEMA。スキーマは、インスタンス内のデータベースではなく、データベース内のスキーマ名を返します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- INFORMATION_SCHEMA.SCHEMATA view
ms.assetid: 4337b643-910d-47d7-bea8-f4052066b9a2
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cb2a34a59bf6257c188210fc7bf2aeacb70f6b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644791"
---
# <a name="information_schemaschemata-returns-schema-names-in-a-database-not-databases-in-an-instance"></a><span data-ttu-id="a0492-102">INFORMATION_SCHEMA.SCHEMATA がインスタンスのデータベースではなく、データベースのスキーマ名を返す</span><span class="sxs-lookup"><span data-stu-id="a0492-102">INFORMATION_SCHEMA.SCHEMATA returns schema names in a database, not databases in an instance</span></span>
  <span data-ttu-id="a0492-103">アップグレード アドバイザーによって、INFORMATION_SCHEMA.SCHEMATA ビューを参照するステートメントが検出されました。</span><span class="sxs-lookup"><span data-stu-id="a0492-103">Upgrade Advisor detected statements that reference the INFORMATION_SCHEMA.SCHEMATA view.</span></span> <span data-ttu-id="a0492-104">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このビューは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにあるすべてのデータベースを返しました。</span><span class="sxs-lookup"><span data-stu-id="a0492-104">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this view returned all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a0492-105">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、このビューはデータベース内のすべてのスキーマを返します。</span><span class="sxs-lookup"><span data-stu-id="a0492-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later, the view returns all schemas in a database.</span></span>  
  
## <a name="component"></a><span data-ttu-id="a0492-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a0492-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="a0492-107">説明</span><span class="sxs-lookup"><span data-stu-id="a0492-107">Description</span></span>  
 <span data-ttu-id="a0492-108">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、INFORMATION_SCHEMA.SCHEMATA ビューは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにあるすべてのデータベースを返しました。</span><span class="sxs-lookup"><span data-stu-id="a0492-108">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the INFORMATION_SCHEMA.SCHEMATA view returned all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a0492-109">現在は、このビューは、SQL 標準に準拠した、データベースにあるすべてのスキーマを返します。</span><span class="sxs-lookup"><span data-stu-id="a0492-109">Now, the view returns all schemas in a database, which complies with the SQL Standard.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="a0492-110">修正措置</span><span class="sxs-lookup"><span data-stu-id="a0492-110">Corrective Action</span></span>  
 <span data-ttu-id="a0492-111">のインスタンス内のすべてのデータベースを返すように、アプリケーションを変更して、**データベース**カタログビューを参照します [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a0492-111">Modify your application to reference the **sys.databases** catalog view to return all databases in an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0492-112">参照</span><span class="sxs-lookup"><span data-stu-id="a0492-112">See Also</span></span>  
 <span data-ttu-id="a0492-113">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="a0492-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="a0492-114">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="a0492-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
