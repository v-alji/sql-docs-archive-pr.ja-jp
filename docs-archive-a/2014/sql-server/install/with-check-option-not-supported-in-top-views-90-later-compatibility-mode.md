---
title: WITH CHECK OPTION は、90以降の互換性モードで TOP を含むビューではサポートされていません。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ee7775c875e33f104341a1da39f5fe6c9326f284
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640347"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a><span data-ttu-id="051d5-102">互換性モード 90 以上では TOP を含むビューで WITH CHECK OPTION がサポートされない</span><span class="sxs-lookup"><span data-stu-id="051d5-102">WITH CHECK OPTION is not supported in views that contain TOP in 90 or later compatibility modes</span></span>
  <span data-ttu-id="051d5-103">ビューの SELECT ステートメントまたは参照先のビューで WITH CHECK OPTION と TOP 句を使用するビューを、アップグレード アドバイザーが検出しました。</span><span class="sxs-lookup"><span data-stu-id="051d5-103">Upgrade Advisor detected a view that uses the WITH CHECK OPTION and a TOP clause in the SELECT statement of the view or in a referenced view.</span></span> <span data-ttu-id="051d5-104">データベース互換性モードが 80 以下の場合、この方法で定義されたビューを使用してデータを変更することはできますが、正しく実行されず、不正確な結果が生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="051d5-104">Views defined this way incorrectly allow data to be modified through the view and may produce inaccurate results when the database compatibility mode is set to 80 and earlier.</span></span> <span data-ttu-id="051d5-105">ビューまたは参照先のビューで TOP 句を使用し、データベース互換性モードが 90 以上に設定されている場合、WITH CHECK OPTION を使用するビューからデータの挿入や更新を行うことはできません。</span><span class="sxs-lookup"><span data-stu-id="051d5-105">Data cannot be inserted or updated through a view that uses WITH CHECK OPTION when the view or a referenced view uses the TOP clause and the database compatibility mode is set to 90 or later.</span></span>  
  
## <a name="component"></a><span data-ttu-id="051d5-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="051d5-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a><span data-ttu-id="051d5-107">修正措置</span><span class="sxs-lookup"><span data-stu-id="051d5-107">Corrective Action</span></span>  
 <span data-ttu-id="051d5-108">アップグレードすると、ユーザー データベースでは互換性モードが維持されます。</span><span class="sxs-lookup"><span data-stu-id="051d5-108">When you upgrade, user databases maintain their compatibility mode.</span></span> <span data-ttu-id="051d5-109">ビューからのデータ変更が必要な場合は、データベース互換性モードを 100 以上に変更する前に WITH CHECK OPTION と TOP の両方を使用するビューを変更してください。</span><span class="sxs-lookup"><span data-stu-id="051d5-109">Before you change the database compatibility mode to 100 or later, modify views that use both WITH CHECK OPTION and TOP if data modification through the view is required.</span></span> <span data-ttu-id="051d5-110">詳細については、「 [sp_dbcmptlevel &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="051d5-110">For more information, see [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="051d5-111">参照</span><span class="sxs-lookup"><span data-stu-id="051d5-111">See Also</span></span>  
 <span data-ttu-id="051d5-112">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="051d5-112">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="051d5-113">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="051d5-113">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
