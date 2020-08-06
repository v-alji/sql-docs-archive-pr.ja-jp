---
title: '手順 8: レッスン 1 のパッケージをわかりやすくする作業 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 67fb8e2adb9062b5b777acc14df0ddc5b45884ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641087"
---
# <a name="step-8-making-the-lesson-1-package-easier-to-understand"></a><span data-ttu-id="fcacc-102">手順 8:レッスン 1 のパッケージをわかりやすくする作業</span><span class="sxs-lookup"><span data-stu-id="fcacc-102">Step 8: Making the Lesson 1 Package Easier to Understand</span></span>
  <span data-ttu-id="fcacc-103">ここまでの作業で、レッスン 1 のパッケージの構成が完了しました。次は、パッケージのレイアウトを整理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fcacc-103">Now that you have completed the configuration of the Lesson 1 package, it is a good idea to tidy up the package layout.</span></span> <span data-ttu-id="fcacc-104">制御フローやデータ フローのレイアウトの図形サイズがまちまちであったり、図形の整列やグループ化が行われていないと、パッケージの機能がわかりにくくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="fcacc-104">If the shapes in the control and data flow layouts are random sizes, or if the shapes are not aligned or grouped, the functionality of package can be more difficult to understand.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="fcacc-105">Data Tools には、パッケージのレイアウトをすばやく簡単に書式設定できるツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="fcacc-105">Data Tools provides tools that make it easy and quick to format the package layout.</span></span> <span data-ttu-id="fcacc-106">この書式設定機能を使用すると、複数の図形を同じサイズにしたり、整列したり、図形間の上下左右の間隔を操作することができます。</span><span class="sxs-lookup"><span data-stu-id="fcacc-106">The formatting features include the ability to make shapes the same size, align shapes, and manipulate the horizontal and vertical spacing between shapes.</span></span>  
  
 <span data-ttu-id="fcacc-107">パッケージの機能をわかりやすくするには、パッケージ機能について説明した注釈を追加するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="fcacc-107">Another way to improve the understanding of package functionality is to add annotations that describe package functionality.</span></span>  
  
 <span data-ttu-id="fcacc-108">この実習では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools の書式設定機能を使用してデータ フローのレイアウトを改善し、さらにデータ フローに注釈を追加します。</span><span class="sxs-lookup"><span data-stu-id="fcacc-108">In this task, you will use the formatting features in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools to improve the layout of the data flow and also add an annotation to the data flow.</span></span>  
  
### <a name="to-format-the-layout-of-the-data-flow"></a><span data-ttu-id="fcacc-109">データ フローのレイアウトを書式設定するには</span><span class="sxs-lookup"><span data-stu-id="fcacc-109">To format the layout of the data flow</span></span>  
  
1.  <span data-ttu-id="fcacc-110">レッスン 1 のパッケージを開いていない場合は、ソリューション エクスプローラーで Lesson 1.dtsx をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcacc-110">If the Lesson 1 package is not already open, double-click Lesson 1.dtsx in Solution Explorer.</span></span>  
  
2.  <span data-ttu-id="fcacc-111">**[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcacc-111">Click the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="fcacc-112">Extract Sample Currency 変換の右上隅にカーソルを合わせ、クリックしてすべてのデータ フロー コンポーネントを囲むようにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="fcacc-112">Place the cursor to the top and to the right of the Extract Sample Currency transformation, click, and then drag the cursor across all the data flow components.</span></span>  
  
4.  <span data-ttu-id="fcacc-113">**[書式]** メニューの **[同じサイズに揃える]** をポイントし、 **[両方]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcacc-113">On the **Format** menu, point to **Make Same Size**, and then click **Both**.</span></span>  
  
5.  <span data-ttu-id="fcacc-114">データ フロー オブジェクトが選択されている状態で、 **[書式]** メニューの **[整列]** をポイントし、 **[左]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcacc-114">With the data flow objects selected, on the **Format** menu, point to **Align**, and then click **Lefts**.</span></span>  
  
### <a name="to-add-an-annotation-to-the-data-flow"></a><span data-ttu-id="fcacc-115">データ フローに注釈を追加するには</span><span class="sxs-lookup"><span data-stu-id="fcacc-115">To add an annotation to the data flow</span></span>  
  
1.  <span data-ttu-id="fcacc-116">データ フローのデザイン画面の背景で任意の場所を右クリックし、 **[注釈の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcacc-116">Right-click anywhere in the background of the data flow design surface and then click **Add Annotation**.</span></span>  
  
2.  <span data-ttu-id="fcacc-117">注釈ボックスに、次のテキストを入力するか、コピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="fcacc-117">Type or paste the following text in the annotation box.</span></span>  
  
     <span data-ttu-id="fcacc-118">**このデータ フローは、ファイルからデータを抽出し、DimCurrency テーブルの CurrencyKey 列の値と DimDate テーブルの DateKey 列の値を参照して、データを NewFactCurrencyRate テーブルに書き込みます。**</span><span class="sxs-lookup"><span data-stu-id="fcacc-118">**The data flow extracts data from a file, looks up values in the CurrencyKey column in the DimCurrency table and the DateKey column in the DimDate table, and writes the data to the NewFactCurrencyRate table.**</span></span>  
  
     <span data-ttu-id="fcacc-119">注釈ボックスのテキストを折り返すには、改行する場所にカーソルを置いて、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fcacc-119">To wrap the text in the annotation box, place the cursor where you want to start a new line and press the Enter key.</span></span>  
  
     <span data-ttu-id="fcacc-120">注釈ボックスにテキストを追加しない場合は、注釈ボックスの外側をクリックするとボックスは表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="fcacc-120">If you do not add text to the annotation box, it disappears when you click outside the box.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fcacc-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="fcacc-121">Next Steps</span></span>  
 [<span data-ttu-id="fcacc-122">手順 9:レッスン 1 のチュートリアル パッケージのテスト</span><span class="sxs-lookup"><span data-stu-id="fcacc-122">Step 9: Testing the Lesson 1 Tutorial Package</span></span>](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
