---
title: 'タスク 5: 用語ベースのリレーションシップを設定する |Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6569d512-637d-4f7b-82e1-1e8582278b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1589ec5843053baa6c42a0b9b0dec019c887da9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720403"
---
# <a name="task-5-setting-term-based-relationships"></a><span data-ttu-id="89f7c-102">タスク 5: 用語ベースのリレーションを設定する</span><span class="sxs-lookup"><span data-stu-id="89f7c-102">Task 5: Setting Term Based Relationships</span></span>
  <span data-ttu-id="89f7c-103">このタスクでは、 **Supplier Name**ドメインの値に対して用語ベースのリレーションをいくつか定義します。</span><span class="sxs-lookup"><span data-stu-id="89f7c-103">In this task, you define a few term-based relations for values for the **Supplier Name** domain.</span></span> <span data-ttu-id="89f7c-104">用語ベースのリレーションを使用すると、ドメインの値の一部になっている用語を修正できます。</span><span class="sxs-lookup"><span data-stu-id="89f7c-104">A term-based relation enables you to make a correction to a term that is part of a value in a domain.</span></span> <span data-ttu-id="89f7c-105">用語ベースのリレーションでは、共通する部分のスペルを除いても同一である複数の値は同一のシノニムと見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="89f7c-105">It enables multiple values that are identical except for the spelling of a common part of them to be considered identical synonyms.</span></span> <span data-ttu-id="89f7c-106">たとえば、 **Inc**は、を**組み込む**ように修正できます。</span><span class="sxs-lookup"><span data-stu-id="89f7c-106">For example, **Inc.** can be corrected to **Incorporated**.</span></span> <span data-ttu-id="89f7c-107">DQS では、ナレッジの検出、クレンジング、または照合プロセスでこれらのリレーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="89f7c-107">DQS uses these relations in the knowledge discovery, cleansing, or matching processes.</span></span> <span data-ttu-id="89f7c-108">詳細については[、「用語ベースのリレーションを作成する](https://msdn.microsoft.com/library/hh510404.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89f7c-108">See [Create Term-based Relations](https://msdn.microsoft.com/library/hh510404.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="89f7c-109">[**ドメイン] ボックスの一覧**で [ **Supplier Name** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="89f7c-109">Select **Supplier Name** in the **Domain list**.</span></span>  
  
2.  <span data-ttu-id="89f7c-110">右側のペインの [**用語ベースの関係**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="89f7c-110">Switch to the **Term-Based Relationships** tab in the right pane.</span></span>  
  
3.  <span data-ttu-id="89f7c-111">ツールバーの [**新しいリレーションシップの追加**] ボタンをクリックして、テーブルにリレーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="89f7c-111">Click **Add new relation** button on the toolbar to add a relation to the table.</span></span>  
  
4.  <span data-ttu-id="89f7c-112">[**値**] フィールドに「 **Co** 」と入力し、[**宛先**] フィールドに「 **Company** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="89f7c-112">Type **Co.** for the **Value** field and **Company** for the **Correct To** field.</span></span>  
  
5.  <span data-ttu-id="89f7c-113">次の値ごとに、上記 2 つの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="89f7c-113">Repeat the previous two steps for the following values:</span></span>  
  
    |<span data-ttu-id="89f7c-114">値</span><span class="sxs-lookup"><span data-stu-id="89f7c-114">Value</span></span>|<span data-ttu-id="89f7c-115">次に修正</span><span class="sxs-lookup"><span data-stu-id="89f7c-115">Correct To</span></span>|  
    |-----------|----------------|  
    |<span data-ttu-id="89f7c-116">Corp.</span><span class="sxs-lookup"><span data-stu-id="89f7c-116">Corp.</span></span>|<span data-ttu-id="89f7c-117">Corporation</span><span class="sxs-lookup"><span data-stu-id="89f7c-117">Corporation</span></span>|  
    |<span data-ttu-id="89f7c-118">Inc.</span><span class="sxs-lookup"><span data-stu-id="89f7c-118">Inc.</span></span>|<span data-ttu-id="89f7c-119">Incorporated</span><span class="sxs-lookup"><span data-stu-id="89f7c-119">Incorporated</span></span>|  
  
     <span data-ttu-id="89f7c-120">![用語ベースのリレーション](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "用語ベースのリレーション")</span><span class="sxs-lookup"><span data-stu-id="89f7c-120">![Term Based Relations](../../2014/tutorials/media/et-settingtermbasedrelations.jpg "Term Based Relations")</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="89f7c-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="89f7c-121">Next Step</span></span>  
 [<span data-ttu-id="89f7c-122">タスク 6: シノニムを設定する</span><span class="sxs-lookup"><span data-stu-id="89f7c-122">Task 6: Setting Synonyms</span></span>](../../2014/tutorials/task-6-setting-synonyms.md)  
  
  
