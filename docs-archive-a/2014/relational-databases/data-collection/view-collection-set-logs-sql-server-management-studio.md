---
title: コレクション セット ログの表示 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], viewing
- collection sets [SQL Server], viewing logs
ms.assetid: 428908b8-fb6a-4d0c-8339-ee133e23aad2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab7c49e72690b76fa9f416a835f7b5b7b3a4553d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643973"
---
# <a name="view-collection-set-logs-sql-server-management-studio"></a><span data-ttu-id="0e1ea-102">コレクション セット ログの表示 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="0e1ea-102">View Collection Set Logs (SQL Server Management Studio)</span></span>
  <span data-ttu-id="0e1ea-103">すべてのコレクション セットのログまたは個々のコレクション セットのログは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]から表示できます。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-103">You can view all the collection set logs or individual collection set logs from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="to-view-collection-set-logs"></a><span data-ttu-id="0e1ea-104">コレクション セットのログを表示するには</span><span class="sxs-lookup"><span data-stu-id="0e1ea-104">To view collection set logs</span></span>  
  
1.  <span data-ttu-id="0e1ea-105">オブジェクト エクスプローラーで、 **[管理]** フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-105">In Object Explorer, expand the **Management** folder.</span></span>  
  
2.  <span data-ttu-id="0e1ea-106">**[データ コレクション]** を右クリックして、 **[ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-106">Right-click **Data Collection**, and then click **View Logs**.</span></span>  
  
     <span data-ttu-id="0e1ea-107">**[ログ ファイルの表示]** が開きます。ビューアーの **[データ コレクション]** ノードの下に、各コレクション セットのすべてのログ ファイルが選択された状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-107">This opens the **Log File Viewer**.All the log files for each collection set are listed and pre-selected under the **Data Collection** node in the viewer.</span></span>  
  
3.  <span data-ttu-id="0e1ea-108">特定のコレクション セットのログを表示するには、表示しないログを含む各コレクション セットの横にあるチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-108">To view specific collection set logs, clear the check box next to each collection set whose log you do not want to view.</span></span> <span data-ttu-id="0e1ea-109">コレクション セットのログ情報が、 **[ログ ファイルの表示]** の詳細ペインから削除されます。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-109">The log information for that collection set is removed from the **Log File Viewer** details pane.</span></span>  
  
### <a name="to-view-a-specific-collection-set-log-file"></a><span data-ttu-id="0e1ea-110">特定のコレクション セットのログ ファイルを表示するには</span><span class="sxs-lookup"><span data-stu-id="0e1ea-110">To view a specific collection set log file</span></span>  
  
1.  <span data-ttu-id="0e1ea-111">オブジェクト エクスプローラーで、 **[管理]** フォルダーを展開し、 **[データ コレクション]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-111">In Object Explorer, expand the **Management** folder, and then expand **Data Collection**.</span></span>  
  
2.  <span data-ttu-id="0e1ea-112">表示するログを含むコレクション セットを右クリックして **[ログの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-112">Right-click the collection set whose log you want to view, and then click **View Logs**.</span></span>  
  
     <span data-ttu-id="0e1ea-113">**[ログ ファイルの表示]** が表示されて、選択したコレクション セットのログ ファイルのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0e1ea-113">The **Log File Viewer** opens, displaying only the log file for the collection set that you selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e1ea-114">参照</span><span class="sxs-lookup"><span data-stu-id="0e1ea-114">See Also</span></span>  
 <span data-ttu-id="0e1ea-115">[[データ コレクション]](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="0e1ea-115">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="0e1ea-116">データ コレクションの管理</span><span class="sxs-lookup"><span data-stu-id="0e1ea-116">Manage Data Collection</span></span>](manage-data-collection.md)  
  
  
