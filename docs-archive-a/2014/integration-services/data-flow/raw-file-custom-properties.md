---
title: RAW ファイルのカスタム プロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7e81f7e1-fac0-4b57-b145-8f1b9e4720bf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7614c03fbf44f37597e586549e306d01c28b523d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633926"
---
# <a name="raw-file-custom-properties"></a><span data-ttu-id="61f16-102">RAW ファイルのカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="61f16-102">Raw File Custom Properties</span></span>
  <span data-ttu-id="61f16-103">**変換元のカスタム プロパティ**</span><span class="sxs-lookup"><span data-stu-id="61f16-103">**Source Custom Properties**</span></span>  
  
 <span data-ttu-id="61f16-104">RAW ファイル ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。</span><span class="sxs-lookup"><span data-stu-id="61f16-104">The Raw File source has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="61f16-105">次の表は、RAW ファイル ソースのカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="61f16-105">The following table describes the custom properties of the Raw File source.</span></span> <span data-ttu-id="61f16-106">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="61f16-106">All properties are read/write.</span></span>  
  
|<span data-ttu-id="61f16-107">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="61f16-107">Property name</span></span>|<span data-ttu-id="61f16-108">データ型</span><span class="sxs-lookup"><span data-stu-id="61f16-108">Data Type</span></span>|<span data-ttu-id="61f16-109">説明</span><span class="sxs-lookup"><span data-stu-id="61f16-109">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="61f16-110">AccessMode</span><span class="sxs-lookup"><span data-stu-id="61f16-110">AccessMode</span></span>|<span data-ttu-id="61f16-111">Integer (列挙)</span><span class="sxs-lookup"><span data-stu-id="61f16-111">Integer (enumeration)</span></span>|<span data-ttu-id="61f16-112">生データへのアクセスに使用するモード。</span><span class="sxs-lookup"><span data-stu-id="61f16-112">The mode used to access the raw data.</span></span> <span data-ttu-id="61f16-113">有効な値は、`File name` (0) および `File name from variable` (1) です。</span><span class="sxs-lookup"><span data-stu-id="61f16-113">The possible values are `File name` (0) and `File name from variable` (1).</span></span> <span data-ttu-id="61f16-114">既定値は `File name` (0) です。</span><span class="sxs-lookup"><span data-stu-id="61f16-114">The default value is `File name` (0).</span></span>|  
|<span data-ttu-id="61f16-115">FileName</span><span class="sxs-lookup"><span data-stu-id="61f16-115">FileName</span></span>|<span data-ttu-id="61f16-116">String</span><span class="sxs-lookup"><span data-stu-id="61f16-116">String</span></span>|<span data-ttu-id="61f16-117">ソース ファイルのパスおよびファイル名。</span><span class="sxs-lookup"><span data-stu-id="61f16-117">The path and file name of the source file.</span></span>|  
  
 <span data-ttu-id="61f16-118">RAW ファイル ソースの出力および出力列には、カスタム プロパティがありません。</span><span class="sxs-lookup"><span data-stu-id="61f16-118">The output and the output columns of the Raw File source have no custom properties.</span></span>  
  
 <span data-ttu-id="61f16-119">詳細については、「 [RAW ファイル ソース](raw-file-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61f16-119">For more information, see [Raw File Source](raw-file-source.md).</span></span>  
  
 <span data-ttu-id="61f16-120">**変換先のカスタム プロパティ**</span><span class="sxs-lookup"><span data-stu-id="61f16-120">**Destination Custom Properties**</span></span>  
  
 <span data-ttu-id="61f16-121">RAW ファイル変換先には、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。</span><span class="sxs-lookup"><span data-stu-id="61f16-121">The Raw File destination has both custom properties and the properties common to all data flow components.</span></span>  
  
 <span data-ttu-id="61f16-122">次の表は、RAW ファイル変換先のカスタム プロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="61f16-122">The following table describes the custom properties of the Raw File destination.</span></span> <span data-ttu-id="61f16-123">すべてのプロパティは読み取り/書き込み可能です。</span><span class="sxs-lookup"><span data-stu-id="61f16-123">All properties are read/write.</span></span>  
  
|<span data-ttu-id="61f16-124">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="61f16-124">Property name</span></span>|<span data-ttu-id="61f16-125">データ型</span><span class="sxs-lookup"><span data-stu-id="61f16-125">Data Type</span></span>|<span data-ttu-id="61f16-126">説明</span><span class="sxs-lookup"><span data-stu-id="61f16-126">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="61f16-127">AccessMode</span><span class="sxs-lookup"><span data-stu-id="61f16-127">AccessMode</span></span>|<span data-ttu-id="61f16-128">Integer (列挙)</span><span class="sxs-lookup"><span data-stu-id="61f16-128">Integer (enumeration)</span></span>|<span data-ttu-id="61f16-129">FileName プロパティにファイル名を含めるか、またはファイル名が含まれる変数名を含めるかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="61f16-129">A value that specifies whether the FileName property contains a file name, or the name of a variable that contains a file name.</span></span> <span data-ttu-id="61f16-130">使用できるオプションは、`File name` (0) および `File name from variable` (1) です。</span><span class="sxs-lookup"><span data-stu-id="61f16-130">The options are `File name` (0) and `File name from variable` (1).</span></span>|  
|<span data-ttu-id="61f16-131">FileName</span><span class="sxs-lookup"><span data-stu-id="61f16-131">FileName</span></span>|<span data-ttu-id="61f16-132">String</span><span class="sxs-lookup"><span data-stu-id="61f16-132">String</span></span>|<span data-ttu-id="61f16-133">RAW ファイル変換先が書き込むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="61f16-133">The name of the file to which the Raw File destination writes.</span></span>|  
|<span data-ttu-id="61f16-134">WriteOption</span><span class="sxs-lookup"><span data-stu-id="61f16-134">WriteOption</span></span>|<span data-ttu-id="61f16-135">Integer (列挙)</span><span class="sxs-lookup"><span data-stu-id="61f16-135">Integer (enumeration)</span></span>|<span data-ttu-id="61f16-136">RAW ファイル変換先が、同じ名前の既存のファイルを削除するかどうかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="61f16-136">A value that specifies whether the Raw File destination deletes an existing file that has the same name.</span></span> <span data-ttu-id="61f16-137">使用できるオプションは、`Create Always` (0)、`Create Once` (1)、`Truncate and Append` (3)、および `Append` (2) です。</span><span class="sxs-lookup"><span data-stu-id="61f16-137">The options are `Create Always` (0), `Create Once` (1), `Truncate and Append` (3), and `Append` (2).</span></span> <span data-ttu-id="61f16-138">このプロパティの既定値は `Create Always` (0) です。</span><span class="sxs-lookup"><span data-stu-id="61f16-138">The default value of this property is `Create Always` (0).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="61f16-139">追加操作では、追加するデータのメタデータが、ファイル内の既存データのメタデータと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="61f16-139">An append operation requires the metadata of the appended data to match the metadata of the data already present in the file.</span></span>  
  
 <span data-ttu-id="61f16-140">RAW ファイル変換先の入力および入力列には、カスタム プロパティはありません。</span><span class="sxs-lookup"><span data-stu-id="61f16-140">The input and the input columns of the Raw File destination have no custom properties.</span></span>  
  
 <span data-ttu-id="61f16-141">詳細については、「 [RAW ファイル変換先](raw-file-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61f16-141">For more information, see [Raw File Destination](raw-file-destination.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61f16-142">参照</span><span class="sxs-lookup"><span data-stu-id="61f16-142">See Also</span></span>  
 [<span data-ttu-id="61f16-143">Common Properties</span><span class="sxs-lookup"><span data-stu-id="61f16-143">Common Properties</span></span>](../common-properties.md)  
  
  
