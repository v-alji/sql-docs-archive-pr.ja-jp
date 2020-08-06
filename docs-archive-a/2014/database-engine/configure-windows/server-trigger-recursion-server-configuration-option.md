---
title: server trigger recursion サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- recursive triggers [SQL Server]
- triggers [SQL Server], recursive
- server trigger recursion option
ms.assetid: da4c25f5-d04c-4951-a3db-409e71a1b468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 23a4997bd1a6f8b2c04af34d5cdc3229575901a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740411"
---
# <a name="server-trigger-recursion-server-configuration-option"></a><span data-ttu-id="0258a-102">server trigger recursion サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="0258a-102">server trigger recursion Server Configuration Option</span></span>
  <span data-ttu-id="0258a-103">サーバーレベルのトリガーを再帰的に起動できるようにするかどうかを指定するには、 **server trigger recursion** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="0258a-103">Use the **server trigger recursion** option to specify whether to allow server-level triggers to fire recursively.</span></span> <span data-ttu-id="0258a-104">このオプションを 1 (ON) に設定すると、サーバーレベルのトリガーを再帰的に起動できます。</span><span class="sxs-lookup"><span data-stu-id="0258a-104">When this option is set to 1 (ON), server-level triggers will be allowed to fire recursively.</span></span> <span data-ttu-id="0258a-105">このオプションを 0 (OFF) に設定すると、サーバーレベルのトリガーは再帰的に起動できません。</span><span class="sxs-lookup"><span data-stu-id="0258a-105">When set to 0 (OFF), server-level triggers cannot be fired recursively.</span></span> <span data-ttu-id="0258a-106">server trigger recursion オプションが 0 (OFF) の場合は、直接再帰のみが回避されます</span><span class="sxs-lookup"><span data-stu-id="0258a-106">Only direct recursion is prevented when the server trigger recursion option is set to 0 (OFF).</span></span> <span data-ttu-id="0258a-107">(間接再帰を無効にするには、**nested triggers** オプションを 0 に設定します)。このオプションの既定値は 1 (ON) です。</span><span class="sxs-lookup"><span data-stu-id="0258a-107">(To disable indirect recursion, set the **nested triggers** option to 0.) The default value for this option is 1 (ON).</span></span> <span data-ttu-id="0258a-108">この設定はすぐに適用されます。サーバーを再起動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0258a-108">The setting takes effect immediately (without a server restart).</span></span>  
  
 <span data-ttu-id="0258a-109">詳しくは、「 [入れ子になったトリガーの作成](../../relational-databases/triggers/create-nested-triggers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0258a-109">For more information, see [Create Nested Triggers](../../relational-databases/triggers/create-nested-triggers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0258a-110">参照</span><span class="sxs-lookup"><span data-stu-id="0258a-110">See Also</span></span>  
 <span data-ttu-id="0258a-111">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0258a-111">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="0258a-112">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0258a-112">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="0258a-113">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0258a-113">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
