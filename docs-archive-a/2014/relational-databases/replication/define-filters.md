---
title: '[フィルターの定義] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5154f002c5a35bc78e2eb6777f2cc7bb3d56b635
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632395"
---
# <a name="define-filters"></a><span data-ttu-id="58ff1-102">[フィルターの定義]</span><span class="sxs-lookup"><span data-stu-id="58ff1-102">Define Filters</span></span>
  <span data-ttu-id="58ff1-103">**[フィルターの定義]** ダイアログ ボックスを使用すると、グリッド内で競合するサブセットを確認するために、データ競合に適用するフィルターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="58ff1-103">The **Define Filters** dialog box allows you to define filters that you then apply to data conflicts to see a subset of the conflicts in the grid.</span></span> <span data-ttu-id="58ff1-104">フィルターを定義するには、 **[演算子]** ボックスで演算子を選択し、値を入力します。</span><span class="sxs-lookup"><span data-stu-id="58ff1-104">To define a filter, choose an operator from the **Operator** drop-down list box and then enter a value.</span></span> <span data-ttu-id="58ff1-105">たとえば、競合で負けたサーバーが **ReplTest1**の競合だけを表示するには、 **[演算子]** ボックスで **[等しい]** を選択し、1 番目の **[値]** 列に「 **ReplTest1** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="58ff1-105">For example, to show only those conflicts in which the conflict loser is server **ReplTest1**, select **Equal to** from the **Operator** drop-down list box and enter **ReplTest1** in the first **Value** column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="58ff1-106">オプション</span><span class="sxs-lookup"><span data-stu-id="58ff1-106">Options</span></span>  
 <span data-ttu-id="58ff1-107">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="58ff1-107">**Operator**</span></span>  
 <span data-ttu-id="58ff1-108">フィルターで使用する演算子 (たとえば、 **[次の値以下]** ) を選択します。</span><span class="sxs-lookup"><span data-stu-id="58ff1-108">Select an operator for the filter, such as **Less than or Equal to**.</span></span>  
  
 <span data-ttu-id="58ff1-109">**Value**</span><span class="sxs-lookup"><span data-stu-id="58ff1-109">**Value**</span></span>  
 <span data-ttu-id="58ff1-110">フィルターの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="58ff1-110">Enter a value for the filter.</span></span> <span data-ttu-id="58ff1-111">ほとんどの演算子は 1 番目の **[値]** 列に値を入力するだけで済みますが、 **[次の値の間]** と **[次の値の範囲外]** の操作は、2 つの **[値]** 列に値を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58ff1-111">Most operators only require a value in the first **Value** column, but the **Between** and **Not Between** operators require a value in both of the **Value** columns.</span></span>  
  
 <span data-ttu-id="58ff1-112">**Clear**</span><span class="sxs-lookup"><span data-stu-id="58ff1-112">**Clear**</span></span>  
 <span data-ttu-id="58ff1-113">このボタンをクリックすると、既に定義されているすべてのフィルターがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="58ff1-113">Click this button to clear all filters that have been previously defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ff1-114">参照</span><span class="sxs-lookup"><span data-stu-id="58ff1-114">See Also</span></span>  
 <span data-ttu-id="58ff1-115">[[Microsoft レプリケーション競合表示モジュール] (マージ レプリケーション)](microsoft-replication-conflict-viewer-merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="58ff1-115">[Microsoft Replication Conflict Viewer &#40;Merge Replication&#41;](microsoft-replication-conflict-viewer-merge-replication.md) </span></span>  
 [<span data-ttu-id="58ff1-116">Microsoft レプリケーション競合表示モジュール (トランザクション レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="58ff1-116">Microsoft Replication Conflict Viewer &#40;Transactional Replication&#41;</span></span>](microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
