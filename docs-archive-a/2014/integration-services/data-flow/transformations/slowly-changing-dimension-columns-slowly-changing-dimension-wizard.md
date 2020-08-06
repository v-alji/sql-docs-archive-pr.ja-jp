---
title: '[緩やかに変化するディメンションの列] (緩やかに変化するディメンション ウィザード) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.scdsupport.f1
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6283887cbddb9844e0ac769281184f588dc2a94d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712189"
---
# <a name="slowly-changing-dimension-columns-slowly-changing-dimension-wizard"></a><span data-ttu-id="57ea7-102">[緩やかに変化するディメンションの列] (緩やかに変化するディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="57ea7-102">Slowly Changing Dimension Columns (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="57ea7-103">**[緩やかに変化するディメンションの列]** ダイアログ ボックスを使用すると、緩やかに変化するディメンションの各列に対して変更の種類を選択できます。</span><span class="sxs-lookup"><span data-stu-id="57ea7-103">Use the **Slowly Changing Dimensions Columns** dialog box to select a change type for each slowly changing dimension column.</span></span>  
  
 <span data-ttu-id="57ea7-104">このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57ea7-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="57ea7-105">オプション</span><span class="sxs-lookup"><span data-stu-id="57ea7-105">Options</span></span>  
 <span data-ttu-id="57ea7-106">**[ディメンション列]**</span><span class="sxs-lookup"><span data-stu-id="57ea7-106">**Dimension Columns**</span></span>  
 <span data-ttu-id="57ea7-107">ディメンション列を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="57ea7-107">Select a dimension column from the list.</span></span>  
  
 <span data-ttu-id="57ea7-108">**[変更の種類]**</span><span class="sxs-lookup"><span data-stu-id="57ea7-108">**Change Type**</span></span>  
 <span data-ttu-id="57ea7-109">**[固定属性]** を選択するか、変化する属性の 2 つのうちのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="57ea7-109">Select a **Fixed Attribute**, or select one of the two types of changing attributes.</span></span> <span data-ttu-id="57ea7-110">列の値を変更しない場合は **[固定属性]** を使用します。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] は、変更をエラーとして扱います。</span><span class="sxs-lookup"><span data-stu-id="57ea7-110">Use **Fixed Attribute** when the value in a column should not change; [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] then treats changes as errors.</span></span> <span data-ttu-id="57ea7-111">**[変化する属性]** を使用して、既存の値を変更後の値で上書きします。</span><span class="sxs-lookup"><span data-stu-id="57ea7-111">Use **Changing Attribute** to overwrite existing values with changed values.</span></span> <span data-ttu-id="57ea7-112">**[履歴属性]** を使用して、変更後の値を新しいレコードに保存し、前のレコードを期限切れにすることができます。</span><span class="sxs-lookup"><span data-stu-id="57ea7-112">Use **Historical Attribute** to save changed values in new records, while marking previous records as outdated.</span></span>  
  
 <span data-ttu-id="57ea7-113">**Remove**</span><span class="sxs-lookup"><span data-stu-id="57ea7-113">**Remove**</span></span>  
 <span data-ttu-id="57ea7-114">ディメンション列を選択し、 **[削除]** をクリックして、マップされた列の一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="57ea7-114">Select a dimension column, and remove it from the list of mapped columns by clicking **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57ea7-115">参照</span><span class="sxs-lookup"><span data-stu-id="57ea7-115">See Also</span></span>  
 [<span data-ttu-id="57ea7-116">緩やかに変化するディメンション ウィザードを使用して出力を構成する</span><span class="sxs-lookup"><span data-stu-id="57ea7-116">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
