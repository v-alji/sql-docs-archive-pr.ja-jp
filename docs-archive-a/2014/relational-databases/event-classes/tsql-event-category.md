---
title: TSQL イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, TSQL event category
- TSQL event category [SQL Server]
- event classes [SQL Server], TSQL event category
ms.assetid: 215f8747-64b5-4bf3-9845-d476b10cda3a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 763d5f31fd3562f54b274a74324ed4715b623a18
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711962"
---
# <a name="tsql-event-category"></a><span data-ttu-id="88ca2-102">TSQL イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="88ca2-102">TSQL Event Category</span></span>
  <span data-ttu-id="88ca2-103">**TSQL** イベント カテゴリには一般的な TSQL イベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="88ca2-103">The **TSQL** event category contains general TSQL events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88ca2-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="88ca2-104">In This Section</span></span>  
  
|<span data-ttu-id="88ca2-105">トピック</span><span class="sxs-lookup"><span data-stu-id="88ca2-105">Topic</span></span>|<span data-ttu-id="88ca2-106">説明</span><span class="sxs-lookup"><span data-stu-id="88ca2-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="88ca2-107">Exec Prepared SQL イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-107">Exec Prepared SQL Event Class</span></span>](exec-prepared-sql-event-class.md)|<span data-ttu-id="88ca2-108">SqlClient、ODBC、OLE DB、または DB-Library が、準備された 1 つまたは複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-108">Indicates that the SqlClient, ODBC, OLE DB, or DB-Library has executed a prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements.</span></span>|  
|[<span data-ttu-id="88ca2-109">Prepare SQL イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-109">Prepare SQL Event Class</span></span>](prepare-sql-event-class.md)|<span data-ttu-id="88ca2-110">SqlClient、ODBC、OLE DB、または DB-Library が、1 つまたは複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用するために準備したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-110">Indicates that SqlClient, ODBC, OLE DB, or DB-Library has prepared a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements for use.</span></span>|  
|[<span data-ttu-id="88ca2-111">SQL:BatchCompleted イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-111">SQL:BatchCompleted Event Class</span></span>](sql-batchcompleted-event-class.md)|<span data-ttu-id="88ca2-112">[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ処理が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-112">Indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch has completed.</span></span>|  
|[<span data-ttu-id="88ca2-113">SQL:BatchStarting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-113">SQL:BatchStarting Event Class</span></span>](sql-batchstarting-event-class.md)|<span data-ttu-id="88ca2-114">[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ処理が開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-114">Indicates that the [!INCLUDE[tsql](../../includes/tsql-md.md)] batch is starting.</span></span>|  
|[<span data-ttu-id="88ca2-115">SQL:StmtCompleted イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-115">SQL:StmtCompleted Event Class</span></span>](sql-stmtcompleted-event-class.md)|<span data-ttu-id="88ca2-116">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-116">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement has completed.</span></span>|  
|[<span data-ttu-id="88ca2-117">SQL:StmtRecompile イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-117">SQL:StmtRecompile Event Class</span></span>](sql-stmtrecompile-event-class.md)|<span data-ttu-id="88ca2-118">ストアド プロシージャ、トリガー、アドホック バッチ、クエリなど、すべての種類のバッチに起因するステートメント レベルの再コンパイルが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-118">Indicates statement-level recompilations caused by all types of batches: stored procedures, triggers, ad hoc batches, and queries.</span></span>|  
|[<span data-ttu-id="88ca2-119">SQL:StmtStarting イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-119">SQL:StmtStarting Event Class</span></span>](sql-stmtstarting-event-class.md)|<span data-ttu-id="88ca2-120">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントが開始したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-120">Indicates that a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is starting.</span></span>|  
|[<span data-ttu-id="88ca2-121">Unprepare SQL イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-121">Unprepare SQL Event Class</span></span>](unprepare-sql-event-class.md)|<span data-ttu-id="88ca2-122">SqlClient、ODBC、OLE DB、または DB-Library が、準備された 1 つまたは複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを削除したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-122">Indicates that the SqlClient, ODBC, OLE DB, or DB-Library has deleted a prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statement or statements.</span></span>|  
|[<span data-ttu-id="88ca2-123">XQuery Static Type イベント クラス</span><span class="sxs-lookup"><span data-stu-id="88ca2-123">XQuery Static Type Event Class</span></span>](xquery-static-type-event-class.md)|<span data-ttu-id="88ca2-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって XQuery 式が実行された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="88ca2-124">Occurs when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executes an XQuery expression.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88ca2-125">参照</span><span class="sxs-lookup"><span data-stu-id="88ca2-125">See Also</span></span>  
 [<span data-ttu-id="88ca2-126">TRANSACT-SQL リファレンス &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="88ca2-126">Transact-SQL Reference &#40;Database Engine&#41;</span></span>](/sql/t-sql/language-reference)  
  
  
