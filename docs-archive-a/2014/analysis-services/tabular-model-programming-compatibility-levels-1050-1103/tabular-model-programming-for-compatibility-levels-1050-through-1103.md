---
title: テーブルモデルのプログラミング |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2565ed28a882750ab9b37beadbce698d3a0abb19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743478"
---
# <a name="tabular-model-programming"></a><span data-ttu-id="58ba8-102">テーブル モデルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="58ba8-102">Tabular Model Programming</span></span>
  <span data-ttu-id="58ba8-103">テーブル モデルでは、リレーショナル構造を使用して、分析アプリケーションおよびレポート アプリケーションによって使用される Analysis Services のデータがモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="58ba8-103">Tabular models use relational constructs to model the Analysis Services data used by analytical and reporting applications.</span></span> <span data-ttu-id="58ba8-104">これらのモデルは、ストレージ用のメモリ内分析エンジンおよび要求に応じてデータを集計して計算する高速テーブル スキャンを使用して、テーブル モード用に構成された Analysis Service インスタンスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="58ba8-104">These models run on an Analysis Service instance that is configured for tabular mode, using an in-memory analytics engine for storage and fast table scans that aggregate and calculate data as it is requested.</span></span>  
  
 <span data-ttu-id="58ba8-105">プログラム的には、AMO、ADOMD.NET、XMLA、または OLE DB で使用するオブジェクトは、テーブル ソリューションでも多次元ソリューションでも基本的に同じです。</span><span class="sxs-lookup"><span data-stu-id="58ba8-105">Programmatically, the objects you work with in AMO, ADOMD.NET, XMLA, or OLE DB are fundamentally the same for both tabular and multidimensional solutions.</span></span> <span data-ttu-id="58ba8-106">カスタム BI ソリューションの要件がテーブル モデル データベースによって最もよく満たされる場合は、任意の Analysis Services クライアント ライブラリおよびプログラミング インターフェイスを使用して、アプリケーションと Analysis Services インスタンス上のテーブル モデルを統合できます。</span><span class="sxs-lookup"><span data-stu-id="58ba8-106">If the requirements of your custom BI solution are best met by a tabular model database, you can use any of the Analysis Services client libraries and programming interfaces to integrate your application with tabular models on an Analysis Services instance.</span></span> <span data-ttu-id="58ba8-107">テーブル モデルのデータをクエリおよび計算するには、組み込まれた MDX または DAX をコードで使用できます。</span><span class="sxs-lookup"><span data-stu-id="58ba8-107">To query and calculate tabular model data, you can use either embedded MDX or DAX in your code.</span></span>  
  
 <span data-ttu-id="58ba8-108">ここでは、テーブル モデル エンティティとそのプロパティをプログラムで操作する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="58ba8-108">This section provides more information about how you can programmatically work with tabular model entities and their properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58ba8-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="58ba8-109">In This Section</span></span>  
 [<span data-ttu-id="58ba8-110">ビジネス インテリジェンス向けの CSDL 注釈 (CSDLBI)</span><span class="sxs-lookup"><span data-stu-id="58ba8-110">CSDL Annotations for Business Intelligence &#40;CSDLBI&#41;</span></span>](/analysis-services/csdlbi/csdl-annotations-for-business-intelligence-csdlbi)  
  
 [<span data-ttu-id="58ba8-111">テーブル オブジェクト モデルについて</span><span class="sxs-lookup"><span data-stu-id="58ba8-111">Understanding the Tabular Object Model</span></span>](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [<span data-ttu-id="58ba8-112">CSDL への BI 注釈のテクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="58ba8-112">Technical Reference for BI Annotations to CSDL</span></span>](/analysis-services/csdlbi/technical-reference-for-bi-annotations-to-csdl)  
  
 [<span data-ttu-id="58ba8-113">IMDEmbedded インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58ba8-113">IMDEmbedded Interface</span></span>](imdembeddeddata-interface.md)  
  
## <a name="see-also"></a><span data-ttu-id="58ba8-114">参照</span><span class="sxs-lookup"><span data-stu-id="58ba8-114">See Also</span></span>  
 <span data-ttu-id="58ba8-115">[SSAS 表形式&#41;の表形式モデル &#40;](../tabular-models/tabular-models-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="58ba8-115">[Tabular Modeling &#40;SSAS Tabular&#41;](../tabular-models/tabular-models-ssas.md) </span></span>  
 [<span data-ttu-id="58ba8-116">SSAS 表形式&#41;&#40;テーブルモデルデザイナー</span><span class="sxs-lookup"><span data-stu-id="58ba8-116">Tabular Model Designer &#40;SSAS Tabular&#41;</span></span>](../tabular-model-designer-ssas-tabular.md)  
  
  
