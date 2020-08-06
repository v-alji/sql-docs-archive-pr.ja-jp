---
title: パースペクティブ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ready-only cube view
- OLAP objects [Analysis Services], perspectives
- storing data [Analysis Services], perspectives
- perspectives [Analysis Services]
- cubes [Analysis Services], perspectives
- visibility [Analysis Services]
- storage [Analysis Services], perspectives
ms.assetid: b064171e-b1b4-4f32-95e5-59e1b831c4c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: f385fd078500739d97394cd8856fc8bd6a3b87e8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716910"
---
# <a name="perspectives"></a><span data-ttu-id="348a8-102">パースペクティブ</span><span class="sxs-lookup"><span data-stu-id="348a8-102">Perspectives</span></span>
  <span data-ttu-id="348a8-103">パースペクティブは、ユーザーがキューブをより単純な方法で表示するための定義です。</span><span class="sxs-lookup"><span data-stu-id="348a8-103">A perspective is a definition that allows users to see a cube in a simpler way.</span></span> <span data-ttu-id="348a8-104">パースペクティブは、キューブの機能のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="348a8-104">A perspective is a subset of the features of a cube.</span></span> <span data-ttu-id="348a8-105">パースペクティブを使用すると、管理者がキューブのビューを作成できるので、ユーザーは各自にとって重要なデータに集中できます。</span><span class="sxs-lookup"><span data-stu-id="348a8-105">A perspective enables administrators to create views of a cube, helping users to focus on the most relevant data for them.</span></span> <span data-ttu-id="348a8-106">パースペクティブには、キューブのすべてのオブジェクトのサブセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="348a8-106">A perspective contains subsets of all objects from a cube.</span></span> <span data-ttu-id="348a8-107">パースペクティブには、親キューブに定義されていない要素を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="348a8-107">A perspective cannot include elements that are not defined in the parent cube.</span></span>  
  
 <span data-ttu-id="348a8-108">単純な <xref:Microsoft.AnalysisServices.Perspective> オブジェクトは、基本情報、ディメンション、メジャー グループ、計算、KPI、アクションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="348a8-108">A simple <xref:Microsoft.AnalysisServices.Perspective> object is composed of: basic information, dimensions, measure groups, calculations, KPIs, and actions.</span></span> <span data-ttu-id="348a8-109">基本情報には、パースペクティブの名前および既定のメジャーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="348a8-109">Basic information includes the name and the default measure of the perspective.</span></span> <span data-ttu-id="348a8-110">ディメンションは、キューブ ディメンションのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="348a8-110">The dimensions are a subset of the cube dimensions.</span></span> <span data-ttu-id="348a8-111">メジャー グループは、キューブのメジャー グループのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="348a8-111">The measure groups are a subset of the cube measure groups.</span></span> <span data-ttu-id="348a8-112">計算は、キューブの計算のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="348a8-112">The calculations are a subset of the cube calculations.</span></span> <span data-ttu-id="348a8-113">KPI は、キューブの KPI のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="348a8-113">The KPIs are a subset of the cube KPIs.</span></span> <span data-ttu-id="348a8-114">アクションは、キューブのアクションのサブセットです。</span><span class="sxs-lookup"><span data-stu-id="348a8-114">The actions are a subset of the cube actions.</span></span>  
  
 <span data-ttu-id="348a8-115">キューブを更新して処理するまで、パースペクティブは使用できません。</span><span class="sxs-lookup"><span data-stu-id="348a8-115">A cube has to be updated and processed before the perspective can be used.</span></span>  
  
 <span data-ttu-id="348a8-116">キューブは、ユーザーがを探索するために非常に複雑なオブジェクトになることがあり [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="348a8-116">Cubes can be very complex objects for users to explore in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="348a8-117">1 つのキューブで完全なデータ ウェアハウスのコンテンツを表現することができ、キューブ内の複数のメジャー グループで複数のファクト テーブルを表したり、複数のディメンション テーブルに基づいた複数のディメンションを伴うことがあります。</span><span class="sxs-lookup"><span data-stu-id="348a8-117">A single cube can represent the contents of a complete data warehouse, with multiple measure groups in a cube representing multiple fact tables, and multiple dimensions based on multiple dimension tables.</span></span> <span data-ttu-id="348a8-118">このようなキューブは非常に複雑で強力ですが、ビジネス インテリジェンス要件やレポート要件を満たすために、キューブのごく一部分しか操作する必要のないユーザーにとっては大きな負担になります。</span><span class="sxs-lookup"><span data-stu-id="348a8-118">Such a cube can be very complex and powerful, but daunting to users who may only need to interact with a small part of the cube in order to satisfy their business intelligence and reporting requirements.</span></span>  
  
 <span data-ttu-id="348a8-119">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、パースペクティブを使用して、でのキューブの認識される複雑さを軽減でき [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="348a8-119">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use a perspective to reduce the perceived complexity of a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="348a8-120">パースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをキューブに対して的を絞って作成するための、表示可能なサブセットを定義できます。</span><span class="sxs-lookup"><span data-stu-id="348a8-120">A perspective defines a viewable subset of a cube that provides focused, business-specific or application-specific viewpoints on the cube.</span></span> <span data-ttu-id="348a8-121">パースペクティブにより、キューブに含まれるオブジェクトの表示設定が決定されます。</span><span class="sxs-lookup"><span data-stu-id="348a8-121">The perspective controls the visibility of objects that are contained by a cube.</span></span> <span data-ttu-id="348a8-122">パースペクティブでは、次のオブジェクトの表示または非表示が可能です。</span><span class="sxs-lookup"><span data-stu-id="348a8-122">The following objects can be displayed or hidden in a perspective:</span></span>  
  
-   <span data-ttu-id="348a8-123">Dimensions</span><span class="sxs-lookup"><span data-stu-id="348a8-123">Dimensions</span></span>  
  
-   <span data-ttu-id="348a8-124">属性</span><span class="sxs-lookup"><span data-stu-id="348a8-124">Attributes</span></span>  
  
-   <span data-ttu-id="348a8-125">階層</span><span class="sxs-lookup"><span data-stu-id="348a8-125">Hierarchies</span></span>  
  
-   <span data-ttu-id="348a8-126">メジャー グループ</span><span class="sxs-lookup"><span data-stu-id="348a8-126">Measure groups</span></span>  
  
-   <span data-ttu-id="348a8-127">メジャー</span><span class="sxs-lookup"><span data-stu-id="348a8-127">Measures</span></span>  
  
-   <span data-ttu-id="348a8-128">主要業績評価指標 (Kpi)</span><span class="sxs-lookup"><span data-stu-id="348a8-128">Key Performance Indicators (KPIs)</span></span>  
  
-   <span data-ttu-id="348a8-129">計算 (計算されるメンバー、名前付きセット、スクリプト コマンド)</span><span class="sxs-lookup"><span data-stu-id="348a8-129">Calculations (calculated members, named sets, and script commands)</span></span>  
  
-   <span data-ttu-id="348a8-130">操作</span><span class="sxs-lookup"><span data-stu-id="348a8-130">Actions</span></span>  
  
 <span data-ttu-id="348a8-131">たとえば、サンプルデータベースの**Adventure works**キューブには、 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 11 個のメジャーグループと、売上、売上予測、財務データを表す20個の異なるキューブディメンションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="348a8-131">For example, the **Adventure Works** cube in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database contains eleven measure groups and twenty-one different cube dimensions, representing sales, sales forecasting, and financial data.</span></span> <span data-ttu-id="348a8-132">クライアント アプリケーションは完全なキューブを直接参照できますが、基本的な売上予測情報を抽出しようとしているユーザーにとって、このビューポイントでは扱いづらい可能性があります。</span><span class="sxs-lookup"><span data-stu-id="348a8-132">A client application can directly reference the complete cube, but this viewpoint may be overwhelming to a user trying to extract basic sales forecasting information.</span></span> <span data-ttu-id="348a8-133">代わりに、同じユーザーが [ **Sales Targets** ] パースペクティブを使用して、 **Adventure works**キューブのビューを売上予測に関連するオブジェクトのみに制限することができます。</span><span class="sxs-lookup"><span data-stu-id="348a8-133">Instead, the same user can use the **Sales Targets** perspective to limit the view of the **Adventure Works** cube to only those objects relevant to sales forecasting.</span></span>  
  
 <span data-ttu-id="348a8-134">パースペクティブでユーザーに表示されないキューブ内のオブジェクトでも、XML for Analysis (XMLA)、多次元式 (MDX)、またはデータ マイニング式 (DMX) のステートメントを使用して、直接参照し取得することができます。</span><span class="sxs-lookup"><span data-stu-id="348a8-134">Objects in a cube that are not visible to the user through a perspective can still be directly referenced and retrieved using XML for Analysis (XMLA), Multidimensional Expressions (MDX), or Data Mining Extensions (DMX) statements.</span></span> <span data-ttu-id="348a8-135">パースペクティブはキューブ内のオブジェクトへのアクセスを制限するものではありません。そのような目的で使用しないでください。パースペクティブは、キューブへのアクセスをより快適にするために使用するものです。</span><span class="sxs-lookup"><span data-stu-id="348a8-135">Perspectives do not restrict access to objects in a cube and should not be used as such; instead, perspectives are used to provide a better user experience while accessing a cube.</span></span>  
  
 <span data-ttu-id="348a8-136">パースペクティブはキューブの読み取り専用ビューであり、パースペクティブを使用してキューブ内のオブジェクトを変更したり、名前を変更したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="348a8-136">A perspective is a read-only view of the cube; objects in the cube cannot be renamed or changed by using a perspective.</span></span> <span data-ttu-id="348a8-137">同様に、パースペクティブを使用して表示部分の合計などのキューブの動作や機能を変更することもできません。</span><span class="sxs-lookup"><span data-stu-id="348a8-137">Similarly, the behavior or features of a cube, such as the use of visual totals, cannot be changed by using a perspective.</span></span>  
  
## <a name="security"></a><span data-ttu-id="348a8-138">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="348a8-138">Security</span></span>  
 <span data-ttu-id="348a8-139">パースペクティブは、セキュリティ メカニズムとして使用するためのものではなく、ビジネス インテリジェンス アプリケーションでのユーザーの使用体験をより良いものにするためのツールとして使用するものです。</span><span class="sxs-lookup"><span data-stu-id="348a8-139">Perspectives are not meant to be used as a security mechanism, but as a tool for providing a better user experience in business intelligence applications.</span></span> <span data-ttu-id="348a8-140">特定のパースペクティブのセキュリティはすべて、基になるキューブから継承されます。</span><span class="sxs-lookup"><span data-stu-id="348a8-140">All security for a particular perspective is inherited from the underlying cube.</span></span> <span data-ttu-id="348a8-141">たとえば、パースペクティブでは、ユーザーがアクセス権を持っていないキューブ内のオブジェクトにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="348a8-141">For example, perspectives cannot provide access to objects in a cube to which a user does not already have access.</span></span> <span data-ttu-id="348a8-142">パースペクティブでキューブのオブジェクトへのアクセスが提供されるようにするには、そのキューブのセキュリティを解決しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="348a8-142">- Security for the cube must be resolved before access to objects in the cube can be provided through a perspective.</span></span>  
  
  
