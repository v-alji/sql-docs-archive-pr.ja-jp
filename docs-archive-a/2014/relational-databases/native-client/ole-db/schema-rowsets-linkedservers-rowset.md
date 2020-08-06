---
title: LINKEDSERVERS 行セット (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
author: rothja
ms.author: jroth
ms.openlocfilehash: 80eded31ebae744e272757a53a7fd1f4b56bf358
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633108"
---
# <a name="linkedservers-rowset-ole-db"></a><span data-ttu-id="e1348-102">LINKEDSERVERS 行セット (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="e1348-102">LINKEDSERVERS Rowset (OLE DB)</span></span>
  <span data-ttu-id="e1348-103">**LINKEDSERVERS** 行セットは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 分散クエリに参加できる、組織のデータ ソースを列挙します。</span><span class="sxs-lookup"><span data-stu-id="e1348-103">The **LINKEDSERVERS** rowset enumerates organization data sources that can participate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distributed queries.</span></span>  
  
 <span data-ttu-id="e1348-104">**LINKEDSERVERS** 行セットは、次の列で構成されます。</span><span class="sxs-lookup"><span data-stu-id="e1348-104">The **LINKEDSERVERS** rowset contains the following columns.</span></span>  
  
|<span data-ttu-id="e1348-105">列名</span><span class="sxs-lookup"><span data-stu-id="e1348-105">Column name</span></span>|<span data-ttu-id="e1348-106">型を表すインジケーター</span><span class="sxs-lookup"><span data-stu-id="e1348-106">Type indicator</span></span>|<span data-ttu-id="e1348-107">説明</span><span class="sxs-lookup"><span data-stu-id="e1348-107">Description</span></span>|  
|-----------------|--------------------|-----------------|  
|<span data-ttu-id="e1348-108">SVR_NAME</span><span class="sxs-lookup"><span data-stu-id="e1348-108">SVR_NAME</span></span>|<span data-ttu-id="e1348-109">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="e1348-109">DBTYPE_WSTR</span></span>|<span data-ttu-id="e1348-110">リンク サーバーの名前。</span><span class="sxs-lookup"><span data-stu-id="e1348-110">Name of a linked server.</span></span>|  
|<span data-ttu-id="e1348-111">SVR_PRODUCT</span><span class="sxs-lookup"><span data-stu-id="e1348-111">SVR_PRODUCT</span></span>|<span data-ttu-id="e1348-112">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="e1348-112">DBTYPE_WSTR</span></span>|<span data-ttu-id="e1348-113">メーカーなどの名前。リンク サーバーの名前で表されるデータ ストアの種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="e1348-113">Manufacturer or other name identifying the type of data store represented by the name of the linked server.</span></span>|  
|<span data-ttu-id="e1348-114">SVR_PROVIDERNAME</span><span class="sxs-lookup"><span data-stu-id="e1348-114">SVR_PROVIDERNAME</span></span>|<span data-ttu-id="e1348-115">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="e1348-115">DBTYPE_WSTR</span></span>|<span data-ttu-id="e1348-116">サーバーからのデータにアクセスする場合に使用する OLE DB プロバイダーの表示名。</span><span class="sxs-lookup"><span data-stu-id="e1348-116">Friendly name of the OLE DB provider used to consume data from the server.</span></span>|  
|<span data-ttu-id="e1348-117">SVR_DATASOURCE</span><span class="sxs-lookup"><span data-stu-id="e1348-117">SVR_DATASOURCE</span></span>|<span data-ttu-id="e1348-118">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="e1348-118">DBTYPE_WSTR</span></span>|<span data-ttu-id="e1348-119">プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_DATASOURCE 文字列。</span><span class="sxs-lookup"><span data-stu-id="e1348-119">OLE DB DBPROP_INIT_DATASOURCE string used to acquire a data source from the provider.</span></span>|  
|<span data-ttu-id="e1348-120">SVR_PROVIDERSTRING</span><span class="sxs-lookup"><span data-stu-id="e1348-120">SVR_PROVIDERSTRING</span></span>|<span data-ttu-id="e1348-121">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="e1348-121">DBTYPE_WSTR</span></span>|<span data-ttu-id="e1348-122">プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_PROVIDERSTRING 値。</span><span class="sxs-lookup"><span data-stu-id="e1348-122">OLE DB DBPROP_INIT_PROVIDERSTRING value used to acquire a data source from the provider.</span></span>|  
|<span data-ttu-id="e1348-123">SVR_LOCATION</span><span class="sxs-lookup"><span data-stu-id="e1348-123">SVR_LOCATION</span></span>|<span data-ttu-id="e1348-124">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="e1348-124">DBTYPE_WSTR</span></span>|<span data-ttu-id="e1348-125">プロバイダーからデータ ソースを取得する場合に使用する OLE DB DBPROP_INIT_LOCATION 文字列。</span><span class="sxs-lookup"><span data-stu-id="e1348-125">OLE DB DBPROP_INIT_LOCATION string used to acquire a data source from the provider.</span></span>|  
  
 <span data-ttu-id="e1348-126">行セットは SRV_NAME で並べ替えられます。SRV_NAME では 1 つの制限がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e1348-126">The rowset is sorted on SRV_NAME and a single restriction is supported on SRV_NAME.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1348-127">参照</span><span class="sxs-lookup"><span data-stu-id="e1348-127">See Also</span></span>  
 [<span data-ttu-id="e1348-128">スキーマ行セットのサポート &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="e1348-128">Schema Rowset Support &#40;OLE DB&#41;</span></span>](schema-rowset-support-ole-db.md)  
  
  
