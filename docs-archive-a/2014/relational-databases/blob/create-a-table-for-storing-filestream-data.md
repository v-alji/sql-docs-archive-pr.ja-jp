---
title: FILESTREAM データを格納するテーブルを作成する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], table storage
ms.assetid: 029c3059-5c83-43e2-a859-9027031b7de1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 484d7b58ce949df79dc7e17ee4dc7307b70c0154
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715409"
---
# <a name="create-a-table-for-storing-filestream-data"></a><span data-ttu-id="cd7f7-102">FILESTREAM データを格納するテーブルを作成する方法</span><span class="sxs-lookup"><span data-stu-id="cd7f7-102">Create a Table for Storing FILESTREAM Data</span></span>
  <span data-ttu-id="cd7f7-103">このトピックでは、FILESTREAM データを格納するテーブルを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-103">This topic shows how to create a table for storing FILESTREAM data.</span></span>  
  
 <span data-ttu-id="cd7f7-104">データベースに FILESTREAM ファイル グループが含まれているときは、FILESTREAM データを格納するテーブルを作成または変更できます。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-104">When the database has a FILESTREAM filegroup, you can create or modify tables to store FILESTREAM data.</span></span> <span data-ttu-id="cd7f7-105">列に FILESTREAM データが含まれていることを指定するために、`varbinary(max)` 列を作成し、FILESTREAM 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-105">To specify that a column contains FILESTREAM data, you create a `varbinary(max)` column and add the FILESTREAM attribute.</span></span>  
  
### <a name="to-create-a-table-to-store-filestream-data"></a><span data-ttu-id="cd7f7-106">FILESTREAM データを格納するテーブルを作成するには</span><span class="sxs-lookup"><span data-stu-id="cd7f7-106">To create a table to store FILESTREAM data</span></span>  
  
1.  <span data-ttu-id="cd7f7-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[新しいクエリ]** をクリックしてクエリ エディターを表示します。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-107">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
2.  <span data-ttu-id="cd7f7-108">次の例からクエリ エディターに [!INCLUDE[tsql](../../includes/tsql-md.md)] コードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-108">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] code from the following example into the Query Editor.</span></span> <span data-ttu-id="cd7f7-109">この [!INCLUDE[tsql](../../includes/tsql-md.md)] コードによって、Records という FILESTREAM が有効なテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-109">This [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a FILESTREAM-enabled table called Records.</span></span>  
  
3.  <span data-ttu-id="cd7f7-110">テーブルを作成するには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-110">To create the table, click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd7f7-111">例</span><span class="sxs-lookup"><span data-stu-id="cd7f7-111">Example</span></span>  
 <span data-ttu-id="cd7f7-112">次のコード例では、 `Records`という名前のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-112">The following code example shows how to create a table that is named `Records`.</span></span> <span data-ttu-id="cd7f7-113">`Id` 列は `ROWGUIDCOL` 列で、Win32 API で FILESTREAM を使用する場合に必要となります。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-113">The `Id` column is a `ROWGUIDCOL` column and is required to use FILESTREAM data with Win32 APIs.</span></span> <span data-ttu-id="cd7f7-114">`SerialNumber` 列は `UNIQUE INTEGER`です。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-114">The `SerialNumber` column is a `UNIQUE INTEGER`.</span></span> <span data-ttu-id="cd7f7-115">`Chart` 列は `FILESTREAM` 列で、 `Chart` をファイル システムに格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-115">The `Chart` column is a `FILESTREAM` column and is used to store the `Chart` in the file system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd7f7-116">この例では、「 [FILESTREAM が有効なデータベースを作成する方法](create-a-filestream-enabled-database.md)」で作成した Archive データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="cd7f7-116">This example refers to the Archive database that is created in [Create a FILESTREAM-Enabled Database](create-a-filestream-enabled-database.md).</span></span>  
  
 [!code-sql[FILESTREAM#FS_CreateTable](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_createtable)]  
  
## <a name="see-also"></a><span data-ttu-id="cd7f7-117">参照</span><span class="sxs-lookup"><span data-stu-id="cd7f7-117">See Also</span></span>  
 <span data-ttu-id="cd7f7-118">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cd7f7-118">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 [<span data-ttu-id="cd7f7-119">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cd7f7-119">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
