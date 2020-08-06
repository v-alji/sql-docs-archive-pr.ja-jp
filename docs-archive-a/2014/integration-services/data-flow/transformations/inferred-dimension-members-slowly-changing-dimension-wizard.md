---
title: 推定ディメンション メンバー (緩やかに変化するディメンション ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dda4345b91c69b134516baab2e5ba9b9990bd6af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644061"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a><span data-ttu-id="bbfcf-102">[推定ディメンション メンバー] (緩やかに変化するディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="bbfcf-102">Inferred Dimension Members (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="bbfcf-103">**[推定ディメンション メンバー]** ダイアログ ボックスを使用すると、推定メンバーを使用するためのオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bbfcf-103">Use the **Inferred Dimension Members** dialog box to specify options for using inferred members.</span></span> <span data-ttu-id="bbfcf-104">推定メンバーは、まだ読み込まれていないディメンション メンバーをファクト テーブルで参照するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="bbfcf-104">Inferred members exist when a fact table references dimension members that are not yet loaded.</span></span> <span data-ttu-id="bbfcf-105">推定メンバーのデータが読み込まれると、新しいレコードを作成する代わりに、既存のレコードを更新できます。</span><span class="sxs-lookup"><span data-stu-id="bbfcf-105">When data for the inferred member is loaded, you can update the existing record rather than create a new one.</span></span>  
  
 <span data-ttu-id="bbfcf-106">このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbfcf-106">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bbfcf-107">オプション</span><span class="sxs-lookup"><span data-stu-id="bbfcf-107">Options</span></span>  
 <span data-ttu-id="bbfcf-108">**[推定メンバー サポートを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="bbfcf-108">**Enable inferred member support**</span></span>  
 <span data-ttu-id="bbfcf-109">推定メンバーを有効にすることを選択した場合は、次のどちらかのオプションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbfcf-109">If you choose to enable inferred members, you must select one of the two options that follow.</span></span>  
  
 <span data-ttu-id="bbfcf-110">**[変化する型を持つすべての列を NULL とする]**</span><span class="sxs-lookup"><span data-stu-id="bbfcf-110">**All columns with a change type are null**</span></span>  
 <span data-ttu-id="bbfcf-111">新しい推定メンバー レコード内で、変化する型を持つすべての列に NULL 値を入力するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbfcf-111">Specify whether to enter null values in all columns with a change type in the new inferred member record.</span></span>  
  
 <span data-ttu-id="bbfcf-112">**[現在のレコードが推定メンバーであるかどうかの識別にブール型の列を使用する]**</span><span class="sxs-lookup"><span data-stu-id="bbfcf-112">**Use a Boolean column to indicate whether the current record is an inferred member**</span></span>  
 <span data-ttu-id="bbfcf-113">現在のレコードが推定メンバーであるかどうかを示すために、既存のブール型の列を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbfcf-113">Specify whether to use an existing Boolean column to indicate whether the current record is an inferred member.</span></span>  
  
 <span data-ttu-id="bbfcf-114">**[推定メンバー インジケーター]**</span><span class="sxs-lookup"><span data-stu-id="bbfcf-114">**Inferred member indicator**</span></span>  
 <span data-ttu-id="bbfcf-115">上記の、推定メンバーであるかどうかの識別にブール型の列を使用することを選択した場合は、一覧から列を選択します。</span><span class="sxs-lookup"><span data-stu-id="bbfcf-115">If you have chosen to use a Boolean column to indicate inferred members as described above, select the column from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfcf-116">参照</span><span class="sxs-lookup"><span data-stu-id="bbfcf-116">See Also</span></span>  
 [<span data-ttu-id="bbfcf-117">緩やかに変化するディメンション ウィザードを使用して出力を構成する</span><span class="sxs-lookup"><span data-stu-id="bbfcf-117">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
