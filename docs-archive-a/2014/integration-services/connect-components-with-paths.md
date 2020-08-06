---
title: パスを使用してコンポーネントを連結する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e11955601406406abe48b53197e95c8224762fee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738622"
---
# <a name="connect-components-with-paths"></a><span data-ttu-id="b3214-102">パスを使用してコンポーネントを連結する</span><span class="sxs-lookup"><span data-stu-id="b3214-102">Connect Components with Paths</span></span>
  <span data-ttu-id="b3214-103">パッケージ内にデータ フローを構築するには、 **デザイナーにある** [データ フロー] [!INCLUDE[ssIS](../includes/ssis-md.md)] タブのデザイン画面を使用します。</span><span class="sxs-lookup"><span data-stu-id="b3214-103">You construct the data flow in a package on the design surface of the **Data Flow** tab in the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="b3214-104">データ フローにデータ フロー コンポーネントが 2 つ含まれる場合、変換元または変換からの出力を変換または変換先への入力に連結することで、これらのコンポーネントを連結できます。</span><span class="sxs-lookup"><span data-stu-id="b3214-104">If a data flow contains two data flow components, you can connect them by connecting the output of a source or transformation to the input of a transformation or destination.</span></span> <span data-ttu-id="b3214-105">2 つのデータ フロー コンポーネント間のコネクタは、パスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b3214-105">The connector between two data flow components is called a path.</span></span>

 <span data-ttu-id="b3214-106">次の図は、1 つの変換元コンポーネント、2 つの変換、1 つの変換先コンポーネント、およびこれらを連結するパスを持つ、簡単なデータ フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="b3214-106">The following diagram shows a simple data flow with a source component, two transformations, a destination component, and the paths that connect them.</span></span>

 <span data-ttu-id="b3214-107">![データフロー](media/mw-dts-08.gif "データ フロー")</span><span class="sxs-lookup"><span data-stu-id="b3214-107">![Data flow](media/mw-dts-08.gif "Data flow")</span></span>

 <span data-ttu-id="b3214-108">2 つのコンポーネントを連結したら、パスを移動するデータのメタデータおよびパスのプロパティを、 **[データ フロー パス エディター]** で表示できます。</span><span class="sxs-lookup"><span data-stu-id="b3214-108">After two components are connected, you can view the metadata of the data that moves through the path and the properties of the path in **Data Flow Path Editor**.</span></span> <span data-ttu-id="b3214-109">詳細については、「 [Integration Services のパス](data-flow/integration-services-paths.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3214-109">For more information, see [Integration Services Paths](data-flow/integration-services-paths.md).</span></span>

 <span data-ttu-id="b3214-110">また、データ ビューアーをパスに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="b3214-110">You can also add data viewers to paths.</span></span> <span data-ttu-id="b3214-111">データ ビューアーを使用すると、パッケージの実行時にデータ フロー コンポーネント間を移動するデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b3214-111">A data viewer makes it possible to view data moving between data flow components when the package is run.</span></span>

### <a name="to-connect-components-in-a-data-flow"></a><span data-ttu-id="b3214-112">データ フロー内でコンポーネントを連結するには</span><span class="sxs-lookup"><span data-stu-id="b3214-112">To connect components in a data flow</span></span>

-   [<span data-ttu-id="b3214-113">データ フロー内でコンポーネントを連結する</span><span class="sxs-lookup"><span data-stu-id="b3214-113">Connect Components in a Data Flow</span></span>](data-flow/connect-components-in-a-data-flow.md)

### <a name="to-set-path-properties"></a><span data-ttu-id="b3214-114">パスのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="b3214-114">To set path properties</span></span>

-   [<span data-ttu-id="b3214-115">データ フロー パス エディターを使用してパスのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="b3214-115">Set the Properties of a Path by Using the Data Flow Path Editor</span></span>](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a><span data-ttu-id="b3214-116">パスのメタデータを表示するには</span><span class="sxs-lookup"><span data-stu-id="b3214-116">To view path metadata</span></span>

-   [<span data-ttu-id="b3214-117">データ フロー パス エディターでパスのメタデータを表示する</span><span class="sxs-lookup"><span data-stu-id="b3214-117">View Path Metadata in the Data Flow Path Editor</span></span>](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a><span data-ttu-id="b3214-118">パスのメタデータを表示するには</span><span class="sxs-lookup"><span data-stu-id="b3214-118">To view path metadata</span></span>

-   [<span data-ttu-id="b3214-119">データ フローにデータ ビューアーを追加する</span><span class="sxs-lookup"><span data-stu-id="b3214-119">Add a Data Viewer to a Data Flow</span></span>](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)

## <a name="see-also"></a><span data-ttu-id="b3214-120">参照</span><span class="sxs-lookup"><span data-stu-id="b3214-120">See Also</span></span>
 <span data-ttu-id="b3214-121">[データフロータスク](control-flow/data-flow-task.md)の[データフロー](data-flow/data-flow.md)変換[を使用したデータの変換](data-flow/transformations/transform-data-with-transformations.md)データ[でのエラー処理](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="b3214-121">[Data Flow Task](control-flow/data-flow-task.md) [Data Flow](data-flow/data-flow.md) [Transform Data with Transformations](data-flow/transformations/transform-data-with-transformations.md) [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>


