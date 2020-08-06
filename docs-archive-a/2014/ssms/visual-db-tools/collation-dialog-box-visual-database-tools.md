---
title: '[照合順序] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.definecolumncollation
- vdtsql.chm:65561
ms.assetid: e4020f79-7abf-4839-b9b2-984ef7049817
author: stevestein
ms.author: sstein
ms.openlocfilehash: d551b2ae7ca27250c144afedf13038efd78ad6ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645953"
---
# <a name="collation-dialog-box-visual-database-tools"></a><span data-ttu-id="cf553-102">[照合順序] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="cf553-102">Collation Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="cf553-103">このダイアログ ボックスを使用すると、列の照合順序を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cf553-103">This dialog box lets you specify a collation sequence for the column.</span></span> <span data-ttu-id="cf553-104">列の照合順序は、列の値を別の列や定数値と比較する演算で使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf553-104">A column's collation sequence is used in any operation that compares values of the column to another column or to constant values.</span></span> <span data-ttu-id="cf553-105">また、SUBSTRING や CHARINDEX などの一部の文字列関数の動作にも影響します。</span><span class="sxs-lookup"><span data-stu-id="cf553-105">It also affects the behavior of some string functions, such as SUBSTRING and CHARINDEX.</span></span> <span data-ttu-id="cf553-106">列の照合順序設定による影響の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf553-106">For a complete list of the effects of a column's collation setting, see the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="cf553-107">このダイアログ ボックスは以下の場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf553-107">This dialog box appears:</span></span>  
  
-   <span data-ttu-id="cf553-108">**[列のプロパティ]** タブの **[照合順序]** フィールドに無効な照合順序名を入力した場合。</span><span class="sxs-lookup"><span data-stu-id="cf553-108">If you enter an invalid collation name in the **Collation** field on the **Column Properties** tab.</span></span>  
  
-   <span data-ttu-id="cf553-109">**[列のプロパティ]** タブの **[照合順序]** フィールドをクリックし、フィールドの右の省略記号ボタン ( **[...]** ) をクリックした場合。</span><span class="sxs-lookup"><span data-stu-id="cf553-109">If you click in the **Collation** field on the **Column Properties** tab, and then click the ellipsis button (**...**) to the right of the field.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf553-110">オプション</span><span class="sxs-lookup"><span data-stu-id="cf553-110">Options</span></span>  
 <span data-ttu-id="cf553-111">**[SQL 照合順序]**</span><span class="sxs-lookup"><span data-stu-id="cf553-111">**SQL Collation**</span></span>  
 <span data-ttu-id="cf553-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって定義された照合順序をドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="cf553-112">Choose among the collation sequences defined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from the drop-down list.</span></span>  
  
 <span data-ttu-id="cf553-113">**[Windows 照合順序]**</span><span class="sxs-lookup"><span data-stu-id="cf553-113">**Windows Collation**</span></span>  
 <span data-ttu-id="cf553-114">Windows によって定義された照合順序をドロップダウン リストから選択します。</span><span class="sxs-lookup"><span data-stu-id="cf553-114">Choose among the collation sequences defined by Windows from the drop-down list.</span></span>  
  
 <span data-ttu-id="cf553-115">**[バイナリ並べ替え]**</span><span class="sxs-lookup"><span data-stu-id="cf553-115">**Binary Sort**</span></span>  
 <span data-ttu-id="cf553-116">比較用に文字の値のバイナリ コードを使用します。</span><span class="sxs-lookup"><span data-stu-id="cf553-116">Use the binary codes of character values for comparisons.</span></span> <span data-ttu-id="cf553-117">このオプションを選択すると、特定のアルファベット比較オプションが使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cf553-117">If you select this option, certain alphabetic comparison options become unavailable.</span></span> <span data-ttu-id="cf553-118">たとえば、アルファベットの大文字と小文字のバイナリ コードは異なるため、大文字と小文字を区別しない比較はできなくなります。</span><span class="sxs-lookup"><span data-stu-id="cf553-118">For example, case-insensitive comparisons become unavailable because uppercase letters and lowercase letters have different binary encodings.</span></span> <span data-ttu-id="cf553-119">**[Windows 照合順序]** を選択した場合にだけ適用されます。</span><span class="sxs-lookup"><span data-stu-id="cf553-119">Applies only if you select **Windows collation**.</span></span>  
  
 <span data-ttu-id="cf553-120">**[辞書並べ替え]**</span><span class="sxs-lookup"><span data-stu-id="cf553-120">**Dictionary Sort**</span></span>  
 <span data-ttu-id="cf553-121">アルファベット比較オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="cf553-121">Use alphabetic comparison options.</span></span> <span data-ttu-id="cf553-122">**[Windows 照合順序]** を選択した場合にだけ適用されます。</span><span class="sxs-lookup"><span data-stu-id="cf553-122">Applies only if you select **Windows collation**.</span></span> <span data-ttu-id="cf553-123">次のアルファベット比較オプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf553-123">The alphabetic comparisons options are:</span></span>  
  
-   <span data-ttu-id="cf553-124">**[大文字と小文字を区別する]** : 大文字と小文字を別の文字として扱う場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="cf553-124">**Case Sensitive** Select this if you want comparisons to consider uppercase and lowercase letters to be unequal.</span></span>  
  
-   <span data-ttu-id="cf553-125">**[アクセントを区別する]** : 文字にアクセント記号が付いている場合と付いていない場合をそれぞれ別の文字として扱うときに選択します。</span><span class="sxs-lookup"><span data-stu-id="cf553-125">**Accent Sensitive** Select this if you want comparisons to consider accented and unaccented letters to be unequal.</span></span> <span data-ttu-id="cf553-126">このオプションを選択すると、別のアクセント記号が付いている場合にも別の文字として扱われます。</span><span class="sxs-lookup"><span data-stu-id="cf553-126">If you select this, comparisons will also consider differently accented letters to be unequal.</span></span>  
  
-   <span data-ttu-id="cf553-127">**[カタカナを区別する]** : 日本語のひらがなとカタカナを区別して扱う場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="cf553-127">**Kana Sensitive** Select this if you want comparisons to consider katakana and hiragana Japanese syllables to be unequal.</span></span>  
  
-   <span data-ttu-id="cf553-128">**[文字幅を区別する]** : 半角文字と全角文字を区別して扱う場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="cf553-128">**Width Sensitive** Select this if you want comparisons to consider half-width and full-width characters to be unequal.</span></span>  
  
 <span data-ttu-id="cf553-129">**[既定値に戻す] ボタン**</span><span class="sxs-lookup"><span data-stu-id="cf553-129">**Restore Default Button**</span></span>  
 <span data-ttu-id="cf553-130">データベースの既定の照合順序を列に適用します。</span><span class="sxs-lookup"><span data-stu-id="cf553-130">Apply the default collation sequence for the database to the column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf553-131">参照</span><span class="sxs-lookup"><span data-stu-id="cf553-131">See Also</span></span>  
 [<span data-ttu-id="cf553-132">集計クエリにおける列の使用 (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="cf553-132">Work with Columns in Aggregate Queries &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
