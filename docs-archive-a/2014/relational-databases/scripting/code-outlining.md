---
title: コードのアウトライン表示
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], outlining code
- Query Editor [SQL Server Management Studio], hiding code
ms.assetid: 556c7dfe-7bc8-4cab-a36f-2b753a05d3f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 0a142ca8fbdcdfcfbfd1b71de06c0b0fd4c5339c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634914"
---
# <a name="code-outlining"></a><span data-ttu-id="5c9a4-102">コードのアウトライン表示</span><span class="sxs-lookup"><span data-stu-id="5c9a4-102">Code Outlining</span></span>
  <span data-ttu-id="5c9a4-103">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のクエリ エディターのアウトライン機能を使用して、クエリの編集時にコードを選択して非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-103">You can use the outlining feature in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] query editors to selectively hide code when you edit queries.</span></span> <span data-ttu-id="5c9a4-104">これにより、特に大きなクエリ ファイルでは、作業中のコードを見やすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-104">This enables you to more easily view the code you are working on, especially in large query files.</span></span>

## <a name="outlining-overview"></a><span data-ttu-id="5c9a4-105">アウトラインの概要</span><span class="sxs-lookup"><span data-stu-id="5c9a4-105">Outlining Overview</span></span>
 <span data-ttu-id="5c9a4-106">既定では、クエリ エディター ウィンドウを開くとすべてのコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-106">By default, all code is visible when you open a query editor window.</span></span> <span data-ttu-id="5c9a4-107">コード領域は折りたたんで非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-107">Regions of the code can be collapsed to hide it from view.</span></span> <span data-ttu-id="5c9a4-108">エディター ウィンドウの左端にある垂直線では負符号 (-) の付いた正方形を使用して、折りたたむことができるコード領域の先頭をそれぞれ識別します。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-108">A vertical line on the left edge of the editor window uses a square with a minus sign (-) to identify the start of each collapsible code region.</span></span> <span data-ttu-id="5c9a4-109">負符号をクリックすると、コード領域のテキストが 3 つのピリオド (...) の付いたボックスに置き換わり、負符号が正符号 (+) に変わります。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-109">When you click a minus sign, the text of the code region is replaced with a box that contains three periods (...), and the minus sign changes to a plus sign (+).</span></span> <span data-ttu-id="5c9a4-110">正符号をクリックすると、折りたたまれていたコードが表示され、正符号が負符号に変わります。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-110">When you click a plus sign, the collapsed code appears and the plus sign changes to a minus sign.</span></span> <span data-ttu-id="5c9a4-111">ポインターを 3 つのピリオドの付いたボックス上に移動すると、折りたたまれているセクションのコードを示すツールヒントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-111">When you move the pointer over a box that has three periods, a tooltip appears that shows the code in the collapsed section.</span></span>

## <a name="system-outline-regions"></a><span data-ttu-id="5c9a4-112">システムのアウトライン領域</span><span class="sxs-lookup"><span data-stu-id="5c9a4-112">System Outline Regions</span></span>
 <span data-ttu-id="5c9a4-113">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の各エディターでは、システム定義のアウトライン領域の既定のセットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-113">Each [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] editor generates a set of default, system-defined outline regions.</span></span>

 <span data-ttu-id="5c9a4-114">MDX と DMX のコード エディターでは、複数行にわたるステートメントごとにアウトライン領域が作成されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-114">The MDX and DMX code editors create outline regions for each multiline statement.</span></span> <span data-ttu-id="5c9a4-115">これは、このようなエディターがサポートする唯一のアウトライン レベルです。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-115">This is the only level of outlining that these editors support.</span></span>

### <a name="analysis-services-xmla-query-editor-regions"></a><span data-ttu-id="5c9a4-116">Analysis Services の XMLA クエリ エディターの領域</span><span class="sxs-lookup"><span data-stu-id="5c9a4-116">Analysis Services XMLA Query Editor Regions</span></span>
 <span data-ttu-id="5c9a4-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の XMLA クエリ エディターでは、複数行にわたる XML 属性ごとにアウトライン領域が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-117">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] XMLA Query Editor generates an outline region for each multiline XML attribute.</span></span> <span data-ttu-id="5c9a4-118">エディターは、入れ子になったタグのアウトライン領域は入れ子にします。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-118">The editor nests the outline regions for nested tags.</span></span> <span data-ttu-id="5c9a4-119">たとえば、XMLA エディターでは次のドキュメントに対して 3 つのアウトライン領域を作成します。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-119">For example, the XMLA Editor creates three outline regions for the following document.</span></span>

 <span data-ttu-id="5c9a4-120">![アウトラインを示す XML コード](../../database-engine/media/editoutlinexmlfull.gif "アウトラインを示す XML コード")</span><span class="sxs-lookup"><span data-stu-id="5c9a4-120">![XML code showing outlining](../../database-engine/media/editoutlinexmlfull.gif "XML code showing outlining")</span></span>

 <span data-ttu-id="5c9a4-121">行の負符号をクリックすると、 \<InnerTag> 次の図に示すように、InnerTag だけが折りたたまれます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-121">When you click the minus sign on the \<InnerTag> line, just the InnerTag is collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="5c9a4-122">![内部ノードが非表示になっている XML コード](../../database-engine/media/editoutlinexmlinnercol.gif "内部ノードが非表示になっている XML コード")</span><span class="sxs-lookup"><span data-stu-id="5c9a4-122">![XML code with inner node hidden](../../database-engine/media/editoutlinexmlinnercol.gif "XML code with inner node hidden")</span></span>

 <span data-ttu-id="5c9a4-123">ポインターを 3 つのピリオド (...) の付いたボックス上に移動すると、次の図に示すように、折りたたまれた領域のコードがツールヒントに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-123">When you move the pointer over the box that has the three periods (...), the code in the collapsed region appears in a tooltip, as shown in the following illustration.</span></span>

 <span data-ttu-id="5c9a4-124">![非表示コードを示すツールヒント付きの XML コード](../../database-engine/media/editoutlinexmlmouse.gif "非表示コードを示すツールヒント付きの XML コード")</span><span class="sxs-lookup"><span data-stu-id="5c9a4-124">![XML code with tooltip showing hidden code](../../database-engine/media/editoutlinexmlmouse.gif "XML code with tooltip showing hidden code")</span></span>

 <span data-ttu-id="5c9a4-125">行の負符号をクリックすると、 \<MiddleTag> 次の図に示すように、MiddleTag と InnerTag の両方が折りたたまれます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-125">When you click the minus sign on the \<MiddleTag> line, both the MiddleTag and InnerTag are collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="5c9a4-126">![内部および中間タグが非表示になっている XML コード](../../database-engine/media/editoutlinexmlmiddlecol.gif "内部および中間タグが非表示になっている XML コード")</span><span class="sxs-lookup"><span data-stu-id="5c9a4-126">![XML code with inner and middle tags hidden](../../database-engine/media/editoutlinexmlmiddlecol.gif "XML code with inner and middle tags hidden")</span></span>

 <span data-ttu-id="5c9a4-127">行の負符号をクリックすると、 \<OuterTag> 次の図に示すように、3行すべてが折りたたまれます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-127">When you click the minus sign on the \<OuterTag> line, all three lines are collapsed, as shown in the following illustration.</span></span>

 <span data-ttu-id="5c9a4-128">![3 つのすべての非表示タグを示す XML コード](../../database-engine/media/editoutlinexmloutercol.gif "3 つのすべての非表示タグを示す XML コード")</span><span class="sxs-lookup"><span data-stu-id="5c9a4-128">![XML code showing all three tags hidden](../../database-engine/media/editoutlinexmloutercol.gif "XML code showing all three tags hidden")</span></span>

### <a name="database-engine-query-editor-regions"></a><span data-ttu-id="5c9a4-129">データベース エンジンのクエリ エディターの領域</span><span class="sxs-lookup"><span data-stu-id="5c9a4-129">Database Engine Query Editor Regions</span></span>
 <span data-ttu-id="5c9a4-130">[!INCLUDE[ssDE](../../../includes/ssde-md.md)] のクエリ エディターでは、次の階層で要素ごとにアウトライン領域が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-130">The [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Query Editor generates outline regions for each element in the following hierarchy:</span></span>

1.  <span data-ttu-id="5c9a4-131">バッチ。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-131">Batches.</span></span> <span data-ttu-id="5c9a4-132">最初のバッチは、ファイルの先頭から最初の GO コマンドまでのコードか、GO コマンドがなければファイルの末尾までのコードです。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-132">The first batch is the code from the start of the file to either the first GO command or the end of the file when there are no GO commands.</span></span> <span data-ttu-id="5c9a4-133">最初の GO の後は、各 GO コマンドから次の GO コマンドまで、またはファイルの末尾までが 1 つのバッチです。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-133">After the first GO, there is one batch from each GO command to either the next GO command or the end of the file.</span></span>

2.  <span data-ttu-id="5c9a4-134">次のキーワードで区切られるブロック。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-134">Blocks delimited by the following keywords:</span></span>

    -   <span data-ttu-id="5c9a4-135">BEGIN - END</span><span class="sxs-lookup"><span data-stu-id="5c9a4-135">BEGIN - END</span></span>

    -   <span data-ttu-id="5c9a4-136">BEGIN TRY - END TRY</span><span class="sxs-lookup"><span data-stu-id="5c9a4-136">BEGIN TRY - END TRY</span></span>

    -   <span data-ttu-id="5c9a4-137">BEGIN CATCH - END CATCH</span><span class="sxs-lookup"><span data-stu-id="5c9a4-137">BEGIN CATCH - END CATCH</span></span>

3.  <span data-ttu-id="5c9a4-138">複数行にわたるステートメント。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-138">Multiline statements.</span></span>

 <span data-ttu-id="5c9a4-139">たとえば、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] のクエリ エディターでは、次のクエリに対して 3 つのアウトライン領域が作成されます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-139">For example, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] Query Editor creates three outline regions for the following query:</span></span>

```
CREATE PROCEDURE Sales.SampleProc --Outline region 1
AS
BEGIN --Outline region 2 
  SELECT GETDATE() AS TimeOfQuery;
  SELECT * --Outline region 3
  FROM sys.transmission_queue;
  SELECT @@VERSION;
END;
GO
```

 <span data-ttu-id="5c9a4-140">`SELECT *` 行の負符号をクリックして、その `SELECT` ステートメントのみを折りたたむことができます。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-140">You can click the minus sign on the `SELECT *` line to collapse just that `SELECT` statement.</span></span> <span data-ttu-id="5c9a4-141">`BEGIN - END` ブロック全体を折りたたむには、 `BEGIN` 行の負符号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-141">To collapse the whole `BEGIN - END` block, click the minus sign on the `BEGIN` line.</span></span> <span data-ttu-id="5c9a4-142">`GO` コマンドまでのバッチ全体を折りたたむには、 `CREATE PROCEDURE` 行の負符号をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-142">To collapse the whole batch to the `GO` command, click the minus sign on the `CREATE PROCEDURE` line.</span></span> <span data-ttu-id="5c9a4-143">`SELECT GETDATE()` 行または `SELECT @@VERSION` 行は、単一行のステートメントでアウトライン領域にはならないため、個別に折りたたむことはできません。</span><span class="sxs-lookup"><span data-stu-id="5c9a4-143">You cannot collapse the `SELECT GETDATE()` or `SELECT @@VERSION` lines individually because they are single line statements and do not get outlining regions.</span></span>


