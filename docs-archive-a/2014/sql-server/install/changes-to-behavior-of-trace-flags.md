---
title: トレースフラグの動作の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11d71e8401f6b870aaeb3f64f4145b509e3a3fe0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640477"
---
# <a name="changes-to-behavior-of-trace-flags"></a><span data-ttu-id="0d590-102">トレース フラグの動作が変更された</span><span class="sxs-lookup"><span data-stu-id="0d590-102">Changes to behavior of trace flags</span></span>
  <span data-ttu-id="0d590-103">あるセッションによって設定されたグローバル トレース フラグは他のセッションですぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="0d590-103">Global trace flags set by a session take effect in other sessions immediately.</span></span> <span data-ttu-id="0d590-104">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] には、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の一部のトレース フラグが存在しません。</span><span class="sxs-lookup"><span data-stu-id="0d590-104">Some trace flags from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] do not exist in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="0d590-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0d590-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="0d590-106">説明</span><span class="sxs-lookup"><span data-stu-id="0d590-106">Description</span></span>  
 <span data-ttu-id="0d590-107">アップグレードする前に、すべてのトレース フラグを無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0d590-107">We recommend that you disable all trace flags before you upgrade.</span></span> <span data-ttu-id="0d590-108">データベースの可用性モードまたは復旧モードを変更するトレースフラグにより、が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスを正常にアップグレードできない場合があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="0d590-108">Trace flags that modify the database availability or recovery modes might prevent the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] from successfully upgrading your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="0d590-109">トレース フラグが必要になり、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でも有効であることを確認した後、トレース フラグを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="0d590-109">You can enable the trace flags after you verify that the trace flags are required and are still valid in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="0d590-110">トレース フラグを再び有効にするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで追加テストを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d590-110">If you must re-enable trace flags, you should perform additional tests on your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="0d590-111">は、グローバル トレース フラグとセッション レベルのトレース フラグをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0d590-111">supports global and session level trace flags.</span></span> <span data-ttu-id="0d590-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] の場合、DBCC TRACEON コマンドに引数 (-1) を追加することによって、ローカル、グローバルのいずれでもトレース フラグを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0d590-112">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], trace flags can be specified as either local or global by using an additional argument (-1) in the DBCC TRACEON command.</span></span> <span data-ttu-id="0d590-113">この引数を指定しない場合、既定値はローカルになります。</span><span class="sxs-lookup"><span data-stu-id="0d590-113">If this argument is not specified, the default value is local.</span></span>  
  
 <span data-ttu-id="0d590-114">また、[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では、セッション A で設定されたトレース フラグは、既に存在するセッション B では自動的に有効になりません。代わりに、セッション B に初めてトレース フラグが設定された後にのみ有効になります。この動作は [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] では非決定的であり、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは決定的です。 以降のバージョンでは、セッション A で設定されたトレース フラグは、他の同時セッションに直ちに設定されます。</span><span class="sxs-lookup"><span data-stu-id="0d590-114">Also, in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], a trace flag set in session A does not automatically take effect in an already existing session B. Instead, this trace flag takes effect only after the first time any trace flag is set in session B. This behavior is nondeterministic in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] and is deterministic in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, where global trace flags set in session A are set immediately in other concurrent sessions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d590-115">参照</span><span class="sxs-lookup"><span data-stu-id="0d590-115">See Also</span></span>  
 <span data-ttu-id="0d590-116">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="0d590-116">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="0d590-117">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="0d590-117">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
