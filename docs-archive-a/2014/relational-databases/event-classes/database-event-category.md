---
title: Database イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2860e1434611393c941a639280343f736073c709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642800"
---
# <a name="database-event-category"></a><span data-ttu-id="c520b-102">Database イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="c520b-102">Database Event Category</span></span>
  <span data-ttu-id="c520b-103">**Database** イベント カテゴリには、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]を監視するためのイベント クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c520b-103">The **Database** event category contains event classes to monitor the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c520b-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c520b-104">In This Section</span></span>  
  
|<span data-ttu-id="c520b-105">トピック</span><span class="sxs-lookup"><span data-stu-id="c520b-105">Topic</span></span>|<span data-ttu-id="c520b-106">説明</span><span class="sxs-lookup"><span data-stu-id="c520b-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c520b-107">Data File Auto Grow イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c520b-107">Data File Auto Grow Event Class</span></span>](data-file-auto-grow-event-class.md)|<span data-ttu-id="c520b-108">データ ファイルが自動的に拡張されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c520b-108">Indicates that the data file grew automatically.</span></span> <span data-ttu-id="c520b-109">データ ファイルが ALTER DATABASE により明示的に拡張された場合、このイベントはトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="c520b-109">This event is not triggered if the data file is grown explicitly through ALTER DATABASE.</span></span>|  
|[<span data-ttu-id="c520b-110">Data File Auto Shrink イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c520b-110">Data File Auto Shrink Event Class</span></span>](data-file-auto-shrink-event-class.md)|<span data-ttu-id="c520b-111">データ ファイルが圧縮されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c520b-111">Indicates that the data file has been shrunk.</span></span>|  
|[<span data-ttu-id="c520b-112">Database Mirroring Connection イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c520b-112">Database Mirroring Connection Event Class</span></span>](database-mirroring-connection-event-class.md)|<span data-ttu-id="c520b-113">データベース ミラーリングのトランスポート接続のステータスをレポートするために生成されるイベントです。</span><span class="sxs-lookup"><span data-stu-id="c520b-113">An event generated to report the status of a transport connection for database mirroring.</span></span>|  
|[<span data-ttu-id="c520b-114">Database Mirroring State Change イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c520b-114">Database Mirroring State Change Event Class</span></span>](database-mirroring-state-change-event-class.md)|<span data-ttu-id="c520b-115">ミラー化されたデータベースの状態が変更された時点を示します。</span><span class="sxs-lookup"><span data-stu-id="c520b-115">Indicates when the state of a mirrored database changes.</span></span>|  
|[<span data-ttu-id="c520b-116">Database Suspect Data Page イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c520b-116">Database Suspect Data Page Event Class</span></span>](database-suspect-data-page-event-class.md)|<span data-ttu-id="c520b-117">**msdb** データベースの **suspect_pages** テーブルにページが加わった時点を示します。</span><span class="sxs-lookup"><span data-stu-id="c520b-117">Indicates when a page is added to the **suspect_pages** table in the **msdb** database.</span></span>|  
|[<span data-ttu-id="c520b-118">Log File Auto Grow イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c520b-118">Log File Auto Grow Event Class</span></span>](log-file-auto-grow-event-class.md)|<span data-ttu-id="c520b-119">ログ ファイルが自動的に拡張されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c520b-119">Indicates that the log file grew automatically.</span></span> <span data-ttu-id="c520b-120">ログ ファイルが ALTER DATABASE により明示的に拡張された場合、このイベントはトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="c520b-120">This event is not triggered if the log file is grown explicitly through ALTER DATABASE.</span></span>|  
|[<span data-ttu-id="c520b-121">Log File Auto Shrink イベント クラス</span><span class="sxs-lookup"><span data-stu-id="c520b-121">Log File Auto Shrink Event Class</span></span>](log-file-auto-shrink-event-class.md)|<span data-ttu-id="c520b-122">ログ ファイルが自動的に拡張されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c520b-122">Indicates that the log file grew automatically.</span></span> <span data-ttu-id="c520b-123">ログ ファイルが ALTER DATABASE により明示的に圧縮された場合、このイベントはトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="c520b-123">This event is not triggered if the log file shrinks explicitly through ALTER DATABASE.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c520b-124">参照</span><span class="sxs-lookup"><span data-stu-id="c520b-124">See Also</span></span>  
 [<span data-ttu-id="c520b-125">拡張イベント</span><span class="sxs-lookup"><span data-stu-id="c520b-125">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
