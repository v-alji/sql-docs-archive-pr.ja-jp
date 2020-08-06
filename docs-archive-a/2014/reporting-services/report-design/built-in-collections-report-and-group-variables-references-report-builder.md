---
title: レポート変数コレクションとグループ変数コレクションの参照 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10404"
- sql12.rtp.rptdesigner.categorygroupproperties.variables.f1
- "10083"
- sql12.rtp.rptdesigner.seriesgroupproperties.variables.f1
- sql12.rtp.rptdesigner.reportproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- "10292"
- "10412"
ms.assetid: 4be5b463-3ce2-483d-a3c6-dae752cb543e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 41dd652bf39721b13801131a5ec268495edf9d29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711730"
---
# <a name="report-and-group-variables-collections-references-report-builder-and-ssrs"></a><span data-ttu-id="2b783-102">レポート変数コレクションとグループ変数コレクションの参照 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2b783-102">Report and Group Variables Collections References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="2b783-103">レポート内の式で複数回使用される複雑な計算があれば、変数を作成した方がよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b783-103">When you have a complex calculation that is used more than once in expressions in a report, you might want to create a variable.</span></span> <span data-ttu-id="2b783-104">このような場合は、レポート変数またはグループ変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="2b783-104">You can create a report variable or a group variable.</span></span> <span data-ttu-id="2b783-105">変数名は、レポート内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b783-105">Variable names must be unique in a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-variables"></a><span data-ttu-id="2b783-106">レポート変数</span><span class="sxs-lookup"><span data-stu-id="2b783-106">Report Variables</span></span>  
 <span data-ttu-id="2b783-107">レポート変数は、為替レートやタイム スタンプなどの時間に依存する計算や、複数回参照される複雑な計算で、値を保持するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2b783-107">Use a report variable to hold a value for time-dependent calculations, such as currency rates or time stamps, or for a complex calculation that is referenced multiple times.</span></span> <span data-ttu-id="2b783-108">既定では、レポート変数は 1 回計算すると、レポート全体の式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2b783-108">By default, a report variable is calculated once and can be used in expressions throughout a report.</span></span> <span data-ttu-id="2b783-109">レポート変数は既定では読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="2b783-109">Report variables are read-only by default.</span></span> <span data-ttu-id="2b783-110">既定を変更して、レポート変数を読み書き可能にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2b783-110">You can change the default to enable a report variable as read-write.</span></span> <span data-ttu-id="2b783-111">レポート変数の値はセッション全体で維持され、次回レポートを処理するときまで変わりません。</span><span class="sxs-lookup"><span data-stu-id="2b783-111">The value in a report variable is preserved throughout a session, until the report is processed again.</span></span>  
  
 <span data-ttu-id="2b783-112">レポート変数を追加するには、 **[レポートのプロパティ]** ダイアログ ボックスを開き、 **[変数]** をクリックして、名前と値を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b783-112">To add a report variable, open the **ReportProperties** dialog box, click **Variables**, and provide a name and a value.</span></span> <span data-ttu-id="2b783-113">文字で始まり、空白を含まない名前を入力します。名前の文字列は大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="2b783-113">Names are case-sensitive strings that begin with a letter and have no spaces.</span></span> <span data-ttu-id="2b783-114">名前に含めることができるのは、文字、数字、またはアンダースコア (_) だけです。</span><span class="sxs-lookup"><span data-stu-id="2b783-114">A name can include letters, numbers, or underscores (_).</span></span>  
  
 <span data-ttu-id="2b783-115">式で変数を参照するには、 `=Variables!CustomTimeStamp.Value`などのグローバル コレクション構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="2b783-115">To refer to the variable in an expression, use the global collection syntax, for example, `=Variables!CustomTimeStamp.Value`.</span></span> <span data-ttu-id="2b783-116">デザイン画面では、この値が `<<Expr>>`としてテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b783-116">On the design surface, the value appears in a text box as `<<Expr>>`.</span></span>  
  
 <span data-ttu-id="2b783-117">レポート変数は、次の方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2b783-117">You can use report variables in the following ways:</span></span>  
  
-   <span data-ttu-id="2b783-118">**読み取り専用の使用** たとえば、タイム スタンプを作成する場合に、値を 1 回設定してレポート セッションの定数を作成します。</span><span class="sxs-lookup"><span data-stu-id="2b783-118">**Read-only use** Set a value once to create a constant for the report session, for example, to create a time stamp.</span></span>  
  
     <span data-ttu-id="2b783-119">テキスト ボックス内の式はユーザーがレポートを読み進める間に要求に応じて評価されるため、次のページに進んでから `Now()` [戻る] **ボタンを使用して戻ると、動的な値 (時刻を返す** 関数が含まれている式など) から異なる値が返される場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b783-119">Because expressions in text boxes are evaluated on-demand as a user pages through a report, dynamic values (for example, an expression that includes the `Now()` function, which returns the time of day) can return different values if you page forward and backward by using the **Back** button.</span></span> <span data-ttu-id="2b783-120">レポート変数の値に式 `=Now()`を設定し、その変数を式に追加することで、レポート処理全体で同じ値が使用されるようになります。</span><span class="sxs-lookup"><span data-stu-id="2b783-120">By setting a the value of a report variable to the expression `=Now()`, and then adding the variable to your expression, you ensure the same value is used throughout report processing.</span></span>  
  
-   <span data-ttu-id="2b783-121">**読み書き可能な使用** 値を 1 回設定して、レポート セッション内でその値をシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="2b783-121">**Read-write use** Set a value once and serialize the value within a report session.</span></span> <span data-ttu-id="2b783-122">変数の読み書き可能オプションは、レポート定義のコード ブロックで静的変数を使用するよりも適切な方法です。</span><span class="sxs-lookup"><span data-stu-id="2b783-122">The read-write option for variables provides a better alternative than using a static variable in the Code block in the report definition.</span></span>  
  
     <span data-ttu-id="2b783-123">変数の**読み取り**専用オプションをオフにすると、変数の書き込み可能なプロパティはに設定され `true` ます。</span><span class="sxs-lookup"><span data-stu-id="2b783-123">When you clear the **Read-Only** option for a variable, the Writable property for the variable is set to `true`.</span></span> <span data-ttu-id="2b783-124">式から値を更新するには、SetValue メソッド (たとえば、 `=Variables!MyVariable.SetValue("123")`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="2b783-124">To update the value from an expression, use the SetValue method, for example, `=Variables!MyVariable.SetValue("123")`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2b783-125">レポート プロセッサによって変数が初期化される時期や、変数を更新する式が評価される時期を制御することはできません。</span><span class="sxs-lookup"><span data-stu-id="2b783-125">You cannot control when the report processor initializes a variable or evaluates an expression that updates a variable.</span></span> <span data-ttu-id="2b783-126">変数の初期化の実行順序は定義されません。</span><span class="sxs-lookup"><span data-stu-id="2b783-126">The order of execution for variable initialization is undefined.</span></span>  
  
 <span data-ttu-id="2b783-127">詳細については、「 [レポート ビルダーでのレポートのプレビュー](../report-builder/previewing-reports-in-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b783-127">For more information about sessions, see [Previewing Reports in Report Builder](../report-builder/previewing-reports-in-report-builder.md).</span></span>  
  
## <a name="group-variables"></a><span data-ttu-id="2b783-128">グループ変数</span><span class="sxs-lookup"><span data-stu-id="2b783-128">Group Variables</span></span>  
 <span data-ttu-id="2b783-129">グループ変数は、グループのスコープ内で複合式を 1 回計算するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2b783-129">Use a group variable to calculate a complex expression once in the scope of a group.</span></span> <span data-ttu-id="2b783-130">グループ変数は、グループとその子グループのスコープ内でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="2b783-130">A group variable is valid only in the scope of the group and its child groups.</span></span>  
  
 <span data-ttu-id="2b783-131">たとえば、別々の税区分にある各アイテムの在庫データをデータ領域に表示し、各カテゴリに異なる税率を適用するとします。</span><span class="sxs-lookup"><span data-stu-id="2b783-131">For example, suppose a data region displays inventory data for items that are in different tax categories and you want to apply different tax rates for each category.</span></span> <span data-ttu-id="2b783-132">Category でデータをグループ化し、親グループで *Tax* 変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="2b783-132">You would group the data on Category and define a *Tax* variable on the parent group.</span></span> <span data-ttu-id="2b783-133">次に、税区分ごとに *ItemTax* のグループ変数を定義し、異なる Category サブグループをそれぞれ適切なグループ変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2b783-133">Then you would define a group variable for *ItemTax* for each tax category and assign each of the different Category subgroups to the correct group variable.</span></span> <span data-ttu-id="2b783-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2b783-134">For example:</span></span>  
  
-   <span data-ttu-id="2b783-135">`[Category]`に基づく親グループでは、値 *Tax* を指定して、変数 `[Tax]`を定義します。</span><span class="sxs-lookup"><span data-stu-id="2b783-135">For the parent group based on `[Category]`, define the variable *Tax* with a value `[Tax]`.</span></span> <span data-ttu-id="2b783-136">カテゴリ値が Food と Clothing であるとします。</span><span class="sxs-lookup"><span data-stu-id="2b783-136">Assume the category values are Food and Clothing.</span></span>  
  
-   <span data-ttu-id="2b783-137">`[Subcategory]`に基づく子グループでは、変数 *ItemsTax* を `=Variables!Tax.Value * Sum(Fields!Price.Value)`として定義します。</span><span class="sxs-lookup"><span data-stu-id="2b783-137">For the child group based on `[Subcategory]`, define the variable *ItemsTax* as `=Variables!Tax.Value * Sum(Fields!Price.Value)`.</span></span> <span data-ttu-id="2b783-138">Food カテゴリのサブカテゴリ値が Beverages と Bread、</span><span class="sxs-lookup"><span data-stu-id="2b783-138">Assume the subcategory values for the category Food are Beverages and Bread.</span></span> <span data-ttu-id="2b783-139">Clothing カテゴリのサブカテゴリ値が Shirts と Hats であるとします。</span><span class="sxs-lookup"><span data-stu-id="2b783-139">Assume the subcategory values for Clothing are Shirts and Hats.</span></span>  
  
-   <span data-ttu-id="2b783-140">子グループの行のテキスト ボックスで、式 `=Variables!ItemsTax.Value`を追加します。</span><span class="sxs-lookup"><span data-stu-id="2b783-140">For a text box in a row in the child group, add the expression `=Variables!ItemsTax.Value`.</span></span>  
  
     <span data-ttu-id="2b783-141">このテキスト ボックスには、Food の税を使用した場合は Beverages と Bread、Clothing の税を使用した場合は Shirts と Hats の税の総額が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b783-141">The text box displays the total tax for Beverages and Bread using the Food tax and for Shirts and Hats using the Clothing tax.</span></span>  
  
 <span data-ttu-id="2b783-142">グループ変数を追加するには、 **[Tablix グループのプロパティ]** ダイアログ ボックスを開き、 **[変数]** をクリックし、名前および値を指定します。</span><span class="sxs-lookup"><span data-stu-id="2b783-142">To add a group variable, open the **Tablix Group Properties** dialog box, click **Variables**, and provide a name and a value.</span></span> <span data-ttu-id="2b783-143">グループ変数は、一意のグループの値ごとに 1 回計算されます。</span><span class="sxs-lookup"><span data-stu-id="2b783-143">The group variable is calculated once per unique group value.</span></span>  
  
 <span data-ttu-id="2b783-144">式で変数を参照するには、 `=Variables!GroupDescription.Value`などのグローバル コレクション構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="2b783-144">To refer to the variable in an expression, use the global collection syntax, for example, `=Variables!GroupDescription.Value`.</span></span> <span data-ttu-id="2b783-145">デザイン画面では、この値が `<<Expr>>`としてテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b783-145">On the design surface, the value appears in a text box as `<<Expr>>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b783-146">参照</span><span class="sxs-lookup"><span data-stu-id="2b783-146">See Also</span></span>  
 <span data-ttu-id="2b783-147">[データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2b783-147">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="2b783-148">[式で使用される組み込みコレクション (レポート ビルダーおよび SSRS)](built-in-collections-in-expressions-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="2b783-148">[Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](built-in-collections-in-expressions-report-builder.md) </span></span>  
 [<span data-ttu-id="2b783-149">式の例 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2b783-149">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
