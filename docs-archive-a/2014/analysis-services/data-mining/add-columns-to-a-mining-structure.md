---
title: マイニング構造への列の追加 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- columns [data mining], mining structure columns
- adding columns
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 093d78b36ab3aae6600b890a8137025c9dc9134e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643024"
---
# <a name="add-columns-to-a-mining-structure"></a><span data-ttu-id="93ed6-102">マイニング構造への列の追加</span><span class="sxs-lookup"><span data-stu-id="93ed6-102">Add Columns to a Mining Structure</span></span>
  <span data-ttu-id="93ed6-103">データ マイニング ウィザードで定義したマイニング構造に列を追加するには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のデータ マイニング デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="93ed6-103">Use Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to add columns to a mining structure after you have defined it in the Data Mining Wizard.</span></span> <span data-ttu-id="93ed6-104">マイニング構造の定義に使用したデータ ソース ビューに存在する列はどれでも追加できます。</span><span class="sxs-lookup"><span data-stu-id="93ed6-104">You can add any column that exists in the data source view that was used to define the mining structure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="93ed6-105">マイニング構造に列のコピーを複数追加することもできます。ただし、同じモデル内で 1 つの列のインスタンスが複数にならないようにし、ソースと派生列の間に誤った相関関係ができるのを防ぐ必要があります。</span><span class="sxs-lookup"><span data-stu-id="93ed6-105">You can add multiple copies of columns to a mining structure; however, you should avoid using more than one instance of the column within the same model, to avoid false correlations between the source and the derived column.</span></span>  
  
### <a name="to-add-a-column-to-a-mining-structure"></a><span data-ttu-id="93ed6-106">マイニング構造に列を追加するには</span><span class="sxs-lookup"><span data-stu-id="93ed6-106">To add a column to a mining structure</span></span>  
  
1.  <span data-ttu-id="93ed6-107">データ マイニング デザイナーで **[マイニング構造]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="93ed6-107">Select the **Mining Structure** tab in Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="93ed6-108">マイニング構造を右クリックして **[列の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="93ed6-108">Right-click the mining structure and select **Add a Column**.</span></span>  
  
     <span data-ttu-id="93ed6-109">**[列の選択]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="93ed6-109">The **Select a Column** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="93ed6-110">**[基になるテーブル]** で、列が格納されているデータ ソース ビュー内のテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="93ed6-110">Under **Source table**, select the table in the data source view where the column resides.</span></span>  
  
4.  <span data-ttu-id="93ed6-111">**[基になる列]** で、マイニング構造に追加する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="93ed6-111">Under **Source column**, select the column that you want to add to the mining structure.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="93ed6-112">既に存在する列を追加すると、構造にコピーが追加され、その名前に "1" が付加されます。</span><span class="sxs-lookup"><span data-stu-id="93ed6-112">If you add a column that already exists, a copy will be included in the structure, and the name appended with a "1".</span></span> <span data-ttu-id="93ed6-113">コピーされた列の名前をわかりやすい名前に変更するには、マイニング構造列の **[名前]** プロパティに新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="93ed6-113">You can change the name of the copied column to something more descriptive by typing a new name in the **Name** property of the mining structure column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ed6-114">参照</span><span class="sxs-lookup"><span data-stu-id="93ed6-114">See Also</span></span>  
 [<span data-ttu-id="93ed6-115">マイニング構造のタスクと操作方法</span><span class="sxs-lookup"><span data-stu-id="93ed6-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
  
