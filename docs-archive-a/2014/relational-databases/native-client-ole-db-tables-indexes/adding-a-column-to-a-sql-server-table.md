---
title: SQL Server テーブルに列を追加する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 97aa2656ccde662a34e1dd80fd662b22f601d4ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739799"
---
# <a name="adding-a-column-to-a-sql-server-table"></a><span data-ttu-id="f2baa-102">SQL Server テーブルへの列の追加</span><span class="sxs-lookup"><span data-stu-id="f2baa-102">Adding a Column to a SQL Server Table</span></span>
  <span data-ttu-id="f2baa-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **Itabledefinition:: addcolumn**関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="f2baa-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::AddColumn** function.</span></span> <span data-ttu-id="f2baa-104">これにより、コンシューマーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに列を追加できます。</span><span class="sxs-lookup"><span data-stu-id="f2baa-104">This allows consumers to add a column to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="f2baa-105">テーブルに列を追加すると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーコンシューマーは次のように制約されます。</span><span class="sxs-lookup"><span data-stu-id="f2baa-105">When you add a column to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer is constrained as follows:</span></span>  
  
-   <span data-ttu-id="f2baa-106">DBPROP_COL_AUTOINCREMENT が VARIANT_TRUE の場合、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2baa-106">If DBPROP_COL_AUTOINCREMENT is VARIANT_TRUE, DBPROP_COL_NULLABLE must be VARIANT_FALSE.</span></span>  
  
-   <span data-ttu-id="f2baa-107"> の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** データ型を使用して列を定義している場合、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2baa-107">If the column is defined by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** data type, DBPROP_COL_NULLABLE must be VARIANT_FALSE.</span></span>  
  
-   <span data-ttu-id="f2baa-108">それ以外の列定義の場合、DBPROP_COL_NULLABLE は VARIANT_TRUE にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2baa-108">For any other column definition, DBPROP_COL_NULLABLE must be VARIANT_TRUE.</span></span>  
  
 <span data-ttu-id="f2baa-109">コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2baa-109">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="f2baa-110">*pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2baa-110">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="f2baa-111">新しい列名は、DBCOLUMNDESC パラメーター *pColumnDesc* の *dbcid* メンバー内にある、*uName* 共用体の *pwszName* メンバーに Unicode 文字列として指定されます。</span><span class="sxs-lookup"><span data-stu-id="f2baa-111">The new column name is specified as a Unicode character string in the *pwszName* member of the *uName* union in the *dbcid* member of the DBCOLUMNDESC parameter *pColumnDesc*.</span></span> <span data-ttu-id="f2baa-112">*eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2baa-112">The *eKind* member must be DBKIND_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2baa-113">参照</span><span class="sxs-lookup"><span data-stu-id="f2baa-113">See Also</span></span>  
 <span data-ttu-id="f2baa-114">[テーブルとインデックス](tables-and-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="f2baa-114">[Tables and Indexes](tables-and-indexes.md) </span></span>  
 [<span data-ttu-id="f2baa-115">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f2baa-115">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
