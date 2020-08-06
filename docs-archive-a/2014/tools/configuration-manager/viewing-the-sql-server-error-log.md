---
title: SQL Server のエラーログを表示する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- cycling SQL Server error log
- viewing SQL Server error log
- errors [SQL Server], logs
- SQL Server error log
- displaying SQL Server error log
- logs [SQL Server], SQL Server error logs
ms.assetid: 6908c21a-65e3-458f-a272-fee256d86448
author: stevestein
ms.author: sstein
ms.openlocfilehash: 822ae4fba589f005aaee41857a9db3388a309254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630730"
---
# <a name="viewing-the-sql-server-error-log"></a><span data-ttu-id="bae6d-102">SQL Server エラー ログの表示</span><span class="sxs-lookup"><span data-stu-id="bae6d-102">Viewing the SQL Server Error Log</span></span>
  <span data-ttu-id="bae6d-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを表示すると、バックアップ操作および復元操作、バッチ コマンド、その他のスクリプトやプロセスなどが正常に終了したことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="bae6d-103">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to ensure that processes have completed successfully (for example, backup and restore operations, batch commands, or other scripts and processes).</span></span> <span data-ttu-id="bae6d-104">これは、自動復旧メッセージ (特に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが停止してから再起動した場合)、カーネル メッセージ、またはその他のサーバー レベルのエラー メッセージを含んでいて、現在または潜在的に問題がある領域を検出するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="bae6d-104">This can be helpful to detect any current or potential problem areas, including automatic recovery messages (particularly if an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has been stopped and restarted), kernel messages, or other server-level error messages.</span></span>  
  
 <span data-ttu-id="bae6d-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または任意のテキスト エディターを使用して表示します。</span><span class="sxs-lookup"><span data-stu-id="bae6d-105">View the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any text editor.</span></span> <span data-ttu-id="bae6d-106">エラー ログの確認方法の詳細については、「 [[ログ ファイルの表示] を開く](../../relational-databases/logs/log-file-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bae6d-106">For more information about how to view the error log, see [Open Log File Viewer](../../relational-databases/logs/log-file-viewer.md).</span></span> <span data-ttu-id="bae6d-107">エラー ログの既定の場所は、 `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` ファイルおよび `ERRORLOG.`*n* ファイルです。</span><span class="sxs-lookup"><span data-stu-id="bae6d-107">By default, the error log is located at `Program Files\Microsoft SQL Server\MSSQL.`*n*`\MSSQL\LOG\ERRORLOG` and `ERRORLOG.`*n* files.</span></span>  
  
 <span data-ttu-id="bae6d-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを起動するたびに、新しいエラー ログが作成されます。ただし、 [sp_cycle_errorlog](/sql/relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql) システム ストアド プロシージャを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動しなくてもエラー ログ ファイルを使い回すことができます。</span><span class="sxs-lookup"><span data-stu-id="bae6d-108">A new error log is created each time an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started, although the [sp_cycle_errorlog](/sql/relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql) system stored procedure can be used to cycle the error log files without having to restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bae6d-109">一般的に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではログのバックアップが新しいものから 6 つ保持されます。最新のログ バックアップの拡張子は .1、2 番目に新しいログ バックアップの拡張子は .2 で、以降同様に続きます。</span><span class="sxs-lookup"><span data-stu-id="bae6d-109">Typically, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retains backups of the previous six logs and gives the most recent log backup the extension .1, the second most recent the extension .2, and so on.</span></span> <span data-ttu-id="bae6d-110">現在のエラー ログには拡張子がありません。</span><span class="sxs-lookup"><span data-stu-id="bae6d-110">The current error log has no extension.</span></span>  
  
 <span data-ttu-id="bae6d-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがオフラインになっている場合または起動できない場合も、そのインスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを表示できます。</span><span class="sxs-lookup"><span data-stu-id="bae6d-111">Be aware that you can also view the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log on instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are offline or cannot start.</span></span> <span data-ttu-id="bae6d-112">詳細については、「 [オフライン ログ ファイルの表示](../../relational-databases/logs/view-offline-log-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bae6d-112">For more information, see [View Offline Log Files](../../relational-databases/logs/view-offline-log-files.md).</span></span>  
  
  
