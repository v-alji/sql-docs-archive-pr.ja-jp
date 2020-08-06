---
title: ネイティブ コンパイル アドバイザー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.nativecompilationwizard.f1
- swb.nativecompilationwizard.f1
ms.assetid: d3898a47-2985-4a08-bc70-fd8331a01b7b
author: rothja
ms.author: jroth
ms.openlocfilehash: b2182d89489af5da8bc3b85b89484fbbf72e4dfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742065"
---
# <a name="native-compilation-advisor"></a><span data-ttu-id="95f2b-102">ネイティブ コンパイル アドバイザー</span><span class="sxs-lookup"><span data-stu-id="95f2b-102">Native Compilation Advisor</span></span>
  <span data-ttu-id="95f2b-103">トランザクションパフォーマンスレポートツール (「[テーブルまたはストアドプロシージャをインメモリ OLTP に移植する必要](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)があるかどうかを判断する」を参照) は、ネイティブコンパイルを使用するように移植した場合にメリットが得られる、データベース内の解釈されたストアドプロシージャについて通知します。</span><span class="sxs-lookup"><span data-stu-id="95f2b-103">Transaction performance reports tool (see [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) informs you about which interpreted stored procedures in your database will benefit if ported to use native compilation.</span></span> <span data-ttu-id="95f2b-104">ネイティブ コンパイルを使用するように移植するストアド プロシージャを特定した後に、ネイティブ コンパイル アドバイザーを使用すると、解釈されたストアド プロシージャをネイティブ コンパイルに移行する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-104">After you identify a stored procedure that you would like to port to use native compilation, you can use the native compilation advisor to help you migrate the interpreted stored procedure to native compilation.</span></span> <span data-ttu-id="95f2b-105">ネイティブ コンパイル ストアド プロシージャの詳細については、「 [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="95f2b-105">For more information about natively compiled stored procedures, see [Natively Compiled Stored Procedures](natively-compiled-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="95f2b-106">まず、解釈されたストアド プロシージャが格納されているインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="95f2b-106">To begin, connect to the instance that contains the interpreted stored procedure.</span></span> <span data-ttu-id="95f2b-107">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] のインスタンスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-107">You can connect to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], or [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance.</span></span> <span data-ttu-id="95f2b-108">ただし、アドバイザーを使用して移行操作を実行する場合は、インメモリ OLTP 機能が有効になっている [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] インスタンスに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95f2b-108">However, if you wish to perform a migration operation with the advisor, you must connect to a [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] instance on which In-Memory OLTP functionality is enabled.</span></span> <span data-ttu-id="95f2b-109">インメモリ OLTP の要件の詳細については、「 [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95f2b-109">For more information about In-Memory OLTP requirements, see [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="95f2b-110">移行方法については、「[In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx)」(インメモリ OLTP - 一般的なワークロード パターンと移行に関する考慮事項) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95f2b-110">For information about migration methodologies, see [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx).</span></span>  
  
## <a name="walkthrough-using-the-native-compilation-advisor"></a><span data-ttu-id="95f2b-111">ネイティブ コンパイル アドバイザーの使用に関するチュートリアル</span><span class="sxs-lookup"><span data-stu-id="95f2b-111">Walkthrough Using the Native Compilation Advisor</span></span>  
 <span data-ttu-id="95f2b-112">**オブジェクト エクスプローラー**で、変換するストアド プロシージャを右クリックし、 **[ネイティブ コンパイル アドバイザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="95f2b-112">In **Object Explorer**, right click the stored procedure you want to convert, and select **Native Compilation Advisor**.</span></span> <span data-ttu-id="95f2b-113">これにより、 **[ストアド プロシージャのネイティブ コンパイル アドバイザー]** のようこそページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-113">This will display the welcome page for the **Stored Procedure Native Compilation Advisor**.</span></span> <span data-ttu-id="95f2b-114">**[次へ]** をクリックして次に進みます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-114">Click **Next** to continue.</span></span>  
  
### <a name="stored-procedure-validation"></a><span data-ttu-id="95f2b-115">[ストアド プロシージャの検証]</span><span class="sxs-lookup"><span data-stu-id="95f2b-115">Stored Procedure Validation</span></span>  
 <span data-ttu-id="95f2b-116">このページでは、ストアド プロシージャでネイティブ コンパイルと互換性のない構造が使用されているかどうかがレポートされます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-116">This page will report if the stored procedure uses any constructs that are not compatible with native compilation.</span></span> <span data-ttu-id="95f2b-117">**[次へ]** をクリックすると、詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-117">You can click **Next** to see details.</span></span> <span data-ttu-id="95f2b-118">ネイティブ コンパイルと互換性のない構造がある場合は、 **[次へ]** をクリックすると、詳細を表示できます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-118">If there are constructs that are not compatible with native compilation, you can click **Next** to see details.</span></span>  
  
### <a name="stored-procedure-validation-result"></a><span data-ttu-id="95f2b-119">[ストアド プロシージャの検証結果]</span><span class="sxs-lookup"><span data-stu-id="95f2b-119">Stored Procedure Validation Result</span></span>  
 <span data-ttu-id="95f2b-120">ネイティブ コンパイルと互換性のない構造がある場合は、 **[ストアド プロシージャの検証結果]** ページに詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-120">If there are constructs that are not compatible with native compilation, the **Stored Procedure Validation Result** page will display details.</span></span> <span data-ttu-id="95f2b-121">レポートを生成 ( **[レポートの生成]** をクリック) し、 **ネイティブ コンパイル アドバイザー**を終了して、ネイティブ コンパイルと互換性があるようにコードを更新できます。</span><span class="sxs-lookup"><span data-stu-id="95f2b-121">You can generate a report (click **Generate Report**), exit the **Native Compilation Advisor**, and update your code so that it is compatible with native compilation.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="95f2b-122">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="95f2b-122">Code Sample</span></span>  
 <span data-ttu-id="95f2b-123">次のサンプルは、解釈されたストアド プロシージャと、ネイティブ コンパイルに対する同等のストアド プロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="95f2b-123">The following sample shows an interpreted stored procedure and the equivalent stored procedure for native compilation.</span></span> <span data-ttu-id="95f2b-124">次のサンプルでは、c:\data というディレクトリがあることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="95f2b-124">The sample assumes a directory called c:\data.</span></span>  
  
```sql  
CREATE DATABASE Demo  
ON  
PRIMARY(NAME = [Demo_data],  
FILENAME = 'C:\DATA\Demo_data.mdf', size=500MB)  
, FILEGROUP [Demo_fg] CONTAINS MEMORY_OPTIMIZED_DATA(  
NAME = [Demo_dir],  
FILENAME = 'C:\DATA\Demo_dir')  
LOG ON (name = [Demo_log], Filename='C:\DATA\Demo_log.ldf', size=500MB)  
COLLATE Latin1_General_100_BIN2;  
GO  
USE Demo;  
GO  
  
CREATE TABLE [dbo].[SalesOrders]  
(  
     [order_id] [int] NOT NULL,  
     [order_date] [datetime] NOT NULL,  
     [order_status] [tinyint] NOT NULL  
  
CONSTRAINT [PK_SalesOrders] PRIMARY KEY NONCLUSTERED HASH   
(  
     [order_id]  
)WITH ( BUCKET_COUNT = 2097152)  
)WITH ( MEMORY_OPTIMIZED = ON )  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrder] @id INT, @date DATETIME2, @status TINYINT  
AS   
BEGIN   
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
  
go  
  
CREATE PROCEDURE [dbo].[InsertOrderXTP] @id INT, @date DATETIME2, @status TINYINT  
  WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS   
BEGIN ATOMIC WITH   
(    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
     LANGUAGE = N'us_english')  
  
  INSERT dbo.SalesOrders VALUES (@id, @date, @status)  
  
END  
go  
  
select * from SalesOrders  
go  
exec dbo.InsertOrder @id= 10, @date = '1956-01-01 12:00:00', @status = 1 ;  
exec dbo.InsertOrderXTP @id= 11, @date = '1956-01-01 12:01:00', @status = 2 ;  
select * from SalesOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="95f2b-125">参照</span><span class="sxs-lookup"><span data-stu-id="95f2b-125">See Also</span></span>  
 [<span data-ttu-id="95f2b-126">インメモリ OLTP への移行</span><span class="sxs-lookup"><span data-stu-id="95f2b-126">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
