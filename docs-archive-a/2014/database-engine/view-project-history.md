---
title: プロジェクト履歴の表示 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing project history
- version control services [SQL Server], project history
- projects [SQL Server Management Studio], historical information
- historical information [SQL Server], projects
ms.assetid: be0ea2ac-4a35-429c-9c9e-4001ea9035a4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85028141050e19e6ed6394a5bb17709ac8f906ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645196"
---
# <a name="view-project-history"></a><span data-ttu-id="9dd98-102">プロジェクト履歴の表示</span><span class="sxs-lookup"><span data-stu-id="9dd98-102">View Project History</span></span>
  <span data-ttu-id="9dd98-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) プロジェクトの履歴には、ファイルの作成、追加、削除、復元など、各プロジェクト ファイルに対して実行したすべてのアクションの一覧が記録されています。</span><span class="sxs-lookup"><span data-stu-id="9dd98-103">The history of a [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) project includes a list of all the actions taken on each of the project files, including file creation, addition, deletion, and recovery.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dd98-104">Visual SourceSafe プロジェクトは、ソース管理対象のファイルのサーバー バージョンが格納されているサーバー上の場所であり、一般にソース管理サーバー フォルダーと呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="9dd98-104">A Visual SourceSafe project is more commonly referred to as the source control server folder, the location where the server version of a source-controlled file is stored on the server.</span></span>  
  
 <span data-ttu-id="9dd98-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、現在読み込まれているソリューションが属する Visual SourceSafe プロジェクトの履歴を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="9dd98-105">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to examine the history of the Visual SourceSafe project to which the currently loaded solution belongs.</span></span> <span data-ttu-id="9dd98-106">プロジェクト履歴の一部として表示されている情報に基づいて、ファイル バージョンのローカル コピーを取得したり、削除されたバージョンを復元したり、プロジェクト間でファイル バージョンを共有したりできます。</span><span class="sxs-lookup"><span data-stu-id="9dd98-106">Based on the information displayed as part of the history of a project, you can retrieve local copies of file versions, restore deleted versions, or share a file version between projects.</span></span>  
  
### <a name="to-view-the-history-of-a-vss-project"></a><span data-ttu-id="9dd98-107">VSS プロジェクトの履歴を表示するには</span><span class="sxs-lookup"><span data-stu-id="9dd98-107">To view the history of a VSS project</span></span>  
  
1.  <span data-ttu-id="9dd98-108">ソリューション エクスプローラーでプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="9dd98-108">In Solution Explorer, select the project.</span></span>  
  
2.  <span data-ttu-id="9dd98-109">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**履歴の表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9dd98-109">On the **File** menu, point to **Source Control** and click **View History**.</span></span>  
  
3.  <span data-ttu-id="9dd98-110">[**履歴** \<Project> ] ダイアログボックスで、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="9dd98-110">In the **History of** \<Project> dialog box, perform any of the following actions:</span></span>  
  
    -   <span data-ttu-id="9dd98-111">選択したファイルの、ソース管理システムのコピーを表示します。</span><span class="sxs-lookup"><span data-stu-id="9dd98-111">View the source control system's copy of a selected file.</span></span>  
  
    -   <span data-ttu-id="9dd98-112">選択したファイルに関する詳細情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="9dd98-112">View detailed information about a selected file.</span></span>  
  
    -   <span data-ttu-id="9dd98-113">選択したファイルをローカル ディスクに取得します。</span><span class="sxs-lookup"><span data-stu-id="9dd98-113">Retrieve a selected file to your local disk.</span></span>  
  
    -   <span data-ttu-id="9dd98-114">選択したファイルをチェックアウトします。</span><span class="sxs-lookup"><span data-stu-id="9dd98-114">Check out a selected file.</span></span>  
  
    -   <span data-ttu-id="9dd98-115">2 つのソース管理プロジェクト間で、選択したファイルを共有します。</span><span class="sxs-lookup"><span data-stu-id="9dd98-115">Share a selected file between two source control projects.</span></span>  
  
    -   <span data-ttu-id="9dd98-116">プリンター、ファイル、またはクリップボードに、履歴レポートをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="9dd98-116">Export the history report to a printer, a file, or the Clipboard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd98-117">参照</span><span class="sxs-lookup"><span data-stu-id="9dd98-117">See Also</span></span>  
 <span data-ttu-id="9dd98-118">[バージョン情報の設定と取得](../../2014/database-engine/set-and-retrieve-version-information.md) </span><span class="sxs-lookup"><span data-stu-id="9dd98-118">[Set and Retrieve Version Information](../../2014/database-engine/set-and-retrieve-version-information.md) </span></span>  
 <span data-ttu-id="9dd98-119">[ファイルの状態の表示](../../2014/database-engine/view-file-status.md) </span><span class="sxs-lookup"><span data-stu-id="9dd98-119">[View File Status](../../2014/database-engine/view-file-status.md) </span></span>  
 <span data-ttu-id="9dd98-120">[ファイルの取得](../../2014/database-engine/retrieve-files.md) </span><span class="sxs-lookup"><span data-stu-id="9dd98-120">[Retrieve Files](../../2014/database-engine/retrieve-files.md) </span></span>  
 [<span data-ttu-id="9dd98-121">ファイルの比較</span><span class="sxs-lookup"><span data-stu-id="9dd98-121">Compare Files</span></span>](../../2014/database-engine/compare-files.md)  
  
  
