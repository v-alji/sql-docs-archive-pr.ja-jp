---
title: 基になるクエリの指定 (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.providesourcequery.f1
ms.assetid: c8cbd07e-b9c3-422f-94b8-d6fc8cf31cf5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b21100f51c279e9ba764c8f82565af9d6e391ef3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642887"
---
# <a name="provide-a-source-query-sql-server-import-and-export-wizard"></a><span data-ttu-id="58f60-102">[基になるクエリの指定]\(SQL Server インポートおよびエクスポート ウィザード)</span><span class="sxs-lookup"><span data-stu-id="58f60-102">Provide a Source Query (SQL Server Import and Export Wizard)</span></span>
  <span data-ttu-id="58f60-103">[基になる**クエリの指定**] ページを使用すると、データソースからコピー先にコピーするデータを生成する SQL ステートメントを入力できます。</span><span class="sxs-lookup"><span data-stu-id="58f60-103">Use the **Provide a Source Query** page to type the SQL statement that will generate the data to copy from the data source to the destination.</span></span>  
  
 <span data-ttu-id="58f60-104">このウィザードの詳細については、「 [SQL Server インポートおよびエクスポートウィザード](import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58f60-104">To learn more about this wizard, see [SQL Server Import and Export Wizard](import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span> <span data-ttu-id="58f60-105">ウィザードを起動するためのオプション、およびウィザードを正常に実行するために必要な権限の詳細については、「 [run the SQL Server Import And Export wizard](start-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58f60-105">To learn about the options for starting the wizard, as well as the permissions required to run the wizard successfully, see [Run the SQL Server Import and Export Wizard](start-the-sql-server-import-and-export-wizard.md).</span></span>  
  
 <span data-ttu-id="58f60-106">SQL Server インポートおよびエクスポート ウィザードの目的は、変換元から変換先にデータをコピーすることです。</span><span class="sxs-lookup"><span data-stu-id="58f60-106">The purpose of the SQL Server Import and Export Wizard is to copy data from a source to a destination.</span></span> <span data-ttu-id="58f60-107">また、このウィザードでは、変換先データベースと変換先テーブルも作成できます。</span><span class="sxs-lookup"><span data-stu-id="58f60-107">The wizard can also create a destination database and destination tables for you.</span></span> <span data-ttu-id="58f60-108">ただし、複数のデータベースやテーブルまたは他の種類のデータベース オブジェクトをコピーする必要がある場合は、データベース コピー ウィザードを使用してください。</span><span class="sxs-lookup"><span data-stu-id="58f60-108">However, if you have to copy multiple databases or tables, or other kinds of database objects, you should use the Copy Database Wizard instead.</span></span> <span data-ttu-id="58f60-109">詳細については、「 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58f60-109">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="58f60-110">Options</span><span class="sxs-lookup"><span data-stu-id="58f60-110">Options</span></span>  
 <span data-ttu-id="58f60-111">**SQL ステートメント**</span><span class="sxs-lookup"><span data-stu-id="58f60-111">**SQL statement**</span></span>  
 <span data-ttu-id="58f60-112">SQL ステートメントを入力して、ソース データベースから選択したデータ行を取得します。</span><span class="sxs-lookup"><span data-stu-id="58f60-112">Type a query statement to retrieve selected rows of data from the source database.</span></span> <span data-ttu-id="58f60-113">たとえば、次のクエリステートメントは、 **SalesPersonID**、 **salesquota**、および**salesquota**を、歩合の割合が1.5% を超える販売員の AdventureWorks データベースから取得します。</span><span class="sxs-lookup"><span data-stu-id="58f60-113">For example, the following query statement retrieves the **SalesPersonID**, **SalesQuota**, and **SalesYTD** from the AdventureWorks database for sales persons whose commission percentage is more than 1.5 percent.</span></span>  
  
```  
SELECT SalesPersonID, SalesQuota, SalesYTD  
FROM Sales.SalesPerson  
WHERE CommissionPct > 0.015  
```  
  
 <span data-ttu-id="58f60-114">**Parse**</span><span class="sxs-lookup"><span data-stu-id="58f60-114">**Parse**</span></span>  
 <span data-ttu-id="58f60-115">**[SQL ステートメント]** テキスト ボックスで、SQL ステートメントの構文をチェックします。</span><span class="sxs-lookup"><span data-stu-id="58f60-115">Checks the syntax of the SQL statement in the **SQL statement** text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58f60-116">ステートメントの構文をチェックするのに必要な時間がタイムアウト値の 30 秒を超えると、解析は停止し、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="58f60-116">If the time that is required to check the syntax of the statement exceeds the time-out value of 30 seconds, parsing stops and generates an error.</span></span> <span data-ttu-id="58f60-117">解析が成功するまでは、ウィザードのこのページ以降に進めません。</span><span class="sxs-lookup"><span data-stu-id="58f60-117">You will not be able to move past this page of the wizard until parsing succeeds.</span></span> <span data-ttu-id="58f60-118">1 つの解決策として、クエリに基づくデータベース ビューを作成し、クエリ テキストを直接入力するのではなく、ウィザードからビューに対してクエリを実行する方法があります。</span><span class="sxs-lookup"><span data-stu-id="58f60-118">One solution is to create a database view based on the query, and to query the view from the wizard, instead of entering the query text directly.</span></span>  
  
 <span data-ttu-id="58f60-119">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="58f60-119">**Browse**</span></span>  
 <span data-ttu-id="58f60-120">[**開く**] ダイアログボックスを使用して、SQL ステートメントを含むファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="58f60-120">Select a file containing a SQL statement by using the **Open** dialog box.</span></span> <span data-ttu-id="58f60-121">ファイルを選択すると、ファイルから [**クエリステートメント**] テキストボックスにテキストがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="58f60-121">Selecting a file copies the text from the file into the **Query statement** text box.</span></span>  
  
  
