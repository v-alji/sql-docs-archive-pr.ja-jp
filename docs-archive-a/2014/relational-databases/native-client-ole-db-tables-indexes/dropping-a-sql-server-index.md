---
title: SQL Server インデックスの削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: rothja
ms.author: jroth
ms.openlocfilehash: 1267cc92645ff8b28757ad2d266e58917fcb4b28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642047"
---
# <a name="dropping-a-sql-server-index"></a><span data-ttu-id="d1c54-102">SQL Server インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="d1c54-102">Dropping a SQL Server Index</span></span>
  <span data-ttu-id="d1c54-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **Iindexdefinition::D ropindex**関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="d1c54-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition::DropIndex** function.</span></span> <span data-ttu-id="d1c54-104">コンシューマーはこの関数を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルからインデックスを削除できます。</span><span class="sxs-lookup"><span data-stu-id="d1c54-104">This allows consumers to remove an index from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="d1c54-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主キーと一意の制約をインデックスとして公開します。</span><span class="sxs-lookup"><span data-stu-id="d1c54-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes some [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PRIMARY KEY and UNIQUE constraints as indexes.</span></span> <span data-ttu-id="d1c54-106">テーブル所有者、データベース所有者、一部の管理ロールのメンバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルを変更して、制約を削除できます。</span><span class="sxs-lookup"><span data-stu-id="d1c54-106">The table owner, database owner, and some administrative role members can modify a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, dropping a constraint.</span></span> <span data-ttu-id="d1c54-107">既定では、テーブル所有者だけが既存のインデックスを削除できます。</span><span class="sxs-lookup"><span data-stu-id="d1c54-107">By default, only the table owner can drop an existing index.</span></span> <span data-ttu-id="d1c54-108">したがって、**DropIndex** が成功するか失敗するかは、アプリケーション ユーザーのアクセス権だけでなく、指定されたインデックスの種類によっても異なります。</span><span class="sxs-lookup"><span data-stu-id="d1c54-108">Therefore, **DropIndex** success or failure depends not only on the application user's access rights but also on the type of index indicated.</span></span>  
  
 <span data-ttu-id="d1c54-109">コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1c54-109">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="d1c54-110">*pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1c54-110">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="d1c54-111">インデックス名は、*pIndexID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定します。</span><span class="sxs-lookup"><span data-stu-id="d1c54-111">Consumers specify the index name as a Unicode character string in the *pwszName* member of the *uName* union in the *pIndexID* parameter.</span></span> <span data-ttu-id="d1c54-112">*pIndexID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1c54-112">The *eKind* member of *pIndexID* must be DBKIND_NAME.</span></span> <span data-ttu-id="d1c54-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、 *pIndexID*が null の場合にテーブルのすべてのインデックスを削除する OLE DB 機能はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1c54-113">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support the OLE DB feature of dropping all indexes on a table when *pIndexID* is null.</span></span> <span data-ttu-id="d1c54-114">*pIndexID* が NULL の場合、E_INVALIDARG を返します。</span><span class="sxs-lookup"><span data-stu-id="d1c54-114">If *pIndexID* is null, E_INVALIDARG is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c54-115">参照</span><span class="sxs-lookup"><span data-stu-id="d1c54-115">See Also</span></span>  
 <span data-ttu-id="d1c54-116">[テーブルとインデックス](tables-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="d1c54-116">[Tables and Indexes](tables-and-indexes.md) </span></span>  
 <span data-ttu-id="d1c54-117">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d1c54-117">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="d1c54-118">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d1c54-118">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
