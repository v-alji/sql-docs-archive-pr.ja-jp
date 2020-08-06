---
title: イベントのトレースと再生 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- replaying events
- traces [SMO]
- events [SMO], replaying
- events [SMO], tracing
ms.assetid: f41b3f85-2f6c-4c3e-9776-8c73d2cc7a53
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7f0d570c70ef1cba080217e6c3a0f9b6055a4d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716177"
---
# <a name="tracing-and-replaying-events"></a><span data-ttu-id="1ea2e-102">イベントのトレースおよび再生</span><span class="sxs-lookup"><span data-stu-id="1ea2e-102">Tracing and Replaying Events</span></span>
  <span data-ttu-id="1ea2e-103">SMO で、[!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの監視に使用する [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 機能にプログラムでアクセスするには、<xref:Microsoft.SqlServer.Management.Trace> 名前空間の `Trace` オブジェクトおよび `Replay` オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-103">In SMO, the `Trace` and `Replay` objects in the <xref:Microsoft.SqlServer.Management.Trace> namespace provide programmatic access to the [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] functionality, which is used for monitoring an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1ea2e-104">各イベントに関するデータをキャプチャし、ファイルやテーブルに保存して、後で分析できます。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-104">You can capture and save data about each event to a file or table to analyze later.</span></span> <span data-ttu-id="1ea2e-105">たとえば、実稼動環境を監視して、どのプロシージャの実行が遅く、パフォーマンスに影響を与えているかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-105">For example, you can monitor a production environment to see which procedures are impeding performance by executing too slowly.</span></span>  
  
 <span data-ttu-id="1ea2e-106">`Trace` オブジェクトおよび `Replay` オブジェクトを使用すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに対するトレースを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-106">The `Trace` and `Replay` objects provide a set of objects that can be used to create traces on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ea2e-107">これらのオブジェクトをユーザー独自のアプリケーションから使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] または [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] に対してトレースを手動で作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-107">These objects can be used from within your own applications to create traces manually for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="1ea2e-108">また、SMO `Trace` オブジェクトを使用して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、または DTS ログを監視することによって作成された SQL トレースのファイルおよびテーブルを読み取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-108">Additionally, SMO `Trace` objects can be used to read SQL Trace files and tables that were created by monitoring [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], or DTS logging.</span></span>  
  
 <span data-ttu-id="1ea2e-109">SMO `Trace` オブジェクトによって、次の操作が可能になります。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-109">SMO `Trace` objects let you perform the following functions:</span></span>  
  
-   <span data-ttu-id="1ea2e-110">トレースの作成。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-110">Create a trace.</span></span>  
  
-   <span data-ttu-id="1ea2e-111">トレース上でのフィルターの設定。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-111">Set filters on the trace.</span></span>  
  
-   <span data-ttu-id="1ea2e-112">トレースするイベントの設定。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-112">Set the events that are being traced.</span></span>  
  
-   <span data-ttu-id="1ea2e-113">トレースの停止または開始。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-113">Stop or start a trace.</span></span>  
  
-   <span data-ttu-id="1ea2e-114">トレース ファイルおよびトレース テーブルの読み取り。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-114">Read trace files, and trace tables.</span></span>  
  
-   <span data-ttu-id="1ea2e-115">トレースでのイベントに関する情報の取得。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-115">Get information about events on a trace.</span></span>  
  
-   <span data-ttu-id="1ea2e-116">トレースでのフィルターに関する情報の取得。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-116">Get information about filters on a trace.</span></span>  
  
-   <span data-ttu-id="1ea2e-117">プログラムを使用したトレース データの操作。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-117">Manipulate trace data programmatically.</span></span>  
  
-   <span data-ttu-id="1ea2e-118">トレース テーブルおよびトレース ファイルの書き込み。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-118">Write trace tables and trace files.</span></span>  
  
-   <span data-ttu-id="1ea2e-119">トレース ファイルまたはトレース テーブルの再生。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-119">Replay trace files or trace tables.</span></span>  
  
 <span data-ttu-id="1ea2e-120">オブジェクトとオブジェクトのトレースデータは、 `Trace` `Replay` SMO アプリケーションで使用できます。また、 [SQL Server プロファイラー](../../../tools/sql-server-profiler/sql-server-profiler.md)を使用して手動で調べることもできます。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-120">The trace data from the `Trace` and `Replay` objects can be used by the SMO application, or it can be examined manually by using [SQL Server Profiler](../../../tools/sql-server-profiler/sql-server-profiler.md).</span></span> <span data-ttu-id="1ea2e-121">トレースデータは、トレース機能を提供する[SQL トレース](../../sql-trace/sql-trace.md)ストアドプロシージャとも互換性があります。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-121">The trace data is also compatible with the [SQL Trace](../../sql-trace/sql-trace.md) stored procedures that also provide tracing capabilities.</span></span>  
  
 <span data-ttu-id="1ea2e-122">SMO トレース オブジェクトは、Microsoft.SQLServer.ConnectionInfo.dll ファイルへの参照が必要となる <xref:Microsoft.SqlServer.Management.Trace> 名前空間に存在します。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-122">The SMO trace objects reside in the <xref:Microsoft.SqlServer.Management.Trace> namespace, which requires a reference to the Microsoft.SQLServer.ConnectionInfo.dll file.</span></span>  
  
 <span data-ttu-id="1ea2e-123">オブジェクト `Trace` およびオブジェクトには、 `Replay` <xref:Microsoft.SqlServer.Management.Common.ServerConnection> <xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> のインスタンスとの接続を確立するためのオブジェクトが必要 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-123">The `Trace` and `Replay` objects require a <xref:Microsoft.SqlServer.Management.Common.ServerConnection><xref:Microsoft.SqlServer.Management.Smo.Server.%23ctor%2A> object to establish a connection with the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1ea2e-124"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトは、<xref:Microsoft.SqlServer.Management.Common> 名前空間にあります。Microsoft.SQLServer.ConnectionInfo.dll ファイルへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-124">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object resides in the <xref:Microsoft.SqlServer.Management.Common> namespace, which requires a reference to the Microsoft.SQLServer.ConnectionInfo.dll file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ea2e-125">  `Trace` オブジェクトおよび `Replay` オブジェクトは、64 ビット プラットフォームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="1ea2e-125">The `Trace` and `Replay` objects are not supported on a 64-bit platform.</span></span>  
  
  
