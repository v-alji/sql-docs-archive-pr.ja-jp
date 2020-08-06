---
title: バージョン情報の設定と取得 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- historical information [SQL Server]
- source controls [SQL Server Management Studio], version information
- retrieving version information
- current file version information
- version control services [SQL Server], retrieving version information
- version control services [SQL Server], setting version information
- status information [SQL Server], source control files
- historical information [SQL Server], source control files
ms.assetid: c3f253c4-4e3d-48e8-8d90-bd6ee899faf7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eff3d40ba9b663ba8611508c5b9f0c9961005b81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712346"
---
# <a name="set-and-retrieve-version-information"></a><span data-ttu-id="8dcc4-102">バージョン情報の設定と取得</span><span class="sxs-lookup"><span data-stu-id="8dcc4-102">Set and Retrieve Version Information</span></span>
  <span data-ttu-id="8dcc4-103">バージョン情報には、ソース管理の対象であるファイルの履歴と現在のステータスが記録されています。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-103">Version information includes the history and current status of a source-controlled file.</span></span> <span data-ttu-id="8dcc4-104">[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe では、ソース管理の対象であるすべてのファイルについて包括的な履歴が保持されるため、1 つ以上のファイルの変化を論理的に追跡できます。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-104">For every source-controlled file, [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe maintains a comprehensive history, so you can track the evolution of one or more files over time.</span></span> <span data-ttu-id="8dcc4-105">この情報を使用して、ファイルのあらゆるバージョンのローカル コピーを取得したり、任意の 2 つのファイル バージョンを比較したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-105">You can also use this information to retrieve a local copy of any version of the file or to compare any two file versions.</span></span>  
  
 <span data-ttu-id="8dcc4-106">ファイル履歴には、次の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-106">The history of a file includes:</span></span>  
  
-   <span data-ttu-id="8dcc4-107">バージョン番号。この番号により、同じファイルの他のバージョンとの間で順序を識別します。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-107">The version number, which identifies its sequence among other versions of the same file.</span></span>  
  
-   <span data-ttu-id="8dcc4-108">実行されるアクション。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-108">The action performed.</span></span> <span data-ttu-id="8dcc4-109">追跡される操作には、ファイルの作成、チェックイン、削除が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-109">Tracked operations include file creation, check in, and deletion.</span></span>  
  
-   <span data-ttu-id="8dcc4-110">ファイルを対象とするアクションを実行したユーザーの名前。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-110">The user name of the person who performed an action involving the file.</span></span>  
  
-   <span data-ttu-id="8dcc4-111">操作が実行された日付と時刻。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-111">The date and time when the operation was performed.</span></span>  
  
 <span data-ttu-id="8dcc4-112">Visual SourceSafe では、現在読み込まれているソリューションの現在のステータス情報も保持されます。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-112">Visual SourceSafe also maintains current status information on the currently loaded solution.</span></span> <span data-ttu-id="8dcc4-113">この情報によって、ファイルの現在のステータスを示すスナップショットが作成されます。このスナップショットには、以下の項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8dcc4-113">This information provides a snapshot of the current state of the file, including:</span></span>  
  
-   <span data-ttu-id="8dcc4-114">ファイルをチェックアウトしたユーザーの ID</span><span class="sxs-lookup"><span data-stu-id="8dcc4-114">The identity of the user who has the file checked out.</span></span>  
  
-   <span data-ttu-id="8dcc4-115">選択したファイルの最新のバージョン番号</span><span class="sxs-lookup"><span data-stu-id="8dcc4-115">The latest version number of the selected file.</span></span>  
  
-   <span data-ttu-id="8dcc4-116">バージョンの作成日</span><span class="sxs-lookup"><span data-stu-id="8dcc4-116">The date when the version was created.</span></span>  
  
-   <span data-ttu-id="8dcc4-117">バージョンに関するユーザー コメント</span><span class="sxs-lookup"><span data-stu-id="8dcc4-117">The user comment associated with the version.</span></span>  
  
-   <span data-ttu-id="8dcc4-118">ファイルを共有するプロジェクトへのパス</span><span class="sxs-lookup"><span data-stu-id="8dcc4-118">The paths to the projects with which the file is shared.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8dcc4-119">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8dcc4-119">In This Section</span></span>  
  
-   [<span data-ttu-id="8dcc4-120">ファイル履歴の表示</span><span class="sxs-lookup"><span data-stu-id="8dcc4-120">View File History</span></span>](../../2014/database-engine/view-file-history.md)  
  
-   [<span data-ttu-id="8dcc4-121">プロジェクト履歴の表示</span><span class="sxs-lookup"><span data-stu-id="8dcc4-121">View Project History</span></span>](../../2014/database-engine/view-project-history.md)  
  
-   [<span data-ttu-id="8dcc4-122">ファイルの状態の表示</span><span class="sxs-lookup"><span data-stu-id="8dcc4-122">View File Status</span></span>](../../2014/database-engine/view-file-status.md)  
  
-   [<span data-ttu-id="8dcc4-123">ファイルの取得</span><span class="sxs-lookup"><span data-stu-id="8dcc4-123">Retrieve Files</span></span>](../../2014/database-engine/retrieve-files.md)  
  
-   [<span data-ttu-id="8dcc4-124">特定のバージョンを最新バージョンとして指定する</span><span class="sxs-lookup"><span data-stu-id="8dcc4-124">Specify a Version as the Latest Version</span></span>](../../2014/database-engine/specify-a-version-as-the-latest-version.md)  
  
-   [<span data-ttu-id="8dcc4-125">ファイルの比較</span><span class="sxs-lookup"><span data-stu-id="8dcc4-125">Compare Files</span></span>](../../2014/database-engine/compare-files.md)  
  
-   [<span data-ttu-id="8dcc4-126">ファイルを共有する</span><span class="sxs-lookup"><span data-stu-id="8dcc4-126">Share Files</span></span>](../../2014/database-engine/share-files.md)  
  
-   [<span data-ttu-id="8dcc4-127">履歴レポートおよびステータス レポートの作成</span><span class="sxs-lookup"><span data-stu-id="8dcc4-127">Create History and Status Reports</span></span>](../../2014/database-engine/create-history-and-status-reports.md)  
  
## <a name="see-also"></a><span data-ttu-id="8dcc4-128">参照</span><span class="sxs-lookup"><span data-stu-id="8dcc4-128">See Also</span></span>  
 [<span data-ttu-id="8dcc4-129">ソース管理の基礎</span><span class="sxs-lookup"><span data-stu-id="8dcc4-129">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)  
  
  
