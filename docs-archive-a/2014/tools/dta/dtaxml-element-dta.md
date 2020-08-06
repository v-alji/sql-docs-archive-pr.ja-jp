---
title: DTAXML 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9f428cf996bb819ece74c13226fcd5116a19142b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719239"
---
# <a name="dtaxml-element-dta"></a><span data-ttu-id="5695e-102">DTAXML 要素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="5695e-102">DTAXML Element (DTA)</span></span>
  <span data-ttu-id="5695e-103">データベース エンジン チューニング アドバイザーの XML 入力ファイルと出力ファイルにおけるルート要素 **DTAXML** には、データベース エンジン チューニング アドバイザーが生成するチューニング入力とチューニング出力を記述したすべての要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5695e-103">The root element of a Database Engine Tuning Advisor XML input or output file, **DTAXML** contains all elements that describe tuning input and the tuning output that Database Engine Tuning Advisor generates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5695e-104">構文</span><span class="sxs-lookup"><span data-stu-id="5695e-104">Syntax</span></span>  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="5695e-105">要素の属性</span><span class="sxs-lookup"><span data-stu-id="5695e-105">Element Attributes</span></span>  
  
|<span data-ttu-id="5695e-106">属性</span><span class="sxs-lookup"><span data-stu-id="5695e-106">Attribute</span></span>|<span data-ttu-id="5695e-107">説明</span><span class="sxs-lookup"><span data-stu-id="5695e-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns:xsi`|<span data-ttu-id="5695e-108">必須。</span><span class="sxs-lookup"><span data-stu-id="5695e-108">Required.</span></span> <span data-ttu-id="5695e-109">XML Schema Instance 名前空間を識別します。</span><span class="sxs-lookup"><span data-stu-id="5695e-109">Identifies the XML Schema Instance namespace.</span></span> <span data-ttu-id="5695e-110">この名前空間の属性を使用して、データベース エンジン チューニング アドバイザーの XML ファイルの検証に使用するスキーマを参照します。</span><span class="sxs-lookup"><span data-stu-id="5695e-110">Attributes from this namespace are used to reference the schema that is used to validate the Database Engine Tuning Advisor XML file.</span></span><br /><br /> <span data-ttu-id="5695e-111">必要な値: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)</span><span class="sxs-lookup"><span data-stu-id="5695e-111">Required value: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)</span></span>|  
|`xmlns`|<span data-ttu-id="5695e-112">必須。</span><span class="sxs-lookup"><span data-stu-id="5695e-112">Required.</span></span> <span data-ttu-id="5695e-113">データベース エンジン チューニング アドバイザーの名前空間を識別します。</span><span class="sxs-lookup"><span data-stu-id="5695e-113">Identifies the Database Engine Tuning Advisor namespace.</span></span><br /><br /> <span data-ttu-id="5695e-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の XML エディターを使用してデータベース エンジン チューニング アドバイザーの XML ファイルを編集する場合、F1 ヘルプとダイナミック ヘルプでは、この値を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの参照トピックを検索します。</span><span class="sxs-lookup"><span data-stu-id="5695e-114">If you edit the Database Engine Tuning Advisor XML file using the XML editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], this value is used by F1 Help and Dynamic Help to locate possible reference topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span><br /><br /> <span data-ttu-id="5695e-115">必須値 :</span><span class="sxs-lookup"><span data-stu-id="5695e-115">Required value:</span></span><br /><br /> <span data-ttu-id="5695e-116">[データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?LinkId=43100) の名前空間</span><span class="sxs-lookup"><span data-stu-id="5695e-116">[Database Engine Tuning Advisor XML Schema](https://go.microsoft.com/fwlink/?LinkId=43100) Namespace</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="5695e-117">要素の特性</span><span class="sxs-lookup"><span data-stu-id="5695e-117">Element Characteristics</span></span>  
  
|<span data-ttu-id="5695e-118">特徴</span><span class="sxs-lookup"><span data-stu-id="5695e-118">Characteristic</span></span>|<span data-ttu-id="5695e-119">説明</span><span class="sxs-lookup"><span data-stu-id="5695e-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5695e-120">**データ型と長さ**</span><span class="sxs-lookup"><span data-stu-id="5695e-120">**Data type and length**</span></span>|<span data-ttu-id="5695e-121">[なし] :</span><span class="sxs-lookup"><span data-stu-id="5695e-121">None.</span></span>|  
|<span data-ttu-id="5695e-122">**既定値**</span><span class="sxs-lookup"><span data-stu-id="5695e-122">**Default value**</span></span>|<span data-ttu-id="5695e-123">[なし] :</span><span class="sxs-lookup"><span data-stu-id="5695e-123">None.</span></span>|  
|<span data-ttu-id="5695e-124">**個数**</span><span class="sxs-lookup"><span data-stu-id="5695e-124">**Occurrence**</span></span>|<span data-ttu-id="5695e-125">DTA の XML ファイルにつき 1 回の出現が必要です。</span><span class="sxs-lookup"><span data-stu-id="5695e-125">Required once per DTA XML file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="5695e-126">要素の関係</span><span class="sxs-lookup"><span data-stu-id="5695e-126">Element Relationships</span></span>  
  
|<span data-ttu-id="5695e-127">リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="5695e-127">Relationship</span></span>|<span data-ttu-id="5695e-128">要素</span><span class="sxs-lookup"><span data-stu-id="5695e-128">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="5695e-129">**親要素**</span><span class="sxs-lookup"><span data-stu-id="5695e-129">**Parent element**</span></span>|<span data-ttu-id="5695e-130">なし</span><span class="sxs-lookup"><span data-stu-id="5695e-130">None</span></span>|  
|<span data-ttu-id="5695e-131">**子要素**</span><span class="sxs-lookup"><span data-stu-id="5695e-131">**Child elements**</span></span>|[<span data-ttu-id="5695e-132">DTAInput 要素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="5695e-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)<br /><br /> <span data-ttu-id="5695e-133">`DTAOutput`要素 (詳細については[データベースエンジンチューニングアドバイザー XML スキーマ](https://schemas.microsoft.com/sqlserver/)を参照してください)</span><span class="sxs-lookup"><span data-stu-id="5695e-133">`DTAOutput` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5695e-134">解説</span><span class="sxs-lookup"><span data-stu-id="5695e-134">Remarks</span></span>  
 <span data-ttu-id="5695e-135">XML 名前空間の詳細については、 [MSDN Library の「](https://go.microsoft.com/fwlink/?LinkId=7341) XML ドキュメントにおける名前空間 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5695e-135">For more information about XML namespaces, see [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5695e-136">例</span><span class="sxs-lookup"><span data-stu-id="5695e-136">Example</span></span>  
 <span data-ttu-id="5695e-137">一般的な **DTAXML** 要素の例については、「[XML 入力ファイル サンプル &#40;DTA&#41;](xml-input-file-samples-dta.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5695e-137">For examples of typical **DTAXML** elements, see [XML Input File Samples &#40;DTA&#41;](xml-input-file-samples-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5695e-138">参照</span><span class="sxs-lookup"><span data-stu-id="5695e-138">See Also</span></span>  
 <span data-ttu-id="5695e-139">[XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="5695e-139">[XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="5695e-140">データベース エンジン チューニング アドバイザーの起動および使用</span><span class="sxs-lookup"><span data-stu-id="5695e-140">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
