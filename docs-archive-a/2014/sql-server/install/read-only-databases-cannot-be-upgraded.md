---
title: 読み取り専用データベースをアップグレードすることはできません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- database cannot be upgraded
ms.assetid: 27964211-ea30-4390-b791-dcf225fb9ae7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ba48ed2bd80961a4949dc13f04fed0637ecc27ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643665"
---
# <a name="read-only-databases-cannot-be-upgraded"></a><span data-ttu-id="c55ed-102">読み取り専用データベースをアップグレードできない</span><span class="sxs-lookup"><span data-stu-id="c55ed-102">Read-only databases cannot be upgraded</span></span>
  <span data-ttu-id="c55ed-103">アップグレード アドバイザーによって、この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにある一部のデータベースをアップグレードできないことが判定されました。</span><span class="sxs-lookup"><span data-stu-id="c55ed-103">Upgrade Advisor has determined that some databases on this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot be upgraded.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c55ed-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c55ed-104">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c55ed-105">説明</span><span class="sxs-lookup"><span data-stu-id="c55ed-105">Description</span></span>  
 <span data-ttu-id="c55ed-106">読み取り専用データベースが検出されました。</span><span class="sxs-lookup"><span data-stu-id="c55ed-106">A read-only database has been detected.</span></span> <span data-ttu-id="c55ed-107">データベースをアップグレードするには、セットアップ時にそのデータベースへの書き込みが可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c55ed-107">To upgrade the database, Setup must be able to write to the database.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c55ed-108">修正措置</span><span class="sxs-lookup"><span data-stu-id="c55ed-108">Corrective Action</span></span>  
 <span data-ttu-id="c55ed-109">データベースを使用しているデータベースがない場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 、または ALTER database ステートメントを使用して、データベースを読み取り/書き込み可能に変更します。</span><span class="sxs-lookup"><span data-stu-id="c55ed-109">When no one is using the database, use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Manager, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], or the ALTER DATABASE statement to change the database to read-write.</span></span> <span data-ttu-id="c55ed-110">次のステートメントを使用すると、データベースが読み取り/書き込み可能に変更されます。</span><span class="sxs-lookup"><span data-stu-id="c55ed-110">The following statement changes the database to read-write.</span></span>  
  
```  
USE master;  
GO  
ALTER DATABASE <database name>  
SET READ_WRITE;  
GO  
```  
  
 <span data-ttu-id="c55ed-111">ALTER DATABASE ステートメントの詳細については、[!INCLUDE[tsql](../../includes/tsql-md.md)] オンライン ブックのトピック「ALTER DATABASE ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c55ed-111">For more information about the ALTER DATABASE statement, see the "ALTER DATABASE ([!INCLUDE[tsql](../../includes/tsql-md.md)])" topic in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55ed-112">参照</span><span class="sxs-lookup"><span data-stu-id="c55ed-112">See Also</span></span>  
 <span data-ttu-id="c55ed-113">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c55ed-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="c55ed-114">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="c55ed-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
