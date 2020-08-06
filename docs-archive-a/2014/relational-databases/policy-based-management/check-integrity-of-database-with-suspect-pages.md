---
title: 問題のあるページを含むデータベースの整合性のチェック | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cc1f87917c78f34ec7722fa21a1a67fda40a8c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711901"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a><span data-ttu-id="093fb-102">問題のあるページを含むデータベースの整合性のチェック</span><span class="sxs-lookup"><span data-stu-id="093fb-102">Check Integrity of Database with Suspect Pages</span></span>
  <span data-ttu-id="093fb-103">このルールでは、データベースの状態が問題ありに設定されているユーザー データベースがないか確認します。</span><span class="sxs-lookup"><span data-stu-id="093fb-103">This rule checks for user databases that have the database status set to suspect.</span></span> <span data-ttu-id="093fb-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] が 824 エラーを含むデータベース ページを読み取ると、そのページは問題があると見なされ、そのページ ID が msdb の suspect_pages テーブルに記録されます。また、そのページを含むデータベースは問題ありに設定されます。</span><span class="sxs-lookup"><span data-stu-id="093fb-104">When the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] reads a database page that contains an 824 error, the page is considered suspect, its page ID is recorded in the suspect_pages table in msdb, and the database that contains the page is set to suspect.</span></span>  
  
 <span data-ttu-id="093fb-105">エラー 824 は、読み取り操作中に論理的な一貫性エラーが検出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="093fb-105">Error 824 indicates that a logical consistency error was detected during a read operation.</span></span> <span data-ttu-id="093fb-106">このエラーは、多くの場合、I/O サブシステムのコンポーネントの障害によりデータが破損したことを示します。</span><span class="sxs-lookup"><span data-stu-id="093fb-106">This error frequently indicates data corruption caused by a faulty I/O subsystem component.</span></span> <span data-ttu-id="093fb-107">このエラー状態は深刻で、データベースの整合性を損なう可能性があるので、すぐに解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="093fb-107">This is a severe error condition that threatens database integrity and must be corrected immediately.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="093fb-108">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="093fb-108">Best Practices Recommendations</span></span>  
  
-   <span data-ttu-id="093fb-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査して、このデータベースの 824 エラーの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="093fb-109">Review the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log for the details of the 824 error for this database.</span></span>  
  
-   <span data-ttu-id="093fb-110">完全なデータベース整合性確認 ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)) を実行します。</span><span class="sxs-lookup"><span data-stu-id="093fb-110">Complete a full database consistency check ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)).</span></span>  
  
-   <span data-ttu-id="093fb-111">[MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397)で定義されているユーザー操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="093fb-111">Implement the user actions that are defined in [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397).</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="093fb-112">詳細情報</span><span class="sxs-lookup"><span data-stu-id="093fb-112">For More Information</span></span>  
 [<span data-ttu-id="093fb-113">suspect_pages テーブルの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="093fb-113">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
