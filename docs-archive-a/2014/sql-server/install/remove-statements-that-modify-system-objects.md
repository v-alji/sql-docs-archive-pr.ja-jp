---
title: システムオブジェクトを変更するステートメントを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742809"
---
# <a name="remove-statements-that-modify-system-objects"></a><span data-ttu-id="6063f-102">システム オブジェクトを変更するステートメントを削除する</span><span class="sxs-lookup"><span data-stu-id="6063f-102">Remove statements that modify system objects</span></span>
  <span data-ttu-id="6063f-103">アップグレード アドバイザーによって、システム カタログを更新するステートメントが検出されました。</span><span class="sxs-lookup"><span data-stu-id="6063f-103">Upgrade Advisor detected statements that update the system catalog.</span></span> <span data-ttu-id="6063f-104">システム カタログを直接更新できません。</span><span class="sxs-lookup"><span data-stu-id="6063f-104">Direct system catalog updates are not allowed.</span></span> <span data-ttu-id="6063f-105">ドキュメントに記載されている公式の API を使用するように SQL スクリプトを変更してください。</span><span class="sxs-lookup"><span data-stu-id="6063f-105">Modify your SQL scripts to use official and documented APIs.</span></span>  
  
## <a name="component"></a><span data-ttu-id="6063f-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6063f-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="6063f-107">説明</span><span class="sxs-lookup"><span data-stu-id="6063f-107">Description</span></span>  
 <span data-ttu-id="6063f-108">システム カタログを直接更新できません。</span><span class="sxs-lookup"><span data-stu-id="6063f-108">Direct system catalog updates are not allowed.</span></span> <span data-ttu-id="6063f-109">システム カタログを直接更新しようとすると、次のエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6063f-109">Any attempt to do so will generate the following error:</span></span>  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a><span data-ttu-id="6063f-110">修正措置</span><span class="sxs-lookup"><span data-stu-id="6063f-110">Corrective Action</span></span>  
 <span data-ttu-id="6063f-111">ドキュメントに記載されている公式の API を使用するように SQL スクリプトを変更してください。</span><span class="sxs-lookup"><span data-stu-id="6063f-111">Modify your SQL scripts to use official and documented APIs.</span></span> <span data-ttu-id="6063f-112">たとえば、 **sysdatabases**システムテーブルで UPDATE ステートメントを実行するのではなく、ALTER database *database_name* SET 緊を使用します。</span><span class="sxs-lookup"><span data-stu-id="6063f-112">For example, use ALTER DATABASE *database_name* SET EMERGENCY instead of running an UPDATE statement on the **sysdatabases** system table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6063f-113">参照</span><span class="sxs-lookup"><span data-stu-id="6063f-113">See Also</span></span>  
 <span data-ttu-id="6063f-114">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="6063f-114">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="6063f-115">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="6063f-115">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
