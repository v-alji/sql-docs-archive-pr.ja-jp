---
title: 権限の階層 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9a04e5595e509de63b362b31b240e113e635581d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714054"
---
# <a name="permissions-hierarchy-database-engine"></a><span data-ttu-id="a3d99-102">権限の階層 (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="a3d99-102">Permissions Hierarchy (Database Engine)</span></span>
  <span data-ttu-id="a3d99-103">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] では、権限を使用してセキュリティで保護できるエンティティの階層コレクションが管理されています。</span><span class="sxs-lookup"><span data-stu-id="a3d99-103">The [!INCLUDE[ssDE](../../../includes/ssde-md.md)] manages a hierarchical collection of entities that can be secured with permissions.</span></span> <span data-ttu-id="a3d99-104">これらのエンティティを、 *セキュリティ保護可能なリソース*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a3d99-104">These entities are known as *securables*.</span></span> <span data-ttu-id="a3d99-105">最も顕著なセキュリティ保護可能なリソースはサーバーとデータベースですが、さらに細かいレベルで個別の権限を設定できます。</span><span class="sxs-lookup"><span data-stu-id="a3d99-105">The most prominent securables are servers and databases, but discrete permissions can be set at a much finer level.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a3d99-106">適切な権限が許可されていることを確認することにより、セキュリティ保護可能なリソースに対するプリンシパルによる操作を制御しています。</span><span class="sxs-lookup"><span data-stu-id="a3d99-106">regulates the actions of principals on securables by verifying that they have been granted appropriate permissions.</span></span>

 <span data-ttu-id="a3d99-107">次の図は、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の権限階層における関係を示します。</span><span class="sxs-lookup"><span data-stu-id="a3d99-107">The following illustration shows the relationships among the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] permissions hierarchies.</span></span>

 <span data-ttu-id="a3d99-108">![データベース エンジンの権限の階層の図](../../database-engine/media/wj-security-layers.gif "データベース エンジンの権限の階層の図")</span><span class="sxs-lookup"><span data-stu-id="a3d99-108">![Diagram of Database Engine permissions hierarchies](../../database-engine/media/wj-security-layers.gif "Diagram of Database Engine permissions hierarchies")</span></span>

## <a name="chart-of-sql-server-permissions"></a><span data-ttu-id="a3d99-109">SQL Server 権限の一覧表</span><span class="sxs-lookup"><span data-stu-id="a3d99-109">Chart of SQL Server Permissions</span></span>
 <span data-ttu-id="a3d99-110">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] のすべてのアクセス許可を示した pdf 形式のポスター サイズの一覧表については、[https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3d99-110">For a poster sized chart of all [!INCLUDE[ssDE](../../../includes/ssde-md.md)] permissions in pdf format, see [https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf](https://github.com/microsoft/sql-server-samples/blob/master/samples/features/security/permissions-posters/Microsoft_SQL_Server_2017_and_Azure_SQL_Database_permissions_infographic.pdf).</span></span>

## <a name="working-with-permissions"></a><span data-ttu-id="a3d99-111">権限を使用した作業</span><span class="sxs-lookup"><span data-stu-id="a3d99-111">Working with Permissions</span></span>
 <span data-ttu-id="a3d99-112">権限は、使い慣れた [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ (RANT、DENY、REVOKE) で操作できます。</span><span class="sxs-lookup"><span data-stu-id="a3d99-112">Permissions can be manipulated with the familiar [!INCLUDE[tsql](../../includes/tsql-md.md)] queries GRANT, DENY, and REVOKE.</span></span> <span data-ttu-id="a3d99-113">権限に関する情報は、 [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) カタログ ビューおよび [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) カタログ ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3d99-113">Information about permissions is visible in the [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) and [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) catalog views.</span></span> <span data-ttu-id="a3d99-114">組み込み関数を使用して権限に関する情報をクエリすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a3d99-114">There is also support for querying permissions information by using built-in functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3d99-115">参照</span><span class="sxs-lookup"><span data-stu-id="a3d99-115">See Also</span></span>
 <span data-ttu-id="a3d99-116">SQL Server の[データベースエンジン &#40;権限](permissions-database-engine.md)の[セキュリティ保護](securing-sql-server.md)&#41;[Securables](securables.md) [プリンシパル &#40;](authentication-access/principals-database-engine.md)データベースエンジン&#41;[GRANT &#40;](/sql/t-sql/statements/grant-transact-sql) transact-sql&#41;[REVOKE](/sql/t-sql/statements/revoke-transact-sql) &#40;&#41;&#40;[&#41;transact-sql HAS_PERMS_BY_NAME](/sql/t-sql/statements/deny-transact-sql) &#40;[&#41;transact-sql fn_builtin_permissions](/sql/t-sql/functions/has-perms-by-name-transact-sql) &#40;&#41;transact-sql server_permissions &#40;&#41;[transact-sql database_permissions &#40;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql)を&#41;を[sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) transact-sql を[し](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)ます。</span><span class="sxs-lookup"><span data-stu-id="a3d99-116">[Securing SQL Server](securing-sql-server.md) [Permissions &#40;Database Engine&#41;](permissions-database-engine.md) [Securables](securables.md) [Principals &#40;Database Engine&#41;](authentication-access/principals-database-engine.md) [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql) [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql) [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql) [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql) [sys.server_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) [sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)</span></span>


