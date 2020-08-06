---
title: OLE DB テーブル値パラメーター向けに変更されたスキーマ行セット | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
author: rothja
ms.author: jroth
ms.openlocfilehash: e09d5127f332c8b6cc948be3eeb74e600bb856f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739798"
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a><span data-ttu-id="97cc0-102">OLE DB テーブル値パラメーター向けに変更されたスキーマ行セット</span><span class="sxs-lookup"><span data-stu-id="97cc0-102">Schema Rowsets Changed for OLE DB Table-Valued Parameters</span></span>
  <span data-ttu-id="97cc0-103">テーブル値パラメーターをサポートするために変更または追加されたスキーマ行セットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="97cc0-103">The following are the schema rowsets that have been changed or added to support table-valued parameters.</span></span>  
  
|<span data-ttu-id="97cc0-104">スキーマ行セット</span><span class="sxs-lookup"><span data-stu-id="97cc0-104">Schema rowset</span></span>|<span data-ttu-id="97cc0-105">説明</span><span class="sxs-lookup"><span data-stu-id="97cc0-105">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="97cc0-106">DBSCHEMA_PROCEDURE_PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="97cc0-106">DBSCHEMA_PROCEDURE_PARAMETERS</span></span>|<span data-ttu-id="97cc0-107">SS_TYPE_CATALOG_NAME および SS_TYPE_SCHEMANAME という名前の 2 つの新しい列が、行セットの末尾に追加されました。</span><span class="sxs-lookup"><span data-stu-id="97cc0-107">Two new columns were added at the end of the rowset named SS_TYPE_CATALOG_NAME and SS_TYPE_SCHEMANAME.</span></span> <span data-ttu-id="97cc0-108">これらの列は、今後の型に再利用できます。</span><span class="sxs-lookup"><span data-stu-id="97cc0-108">These columns could be re-used for future types.</span></span> <span data-ttu-id="97cc0-109">TYPE_NAME 列および LOCAL_TYPE_NAME 列には、テーブル値パラメーター TABLE 型の名前が含まれます。</span><span class="sxs-lookup"><span data-stu-id="97cc0-109">The TYPE_NAME and LOCAL_TYPE_NAME columns will contain the name of the table-valued parameter TABLE type.</span></span> <span data-ttu-id="97cc0-110">DATA_TYPE 列には、テーブル値パラメーターの値 DBTYPE_TABLE = 143 が含まれます。</span><span class="sxs-lookup"><span data-stu-id="97cc0-110">The DATA_TYPE column will have value DBTYPE_TABLE = 143 for table-valued parameters.</span></span>|  
|<span data-ttu-id="97cc0-111">DBSCHEMA_TABLE_TYPES</span><span class="sxs-lookup"><span data-stu-id="97cc0-111">DBSCHEMA_TABLE_TYPES</span></span>|<span data-ttu-id="97cc0-112">この行セットは、テーブル値パラメーターをサポートするために追加されました。</span><span class="sxs-lookup"><span data-stu-id="97cc0-112">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="97cc0-113">これは、DBSCHEMA_TABLES と似ていますが、テーブル、ビュー、またはシノニムではなく、テーブル型のメタデータのみを返す点が異なります。</span><span class="sxs-lookup"><span data-stu-id="97cc0-113">It is identical to DBSCHEMA_TABLES, except that it returns metadata only for table types, rather than for tables, views, or synonyms.</span></span> <span data-ttu-id="97cc0-114">TABLE_TYPE 列の値は、'TABLE TYPE' になります。</span><span class="sxs-lookup"><span data-stu-id="97cc0-114">The TABLE_TYPE column will have the value 'TABLE TYPE'.</span></span>|  
|<span data-ttu-id="97cc0-115">DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS</span><span class="sxs-lookup"><span data-stu-id="97cc0-115">DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS</span></span>|<span data-ttu-id="97cc0-116">この行セットは、テーブル値パラメーターをサポートするために追加されました。</span><span class="sxs-lookup"><span data-stu-id="97cc0-116">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="97cc0-117">これは、DBSCHEMA_PRIMARY_KEYS と似ていますが、テーブルではなく、テーブル型の主キーのメタデータのみを返す点が異なります。</span><span class="sxs-lookup"><span data-stu-id="97cc0-117">It is identical to DBSCHEMA_PRIMARY_KEYS, except that it returns primary keys metadata only for table types, rather than for tables.</span></span>|  
|<span data-ttu-id="97cc0-118">DBSCHEMA_TABLE_TYPE_COLUMNS</span><span class="sxs-lookup"><span data-stu-id="97cc0-118">DBSCHEMA_TABLE_TYPE_COLUMNS</span></span>|<span data-ttu-id="97cc0-119">この行セットは、テーブル値パラメーターをサポートするために追加されました。</span><span class="sxs-lookup"><span data-stu-id="97cc0-119">This rowset was added to support table-valued parameters.</span></span> <span data-ttu-id="97cc0-120">これは、DBSCHEMA_COLUMNS と似ていますが、テーブル、ビュー、またはシノニムではなく、テーブル型の列のメタデータのみを返す点が異なります。</span><span class="sxs-lookup"><span data-stu-id="97cc0-120">It is identical to DBSCHEMA_COLUMNS, except that it returns column metadata only for table types, rather than for tables, views, or synonyms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97cc0-121">参照</span><span class="sxs-lookup"><span data-stu-id="97cc0-121">See Also</span></span>  
 <span data-ttu-id="97cc0-122">[テーブル値パラメーター &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="97cc0-122">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="97cc0-123">テーブル値パラメーターの使用 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="97cc0-123">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
