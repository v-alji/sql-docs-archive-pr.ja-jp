---
title: トレースと Windows パフォーマンス ログ データの関連付け | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- correlating trace with log data
- logs [SQL Server], traces
- Profiler [SQL Server Profiler], correlating trace with log data
- traces [SQL Server], logs
- SQL Server Profiler, correlating trace with log data
ms.assetid: 1e4412c8-d27c-4aae-9b35-214128d1d00a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 879441c948f0ad04b971159a37ec0dcec90e3ada
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711281"
---
# <a name="correlate-a-trace-with-windows-performance-log-data"></a>トレースと Windows パフォーマンス ログ データの関連付け
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用すると、Microsoft Windows パフォーマンス ログを開き、トレースと関連付けるカウンターを選択し、選択したパフォーマンス カウンターをトレースと共に [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のグラフィカル ユーザー インターフェイスに表示できます。 トレース ウィンドウでイベントを選択すると、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] の [システム モニター] データ ウィンドウ画面の赤い縦棒で、選択したトレース イベントに関連付けられているパフォーマンス ログ データが示されます。  
  
 トレースをパフォーマンス カウンターに関連付けるには、**StartTime** および **EndTime** データ列を含んでいるトレース ファイルまたはテーブルを開き、**の**[ファイル][!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] メニューで **[パフォーマンス データのインポート]** をクリックします。 パフォーマンス ログを開き、トレースに関連付けるシステム モニター オブジェクトおよびカウンターを選択します。  
  
## <a name="see-also"></a>参照  
 [トレースと Windows パフォーマンス ログ データの関連付け &#40;SQL Server Profiler&#41;](correlate-a-trace-with-windows-performance-log-data.md)  
  
  
