---
title: データ ソース情報のプロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
author: rothja
ms.author: jroth
ms.openlocfilehash: c10a4e762bbe3421e720753941f5e0a5702832ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740878"
---
# <a name="data-source-information-properties"></a><span data-ttu-id="d3fb1-102">データ ソース情報のプロパティ</span><span class="sxs-lookup"><span data-stu-id="d3fb1-102">Data Source Information Properties</span></span>
  <span data-ttu-id="d3fb1-103">プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERDATASOURCEINFO には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにより、次のデータ ソース情報プロパティが定義されます。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-103">In the provider-specific property set DBPROPSET_SQLSERVERDATASOURCEINFO, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following data source information properties.</span></span>  
  
|<span data-ttu-id="d3fb1-104">プロパティ ID</span><span class="sxs-lookup"><span data-stu-id="d3fb1-104">Property ID</span></span>|<span data-ttu-id="d3fb1-105">説明</span><span class="sxs-lookup"><span data-stu-id="d3fb1-105">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d3fb1-106">SSPROP_COLUMNLEVELCOLLATION</span><span class="sxs-lookup"><span data-stu-id="d3fb1-106">SSPROP_COLUMNLEVELCOLLATION</span></span>|<span data-ttu-id="d3fb1-107">型: VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="d3fb1-107">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="d3fb1-108">R/W: 読み取り</span><span class="sxs-lookup"><span data-stu-id="d3fb1-108">R/W: Read</span></span><br /><br /> <span data-ttu-id="d3fb1-109">既定値 : VARIANT_TRUE</span><span class="sxs-lookup"><span data-stu-id="d3fb1-109">Default: VARIANT_TRUE</span></span><br /><br /> <span data-ttu-id="d3fb1-110">説明 : 列の照合順序がサポートされるかどうかの判断に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-110">Description: Used to determine if column collation is supported.</span></span><br /><br /> <span data-ttu-id="d3fb1-111">VARIANT_TRUE: 列レベルの照合順序がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-111">VARIANT_TRUE: Column level collation is supported.</span></span><br /><br /> <span data-ttu-id="d3fb1-112">VARIANT_FALSE: 列レベルの照合順序はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-112">VARIANT_FALSE: Column level collation is not supported.</span></span>|  
|<span data-ttu-id="d3fb1-113">SSPROP_UNICODELCID</span><span class="sxs-lookup"><span data-stu-id="d3fb1-113">SSPROP_UNICODELCID</span></span>|<span data-ttu-id="d3fb1-114">型 : VT_I4 R/W: 読み取り</span><span class="sxs-lookup"><span data-stu-id="d3fb1-114">Type: VT_I4 R/W: Read</span></span><br /><br /> <span data-ttu-id="d3fb1-115">説明 : Unicode ロケール ID です。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-115">Description: Unicode locale ID.</span></span><br /><br /> <span data-ttu-id="d3fb1-116">これは、Unicode データの並べ替えに使われるロケールです。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-116">This is the locale used for Unicode data sorting.</span></span>|  
|<span data-ttu-id="d3fb1-117">SSPROP_UNICODECOMPARISONSTYLE</span><span class="sxs-lookup"><span data-stu-id="d3fb1-117">SSPROP_UNICODECOMPARISONSTYLE</span></span>|<span data-ttu-id="d3fb1-118">型 : VT_I4 R/W: 読み取り</span><span class="sxs-lookup"><span data-stu-id="d3fb1-118">Type: VT_I4 R/W: Read</span></span><br /><br /> <span data-ttu-id="d3fb1-119">説明 : Unicode 比較形式です。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-119">Description: Unicode comparison style.</span></span><br /><br /> <span data-ttu-id="d3fb1-120">Unicode データの並べ替えに使われる並べ替えオプションです。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-120">The sorting options used for Unicode data sorting.</span></span>|  
  
 <span data-ttu-id="d3fb1-121">プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERSTREAM には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーにより、次の追加プロパティが定義されます。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-121">In the provider-specific property set DBPROPSET_SQLSERVERSTREAM, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following additional property.</span></span>  
  
|<span data-ttu-id="d3fb1-122">プロパティ ID</span><span class="sxs-lookup"><span data-stu-id="d3fb1-122">Property ID</span></span>|<span data-ttu-id="d3fb1-123">説明</span><span class="sxs-lookup"><span data-stu-id="d3fb1-123">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d3fb1-124">SSPROP_STREAM_XMLROOT</span><span class="sxs-lookup"><span data-stu-id="d3fb1-124">SSPROP_STREAM_XMLROOT</span></span>|<span data-ttu-id="d3fb1-125">型 : VT_BSTR R/W: 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="d3fb1-125">Type: VT_BSTR R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="d3fb1-126">説明: FOR XML クエリの結果に、整形式でないドキュメントを許可します。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-126">Description: The result of a FOR XML query may not be a well-formed document.</span></span> <span data-ttu-id="d3fb1-127">このプロパティを指定すると、'select ... for XML' クエリの結果はこのプロパティが提供するルート タグにラップされて、整形式の XML ドキュメントが返されます。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-127">When this property is specified, the result of a 'select ... for XML' query is wrapped in the root tag provided by this property to return a well formed XML document.</span></span> <span data-ttu-id="d3fb1-128">クエリがブラウザーから実行されている場合、結果の読み込み時にブラウザーがパーサー エラーを表示する場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-128">If the query is executed in the browser it may cause the browser to display parser errors when loading the result.</span></span> <span data-ttu-id="d3fb1-129">このエラーを回避するために、SQL ISAPI はキーワード ROOT をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-129">To avoid the error, SQL ISAPI supports the keyword ROOT.</span></span> <span data-ttu-id="d3fb1-130">このキーワードは SSPROP_STREAM_XMLROOT プロパティにマップされます。</span><span class="sxs-lookup"><span data-stu-id="d3fb1-130">This keyword maps to SSPROP_STREAM_XMLROOT property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3fb1-131">参照</span><span class="sxs-lookup"><span data-stu-id="d3fb1-131">See Also</span></span>  
 [<span data-ttu-id="d3fb1-132">データ ソース オブジェクト &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="d3fb1-132">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
