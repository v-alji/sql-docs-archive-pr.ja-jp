---
title: For ループコンテナーを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: b9cd7ea7-b198-4a35-8b16-6acf09611ca5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9cb33ea5b7f3f59baad3c94f6bc845c281613ec9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632627"
---
# <a name="configure-a-for-loop-container"></a><span data-ttu-id="39875-102">For ループ コンテナーを構成する</span><span class="sxs-lookup"><span data-stu-id="39875-102">Configure a For Loop Container</span></span>
  <span data-ttu-id="39875-103">この手順では、 **[For ループ エディター]** ダイアログ ボックスを使用して、For ループ コンテナーを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39875-103">This procedure describes how to configure a For Loop container by using the **For Loop Editor** dialog box.</span></span>  
  
### <a name="to-configure-the-for-loop-container"></a><span data-ttu-id="39875-104">For ループ コンテナーを構成するには</span><span class="sxs-lookup"><span data-stu-id="39875-104">To configure the For Loop container</span></span>  
  
1.  <span data-ttu-id="39875-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、For ループ コンテナーをダブルクリックして **[For ループ エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="39875-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], double-click the For Loop container to open the **For Loop Editor**.</span></span>  
  
2.  <span data-ttu-id="39875-106">必要に応じて、For ループ コンテナーの名前と説明を変更します。</span><span class="sxs-lookup"><span data-stu-id="39875-106">Optionally, modify the name and description of the For Loop container.</span></span>  
  
3.  <span data-ttu-id="39875-107">必要に応じて、 **[InitExpression]** テキスト ボックスに初期化式を入力します。</span><span class="sxs-lookup"><span data-stu-id="39875-107">Optionally, type an initialization expression in the **InitExpression** text box.</span></span>  
  
4.  <span data-ttu-id="39875-108">**[EvalExpression]** テキスト ボックスに、評価式を入力します。</span><span class="sxs-lookup"><span data-stu-id="39875-108">Type an evaluation expression in the **EvalExpression** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39875-109">式はブール値に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="39875-109">The expression must evaluate to a Boolean.</span></span> <span data-ttu-id="39875-110">式が `false` に評価されると、ループは実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="39875-110">When the expression evaluates to `false`, the loop stops running.</span></span>  
  
5.  <span data-ttu-id="39875-111">必要に応じて、 **[AssignExpression]** テキスト ボックスに代入式を入力します。</span><span class="sxs-lookup"><span data-stu-id="39875-111">Optionally, type an assignment expression in the **AssignExpression** text box.</span></span>  
  
6.  <span data-ttu-id="39875-112">必要に応じて、 **[式]** をクリックし、 **[式]** ページで For ループ コンテナーのプロパティ用のプロパティ式を作成します。</span><span class="sxs-lookup"><span data-stu-id="39875-112">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions for the properties of the For Loop container.</span></span> <span data-ttu-id="39875-113">詳細については、「 [プロパティ式を追加または変更する](expressions/add-or-change-a-property-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39875-113">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
7.  <span data-ttu-id="39875-114">**[OK]** をクリックし、 **[For ループ エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="39875-114">Click **OK** to close the **For Loop Editor**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39875-115">参照</span><span class="sxs-lookup"><span data-stu-id="39875-115">See Also</span></span>  
 <span data-ttu-id="39875-116">[For ループコンテナー](control-flow/for-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="39875-116">[For Loop Container](control-flow/for-loop-container.md) </span></span>  
 <span data-ttu-id="39875-117">[SSIS&#41; 式の Integration Services &#40;](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="39875-117">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 [<span data-ttu-id="39875-118">パッケージでプロパティ式を使用する</span><span class="sxs-lookup"><span data-stu-id="39875-118">Use Property Expressions in Packages</span></span>](expressions/use-property-expressions-in-packages.md)  
  
  
