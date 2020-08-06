---
title: Cursors イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Cursors event category [SQL Server]
- event classes [SQL Server], Cursors event category
- SQL Server event classes, Cursors event category
ms.assetid: 752e0695-b464-4720-93be-5b9b53b7ab21
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3b31ff8ccb9c662a2f0ea54adc9cd2d466103be2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715258"
---
# <a name="cursors-event-category"></a><span data-ttu-id="08cae-102">Cursors イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="08cae-102">Cursors Event Category</span></span>
  <span data-ttu-id="08cae-103">**Cursors** イベント カテゴリには、カーソルの動作の監視に使用するイベント クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="08cae-103">The **Cursors** event category contains event classes that are used to monitor the behavior of cursors.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08cae-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="08cae-104">In This Section</span></span>  
  
|<span data-ttu-id="08cae-105">トピック</span><span class="sxs-lookup"><span data-stu-id="08cae-105">Topic</span></span>|<span data-ttu-id="08cae-106">説明</span><span class="sxs-lookup"><span data-stu-id="08cae-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="08cae-107">CursorClose イベント クラス</span><span class="sxs-lookup"><span data-stu-id="08cae-107">CursorClose Event Class</span></span>](cursorclose-event-class.md)|<span data-ttu-id="08cae-108">アプリケーション プログラミング インターフェイス (API) のカーソルで発生する、カーソルを閉じるイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08cae-108">Describes cursor close events that occur in application programming interface (API) cursors.</span></span>|  
|[<span data-ttu-id="08cae-109">CursorExecute イベント クラス</span><span class="sxs-lookup"><span data-stu-id="08cae-109">CursorExecute Event Class</span></span>](cursorexecute-event-class.md)|<span data-ttu-id="08cae-110">API のカーソルで発生する、カーソルを実行するイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08cae-110">Describes cursor execute events that occur in API cursors.</span></span>|  
|[<span data-ttu-id="08cae-111">CursorImplicitConversion イベント クラス</span><span class="sxs-lookup"><span data-stu-id="08cae-111">CursorImplicitConversion Event Class</span></span>](cursorimplicitconversion-event-class.md)|<span data-ttu-id="08cae-112">API のカーソル、または [!INCLUDE[tsql](../../includes/tsql-md.md)] のカーソルで発生する、カーソルを暗黙的に変換するイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08cae-112">Describes cursor implicit conversion events that occur in API or [!INCLUDE[tsql](../../includes/tsql-md.md)] cursors.</span></span>|  
|[<span data-ttu-id="08cae-113">CursorOpen イベント クラス</span><span class="sxs-lookup"><span data-stu-id="08cae-113">CursorOpen Event Class</span></span>](cursoropen-event-class.md)|<span data-ttu-id="08cae-114">API のカーソルで発生する、カーソルを開くイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08cae-114">Describes cursor open events that occur in API cursors.</span></span>|  
|[<span data-ttu-id="08cae-115">CursorPrepare イベント クラス</span><span class="sxs-lookup"><span data-stu-id="08cae-115">CursorPrepare Event Class</span></span>](cursorprepare-event-class.md)|<span data-ttu-id="08cae-116">API のカーソルで発生する、カーソルを準備するイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08cae-116">Describes cursor prepare events that occur in API cursors.</span></span>|  
|[<span data-ttu-id="08cae-117">CursorRecompile イベント クラス</span><span class="sxs-lookup"><span data-stu-id="08cae-117">CursorRecompile Event Class</span></span>](cursorrecompile-event-class.md)|<span data-ttu-id="08cae-118">API のカーソルで発生する、カーソルを再コンパイルするイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08cae-118">Describes cursor recompile events that occur in API cursors.</span></span>|  
|[<span data-ttu-id="08cae-119">CursorUnprepare イベント クラス</span><span class="sxs-lookup"><span data-stu-id="08cae-119">CursorUnprepare Event Class</span></span>](cursorunprepare-event-class.md)|<span data-ttu-id="08cae-120">API のカーソルで発生する、カーソルの準備を解除するイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08cae-120">Describes cursor unprepare events that occur in API cursors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08cae-121">参照</span><span class="sxs-lookup"><span data-stu-id="08cae-121">See Also</span></span>  
 [<span data-ttu-id="08cae-122">拡張イベント</span><span class="sxs-lookup"><span data-stu-id="08cae-122">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
