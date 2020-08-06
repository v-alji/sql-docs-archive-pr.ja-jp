---
title: allow updates サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d7e3ede317509a2044be90635db46e30a932af66
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642309"
---
# <a name="allow-updates-server-configuration-option"></a><span data-ttu-id="06973-102">allow updates サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="06973-102">allow updates Server Configuration Option</span></span>
  <span data-ttu-id="06973-103">このオプションは **sp_configure** ストアド プロシージャにまだ含まれていますが、その機能を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="06973-103">This option is still present in the **sp_configure** stored procedure, although its functionality is unavailable in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="06973-104">設定しても何の影響もありません。</span><span class="sxs-lookup"><span data-stu-id="06973-104">The setting has no effect.</span></span> <span data-ttu-id="06973-105">システム テーブルの直接更新はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="06973-105">Direct updates to the system tables are not supported.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 <span data-ttu-id="06973-106">**allow updates** オプションを変更すると、RECONFIGURE ステートメントが失敗します。</span><span class="sxs-lookup"><span data-stu-id="06973-106">Changing the **allow updates** option will cause the RECONFIGURE statement to fail.</span></span> <span data-ttu-id="06973-107">**allow updates** オプションへの変更は、すべてのスクリプトから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06973-107">Changes to the **allow updates** option should be removed from all scripts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06973-108">参照</span><span class="sxs-lookup"><span data-stu-id="06973-108">See Also</span></span>  
 [<span data-ttu-id="06973-109">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="06973-109">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
