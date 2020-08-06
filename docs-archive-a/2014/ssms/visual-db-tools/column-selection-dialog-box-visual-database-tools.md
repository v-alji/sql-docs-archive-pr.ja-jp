---
title: '[列の選択] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.columnselection
- vdtsql.chm:65548
ms.assetid: 479bae2c-fee0-4215-b424-1ab779a7e5ca
author: stevestein
ms.author: sstein
ms.openlocfilehash: da3effa33704b796dc2597512be7780594706423
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711493"
---
# <a name="column-selection-dialog-box-visual-database-tools"></a><span data-ttu-id="1dce5-102">[列の選択] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1dce5-102">Column Selection Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="1dce5-103">データベース ダイアグラムのテーブルのカスタム ビューを変更するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-103">Lets you change the Custom view for tables in the database diagram.</span></span> <span data-ttu-id="1dce5-104">カスタム ビューには、ユーザーによって指定された列プロパティだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1dce5-104">Custom view shows only the column properties identified by the user.</span></span>  
  
 <span data-ttu-id="1dce5-105">このダイアログ ボックスは、テーブルを右クリックしてショートカット メニューの **[カスタム ビューの変更]** をクリックしたときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1dce5-105">This dialog box appears when you right-click a table and then choose **Modify Custom View** from the shortcut menu.</span></span>  
  
## <a name="options"></a><span data-ttu-id="1dce5-106">オプション</span><span class="sxs-lookup"><span data-stu-id="1dce5-106">Options</span></span>  
 <span data-ttu-id="1dce5-107">**使用可能な列**</span><span class="sxs-lookup"><span data-stu-id="1dce5-107">**Available columns**</span></span>  
 <span data-ttu-id="1dce5-108">選択したデータベース テーブル内にあるすべての列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-108">Lists all columns existing in the selected database table.</span></span> <span data-ttu-id="1dce5-109">ここに表示される列は、データベース テーブルのプロパティおよびデータベースのタイプによって異なります。</span><span class="sxs-lookup"><span data-stu-id="1dce5-109">The columns listed here depend on the properties of the database table and the type of database.</span></span> <span data-ttu-id="1dce5-110">表示する列を強調表示し、矢印ボタンを使用して列を **[選択した列]** ボックスに移動します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-110">Highlight the desired column and use the arrow buttons to move the columns to the **Selected columns** box.</span></span>  
  
 <span data-ttu-id="1dce5-111">**[選択した列]**</span><span class="sxs-lookup"><span data-stu-id="1dce5-111">**Selected columns**</span></span>  
 <span data-ttu-id="1dce5-112">カスタム ビューに対して現在定義されている列プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-112">Displays the column properties currently defined for the Custom view.</span></span> <span data-ttu-id="1dce5-113">矢印ボタンを使用して、[選択した列] ボックスの一覧に列プロパティを追加したり、一覧から列プロパティを削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="1dce5-113">Use the arrow buttons to add and remove column properties to the Selected Columns list.</span></span>  
  
 <span data-ttu-id="1dce5-114">**矢印コントロール**</span><span class="sxs-lookup"><span data-stu-id="1dce5-114">**Arrow controls**</span></span>  
 <span data-ttu-id="1dce5-115">上矢印および下矢印ボタンを使用して、 **[選択した列]** ボックスの一覧内で強調表示された列を上または下に移動します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-115">Use the up and down arrow buttons to move highlighted columns up or down in the **Selected columns** list.</span></span>  
  
 <span data-ttu-id="1dce5-116">1 つまたはすべてのプロパティをカスタム ビューに追加するには、> および >> 矢印を使用します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-116">Use the > and >> arrows to add one or all of the properties to the custom view.</span></span>  
  
 <span data-ttu-id="1dce5-117">1 つまたはすべてのプロパティをカスタム ビューから削除するには、< および << 矢印を使用します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-117">Use the < and << arrows to remove one or all of the properties from the custom view.</span></span>  
  
 <span data-ttu-id="1dce5-118">**[既定値として保存]**</span><span class="sxs-lookup"><span data-stu-id="1dce5-118">**Save as default**</span></span>  
 <span data-ttu-id="1dce5-119">既定のカスタム ビューを、このダイアログ ボックスで選択した列で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1dce5-119">Replaces the default Custom view with the columns selected in this dialog box.</span></span> <span data-ttu-id="1dce5-120">このオプションを選択しない場合、ダイアログ ボックスで指定した列の選択内容は、データベース ダイアグラムで選択されているテーブルにだけ適用されます。</span><span class="sxs-lookup"><span data-stu-id="1dce5-120">If not selected, the column selection specified in the dialog box will be applied only to the selected table in the database diagram.</span></span>  
  
 <span data-ttu-id="1dce5-121">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="1dce5-121">**OK**</span></span>  
 <span data-ttu-id="1dce5-122">カスタム ビューを保存します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-122">Saves the Custom view.</span></span>  
  
 <span data-ttu-id="1dce5-123">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="1dce5-123">**Cancel**</span></span>  
 <span data-ttu-id="1dce5-124">カスタム ビューの変更を取り消します。</span><span class="sxs-lookup"><span data-stu-id="1dce5-124">Cancels the modification of Custom view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dce5-125">参照</span><span class="sxs-lookup"><span data-stu-id="1dce5-125">See Also</span></span>  
 <span data-ttu-id="1dce5-126">[データベースダイアグラムの使用 &#40;Visual Database Tools&#41;](visual-database-tools.md) </span><span class="sxs-lookup"><span data-stu-id="1dce5-126">[Work with Database Diagrams &#40;Visual Database Tools&#41;](visual-database-tools.md) </span></span>  
 [<span data-ttu-id="1dce5-127">ダイアグラムに表示される情報の量のカスタマイズ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="1dce5-127">Customize the Amount of Information Displayed in Diagrams &#40;Visual Database Tools&#41;</span></span>](customize-the-amount-of-information-displayed-in-diagrams-visual-database-tools.md)  
  
  
