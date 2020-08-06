---
title: MSSQLSERVER_2527 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 900707634a016ecfd29f9f676e68b4d2f557ccea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634543"
---
# <a name="mssqlserver_2527"></a><span data-ttu-id="a4dd6-102">MSSQLSERVER_2527</span><span class="sxs-lookup"><span data-stu-id="a4dd6-102">MSSQLSERVER_2527</span></span>
    
## <a name="details"></a><span data-ttu-id="a4dd6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a4dd6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4dd6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a4dd6-104">Product Name</span></span>|<span data-ttu-id="a4dd6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a4dd6-105">SQL Server</span></span>|  
|<span data-ttu-id="a4dd6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a4dd6-106">Event ID</span></span>|<span data-ttu-id="a4dd6-107">2527</span><span class="sxs-lookup"><span data-stu-id="a4dd6-107">2527</span></span>|  
|<span data-ttu-id="a4dd6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a4dd6-108">Event Source</span></span>|<span data-ttu-id="a4dd6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a4dd6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a4dd6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a4dd6-110">Component</span></span>|<span data-ttu-id="a4dd6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a4dd6-111">SQLEngine</span></span>|  
|<span data-ttu-id="a4dd6-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a4dd6-112">Symbolic Name</span></span>|<span data-ttu-id="a4dd6-113">DBCC_INDEX_FILEGROUP_IS_OFFLINE</span><span class="sxs-lookup"><span data-stu-id="a4dd6-113">DBCC_INDEX_FILEGROUP_IS_OFFLINE</span></span>|  
|<span data-ttu-id="a4dd6-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a4dd6-114">Message Text</span></span>|<span data-ttu-id="a4dd6-115">テーブル O_NAME のインデックス I_NAME を処理できません。ファイル グループ F_NAME がオフラインです。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-115">Unable to process index I_NAME of table O_NAME because filegroup F_NAME is offline.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a4dd6-116">説明</span><span class="sxs-lookup"><span data-stu-id="a4dd6-116">Explanation</span></span>  
 <span data-ttu-id="a4dd6-117">この情報メッセージは、インデックスに対応するデータを格納しているファイル グループの 1 つがオフライン状態なので、インデックスをチェックできないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-117">This informational message indicates that the index cannot be checked because one of the filegroups that stores data for the index is offline.</span></span> <span data-ttu-id="a4dd6-118">ファイル グループ内のファイルの状態により、ファイル グループ全体の可用性が決まります。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-118">The state of the files in a filegroup determines the availability of the whole filegroup.</span></span> <span data-ttu-id="a4dd6-119">ファイル グループを使用可能にするには、ファイル グループ内のすべてのファイルがオンラインである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-119">For a filegroup to be available, all files within the filegroup must be online.</span></span> <span data-ttu-id="a4dd6-120">他に問題がなければ、同じオブジェクトの他のインデックスはすべてチェックされます。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-120">If there are no other problems, all other indexes of the same object will be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a4dd6-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a4dd6-121">User Action</span></span>  
 <span data-ttu-id="a4dd6-122">指定したファイル グループのファイルの状態を表示するには、**sys.database_files** カタログ ビューまたは **sys.master_files** カタログ ビューにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-122">To view the state of the files for the specified filegroup, query either the **sys.database_files** or **sys.master_files** catalog view.</span></span>  
  
 <span data-ttu-id="a4dd6-123">オフライン ファイルをバックアップから復元します。</span><span class="sxs-lookup"><span data-stu-id="a4dd6-123">Restore the offline file from a backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4dd6-124">参照</span><span class="sxs-lookup"><span data-stu-id="a4dd6-124">See Also</span></span>  
 <span data-ttu-id="a4dd6-125">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a4dd6-125">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) </span></span>  
 <span data-ttu-id="a4dd6-126">[master_files &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a4dd6-126">[sys.master_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql) </span></span>  
 [<span data-ttu-id="a4dd6-127">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a4dd6-127">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
