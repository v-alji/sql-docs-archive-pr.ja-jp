---
title: in-doubt xact resolution サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6b8db57ef2a4ee85d65e8c25de28ff7ada7994e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713505"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a><span data-ttu-id="c68b3-102">in-doubt xact resolution サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="c68b3-102">in-doubt xact resolution Server Configuration Option</span></span>
  <span data-ttu-id="c68b3-103">**in-doubt xact resolution** オプションは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) で解決できないトランザクションの既定の結果を制御する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c68b3-103">Use the **in-doubt xact resolution** option to control the default outcome of transactions that the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) is unable to resolve.</span></span> <span data-ttu-id="c68b3-104">トランザクションを解決できない原因は、復旧時の MS DTC のダウン タイムまたは状態が不明なトランザクション結果に関連している場合があります。</span><span class="sxs-lookup"><span data-stu-id="c68b3-104">Inability to resolve transactions may be related to the MS DTC down time or an unknown transaction outcome at the time of recovery.</span></span>  
  
 <span data-ttu-id="c68b3-105">次の表は、状態が不明なトランザクションの解決について考えられる結果の値を示しています。</span><span class="sxs-lookup"><span data-stu-id="c68b3-105">The following table lists the possible outcome values for resolving an in-doubt transaction.</span></span>  
  
|<span data-ttu-id="c68b3-106">結果の値</span><span class="sxs-lookup"><span data-stu-id="c68b3-106">Outcome value</span></span>|<span data-ttu-id="c68b3-107">説明</span><span class="sxs-lookup"><span data-stu-id="c68b3-107">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="c68b3-108">0</span><span class="sxs-lookup"><span data-stu-id="c68b3-108">0</span></span>|<span data-ttu-id="c68b3-109">推測しません。</span><span class="sxs-lookup"><span data-stu-id="c68b3-109">No presumption.</span></span> <span data-ttu-id="c68b3-110">状態が不明なトランザクションを MS DTC で解決できない場合、復旧は失敗します。</span><span class="sxs-lookup"><span data-stu-id="c68b3-110">Recovery fails if MS DTC cannot resolve any in-doubt transactions.</span></span>|  
|<span data-ttu-id="c68b3-111">1</span><span class="sxs-lookup"><span data-stu-id="c68b3-111">1</span></span>|<span data-ttu-id="c68b3-112">コミットを推測します。</span><span class="sxs-lookup"><span data-stu-id="c68b3-112">Presume commit.</span></span> <span data-ttu-id="c68b3-113">MS DTC の状態が不明なトランザクションは、コミットされたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="c68b3-113">Any MS DTC in-doubt transactions are presumed to have committed.</span></span>|  
|<span data-ttu-id="c68b3-114">2</span><span class="sxs-lookup"><span data-stu-id="c68b3-114">2</span></span>|<span data-ttu-id="c68b3-115">中断を推測します。</span><span class="sxs-lookup"><span data-stu-id="c68b3-115">Presume abort.</span></span> <span data-ttu-id="c68b3-116">MS DTC の状態が不明なトランザクションは、中断されたと見なされます。</span><span class="sxs-lookup"><span data-stu-id="c68b3-116">Any MS DTC in-doubt transactions are presumed to have aborted.</span></span>|  
  
 <span data-ttu-id="c68b3-117">次の例のように、長時間にわたるダウン タイムの可能性を最低限に抑えるために、管理者はコミットまたは中断を推測するようにこのオプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="c68b3-117">To minimize the possibility of extended down time, an administrator might choose to configure this option either to presume commit or presume abort, as shown in the following example.</span></span>  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -- presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="c68b3-118">また、次の例のように、DTC エラーを認識するために、既定値 (推測なし) のままにして復旧を失敗させることができます。</span><span class="sxs-lookup"><span data-stu-id="c68b3-118">Alternatively, the administrator might want to leave the default (no presumption) and allow recovery to fail in order to be made aware of a DTC failure, as shown in the following example.</span></span>  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -- presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE -- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 -- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 <span data-ttu-id="c68b3-119">**in-doubt xact resolution** は拡張オプションです。</span><span class="sxs-lookup"><span data-stu-id="c68b3-119">The **in-doubt xact resolution** option is an advanced option.</span></span> <span data-ttu-id="c68b3-120">**sp_configure** システム ストアド プロシージャを使用して **in-doubt xact resolution** の設定を変更するには、 **show advanced options** を 1 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c68b3-120">If you are using the **sp_configure** system stored procedure to change the setting, you can change **in-doubt xact resolution** only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="c68b3-121">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="c68b3-121">The setting takes effect immediately without a server restart.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c68b3-122">分散トランザクションに関係するすべての [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで、このオプションを同じように構成すると、データの不整合を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="c68b3-122">Consistent configuration of this option across all [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances involved in any distributed transactions will help avoid data inconsistencies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68b3-123">参照</span><span class="sxs-lookup"><span data-stu-id="c68b3-123">See Also</span></span>  
 <span data-ttu-id="c68b3-124">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c68b3-124">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="c68b3-125">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c68b3-125">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="c68b3-126">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c68b3-126">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
