---
title: 予約されたキーワード | に続くコロンを削除します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- reserved keywords
ms.assetid: 4f23f7e4-7b4d-4e19-86c9-7527bb8b107d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fc6882439338509a3c716129d9504f209ab1e555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742813"
---
# <a name="remove-colon-following-reserved-keyword"></a><span data-ttu-id="780b6-102">予約されたキーワードの後のコロンを削除する</span><span class="sxs-lookup"><span data-stu-id="780b6-102">Remove colon following reserved keyword</span></span>
  <span data-ttu-id="780b6-103">アップグレード アドバイザーは、予約されたキーワードの後にコロン (:) が含まれたスクリプトを検出しました。</span><span class="sxs-lookup"><span data-stu-id="780b6-103">The Upgrade Advisor detected a script that contains a colon (:) following a reserved keyword.</span></span> <span data-ttu-id="780b6-104">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この構文は無視され、ステートメントが正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="780b6-104">In earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this syntax is ignored and the statements execute successfully.</span></span> <span data-ttu-id="780b6-105">現在、データベース互換性モードが 100 以上に設定されていると、この構文が原因でステートメントが失敗します。</span><span class="sxs-lookup"><span data-stu-id="780b6-105">Now, this syntax causes the statement to fail when the database compatibility mode is set to 100 or later.</span></span>  
  
 <span data-ttu-id="780b6-106">ユーザー データベースでは、互換性モードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="780b6-106">User databases maintain their compatibility mode.</span></span>  
  
## <a name="component"></a><span data-ttu-id="780b6-107">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="780b6-107">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="780b6-108">修正措置</span><span class="sxs-lookup"><span data-stu-id="780b6-108">Corrective Action</span></span>  
 <span data-ttu-id="780b6-109">データベース互換性モードを 100 以上に変更する前に、スクリプト内の予約されたキーワードの後にあるコロンを削除してください。</span><span class="sxs-lookup"><span data-stu-id="780b6-109">Before you change the database compatibility mode to 100 or later, modify your scripts by removing colons that follow reserved keywords.</span></span> <span data-ttu-id="780b6-110">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「sp_dbcmptlevel」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="780b6-110">For more information, see "sp_dbcmptlevel" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780b6-111">参照</span><span class="sxs-lookup"><span data-stu-id="780b6-111">See Also</span></span>  
 <span data-ttu-id="780b6-112">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="780b6-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="780b6-113">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="780b6-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
