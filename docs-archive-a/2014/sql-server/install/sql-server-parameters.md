---
title: SQL Server Parameters |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2b885e7616506fd08cae99166cc794dbfb5dac7d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720805"
---
# <a name="sql-server-parameters"></a><span data-ttu-id="2abc8-102">SQL Server パラメーター</span><span class="sxs-lookup"><span data-stu-id="2abc8-102">SQL Server Parameters</span></span>
  <span data-ttu-id="2abc8-103">このページでは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の分析で使用するパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="2abc8-103">On this page, set parameters that the analyzer will use for [!INCLUDE[ssDE](../../includes/ssde-md.md)] analysis.</span></span> <span data-ttu-id="2abc8-104">1 つ、複数、またはすべてのデータベースの分析、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して作成されたトレース ファイルの分析、および SQL バッチ ファイルの分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2abc8-104">You can analyze one, several, or all databases, analyze trace files that were created by using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], and analyze SQL batch files.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2abc8-105">分析対象のトレース ファイルまたは SQL バッチ ファイルを送信する場合に限り、一部のアップグレード問題が検出される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2abc8-105">Some upgrade issues can be detected only if you submit trace files or SQL batch files to be analyzed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2abc8-106">Options</span><span class="sxs-lookup"><span data-stu-id="2abc8-106">Options</span></span>  
 <span data-ttu-id="2abc8-107">**[分析するデータベース]**</span><span class="sxs-lookup"><span data-stu-id="2abc8-107">**Database(s) to analyze**</span></span>  
 <span data-ttu-id="2abc8-108">すべてのデータベースを分析するには、[**すべてのデータベース**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2abc8-108">To analyze all databases, select the **All databases** check box.</span></span> <span data-ttu-id="2abc8-109">データベースを選択して分析するには、各データベースの横にあるチェック ボックスをオンにしてスキャンの対象とします。</span><span class="sxs-lookup"><span data-stu-id="2abc8-109">To analyze a selection of databases, select the check box next to each database to include in the scan.</span></span>  
  
 <span data-ttu-id="2abc8-110">**[トレース ファイルの分析]**</span><span class="sxs-lookup"><span data-stu-id="2abc8-110">**Analyze trace file(s)**</span></span>  
 <span data-ttu-id="2abc8-111">ファイル システムのトレース ファイルを分析するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2abc8-111">Select this check box to analyze trace files in the file system.</span></span>  
  
 <span data-ttu-id="2abc8-112">**[トレース ファイルのパス]**</span><span class="sxs-lookup"><span data-stu-id="2abc8-112">**Path to trace file(s)**</span></span>  
 <span data-ttu-id="2abc8-113">1 つ以上のファイルを分析できます。</span><span class="sxs-lookup"><span data-stu-id="2abc8-113">You can analyze one or more files.</span></span> <span data-ttu-id="2abc8-114">場所を参照して複数のファイルを選択したり、複数のファイル名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2abc8-114">You can browse to a location and select multiple files, or you can provide multiple file names.</span></span> <span data-ttu-id="2abc8-115">各ファイルへの完全パス名およびファイル名を使用し、パイプ文字 (|) でエントリを区切ります。</span><span class="sxs-lookup"><span data-stu-id="2abc8-115">Use the full path name to each file, include the file name, and separate entries by using the pipe character (|).</span></span>  
  
 <span data-ttu-id="2abc8-116">[**トレースファイルの分析**] を有効にすると、パス名とファイル名を入力するまで [**次へ**] が無効になります。</span><span class="sxs-lookup"><span data-stu-id="2abc8-116">If you enable **Analyze trace file(s)**, **Next** is disabled until you enter a path name and a file name.</span></span>  
  
 <span data-ttu-id="2abc8-117">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バッチファイルの分析**</span><span class="sxs-lookup"><span data-stu-id="2abc8-117">**Analyze [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch file(s)**</span></span>  
 <span data-ttu-id="2abc8-118">ファイル システムの [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ ファイルを分析するには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2abc8-118">Select this check box to analyze [!INCLUDE[tsql](../../includes/tsql-md.md)] batch files in the file system.</span></span>  
  
 <span data-ttu-id="2abc8-119">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バッチファイルのパス**</span><span class="sxs-lookup"><span data-stu-id="2abc8-119">**Path to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch file(s)**</span></span>  
 <span data-ttu-id="2abc8-120">1 つ以上のバッチ ファイルを分析できます。</span><span class="sxs-lookup"><span data-stu-id="2abc8-120">You can analyze one or more batch files.</span></span> <span data-ttu-id="2abc8-121">場所を参照して複数のファイルを選択したり、複数のファイル名を入力できます。</span><span class="sxs-lookup"><span data-stu-id="2abc8-121">You can browse to a location and select multiple files, or you can type multiple file names.</span></span> <span data-ttu-id="2abc8-122">各ファイルへの完全パス名およびファイル名を使用し、パイプ文字 (|) でエントリを区切ります。</span><span class="sxs-lookup"><span data-stu-id="2abc8-122">Use the full path name to each file, include the file name, and separate entries by using the pipe character (|).</span></span>  
  
 <span data-ttu-id="2abc8-123">[ **SQL バッチファイルの分析**] を有効にすると、パス名とファイル名を入力するまで **[次へ**] ボタンが無効になります。</span><span class="sxs-lookup"><span data-stu-id="2abc8-123">If you enable **Analyze SQL batch file(s)**, the **Next** button is disabled until you enter a path name and a file name.</span></span>  
  
 <span data-ttu-id="2abc8-124">**[SQL バッチ区切り記号]**</span><span class="sxs-lookup"><span data-stu-id="2abc8-124">**SQL Batch Separator**</span></span>  
 <span data-ttu-id="2abc8-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの個別のバッチに使用するテキストです。</span><span class="sxs-lookup"><span data-stu-id="2abc8-125">The text that is used to separate batches of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="2abc8-126">既定値は **[** 実行] です。</span><span class="sxs-lookup"><span data-stu-id="2abc8-126">The default value is **GO**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abc8-127">参照</span><span class="sxs-lookup"><span data-stu-id="2abc8-127">See Also</span></span>  
 <span data-ttu-id="2abc8-128">[アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="2abc8-128">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="2abc8-129">アップグレード アドバイザーのユーザー インターフェイス リファレンス</span><span class="sxs-lookup"><span data-stu-id="2abc8-129">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
