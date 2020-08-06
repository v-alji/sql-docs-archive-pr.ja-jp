---
title: 'タスク 3: サプライヤーのナレッジベースに対してデータをクレンジングする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 647c924a-9b91-4294-8d96-e81416e4e90e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 13201a8b904a5fc5232b9fa860710e4e39cce67a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720414"
---
# <a name="task-3-cleansing-data-against-the-suppliers-knowledge-base"></a><span data-ttu-id="f7eae-102">タスク 3: Suppliers ナレッジ ベースに対してデータをクレンジングする</span><span class="sxs-lookup"><span data-stu-id="f7eae-102">Task 3: Cleansing Data against the Suppliers Knowledge Base</span></span>
  <span data-ttu-id="f7eae-103">ここでは、コンピューター支援型のクレンジング プロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7eae-103">In this task, you run the computer-assisted cleansing process.</span></span> <span data-ttu-id="f7eae-104">DQS は、指定されたしきい値に基づいて高度なアルゴリズムと信頼レベルを使用して、選択したナレッジベースに対してデータを分析し、クレンジングします。</span><span class="sxs-lookup"><span data-stu-id="f7eae-104">DQS uses advanced algorithms and confidence levels based on the threshold values specified to analyze the data against the selected knowledge base, and then cleanse it.</span></span> <span data-ttu-id="f7eae-105">詳細については、「 [DQS (内部) ナレッジを使用したデータのクレンジング](https://msdn.microsoft.com/library/hh213061.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7eae-105">See [Cleansing Data Using DQS (Internal) Knowledge](https://msdn.microsoft.com/library/hh213061.aspx) for more details.</span></span>

1.  <span data-ttu-id="f7eae-106">[**開始**] をクリックして、コンピューター支援型のクレンジングプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="f7eae-106">Click **Start** to start the computer-assisted cleansing process.</span></span>

     <span data-ttu-id="f7eae-107">![クレンジング プロセスの [クレンジング] ページ](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "クレンジング プロセスの [クレンジング] ページ")</span><span class="sxs-lookup"><span data-stu-id="f7eae-107">![Cleanse Page of the Cleansing Process](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-01.jpg "Cleanse Page of the Cleansing Process")</span></span>

2.  <span data-ttu-id="f7eae-108">クレンジングプロセスが完了したら、[**プロファイラー** ] タブで**統計**を確認します。ソースの統計情報には、処理されたレコードの数、正しいことが検出されたレコードの数、dqs によって修正されたレコードの数、DQS によって提案された変更を含むレコードの数、および無効なレコードの数が示されます。</span><span class="sxs-lookup"><span data-stu-id="f7eae-108">When the cleansing process is completed, review **statistics** in the **Profiler** tab. The Source Statistics provide the number of records processed, number of records that are found to be correct, number of records that DQS corrects, number of records that have changes suggested by DQS, and the number of records that are invalid.</span></span> <span data-ttu-id="f7eae-109">右側のリスト ボックスには、クレンジング プロセスに含まれる各ドメインの、修正された値、提案された値、値の完全性 (データがどの程度存在するか) と正確性 (データがどの程度意図されたとおりに使用できるか) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7eae-109">In the list box to the right, you can see the corrected values, suggested values, and the completeness (the extent to which the data is present) and accuracy (the extent to which the data can be used for intended purposes) of values for each domain involved in the cleansing process.</span></span>

     <span data-ttu-id="f7eae-110">![クレンジングの結果](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "クレンジングの結果")</span><span class="sxs-lookup"><span data-stu-id="f7eae-110">![Cleansing Results](../../2014/tutorials/media/et-cleansingdataagainstthesupplierkb-02.jpg "Cleansing Results")</span></span>

3.  <span data-ttu-id="f7eae-111">[**次へ**] をクリックし**て、[管理と結果の表示**] ページに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="f7eae-111">Click **Next** to switch to **Manage and View Results** page.</span></span>

## <a name="next-step"></a><span data-ttu-id="f7eae-112">次の手順</span><span class="sxs-lookup"><span data-stu-id="f7eae-112">Next Step</span></span>
 [<span data-ttu-id="f7eae-113">タスク 4: 結果を管理および表示する</span><span class="sxs-lookup"><span data-stu-id="f7eae-113">Task 4: Manaing and Viewing Results</span></span>](../../2014/tutorials/task-4-manaing-and-viewing-results.md)


