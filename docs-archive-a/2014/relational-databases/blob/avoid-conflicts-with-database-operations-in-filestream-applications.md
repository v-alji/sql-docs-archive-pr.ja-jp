---
title: FILESTREAM アプリケーションでのデータベース操作との競合の回避 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Win32 and Transact-SQL Conflicts
ms.assetid: 8b1ee196-69af-4f9b-9bf5-63d8ac2bc39b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0ac7e681766396d3a3b4412d91a968b4cdc653c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643992"
---
# <a name="avoid-conflicts-with-database-operations-in-filestream-applications"></a><span data-ttu-id="c859b-102">FILESTREAM アプリケーションでのデータベース操作との競合の回避</span><span class="sxs-lookup"><span data-stu-id="c859b-102">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>
  <span data-ttu-id="c859b-103">SqlOpenFilestream() により Win32 ファイル ハンドルを開いて FILESTREAM BLOB データの読み取りまたは書き込みを行うアプリケーションでは、共通のトランザクションで管理される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで競合エラーが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c859b-103">Applications that use SqlOpenFilestream() to open Win32 file handles for reading or writing FILESTREAM BLOB data can encounter conflict errors with [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are managed in a common transaction.</span></span> <span data-ttu-id="c859b-104">この例として、完了までに時間がかかる [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリや MARS クエリなどがあります。</span><span class="sxs-lookup"><span data-stu-id="c859b-104">This includes [!INCLUDE[tsql](../../includes/tsql-md.md)] or MARS queries that take a long time to finish execution.</span></span> <span data-ttu-id="c859b-105">アプリケーションは、このような競合を回避できるように注意深く設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c859b-105">Applications must be carefully designed to help avoid these types of conflicts.</span></span>  
  
 <span data-ttu-id="c859b-106">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] またはアプリケーションが FILESTREAM BLOB を開こうとする場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によって、関連付けられたトランザクション コンテキストがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="c859b-106">When [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] or applications try to open FILESTREAM BLOBs, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] checks the associated transaction context.</span></span> <span data-ttu-id="c859b-107">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、DDL ステートメント、DML ステートメント、データの取得、トランザクションの管理のうち、どれが開く操作の対象になっているかに基づいて、要求を許可または拒否します。</span><span class="sxs-lookup"><span data-stu-id="c859b-107">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] allows or denies the request based on whether the open operation is working with DDL statements, DML statements, retrieving data, or managing transactions.</span></span> <span data-ttu-id="c859b-108">次の表は、トランザクションで開いているファイルの種類に基づいて、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ステートメントが許可されるか拒否されるかが、 [!INCLUDE[tsql](../../includes/tsql-md.md)] でどのように決まるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="c859b-108">The following table shows how the [!INCLUDE[ssDE](../../includes/ssde-md.md)] determines whether a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement will be allowed or denied based on the type of files that are open in the transaction.</span></span>  
  
|<span data-ttu-id="c859b-109">Transact-SQL ステートメント</span><span class="sxs-lookup"><span data-stu-id="c859b-109">Transact-SQL statements</span></span>|<span data-ttu-id="c859b-110">読み取り用に開く</span><span class="sxs-lookup"><span data-stu-id="c859b-110">Opened for read</span></span>|<span data-ttu-id="c859b-111">書き込み用に開く</span><span class="sxs-lookup"><span data-stu-id="c859b-111">Opened for write</span></span>|  
|------------------------------|---------------------|----------------------|  
|<span data-ttu-id="c859b-112">CREATE TABLE、CREATE INDEX、DROP TABLE、ALTER TABLE などの、データベース メタデータを処理する DDL ステートメント</span><span class="sxs-lookup"><span data-stu-id="c859b-112">DDL statements that work with database metadata, such as CREATE TABLE, CREATE INDEX, DROP TABLE, and ALTER TABLE.</span></span>|<span data-ttu-id="c859b-113">許可</span><span class="sxs-lookup"><span data-stu-id="c859b-113">Allowed</span></span>|<span data-ttu-id="c859b-114">ブロックされてタイムアウトで失敗</span><span class="sxs-lookup"><span data-stu-id="c859b-114">Are blocked and fail with a time-out.</span></span>|  
|<span data-ttu-id="c859b-115">UPDATE、DELETE、INSERT などの、データベース内に格納されているデータを処理する DML ステートメント</span><span class="sxs-lookup"><span data-stu-id="c859b-115">DML statements that work with the data that is stored in the database, such as UPDATE, DELETE, and INSERT.</span></span>|<span data-ttu-id="c859b-116">許可</span><span class="sxs-lookup"><span data-stu-id="c859b-116">Allowed</span></span>|<span data-ttu-id="c859b-117">拒否</span><span class="sxs-lookup"><span data-stu-id="c859b-117">Denied</span></span>|  
|<span data-ttu-id="c859b-118">SELECT</span><span class="sxs-lookup"><span data-stu-id="c859b-118">SELECT</span></span>|<span data-ttu-id="c859b-119">許可</span><span class="sxs-lookup"><span data-stu-id="c859b-119">Allowed</span></span>|<span data-ttu-id="c859b-120">許可</span><span class="sxs-lookup"><span data-stu-id="c859b-120">Allowed</span></span>|  
|<span data-ttu-id="c859b-121">COMMIT TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="c859b-121">COMMIT TRANSACTION</span></span>|<span data-ttu-id="c859b-122">拒否\*</span><span class="sxs-lookup"><span data-stu-id="c859b-122">Denied\*</span></span>|<span data-ttu-id="c859b-123">拒否\*</span><span class="sxs-lookup"><span data-stu-id="c859b-123">Denied\*.</span></span>|  
|<span data-ttu-id="c859b-124">SAVE TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="c859b-124">SAVE TRANSACTION</span></span>|<span data-ttu-id="c859b-125">拒否\*</span><span class="sxs-lookup"><span data-stu-id="c859b-125">Denied\*</span></span>|<span data-ttu-id="c859b-126">拒否\*</span><span class="sxs-lookup"><span data-stu-id="c859b-126">Denied\*</span></span>|  
|<span data-ttu-id="c859b-127">ROLLBACK</span><span class="sxs-lookup"><span data-stu-id="c859b-127">ROLLBACK</span></span>|<span data-ttu-id="c859b-128">許可\*</span><span class="sxs-lookup"><span data-stu-id="c859b-128">Allowed\*</span></span>|<span data-ttu-id="c859b-129">許可\*</span><span class="sxs-lookup"><span data-stu-id="c859b-129">Allowed\*</span></span>|  
  
 <span data-ttu-id="c859b-130">\* トランザクションは取り消され、トランザクション コンテキストで開かれたハンドルは無効になります。</span><span class="sxs-lookup"><span data-stu-id="c859b-130">\* The transaction is canceled, and open handles for the transaction context are invalidated.</span></span> <span data-ttu-id="c859b-131">アプリケーションは、開いているハンドルをすべて閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c859b-131">The application must close all open handles.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c859b-132">例</span><span class="sxs-lookup"><span data-stu-id="c859b-132">Examples</span></span>  
 <span data-ttu-id="c859b-133">次の例に、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントと FILESTREAM Win32 アクセスで競合が発生する可能性がある場合を示します。</span><span class="sxs-lookup"><span data-stu-id="c859b-133">The following examples show how [!INCLUDE[tsql](../../includes/tsql-md.md)] statements and FILESTREAM Win32 access can cause conflicts.</span></span>  
  
### <a name="a-opening-a-filestream-blob-for-write-access"></a><span data-ttu-id="c859b-134">A.</span><span class="sxs-lookup"><span data-stu-id="c859b-134">A.</span></span> <span data-ttu-id="c859b-135">書き込みアクセス用に FILESTREAM BLOB を開く</span><span class="sxs-lookup"><span data-stu-id="c859b-135">Opening a FILESTREAM BLOB for write access</span></span>  
 <span data-ttu-id="c859b-136">次の例は、書き込み専用アクセスでファイルを開いた場合の影響を示しています。</span><span class="sxs-lookup"><span data-stu-id="c859b-136">The following example shows the effect of opening a file for write access only.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//Write some date to the FILESTREAM BLOB.  
WriteFile(dstHandle, updateData, ...);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed. The FILESTREAM BLOB is  
//returned without the modifications that are made by  
//WriteFile(dstHandle, updateData, ...).  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed. The FILESTREAM BLOB  
//is returned with the updateData applied.  
```  
  
### <a name="b-opening-a-filestream-blob-for-read-access"></a><span data-ttu-id="c859b-137">B.</span><span class="sxs-lookup"><span data-stu-id="c859b-137">B.</span></span> <span data-ttu-id="c859b-138">読み取りアクセス用に FILESTREAM BLOB を開く</span><span class="sxs-lookup"><span data-stu-id="c859b-138">Opening a FILESTREAM BLOB for read access</span></span>  
 <span data-ttu-id="c859b-139">次の例は、読み取り専用アクセスでファイルを開いた場合の影響を示しています。</span><span class="sxs-lookup"><span data-stu-id="c859b-139">The following example shows the effect of opening a file for read access only.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed. Any changes that are  
//made to the FILESTREAM BLOB will not be returned until  
//the dstHandle is closed.  
//SELECT statements will be allowed.  
CloseHandle(dstHandle);  
  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="c-opening-and-closing-multiple-filestream-blob-files"></a><span data-ttu-id="c859b-140">C.</span><span class="sxs-lookup"><span data-stu-id="c859b-140">C.</span></span> <span data-ttu-id="c859b-141">複数の FILESTREAM BLOB ファイルを開いて閉じる</span><span class="sxs-lookup"><span data-stu-id="c859b-141">Opening and closing multiple FILESTREAM BLOB files</span></span>  
 <span data-ttu-id="c859b-142">複数のファイルが開いている場合は、最も厳しい規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c859b-142">If multiple files are open, the most restrictive rule is used.</span></span> <span data-ttu-id="c859b-143">2 つのファイルを開く例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c859b-143">The following example opens two files.</span></span> <span data-ttu-id="c859b-144">最初のファイルは読み取り用に、2 番目のファイルは書き込み用に開かれます。</span><span class="sxs-lookup"><span data-stu-id="c859b-144">The first file is opened for read and the second for write.</span></span> <span data-ttu-id="c859b-145">DML ステートメントは、2 番目のファイルが開かれるまで拒否されます。</span><span class="sxs-lookup"><span data-stu-id="c859b-145">DML statements will be denied until the second file is opened.</span></span>  
  
```  
dstHandle =  OpenSqlFilestream(dstFilePath, Read, 0,  
    transactionToken, cbTransactionToken, 0);  
//DDL statements will be denied.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
  
dstHandle1 =  OpenSqlFilestream(dstFilePath1, Write, 0,  
    transactionToken, cbTransactionToken, 0);  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
//Close the read handle. The write handle is still open.  
CloseHandle(dstHandle);  
//DML statements are still denied because the write handle is open.  
  
//DDL statements will be denied.  
//DML statements will be denied.  
//SELECT statements will be allowed.  
  
CloseHandle(dstHandle1);  
//DDL statements will be allowed.  
//DML statements will be allowed.  
//SELECT statements will be allowed.  
```  
  
### <a name="d-failing-to-close-a-cursor"></a><span data-ttu-id="c859b-146">D.</span><span class="sxs-lookup"><span data-stu-id="c859b-146">D.</span></span> <span data-ttu-id="c859b-147">カーソルが閉じられていない</span><span class="sxs-lookup"><span data-stu-id="c859b-147">Failing to close a cursor</span></span>  
 <span data-ttu-id="c859b-148">次の例では、ステートメントのカーソルが閉じられていないために、 `OpenSqlFilestream()` で書き込みアクセス用に BLOB を開くことができない場合を示しています。</span><span class="sxs-lookup"><span data-stu-id="c859b-148">The following example shows how a statement cursor that is not closed can prevent `OpenSqlFilestream()` from opening the BLOB for write access.</span></span>  
  
```  
TCHAR *sqlDBQuery =  
TEXT("SELECT GET_FILESTREAM_TRANSACTION_CONTEXT(),")  
TEXT("Chart.PathName() FROM Archive.dbo.Records");  
  
//Execute a long-running Transact-SQL statement. Do not allow  
//the statement to complete before trying to  
//open the file.  
  
SQLExecDirect(hstmt, sqlDBQuery, SQL_NTS);  
  
//Before you call OpenSqlFilestream() any open files  
//that the Cursor the Transact-SQL statement is using  
// must be closed. In this example,  
//SQLCloseCursor(hstmt) is not called so that  
//the transaction will indicate that there is a file  
//open for reading. This will cause the call to  
//OpenSqlFilestream() to fail because the file is  
//still open.  
  
HANDLE srcHandle =  OpenSqlFilestream(srcFilePath,  
     Write, 0,  transactionToken,  cbTransactionToken,  0);  
  
//srcHandle will == INVALID_HANDLE_VALUE because the  
//cursor is still open.  
```  
  
## <a name="see-also"></a><span data-ttu-id="c859b-149">参照</span><span class="sxs-lookup"><span data-stu-id="c859b-149">See Also</span></span>  
 <span data-ttu-id="c859b-150">[OpenSqlFilestream による FILESTREAM データへのアクセス](access-filestream-data-with-opensqlfilestream.md) </span><span class="sxs-lookup"><span data-stu-id="c859b-150">[Access FILESTREAM Data with OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) </span></span>  
 [<span data-ttu-id="c859b-151">複数のアクティブな結果セット &#40;MARS&#41; の使用</span><span class="sxs-lookup"><span data-stu-id="c859b-151">Using Multiple Active Result Sets &#40;MARS&#41;</span></span>](../native-client/features/using-multiple-active-result-sets-mars.md)  
  
  
