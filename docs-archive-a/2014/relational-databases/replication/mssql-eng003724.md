---
title: MSSQL_ENG003724 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG003724 error
ms.assetid: 10cb119d-92df-4124-b85d-cd2f2666c99c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: dbfb68575c5ffa73276b3bbe1643381c3f0cc412
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741798"
---
# <a name="mssql_eng003724"></a><span data-ttu-id="8aa6e-102">MSSQL_ENG003724</span><span class="sxs-lookup"><span data-stu-id="8aa6e-102">MSSQL_ENG003724</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8aa6e-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="8aa6e-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8aa6e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8aa6e-104">Product Name</span></span>|<span data-ttu-id="8aa6e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8aa6e-105">SQL Server</span></span>|  
|<span data-ttu-id="8aa6e-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8aa6e-106">Event ID</span></span>|<span data-ttu-id="8aa6e-107">3724</span><span class="sxs-lookup"><span data-stu-id="8aa6e-107">3724</span></span>|  
|<span data-ttu-id="8aa6e-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8aa6e-108">Event Source</span></span>|<span data-ttu-id="8aa6e-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8aa6e-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8aa6e-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8aa6e-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8aa6e-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8aa6e-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8aa6e-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8aa6e-112">Message Text</span></span>|<span data-ttu-id="8aa6e-113">%S_MSG '%.\*ls' を %S_MSG できません。レプリケーションに使用されています。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-113">Cannot %S_MSG the %S_MSG '%.\*ls' because it is being used for replication.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8aa6e-114">説明</span><span class="sxs-lookup"><span data-stu-id="8aa6e-114">Explanation</span></span>  
 <span data-ttu-id="8aa6e-115">データベース内のオブジェクトがレプリケートされると、システム テーブル **sysarticles** (スナップショット パブリケーションまたはトランザクション パブリケーションの場合) または **sysmergearticles** (マージ パブリケーションの場合) に、レプリケート済みのマークが付けられています。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-115">When objects in a database are replicated, they are marked as replicated in the system table **sysarticles** (for snapshot and transactional publications) or **sysmergearticles** (for merge publications).</span></span> <span data-ttu-id="8aa6e-116">レプリケート済みのオブジェクトを削除しようとした場合に、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-116">If you attempt drop a replicated object, this error is raised.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8aa6e-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8aa6e-117">User Action</span></span>  
 <span data-ttu-id="8aa6e-118">データベース オブジェクトを削除する前に、そのオブジェクトがレプリケートされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-118">Ensure the database object is not replicated before attempting to drop it.</span></span> <span data-ttu-id="8aa6e-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-119">For example:</span></span>  
  
-   <span data-ttu-id="8aa6e-120">パブリケーション データベースでエラーが発生した場合、オブジェクトを削除する前にパブリケーションからアーティクルを削除します。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-120">If the error occurs in the publication database, drop the article from the publication before dropping the object.</span></span> <span data-ttu-id="8aa6e-121">詳細については、「[Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md)」 (既存のパブリケーションでのアーティクルの追加および削除) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-121">For more information, see [Add Articles to and Drop Articles from Existing Publications](publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
-   <span data-ttu-id="8aa6e-122">サブスクリプション データベースでエラーが発生した場合、オブジェクトを削除する前にそのサブスクリプションを削除します。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-122">If the error occurs in the subscription database, drop the subscription before dropping the object.</span></span> <span data-ttu-id="8aa6e-123">詳細については、「[パブリケーションのサブスクライブ](subscribe-to-publications.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-123">For more information, see [Subscribe to Publications](subscribe-to-publications.md).</span></span> <span data-ttu-id="8aa6e-124">トランザクション パブリケーションに対するサブスクリプションの場合、パブリケーション全体を削除するのではなく、個々のアーティクルに対するサブスクリプションを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-124">For subscriptions to transactional publications, it is possible to drop the subscription to an individual article rather than the entire publication.</span></span> <span data-ttu-id="8aa6e-125">詳細については、「[sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-125">For more information, see [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql).</span></span>  
  
 <span data-ttu-id="8aa6e-126">レプリケートされていないデータベースでこのエラーが発生した場合は、[sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) を実行して、データベース内のオブジェクトにレプリケート済みのマークが付かないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="8aa6e-126">If this error occurs in a database that is not replicated, execute [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to ensure objects in the database are not marked as replicated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa6e-127">参照</span><span class="sxs-lookup"><span data-stu-id="8aa6e-127">See Also</span></span>  
 [<span data-ttu-id="8aa6e-128">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="8aa6e-128">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  
