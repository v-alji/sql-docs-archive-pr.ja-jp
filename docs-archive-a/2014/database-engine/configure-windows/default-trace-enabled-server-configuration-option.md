---
title: default trace enabled サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- logs [SQL Server], traces
- traces [SQL Server], logs
- default trace enabled option
ms.assetid: 1322d668-44f4-469e-8fd6-e0d02a81c8f2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8d40305de7375f2ae10d563871fd40b7acfa463f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740422"
---
# <a name="default-trace-enabled-server-configuration-option"></a><span data-ttu-id="6f6ac-102">default trace enabled サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="6f6ac-102">default trace enabled Server Configuration Option</span></span>
  <span data-ttu-id="6f6ac-103">**default trace enabled** オプションは、既定のトレース ログ ファイルを有効または無効にする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-103">Use the **default trace enabled** option to enable or disable the default trace log files.</span></span> <span data-ttu-id="6f6ac-104">既定のトレース機能では、主に構成オプションに関連する操作および変更の詳しい永続的なログが提供されます。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-104">The default trace functionality provides a rich, persistent log of activity and changes primarily related to the configuration options.</span></span>  
  
> [!WARNING]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] <span data-ttu-id="6f6ac-105">代わりに拡張イベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-105">Use Extended Events instead.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="6f6ac-106">目的</span><span class="sxs-lookup"><span data-stu-id="6f6ac-106">Purpose</span></span>  
 <span data-ttu-id="6f6ac-107">既定のトレース機能は、問題が初めて発生したときに、その問題を診断するために必要なログ データを提供することによって、データベース管理者によるトラブルシューティングを支援します。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-107">Default trace provides troubleshooting assistance to database administrators by ensuring that they have the log data necessary to diagnose problems the first time they occur.</span></span>  
  
## <a name="viewing"></a><span data-ttu-id="6f6ac-108">表示</span><span class="sxs-lookup"><span data-stu-id="6f6ac-108">Viewing</span></span>  
 <span data-ttu-id="6f6ac-109">既定のトレース ログは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] で開いて確認するか、 [!INCLUDE[tsql](../../includes/tsql-md.md)] システム関数を使用して `fn_trace_gettable` でクエリできます。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-109">The default trace logs can be opened and examined by [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] or queried with [!INCLUDE[tsql](../../includes/tsql-md.md)] by using the `fn_trace_gettable` system function.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="6f6ac-110">では、通常のトレース出力ファイルを開く場合と同様に、既定のトレース ログ ファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-110">can open the default trace log files just as it does normal trace output files.</span></span> <span data-ttu-id="6f6ac-111">既定のトレース ログは、ロールオーバー トレース ファイルを使用して、既定により `\MSSQL\LOG` ディレクトリに保存されます。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-111">The default trace log is stored by default in the `\MSSQL\LOG` directory using a rollover trace file.</span></span> <span data-ttu-id="6f6ac-112">既定のトレース ログ ファイルのベース ファイル名は `log.trc`です。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-112">The base file name for the default trace log file is `log.trc`.</span></span> <span data-ttu-id="6f6ac-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の標準インストールの場合、既定のトレースが有効になっているため、TraceID 1 になります。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-113">In a typical installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the default trace is enabled and thus becomes TraceID 1.</span></span> <span data-ttu-id="6f6ac-114">インストール後や他のトレースの作成後に有効にした場合、TraceID の数値が大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-114">If enabled after installation and after creating other traces, the TraceID can become a larger number.</span></span>  
  
 <span data-ttu-id="6f6ac-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler を使用してこのトレース ファイルを表示する方法については、「[トレース ファイルを開く&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-115">For more information about using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler to view this trace file, see [Open a Trace File &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f6ac-116">例:</span><span class="sxs-lookup"><span data-stu-id="6f6ac-116">Example:</span></span>  
 <span data-ttu-id="6f6ac-117">次のステートメントは、既定の場所にある既定のトレース ログを開きます。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-117">The following statement opens the default trace log in the default location:</span></span>  
  
```  
SELECT *   
FROM fn_trace_gettable  
('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\LOG\log.trc', default);  
GO  
  
```  
  
## <a name="configuring"></a><span data-ttu-id="6f6ac-118">構成</span><span class="sxs-lookup"><span data-stu-id="6f6ac-118">Configuring</span></span>  
 <span data-ttu-id="6f6ac-119">**default trace enabled** オプションを 1 に設定すると、 **既定のトレース**が有効になります。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-119">When set to 1, the **default trace enabled** option enables **Default Trace**.</span></span> <span data-ttu-id="6f6ac-120">このオプションの既定値は 1 (ON) です。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-120">The default setting for this option is 1 (ON).</span></span> <span data-ttu-id="6f6ac-121">0 に設定すると、トレースがオフになります。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-121">A value of 0 turns off the trace.</span></span>  
  
 <span data-ttu-id="6f6ac-122">**default trace enabled** オプションは拡張オプションです。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-122">The **default trace enabled** option is an advanced option.</span></span> <span data-ttu-id="6f6ac-123">**sp_configure** システム ストアド プロシージャを使用して **default trace enabled** オプションの設定を変更するには、 **show advanced options** を 1 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-123">If you are using the **sp_configure** system stored procedure to change the setting, you can change the **default trace enabled** option only when **show advanced options** is set to 1.</span></span> <span data-ttu-id="6f6ac-124">新しい設定は、サーバーを再起動しなくてもすぐに有効になります。</span><span class="sxs-lookup"><span data-stu-id="6f6ac-124">The setting takes effect immediately without a server restart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6ac-125">参照</span><span class="sxs-lookup"><span data-stu-id="6f6ac-125">See Also</span></span>  
 <span data-ttu-id="6f6ac-126">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6f6ac-126">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="6f6ac-127">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6f6ac-127">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="6f6ac-128">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="6f6ac-128">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
