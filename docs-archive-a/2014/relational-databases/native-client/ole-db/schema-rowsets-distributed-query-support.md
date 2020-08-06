---
title: スキーマ行セットでの分散クエリのサポート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], SQL Server Native Client OLE DB provider
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
ms.assetid: 11354bb6-be42-4d8d-854c-42dd3dc38656
author: rothja
ms.author: jroth
ms.openlocfilehash: 48b57bbf40590f8ad5c049268f25fe66d2f94357
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633110"
---
# <a name="distributed-query-support-in-schema-rowsets"></a><span data-ttu-id="60945-102">スキーマ行セットでの分散クエリのサポート</span><span class="sxs-lookup"><span data-stu-id="60945-102">Distributed Query Support in Schema Rowsets</span></span>
  <span data-ttu-id="60945-103">分散クエリをサポートするために、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider **IDBSchemaRowset**インターフェイスは、リンクサーバー上のメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="60945-103">To support [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed queries, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider **IDBSchemaRowset** interface returns metadata on linked servers.</span></span>  
  
 <span data-ttu-id="60945-104">DBPROPSET_SQLSERVERSESSION の SSPROP_QUOTEDCATALOGNAMES プロパティが VARIANT_TRUE の場合、カタログ名には引用符で囲んだ識別子 ("my.catalog" など) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="60945-104">If the DBPROPSET_SQLSERVERSESSION property SSPROP_QUOTEDCATALOGNAMES is VARIANT_TRUE, a quoted identifier can be specified for the catalog name (for example "my.catalog").</span></span> <span data-ttu-id="60945-105">スキーマ行セットの出力をカタログによって制限する場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、リンクサーバーとカタログ名を含む2つの部分で構成される名前を認識します。</span><span class="sxs-lookup"><span data-stu-id="60945-105">When restricting schema rowset output by catalog, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider recognizes a two-part name containing the linked server and catalog name.</span></span> <span data-ttu-id="60945-106">次の表のスキーマ行セットの場合は、2部構成のカタログ名を_linked_server_として指定し**ます。**_カタログ_では、出力が名前付きリンクサーバーの適用可能なカタログに制限されます。</span><span class="sxs-lookup"><span data-stu-id="60945-106">For the schema rowsets in the table below, specifying a two-part catalog name as _linked_server_**.**_catalog_ restricts output to the applicable catalog of the named linked server.</span></span>  
  
|<span data-ttu-id="60945-107">スキーマ行セット</span><span class="sxs-lookup"><span data-stu-id="60945-107">Schema rowset</span></span>|<span data-ttu-id="60945-108">カタログの制限</span><span class="sxs-lookup"><span data-stu-id="60945-108">Catalog restriction</span></span>|  
|-------------------|-------------------------|  
|<span data-ttu-id="60945-109">DBSCHEMA_CATALOGS</span><span class="sxs-lookup"><span data-stu-id="60945-109">DBSCHEMA_CATALOGS</span></span>|<span data-ttu-id="60945-110">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="60945-110">CATALOG_NAME</span></span>|  
|<span data-ttu-id="60945-111">DBSCHEMA_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="60945-111">DBSCHEMA_COLUMNS</span></span>|<span data-ttu-id="60945-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="60945-112">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="60945-113">DBSCHEMA_PRIMARY_KEYS</span><span class="sxs-lookup"><span data-stu-id="60945-113">DBSCHEMA_PRIMARY_KEYS</span></span>|<span data-ttu-id="60945-114">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="60945-114">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="60945-115">DBSCHEMA_TABLES</span><span class="sxs-lookup"><span data-stu-id="60945-115">DBSCHEMA_TABLES</span></span>|<span data-ttu-id="60945-116">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="60945-116">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="60945-117">DBSCHEMA_FOREIGN_KEYS</span><span class="sxs-lookup"><span data-stu-id="60945-117">DBSCHEMA_FOREIGN_KEYS</span></span>|<span data-ttu-id="60945-118">PK_TABLE_CATALOG FK_TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="60945-118">PK_TABLE_CATALOG FK_TABLE_CATALOG</span></span>|  
|<span data-ttu-id="60945-119">DBSCHEMA_INDEXES</span><span class="sxs-lookup"><span data-stu-id="60945-119">DBSCHEMA_INDEXES</span></span>|<span data-ttu-id="60945-120">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="60945-120">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="60945-121">DBSCHEMA_COLUMN_PRIVILEGES</span><span class="sxs-lookup"><span data-stu-id="60945-121">DBSCHEMA_COLUMN_PRIVILEGES</span></span>|<span data-ttu-id="60945-122">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="60945-122">TABLE_CATALOG</span></span>|  
|<span data-ttu-id="60945-123">DBSCHEMA_TABLE_PRIVILEGES</span><span class="sxs-lookup"><span data-stu-id="60945-123">DBSCHEMA_TABLE_PRIVILEGES</span></span>|<span data-ttu-id="60945-124">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="60945-124">TABLE_CATALOG</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="60945-125">スキーマ行セットをリンク サーバーのすべてのカタログに制限するには、*linked_server* 構文を使用します (ピリオドを区切り文字として名前を指定します)。</span><span class="sxs-lookup"><span data-stu-id="60945-125">To restrict a schema rowset to all catalogs from a linked server, use the syntax *linked_server* (where the period separator is part of the name specification).</span></span> <span data-ttu-id="60945-126">この構文は、カタログ名の制限で NULL を指定する場合と同じで、カタログをサポートしないデータ ソースをリンク サーバーが示している場合にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="60945-126">This syntax is equivalent to specifying NULL for the catalog name restriction and is also used when the linked server indicates a data source that does not support catalogs.</span></span>  
  
 <span data-ttu-id="60945-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、リンクサーバーとして登録された OLE DB データソースの一覧を返す、スキーマ行セットの LINKEDSERVERS を定義します。</span><span class="sxs-lookup"><span data-stu-id="60945-127">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the schema rowset LINKEDSERVERS, returning a list of OLE DB data sources registered as linked servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60945-128">参照</span><span class="sxs-lookup"><span data-stu-id="60945-128">See Also</span></span>  
 <span data-ttu-id="60945-129">[スキーマ行セットのサポート &#40;OLE DB&#41;](schema-rowset-support-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="60945-129">[Schema Rowset Support &#40;OLE DB&#41;](schema-rowset-support-ole-db.md) </span></span>  
 [<span data-ttu-id="60945-130">LINKEDSERVERS 行セット &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="60945-130">LINKEDSERVERS Rowset &#40;OLE DB&#41;</span></span>](schema-rowsets-linkedservers-rowset.md)  
  
  
