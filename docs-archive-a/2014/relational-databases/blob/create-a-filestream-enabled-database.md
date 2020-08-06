---
title: FILESTREAM が有効なデータベースを作成する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FILESTREAM-enabled databases
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0fe6e5bc6e4f60bc0703482f3bf4d761104b3c5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716378"
---
# <a name="create-a-filestream-enabled-database"></a><span data-ttu-id="28e4f-102">FILESTREAM が有効なデータベースを作成する方法</span><span class="sxs-lookup"><span data-stu-id="28e4f-102">Create a FILESTREAM-Enabled Database</span></span>
  <span data-ttu-id="28e4f-103">このトピックでは、FILESTREAM をサポートするデータベースを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28e4f-103">This topic shows how to create a database that supports FILESTREAM.</span></span> <span data-ttu-id="28e4f-104">FILESTREAM は特殊なファイル グループを使用するので、データベースの作成時に少なくとも 1 つのファイル グループに対して CONTAINS FILESTREAM 句を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28e4f-104">Because FILESTREAM uses a special type of filegroup, when you create the database, you must specify the CONTAINS FILESTREAM clause for at least one filegroup.</span></span>  
  
 <span data-ttu-id="28e4f-105">FILESTREAM ファイル グループに、2 つ以上のファイルを含められます。</span><span class="sxs-lookup"><span data-stu-id="28e4f-105">A FILESTREAM filegroup can contain more than one file.</span></span> <span data-ttu-id="28e4f-106">複数のファイルを含む FILESTREAM ファイル グループの作成方法を示すコード例については、「 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28e4f-106">For a code example that demonstrates how to create a FILESTREAM filegroup that contains multiple files, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
### <a name="to-create-a-filestream-enabled-database"></a><span data-ttu-id="28e4f-107">FILESTREAM が有効なデータベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="28e4f-107">To create a FILESTREAM-enabled database</span></span>  
  
1.  <span data-ttu-id="28e4f-108">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[新しいクエリ]** をクリックしてクエリ エディターを表示します。</span><span class="sxs-lookup"><span data-stu-id="28e4f-108">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
2.  <span data-ttu-id="28e4f-109">コードをコピー [!INCLUDE[tsql](../../includes/tsql-md.md)] すると、Archive という名前の FILESTREAM が有効なデータベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="28e4f-109">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] code creates a FILESTREAM-enabled database called Archive.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="28e4f-110">このスクリプトでは、ディレクトリ C:\Data が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="28e4f-110">For this script, the directory C:\Data must exist.</span></span>  
  
3.  <span data-ttu-id="28e4f-111">データベースを構築するには、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28e4f-111">To build the database, click **Execute**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28e4f-112">例</span><span class="sxs-lookup"><span data-stu-id="28e4f-112">Example</span></span>  
 <span data-ttu-id="28e4f-113">次のコード例では、 `Archive`という名前のデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="28e4f-113">The following code example creates a database that is named `Archive`.</span></span> <span data-ttu-id="28e4f-114">このデータベースは、 `PRIMARY`、 `Arch1`、 `FileStreamGroup1`という 3 つのファイル グループを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="28e4f-114">The database contains three filegroups: `PRIMARY`, `Arch1`, and `FileStreamGroup1`.</span></span> <span data-ttu-id="28e4f-115">`PRIMARY` と `Arch1` は、FILESTREAM データを含むことのできない通常のファイル グループです。</span><span class="sxs-lookup"><span data-stu-id="28e4f-115">`PRIMARY` and `Arch1` are regular filegroups that cannot contain FILESTREAM data.</span></span> <span data-ttu-id="28e4f-116">`FileStreamGroup1` は、 `FILESTREAM` ファイル グループです。</span><span class="sxs-lookup"><span data-stu-id="28e4f-116">`FileStreamGroup1` is the `FILESTREAM` filegroup.</span></span>  
  
```sql  
CREATE DATABASE Archive   
ON  
PRIMARY ( NAME = Arch1,  
    FILENAME = 'c:\data\archdat1.mdf'),  
FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
    FILENAME = 'c:\data\filestream1')  
LOG ON  ( NAME = Archlog1,  
    FILENAME = 'c:\data\archlog1.ldf')  
GO  
```  
  
 <span data-ttu-id="28e4f-117">`FILESTREAM` ファイル グループに対しては、 `FILENAME` がパスを参照します。</span><span class="sxs-lookup"><span data-stu-id="28e4f-117">For a `FILESTREAM` filegroup, `FILENAME` refers to a path.</span></span> <span data-ttu-id="28e4f-118">最後のフォルダーまでのパスが存在する必要がありますが、最後のフォルダーは存在できません。</span><span class="sxs-lookup"><span data-stu-id="28e4f-118">The path up to the last folder must exist, and the last folder must not exist.</span></span> <span data-ttu-id="28e4f-119">この例では、 `c:\data` が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28e4f-119">In this example, `c:\data` must exist.</span></span> <span data-ttu-id="28e4f-120">ただし、 `filestream1` ステートメントを実行するときに `CREATE DATABASE` サブフォルダーが存在してはいけません。</span><span class="sxs-lookup"><span data-stu-id="28e4f-120">However, the `filestream1` subfolder cannot exist when you execute the `CREATE DATABASE` statement.</span></span> <span data-ttu-id="28e4f-121">構文の詳細については、「 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28e4f-121">For more information about the syntax, see [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql).</span></span>  
  
 <span data-ttu-id="28e4f-122">上の例を実行すると、c:\Data\filestream1 フォルダーに filestream.hdr ファイルと $FSLOG フォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="28e4f-122">After you run the previous example, a filestream.hdr file and an $FSLOG folder appears in the c:\Data\filestream1 folder.</span></span> <span data-ttu-id="28e4f-123">filestream.hdr ファイルは、FILESTREAM コンテナーのヘッダー ファイルです。</span><span class="sxs-lookup"><span data-stu-id="28e4f-123">The filestream.hdr file is a header file for the FILESTREAM container.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="28e4f-124">filestream.hdr ファイルは、重要なシステム ファイルです。</span><span class="sxs-lookup"><span data-stu-id="28e4f-124">The filestream.hdr file is an important system file.</span></span> <span data-ttu-id="28e4f-125">このファイルには、FILESTREAM ヘッダー情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="28e4f-125">It contains FILESTREAM header information.</span></span> <span data-ttu-id="28e4f-126">このファイルを削除したり変更したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="28e4f-126">Do not remove or modify this file.</span></span>  
  
 <span data-ttu-id="28e4f-127">既存のデータベースに対しては、 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) ステートメントを使用して FILESTREAM ファイル グループを追加できます。</span><span class="sxs-lookup"><span data-stu-id="28e4f-127">For existing databases, you can use the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql) statement to add a FILESTREAM filegroup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e4f-128">参照</span><span class="sxs-lookup"><span data-stu-id="28e4f-128">See Also</span></span>  
 <span data-ttu-id="28e4f-129">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="28e4f-129">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="28e4f-130">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="28e4f-130">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
