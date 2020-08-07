---
title: SERVERPROPERTY は SQL Server 2005 | で LCID プロパティの正しい結果を返しますMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SERVERPROPERTY function
ms.assetid: 833a2fc9-b480-4697-aa7b-9677e78ee0b4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ebb125a86e6e30f2c3638004593da7657f02f1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715970"
---
# <a name="serverproperty-returns-correct-result-for-lcid-property-in-sql-server-2005"></a><span data-ttu-id="9c4d4-102">SQL Server 2005 では SERVERPROPERTY が LCID プロパティの正しい結果を返す</span><span class="sxs-lookup"><span data-stu-id="9c4d4-102">SERVERPROPERTY returns correct result for LCID property in SQL Server 2005</span></span>
  <span data-ttu-id="9c4d4-103">SERVERPROPERTY('LCID') がバイナリ照合順序のサーバーで実行されると、この関数はサーバーの照合順序に対応した Windows ロケール識別子 (LCID) を返します。</span><span class="sxs-lookup"><span data-stu-id="9c4d4-103">When SERVERPROPERTY('LCID') is run on binary collation servers, the function returns the Windows locale identifier (LCID) that corresponds to the collation of the server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9c4d4-104">SERVERPROPERTY ('LCID') への参照を含むバッチ ファイルとトレース ファイルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の他のインスタンスで実行される場合、他のインスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスと同じ照合順序である場合に限って、この動作変更があることが検出されます。</span><span class="sxs-lookup"><span data-stu-id="9c4d4-104">For batch and trace files that contain references to SERVERPROPERTY ('LCID') and are run on other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Upgrade Advisor will detect this behavior change only if the other instances have the same collation as the current instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="9c4d4-105">修正措置</span><span class="sxs-lookup"><span data-stu-id="9c4d4-105">Corrective Action</span></span>  
 <span data-ttu-id="9c4d4-106">SERVERPROPERTY('LCID') がサーバーの照合順序に対応する Windows LCID を返すようにアプリケーションを修正してください。</span><span class="sxs-lookup"><span data-stu-id="9c4d4-106">Modify applications to expect SERVERPROPERTY('LCID') to return the Windows LCID that corresponds to the collation of the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4d4-107">参照</span><span class="sxs-lookup"><span data-stu-id="9c4d4-107">See Also</span></span>  
 <span data-ttu-id="9c4d4-108">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="9c4d4-108">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="9c4d4-109">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="9c4d4-109">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
