---
title: SQL ステートメントの構築 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
ms.assetid: 0acc71e2-8004-4dd8-8592-05c022bdd692
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c454f936c49335555ca09b190e4d604c9fbad64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631876"
---
# <a name="constructing-an-sql-statement-odbc"></a><span data-ttu-id="51f8d-102">SQL ステートメントの構築 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="51f8d-102">Constructing an SQL Statement (ODBC)</span></span>
  <span data-ttu-id="51f8d-103">ODBC アプリケーションでは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行することで、ほぼすべてのデータベース アクセスを行います。</span><span class="sxs-lookup"><span data-stu-id="51f8d-103">ODBC applications perform almost all of their database access by executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="51f8d-104">これらのステートメントの形式は、アプリケーションの要件によって異なります。</span><span class="sxs-lookup"><span data-stu-id="51f8d-104">The form of these statements depends on the application requirements.</span></span> <span data-ttu-id="51f8d-105">SQL ステートメントは、次の方法で構築できます。</span><span class="sxs-lookup"><span data-stu-id="51f8d-105">SQL statements can be constructed in the following ways:</span></span>  
  
-   <span data-ttu-id="51f8d-106">ハードコーディング</span><span class="sxs-lookup"><span data-stu-id="51f8d-106">Hard-coded</span></span>  
  
     <span data-ttu-id="51f8d-107">アプリケーションで固定タスクとして実行される静的ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="51f8d-107">Static statements performed by an application as a fixed task.</span></span>  
  
-   <span data-ttu-id="51f8d-108">実行時に構築</span><span class="sxs-lookup"><span data-stu-id="51f8d-108">Constructed at run time</span></span>  
  
     <span data-ttu-id="51f8d-109">実行時に構築される SQL ステートメントで、これによりユーザーは SELECT、WHERE、ORDER BY などの一般的な句を使用してステートメントを調整できます。</span><span class="sxs-lookup"><span data-stu-id="51f8d-109">SQL statements constructed at run time that enable the user to tailor the statement by using common clauses, such as SELECT, WHERE, and ORDER BY.</span></span> <span data-ttu-id="51f8d-110">これには、ユーザーが入力したアドホック クエリも含まれます。</span><span class="sxs-lookup"><span data-stu-id="51f8d-110">This includes ad hoc queries entered by users.</span></span>  
  
 <span data-ttu-id="51f8d-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント odbc ドライバーは、によって直接サポートされていない odbc および ISO 構文に対してのみ SQL ステートメントを解析します。この構文は、ドライバーによって [!INCLUDE[ssDE](../../includes/ssde-md.md)] に変換され [!INCLUDE[tsql](../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="51f8d-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client ODBC driver parses SQL statements only for ODBC and ISO syntax not directly supported by the [!INCLUDE[ssDE](../../includes/ssde-md.md)], which the driver transforms into [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="51f8d-112">その他すべての SQL 構文は、変更されずに[!INCLUDE[ssDE](../../includes/ssde-md.md)]に渡されます。ここでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] かどうかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="51f8d-112">All other SQL syntax is passed to the [!INCLUDE[ssDE](../../includes/ssde-md.md)] unchanged, where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will determine if it is valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="51f8d-113">この方法には、次の 2 つの利点があります。</span><span class="sxs-lookup"><span data-stu-id="51f8d-113">This approach yields two benefits:</span></span>  
  
-   <span data-ttu-id="51f8d-114">オーバーヘッドの削減</span><span class="sxs-lookup"><span data-stu-id="51f8d-114">Reduced overhead</span></span>  
  
     <span data-ttu-id="51f8d-115">ドライバーの処理オーバーヘッドが最小限に抑えられます。これは、スキャンする必要のある ODBC 句および ISO 句の数が少ないためです。</span><span class="sxs-lookup"><span data-stu-id="51f8d-115">Processing overhead for the driver is minimized because it only has to scan for a small set of ODBC and ISO clauses.</span></span>  
  
-   <span data-ttu-id="51f8d-116">柔軟性</span><span class="sxs-lookup"><span data-stu-id="51f8d-116">Flexibility</span></span>  
  
     <span data-ttu-id="51f8d-117">プログラマは、アプリケーションの移植性を調整できます。</span><span class="sxs-lookup"><span data-stu-id="51f8d-117">Programmers can tailor the portability of their applications.</span></span> <span data-ttu-id="51f8d-118">複数のデータベースに対する移植性を強化するには、主に ODBC 構文および ISO 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="51f8d-118">To enhance portability against multiple databases, use primarily ODBC and ISO syntax.</span></span> <span data-ttu-id="51f8d-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の強力な機能を使用するには、対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="51f8d-119">To use enhancements specific to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], use the appropriate [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax.</span></span> <span data-ttu-id="51f8d-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT odbc ドライバーは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] odbc ベースのアプリケーションがのすべての機能を利用できるように、完全な構文をサポートしてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="51f8d-120">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver supports the complete [!INCLUDE[tsql](../../includes/tsql-md.md)] syntax so ODBC-based applications can take advantage of all the features in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="51f8d-121">SELECT ステートメント内の列リストには、現在のタスクを実行するのに必要な列だけを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="51f8d-121">The column list in a SELECT statement should contain only the columns required to perform the current task.</span></span> <span data-ttu-id="51f8d-122">これにより、ネットワーク経由で送信されるデータ量が少なくなるだけでなく、アプリケーションに対するデータベース変更の影響も少なくなります。</span><span class="sxs-lookup"><span data-stu-id="51f8d-122">Not only does this reduce the amount of data sent across the network, but also it reduces the effect of database changes on the application.</span></span> <span data-ttu-id="51f8d-123">アプリケーションでテーブルの列を参照していなければ、アプリケーションは、その列に行われる変更の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="51f8d-123">If an application does not reference a column from a table, then the application is not affected by any changes made to that column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f8d-124">参照</span><span class="sxs-lookup"><span data-stu-id="51f8d-124">See Also</span></span>  
 [<span data-ttu-id="51f8d-125">ODBC&#41;&#40;クエリの実行</span><span class="sxs-lookup"><span data-stu-id="51f8d-125">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
