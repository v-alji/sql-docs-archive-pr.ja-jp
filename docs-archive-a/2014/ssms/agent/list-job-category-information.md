---
title: ジョブ カテゴリ情報の一覧の表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 924e2b064980b2ea7068230610414262995da1a6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720810"
---
# <a name="list-job-category-information"></a><span data-ttu-id="dedf9-102">ジョブ カテゴリ情報の一覧の表示</span><span class="sxs-lookup"><span data-stu-id="dedf9-102">List Job Category Information</span></span>
  <span data-ttu-id="dedf9-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]または SQL Server 管理オブジェクトを使用して、でジョブカテゴリ情報を一覧表示する方法 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dedf9-103">How to list job category information in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)] or SQL Server Management Objects.</span></span>  

  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="dedf9-104">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="dedf9-104">Security</span></span>  
 <span data-ttu-id="dedf9-105">詳細については、「 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dedf9-105">For detailed information, see [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).</span></span>  

  
##  <a name="using-transact-sql"></a><a name="TSQL"></a> <span data-ttu-id="dedf9-106">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="dedf9-106">Using Transact-SQL</span></span>  
  
#### <a name="to-list-job-category-information"></a><span data-ttu-id="dedf9-107">ジョブ カテゴリ情報の一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="dedf9-107">To list job category information</span></span>  
  
1.  <span data-ttu-id="dedf9-108">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="dedf9-108">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="dedf9-109">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dedf9-109">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="dedf9-110">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dedf9-110">Copy and paste the following example into the query window and click **Execute**.</span></span>  
  
    ```sql
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 <span data-ttu-id="dedf9-111">詳細については、「 [sp_help_category &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dedf9-111">For more information, see [sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).</span></span>  
  
  
##  <a name="using-sql-server-management-objects"></a><a name="SMO"></a><span data-ttu-id="dedf9-112">SQL Server 管理オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="dedf9-112">Using SQL Server Management Objects</span></span>  
 <span data-ttu-id="dedf9-113">**ジョブ カテゴリ情報の一覧を表示するには**</span><span class="sxs-lookup"><span data-stu-id="dedf9-113">**To list job category information**</span></span>  
  
 <span data-ttu-id="dedf9-114">Visual Basic、Visual C#、PowerShell などのプログラミング言語で `JobCategory` クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="dedf9-114">Use the `JobCategory` class by using a programming language that you choose, such as Visual Basic, Visual C#, or PowerShell..</span></span> <span data-ttu-id="dedf9-115">詳細については、「 [SQL Server 管理オブジェクト &#40;SMO&#41; プログラミングガイド](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dedf9-115">For more information, see [SQL Server Management Objects &#40;SMO&#41; Programming Guide](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).</span></span>  
