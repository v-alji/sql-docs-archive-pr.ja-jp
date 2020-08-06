---
title: osql は ED と !! をサポートしない コマンド |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- ED command
- osql utility [SQL Server]
- '!! command'
ms.assetid: 7cc2852f-94e8-4292-9326-c3f1a1acd281
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1ad92a32c47002c8f56e56a5b3695d42d3bdd671
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641407"
---
# <a name="osql-no-longer-supports-the-ed-and--commands"></a><span data-ttu-id="d5c8f-103">osql は ED と !! をサポートしない</span><span class="sxs-lookup"><span data-stu-id="d5c8f-103">osql no longer supports the ED and !!</span></span> <span data-ttu-id="d5c8f-104">commands</span><span class="sxs-lookup"><span data-stu-id="d5c8f-104">commands</span></span>
  <span data-ttu-id="d5c8f-105">**Osql**ユーティリティでは、 **ED**と **!!**</span><span class="sxs-lookup"><span data-stu-id="d5c8f-105">The **osql** utility does not support the **ED** and **!!**</span></span> <span data-ttu-id="d5c8f-106">コ.</span><span class="sxs-lookup"><span data-stu-id="d5c8f-106">commands.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="d5c8f-107">修正措置</span><span class="sxs-lookup"><span data-stu-id="d5c8f-107">Corrective Action</span></span>  
 <span data-ttu-id="d5c8f-108">**ED**と **!!** への参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="d5c8f-108">Remove references to the **ED** and **!!**</span></span> <span data-ttu-id="d5c8f-109">スクリプトからのコマンドです。</span><span class="sxs-lookup"><span data-stu-id="d5c8f-109">commands from your scripts.</span></span>  
  
 <span data-ttu-id="d5c8f-110">**ED**と **!!** を使用する場合は、</span><span class="sxs-lookup"><span data-stu-id="d5c8f-110">If you want to use the **ED** and **!!**</span></span> <span data-ttu-id="d5c8f-111">コマンドで、 **osql**の代わりに**sqlcmd**ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d5c8f-111">commands, use the **sqlcmd** utility instead of **osql**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c8f-112">参照</span><span class="sxs-lookup"><span data-stu-id="d5c8f-112">See Also</span></span>  
 <span data-ttu-id="d5c8f-113">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="d5c8f-113">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="d5c8f-114">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="d5c8f-114">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
