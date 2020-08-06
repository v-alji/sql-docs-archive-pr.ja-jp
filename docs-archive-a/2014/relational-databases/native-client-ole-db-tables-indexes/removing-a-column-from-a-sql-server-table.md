---
title: SQL Server テーブルからの列の削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- SQL Server Native Client OLE DB provider, columns
ms.assetid: 210811b7-cbd6-421e-bc6e-df9482236768
author: rothja
ms.author: jroth
ms.openlocfilehash: 8f40c466910aae7e0d349cd4a65ab265282bc8eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642045"
---
# <a name="removing-a-column-from-a-sql-server-table"></a><span data-ttu-id="53ddc-102">SQL Server テーブルからの列の削除</span><span class="sxs-lookup"><span data-stu-id="53ddc-102">Removing a Column from a SQL Server Table</span></span>
  <span data-ttu-id="53ddc-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **Itabledefinition::D ropcolumn**関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="53ddc-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **ITableDefinition::DropColumn** function.</span></span> <span data-ttu-id="53ddc-104">コンシューマーはこの関数を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルから列を削除できます。</span><span class="sxs-lookup"><span data-stu-id="53ddc-104">This allows consumers to remove a column from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="53ddc-105">コンシューマーはテーブル名は、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定します。</span><span class="sxs-lookup"><span data-stu-id="53ddc-105">Consumers specify the table name as a Unicode character string in the *pwszName*member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="53ddc-106">*pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="53ddc-106">The *eKind*member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="53ddc-107">列名は *pColumnID* パラメーターの *uName* 共用体の *pwszName* メンバーに指定します。</span><span class="sxs-lookup"><span data-stu-id="53ddc-107">The consumer indicates a column name in the *pwszName*member of the *uName* union in the *pColumnID* parameter.</span></span> <span data-ttu-id="53ddc-108">列名は Unicode 文字列で指定します。</span><span class="sxs-lookup"><span data-stu-id="53ddc-108">The column name is a Unicode character string.</span></span> <span data-ttu-id="53ddc-109">*pColumnID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="53ddc-109">The *eKind* member of *pColumnID* must be DBKIND_NAME.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53ddc-110">例</span><span class="sxs-lookup"><span data-stu-id="53ddc-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="53ddc-111">コード</span><span class="sxs-lookup"><span data-stu-id="53ddc-111">Code</span></span>  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a><span data-ttu-id="53ddc-112">参照</span><span class="sxs-lookup"><span data-stu-id="53ddc-112">See Also</span></span>  
 [<span data-ttu-id="53ddc-113">テーブルとインデックス</span><span class="sxs-lookup"><span data-stu-id="53ddc-113">Tables and Indexes</span></span>](tables-and-indexes.md)  
  
  
