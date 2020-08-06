---
title: テーブルの種類の指定 (データマイニングウィザード) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytabletypes.f1
ms.assetid: 8209a707-faef-4ffc-8991-6c13bb350753
author: minewiskan
ms.author: owend
ms.openlocfilehash: 88c09f26958c37ed0a99efb54a5eb5c08505d16b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643508"
---
# <a name="specify-table-types-data-mining-wizard"></a><span data-ttu-id="0f310-102">[テーブルの種類の指定] (データ マイニング ウィザード)</span><span class="sxs-lookup"><span data-stu-id="0f310-102">Specify Table Types (Data Mining Wizard)</span></span>
  <span data-ttu-id="0f310-103">**[テーブルの種類の指定]** ページを使用すると、マイニング構造を定義するために使用するテーブルを識別できます。</span><span class="sxs-lookup"><span data-stu-id="0f310-103">Use the **Specify Table Types** page to identify the tables to use to define the mining structure.</span></span> <span data-ttu-id="0f310-104">テーブルが選択されていない場合、マイニング構造の定義にテーブルは使用されません。</span><span class="sxs-lookup"><span data-stu-id="0f310-104">If a table is not selected, it will not be used to define the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f310-105">後から、**データ マイニング デザイナー**の **[マイニング構造]** タブでテーブルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="0f310-105">You can add tables later from the **Mining Structure** tab in **Data Mining Designer**.</span></span>  
  
 <span data-ttu-id="0f310-106">**詳細情報:** [入れ子になったテーブル &#40;Analysis Services - データ マイニング&#41;](data-mining/nested-tables-analysis-services-data-mining.md)、[データ マイニング ウィザード &#40;Analysis Services - データ マイニング&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md)、[リレーショナル マイニング構造の作成](data-mining/create-a-relational-mining-structure.md)</span><span class="sxs-lookup"><span data-stu-id="0f310-106">**For More Information:** [Nested Tables &#40;Analysis Services - Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Create a Relational Mining Structure](data-mining/create-a-relational-mining-structure.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="0f310-107">Options</span><span class="sxs-lookup"><span data-stu-id="0f310-107">Options</span></span>  
 <span data-ttu-id="0f310-108">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="0f310-108">**Tables**</span></span>  
 <span data-ttu-id="0f310-109">ウィザードの **[データ ソース ビューの選択]** ページで選択したテーブルをデータ ソース ビューに表示します。</span><span class="sxs-lookup"><span data-stu-id="0f310-109">Displays the tables in the data source view that you selected on the **Select Data Source View** page of the wizard.</span></span>  
  
 <span data-ttu-id="0f310-110">**Case**</span><span class="sxs-lookup"><span data-stu-id="0f310-110">**Case**</span></span>  
 <span data-ttu-id="0f310-111">ケース テーブルとして使用するテーブルを 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="0f310-111">Select one table to use as the case table.</span></span>  
  
 <span data-ttu-id="0f310-112">**複合**</span><span class="sxs-lookup"><span data-stu-id="0f310-112">**Nested**</span></span>  
 <span data-ttu-id="0f310-113">入れ子になったテーブルとして使用するテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="0f310-113">Select the tables to use as nested tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f310-114">これらのテーブルとケース テーブルとのリレーションシップは、一対多ではなく、多対一である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f310-114">These tables must have a many-to-one relationship with the case table, not a one-to-many relationship.</span></span> <span data-ttu-id="0f310-115">テーブルを入れ子として選択する前に、このリレーションシップをデータ ソース ビューで指定してください。</span><span class="sxs-lookup"><span data-stu-id="0f310-115">You must specify this relationship in the data source view before you can select the table as nested.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f310-116">参照</span><span class="sxs-lookup"><span data-stu-id="0f310-116">See Also</span></span>  
 <span data-ttu-id="0f310-117">[データマイニングウィザードの F1 ヘルプ &#40;Analysis Services データマイニング&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0f310-117">[Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="0f310-118">[データマイニングウィザードの &#40;データソースビューの選択&#41;](select-data-source-view-data-mining-wizard.md) </span><span class="sxs-lookup"><span data-stu-id="0f310-118">[Select Data Source View &#40;Data Mining Wizard&#41;](select-data-source-view-data-mining-wizard.md) </span></span>  
 [<span data-ttu-id="0f310-119">データマイニング &#40;トレーニングウィザードを指定し&#41;</span><span class="sxs-lookup"><span data-stu-id="0f310-119">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](specify-the-training-data-data-mining-wizard.md)  
  
  
