---
title: '[式ビルダー] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.expressionbuilder.f1
helpviewer_keywords:
- Expression Builder dialog box
ms.assetid: 4717ce33-bd4e-44bc-81e0-002de075b4d1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 812b0d744d415d5419d54176359ddcd5837dd206
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640177"
---
# <a name="expression-builder"></a><span data-ttu-id="3d9b2-102">式ビルダー</span><span class="sxs-lookup"><span data-stu-id="3d9b2-102">Expression Builder</span></span>
  <span data-ttu-id="3d9b2-103">**[式ビルダー]** ダイアログ ボックスには、変数を一覧表示したり、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 式の言語に含まれる関数、型キャスト、および演算子への組み込み参照を提供するグラフィカル ユーザー インターフェイスが用意されています。このグラフィカル ユーザー インターフェイスを使用して、プロパティ式の作成および編集や、変数の値を設定する式の作成を行えます。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-103">Use the **Expression Builder** dialog box to create and edit a property expression or write the expression that sets the value of a variable using a graphical user interface that lists variables and provides a built-in reference to the functions, type casts, and operators that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language includes.</span></span>  
  
 <span data-ttu-id="3d9b2-104">プロパティ式とは、プロパティに割り当てられる式です。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-104">A property expression is an expression that is assigned to a property.</span></span> <span data-ttu-id="3d9b2-105">式が評価されると、式の評価結果を使用してプロパティが動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-105">When the expression is evaluated, the property is dynamically updated to use the evaluation result of the expression.</span></span> <span data-ttu-id="3d9b2-106">同様に、変数内で式を使用することにより、式の評価結果で変数値を更新することができます。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-106">Likewise, an expression that is used in a variable enables the variable value to be updated with the evaluation result of the expression.</span></span>  
  
 <span data-ttu-id="3d9b2-107">式を使用するには次のように多くの方法があります。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-107">There are many ways to use expressions:</span></span>  
  
-   <span data-ttu-id="3d9b2-108">**タスク:** 変数内に格納されている電子メール アドレスを挿入することにより、メール送信タスクで使用される [宛先] 行を更新します。または、"売上:" などの文字列と GETDATE 関数から返される現在の日付を連結することにより、[件名] 行を更新します。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-108">**Tasks** Update the To line that a Send Mail task uses by inserting an e-mail address that is stored in a variable; or update the Subject line by concatenating a string such as "Sales for: " and the current date returned by the GETDATE function.</span></span>  
  
-   <span data-ttu-id="3d9b2-109">**変数:** `DATEPART("mm",GETDATE())`などの式を使用して、変数の値を現在の月に設定します。または、式 `"Today's date is " + (DT_WSTR,30)(GETDATE())`を使用して文字列リテラルと現在の日付を連結することにより、文字列の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-109">**Variables** Set the value of a variable to the current month by using an expression like `DATEPART("mm",GETDATE())`; or set the value of a string by concatenating the string literal and the current date by using the expression `"Today's date is " + (DT_WSTR,30)(GETDATE())`.</span></span>  
  
-   <span data-ttu-id="3d9b2-110">**接続マネージャー :** 異なるコード ページ識別子が格納されている変数を使用することにより、フラット ファイル接続マネージャーのコード ページを設定します。または、式に 3 などの正の整数を入力してデータ ファイル内のスキップする行数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-110">**Connection Managers** Set the code page of a Flat File connection manager by using a variable that contains a different code page identifier; or specify the number of rows in the data file to skip by entering a positive integer like 3 in the expression.</span></span>  
  
 <span data-ttu-id="3d9b2-111">プロパティ式と式の作成の詳細については、「[パッケージでプロパティ式を使用する](use-property-expressions-in-packages.md)」と「[Integration Services (SSIS) の式](integration-services-ssis-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-111">To learn more about property expressions and writing expressions, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md) and [Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3d9b2-112">オプション</span><span class="sxs-lookup"><span data-stu-id="3d9b2-112">Options</span></span>  
  
|<span data-ttu-id="3d9b2-113">期間</span><span class="sxs-lookup"><span data-stu-id="3d9b2-113">Term</span></span>|<span data-ttu-id="3d9b2-114">定義</span><span class="sxs-lookup"><span data-stu-id="3d9b2-114">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="3d9b2-115">**変数**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-115">**Variables**</span></span>|<span data-ttu-id="3d9b2-116">**[変数]** フォルダーを展開し、変数を **[式]** ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-116">Expand the **Variables** folder and drag variables to the **Expression** box.</span></span>|  
|<span data-ttu-id="3d9b2-117">**数学関数**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-117">**Mathematical Functions**</span></span><br /><br /> <span data-ttu-id="3d9b2-118">**文字列関数**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-118">**String Functions**</span></span><br /><br /> <span data-ttu-id="3d9b2-119">**日付/時刻関数**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-119">**Date/Time Functions**</span></span><br /><br /> <span data-ttu-id="3d9b2-120">**NULL 関数**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-120">**NULL Functions**</span></span><br /><br /> <span data-ttu-id="3d9b2-121">**[型キャスト]**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-121">**Type Casts**</span></span><br /><br /> <span data-ttu-id="3d9b2-122">**オペレーター**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-122">**Operators**</span></span>|<span data-ttu-id="3d9b2-123">フォルダーを展開し、関数、型キャスト、および演算子を **[式]** ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-123">Expand the folders and drag functions, type casts, and operators to the **Expression** box.</span></span>|  
|<span data-ttu-id="3d9b2-124">**[式]**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-124">**Expression**</span></span>|<span data-ttu-id="3d9b2-125">式を編集または入力します。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-125">Edit or type an expression.\`</span></span>|  
|<span data-ttu-id="3d9b2-126">**[評価結果]**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-126">**Evaluated value**</span></span>|<span data-ttu-id="3d9b2-127">式の評価結果を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-127">Lists the evaluation result of the expression.</span></span>|  
|<span data-ttu-id="3d9b2-128">**[式の評価]**</span><span class="sxs-lookup"><span data-stu-id="3d9b2-128">**Evaluate Expression**</span></span>|<span data-ttu-id="3d9b2-129">**[式の評価]** をクリックすると、式の評価結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d9b2-129">Click **Evaluate Expression** to view the evaluation result of the expression.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d9b2-130">参照</span><span class="sxs-lookup"><span data-stu-id="3d9b2-130">See Also</span></span>  
 <span data-ttu-id="3d9b2-131">[[式] ページ](expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="3d9b2-131">[Expressions Page](expressions-page.md) </span></span>  
 <span data-ttu-id="3d9b2-132">[プロパティ式エディター](property-expressions-editor.md) </span><span class="sxs-lookup"><span data-stu-id="3d9b2-132">[Property Expressions Editor](property-expressions-editor.md) </span></span>  
 <span data-ttu-id="3d9b2-133">[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="3d9b2-133">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="3d9b2-134">システム変数</span><span class="sxs-lookup"><span data-stu-id="3d9b2-134">System Variables</span></span>](../system-variables.md)  
  
  
