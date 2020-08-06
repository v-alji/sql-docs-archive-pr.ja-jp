---
title: 90以降の互換性モードでは、FOR BROWSE はビューで許可されていません。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], FOR BROWSE clause
- FOR BROWSE clause
ms.assetid: 8f49b1c1-d877-4c46-b988-f8cdd8ac0925
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 251e0ae2ff6f19dfcff3b0f8056f6697c1bfc40d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643138"
---
# <a name="for-browse-is-not-allowed-in-views-in-90-or-later-compatibility-modes"></a><span data-ttu-id="26337-102">互換性モードが 90 以上の場合、FOR BROWSE はビューで使用できません</span><span class="sxs-lookup"><span data-stu-id="26337-102">FOR BROWSE is not allowed in views in 90 or later compatibility modes</span></span>
  <span data-ttu-id="26337-103">アップグレード アドバイザーは、ビューで FOR BROWSE 句が使用されているのを検出しました。</span><span class="sxs-lookup"><span data-stu-id="26337-103">Upgrade Advisor detected the use of the FOR BROWSE clause in a view.</span></span> <span data-ttu-id="26337-104">データベースの互換性モードが 80 に設定されている場合は、FOR BROWSE 句をビューで使用できます (ただし、無視されます)。</span><span class="sxs-lookup"><span data-stu-id="26337-104">The FOR BROWSE clause is allowed (and ignored) in views when the database compatibility mode is set to 80.</span></span> <span data-ttu-id="26337-105">FOR BROWSE 句は、データベース互換性モードが 90 以上に設定されている場合、ビューで使用できません。</span><span class="sxs-lookup"><span data-stu-id="26337-105">The FOR BROWSE clause is not allowed in views when the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="26337-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="26337-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="26337-107">修正措置</span><span class="sxs-lookup"><span data-stu-id="26337-107">Corrective Action</span></span>  
 <span data-ttu-id="26337-108">アップグレードすると、ユーザー データベースでは互換性モードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="26337-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="26337-109">データベース互換性モードを 90 以上に変更する前に、ビュー定義から FOR BROWSE 句を削除します。</span><span class="sxs-lookup"><span data-stu-id="26337-109">Before you change the database compatibility mode to 90 or later, remove the FOR BROWSE clause from view definitions.</span></span> <span data-ttu-id="26337-110">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「sp_dbcmptlevel」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26337-110">For more information, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26337-111">参照</span><span class="sxs-lookup"><span data-stu-id="26337-111">See Also</span></span>  
 <span data-ttu-id="26337-112">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="26337-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="26337-113">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="26337-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
