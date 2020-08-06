---
title: SQL Server 2014 | の Analysis Services 廃止された機能Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, backward compatibility
- SSAS, backward compatibility
- SQL Server Analysis Services, backward compatibility
- discontinued functionality [Analysis Services]
- unsupported features [Analysis Services]
ms.assetid: 39406be1-9819-4629-9c29-b32fb20bab2e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5414344eb65c907593c9077ee2ba5610b8b397c0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645245"
---
# <a name="discontinued-analysis-services-functionality-in-sql-server-2014"></a><span data-ttu-id="be3d7-102">SQL Server 2014 で提供が中止された Analysis Services の機能</span><span class="sxs-lookup"><span data-stu-id="be3d7-102">Discontinued Analysis Services Functionality in SQL Server 2014</span></span>
  <span data-ttu-id="be3d7-103">このトピックでは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] で使用できなくなった [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="be3d7-103">This topic describes [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] features that are no longer available in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
## <a name="discontinued-features-in-sssql14"></a><span data-ttu-id="be3d7-104">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be3d7-104">Discontinued Features in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
  
|<span data-ttu-id="be3d7-105">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="be3d7-105">Category</span></span>|<span data-ttu-id="be3d7-106">非推奨の機能</span><span class="sxs-lookup"><span data-stu-id="be3d7-106">Deprecated feature</span></span>|<span data-ttu-id="be3d7-107">代替</span><span class="sxs-lookup"><span data-stu-id="be3d7-107">Replacement</span></span>|  
|--------------|------------------------|-----------------|  
|<span data-ttu-id="be3d7-108">ローカル キューブ</span><span class="sxs-lookup"><span data-stu-id="be3d7-108">Local cubes</span></span>|<span data-ttu-id="be3d7-109">InsertInto 接続文字列プロパティ</span><span class="sxs-lookup"><span data-stu-id="be3d7-109">InsertInto connection string property</span></span>|<span data-ttu-id="be3d7-110">ローカル キューブを設定するための元の接続文字列の構文は、CREATE GLOBAL CUBE ステートメントに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="be3d7-110">Original connection string syntax for populating local cubes is replaced by the Create Global Cube statement.</span></span> <span data-ttu-id="be3d7-111">詳細については、「 [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be3d7-111">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).</span></span>|  
|<span data-ttu-id="be3d7-112">ローカル キューブ</span><span class="sxs-lookup"><span data-stu-id="be3d7-112">Local cubes</span></span>|<span data-ttu-id="be3d7-113">CreateCube 接続文字列プロパティ</span><span class="sxs-lookup"><span data-stu-id="be3d7-113">CreateCube connection string property</span></span>|<span data-ttu-id="be3d7-114">ローカル キューブを設定するための元の接続文字列の構文は、CREATE GLOBAL CUBE ステートメントに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="be3d7-114">Original connection string syntax for populating local cubes is replaced by the Create Global Cube statement.</span></span> <span data-ttu-id="be3d7-115">詳細については、「 [CREATE GLOBAL CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be3d7-115">For more information, see [CREATE GLOBAL CUBE Statement  &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube).</span></span>|  
|<span data-ttu-id="be3d7-116">データ マイニング</span><span class="sxs-lookup"><span data-stu-id="be3d7-116">Data Mining</span></span>|<span data-ttu-id="be3d7-117">SQL Server 2000 PMML</span><span class="sxs-lookup"><span data-stu-id="be3d7-117">SQL Server 2000 PMML</span></span>|<span data-ttu-id="be3d7-118">SQL Server 2000 PMML 機能は、PMML 仕様では使用できなかったデータ マイニング アルゴリズムによって提供される独自の機能をサポートする専用の拡張機能がある PMML の形式を生成します。</span><span class="sxs-lookup"><span data-stu-id="be3d7-118">The SQL Server 2000 PMML feature produced a form of PMML that had proprietary extensions to support unique features provided by Data Mining algorithms that were not available in the PMML specification.</span></span> <span data-ttu-id="be3d7-119">SQL Server 2005 では、Analysis Services によって PMML 機能が新しい PMML 2. 1 標準に更新されました。</span><span class="sxs-lookup"><span data-stu-id="be3d7-119">In SQL Server 2005, Analysis Services updated the PMML feature to the newer PMML 2.1 standard.</span></span> <span data-ttu-id="be3d7-120">そのため、SQL Server 2000 で追加された専用の拡張機能は必要なくなりましたが、このリリースでもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="be3d7-120">As a result, the proprietary extensions added in SQL Server 2000 are no longer needed, although they are still supported in this release.</span></span>|  
|<span data-ttu-id="be3d7-121">MDX ステートメント</span><span class="sxs-lookup"><span data-stu-id="be3d7-121">MDX Statement</span></span>|<span data-ttu-id="be3d7-122">CREATE ACTION ステートメント</span><span class="sxs-lookup"><span data-stu-id="be3d7-122">Create Action statement</span></span>|<span data-ttu-id="be3d7-123">このステートメントは、旧バージョンとの互換性のために用意されています。</span><span class="sxs-lookup"><span data-stu-id="be3d7-123">This statement is included for backwards compatibility.</span></span> <span data-ttu-id="be3d7-124">このステートメントは、Action オブジェクトに置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="be3d7-124">It is replaced by the Action object.</span></span> <span data-ttu-id="be3d7-125">の最近のバージョンでアクションを作成する方法の詳細について [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、「 [actions &#40;Analysis Services-多次元データ&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be3d7-125">For more information about how to create actions in recent versions of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], see [Actions &#40;Analysis Services - Multidimensional Data&#41;](multidimensional-models/actions-analysis-services-multidimensional-data.md).</span></span>|  
  
## <a name="discontinued-features-in-previous-releases"></a><span data-ttu-id="be3d7-126">以前のリリースで廃止された機能</span><span class="sxs-lookup"><span data-stu-id="be3d7-126">Discontinued Features in Previous Releases</span></span>  
 <span data-ttu-id="be3d7-127">SQL Server 2000 Analysis Services データベースを新しいバージョンに移行する際に使用された移行ウィザードは、SQL Server 2000 がサポートされなくなったため、提供が中止されました。</span><span class="sxs-lookup"><span data-stu-id="be3d7-127">Migration Wizard, used to migrate SQL Server 2000 Analysis Services databases to newer versions, is discontinued because SQL Server 2000 is no longer supported.</span></span>  
  
 <span data-ttu-id="be3d7-128">SQL Server 2000 Analysis Services データベースとの互換性を維持するための Decision Support オブジェクト (DSO) ライブラリも提供が中止され、SQL Server に付属しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="be3d7-128">Decision Support Objects (DSO) library that provided compatibility with SQL Server 2000 Analysis Services databases is also discontinued and no longer part of SQL Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be3d7-129">参照</span><span class="sxs-lookup"><span data-stu-id="be3d7-129">See Also</span></span>  
 [<span data-ttu-id="be3d7-130">Analysis Services の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="be3d7-130">Analysis Services Backward Compatibility</span></span>](analysis-services-backward-compatibility.md)  
  
  
