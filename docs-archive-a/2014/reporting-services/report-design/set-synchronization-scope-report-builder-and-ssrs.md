---
title: 同期スコープの設定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6f4a11e6-6151-47be-a43f-e3dbf6c0e737
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3efbb7774d5116c9b3a18457291434f2a05aac7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631542"
---
# <a name="set-synchronization-scope-report-builder-and-ssrs"></a><span data-ttu-id="a1678-102">同期スコープの設定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="a1678-102">Set Synchronization Scope (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a1678-103">インジケーターは、指定されたスコープ内のインジケーター値の範囲全体を同期することによってデータ値を示します。</span><span class="sxs-lookup"><span data-stu-id="a1678-103">Indicators convey data values by synchronizing across the range of indicator values within a specified scope.</span></span> <span data-ttu-id="a1678-104">既定では、このスコープは、インジケーターを含んでいるテーブルやマトリックスなどのインジケーターの親コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="a1678-104">By default, the scope is the parent container of the indicator such as the table or matrix that contains the indicator.</span></span> <span data-ttu-id="a1678-105">インジケーターの同期は、レポートのレイアウトに応じて変更できます。</span><span class="sxs-lookup"><span data-stu-id="a1678-105">You can change the synchronization of the indicator depending on the layout of your report.</span></span> <span data-ttu-id="a1678-106">たとえば、テーブルなどのデータ領域に行グループがある場合は、インジケーターのスコープとしてそのグループを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1678-106">For example, if a data region such as a table has a row group, you can specify the group as the indicator scope.</span></span> <span data-ttu-id="a1678-107">インジケーターの同期は省略することもできます。</span><span class="sxs-lookup"><span data-stu-id="a1678-107">The indicator can also omit synchronization.</span></span>  
  
 <span data-ttu-id="a1678-108">測定単位などのオプションは、式を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="a1678-108">Options such as measurement units can be set by using expressions.</span></span> <span data-ttu-id="a1678-109">詳細については、「[式 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1678-109">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="a1678-110">レポート内のスコープの説明および設定方法については、「[合計、集計、および組み込みコレクションの式のスコープ &#40;レポート ビルダーおよび SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1678-110">For general information about understanding and setting scope within reports, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-synchronization-scope-of-an-indicator"></a><span data-ttu-id="a1678-111">インジケーターの同期スコープを変更するには</span><span class="sxs-lookup"><span data-stu-id="a1678-111">To change the synchronization scope of an indicator</span></span>  
  
1.  <span data-ttu-id="a1678-112">変更するインジケーターを右クリックし、[**インジケーターのプロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1678-112">Right click the indicator you want to change and click **Indicator Properties**.</span></span>  
  
2.  <span data-ttu-id="a1678-113">左ペインの **[値と状態]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1678-113">Click **Values and States** in the left pane.</span></span>  
  
3.  <span data-ttu-id="a1678-114">**[同期スコープ]** の一覧で、適用するスコープをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a1678-114">In the **Synchronization scope** list, click the scope that you want to apply.</span></span>  
  
     <span data-ttu-id="a1678-115">インジケーターから同期スコープを削除する **[(なし)]** オプションは、常に使用可能です。</span><span class="sxs-lookup"><span data-stu-id="a1678-115">The **(None)** option, which removes synchronization scope from the indicator, is always available.</span></span> <span data-ttu-id="a1678-116">他のオプションはレポートのレイアウトに依存します。</span><span class="sxs-lookup"><span data-stu-id="a1678-116">Other options depend on the layout of your report.</span></span>  
  
     <span data-ttu-id="a1678-117">必要に応じて、 **式** ( *[fx]* ) ボタンをクリックして、スコープを設定する式を編集します。</span><span class="sxs-lookup"><span data-stu-id="a1678-117">Optionally, click the **Expression** (*fx*) button to edit an expression that sets the scope.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1678-118">参照</span><span class="sxs-lookup"><span data-stu-id="a1678-118">See Also</span></span>  
 [<span data-ttu-id="a1678-119">インジケーター &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a1678-119">Indicators &#40;Report Builder and SSRS&#41;</span></span>](indicators-report-builder-and-ssrs.md)  
  
  
