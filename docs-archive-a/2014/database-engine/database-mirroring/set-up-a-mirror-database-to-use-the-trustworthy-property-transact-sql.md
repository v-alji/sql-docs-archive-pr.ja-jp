---
title: TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database option
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6cd46a08037bcb6eee178a96d84bdab358e5350d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716729"
---
# <a name="set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql"></a><span data-ttu-id="26001-102">TRUSTWORTHY プロパティを使用するようにミラー データベースを設定する方法 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="26001-102">Set Up a Mirror Database to Use the Trustworthy Property (Transact-SQL)</span></span>
  <span data-ttu-id="26001-103">データベースをバックアップするときに、TRUSTWORTHY データベース プロパティは OFF に設定されます。</span><span class="sxs-lookup"><span data-stu-id="26001-103">When a database is backed up, the TRUSTWORTHY database property is set to OFF.</span></span> <span data-ttu-id="26001-104">したがって、新しいミラー データベースでは TRUSTWORTHY は常に OFF です。</span><span class="sxs-lookup"><span data-stu-id="26001-104">Therefore, on a new mirror database TRUSTWORTHY is always OFF.</span></span> <span data-ttu-id="26001-105">フェールオーバー後にデータベースを信頼可能にする必要がある場合は、ミラーリングを開始した後で追加の設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="26001-105">If the database needs to be trustworthy after a failover, extra setup steps are necessary after mirroring begins.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="26001-106">このデータベース プロパティの詳細については、「 [TRUSTWORTHY データベース プロパティ](../../relational-databases/security/trustworthy-database-property.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26001-106">For information about this database property, see [TRUSTWORTHY Database Property](../../relational-databases/security/trustworthy-database-property.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="26001-107">手順</span><span class="sxs-lookup"><span data-stu-id="26001-107">Procedure</span></span>  
  
#### <a name="to-setup-a-mirror-database-to-use-the-trustworthy-property"></a><span data-ttu-id="26001-108">TRUSTWORTHY プロパティを使用するようにミラー データベースを設定するには</span><span class="sxs-lookup"><span data-stu-id="26001-108">To setup a mirror database to use the Trustworthy Property</span></span>  
  
1.  <span data-ttu-id="26001-109">プリンシパル サーバー インスタンスで、プリンシパル データベースの TRUSTWORTHY プロパティがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="26001-109">On the principal server instance, verify that the principal database has the Trustworthy property turned on.</span></span>  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     <span data-ttu-id="26001-110">詳細については、「[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26001-110">For more information, see [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).</span></span>  
  
2.  <span data-ttu-id="26001-111">ミラーリングが開始された後、データベースが現在プリンシパル データベースであること、セッションが同期動作モードを使用していること、およびセッションが既に同期していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="26001-111">After starting mirroring, verify that the database is currently the principal database, the session is using a synchronous operating mode, and the session is already synchronized.</span></span>  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     <span data-ttu-id="26001-112">詳細については、「[sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26001-112">For more information, see [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).</span></span>  
  
3.  <span data-ttu-id="26001-113">ミラーリング セッションが同期されたら、ミラー データベースに手動でフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="26001-113">Once the mirroring session is synchronized, manually fail over to the mirror database.</span></span>  
  
     <span data-ttu-id="26001-114">この操作を行うには、SQL Server Management Studio または Transact-SQL を使用します。</span><span class="sxs-lookup"><span data-stu-id="26001-114">This can be done in either SQL Server Management Studio or using Transact-SQL:</span></span>  
  
    -   [<span data-ttu-id="26001-115">データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="26001-115">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="26001-116">データベース ミラーリング セッションを手動でフェールオーバーする方法 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26001-116">Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  <span data-ttu-id="26001-117">次の ALTER DATABASE コマンドを使用して、TRUSTWORTHY データベース プロパティをオンにします。</span><span class="sxs-lookup"><span data-stu-id="26001-117">Turn on the trustworthy database property using the following ALTER DATABASE command:</span></span>  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     <span data-ttu-id="26001-118">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26001-118">For more information, see[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
5.  <span data-ttu-id="26001-119">必要に応じて、手動で再度フェールオーバーし、元のプリンシパルに戻します。</span><span class="sxs-lookup"><span data-stu-id="26001-119">Optionally, manually failover again to return to the original principal.</span></span>  
  
6.  <span data-ttu-id="26001-120">必要に応じて、SAFETY を OFF に設定し、WITNESS も OFF に設定されていることを確認して、非同期の高パフォーマンス モードに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="26001-120">Optionally, switch to asynchronous, high-performance mode by setting SAFETY to OFF and ensuring that WITNESS is also set to OFF.</span></span>  
  
     <span data-ttu-id="26001-121">Transact-SQL での操作</span><span class="sxs-lookup"><span data-stu-id="26001-121">In Transact-SQL:</span></span>  
  
    -   [<span data-ttu-id="26001-122">データベース ミラーリング セッションでのトランザクションの安全性の変更 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26001-122">Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;</span></span>](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [<span data-ttu-id="26001-123">データベース ミラーリング セッションからのミラーリング監視サーバーの削除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="26001-123">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     <span data-ttu-id="26001-124">SQL Server Management Studio での操作</span><span class="sxs-lookup"><span data-stu-id="26001-124">In SQL Server Management Studio:</span></span>  
  
    -   [<span data-ttu-id="26001-125">Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="26001-125">Establish a Database Mirroring Session Using Windows Authentication &#40;SQL Server Management Studio&#41;</span></span>](establish-database-mirroring-session-windows-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="26001-126">参照</span><span class="sxs-lookup"><span data-stu-id="26001-126">See Also</span></span>  
 <span data-ttu-id="26001-127">[TRUSTWORTHY データベース プロパティ](../../relational-databases/security/trustworthy-database-property.md) </span><span class="sxs-lookup"><span data-stu-id="26001-127">[TRUSTWORTHY Database Property](../../relational-databases/security/trustworthy-database-property.md) </span></span>  
 [<span data-ttu-id="26001-128">暗号化されたミラー データベースの設定</span><span class="sxs-lookup"><span data-stu-id="26001-128">Set Up an Encrypted Mirror Database</span></span>](set-up-an-encrypted-mirror-database.md)  
  
  
