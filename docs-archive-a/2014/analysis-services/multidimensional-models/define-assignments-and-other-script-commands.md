---
title: 割り当てとその他のスクリプトコマンドを定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- empty scripts [Analysis Services]
- calculations [Analysis Services], scripts
- MDX [Analysis Services], scripts
- scripts [Analysis Services], calculations
ms.assetid: f28b9b22-3dc7-4a45-b4eb-2d023f2c94b8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 184c998bb4bd27d077cca78e792a7e7712f87666
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643582"
---
# <a name="define-assignments-and-other-script-commands"></a><span data-ttu-id="eaa01-102">割り当てとその他のスクリプト コマンドの定義</span><span class="sxs-lookup"><span data-stu-id="eaa01-102">Define Assignments and Other Script Commands</span></span>
  <span data-ttu-id="eaa01-103">キューブ デザイナーの **[計算]** タブで、ツール バーの **[新しいスクリプト コマンド]** アイコンをクリックして、空のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="eaa01-103">On the **Calculations** tab of Cube Designer, click the **New ScriptCommand** icon on the toolbar to create an empty script.</span></span> <span data-ttu-id="eaa01-104">新しいスクリプトを作成すると、最初に [計算] タブの [**スクリプトオーガナイザー** ] ペインに空白のタイトルが表示されます。計算式ペインに入力する文字は、[**スクリプトオーガナイザー**] でアイテムの名前として表示されます。</span><span class="sxs-lookup"><span data-stu-id="eaa01-104">When you create a new script, it initially is displayed with a blank title in the **Script Organizer** pane of the Calculations tab. The characters you type in the Calculation Expressions pane will be visible as the name of the item in **Script Organizer**.</span></span> <span data-ttu-id="eaa01-105">このため、最初の行にコメント付きの名前を入力すると、 **[スクリプト オーガナイザー]** ペインでスクリプトが識別しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="eaa01-105">Therefore, you may want to type a commented name on the first line to more easily identify the script in the **Script Organizer** pane.</span></span> <span data-ttu-id="eaa01-106">詳細については、「 [Microsoft SQL Server 2005 の MDX スクリプトの紹介](https://go.microsoft.com/fwlink/?LinkId=81892)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaa01-106">For more information, see [Introduction to MDX Scripting in Microsoft SQL Server 2005](https://go.microsoft.com/fwlink/?LinkId=81892).</span></span> <span data-ttu-id="eaa01-107">MDX クエリおよび計算に関連するパフォーマンスの問題の詳細については、「 [SQL Server 2005 Analysis Services パフォーマンスガイド](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide)」の「効率的な Mdx の記述」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eaa01-107">For more information about performance issues related to MDX queries and calculations, see the section "Writing Efficient MDX" in the [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eaa01-108">最初に、キューブ デザイナーの **[計算]** タブに切り替えると、 **[スクリプト オーガナイザー]** ペインには、CALCULATE コマンドを持つスクリプトが 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="eaa01-108">When you initially switch to the **Calculations** tab of Cube Designer, the **Script Organizer** pane contains a single script with a CALCULATE command.</span></span> <span data-ttu-id="eaa01-109">CALCULATE コマンドは、キューブ内のセルの集計を制御し、キューブの集計方法を手動で指定する場合にのみ編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eaa01-109">The CALCULATE command controls the aggregation of the cells in the cube and should be edited only if you intend to manually specify how the cube is to be aggregated.</span></span>  
  
 <span data-ttu-id="eaa01-110">計算式ペインを使用して、多次元式 (MDX) 構文で式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="eaa01-110">You can use the Calculation Expressions pane to build an expression in Multidimensional Expressions (MDX) syntax.</span></span> <span data-ttu-id="eaa01-111">式の作成中は、キューブ コンポーネント、関数、およびテンプレートを **[計算ツール]** ペインから計算式ペインにドラッグまたはコピーできます。</span><span class="sxs-lookup"><span data-stu-id="eaa01-111">While you build the expression, you can drag or copy cube components, functions, and templates from the **Calculation Tools** pane to the Calculation Expressions pane.</span></span> <span data-ttu-id="eaa01-112">これにより、アイテムのスクリプトが、それをドロップまたは貼り付ける場所で計算式ペインに追加されます。</span><span class="sxs-lookup"><span data-stu-id="eaa01-112">Doing so adds the script for the item to the Calculation Expressions pane in the location that you drop or paste it.</span></span> <span data-ttu-id="eaa01-113">引数とその区切り記号 (&#xAB; と &#xBB;) を適切な値に置換してください。</span><span class="sxs-lookup"><span data-stu-id="eaa01-113">Replace arguments and their delimiters (« and ») with the appropriate values.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eaa01-114">計算式ペインを使用して、複数のステートメントが含まれている式を書き込む場合は、MDX スクリプトの最後の行を除くすべての行がセミコロン (;) で終了していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="eaa01-114">When writing an expression that contains multiple statements using the Calculation Expressions pane, ensure that all lines except the last line of the MDX script end with a semi-colon (;).</span></span> <span data-ttu-id="eaa01-115">計算は、1 つの MDX スクリプトに連結され、各スクリプトにはセミコロンが追加されて、MDX スクリプトが正しくコンパイルされることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="eaa01-115">Calculations are concatenated into a single MDX script, and each script has a semi-colon appended to it to ensure that the MDX script compiles correctly.</span></span> <span data-ttu-id="eaa01-116">計算式ペインでスクリプトの最後の行にセミコロンを追加した場合、キューブは正しく作成および配置されますが、それに対してクエリを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="eaa01-116">If you add a semi-colon to the last line of the script in the Calculation Expressions pane, the cube will build and deploy correctly but you will be unable to run queries against it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa01-117">参照</span><span class="sxs-lookup"><span data-stu-id="eaa01-117">See Also</span></span>  
 [<span data-ttu-id="eaa01-118">多次元モデルの計算</span><span class="sxs-lookup"><span data-stu-id="eaa01-118">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)  
  
  
