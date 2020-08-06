---
title: OLE DB API による機能強化された日付と時刻のサポート | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: rothja
ms.author: jroth
ms.openlocfilehash: cdb17f0d2104373ea797ff9403cc417dfaa3d868
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643813"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a><span data-ttu-id="5eaea-102">OLE DB API による機能強化された日付と時刻のサポート</span><span class="sxs-lookup"><span data-stu-id="5eaea-102">OLE DB API Support for Date and Time Enhancements</span></span>
  <span data-ttu-id="5eaea-103">機能強化された日付や時刻をサポートする OLE DB API を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5eaea-103">The following OLE DB APIs support enhanced date/time features.</span></span>  
  
|<span data-ttu-id="5eaea-104">機能</span><span class="sxs-lookup"><span data-stu-id="5eaea-104">Function</span></span>|<span data-ttu-id="5eaea-105">説明</span><span class="sxs-lookup"><span data-stu-id="5eaea-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5eaea-106">IAccessor::CreateAccessor</span><span class="sxs-lookup"><span data-stu-id="5eaea-106">IAccessor::CreateAccessor</span></span>|<span data-ttu-id="5eaea-107">アプリケーションで `datetime`、`datetime2`、および `smalldatetime` の各値を区別できるように、DBBINDING 構造体にフラグが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5eaea-107">A flag is added in the DBBINDING structure to enable applications to discriminate between `datetime`, `datetime2`, and `smalldatetime` values.</span></span> <span data-ttu-id="5eaea-108">詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eaea-108">For more information, see [Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="5eaea-109">IBCPSession::BCPColFmt</span><span class="sxs-lookup"><span data-stu-id="5eaea-109">IBCPSession::BCPColFmt</span></span>|<span data-ttu-id="5eaea-110">詳細については、「 [&#40;OLE DB および ODBC&#41;の拡張された日付/時刻型に対する一括コピーの変更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eaea-110">For more information, see [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span>|  
|<span data-ttu-id="5eaea-111">ICommandWithParameters::GetParameterInfo</span><span class="sxs-lookup"><span data-stu-id="5eaea-111">ICommandWithParameters::GetParameterInfo</span></span>|<span data-ttu-id="5eaea-112">詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eaea-112">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="5eaea-113">ICommandWithParameters::SetParameterinfo</span><span class="sxs-lookup"><span data-stu-id="5eaea-113">ICommandWithParameters::SetParameterinfo</span></span>|<span data-ttu-id="5eaea-114">詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eaea-114">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="5eaea-115">IColumnsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="5eaea-115">IColumnsRowset::GetColumnsRowset</span></span>|<span data-ttu-id="5eaea-116">詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eaea-116">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="5eaea-117">IColumnsInfo::GetColumnInfo</span><span class="sxs-lookup"><span data-stu-id="5eaea-117">IColumnsInfo::GetColumnInfo</span></span>|<span data-ttu-id="5eaea-118">詳細については、「[パラメーターと行セットのメタデータ](metadata-parameter-and-rowset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eaea-118">For more information, see[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).</span></span>|  
|<span data-ttu-id="5eaea-119">IDBSchemaRowset::GetRowset</span><span class="sxs-lookup"><span data-stu-id="5eaea-119">IDBSchemaRowset::GetRowset</span></span>|<span data-ttu-id="5eaea-120">影響を受けるスキーマ行セットについては、「[日付、時刻、スキーマ行セット](../native-client-ole-db-rowsets/rowsets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eaea-120">For details of the affected schema rowsets, see[Date and Time and Schema Rowsets](../native-client-ole-db-rowsets/rowsets.md).</span></span>|  
|<span data-ttu-id="5eaea-121">IRowsetFastLoad</span><span class="sxs-lookup"><span data-stu-id="5eaea-121">IRowsetFastLoad</span></span>|<span data-ttu-id="5eaea-122">このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。</span><span class="sxs-lookup"><span data-stu-id="5eaea-122">This interface supports the new date/time types, but there is no change to its interface.</span></span>|  
|<span data-ttu-id="5eaea-123">ITableDefinition::CreateTable</span><span class="sxs-lookup"><span data-stu-id="5eaea-123">ITableDefinition::CreateTable</span></span>|<span data-ttu-id="5eaea-124">詳細については、「[OLE DB の日付/時刻の強化に対するデータ型のサポート](data-type-support-for-ole-db-date-and-time-improvements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eaea-124">For more information, see [Data Type Support for OLE DB Date and Time Improvements](data-type-support-for-ole-db-date-and-time-improvements.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eaea-125">参照</span><span class="sxs-lookup"><span data-stu-id="5eaea-125">See Also</span></span>  
 [<span data-ttu-id="5eaea-126">日付と時刻の強化機能 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="5eaea-126">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
