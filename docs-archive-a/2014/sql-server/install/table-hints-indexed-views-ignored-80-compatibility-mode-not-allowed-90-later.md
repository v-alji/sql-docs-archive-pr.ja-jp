---
title: インデックス付きビュー定義内のテーブルヒントは80互換性モードでは無視され、90モード以降では許可されません |。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- query hints [SQL Server]
- indexed views [SQL Server], query hints
ms.assetid: 405dfcff-a3a6-4e6d-a53a-ed77bbacdd13
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: cf3cb2b06dc477d93c8fd42312b4835ded42afb4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720799"
---
# <a name="table-hints-in-indexed-view-definitions-are-ignored-in-80-compatibility-mode-and-are-not-allowed-in-90-mode-or-later"></a><span data-ttu-id="ec575-102">インデックス付きビュー定義のテーブル ヒントが互換性モード 80 では無視され、互換性モード 90 以上では許可されない</span><span class="sxs-lookup"><span data-stu-id="ec575-102">Table hints in indexed view definitions are ignored in 80 compatibility mode and are not allowed in 90 mode or later</span></span>
  <span data-ttu-id="ec575-103">互換性モード 90 以上では、インデックス付きビューの定義のテーブル ヒントは使用できません。</span><span class="sxs-lookup"><span data-stu-id="ec575-103">Table hints in the definitions of indexed views are not permitted in the compatibility mode of 90 or later.</span></span> <span data-ttu-id="ec575-104">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「インデックス付きビューのデザイン」、「インデックス付きビューの作成」、および「クエリ ヒント ([!INCLUDE[tsql](../../includes/tsql-md.md)])」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec575-104">For more information, see the following topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online: "Designing Indexed Views," "Creating Indexed Views," and "Query Hint ([!INCLUDE[tsql](../../includes/tsql-md.md)])."</span></span>  
  
## <a name="component"></a><span data-ttu-id="ec575-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ec575-105">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="ec575-106">修正措置</span><span class="sxs-lookup"><span data-stu-id="ec575-106">Corrective Action</span></span>  
 <span data-ttu-id="ec575-107">テーブル ヒントは、インデックス付きビューの定義から削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec575-107">Table hints must be removed from the definitions of indexed views.</span></span> <span data-ttu-id="ec575-108">どの互換性モードを使用しているかにかかわらず、アプリケーションをテストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ec575-108">Regardless of which compatibility mode is used, we recommend that you test the application.</span></span> <span data-ttu-id="ec575-109">アプリケーションをテストすることによって、インデックス付きビューがクエリに一致した場合など、インデックス付きビューが作成、更新、アクセスされたときに想定どおりに実行されるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ec575-109">By testing the application, you can make sure it performs as expected when indexed views are created, updated, and accessed, including when indexed views are matched to queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec575-110">参照</span><span class="sxs-lookup"><span data-stu-id="ec575-110">See Also</span></span>  
 <span data-ttu-id="ec575-111">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="ec575-111">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="ec575-112">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="ec575-112">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
