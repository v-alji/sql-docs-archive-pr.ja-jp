---
title: XML 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, elements
- XML for Analysis, elements
- elements [XML for Analysis]
ms.assetid: 40ab2360-efb6-4ba6-bf23-e84964e51008
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c1e5b046bfa57302baefc43a4da989be9c70e08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644222"
---
# <a name="xml-elements-xmla"></a><span data-ttu-id="d871b-102">XML 要素 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="d871b-102">XML Elements (XMLA)</span></span>
  <span data-ttu-id="d871b-103">次のトピックでは、でサポートされるさまざまな XML for Analysis (XMLA) 要素のカテゴリについて説明し [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d871b-103">The following topics describe the various XML for Analysis (XMLA) element categories supported by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d871b-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d871b-104">In This Section</span></span>  
  
|<span data-ttu-id="d871b-105">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d871b-105">Property</span></span>|<span data-ttu-id="d871b-106">説明</span><span class="sxs-lookup"><span data-stu-id="d871b-106">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="d871b-107">XMLA&#41;&#40;ヘッダー</span><span class="sxs-lookup"><span data-stu-id="d871b-107">Headers &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/xml-elements-headers)|<span data-ttu-id="d871b-108">プロトコルレベルの機能を管理するために、アプリケーションまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスによって SOAP エンベロープの SOAP ヘッダーの中で送信される要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d871b-108">Describes those elements sent in the SOAP header of a SOAP envelope, either by an application or by an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, to manage protocol-level features.</span></span>|  
|[<span data-ttu-id="d871b-109">XMLA&#41;&#40;メソッド</span><span class="sxs-lookup"><span data-stu-id="d871b-109">Methods &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods)|<span data-ttu-id="d871b-110">データまたはメタデータの取得、またはインスタンスに対する操作の実行のために、アプリケーションによって [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに送信される SOAP エンベロープ内の最上位要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d871b-110">Describes the topmost elements sent by an application in a SOAP envelope to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to retrieve data or metadata, or to perform actions on the instance.</span></span>|  
|[<span data-ttu-id="d871b-111">XMLA&#41;&#40;コマンド</span><span class="sxs-lookup"><span data-stu-id="d871b-111">Commands &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/xml-elements-commands)|<span data-ttu-id="d871b-112">特定の操作を実行するために XMLA メソッド内で送信される要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d871b-112">Describes the elements sent within an XMLA method to perform a specific action.</span></span>|  
|[<span data-ttu-id="d871b-113">XMLA&#41;&#40;オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d871b-113">Objects &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|<span data-ttu-id="d871b-114">アプリケーションが、XMLA メソッドへの応答として [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスから受信する、SOAP エンベロープ内の最上位の要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d871b-114">Describes the topmost elements received by an application in a SOAP envelope from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in response to an XMLA method.</span></span>|  
|[<span data-ttu-id="d871b-115">XMLA&#41;&#40;プロパティ</span><span class="sxs-lookup"><span data-stu-id="d871b-115">Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/xml-elements-properties)|<span data-ttu-id="d871b-116">XMLA ヘッダー、メソッド、オブジェクト、またはコマンドの子要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d871b-116">Describes the child elements for XMLA headers, methods, objects, or commands.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d871b-117">参照</span><span class="sxs-lookup"><span data-stu-id="d871b-117">See Also</span></span>  
 <span data-ttu-id="d871b-118">[XMLA&#41;&#40;XML データ型](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/xml-data-types-xmla) </span><span class="sxs-lookup"><span data-stu-id="d871b-118">[XML Data Types &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/xml-data-types-xmla) </span></span>  
 [<span data-ttu-id="d871b-119">Analysis Services スクリプト言語 (ASSL) での開発</span><span class="sxs-lookup"><span data-stu-id="d871b-119">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
  
