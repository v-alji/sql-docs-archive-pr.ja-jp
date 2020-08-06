---
title: 予測クエリを手動で編集する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
author: minewiskan
ms.author: owend
ms.openlocfilehash: e887e935dafcd2428859fd959cb7bc64650c660d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645916"
---
# <a name="manually-edit-a-prediction-query"></a><span data-ttu-id="d6263-102">手動での予測クエリの編集</span><span class="sxs-lookup"><span data-stu-id="d6263-102">Manually Edit a Prediction Query</span></span>
  <span data-ttu-id="d6263-103">予測クエリ ビルダーでクエリのデザインを終えたら、データ マイニング デザイナーの **[マイニング モデル予測]** タブにあるクエリ テキスト ビューに切り替えて、クエリを変更できます。</span><span class="sxs-lookup"><span data-stu-id="d6263-103">After you have designed a query by using the Prediction Query Builder, you can modify the query by switching to Query Text view on the **Mining Model Prediction** tab of Data Mining Designer.</span></span> <span data-ttu-id="d6263-104">画面の下部に、クエリ ビルダーによって作成されたクエリを含んでいるテキスト エディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6263-104">A text editor appears at the bottom of the screen to display the query that the query builder created.</span></span>  
  
 <span data-ttu-id="d6263-105">クエリ テキスト ビューに切り替えると、クエリへの追加を行う場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="d6263-105">Switching to Query Text view is useful for making additions to the query.</span></span> <span data-ttu-id="d6263-106">たとえば、WHERE 句や ORDER BY 句を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d6263-106">For example, you can add a WHERE clause or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="d6263-107">予測クエリ ビルダーのグリッドを使用してオブジェクトおよび列の名前を挿入し、個々の予測関数の構文を設定してから、手動編集モードに切り替えて、パラメーター値を変更します。</span><span class="sxs-lookup"><span data-stu-id="d6263-107">Use the grid in the Prediction Query Builder to insert the names of objects and columns and set up the syntax for individual prediction functions, and then switch to manual editing mode to change parameter values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d6263-108">**クエリ テキスト** ビューから **デザイン** ビューに戻ると、 **クエリ テキスト** ビューで行った変更は失われます。</span><span class="sxs-lookup"><span data-stu-id="d6263-108">If you switch back to **Design** view from **Query Text** view, any changes that you made in **Query Text** view will be lost.</span></span>  
  
### <a name="modify-a-query"></a><span data-ttu-id="d6263-109">クエリの変更</span><span class="sxs-lookup"><span data-stu-id="d6263-109">Modify a query</span></span>  
  
1.  <span data-ttu-id="d6263-110">**のデータ マイニング デザイナーにある** [マイニング モデル予測] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブで、 **[SQL]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6263-110">On the **Mining Model Prediction** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click **SQL**.</span></span>  
  
     <span data-ttu-id="d6263-111">画面の下部にあるグリッドが、クエリを含んでいるテキスト エディターに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="d6263-111">The grid at the bottom of the screen is replaced by a text editor that contains the query.</span></span> <span data-ttu-id="d6263-112">このエディターでクエリの変更を入力できます。</span><span class="sxs-lookup"><span data-stu-id="d6263-112">You can type changes to the query in this editor.</span></span>  
  
2.  <span data-ttu-id="d6263-113">クエリを実行するには、 **[マイニング モデル]** メニューの **[結果]** をクリックするか、クエリ結果に切り替えるボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6263-113">To run the query, on the **Mining Model** menu, select **Result**, or click the button to switch to query results.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d6263-114">作成したクエリが無効であれば、[結果] ウィンドウにはエラーも結果も表示されません。</span><span class="sxs-lookup"><span data-stu-id="d6263-114">If the query that you have created is invalid, the Results window does not display an error and does not display any results.</span></span> <span data-ttu-id="d6263-115">**[デザイン]** ボタンをクリックするか、 **[マイニング モデル]** メニューの **[デザイン]** または **[クエリ]** をクリックして問題を修正し、再度クエリを実行してください。</span><span class="sxs-lookup"><span data-stu-id="d6263-115">Click the **Design** button, or select **Design** or **Query** from the **Mining Model** menu to correct the problem and run the query again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6263-116">参照</span><span class="sxs-lookup"><span data-stu-id="d6263-116">See Also</span></span>  
 <span data-ttu-id="d6263-117">[データマイニングクエリ](data-mining-queries.md) </span><span class="sxs-lookup"><span data-stu-id="d6263-117">[Data Mining Queries](data-mining-queries.md) </span></span>  
 <span data-ttu-id="d6263-118">[予測クエリビルダー &#40;データマイニング&#41;](../prediction-query-builder-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="d6263-118">[Prediction Query Builder &#40;Data Mining&#41;](../prediction-query-builder-data-mining.md) </span></span>  
 [<span data-ttu-id="d6263-119">レッスン 6: 予測の作成と操作 &#40;基本的なデータ マイニング チュートリアル&#41;</span><span class="sxs-lookup"><span data-stu-id="d6263-119">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
  
