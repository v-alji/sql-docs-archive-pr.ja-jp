---
title: 固定属性と変化する属性のオプション (緩やかに変化するディメンション ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df654cd97b343179828ebd94dea40eacc90e003d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633234"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a><span data-ttu-id="e66e4-102">[固定属性と変化する属性のオプション] (緩やかに変化するディメンション ウィザード)</span><span class="sxs-lookup"><span data-stu-id="e66e4-102">Fixed and Changing Attribute Options (Slowly Changing Dimension Wizard</span></span>
  <span data-ttu-id="e66e4-103">**[固定属性と変化する属性のオプション]** ダイアログ ボックスを使用すると、固定属性と変化する属性において変更に応答する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="e66e4-103">Use the **Fixed and Changing Attribute Options** dialog box to specify how to respond to changes in fixed and changing attributes.</span></span>  
  
 <span data-ttu-id="e66e4-104">このウィザードの詳細については、「 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e66e4-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e66e4-105">オプション</span><span class="sxs-lookup"><span data-stu-id="e66e4-105">Options</span></span>  
 <span data-ttu-id="e66e4-106">**[固定属性]**</span><span class="sxs-lookup"><span data-stu-id="e66e4-106">**Fixed attributes**</span></span>  
 <span data-ttu-id="e66e4-107">固定属性の場合は、固定属性で変更が検出された場合に、タスクが失敗するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e66e4-107">For fixed attributes, indicate whether the task should fail if a change is detected in a fixed attribute.</span></span>  
  
 <span data-ttu-id="e66e4-108">**[変化する属性]**</span><span class="sxs-lookup"><span data-stu-id="e66e4-108">**Changing attributes**</span></span>  
 <span data-ttu-id="e66e4-109">変化する属性の場合は、変化する属性で変更が検出された場合に、現在のレコードに加え、古いレコードや有効期限が切れたレコードをタスクが変更するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e66e4-109">For changing attributes, indicate whether the task should change outdated or expired records, in addition to current records, when a change is detected in a changing attribute.</span></span> <span data-ttu-id="e66e4-110">有効期限が切れたレコードとは、履歴属性の変更 (種類 2 の変更) によって新しいレコードに置き換えられたレコードのことです。</span><span class="sxs-lookup"><span data-stu-id="e66e4-110">An expired record is a record that has been replaced with a newer record by a change in a historical attribute (a Type 2 change).</span></span> <span data-ttu-id="e66e4-111">このオプションを選択すると、リレーショナル データ ウェアハウスで構築された多次元オブジェクトに処理要件が追加される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e66e4-111">Selecting this option may impose additional processing requirements on a multidimensional object constructed on the relational data warehouse.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66e4-112">参照</span><span class="sxs-lookup"><span data-stu-id="e66e4-112">See Also</span></span>  
 [<span data-ttu-id="e66e4-113">緩やかに変化するディメンション ウィザードを使用して出力を構成する</span><span class="sxs-lookup"><span data-stu-id="e66e4-113">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
