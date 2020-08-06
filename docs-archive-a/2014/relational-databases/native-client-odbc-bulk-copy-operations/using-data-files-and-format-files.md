---
title: データファイルとフォーマットファイルの使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e0ee92f79e2c8cab9605db0188e01898df8c23e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742029"
---
# <a name="using-data-files-and-format-files"></a><span data-ttu-id="b51f9-102">データ ファイルとフォーマット ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="b51f9-102">Using Data Files and Format Files</span></span>
  <span data-ttu-id="b51f9-103">最も単純な一括コピー プログラムでは次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-103">The simplest bulk copy program does the following:</span></span>  
  
1.  <span data-ttu-id="b51f9-104">[Bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を呼び出して、テーブルまたはビューからデータファイルへの一括コピー (BCP_OUT の設定) を指定します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-104">Calls [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to specify bulk copying out (set BCP_OUT) from a table or view to a data file.</span></span>  
  
2.  <span data-ttu-id="b51f9-105">[Bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)を呼び出して、一括コピー操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-105">Calls [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="b51f9-106">データ ファイルはネイティブ モードで作成されるので、テーブルやビューのすべての列から取得したデータは、データベースと同じ形式でデータ ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-106">The data file is created in native mode; therefore, data from all columns in the table or view are stored in the data file in the same format as in the database.</span></span> <span data-ttu-id="b51f9-107">その後、同様の手順を使用して、このデータ ファイルをサーバーに一括コピーできます。ただし、DB_OUT ではなく DB_IN を設定します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-107">The file can then be bulk copied into a server by using these same steps and setting DB_IN instead of DB_OUT.</span></span> <span data-ttu-id="b51f9-108">この操作は、コピー元のテーブルとコピー先のテーブルの構造が厳密に同じ場合にのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-108">This works only if both the source and target tables have exactly the same structure.</span></span> <span data-ttu-id="b51f9-109">結果のデータファイルは、 **/n** (ネイティブモード) スイッチを使用して**bcp**ユーティリティに入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-109">The resulting data file can also be input to the **bcp** utility by using the **/n** (native mode) switch.</span></span>  
  
 <span data-ttu-id="b51f9-110">テーブルやビューから直接取得するのではなく、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの結果セットを一括コピー出力するには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-110">To bulk copy out the result set of a [!INCLUDE[tsql](../../includes/tsql-md.md)] statement instead of directly from a table or view:</span></span>  
  
1.  <span data-ttu-id="b51f9-111">**Bcp_init**を呼び出して一括コピーを指定しますが、テーブル名には NULL を指定します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-111">Call **bcp_init** to specify bulk copying out, but specify NULL for the table name.</span></span>  
  
2.  <span data-ttu-id="b51f9-112">*EOption*を BCPHINTS に設定し、transact-sql ステートメントを含む sqltchar 文字列へのポインターを*ivalue*に設定して[bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-112">Call [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) with *eOption* set to BCPHINTS and *iValue* set to a pointer to a SQLTCHAR string containing the Transact-SQL statement.</span></span>  
  
3.  <span data-ttu-id="b51f9-113">**Bcp_exec**を呼び出して、一括コピー操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-113">Call **bcp_exec** to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="b51f9-114">結果セットを生成するステートメントであればどのような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントも使用できます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-114">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement can be any statement that generates a result set.</span></span> <span data-ttu-id="b51f9-115">作成されるデータ ファイルには [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの最初の結果セットが格納されます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-115">The data file is created containing the first result set of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="b51f9-116">[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで複数の結果セットが生成される場合、一括コピーでは、最初の結果セットよりも後にある結果セットは無視されます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-116">Bulk copy ignores any result set after the first if the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement generates multiple result sets.</span></span>  
  
 <span data-ttu-id="b51f9-117">列のデータがテーブルとは異なる形式で格納されるデータファイルを作成するには、 [bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)を呼び出して、変更する列の数を指定した後、形式を変更する各列に対して[bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-117">To create a data file in which column data is stored in a different format than in the table, call [bcp_columns](../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) to specify how many columns will be changed, then call [bcp_colfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) for each column whose format you want to change.</span></span> <span data-ttu-id="b51f9-118">これは、 **bcp_init**を呼び出した後、 **bcp_exec**を呼び出す前に行います。</span><span class="sxs-lookup"><span data-stu-id="b51f9-118">This is done after calling **bcp_init** but before calling **bcp_exec**.</span></span> <span data-ttu-id="b51f9-119">**bcp_colfmt**は、列のデータをデータファイルに格納する形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-119">**bcp_colfmt** specifies the format in which the column's data is stored in the data file.</span></span> <span data-ttu-id="b51f9-120">これは、一括コピー時に使用できます。**Bcp_colfmt**を使用して、行ターミネータと列ターミネータを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-120">It can be used when bulk copying in or out. You can also use **bcp_colfmt** to set the row and column terminators.</span></span> <span data-ttu-id="b51f9-121">たとえば、データにタブ文字が含まれていない場合は**bcp_colfmt**を使用してタブ区切りファイルを作成し、各列のターミネータとしてタブ文字を設定できます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-121">For example, if your data contains no tab characters, you can create a tab-delimited file by using **bcp_colfmt** to set the tab character as the terminator for each column.</span></span>  
  
 <span data-ttu-id="b51f9-122">**Bcp_colfmt**を一括コピーして使用する場合、 **bcp_colfmt**を最後に呼び出した後[bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)を呼び出すことによって作成したデータファイルを記述するフォーマットファイルを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-122">When bulk copying out and using **bcp_colfmt**, you can easily create a format file describing the data file you have created by calling [bcp_writefmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) after the last call to **bcp_colfmt**.</span></span>  
  
 <span data-ttu-id="b51f9-123">フォーマットファイルで記述されたデータファイルからを一括コピーする場合は、 **bcp_init**の後、 **bcp_exec**する前に[bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)を呼び出してフォーマットファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="b51f9-123">When bulk copying in from a data file described by a format file, read the format file by calling [bcp_readfmt](../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) after **bcp_init** but before **bcp_exec**.</span></span>  
  
 <span data-ttu-id="b51f9-124">**Bcp_control**関数は、データファイルからへの一括コピー時にいくつかのオプションを制御し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="b51f9-124">The **bcp_control** function controls several options when bulk copying into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a data file.</span></span> <span data-ttu-id="b51f9-125">**bcp_control**は、終了前のエラーの最大数、一括コピーを開始するファイル内の行、停止する行、バッチサイズなどのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="b51f9-125">**bcp_control** sets options, such as the maximum number of errors before termination, the row in the file on which to start the bulk copy, the row to stop on, and the batch size.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b51f9-126">参照</span><span class="sxs-lookup"><span data-stu-id="b51f9-126">See Also</span></span>  
 [<span data-ttu-id="b51f9-127">ODBC&#41;&#40;の一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="b51f9-127">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  
