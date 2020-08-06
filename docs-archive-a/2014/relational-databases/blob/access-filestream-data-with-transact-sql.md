---
title: Transact-SQL による FILESTREAM データへのアクセス | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Transact-SQL
ms.assetid: a6bf0ce7-7e5e-4a07-8917-ee526c9d0a05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06d395f1acc3723fc6b45fdfa08efbae354d8014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718290"
---
# <a name="access-filestream-data-with-transact-sql"></a><span data-ttu-id="cd677-102">Transact-SQL による FILESTREAM データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="cd677-102">Access FILESTREAM Data with Transact-SQL</span></span>
  <span data-ttu-id="cd677-103">このトピックでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] の INSERT、UPDATE、および DELETE ステートメントを使用して FILESTREAM データを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd677-103">This topic describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT, UPDATE, and DELETE statements to manage FILESTREAM data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd677-104">このトピックの例を実行するには、「 [FILESTREAM が有効なデータベースを作成する方法](create-a-filestream-enabled-database.md) 」および「 [FILESTREAM データを格納するテーブルを作成する方法](create-a-table-for-storing-filestream-data.md)」に基づいて、FILESTREAM が有効なデータベースとテーブルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd677-104">The examples in this topic require the FILESTREAM-enabled database and table that are created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md) and [Create a Table for Storing FILESTREAM Data](create-a-table-for-storing-filestream-data.md).</span></span>  
  
##  <a name="inserting-a-row-that-contains-filestream-data"></a><a name="ins"></a> <span data-ttu-id="cd677-105">FILESTREAM データを含む行の挿入</span><span class="sxs-lookup"><span data-stu-id="cd677-105">Inserting a Row That Contains FILESTREAM Data</span></span>  
 <span data-ttu-id="cd677-106">FILESTREAM データをサポートするテーブルに行を追加するには、 [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd677-106">To add a row to a table that supports FILESTREAM data, use the [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT statement.</span></span> <span data-ttu-id="cd677-107">FILESTREAM 列にデータを挿入するときに、NULL または値を挿入でき `varbinary(max)` ます。</span><span class="sxs-lookup"><span data-stu-id="cd677-107">When you insert data into a FILESTREAM column, you can insert NULL or a `varbinary(max)` value.</span></span>  
  
### <a name="inserting-null"></a><span data-ttu-id="cd677-108">NULL の挿入</span><span class="sxs-lookup"><span data-stu-id="cd677-108">Inserting NULL</span></span>  
 <span data-ttu-id="cd677-109">`NULL`を挿入する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cd677-109">The following example shows how to insert `NULL`.</span></span> <span data-ttu-id="cd677-110">FILESTREAM 値が `NULL`の場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] はファイル システムにファイルを作成しません。</span><span class="sxs-lookup"><span data-stu-id="cd677-110">When the FILESTREAM value is `NULL`, the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not create a file in the file system.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertNULL](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertnull)]  
  
### <a name="inserting-a-zero-length-record"></a><span data-ttu-id="cd677-111">長さ 0 のレコードの挿入</span><span class="sxs-lookup"><span data-stu-id="cd677-111">Inserting a Zero-Length Record</span></span>  
 <span data-ttu-id="cd677-112">`INSERT` を使用して長さ 0 のレコードを作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cd677-112">The following example shows how to use `INSERT` to create a zero-length record.</span></span> <span data-ttu-id="cd677-113">これは、ファイル ハンドルを取得する必要がある場合に役立ちますが、Win32 API を使用してファイルを操作します。</span><span class="sxs-lookup"><span data-stu-id="cd677-113">This is useful for when you want to obtain a file handle, but will be manipulating the file by using Win32 APIs.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertZero](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertzero)]  
  
### <a name="creating-a-data-file"></a><span data-ttu-id="cd677-114">データ ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="cd677-114">Creating a Data File</span></span>  
 <span data-ttu-id="cd677-115">`INSERT` を使用して、データを含むファイルを作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cd677-115">The following example shows how to use `INSERT` to create a file that contains data.</span></span> <span data-ttu-id="cd677-116">[!INCLUDE[ssDE](../../includes/ssde-md.md)] によって、文字列 `Seismic Data` が `varbinary(max)` 値に変換されます。</span><span class="sxs-lookup"><span data-stu-id="cd677-116">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] converts the string `Seismic Data` to a `varbinary(max)` value.</span></span> <span data-ttu-id="cd677-117">Windows ファイルが存在しない場合は、FILESTREAM によってそのファイルが作成されます。その後にデータがデータ ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="cd677-117">FILESTREAM creates the Windows file if it does not already exist.The data is then added to the data file.</span></span>  
  
 [!code-sql[FILESTREAM#FS_InsertData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_insertdata)]  
  
 <span data-ttu-id="cd677-118">すべてのデータを `Archive`.`dbo.Records`</span><span class="sxs-lookup"><span data-stu-id="cd677-118">When you select all data from the `Archive`.`dbo.Records`</span></span> <span data-ttu-id="cd677-119">テーブルから選択すると、次の表に示すような結果になります。</span><span class="sxs-lookup"><span data-stu-id="cd677-119">table, the results are similar to the results that are shown in the following table.</span></span> <span data-ttu-id="cd677-120">ただし、 `Id` 列に格納される GUID は異なります。</span><span class="sxs-lookup"><span data-stu-id="cd677-120">However, the `Id` column will contain different GUIDs.</span></span>  
  
|<span data-ttu-id="cd677-121">Id</span><span class="sxs-lookup"><span data-stu-id="cd677-121">Id</span></span>|<span data-ttu-id="cd677-122">SerialNumber</span><span class="sxs-lookup"><span data-stu-id="cd677-122">SerialNumber</span></span>|<span data-ttu-id="cd677-123">再開</span><span class="sxs-lookup"><span data-stu-id="cd677-123">Resume</span></span>|  
|--------|------------------|------------|  
|`C871B90F-D25E-47B3-A560-7CC0CA405DAC`|`1`|`NULL`|  
|`F8F5C314-0559-4927-8FA9-1535EE0BDF50`|`2`|`0x`|  
|`7F680840-B7A4-45D4-8CD5-527C44D35B3F`|`3`|`0x536569736D69632044617461`|  
  
##  <a name="updating-filestream-data"></a><a name="upd"></a> <span data-ttu-id="cd677-124">FILESTREAM データを更新する</span><span class="sxs-lookup"><span data-stu-id="cd677-124">Updating FILESTREAM Data</span></span>  
 <span data-ttu-id="cd677-125">[!INCLUDE[tsql](../../includes/tsql-md.md)] を使用すると、ファイル システムのファイルのデータを更新できます。ただし、大量のデータをファイルにストリーミングする必要があるときには、この操作は適していません。</span><span class="sxs-lookup"><span data-stu-id="cd677-125">You can use [!INCLUDE[tsql](../../includes/tsql-md.md)] to update the data in the file system file; although, you might not want to do this when you have to stream large amounts of data to a file.</span></span>  
  
 <span data-ttu-id="cd677-126">ファイル レコード内の任意のテキストを、 `Xray 1`というテキストに置換する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cd677-126">The following example replaces any text in the file record with the text `Xray 1`.</span></span>  
  
 [!code-sql[FILESTREAM#FS_UpdateData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_updatedata)]  
  
##  <a name="deleting-filestream-data"></a><a name="del"></a> <span data-ttu-id="cd677-127">FILESTREAM データの削除</span><span class="sxs-lookup"><span data-stu-id="cd677-127">Deleting FILESTREAM Data</span></span>  
 <span data-ttu-id="cd677-128">FILESTREAM フィールドを含む行を削除すると、その基となるファイル システム ファイルも削除されます。</span><span class="sxs-lookup"><span data-stu-id="cd677-128">When you delete a row that contains a FILESTREAM field, you also delete its underlying file system files.</span></span> <span data-ttu-id="cd677-129">行、したがってファイルを削除する唯一の方法は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE ステートメントを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="cd677-129">The only way to delete a row, and therefore the file, is to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] DELETE statement.</span></span>  
  
 <span data-ttu-id="cd677-130">行およびそれに関連付けられているファイル システム ファイルを削除する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cd677-130">The following example shows how to delete a row and its associated file system files.</span></span>  
  
 [!code-sql[FILESTREAM#FS_DeleteData](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_deletedata)]  
  
 <span data-ttu-id="cd677-131">すべてのデータを `dbo.Archive` テーブルから選択すると、その行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="cd677-131">When you select all data from the `dbo.Archive` table, the row is gone.</span></span> <span data-ttu-id="cd677-132">関連付けられていたファイルは使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cd677-132">You can no longer use the associated file.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd677-133">基になるファイルは、FILESTREAM ガベージ コレクターによって削除されます。</span><span class="sxs-lookup"><span data-stu-id="cd677-133">The underlying files are removed by the FILESTREAM garbage collector.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd677-134">参照</span><span class="sxs-lookup"><span data-stu-id="cd677-134">See Also</span></span>  
 <span data-ttu-id="cd677-135">[FILESTREAM の有効化と構成](enable-and-configure-filestream.md) </span><span class="sxs-lookup"><span data-stu-id="cd677-135">[Enable and Configure FILESTREAM](enable-and-configure-filestream.md) </span></span>  
 [<span data-ttu-id="cd677-136">FILESTREAM アプリケーションでのデータベース操作との競合の回避</span><span class="sxs-lookup"><span data-stu-id="cd677-136">Avoid Conflicts with Database Operations in FILESTREAM Applications</span></span>](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
