---
title: データベース オブジェクトへのアクセス権の付与 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- granting access to database objects
ms.assetid: a44d9bbf-f58e-4734-b7f4-eb3b492b777b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 22bd0bb1f01e59ec30f7cf1bbf128c890d3d5d64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644734"
---
# <a name="granting-access-to-a-database-object"></a><span data-ttu-id="9bfee-102">データベース オブジェクトへのアクセス権の付与</span><span class="sxs-lookup"><span data-stu-id="9bfee-102">Granting Access to a Database Object</span></span>
  <span data-ttu-id="9bfee-103">管理者は **Products** テーブルおよび **vw_Names** ビューから SELECT を実行し、 **pr_Names** プロシージャを実行できますが、ユーザー Mary は実行できません。</span><span class="sxs-lookup"><span data-stu-id="9bfee-103">As an administrator, you can execute the SELECT from the **Products** table and the **vw_Names** view, and execute the **pr_Names** procedure; however, Mary cannot.</span></span> <span data-ttu-id="9bfee-104">Mary に必要な権限を付与するには、GRANT ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="9bfee-104">To grant Mary the necessary permissions, use the GRANT statement.</span></span>  
  
### <a name="procedure-title"></a><span data-ttu-id="9bfee-105">手順のタイトル</span><span class="sxs-lookup"><span data-stu-id="9bfee-105">Procedure Title</span></span>  
  
1.  <span data-ttu-id="9bfee-106">次のステートメントを実行して、 `Mary` ストアド プロシージャの `EXECUTE` 権限を `pr_Names` に与えます。</span><span class="sxs-lookup"><span data-stu-id="9bfee-106">Execute the following statement to give `Mary` the `EXECUTE` permission for the `pr_Names` stored procedure.</span></span>  
  
    ```  
    GRANT EXECUTE ON pr_Names TO Mary;  
    GO  
    ```  
  
 <span data-ttu-id="9bfee-107">このシナリオでは、Mary はストアド プロシージャを使用して **Products** テーブルにのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9bfee-107">In this scenario, Mary can only access the **Products** table by using the stored procedure.</span></span> <span data-ttu-id="9bfee-108">Mary がビューに対して SELECT ステートメントを実行できるようにする場合は、 `GRANT SELECT ON vw_Names TO Mary`も実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bfee-108">If you want Mary to be able to execute a SELECT statement against the view, then you must also execute `GRANT SELECT ON vw_Names TO Mary`.</span></span> <span data-ttu-id="9bfee-109">データベース オブジェクトへのアクセス権を削除するには、REVOKE ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="9bfee-109">To remove access to database objects, use the REVOKE statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9bfee-110">テーブル、ビュー、およびストアド プロシージャが同じスキーマに所有されていない場合は、権限を付与すると、複雑になります。</span><span class="sxs-lookup"><span data-stu-id="9bfee-110">If the table, the view, and the stored procedure are not owned by the same schema, granting permissions becomes more complex.</span></span>  
  
## <a name="about-grant"></a><span data-ttu-id="9bfee-111">GRANT について</span><span class="sxs-lookup"><span data-stu-id="9bfee-111">About GRANT</span></span>  
 <span data-ttu-id="9bfee-112">ストアド プロシージャを実行するには、EXECUTE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9bfee-112">You must have EXECUTE permission to execute a stored procedure.</span></span> <span data-ttu-id="9bfee-113">データにアクセスしたり、データを変更するには、SELECT、INSERT、UPDATE、および DELETE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="9bfee-113">You must have SELECT, INSERT, UPDATE, and DELETE permissions to access and change data.</span></span> <span data-ttu-id="9bfee-114">GRANT ステートメントは、テーブルを作成する権限など、他の権限にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="9bfee-114">The GRANT statement is also used for other permissions, such as permission to create tables.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9bfee-115">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="9bfee-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9bfee-116">概要 : データベース オブジェクトに対する権限の構成</span><span class="sxs-lookup"><span data-stu-id="9bfee-116">Summary: Configuring Permissions on Database Objects</span></span>](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="9bfee-117">参照</span><span class="sxs-lookup"><span data-stu-id="9bfee-117">See Also</span></span>  
 <span data-ttu-id="9bfee-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="9bfee-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 [<span data-ttu-id="9bfee-119">REVOKE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9bfee-119">REVOKE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/revoke-transact-sql)  
  
  
