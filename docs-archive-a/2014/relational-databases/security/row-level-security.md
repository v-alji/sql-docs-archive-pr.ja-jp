---
title: 行レベルのセキュリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- row level security described
- row level security
- access control predicates
- security [SQL Server], predicate based access control
- predicate based security
ms.assetid: 7221fa4e-ca4a-4d5c-9f93-1b8a4af7b9e8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c67f84723e79b66d0454fb509f2fa9ced03dac7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714025"
---
# <a name="row-level-security"></a><span data-ttu-id="ffcfb-102">行レベルのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="ffcfb-102">Row-Level Security</span></span>
  <span data-ttu-id="ffcfb-103">行レベルのセキュリティを使用すると、クエリを実行しているユーザーの特性 (たとえば、グループ メンバーシップや実行コンテキストなど) に基づいて、データベース テーブル内の行へのアクセスを制御できます。</span><span class="sxs-lookup"><span data-stu-id="ffcfb-103">Row-Level Security enables customers to control access to rows in a database table based on the characteristics of the user executing a query (e.g., group membership or execution context).</span></span> <span data-ttu-id="ffcfb-104">行レベルのセキュリティが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 で使用可能になりました。</span><span class="sxs-lookup"><span data-stu-id="ffcfb-104">Row-Level Security is now available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016.</span></span> <span data-ttu-id="ffcfb-105">この機能の現在の説明については、現在のドキュメントの「 [行レベルのセキュリティ](https://msdn.microsoft.com/library/dn765131.aspx) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffcfb-105">See [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) in the current documentation for the current description of this feature.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffcfb-106">参照</span><span class="sxs-lookup"><span data-stu-id="ffcfb-106">See Also</span></span>  
 <span data-ttu-id="ffcfb-107">[セキュリティポリシー &#40;Azure SQL Database の作成&#41;](/sql/t-sql/statements/create-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffcfb-107">[CREATE SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/create-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="ffcfb-108">[セキュリティポリシーの変更 &#40;Azure SQL Database&#41;](/sql/t-sql/statements/alter-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffcfb-108">[ALTER SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/alter-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="ffcfb-109">[セキュリティポリシー &#40;Azure SQL Database&#41;を削除します](/sql/t-sql/statements/drop-security-policy-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffcfb-109">[DROP SECURITY POLICY &#40;Azure SQL Database&#41;](/sql/t-sql/statements/drop-security-policy-transact-sql) </span></span>  
 <span data-ttu-id="ffcfb-110">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffcfb-110">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 <span data-ttu-id="ffcfb-111">[security_policies &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffcfb-111">[sys.security_policies &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-policies-transact-sql) </span></span>  
 <span data-ttu-id="ffcfb-112">[security_predicates &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ffcfb-112">[sys.security_predicates &#40;Azure SQL Database&#41;](/sql/relational-databases/system-catalog-views/sys-security-predicates-transact-sql) </span></span>  
 [<span data-ttu-id="ffcfb-113">ユーザー定義関数の作成 &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="ffcfb-113">Create User-defined Functions &#40;Database Engine&#41;</span></span>](../user-defined-functions/create-user-defined-functions-database-engine.md)  
  
  
