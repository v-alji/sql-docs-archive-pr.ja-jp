---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b202b28eabe1feb1ed180bda0d58d2e84c7d10d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631824"
---
# <a name="mssql_eng004929"></a><span data-ttu-id="7fa16-102">MSSQL_ENG004929</span><span class="sxs-lookup"><span data-stu-id="7fa16-102">MSSQL_ENG004929</span></span>
    
## <a name="message-details"></a><span data-ttu-id="7fa16-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="7fa16-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7fa16-104">製品名</span><span class="sxs-lookup"><span data-stu-id="7fa16-104">Product Name</span></span>|<span data-ttu-id="7fa16-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="7fa16-105">SQL Server</span></span>|  
|<span data-ttu-id="7fa16-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7fa16-106">Event ID</span></span>|<span data-ttu-id="7fa16-107">4929</span><span class="sxs-lookup"><span data-stu-id="7fa16-107">4929</span></span>|  
|<span data-ttu-id="7fa16-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="7fa16-108">Event Source</span></span>|<span data-ttu-id="7fa16-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7fa16-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7fa16-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7fa16-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="7fa16-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="7fa16-111">Symbolic Name</span></span>||  
|<span data-ttu-id="7fa16-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="7fa16-112">Message Text</span></span>|<span data-ttu-id="7fa16-113">%S_MSG '%.\*ls' は、レプリケーションでパブリッシュされているので変更できません。</span><span class="sxs-lookup"><span data-stu-id="7fa16-113">Cannot alter the %S_MSG '%.\*ls' because it is being published for replication.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7fa16-114">説明</span><span class="sxs-lookup"><span data-stu-id="7fa16-114">Explanation</span></span>  
 <span data-ttu-id="7fa16-115">通常、このエラーは、トランザクション レプリケーションでパブリッシュされているテーブル上の主キーの制約を削除しようとすると発生します。</span><span class="sxs-lookup"><span data-stu-id="7fa16-115">This error typically occurs if you attempt to drop the primary key constraint on a table that is published for transactional replication.</span></span> <span data-ttu-id="7fa16-116">トランザクション レプリケーションではパブリッシュされたテーブルごとに 1 つの主キーが必要であるため、制約は削除できません。</span><span class="sxs-lookup"><span data-stu-id="7fa16-116">Transactional replication requires a primary key for each published table; therefore the constraint cannot be dropped.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7fa16-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="7fa16-117">User Action</span></span>  
 <span data-ttu-id="7fa16-118">制約を削除するには、最初にテーブルに関連付けられているアーティクルを削除します。</span><span class="sxs-lookup"><span data-stu-id="7fa16-118">To drop the constraint, first drop the article associated with the table.</span></span> <span data-ttu-id="7fa16-119">詳細については、「[Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md)」 (既存のパブリケーションでのアーティクルの追加および削除) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fa16-119">For more information, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span> <span data-ttu-id="7fa16-120">レプリケートされていないデータベースでこのエラーが発生した場合は、[sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行して、データベース内のオブジェクトにレプリケート済みのマークが付かないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="7fa16-120">If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to ensure objects in the database are not marked as replicated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa16-121">参照</span><span class="sxs-lookup"><span data-stu-id="7fa16-121">See Also</span></span>  
 [<span data-ttu-id="7fa16-122">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="7fa16-122">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
