---
title: 変換を使用してデータを変換する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], transformations
- transformations [Integration Services], about transformations
- transforming data [Integration Services]
ms.assetid: e1340b6f-ef75-4b14-af6f-823586eff0ed
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 952d8ea4eeea2dd8010a17a2b3deba41447b6231
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645194"
---
# <a name="transform-data-with-transformations"></a><span data-ttu-id="5b5ff-102">変換を使用してデータを変換する</span><span class="sxs-lookup"><span data-stu-id="5b5ff-102">Transform Data with Transformations</span></span>
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="5b5ff-103">には、変換元、変換、および変換先という 3 種類のデータ フロー コンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-103">includes three types of data flow components: sources, transformations, and destinations.</span></span>  
  
 <span data-ttu-id="5b5ff-104">次の図は、1 つの変換元、2 つの変換、および 1 つの変換先を持つ、簡単なデータ フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-104">The following diagram shows a simple data flow that has a source, two transformations, and a destination.</span></span>  
  
 <span data-ttu-id="5b5ff-105">![データ フロー](../../media/mw-dts-08.gif "Data flow")</span><span class="sxs-lookup"><span data-stu-id="5b5ff-105">![Data flow](../../media/mw-dts-08.gif "Data flow")</span></span>  
  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="5b5ff-106">の変換では、次の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-106">transformations provide the following functionality:</span></span>  
  
-   <span data-ttu-id="5b5ff-107">行セットを分割、コピー、およびマージしたり、参照操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-107">Splitting, copying, and merging rowsets and performing lookup operations.</span></span>  
  
-   <span data-ttu-id="5b5ff-108">小文字を大文字に変更する変換などを適用することにより、列の値を更新して新しい列を作成します。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-108">Updating column values and creating new columns by applying transformations such as changing lowercase to uppercase.</span></span>  
  
-   <span data-ttu-id="5b5ff-109">データのクリーンアップ、テキストのマイニング、データ マイニング予測クエリの実行などのビジネス インテリジェンス操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-109">Performing business intelligence operations such as cleaning data, mining text, or running data mining prediction queries.</span></span>  
  
-   <span data-ttu-id="5b5ff-110">集計または並べ替えられた値、サンプル データ、またはピボットされたデータおよびピボット解除されたデータで構成される、新しい行セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-110">Creating new rowsets that consist of aggregate or sorted values, sample data, or pivoted and unpivoted data.</span></span>  
  
-   <span data-ttu-id="5b5ff-111">データのエクスポートおよびインポート、監査情報の提供、緩やかに変化するディメンションの処理などを行うタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-111">Performing tasks such as exporting and importing data, providing audit information, and working with slowly changing dimensions.</span></span>  
  
 <span data-ttu-id="5b5ff-112">詳しくは、「 [Integration Services の変換](integration-services-transformations.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-112">For more information, see [Integration Services Transformations](integration-services-transformations.md).</span></span>  
  
 <span data-ttu-id="5b5ff-113">カスタムの変換を記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-113">You can also write custom transformations.</span></span> <span data-ttu-id="5b5ff-114">詳しくは、「 [カスタム データ フロー コンポーネントの開発](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) 」と「 [特定の種類のデータ フロー コンポーネントの開発](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-114">For more information, see [Developing a Custom Data Flow Component](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) and [Developing Specific Types of Data Flow Components](../../extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md).</span></span>  
  
 <span data-ttu-id="5b5ff-115">変換をデータ フロー デザイナーに追加した後で、変換を構成する前に、データ フロー内の別の変換または変換元の出力をこの変換の入力に連結することにより、変換をデータ フローに連結します。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-115">After you add the transformation to the data flow designer, but before you configure the transformation, you connect the transformation to the data flow by connecting the output of another transformation or source in the data flow to the input of this transformation.</span></span> <span data-ttu-id="5b5ff-116">2 つのデータ フロー コンポーネント間のコネクタは、パスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-116">The connector between two data flow components is called a path.</span></span> <span data-ttu-id="5b5ff-117">コンポーネントの連結とパスを使用した作業の詳細については、「 [パスを使用してコンポーネントを連結する](../../connect-components-with-paths.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5b5ff-117">For more information about connecting components and working with paths, see [Connect Components with Paths](../../connect-components-with-paths.md).</span></span>  
  
### <a name="to-add-a-transformation-to-a-data-flow"></a><span data-ttu-id="5b5ff-118">変換をデータ フローに追加するには</span><span class="sxs-lookup"><span data-stu-id="5b5ff-118">To add a transformation to a data flow</span></span>  
  
-   [<span data-ttu-id="5b5ff-119">データ フローでコンポーネントを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="5b5ff-119">Add or Delete a Component in a Data Flow</span></span>](../add-or-delete-a-component-in-a-data-flow.md)  
  
### <a name="to-connect-a-transformation-to-a-data-flow"></a><span data-ttu-id="5b5ff-120">変換をデータ フローに連結するには</span><span class="sxs-lookup"><span data-stu-id="5b5ff-120">To connect a transformation to a data flow</span></span>  
  
-   [<span data-ttu-id="5b5ff-121">データ フロー内でコンポーネントを連結する</span><span class="sxs-lookup"><span data-stu-id="5b5ff-121">Connect Components in a Data Flow</span></span>](../connect-components-in-a-data-flow.md)  
  
### <a name="to-set-the-properties-of-a-transformation"></a><span data-ttu-id="5b5ff-122">変換のプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="5b5ff-122">To set the properties of a transformation</span></span>  
  
-   [<span data-ttu-id="5b5ff-123">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="5b5ff-123">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b5ff-124">参照</span><span class="sxs-lookup"><span data-stu-id="5b5ff-124">See Also</span></span>  
 <span data-ttu-id="5b5ff-125">[データ フロー タスク](../../control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="5b5ff-125">[Data Flow Task](../../control-flow/data-flow-task.md) </span></span>  
 <span data-ttu-id="5b5ff-126">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="5b5ff-126">[Data Flow](../data-flow.md) </span></span>  
 <span data-ttu-id="5b5ff-127">[パスを使用してコンポーネントを連結する](../../connect-components-with-paths.md) </span><span class="sxs-lookup"><span data-stu-id="5b5ff-127">[Connect Components with Paths](../../connect-components-with-paths.md) </span></span>  
 <span data-ttu-id="5b5ff-128">[データのエラー処理](../error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="5b5ff-128">[Error Handling in Data](../error-handling-in-data.md) </span></span>  
 [<span data-ttu-id="5b5ff-129">データ フロー</span><span class="sxs-lookup"><span data-stu-id="5b5ff-129">Data Flow</span></span>](../data-flow.md)  
  
  
