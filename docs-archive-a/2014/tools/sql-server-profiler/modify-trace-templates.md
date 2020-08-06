---
title: トレーステンプレートの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a26d0a70f65b6ff60dcf42ffb98e67dc0d2b52d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632238"
---
# <a name="modify-trace-templates"></a><span data-ttu-id="e3260-102">トレース テンプレートの変更</span><span class="sxs-lookup"><span data-stu-id="e3260-102">Modify Trace Templates</span></span>
  <span data-ttu-id="e3260-103">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を実行しているローカル コンピューター上のファイルに保存されたテンプレートは変更することができます。</span><span class="sxs-lookup"><span data-stu-id="e3260-103">You can modify templates that are saved in a file on the local computer on which [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] is running.</span></span> <span data-ttu-id="e3260-104">また、それらのファイルから派生したテンプレートも変更できます。</span><span class="sxs-lookup"><span data-stu-id="e3260-104">You can also modify templates derived from those files.</span></span> <span data-ttu-id="e3260-105">既存のテンプレートを変更する場合は、 **[トレースのプロパティ]** ダイアログ ボックスの **[イベントの選択]** タブで、最初にプロパティを設定したときと同じ順序で、イベント クラスやデータ列などのテンプレートのプロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="e3260-105">When you modify existing templates, you edit template properties such as event classes and data columns, in the same order that the properties were set originally, on the **Events Selection** tab of the **Trace Properties** dialog box.</span></span> <span data-ttu-id="e3260-106">イベント クラスとデータ列は追加または削除することができ、フィルターは変更することができます。</span><span class="sxs-lookup"><span data-stu-id="e3260-106">Event classes and data columns can be added or removed, and filters can be changed.</span></span> <span data-ttu-id="e3260-107">テンプレートを変更すると、ユーザー固有のテンプレートが作成されます。元のシステム テンプレートは変更されません。</span><span class="sxs-lookup"><span data-stu-id="e3260-107">After the template is modified, a user-specific template is created and the original system template is left intact.</span></span> <span data-ttu-id="e3260-108">詳細については、「 [トレースとトレース テンプレートの保存](save-traces-and-trace-templates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3260-108">For more information, see [Save Traces and Trace Templates](save-traces-and-trace-templates.md).</span></span>  
  
 <span data-ttu-id="e3260-109">トレースを作成したときに使用した元のテンプレートを覚えていない (または保存していなかった) 場合や、後日同じトレースを実行する場合など、既存のトレース ファイルからテンプレートを派生させる必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="e3260-109">You may need to derive a template from an existing trace file if you cannot remember (or have not saved) the original template that was used to create the trace, or if you want to run the same trace at a later date.</span></span> <span data-ttu-id="e3260-110">既存のトレースを使用する場合、プロパティを参照できますが、変更できません。</span><span class="sxs-lookup"><span data-stu-id="e3260-110">When working with existing traces, you can view the properties, but you cannot modify the properties.</span></span> <span data-ttu-id="e3260-111">プロパティを変更するには、トレースを停止または一時停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3260-111">To modify the properties, stop or pause the trace.</span></span> <span data-ttu-id="e3260-112">詳細については、「[トレース ファイルまたはトレース テーブルからのテンプレートの作成 &#40;SQL Server Profiler&#41;](sql-server-profiler.md)」および「[実行中のトレースからのテンプレートの作成 &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3260-112">For more information, see [Derive a Template from a Trace File or Trace Table &#40;SQL Server Profiler&#41;](sql-server-profiler.md) and [Derive a Template from a Running Trace &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md).</span></span>  
  
 <span data-ttu-id="e3260-113">**トレース テンプレートを作成するには**</span><span class="sxs-lookup"><span data-stu-id="e3260-113">**To create a trace template**</span></span>  
  
 [<span data-ttu-id="e3260-114">トレース テンプレートの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="e3260-114">Create a Trace Template &#40;SQL Server Profiler&#41;</span></span>](create-a-trace-template-sql-server-profiler.md)  
  
 <span data-ttu-id="e3260-115">**トレース テンプレートからトレースを実行するには**</span><span class="sxs-lookup"><span data-stu-id="e3260-115">**To run a trace from a trace template**</span></span>  
  
 [<span data-ttu-id="e3260-116">トレースの作成 &#40;SQL Server Profiler&#41;</span><span class="sxs-lookup"><span data-stu-id="e3260-116">Create a Trace &#40;SQL Server Profiler&#41;</span></span>](create-a-trace-sql-server-profiler.md)  
  
 <span data-ttu-id="e3260-117">**トレース テンプレートを変更するには**</span><span class="sxs-lookup"><span data-stu-id="e3260-117">**To modify a trace template**</span></span>  
  
 [<span data-ttu-id="e3260-118">SQL Server Profiler の使用</span><span class="sxs-lookup"><span data-stu-id="e3260-118">Using SQL Server Profiler</span></span>](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [<span data-ttu-id="e3260-119">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e3260-119">Using Transact-SQL</span></span>](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 <span data-ttu-id="e3260-120">**トレース テンプレートまたはトレース ファイルからイベントを追加または削除するには**</span><span class="sxs-lookup"><span data-stu-id="e3260-120">**To add or remove events from a trace template or trace file**</span></span>  
  
 [<span data-ttu-id="e3260-121">SQL Server Profiler の使用</span><span class="sxs-lookup"><span data-stu-id="e3260-121">Using SQL Server Profiler</span></span>](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [<span data-ttu-id="e3260-122">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="e3260-122">Using Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="e3260-123">参照</span><span class="sxs-lookup"><span data-stu-id="e3260-123">See Also</span></span>  
 [<span data-ttu-id="e3260-124">トレースを開始する</span><span class="sxs-lookup"><span data-stu-id="e3260-124">Start a Trace</span></span>](start-a-trace.md)  
  
  
