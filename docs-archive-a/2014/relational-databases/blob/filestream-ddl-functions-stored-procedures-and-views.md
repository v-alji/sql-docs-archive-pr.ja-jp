---
title: FILESTREAM DDL、関数、ストアド プロシージャ、およびビュー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dffcc454d21a0a8dea0e98c4db2c19a4af29e948
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631092"
---
# <a name="filestream-ddl-functions-stored-procedures-and-views"></a><span data-ttu-id="f5392-102">FILESTREAM DDL、関数、ストアド プロシージャ、およびビュー</span><span class="sxs-lookup"><span data-stu-id="f5392-102">FILESTREAM DDL, Functions, Stored Procedures, and Views</span></span>
  <span data-ttu-id="f5392-103">FILESTREAM をサポートする Transact-SQL ステートメントおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース オブジェクトの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f5392-103">Lists the Transact-SQL statements and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database objects that support FILESTREAM.</span></span>  
  
 <span data-ttu-id="f5392-104">FileTable 機能をサポートするデータベース オブジェクトの一覧については、「 [FileTable DDL, Functions, Stored Procedures, and Views](../views/views.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5392-104">For the list of database objects that support the FileTable feature, see [FileTable DDL, Functions, Stored Procedures, and Views](../views/views.md).</span></span>  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> <span data-ttu-id="f5392-105">Transact-SQL データ定義言語 (DDL) ステートメント</span><span class="sxs-lookup"><span data-stu-id="f5392-105">Transact-SQL Data Definition Language (DDL) Statements</span></span>  
  
-   [<span data-ttu-id="f5392-106">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-106">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [<span data-ttu-id="f5392-107">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-107">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [<span data-ttu-id="f5392-108">CREATE TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-108">CREATE TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-table-transact-sql)  
  
-   [<span data-ttu-id="f5392-109">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-109">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
-   [<span data-ttu-id="f5392-110">CREATE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-110">CREATE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-index-transact-sql)  
  
-   <span data-ttu-id="f5392-111">[DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)DROP INDEX</span><span class="sxs-lookup"><span data-stu-id="f5392-111">[DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)DROP INDEX</span></span>  
  
##  <a name="system-functions"></a><a name="func"></a> <span data-ttu-id="f5392-112">システム関数</span><span class="sxs-lookup"><span data-stu-id="f5392-112">System Functions</span></span>  
  
-   [<span data-ttu-id="f5392-113">GET_FILESTREAM_TRANSACTION_CONTEXT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-113">GET_FILESTREAM_TRANSACTION_CONTEXT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql)  
  
-   [<span data-ttu-id="f5392-114">PathName &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-114">PathName &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/pathname-transact-sql)  
  
##  <a name="system-stored-procedures"></a><a name="proc"></a> <span data-ttu-id="f5392-115">システム ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f5392-115">System Stored Procedures</span></span>  
  
-   [<span data-ttu-id="f5392-116">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-116">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [<span data-ttu-id="f5392-117">sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-117">sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection)  
  
##  <a name="system-views---catalog-views"></a><a name="cat"></a> <span data-ttu-id="f5392-118">システム ビュー - カタログ ビュー</span><span class="sxs-lookup"><span data-stu-id="f5392-118">System Views - Catalog Views</span></span>  
  
-   [<span data-ttu-id="f5392-119">sys.database_filestream_options &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-119">sys.database_filestream_options &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> <span data-ttu-id="f5392-120">システム ビュー - 動的管理ビュー</span><span class="sxs-lookup"><span data-stu-id="f5392-120">System Views - Dynamic Management Views</span></span>  
  
-   [<span data-ttu-id="f5392-121">sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-121">sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql)  
  
-   [<span data-ttu-id="f5392-122">sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5392-122">sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql)  
  
##  <a name="programming-apis"></a><a name="api"></a> <span data-ttu-id="f5392-123">プログラミング API</span><span class="sxs-lookup"><span data-stu-id="f5392-123">Programming APIs</span></span>  
  
-   [<span data-ttu-id="f5392-124">OpenSqlFilestream による FILESTREAM データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="f5392-124">Access FILESTREAM Data with OpenSqlFilestream</span></span>](access-filestream-data-with-opensqlfilestream.md)  
  
-   [<span data-ttu-id="f5392-125">マネージド API: SqlFileStream クラス</span><span class="sxs-lookup"><span data-stu-id="f5392-125">Managed API - SqlFileStream Class</span></span>](https://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
