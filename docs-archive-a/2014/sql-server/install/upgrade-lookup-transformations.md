---
title: 参照変換のアップグレード |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 74430ab1bed232b8d510a8c28a8a690d88d1f6ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632272"
---
# <a name="upgrade-lookup-transformations"></a><span data-ttu-id="71346-102">参照変換のアップグレード</span><span class="sxs-lookup"><span data-stu-id="71346-102">Upgrade Lookup Transformations</span></span>
  <span data-ttu-id="71346-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] を [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードする場合、パッケージに変更を加え、参照変換でこれらの新しい機能を利用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="71346-103">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] consider modifying packages to take advantage of the new features in the Lookup Transformation.</span></span> <span data-ttu-id="71346-104">この変換では、[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] で使用可能なキャッシュの種類とデータ出力オプションがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="71346-104">The transformation supports the caching types and data output options available in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)].</span></span> <span data-ttu-id="71346-105">キャッシュとデータ出力の詳細については、「[参照変換](../../integration-services/data-flow/transformations/lookup-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71346-105">For more information about additional the caching and data outputs, see [Lookup Transformation](../../integration-services/data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="71346-106">[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] で使用可能なキャッシュの種類は、完全キャッシュ、部分キャッシュ、およびキャッシュなしです。</span><span class="sxs-lookup"><span data-stu-id="71346-106">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the available caching types are full caching, partial caching, and no caching.</span></span> <span data-ttu-id="71346-107">[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] では、これらのいずれかの種類のキャッシュを使用するように参照変換を構成できます。</span><span class="sxs-lookup"><span data-stu-id="71346-107">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], you can configure a Lookup transformation to use one of these caching types.</span></span> <span data-ttu-id="71346-108">部分キャッシュまたはキャッシュなしの実装方法の詳細については、「[キャッシュなしモードまたは部分キャッシュモードでの参照の実装](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71346-108">For more information about how to implement partial caching or no caching, see [Implement a Lookup in No Cache or Partial Cache Mode](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md).</span></span> <span data-ttu-id="71346-109">完全キャッシュを実装する方法については、「[キャッシュ接続マネージャーを使用してフルキャッシュモードの参照変換を実装](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md)する」および「 [OLE DB 接続マネージャーを使用してフルキャッシュモードの参照変換を実装](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71346-109">For information about how to implement full caching, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) and [Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="71346-110">[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)] では、参照変換は 1 つの入力、1 つの出力、および 1 つのエラー出力になっていました。</span><span class="sxs-lookup"><span data-stu-id="71346-110">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the Lookup transformation had an input, an output, and an error output.</span></span> <span data-ttu-id="71346-111">参照データセットに一致するエントリがある入力の行は、出力で処理されていました。</span><span class="sxs-lookup"><span data-stu-id="71346-111">Rows in the input that had matching entries in the reference dataset were handled by the output.</span></span> <span data-ttu-id="71346-112">一致するエントリがない入力の行はエラーとして処理され、エラー出力にリダイレクトされていました。</span><span class="sxs-lookup"><span data-stu-id="71346-112">Rows in the input that did not have matching entries were treated as errors and could be redirected to the error output.</span></span> <span data-ttu-id="71346-113">[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] では、参照変換の出力は 2 つ (一致する出力と一致しない出力) になります。</span><span class="sxs-lookup"><span data-stu-id="71346-113">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], the Lookup transformation has two outputs: a match output and a no match output.</span></span>  
  
 <span data-ttu-id="71346-114">既定では、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] で作成された参照変換を実行すると、[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] では一致するエントリのない行はエラーとして処理され、その行はエラー出力にリダイレクトできます。</span><span class="sxs-lookup"><span data-stu-id="71346-114">By default, when you run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] treats the rows without matching entries as errors and enables you to redirect the rows to an error output.</span></span> <span data-ttu-id="71346-115">行をエラーではないものとして処理し、それらの行を、一致しない出力にリダイレクトするように参照変換を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="71346-115">You have the option of configuring the Lookup transformation to treat the rows as non-errors and redirect the rows to the no match output.</span></span>  
  
 <span data-ttu-id="71346-116">詳細については、「 [[参照変換エディター] &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71346-116">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71346-117">参照</span><span class="sxs-lookup"><span data-stu-id="71346-117">See Also</span></span>  
 [<span data-ttu-id="71346-118">参照変換</span><span class="sxs-lookup"><span data-stu-id="71346-118">Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
