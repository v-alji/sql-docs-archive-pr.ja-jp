---
title: ユーザー定義データベースの照合順序を、master および model データベースの照合順序と一致するように設定します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c686446f-dae1-4b05-a3df-837b3422988d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b48696fb56c40062d62f04845715170887f84fda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712345"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-those-of-the-master-and-model-databases"></a><span data-ttu-id="d0849-102">ユーザー定義データベースの照合順序が master データベースおよび model データベースの照合順序と一致するように設定</span><span class="sxs-lookup"><span data-stu-id="d0849-102">Set the Collation of User-defined Databases to Match Those of the master and model Databases</span></span>
  <span data-ttu-id="d0849-103">このルールでは、ユーザー定義データベースの定義に使用されたデータベース照合順序と master または model の照合順序が一致しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d0849-103">This rule checks whether user-defined databases are defined by using a database collation that is the same as the collation for master or model.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="d0849-104">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="d0849-104">Best Practices Recommendations</span></span>  
 <span data-ttu-id="d0849-105">ユーザー定義データベースの照合順序と master または model データベースの照合順序を一致させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d0849-105">We recommend that the collations of user-defined databases match the collation of master or model.</span></span> <span data-ttu-id="d0849-106">照合順序が一致していない場合、照合順序の競合が発生してコードが実行されなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d0849-106">Otherwise, collation conflicts can occur that might prevent code from executing.</span></span> <span data-ttu-id="d0849-107">たとえば、ストアド プロシージャによってあるテーブルを一時テーブルに結合すると、ユーザー定義のデータベースと model データベースの照合順序が異なる場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ではバッチが終了し、照合順序の競合エラーが返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d0849-107">For example, when a stored procedure joins one table to a temporary table, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] might end the batch and return a collation conflict error if the collations of the user-defined database and the model database are different.</span></span> <span data-ttu-id="d0849-108">この現象は、一時テーブルが tempdb に作成されることが原因で発生します。tempdb の照合順序は、model データベースの照合順序に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d0849-108">This occurs because temporary tables are created in tempdb, which bases its collation on that of model.</span></span>  
  
 <span data-ttu-id="d0849-109">照合順序の競合エラーが発生した場合は、次のいずれかの解決策を検討してください。</span><span class="sxs-lookup"><span data-stu-id="d0849-109">If you experience collation conflict errors, consider one of the following solutions:</span></span>  
  
-   <span data-ttu-id="d0849-110">データをユーザー データベースからエクスポートし、照合順序が master データベースおよび model データベースと同じ新しいテーブルにインポートします。</span><span class="sxs-lookup"><span data-stu-id="d0849-110">Export the data from the user database and import it into new tables that have the same collation as the master and model databases.</span></span>  
  
-   <span data-ttu-id="d0849-111">ユーザー データベースの照合順序と一致する照合順序を使用するようにシステム データベースを再構築します。</span><span class="sxs-lookup"><span data-stu-id="d0849-111">Rebuild the system databases to use a collation that matches the user database collation.</span></span> <span data-ttu-id="d0849-112">システムデータベースを再構築する方法の詳細については、「[システムデータベースの再構築](../relational-databases/databases/system-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0849-112">For more information about how to rebuild the system databases, see [Rebuild System Databases](../relational-databases/databases/system-databases.md).</span></span>  
  
-   <span data-ttu-id="d0849-113">ユーザー テーブルを tempdb 内のテーブルに結合するストアド プロシージャを、ユーザー データベースの照合順序を使用して tempdb にテーブルを作成するように変更します。</span><span class="sxs-lookup"><span data-stu-id="d0849-113">Modify any stored procedures that join user tables to tables in tempdb to create the tables in tempdb by using the collation of the user database.</span></span> <span data-ttu-id="d0849-114">これを行うには、次の例に示すように、一時テーブルの列定義に `COLLATE database_default` 句を追加します。</span><span class="sxs-lookup"><span data-stu-id="d0849-114">To do this, add the `COLLATE database_default` clause to the column definitions of the temporary table, as shown in the following example:</span></span>  
  
    ```  
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )  
    ```  
  
## <a name="for-more-information"></a><span data-ttu-id="d0849-115">詳細情報</span><span class="sxs-lookup"><span data-stu-id="d0849-115">For More Information</span></span>  
 [<span data-ttu-id="d0849-116">データベースの照合順序の設定または変更</span><span class="sxs-lookup"><span data-stu-id="d0849-116">Set or Change the Database Collation</span></span>](../relational-databases/collations/set-or-change-the-database-collation.md)  
  
 [<span data-ttu-id="d0849-117">列の照合順序の設定または変更</span><span class="sxs-lookup"><span data-stu-id="d0849-117">Set or Change the Column Collation</span></span>](../relational-databases/collations/set-or-change-the-column-collation.md)  
  
 [<span data-ttu-id="d0849-118">ALTER DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0849-118">ALTER DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [<span data-ttu-id="d0849-119">COLLATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0849-119">COLLATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/collations)  
  
 [<span data-ttu-id="d0849-120">sys.databases &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d0849-120">sys.databases &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [<span data-ttu-id="d0849-121">マイクロソフトサポート技術情報の記事325335</span><span class="sxs-lookup"><span data-stu-id="d0849-121">Microsoft Knowledge Base article 325335</span></span>](https://go.microsoft.com/fwlink/?linkid=117751)  
  
 [<span data-ttu-id="d0849-122">コマンド プロンプトから SQL Server 2008 をインストールする方法</span><span class="sxs-lookup"><span data-stu-id="d0849-122">How to: Install SQL Server 2008 from the Command Prompt</span></span>](https://go.microsoft.com/fwlink/?LinkId=81585)  
  
## <a name="see-also"></a><span data-ttu-id="d0849-123">参照</span><span class="sxs-lookup"><span data-stu-id="d0849-123">See Also</span></span>  
 [<span data-ttu-id="d0849-124">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="d0849-124">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
