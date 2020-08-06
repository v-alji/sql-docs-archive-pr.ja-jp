---
title: マージアーティクルのダミー更新の実行 (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07fa0f868b2c3f98496046b138424d7d3a2fa2fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736271"
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a><span data-ttu-id="3d2ea-102">マージ アーティクルのダミー更新の実行 (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="3d2ea-102">Perform a Dummy Update for a Merge Article (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="3d2ea-103">マージ レプリケーションではレプリケーション処理の中でトリガーを使用します。パブリッシュ済みのテーブルに更新が加えられると、更新トリガーが起動します。</span><span class="sxs-lookup"><span data-stu-id="3d2ea-103">Merge replication uses triggers as part of the replication process; when an update is made to published table, an update trigger fires.</span></span> <span data-ttu-id="3d2ea-104">WRITETEXT 操作や UPDATETEXT 操作の際など、トリガーを起動せずにデータを更新できる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="3d2ea-104">In some cases, data can be updated without the trigger firing, such as during the WRITETEXT and UPDATETEXT operations.</span></span> <span data-ttu-id="3d2ea-105">このような場合、ダミーの UPDATE ステートメントを明示的に追加して、変更をレプリケートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d2ea-105">In these cases, you need to add a dummy UPDATE statement explicitly to replicate the change.</span></span> <span data-ttu-id="3d2ea-106">ダミーの UPDATE ステートメントは、レプリケーション ストアド プロシージャを使用して追加できます。</span><span class="sxs-lookup"><span data-stu-id="3d2ea-106">You can add a dummy UPDATE statement using replication stored procedures.</span></span>  
  
### <a name="to-add-a-dummy-update-statement"></a><span data-ttu-id="3d2ea-107">ダミーの UPDATE ステートメントを追加するには</span><span class="sxs-lookup"><span data-stu-id="3d2ea-107">To add a dummy UPDATE statement</span></span>  
  
1.  <span data-ttu-id="3d2ea-108">ダミーの更新を必要とするマージ パブリッシュ済みテーブルの行に対して、操作 (たとえば UPDATETEXT など) を実行します。</span><span class="sxs-lookup"><span data-stu-id="3d2ea-108">Execute the operation (for example, UPDATETEXT) on a row in a merge published table  that requires a dummy update.</span></span>  
  
2.  <span data-ttu-id="3d2ea-109">サーバー (パブリッシャーまたはサブスクライバー) 上の変更が加えられたデータベースに対して、[sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="3d2ea-109">At the server (Publisher or Subscriber) on the database where the change was made, execute [sp_mergedummyupdate &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql).</span></span> <span data-ttu-id="3d2ea-110">変更が加えられたテーブル **@source_object** と、の変更された行の一意の識別子を指定し **@rowguid** ます。</span><span class="sxs-lookup"><span data-stu-id="3d2ea-110">Specify the table on which the change was made for **@source_object**, and the unique identifier of the changed row for **@rowguid**.</span></span>  
  
3.  <span data-ttu-id="3d2ea-111">サブスクリプションを同期して、変更された行をレプリケートします。</span><span class="sxs-lookup"><span data-stu-id="3d2ea-111">Synchronize the subscription to replicate the changed row.</span></span>  
  
  
