---
title: テーブルとインデックス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: rothja
ms.author: jroth
ms.openlocfilehash: abc7c314e433eb9f107bd191738d951706f1b50d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642043"
---
# <a name="tables-and-indexes"></a><span data-ttu-id="d8f3c-102">テーブルとインデックス</span><span class="sxs-lookup"><span data-stu-id="d8f3c-102">Tables and Indexes</span></span>
  <span data-ttu-id="d8f3c-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **iindexdefinition**インターフェイスと**itabledefinition**インターフェイスを公開します。これにより、コンシューマーはテーブルとインデックスを作成、変更、および削除でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition** and **ITableDefinition** interfaces, allowing consumers to create, alter, and drop [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables and indexes.</span></span> <span data-ttu-id="d8f3c-104">有効なテーブルやインデックスの定義は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-104">Valid table and index definitions depend on the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d8f3c-105">テーブルやインデックスを作成または削除できるかどうかは、コンシューマー アプリケーション ユーザーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アクセス権によって決まります。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-105">The ability to create or drop tables and indexes depends on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] access rights of the consumer-application user.</span></span> <span data-ttu-id="d8f3c-106">テーブルの削除は、宣言参照整合性制約やその他の要因の指定によってさらに制約できます。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-106">Dropping a table can be further constrained by the presence of declarative referential integrity constraints or other factors.</span></span>  
  
 <span data-ttu-id="d8f3c-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を対象とするほとんどのアプリケーションは、これらの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーインターフェイスではなく、sql-dmo を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-107">Most applications targeting [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use SQL-DMO instead of these [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider interfaces.</span></span> <span data-ttu-id="d8f3c-108">SQL-DMO は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべての管理機能をサポートする OLE オートメーション オブジェクトの集まりです。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-108">SQL-DMO is a collection of OLE Automation objects that support all the administrative functions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d8f3c-109">複数の OLE DB プロバイダーを対象とするアプリケーションでは、さまざまな OLE DB プロバイダーでサポートされる、これらの汎用 OLE DB インターフェイスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-109">Applications targeting multiple OLE DB providers use these generic OLE DB interfaces that are supported by the various OLE DB providers.</span></span>  
  
 <span data-ttu-id="d8f3c-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、プロバイダー固有の DBPROPSET_SQLSERVERCOLUMN プロパティ セットで、次のプロパティを定義しています。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-110">In the provider-specific property set DBPROPSET_SQLSERVERCOLUMN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] defines the following property.</span></span>  
  
|<span data-ttu-id="d8f3c-111">プロパティ ID</span><span class="sxs-lookup"><span data-stu-id="d8f3c-111">Property ID</span></span>|<span data-ttu-id="d8f3c-112">説明</span><span class="sxs-lookup"><span data-stu-id="d8f3c-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d8f3c-113">SSPROP_COL_COLLATIONNAME</span><span class="sxs-lookup"><span data-stu-id="d8f3c-113">SSPROP_COL_COLLATIONNAME</span></span>|<span data-ttu-id="d8f3c-114">型: VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="d8f3c-114">Type: VT_BSTR</span></span><br /><br /> <span data-ttu-id="d8f3c-115">R/W: 書き込み</span><span class="sxs-lookup"><span data-stu-id="d8f3c-115">R/W: Write</span></span><br /><br /> <span data-ttu-id="d8f3c-116">既定値 : NULL</span><span class="sxs-lookup"><span data-stu-id="d8f3c-116">Default: Null</span></span><br /><br /> <span data-ttu-id="d8f3c-117">説明 : このプロパティは、**ITableDefinition** でのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-117">Description: This property is used only in **ITableDefinition**.</span></span> <span data-ttu-id="d8f3c-118">このプロパティに指定した文字列は、[CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) ステートメントの作成時に</span><span class="sxs-lookup"><span data-stu-id="d8f3c-118">The string specified in this property is used when creating a [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql)</span></span><br /><br /> <span data-ttu-id="d8f3c-119">ステートメントの使用などがあります。</span><span class="sxs-lookup"><span data-stu-id="d8f3c-119">statement.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="d8f3c-120">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d8f3c-120">In This Section</span></span>  
  
-   [<span data-ttu-id="d8f3c-121">SQL Server テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="d8f3c-121">Creating SQL Server Tables</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [<span data-ttu-id="d8f3c-122">SQL Server テーブルへの列の追加</span><span class="sxs-lookup"><span data-stu-id="d8f3c-122">Adding a Column to a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [<span data-ttu-id="d8f3c-123">SQL Server テーブルからの列の削除</span><span class="sxs-lookup"><span data-stu-id="d8f3c-123">Removing a Column from a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [<span data-ttu-id="d8f3c-124">SQL Server テーブルの削除</span><span class="sxs-lookup"><span data-stu-id="d8f3c-124">Dropping a SQL Server Table</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [<span data-ttu-id="d8f3c-125">SQL Server インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="d8f3c-125">Creating SQL Server Indexes</span></span>](../../relational-databases/indexes/indexes.md)  
  
-   [<span data-ttu-id="d8f3c-126">SQL Server インデックスの削除</span><span class="sxs-lookup"><span data-stu-id="d8f3c-126">Dropping a SQL Server Index</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a><span data-ttu-id="d8f3c-127">参照</span><span class="sxs-lookup"><span data-stu-id="d8f3c-127">See Also</span></span>  
 <span data-ttu-id="d8f3c-128">[SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="d8f3c-128">[SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md) </span></span>  
 <span data-ttu-id="d8f3c-129">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d8f3c-129">[DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql) </span></span>  
 <span data-ttu-id="d8f3c-130">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d8f3c-130">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 [<span data-ttu-id="d8f3c-131">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d8f3c-131">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
