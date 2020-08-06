---
title: 計算されるメンバーを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculated members [Analysis Services]
- custom measures [Analysis Services]
- members [Analysis Services], calculated
- calculations [Analysis Services], calculated members
ms.assetid: 820e4b18-9c3a-4b12-a126-ca16d8364a00
author: minewiskan
ms.author: owend
ms.openlocfilehash: c45ef3cf720e6a3cc43156b032d91d205d6334bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632154"
---
# <a name="create-calculated-members"></a><span data-ttu-id="3d055-102">計算されるメンバーの作成</span><span class="sxs-lookup"><span data-stu-id="3d055-102">Create Calculated Members</span></span>
  <span data-ttu-id="3d055-103">キューブ データ、算術演算子、数値、関数などを組み合わせることによって、「計算されるメンバー」と呼ばれる、カスタマイズされたメジャーまたはディメンション メンバーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3d055-103">You can create customized measures or dimension members, called calculated members, by combining cube data, arithmetic operators, numbers, and functions.</span></span> <span data-ttu-id="3d055-104">たとえば、既存のドル メジャーに換算率を掛けて、ドルをユーロに換算する、Euro という計算されるメンバーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3d055-104">For example, you can create a calculated member named Euros that converts dollars to euros by multiplying an existing dollar measure by a conversion rate.</span></span> <span data-ttu-id="3d055-105">Euro は、別個の行または列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-105">Euros can then be displayed to end users in a separate row or column.</span></span>  
  
 <span data-ttu-id="3d055-106">計算されるメンバーの定義は格納されますが、その値はメモリにしか存在しません。</span><span class="sxs-lookup"><span data-stu-id="3d055-106">Calculated member definitions are stored, but their values exist only in memory.</span></span> <span data-ttu-id="3d055-107">上記の例では、Euro の値はエンド ユーザーに表示されますが、キューブ データとしては格納されません。</span><span class="sxs-lookup"><span data-stu-id="3d055-107">In the preceding example, values in marks are displayed to end users but are not stored as cube data.</span></span>  
  
 <span data-ttu-id="3d055-108">計算されるメンバーはキューブで作成します。</span><span class="sxs-lookup"><span data-stu-id="3d055-108">You create calculated members in cubes.</span></span> <span data-ttu-id="3d055-109">計算されるメンバーを作成するには、キューブ デザイナーの **[計算]** タブで、ツール バーの **[新しい計算されるメンバー]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d055-109">To create a calculated member, in Cube Designer, on the **Calculations** tab, click the **New Calculated Member** icon on the toolbar.</span></span> <span data-ttu-id="3d055-110">このコマンドでは、計算されるメンバーの次のオプションを指定するためのフォームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-110">This command displays a form to specify the following options for the calculated member:</span></span>  
  
 <span data-ttu-id="3d055-111">**名前**</span><span class="sxs-lookup"><span data-stu-id="3d055-111">**Name**</span></span>  
 <span data-ttu-id="3d055-112">計算されるメンバーの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="3d055-112">Select the name of the calculated member.</span></span> <span data-ttu-id="3d055-113">キューブを参照すると、この名前は、計算されるメンバーの値の列または行のヘッダーとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-113">This name appears as the column or row heading for the calculated member values when end users browse the cube.</span></span>  
  
 <span data-ttu-id="3d055-114">**親階層**</span><span class="sxs-lookup"><span data-stu-id="3d055-114">**Parent hierarchy**</span></span>  
 <span data-ttu-id="3d055-115">計算されるメンバーに含める親階層を選択します。</span><span class="sxs-lookup"><span data-stu-id="3d055-115">Select the parent hierarchy to include in the calculated member.</span></span> <span data-ttu-id="3d055-116">階層は、キューブ内の数値データ (メジャー) を分析目的で分割する基準となる、ディメンションの記述カテゴリです。</span><span class="sxs-lookup"><span data-stu-id="3d055-116">Hierarchies are descriptive categories of a dimension by which the numeric data (that is, measures) in a cube can be separated for analysis.</span></span> <span data-ttu-id="3d055-117">表形式のブラウザーでは、エンド ユーザーがキューブ内のデータを参照すると、階層に列ヘッダーと行ヘッダーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-117">In tabular browsers, hierarchies provide the column and row headings displayed to end users when they browse data in a cube.</span></span> <span data-ttu-id="3d055-118">グラフィカルなブラウザーでは、別の種類の説明ラベルが表示されますが、機能は表形式のブラウザーの場合と同じです。計算されるメンバーでは、選択した親ディメンション内に新しいヘッダー (ラベル) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-118">(In graphical browsers, they provide other types of descriptive labels, but they have the same function as in tabular browsers.) A calculated member provides a new heading (or label) in the parent dimension you select.</span></span>  
  
 <span data-ttu-id="3d055-119">また、計算されるメンバーを、ディメンションではなくメジャーに含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="3d055-119">Alternatively, you can include the calculated member in the measures instead of in a dimension.</span></span> <span data-ttu-id="3d055-120">この場合も、新しい列ヘッダーまたは行ヘッダーが表示されますが、ブラウザーではメジャーに付加されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-120">This option also provides a new column or row heading, but it is attached to measures in the browser.</span></span>  
  
 <span data-ttu-id="3d055-121">**[親メンバー]**</span><span class="sxs-lookup"><span data-stu-id="3d055-121">**Parent member**</span></span>  
 <span data-ttu-id="3d055-122">計算されるメンバーを含める親メンバーを選択するには、 **[変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d055-122">Click **Change** to select a parent member to include the calculated member.</span></span> <span data-ttu-id="3d055-123">親ディメンションとして 1 レベルの階層または MEASURES を選択した場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="3d055-123">This option is unavailable if you select a one-level hierarchy or MEASURES as the parent dimension.</span></span>  
  
 <span data-ttu-id="3d055-124">階層はレベルに分割され、そこにメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3d055-124">Hierarchies are divided into levels that contain members.</span></span> <span data-ttu-id="3d055-125">各メンバーによってヘッダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-125">Each member produces a heading.</span></span> <span data-ttu-id="3d055-126">キューブ内のデータを参照中、選択したヘッダーから、これまで表示されていなかった下位のヘッダーにドリル ダウンできます。</span><span class="sxs-lookup"><span data-stu-id="3d055-126">While browsing data in a cube, end users can drill down from a selected heading to previously undisplayed subordinate headings.</span></span> <span data-ttu-id="3d055-127">計算されるメンバーのヘッダーは、選択した親メンバーの直下に属するレベルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-127">The heading for the calculated member is added at the level directly below the parent member you select.</span></span>  
  
 <span data-ttu-id="3d055-128">**[式]**</span><span class="sxs-lookup"><span data-stu-id="3d055-128">**Expression**</span></span>  
 <span data-ttu-id="3d055-129">計算されるメンバーの値を作成する式を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d055-129">Specify the expression that produces the values of the calculated member.</span></span> <span data-ttu-id="3d055-130">この式は、多次元式 (MDX) で記述できます。</span><span class="sxs-lookup"><span data-stu-id="3d055-130">This expression can be written in Multidimensional Expressions (MDX).</span></span> <span data-ttu-id="3d055-131">式には、次の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3d055-131">The expression can contain any of the following:</span></span>  
  
-   <span data-ttu-id="3d055-132">ディメンション、レベル、メジャーなどのキューブのコンポーネントを表すデータ式</span><span class="sxs-lookup"><span data-stu-id="3d055-132">Data expressions that represent cube components such as dimensions, levels, measures, and so on</span></span>  
  
-   <span data-ttu-id="3d055-133">算術演算子</span><span class="sxs-lookup"><span data-stu-id="3d055-133">Arithmetic operators</span></span>  
  
-   <span data-ttu-id="3d055-134">数値</span><span class="sxs-lookup"><span data-stu-id="3d055-134">Numbers</span></span>  
  
-   <span data-ttu-id="3d055-135">関数</span><span class="sxs-lookup"><span data-stu-id="3d055-135">Functions</span></span>  
  
 <span data-ttu-id="3d055-136">**[計算ツール]** ペインの **[メタデータ]** タブからキューブのコンポーネントをドラッグまたはコピーして、簡単に式に追加できます。</span><span class="sxs-lookup"><span data-stu-id="3d055-136">You can drag or copy cube components from the **Metadata** tab of the **Calculation Tools** pane to quickly add them to an expression.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3d055-137">計算されるメンバーが、別の計算されるメンバーの値式で使用される場合は、先に作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d055-137">Any calculated member that is to be used in the value expression of another calculated member must be created before the calculated member that uses it.</span></span>  
  
 <span data-ttu-id="3d055-138">書式設定文字列</span><span class="sxs-lookup"><span data-stu-id="3d055-138">Format String</span></span>  
 <span data-ttu-id="3d055-139">計算されるメンバーに基づいたセル値の書式を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d055-139">Specifies the format of cell values that are based on the calculated member.</span></span> <span data-ttu-id="3d055-140">このプロパティは、メジャーの `Display Format` プロパティと同じ値を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d055-140">This property accepts the same values as the `Display Format` property for measures.</span></span> <span data-ttu-id="3d055-141">表示形式の詳細については、「 [メジャーのプロパティの構成](configure-measure-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d055-141">For more information about display formats, see [Configure Measure Properties](configure-measure-properties.md).</span></span>  
  
 <span data-ttu-id="3d055-142">Visible</span><span class="sxs-lookup"><span data-stu-id="3d055-142">Visible</span></span>  
 <span data-ttu-id="3d055-143">計算されるメンバーをキューブ メタデータの取得時に表示するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3d055-143">Determines whether the calculated member is visible or hidden when cube metadata is retrieved.</span></span> <span data-ttu-id="3d055-144">計算されるメンバーを表示しない場合でも、そのメンバーを MDX 式、ステートメント、およびスクリプトで使用できますが、クライアント ユーザー インターフェイスでは選択可能なオブジェクトとしては表示されません。</span><span class="sxs-lookup"><span data-stu-id="3d055-144">If the calculated member is hidden, it can still be used in MDX expressions, statements, and scripts, but it is not displayed as a selectable object in client user interfaces.</span></span>  
  
 <span data-ttu-id="3d055-145">空以外の動作</span><span class="sxs-lookup"><span data-stu-id="3d055-145">Non-empty Behavior</span></span>  
 <span data-ttu-id="3d055-146">MDX の NON EMPTY クエリの解決に使用するメジャー名を格納します。</span><span class="sxs-lookup"><span data-stu-id="3d055-146">Stores the names of measures used to resolve NON EMPTY queries in MDX.</span></span> <span data-ttu-id="3d055-147">このプロパティが空白の場合、メンバーが空であるかどうかを判断するために、計算されるメンバーを繰り返し評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d055-147">If this property is blank, the calculated member must be evaluated repeatedly to determine whether a member is empty.</span></span> <span data-ttu-id="3d055-148">このプロパティに 1 つまたは複数のメジャーの名前が格納されている場合、指定されたすべてのメジャーが空であれば、計算されるメンバーも空として処理されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-148">If this property contains the name of one or more measures, the calculated member is treated as empty if all the specified measures are empty.</span></span> <span data-ttu-id="3d055-149">このプロパティは、Null 値以外のレコードだけを返す最適化ヒントとして Analysis Services に渡されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-149">This property is an optimization hint to Analysis Services to return only non-NULL records.</span></span> <span data-ttu-id="3d055-150">Null 値以外のレコードだけが返されるので、NON EMPTY 演算子や NonEmpty 関数を利用する MDX クエリや、セル値の計算を必要とする MDX クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="3d055-150">Returning only non-NULL records improves the performance of MDX queries that utilize the NON EMPTY operator or the NonEmpty function, or that require the calculation of cell values.</span></span> <span data-ttu-id="3d055-151">セルの計算で最良のパフォーマンスを得るには、できるだけ 1 つのメンバーのみを指定してください。</span><span class="sxs-lookup"><span data-stu-id="3d055-151">For best performance with cell calculations, specify only a single member when possible.</span></span>  
  
 <span data-ttu-id="3d055-152">[色の式]</span><span class="sxs-lookup"><span data-stu-id="3d055-152">Color Expressions</span></span>  
 <span data-ttu-id="3d055-153">計算されるメンバーの値に基づいてセルの前景色と背景色を動的に設定する MDX 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d055-153">Specifies MDX expressions that dynamically set the foreground and background colors of cells based on the value of the calculated member.</span></span> <span data-ttu-id="3d055-154">クライアント アプリケーションでサポートされていない場合、このプロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-154">This property is ignored if unsupported by client applications.</span></span>  
  
 <span data-ttu-id="3d055-155">[フォントの式]</span><span class="sxs-lookup"><span data-stu-id="3d055-155">Font Expressions</span></span>  
 <span data-ttu-id="3d055-156">計算されるメンバーの値に基づいてセルのフォント、フォント サイズ、およびフォントの属性を動的に設定する MDX 式を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d055-156">Specifies MDX expressions that dynamically set the font, font size, and font attributes for cells based on the value of the calculated member.</span></span> <span data-ttu-id="3d055-157">クライアント アプリケーションでサポートされていない場合、このプロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="3d055-157">This property is ignored if unsupported by client applications.</span></span>  
  
 <span data-ttu-id="3d055-158">キューブ コンポーネントは、 **[計算ツール]** ペインの **[メタデータ]** タブから計算式ペインの **[式]** ボックスにコピーまたはドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="3d055-158">You can copy or drag cube components from the **Metadata** tab of the **Calculation Tools** pane to the **Expression** box in the Calculation Expressions pane.</span></span> <span data-ttu-id="3d055-159">関数は、 **[計算ツール]** ペインの **[関数]** タブから計算式ペインの **[式]** ボックスにコピーまたはドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="3d055-159">You can copy or drag functions from the **Functions** tab in the **Calculation Tools** pane to the **Expression** box in the Calculation Expressions pane.</span></span>  
  
## <a name="addressing-calculated-members"></a><span data-ttu-id="3d055-160">計算されるメンバーのアドレス指定</span><span class="sxs-lookup"><span data-stu-id="3d055-160">Addressing Calculated Members</span></span>  
 <span data-ttu-id="3d055-161">**キューブ デザイナー** の **[計算]** タブで、計算されるメンバーを作成する場合は、そのメンバーを格納する親階層を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d055-161">When you create a calculated member on the **Calculations** tab of **Cube Designer**, you specify the parent hierarchy in which the calculated member is stored.</span></span> <span data-ttu-id="3d055-162">親階層では、次の規則に従って、計算されるメンバーのアドレス指定方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="3d055-162">The parent hierarchy determines how a calculated member can be addressed, according to the following rules:</span></span>  
  
-   <span data-ttu-id="3d055-163">計算されるメンバーがメジャー ディメンションで作成された場合、そのメンバーはそのディメンション内でアドレス指定可能です。</span><span class="sxs-lookup"><span data-stu-id="3d055-163">If a calculated member is created in the measures dimension, the calculated member is addressable in that dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d055-164">参照</span><span class="sxs-lookup"><span data-stu-id="3d055-164">See Also</span></span>  
 [<span data-ttu-id="3d055-165">多次元モデルの計算</span><span class="sxs-lookup"><span data-stu-id="3d055-165">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
