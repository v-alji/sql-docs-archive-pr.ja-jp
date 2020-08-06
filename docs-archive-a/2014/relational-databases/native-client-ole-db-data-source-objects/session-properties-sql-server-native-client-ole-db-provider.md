---
title: セッションのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
author: rothja
ms.author: jroth
ms.openlocfilehash: 99f2bc6def0f470f653446c87216c3e854b2f819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632450"
---
# <a name="session-properties"></a><span data-ttu-id="7a20a-102">セッション プロパティ</span><span class="sxs-lookup"><span data-stu-id="7a20a-102">Session Properties</span></span>
  <span data-ttu-id="7a20a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、OLE DB セッションプロパティを次のように解釈します。</span><span class="sxs-lookup"><span data-stu-id="7a20a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider interprets OLE DB session properties as follows.</span></span>  
  
|<span data-ttu-id="7a20a-104">プロパティ ID</span><span class="sxs-lookup"><span data-stu-id="7a20a-104">Property ID</span></span>|<span data-ttu-id="7a20a-105">説明</span><span class="sxs-lookup"><span data-stu-id="7a20a-105">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7a20a-106">DBPROP_SESS_AUTOCOMMITISOLEVELS</span><span class="sxs-lookup"><span data-stu-id="7a20a-106">DBPROP_SESS_AUTOCOMMITISOLEVELS</span></span>|<span data-ttu-id="7a20a-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、混乱レベルの DBPROPVAL_TI_CHAOS を除き、すべての自動コミットトランザクション分離レベルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="7a20a-107">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports all autocommit transaction isolation levels with the exception of the chaos level DBPROPVAL_TI_CHAOS.</span></span>|  
  
 <span data-ttu-id="7a20a-108">プロバイダー固有のプロパティセット DBPROPSET_SQLSERVERSESSION では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、次の追加のセッションプロパティが定義されます。</span><span class="sxs-lookup"><span data-stu-id="7a20a-108">In the provider-specific property set DBPROPSET_SQLSERVERSESSION, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following additional session property.</span></span>  
  
|<span data-ttu-id="7a20a-109">プロパティ ID</span><span class="sxs-lookup"><span data-stu-id="7a20a-109">Property ID</span></span>|<span data-ttu-id="7a20a-110">説明</span><span class="sxs-lookup"><span data-stu-id="7a20a-110">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7a20a-111">SSPROP_QUOTEDCATALOGNAMES</span><span class="sxs-lookup"><span data-stu-id="7a20a-111">SSPROP_QUOTEDCATALOGNAMES</span></span>|<span data-ttu-id="7a20a-112">型: VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="7a20a-112">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="7a20a-113">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="7a20a-113">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="7a20a-114">既定値はVARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="7a20a-114">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="7a20a-115">説明 : CATALOG 制約で、引用符で囲まれた識別子を許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7a20a-115">Description: Quoted identifiers allowed in CATALOG restriction.</span></span><br /><br /> <span data-ttu-id="7a20a-116">VARIANT_TRUE: 分散クエリをサポートするスキーマ行セットのカタログ制約で、引用符で囲まれた識別子が認識されます。</span><span class="sxs-lookup"><span data-stu-id="7a20a-116">VARIANT_TRUE: Quoted identifiers are recognized for a catalog restriction for the schema rowsets that supply distributed query support.</span></span><br /><br /> <span data-ttu-id="7a20a-117">VARIANT_FALSE: 分散クエリをサポートするスキーマ行セットのカタログ制約で、引用符で囲まれた識別子が認識されません。</span><span class="sxs-lookup"><span data-stu-id="7a20a-117">VARIANT_FALSE: Quoted identifiers are not recognized for a catalog restriction for the schema rowsets that supply distributed query support.</span></span><br /><br /> <span data-ttu-id="7a20a-118">分散クエリをサポートするスキーマ行セットの詳細については、「[スキーマ行セットでの分散クエリのサポート](../native-client/ole-db/schema-rowsets-distributed-query-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a20a-118">For more information about schema rowsets that supply distributed query support, see [Distributed Query Support in Schema Rowsets](../native-client/ole-db/schema-rowsets-distributed-query-support.md).</span></span>|  
|<span data-ttu-id="7a20a-119">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="7a20a-119">SSPROP_ALLOWNATIVEVARIANT</span></span>|<span data-ttu-id="7a20a-120">型: VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="7a20a-120">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="7a20a-121">R/W: 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="7a20a-121">R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="7a20a-122">既定値はVARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="7a20a-122">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="7a20a-123">説明 : データを DBTYPE_VARIANT と DBTYPE_SQLVARIANT のどちらとしてフェッチするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="7a20a-123">Description: Determines if the data fetched in is as DBTYPE_VARIANT or DBTYPE_SQLVARIANT.</span></span><br /><br /> <span data-ttu-id="7a20a-124">VARIANT_TRUE: 列の型は DBTYPE_SQLVARIANT として返され、バッファーには SSVARIANT 構造体が保持されます。</span><span class="sxs-lookup"><span data-stu-id="7a20a-124">VARIANT_TRUE: Column type is returned as DBTYPE_SQLVARIANT in which case the buffer will hold SSVARIANT structure.</span></span><br /><br /> <span data-ttu-id="7a20a-125">VARIANT_FALSE: 列の型は DBTYPE_VARIANT として返され、バッファーには VARIANT 構造体が保持されます。</span><span class="sxs-lookup"><span data-stu-id="7a20a-125">VARIANT_FALSE: Column type is returned as DBTYPE_VARIANT and the buffer will have VARIANT structure.</span></span>|  
|<span data-ttu-id="7a20a-126">SSPROP_ASYNCH_BULKCOPY</span><span class="sxs-lookup"><span data-stu-id="7a20a-126">SSPROP_ASYNCH_BULKCOPY</span></span>|<span data-ttu-id="7a20a-127">非同期モードを使用するには、プロバイダー固有のセッション プロパティ SSPROP_ASYNCH_BULKCOPY を VARIANT_TRUE に設定してから、BCPExec メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7a20a-127">To use asynchronous mode, set the provider specific session property SSPROP_ASYNCH_BULKCOPY to VARIANT_TRUE before calling the BCPExec method.</span></span> <span data-ttu-id="7a20a-128">このプロパティは、DBPROPSET_SQLSERVERSESSION プロパティ セットに含まれています。</span><span class="sxs-lookup"><span data-stu-id="7a20a-128">This property is available in the DBPROPSET_SQLSERVERSESSION property set.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a20a-129">参照</span><span class="sxs-lookup"><span data-stu-id="7a20a-129">See Also</span></span>  
 [<span data-ttu-id="7a20a-130">データ ソース オブジェクト &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="7a20a-130">Data Source Objects &#40;OLE DB&#41;</span></span>](data-source-objects-ole-db.md)  
  
  
