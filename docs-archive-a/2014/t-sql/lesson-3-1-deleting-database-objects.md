---
title: データベース オブジェクトの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 6bd69935dbfac020c4c75bb391e7932009fd4197
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632255"
---
# <a name="deleting-database-objects"></a><span data-ttu-id="a7d34-102">データベース オブジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="a7d34-102">Deleting Database Objects</span></span>
  <span data-ttu-id="a7d34-103">このチュートリアルのすべてのトレースを削除するには、データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-103">To remove all traces of this tutorial, you could just delete the database.</span></span> <span data-ttu-id="a7d34-104">ただし、このトピックでは、チュートリアルを進みながら実行したすべての操作を元に戻す手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-104">However, in this topic, you will go through the steps to reverse every action you took doing the tutorial.</span></span>  
  
### <a name="removing-permissions-and-objects"></a><span data-ttu-id="a7d34-105">権限とオブジェクトの削除</span><span class="sxs-lookup"><span data-stu-id="a7d34-105">Removing permissions and objects</span></span>  
  
1.  <span data-ttu-id="a7d34-106">オブジェクトを削除する前に、適切なデータベースで作業していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-106">Before you delete objects, make sure you are in the correct database:</span></span>  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  <span data-ttu-id="a7d34-107">ストアド プロシージャに対する `REVOKE` の実行権限を削除するには、 `Mary` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-107">Use the `REVOKE` statement to remove execute permission for `Mary` on the stored procedure:</span></span>  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  <span data-ttu-id="a7d34-108">`DROP` データベースに対する `Mary` のアクセス権限を削除するには、 `TestData` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-108">Use the `DROP` statement to remove permission for `Mary` to access the `TestData` database:</span></span>  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  <span data-ttu-id="a7d34-109">`DROP` が `Mary` のこのインスタンスにアクセスする権限を削除するには、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-109">Use the `DROP` statement to remove permission for `Mary` to access this instance of [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:</span></span>  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  <span data-ttu-id="a7d34-110">ストアド プロシージャ `DROP` を削除するには、 `pr_Names`ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-110">Use the `DROP` statement to remove the store procedure `pr_Names`:</span></span>  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  <span data-ttu-id="a7d34-111">ビュー `DROP` を削除するには、 `vw_Names`ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-111">Use the `DROP` statement to remove the view `vw_Names`:</span></span>  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  <span data-ttu-id="a7d34-112">`DELETE` テーブルからすべての行を削除するには、 `Products` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-112">Use the `DELETE` statement to remove all rows from the `Products` table:</span></span>  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  <span data-ttu-id="a7d34-113">`DROP` テーブルを削除するには、 `Products` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-113">Use the `DROP` statement to remove the `Products` table:</span></span>  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. <span data-ttu-id="a7d34-114">データベースでの作業中は、 `TestData` データベースを削除できません。したがって、まずコンテキストを他のデータベースに切り替えてから、 `DROP` ステートメントを使用して `TestData` データベースを削除します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-114">You cannot remove the `TestData` database while you are in the database; therefore, first switch context to another database, and then use the `DROP` statement to remove the `TestData` database:</span></span>  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
 <span data-ttu-id="a7d34-115">これで、「 [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの記述」のチュートリアルを終了します。</span><span class="sxs-lookup"><span data-stu-id="a7d34-115">This concludes the Writing [!INCLUDE[tsql](../includes/tsql-md.md)] Statements tutorial.</span></span> <span data-ttu-id="a7d34-116">このチュートリアルは概要であり、使用できるステートメントのすべてのオプションが記載されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a7d34-116">Remember, this tutorial is a brief overview and it does not describe all the options to the statements that are used.</span></span> <span data-ttu-id="a7d34-117">効率のよいデータベース構造を設計して作成し、セキュリティ保護されたデータ アクセスを構成するには、このチュートリアルで示したデータベースよりも複雑なデータベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="a7d34-117">Designing and creating an efficient database structure and configuring secure access to the data requires a more complex database than that shown in this tutorial.</span></span>  
  
## <a name="return-to-sql-server-tools-portal"></a><span data-ttu-id="a7d34-118">SQL Server ツールのポータルに戻る</span><span class="sxs-lookup"><span data-stu-id="a7d34-118">Return to SQL Server Tools Portal</span></span>  
 [<span data-ttu-id="a7d34-119">チュートリアル:Transact-SQL ステートメントの作成</span><span class="sxs-lookup"><span data-stu-id="a7d34-119">Tutorial: Writing Transact-SQL Statements</span></span>](tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a><span data-ttu-id="a7d34-120">参照</span><span class="sxs-lookup"><span data-stu-id="a7d34-120">See Also</span></span>  
 <span data-ttu-id="a7d34-121">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7d34-121">[REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) </span></span>  
 <span data-ttu-id="a7d34-122">[DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7d34-122">[DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql) </span></span>  
 <span data-ttu-id="a7d34-123">[Transact-sql&#41;&#40;のログインを削除します。](/sql/t-sql/statements/drop-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7d34-123">[DROP LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-login-transact-sql) </span></span>  
 <span data-ttu-id="a7d34-124">[DROP PROCEDURE &#40;Transact-sql&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7d34-124">[DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql) </span></span>  
 <span data-ttu-id="a7d34-125">[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7d34-125">[DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql) </span></span>  
 <span data-ttu-id="a7d34-126">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7d34-126">[DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) </span></span>  
 <span data-ttu-id="a7d34-127">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a7d34-127">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span></span>  
 [<span data-ttu-id="a7d34-128">DROP DATABASE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a7d34-128">DROP DATABASE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)  
  
  
