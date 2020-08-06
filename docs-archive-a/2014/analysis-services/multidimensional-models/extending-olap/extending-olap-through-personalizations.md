---
title: パーソナルを使用した OLAP の拡張 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93669980e989b1cb11673f45c111de3609bbe920
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741394"
---
# <a name="extending-olap-through-personalizations"></a><span data-ttu-id="40960-102">パーソナル化による OLAP の拡張</span><span class="sxs-lookup"><span data-stu-id="40960-102">Extending OLAP through personalizations</span></span>
  <span data-ttu-id="40960-103">Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] には、多次元式 (MDX) やデータ マイニング拡張機能 (DMX) 言語と組み合わせて使用できる組み込み関数が豊富に用意されています。</span><span class="sxs-lookup"><span data-stu-id="40960-103">Microsoft  [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] supplies many intrinsic functions for use with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages.</span></span> <span data-ttu-id="40960-104">これらの関数は、標準的な統計計算から階層に含まれるメンバーのスキャンまで、さまざまな処理に対応できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="40960-104">These functions are designed to accomplish everything from standard statistical calculations to traversing members in a hierarchy.</span></span> <span data-ttu-id="40960-105">ただし、その他の複雑で堅牢な製品と同様に、常にこのような製品の機能をさらに拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40960-105">However, as with any other complex and robust product, there is always the need to extend the functionality of such a product further.</span></span>  
  
 <span data-ttu-id="40960-106">そのため、Analysis Services は、標準機能だけでは満たすことのできないビジネス ニーズを補うために、サービスのインスタンスにアセンブリやパーソナル化された拡張機能を追加できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="40960-106">Therefore, Analysis Services provides you with the ability to add assemblies and personalized extensions to an instance of the service, in order to complete your business needs whenever the standard functionality is not enough.</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="40960-107">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="40960-107">Assemblies</span></span>  
 <span data-ttu-id="40960-108">アセンブリにより、MDX と DMX のビジネス機能の拡張が可能になります。</span><span class="sxs-lookup"><span data-stu-id="40960-108">Assemblies enable you to extend the business functionality of MDX and DMX.</span></span> <span data-ttu-id="40960-109">必要な機能をダイナミック リンク ライブラリ (DLL) などのライブラリとして作成し、このライブラリをアセンブリとして Analysis Services のインスタンスまたは Analysis Services データベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="40960-109">You build the functionality that you want into a library, such as a dynamic link library (DLL), then add the library as an assembly to an instance of Analysis Services or to an Analysis Services database.</span></span> <span data-ttu-id="40960-110">ライブラリ内のパブリック メソッドは、ユーザー定義関数として、MDX および DMX 式、プロシージャ、計算、動作、およびクライアント アプリケーションに公開されます。</span><span class="sxs-lookup"><span data-stu-id="40960-110">The public methods in the library are then exposed as user-defined functions to MDX and DMX expressions, procedures, calculations, actions, and client applications.</span></span>  
  
## <a name="personalized-extensions"></a><span data-ttu-id="40960-111">パーソナル化拡張機能</span><span class="sxs-lookup"><span data-stu-id="40960-111">Personalized Extensions</span></span>  
 <span data-ttu-id="40960-112">SQL Server Analysis Services のパーソナル化拡張機能は、プラグイン アーキテクチャを実装するという概念の基盤です。</span><span class="sxs-lookup"><span data-stu-id="40960-112">SQL Server Analysis Services personalization extensions are the foundation of the idea of implementing a plug-in architecture.</span></span> <span data-ttu-id="40960-113">Analysis Services パーソナル化拡張機能は、既存のマネージアセンブリアーキテクチャに対する単純で洗練された変更であり、Analysis Services [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120))オブジェクトモデル、多次元式 (MDX) 構文、およびスキーマ行セット全体で公開されます。</span><span class="sxs-lookup"><span data-stu-id="40960-113">Analysis Services personalization extensions are a simple and elegant modification to the existing managed assembly architecture and are exposed throughout the Analysis Services [Microsoft.AnalysisServices.AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) object model, Multidimensional Expressions (MDX) syntax, and schema rowsets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40960-114">参照</span><span class="sxs-lookup"><span data-stu-id="40960-114">See Also</span></span>  
 <span data-ttu-id="40960-115">[多次元モデルのアセンブリの管理](../multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="40960-115">[Multidimensional Model Assemblies Management](../multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="40960-116">Analysis Services のパーソナル化拡張機能</span><span class="sxs-lookup"><span data-stu-id="40960-116">Analysis Services Personalization Extensions</span></span>](analysis-services-personalization-extensions.md)  
  
  
