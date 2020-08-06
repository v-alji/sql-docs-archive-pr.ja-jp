---
title: 多次元モデル内のディメンション |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
author: minewiskan
ms.author: owend
ms.openlocfilehash: b9e452453b80de3656abf62cdcd90519cf4a6c99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741397"
---
# <a name="dimensions-in-multidimensional-models"></a><span data-ttu-id="b64e6-102">多次元モデル内のディメンション</span><span class="sxs-lookup"><span data-stu-id="b64e6-102">Dimensions in Multidimensional Models</span></span>
  <span data-ttu-id="b64e6-103">データベース ディメンションとは、ファクト データに関する情報を 1 つまたは複数のキューブで提供するための、属性と呼ばれる関連オブジェクトが集まったものです。</span><span class="sxs-lookup"><span data-stu-id="b64e6-103">A database dimension is a collection of related objects, called attributes, which can be used to provide information about fact data in one or more cubes.</span></span> <span data-ttu-id="b64e6-104">たとえば、Product ディメンションの一般的な属性としては、製品名、製品カテゴリ、製品ライン、製品サイズ、製品価格などがあります。</span><span class="sxs-lookup"><span data-stu-id="b64e6-104">For example, typical attributes in a product dimension might be product name, product category, product line, product size, and product price.</span></span> <span data-ttu-id="b64e6-105">これらのオブジェクトは、データ ソース ビューのテーブル内の列にバインドされており、</span><span class="sxs-lookup"><span data-stu-id="b64e6-105">These objects are bound to one or more columns in one or more tables in a data source view.</span></span> <span data-ttu-id="b64e6-106">既定では、これらの属性は、属性階層として表示され、キューブ内のファクト データを理解する際に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b64e6-106">By default, these attributes are visible as attribute hierarchies and can be used to understand the fact data in a cube.</span></span> <span data-ttu-id="b64e6-107">属性はユーザー定義階層にまとめることができます。これらの階層には、ユーザーがキューブ内のデータを参照する際に使用できるナビゲーション パスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b64e6-107">Attributes can be organized into user-defined hierarchies that provide navigational paths to assist users when browsing the data in a cube.</span></span>  
  
 <span data-ttu-id="b64e6-108">キューブには、ユーザーがファクト データの分析の基準として使用する、すべてのディメンションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b64e6-108">Cubes contain all the dimensions on which users base their analyses of fact data.</span></span> <span data-ttu-id="b64e6-109">キューブ内のデータベース ディメンションのインスタンスは、キューブ ディメンションと呼ばれ、キューブ内の 1 つ以上のメジャー グループに関連しています。</span><span class="sxs-lookup"><span data-stu-id="b64e6-109">An instance of a database dimension in a cube is called a cube dimension and relates to one or more measure groups in the cube.</span></span> <span data-ttu-id="b64e6-110">データベース ディメンションは、キューブで何度も使用できます。</span><span class="sxs-lookup"><span data-stu-id="b64e6-110">A database dimension can be used multiple times in a cube.</span></span> <span data-ttu-id="b64e6-111">たとえば、ファクト テーブルに時間関連のファクトが複数含まれている場合は、時間関連の各ファクトを分析するために別々のキューブ ディメンションを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b64e6-111">For example, a fact table can have multiple time-related facts, and a separate cube dimension can be defined to assist in analyzing each time-related fact.</span></span> <span data-ttu-id="b64e6-112">ただし、時間関連のデータベース ディメンションは 1 つしか必要ありません。つまり、時間に基づく複数のキューブ ディメンションをサポートするために、時間関連のリレーショナル データベースも 1 つしか必要となりません。</span><span class="sxs-lookup"><span data-stu-id="b64e6-112">However, only one time-related database dimension needs to exist, which also means that only one time-related relational database table needs to exist to support multiple cube dimensions based on time.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b64e6-113"> ディメンション デザインに関連するパフォーマンスの問題ついては、「 [SQL Server 2008 R2 Analysis Services パフォーマンス ガイド](https://go.microsoft.com/fwlink/?LinkId=306717)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b64e6-113">For performance issues related to dimension design, see the [SQL Server 2008 R2 Analysis Services Performance Guide](https://go.microsoft.com/fwlink/?LinkId=306717).</span></span>  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a><span data-ttu-id="b64e6-114">ディメンション、属性、および階層の定義</span><span class="sxs-lookup"><span data-stu-id="b64e6-114">Defining Dimensions, Attributes, and Hierarchies</span></span>  
 <span data-ttu-id="b64e6-115">データベースとキューブのディメンション、属性、および階層を定義するための最も簡単な方法は、キューブ ウィザードを使用して、キューブの定義と同時にディメンションを作成することです。</span><span class="sxs-lookup"><span data-stu-id="b64e6-115">The simplest method for defining database and cube dimensions, attributes, and hierarchies is to use the Cube Wizard to create dimensions at the same time that you define the cube.</span></span> <span data-ttu-id="b64e6-116">キューブ ウィザードでは、データ ソース ビューのディメンション テーブルに基づいてディメンションを作成します。このディメンション テーブルは、キューブで使用するために、ウィザードで指定されたり、ユーザーが指定したりします。</span><span class="sxs-lookup"><span data-stu-id="b64e6-116">The Cube Wizard will create dimensions based on the dimension tables in the data source view that the wizard identifies or that you specify for use in the cube.</span></span> <span data-ttu-id="b64e6-117">その後、データベース ディメンションを作成して新しいキューブに追加すると、キューブ ディメンションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b64e6-117">The wizard then creates the database dimensions and adds them to the new cube, creating cube dimensions.</span></span>  
  
 <span data-ttu-id="b64e6-118">キューブを作成するときは、データベースに既に存在するディメンションを新しいキューブに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="b64e6-118">When you create a cube, you can also add to the new cube any dimensions that already exist in the database.</span></span> <span data-ttu-id="b64e6-119">これらのディメンションは、別のキューブやディメンション ウィザードで以前に定義されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b64e6-119">These dimensions may have been previously defined for another cube or by the Dimension Wizard.</span></span> <span data-ttu-id="b64e6-120">データベース ディメンションは、定義した後に、ディメンション デザイナーで変更および構成できます。</span><span class="sxs-lookup"><span data-stu-id="b64e6-120">After a database dimension has been defined, you can modify and configure the database dimension in Dimension Designer.</span></span> <span data-ttu-id="b64e6-121">またキューブ ディメンションは、キューブ デザイナーで、限られた範囲内でカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="b64e6-121">You can also customize the cube dimension, to a limited extent, in Cube Designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b64e6-122">XMLA または分析管理オブジェクト (AMO) のいずれかを使用すると、ディメンション、属性、および階層をプログラムによってデザインおよび構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b64e6-122">You can also design and configure dimensions, attributes, and hierarchies programmatically by using either XMLA or Analysis Management Objects (AMO).</span></span> <span data-ttu-id="b64e6-123">詳細については、「 [Analysis Services Scripting Language &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)」と「[分析管理オブジェクト &#40;AMO&#41;を使用した開発](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b64e6-123">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) and [Developing with Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b64e6-124">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b64e6-124">In This Section</span></span>  
 <span data-ttu-id="b64e6-125">このトピックでは、次の内容について紹介します。</span><span class="sxs-lookup"><span data-stu-id="b64e6-125">The following table describes the topics in this section.</span></span>  
  
 [<span data-ttu-id="b64e6-126">データベース ディメンションの定義</span><span class="sxs-lookup"><span data-stu-id="b64e6-126">Define Database Dimensions</span></span>](define-database-dimensions.md)  
 <span data-ttu-id="b64e6-127">ディメンション デザイナーを使用して、データベース ディメンションを変更および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b64e6-127">Describes how to modify and configure a database dimension by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="b64e6-128">ディメンションの属性のプロパティの参照</span><span class="sxs-lookup"><span data-stu-id="b64e6-128">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
 <span data-ttu-id="b64e6-129">ディメンション デザイナーを使用して、データベース ディメンションの属性を定義、変更、および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b64e6-129">Describes how to define, modify, and configure a database dimension attribute by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="b64e6-130">属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="b64e6-130">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
 <span data-ttu-id="b64e6-131">ディメンション デザイナーを使用して、属性リレーションシップを定義、変更、および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b64e6-131">Describes how to define, modify, and configure an attribute relationship by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="b64e6-132">ユーザー定義階層の作成</span><span class="sxs-lookup"><span data-stu-id="b64e6-132">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
 <span data-ttu-id="b64e6-133">ディメンション デザイナーを使用してユーザー定義階層のディメンション属性を定義、変更、および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b64e6-133">Describes how to define, modify, and configure a user-defined hierarchy of dimension attributes by using Dimension Designer.</span></span>  
  
 [<span data-ttu-id="b64e6-134">ビジネス インテリジェンス ウィザードを使用したディメンションの拡張</span><span class="sxs-lookup"><span data-stu-id="b64e6-134">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 <span data-ttu-id="b64e6-135">ビジネス インテリジェンス ウィザードを使用して、データベース ディメンションを拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b64e6-135">Describes how to enhance a database dimension by using the Business Intelligence Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64e6-136">参照</span><span class="sxs-lookup"><span data-stu-id="b64e6-136">See Also</span></span>  
 [<span data-ttu-id="b64e6-137">多次元モデルのキューブ</span><span class="sxs-lookup"><span data-stu-id="b64e6-137">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
