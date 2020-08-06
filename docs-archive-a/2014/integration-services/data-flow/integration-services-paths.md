---
title: Integration Services のパス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- paths [Integration Services], about paths
- data flow [Integration Services], paths
- paths [Integration Services]
- destinations [Integration Services], paths
- sources [Integration Services], paths
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c52bbd06974311a7fc94b3058309399d70df0034
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715634"
---
# <a name="integration-services-paths"></a><span data-ttu-id="c1987-102">Integration Services のパス</span><span class="sxs-lookup"><span data-stu-id="c1987-102">Integration Services Paths</span></span>
  <span data-ttu-id="c1987-103">パスは、データ フロー コンポーネントの出力を別のコンポーネントの入力に連結することにより、データ フロー内の 2 つのコンポーネントを連結します。</span><span class="sxs-lookup"><span data-stu-id="c1987-103">A path connects two components in a data flow by connecting the output of one data flow component to the input of another component.</span></span> <span data-ttu-id="c1987-104">パスには連結元と連結先があります。</span><span class="sxs-lookup"><span data-stu-id="c1987-104">A path has a source and a destination.</span></span> <span data-ttu-id="c1987-105">たとえば、パスが OLE DB ソースと並べ替え変換を連結する場合、OLE DB ソースはパスの連結元であり、並べ替え変換はパスの連結先になります。</span><span class="sxs-lookup"><span data-stu-id="c1987-105">For example, if a path connects an OLE DB source and a Sort transformation, the OLE DB source is the source of the path, and the Sort transformation is the destination of the path.</span></span> <span data-ttu-id="c1987-106">連結元とはパスが開始するコンポーネントで、連結先とはパスが終了するコンポーネントのことです。</span><span class="sxs-lookup"><span data-stu-id="c1987-106">The source is the component where the path starts, and the destination is the component where the path ends.</span></span>  
  
 <span data-ttu-id="c1987-107">パッケージを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで実行する場合、データ ビューアーをパスにアタッチすることにより、データ フロー内のデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="c1987-107">If you run a package in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you can view the data in a data flow by attaching data viewers to a path.</span></span> <span data-ttu-id="c1987-108">データ ビューアーを構成し、グリッドにデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="c1987-108">A data viewer can be configured to display data in a grid.</span></span> <span data-ttu-id="c1987-109">データ ビューアーは、デバッグ用のツールとして便利です。</span><span class="sxs-lookup"><span data-stu-id="c1987-109">A data viewer is a useful debugging tool.</span></span> <span data-ttu-id="c1987-110">詳細については、「 [データ フローのデバッグ](../troubleshooting/debugging-data-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1987-110">For more information, see [Debugging Data Flow](../troubleshooting/debugging-data-flow.md).</span></span>  
  
## <a name="configuration-of-the-path"></a><span data-ttu-id="c1987-111">パスの構成</span><span class="sxs-lookup"><span data-stu-id="c1987-111">Configuration of the Path</span></span>  
 <span data-ttu-id="c1987-112">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでは **[データ フロー パス エディター]** ダイアログ ボックスが用意され、これを使用すると、パスのプロパティの設定、パスに渡されるデータ列のメタデータの表示、およびデータ ビューアーの構成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c1987-112">The [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer provides the **Data Flow Path Editor** dialog box for setting path properties, viewing the metadata of the data columns that pass through the path, and configuring data viewers.</span></span>  
  
 <span data-ttu-id="c1987-113">構成可能なパスのプロパティは、パスの名前、説明、および注釈です。</span><span class="sxs-lookup"><span data-stu-id="c1987-113">The configurable path properties include the name, description, and annotation of the path.</span></span> <span data-ttu-id="c1987-114">パスはプログラムによって構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c1987-114">You can also configure paths programmatically.</span></span> <span data-ttu-id="c1987-115">詳細については、「 [プログラムによるデータ フロー コンポーネントの接続](../building-packages-programmatically/connecting-data-flow-components-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1987-115">For more information, see [Connecting Data Flow Components Programmatically](../building-packages-programmatically/connecting-data-flow-components-programmatically.md).</span></span>  
  
 <span data-ttu-id="c1987-116">パスの注釈を設定すると、 **デザイナーの** [データ フロー] [!INCLUDE[ssIS](../../includes/ssis-md.md)] タブにあるデザイン画面に、パスの連結元の名前またはパスの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1987-116">A path annotation displays the name of the path source or the path name on the design surface of the **Data Flow** tab in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="c1987-117">パスの注釈は、データ フロー、制御フロー、およびイベント ハンドラーに追加できる注釈と同様です。</span><span class="sxs-lookup"><span data-stu-id="c1987-117">Path annotations are similar to the annotations you can add to data flows, control flows, and event handlers.</span></span> <span data-ttu-id="c1987-118">唯一の違いは、パスの注釈はパスにアタッチされるのに対し、他の注釈は、 **デザイナーの**[データ フロー] **、** [制御フロー] **、および**[イベント ハンドラー] [!INCLUDE[ssIS](../../includes/ssis-md.md)] タブに表示される点です。</span><span class="sxs-lookup"><span data-stu-id="c1987-118">The only difference is that a path annotation is attached to a path, whereas other annotations appear on the **Data Flow**, **Control Flow**, and **Event Handle**r tabs of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="c1987-119">パスの注釈のメタデータは、各列の名前、データ型、有効桁数、小数点以下桁数、長さ、コード ページ、およびソース コンポーネントを、直前のコンポーネントの出力内で表示します。</span><span class="sxs-lookup"><span data-stu-id="c1987-119">The metadata shows the name, data type, precision, scale, length, code page, and source component of each column in the output of the previous component.</span></span> <span data-ttu-id="c1987-120">ソース コンポーネントとは、列を作成したデータ フロー コンポーネントのことです。</span><span class="sxs-lookup"><span data-stu-id="c1987-120">The source component is the data flow component that created the column.</span></span> <span data-ttu-id="c1987-121">このコンポーネントは、データ フロー内で最初のコンポーネントである場合もあれば、そうでない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c1987-121">This may or may not be the first component in the data flow.</span></span> <span data-ttu-id="c1987-122">たとえば、全体結合変換と並べ替え変換では独自の列が作成され、その列が出力列のソースになります。</span><span class="sxs-lookup"><span data-stu-id="c1987-122">For example, the Union All and Sort transformations create their own columns, and they are the sources of their output columns.</span></span> <span data-ttu-id="c1987-123">対照的に、列コピー変換では、列を変更しないまま渡したり、入力列をコピーして新しい列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="c1987-123">In contrast, a Copy Column transformation can pass through columns without changing them or can create new columns by copying input columns.</span></span> <span data-ttu-id="c1987-124">列コピー変換は、新しい列に対してのみ変換元コンポーネントとなります。</span><span class="sxs-lookup"><span data-stu-id="c1987-124">The Copy Column transformation is the source component only of the new columns.</span></span>  
  
 <span data-ttu-id="c1987-125">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="c1987-125">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="c1987-126">**[データ フロー パス エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1987-126">For more information about the properties that you can set in the **Data Flow Path Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="c1987-127">[データフローパスエディター &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="c1987-127">[Data Flow Path Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   [<span data-ttu-id="c1987-128">データフローパスエディター &#40;メタデータページ&#41;</span><span class="sxs-lookup"><span data-stu-id="c1987-128">Data Flow Path Editor &#40;Metadata Page&#41;</span></span>](../data-flow-path-editor-metadata-page.md)  
  
-   <span data-ttu-id="c1987-129">[データフローパスエディターの [データビューアー] ページ &#40;&#41;](../data-flow-path-editor-data-viewers-page.md)</span><span class="sxs-lookup"><span data-stu-id="c1987-129">[Data Flow Path Editor &#40;Data Viewers Page&#41;](../data-flow-path-editor-data-viewers-page.md)</span></span>  
  
 <span data-ttu-id="c1987-130">プログラムによって設定できるプロパティの詳細については、「[パスのプロパティ](../path-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1987-130">For more information about the properties that you can set programmatically, see [Path Properties](../path-properties.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c1987-131">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c1987-131">Related Tasks</span></span>  
  
-   [<span data-ttu-id="c1987-132">データ フロー パス エディターでパスのメタデータを表示する</span><span class="sxs-lookup"><span data-stu-id="c1987-132">View Path Metadata in the Data Flow Path Editor</span></span>](../view-path-metadata-in-the-data-flow-path-editor.md)  
  
-   [<span data-ttu-id="c1987-133">データ フロー内でコンポーネントを連結する</span><span class="sxs-lookup"><span data-stu-id="c1987-133">Connect Components in a Data Flow</span></span>](connect-components-in-a-data-flow.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1987-134">参照</span><span class="sxs-lookup"><span data-stu-id="c1987-134">See Also</span></span>  
 [<span data-ttu-id="c1987-135">データ フロー</span><span class="sxs-lookup"><span data-stu-id="c1987-135">Data Flow</span></span>](data-flow.md)  
  
  
