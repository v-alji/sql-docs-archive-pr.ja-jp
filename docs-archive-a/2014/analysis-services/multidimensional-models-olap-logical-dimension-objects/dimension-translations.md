---
title: ディメンションの翻訳 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], translations
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- LCIDs
- translations [Analysis Services], dimensions
ms.assetid: 38fc1e05-2ac9-4816-b52b-dfd19c3a43a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6f31773ad871ef7e3fc8f99d57e7a9099335b899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738970"
---
# <a name="dimension-translations"></a><span data-ttu-id="83b6e-102">ディメンションの翻訳</span><span class="sxs-lookup"><span data-stu-id="83b6e-102">Dimension Translations</span></span>
  <span data-ttu-id="83b6e-103">翻訳は、ラベルとキャプションの表示言語を変更する単純なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="83b6e-103">A translation is a simple mechanism to change the displayed labels and captions from one language to another.</span></span> <span data-ttu-id="83b6e-104">各翻訳は、値のペアとして定義されます。翻訳済みテキストの文字列と言語 ID の数値とのペアです。</span><span class="sxs-lookup"><span data-stu-id="83b6e-104">Each translation is defined as a pair of values: a string with the translated text, and a number with the language ID.</span></span> <span data-ttu-id="83b6e-105">翻訳は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のすべてのオブジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-105">Translations are available for all objects in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="83b6e-106">ディメンションは翻訳された属性値も持つことができます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-106">Dimensions can also have the attribute values translated.</span></span> <span data-ttu-id="83b6e-107">クライアント アプリケーションは、ユーザーによって定義された言語設定を検索し、すべてのキャプションとラベルの表示をその言語に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-107">The client application is responsible for finding the language setting that the user has defined, and switch to display all captions and labels to that language.</span></span> <span data-ttu-id="83b6e-108">1 つのオブジェクトに対する翻訳の数に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="83b6e-108">An object can have as many translations as you want.</span></span>  
  
 <span data-ttu-id="83b6e-109">簡単な <xref:Microsoft.AnalysisServices.Translation> オブジェクトは、言語 ID 番号およびキャプションの翻訳で構成されます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-109">A simple <xref:Microsoft.AnalysisServices.Translation> object is composed of: language ID number, and translated caption.</span></span> <span data-ttu-id="83b6e-110">言語 ID 番号は、言語 ID を含む `Integer` です。</span><span class="sxs-lookup"><span data-stu-id="83b6e-110">The language ID number is an `Integer` with the language ID.</span></span> <span data-ttu-id="83b6e-111">キャプションの翻訳は、翻訳されたテキストです。</span><span class="sxs-lookup"><span data-stu-id="83b6e-111">The translated caption is the translated text.</span></span>  
  
 <span data-ttu-id="83b6e-112">で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ディメンションの翻訳は、ディメンションの名前、オブジェクトの名前、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] またはキャプション、メンバー、階層レベルなどのメンバーの1つの名前を、言語固有で表現したものです。</span><span class="sxs-lookup"><span data-stu-id="83b6e-112">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], a dimension translation is a language-specific representation of the name of a dimension, the name of an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object or one of its members, such as a caption, member, or hierarchy level.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="83b6e-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、キューブオブジェクトの翻訳もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="83b6e-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] also supports translations of cube objects.</span></span>  
  
 <span data-ttu-id="83b6e-114">翻訳によって、複数言語を使用するクライアント アプリケーションをサーバーがサポートできるようになります。</span><span class="sxs-lookup"><span data-stu-id="83b6e-114">Translations provide server support for client applications that can support multiple languages.</span></span> <span data-ttu-id="83b6e-115">キューブとキューブのディメンションは、異なる国々のユーザーによって表示されることが頻繁にあります。</span><span class="sxs-lookup"><span data-stu-id="83b6e-115">Frequently, users from different countries view a cube and its dimensions.</span></span> <span data-ttu-id="83b6e-116">キューブやキューブのディメンションのさまざまな要素を異なる言語に翻訳できれば、異なる国々のユーザーがキューブを表示し、理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-116">It is useful to be able to translate various elements of a cube and its dimensions into a different language so that these users can view and understand the cube.</span></span> <span data-ttu-id="83b6e-117">たとえば、フランスのビジネス ユーザーは、フランス語ロケールが設定されているワークステーションからキューブにアクセスし、オブジェクト プロパティの値をフランス語で表示できます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-117">For example, a business user in France can access a cube from a workstation with a French locale setting, and see the object property values in French.</span></span> <span data-ttu-id="83b6e-118">ドイツのビジネス ユーザーがドイツ語ロケールの設定されたワークステーションから同じキューブにアクセスした場合は、オブジェクト プロパティの値をドイツ語で表示できます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-118">However, a business user in Germany who accesses the same cube from a workstation with a German locale setting sees the same object property values in German.</span></span>  
  
 <span data-ttu-id="83b6e-119">クライアント コンピューターの照合順序と言語の情報は、ロケール識別子 (LCID) の形式で保存されます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-119">The collation and language information for the client computer is stored in the form of a locale identifier (LCID).</span></span> <span data-ttu-id="83b6e-120">クライアントは接続時に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに LCID を渡します。</span><span class="sxs-lookup"><span data-stu-id="83b6e-120">Upon connection, the client passes the LCID to the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="83b6e-121">このインスタンスでは LCID を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのメタデータを表示する際にどの翻訳セットを使用するかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-121">The instance uses the LCID to determine which set of translations to use when providing metadata for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects.</span></span> <span data-ttu-id="83b6e-122">指定された翻訳が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトにない場合は、既定言語を使用してコンテンツがクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="83b6e-122">If an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object does not contain the specified translation, the default language is used to return the content back to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b6e-123">参照</span><span class="sxs-lookup"><span data-stu-id="83b6e-123">See Also</span></span>  
 <span data-ttu-id="83b6e-124">[キューブの翻訳](../multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span><span class="sxs-lookup"><span data-stu-id="83b6e-124">[Cube Translations](../multidimensional-models-olap-logical-cube-objects/cube-translations.md) </span></span>  
 <span data-ttu-id="83b6e-125">[翻訳 &#40;Analysis Services&#41;](../translations-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="83b6e-125">[Translations &#40;Analysis Services&#41;](../translations-analysis-services.md) </span></span>  
 [<span data-ttu-id="83b6e-126">グローバリゼーションのヒントとベスト プラクティス (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="83b6e-126">Globalization Tips and Best Practices &#40;Analysis Services&#41;</span></span>](../globalization-tips-and-best-practices-analysis-services.md)  
  
  
