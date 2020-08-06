---
title: XML ソースのカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e152b23b4f59ca46cb8272ca677dc1161b3efec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644034"
---
# <a name="xml-source-custom-properties"></a><span data-ttu-id="a1b43-102">XML 入力元のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1b43-102">XML Source Custom Properties</span></span>
  <span data-ttu-id="a1b43-103">XML ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。</span><span class="sxs-lookup"><span data-stu-id="a1b43-103">The XML source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="a1b43-104">次の表は、XML ソースのカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="a1b43-104">The following table describes the custom properties of the XML source.</span></span> <span data-ttu-id="a1b43-105">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="a1b43-105">All properties are read/write.</span></span>  
  
|<span data-ttu-id="a1b43-106">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="a1b43-106">Property name</span></span>|<span data-ttu-id="a1b43-107">データ型</span><span class="sxs-lookup"><span data-stu-id="a1b43-107">Data Type</span></span>|<span data-ttu-id="a1b43-108">説明</span><span class="sxs-lookup"><span data-stu-id="a1b43-108">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="a1b43-109">AccessMode</span><span class="sxs-lookup"><span data-stu-id="a1b43-109">AccessMode</span></span>|<span data-ttu-id="a1b43-110">整数</span><span class="sxs-lookup"><span data-stu-id="a1b43-110">Integer</span></span>|<span data-ttu-id="a1b43-111">XML データへのアクセスに使用するモード。</span><span class="sxs-lookup"><span data-stu-id="a1b43-111">The mode used to access the XML data.</span></span>|  
|<span data-ttu-id="a1b43-112">UseInlineSchema</span><span class="sxs-lookup"><span data-stu-id="a1b43-112">UseInlineSchema</span></span>|<span data-ttu-id="a1b43-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="a1b43-113">Boolean</span></span>|<span data-ttu-id="a1b43-114">XML ソース内のインライン スキーマ定義を使用するかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="a1b43-114">A value that indicates whether to use an inline schema definition within the XML source.</span></span> <span data-ttu-id="a1b43-115">このプロパティの既定値は `False` です。</span><span class="sxs-lookup"><span data-stu-id="a1b43-115">The default value of this property is `False`.</span></span>|  
|<span data-ttu-id="a1b43-116">XMLData</span><span class="sxs-lookup"><span data-stu-id="a1b43-116">XMLData</span></span>|<span data-ttu-id="a1b43-117">String</span><span class="sxs-lookup"><span data-stu-id="a1b43-117">String</span></span>|<span data-ttu-id="a1b43-118">XML データを取得するファイルまたは変数。</span><span class="sxs-lookup"><span data-stu-id="a1b43-118">The file or variables from which to retrieve the XML data.</span></span><br /><br /> <span data-ttu-id="a1b43-119">このプロパティの値は、プロパティ式を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a1b43-119">The value of this property can be specified by using a property expression.</span></span>|  
|<span data-ttu-id="a1b43-120">XMLSchemaDefinition</span><span class="sxs-lookup"><span data-stu-id="a1b43-120">XMLSchemaDefinition</span></span>|<span data-ttu-id="a1b43-121">String</span><span class="sxs-lookup"><span data-stu-id="a1b43-121">String</span></span>|<span data-ttu-id="a1b43-122">スキーマ定義ファイル (.xsd) のパスおよびファイル名。</span><span class="sxs-lookup"><span data-stu-id="a1b43-122">The path and file name of the schema definition file (.xsd).</span></span><br /><br /> <span data-ttu-id="a1b43-123">このプロパティの値は、プロパティ式を使用して指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a1b43-123">The value of this property can be specified by using a property expression.</span></span>|  
  
 <span data-ttu-id="a1b43-124">次の表は、XML ソースの出力のカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="a1b43-124">The following table describes the custom properties of the output of the XML source.</span></span> <span data-ttu-id="a1b43-125">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="a1b43-125">All properties are read/write.</span></span>  
  
|<span data-ttu-id="a1b43-126">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="a1b43-126">Property name</span></span>|<span data-ttu-id="a1b43-127">データ型</span><span class="sxs-lookup"><span data-stu-id="a1b43-127">Data Type</span></span>|<span data-ttu-id="a1b43-128">説明</span><span class="sxs-lookup"><span data-stu-id="a1b43-128">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="a1b43-129">RowsetID</span><span class="sxs-lookup"><span data-stu-id="a1b43-129">RowsetID</span></span>|<span data-ttu-id="a1b43-130">String</span><span class="sxs-lookup"><span data-stu-id="a1b43-130">String</span></span>|<span data-ttu-id="a1b43-131">出力に関連付けられた行セットを識別する値。</span><span class="sxs-lookup"><span data-stu-id="a1b43-131">A value that identifies the rowset associated with the output.</span></span>|  
  
 <span data-ttu-id="a1b43-132">XML ソースの出力列には、カスタム プロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="a1b43-132">The output columns of the XML source have no custom properties.</span></span>  
  
 <span data-ttu-id="a1b43-133">詳細については、「 [XML ソース](xml-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1b43-133">For more information, see [XML Source](xml-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1b43-134">参照</span><span class="sxs-lookup"><span data-stu-id="a1b43-134">See Also</span></span>  
 [<span data-ttu-id="a1b43-135">Common Properties</span><span class="sxs-lookup"><span data-stu-id="a1b43-135">Common Properties</span></span>](../common-properties.md)  
  
  
