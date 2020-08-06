---
title: disallow results from triggers サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- triggers [SQL Server], result sets
- result sets [SQL Server], triggers
- disallow results from triggers option
ms.assetid: 47149073-307d-47a5-b7d2-66a737d3231d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f162a6e06706561d861bfc54a1ae4027f2c3466e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711026"
---
# <a name="disallow-results-from-triggers-server-configuration-option"></a><span data-ttu-id="667f9-102">disallow results from triggers サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="667f9-102">disallow results from triggers Server Configuration Option</span></span>
  <span data-ttu-id="667f9-103">**disallow results from triggers** オプションは、トリガーによって結果セットを返すかどうかを制御する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="667f9-103">Use the **disallow results from triggers** option to control whether triggers return result sets.</span></span> <span data-ttu-id="667f9-104">結果セットを返すトリガーは、それと連動するように設計されていないアプリケーションでは予期しない動作を起こすことがあります。</span><span class="sxs-lookup"><span data-stu-id="667f9-104">Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]<span data-ttu-id="667f9-105">この値は 1 に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="667f9-105">We recommend that you set this value to 1.</span></span>  
  
 <span data-ttu-id="667f9-106">1 に設定すると、 **disallow results from triggers** オプションが ON になります。</span><span class="sxs-lookup"><span data-stu-id="667f9-106">When set to 1, the **disallow results from triggers** option is set to ON.</span></span> <span data-ttu-id="667f9-107">このオプションの既定値は 0 (OFF) です。</span><span class="sxs-lookup"><span data-stu-id="667f9-107">The default setting for this option is 0 (OFF).</span></span> <span data-ttu-id="667f9-108">このオプションを 1 (ON) に設定した場合は、トリガーによって結果セットを返そうとするとエラーになり、次のエラー メッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="667f9-108">If this option is set to 1 (ON), any attempt by a trigger to return a result set fails, and the user receives the following error message:</span></span>  
  
 <span data-ttu-id="667f9-109">"メッセージ 524、レベル 16、状態 1、プロシージャ \<Procedure Name>、行 \<Line#></span><span class="sxs-lookup"><span data-stu-id="667f9-109">"Msg 524, Level 16, State 1, Procedure \<Procedure Name>, Line \<Line#></span></span>  
  
 <span data-ttu-id="667f9-110">"トリガーから結果セットが返されましたが、サーバー オプション 'disallow_results_from_triggers' は true です。"</span><span class="sxs-lookup"><span data-stu-id="667f9-110">"A trigger returned a resultset and the server option 'disallow_results_from_triggers' is true."</span></span>  
  
 <span data-ttu-id="667f9-111">**disallow results from triggers** オプションは [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス レベルで適用され、インスタンス内のすべての既存のトリガーの動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="667f9-111">The **disallow results from triggers** option is applied at the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance level, and it will determine behavior for all existing triggers within the instance.</span></span>  
  
 <span data-ttu-id="667f9-112">**disallow results from triggers** は拡張オプションです。</span><span class="sxs-lookup"><span data-stu-id="667f9-112">The **disallow results from triggers** option is an advanced option.</span></span> <span data-ttu-id="667f9-113">**sp_configure** システム ストアド プロシージャを使用して disallow results from triggers の設定を変更するには、 **show advanced options** を 1 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="667f9-113">If you are using the **sp_configure** system stored procedure to change the setting, you can change disallow results from triggers only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="667f9-114">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="667f9-114">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="667f9-115">参照</span><span class="sxs-lookup"><span data-stu-id="667f9-115">See Also</span></span>  
 <span data-ttu-id="667f9-116">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="667f9-116">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="667f9-117">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="667f9-117">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="667f9-118">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="667f9-118">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
