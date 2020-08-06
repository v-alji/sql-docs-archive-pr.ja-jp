---
title: '[カスタマイズ] ([コマンド] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.vs.customizecom.f1
ms.assetid: c8965f2c-51d9-437d-a6f3-8ac2075ede6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 684fb9a6266fafae00b9881eb64a3642e6c98c79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717210"
---
# <a name="customize-commands-page"></a><span data-ttu-id="affdb-102">[カスタマイズ] ([コマンド] ページ)</span><span class="sxs-lookup"><span data-stu-id="affdb-102">Customize (Commands Page)</span></span>
  <span data-ttu-id="affdb-103">このダイアログ ボックスでは、ツール バーおよびメニューのコマンドを追加したり、削除したりできます。また、ツール バー ボタンやメニュー コマンドに使用されているイメージを変更できます。</span><span class="sxs-lookup"><span data-stu-id="affdb-103">This dialog box enables you to add and remove commands on toolbars and menus as well as change the images used for toolbar buttons or menu commands.</span></span> <span data-ttu-id="affdb-104">**[コマンド]** ページにアクセスするには、 **[ツール]** メニューの **[カスタマイズ]** をクリックし、次に **[コマンド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="affdb-104">You can access the **Commands** page by clicking **Customize** on the **Tools** menu and then clicking **Commands**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="affdb-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="affdb-105">UI element list</span></span>  
 <span data-ttu-id="affdb-106">**Categories (カテゴリ)**</span><span class="sxs-lookup"><span data-stu-id="affdb-106">**Categories**</span></span>  
 <span data-ttu-id="affdb-107">**[コマンド]** リスト ボックスに表示されるコマンドのセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="affdb-107">Specifies the set of commands that are displayed in the **Commands** list box.</span></span> <span data-ttu-id="affdb-108">コマンドのカテゴリは、現在の環境がサポートしているツールおよびデザイナーによって提供されたメニュー タイトルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="affdb-108">The categories of commands are based on menu titles provided by the tools and designers that the environment is currently supporting.</span></span> <span data-ttu-id="affdb-109">このタイトルの一覧は動的であるため、カテゴリの順序とメニュー タイトルは、ツールとデザイナーおよび実行されたカスタマイズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="affdb-109">This list of titles is dynamic so that the order of categories and the menu titles change, depending on the tools and the designer, as well as any customizations made to them.</span></span> <span data-ttu-id="affdb-110">したがって、異なるデザイナーの 2 つのメニューが同じ名前を持つ可能性があります。その場合、同じタイトルが 2 回表示されても別のコマンド セットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="affdb-110">Therefore, it is possible for two menus from different designers to have the same name, so the same title can appear twice but offer different command sets.</span></span>  
  
 <span data-ttu-id="affdb-111">**コマンド**</span><span class="sxs-lookup"><span data-stu-id="affdb-111">**Commands**</span></span>  
 <span data-ttu-id="affdb-112">選択されているカテゴリに基づいて、コマンドおよびコマンド イメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="affdb-112">Displays the commands and command images based on the category you selected.</span></span> <span data-ttu-id="affdb-113">コマンドをカスタマイズするツール バーにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="affdb-113">You can drag a command onto the toolbar you want to customize.</span></span>  
  
 <span data-ttu-id="affdb-114">**[選択したボタンの編集]**</span><span class="sxs-lookup"><span data-stu-id="affdb-114">**Modify Selection**</span></span>  
 <span data-ttu-id="affdb-115">ツール バーのボタンの表示をカスタマイズするために使用できるコマンドの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="affdb-115">Displays a list of commands you can use to customize the display of the button on the toolbar.</span></span> <span data-ttu-id="affdb-116">たとえば、イメージやアクセス キーを変更したり、コマンドのイメージの代わりにテキストを表示するかどうかを指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="affdb-116">For example, you can change the image or accelerator keys, as well as specify whether to display text instead of an image for the command.</span></span> <span data-ttu-id="affdb-117">このボタンは、カスタマイズするツール バーでコマンド ボタンを選択すると、使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="affdb-117">This button is available after you select a command button on a toolbar you want to customize.</span></span>  
  
 <span data-ttu-id="affdb-118">**[コマンドの配置の変更]**</span><span class="sxs-lookup"><span data-stu-id="affdb-118">**Rearrange Commands**</span></span>  
 <span data-ttu-id="affdb-119">**[コマンドの配置の変更]** ダイアログ ボックスを表示します。このダイアログ ボックスで、メニューまたはツール バーのコマンドの名前の変更、並べ替え、追加、および削除を行ったり、ボタンおよびコマンドのイメージを変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="affdb-119">Displays the **Rearrange Commands** dialog box, which allows you to rename, reorder, add, and remove commands on menus and toolbars as well as change button and command images.</span></span>  
  
 <span data-ttu-id="affdb-120">**[キーボード]**</span><span class="sxs-lookup"><span data-stu-id="affdb-120">**Keyboard**</span></span>  
 <span data-ttu-id="affdb-121">コマンドに対するショートカット キーの組み合わせを指定できるように、 **[オプション]** ダイアログ ボックスの **[キーボード]** ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="affdb-121">Displays the **Keyboard** page of the **Options** dialog box so you can specify shortcut key combinations for commands.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="affdb-122">参照</span><span class="sxs-lookup"><span data-stu-id="affdb-122">See Also</span></span>  
 [<span data-ttu-id="affdb-123">メニューとショートカット キーのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="affdb-123">Customize Menus and Shortcut Keys</span></span>](../customize-menus-and-shortcut-keys.md)  
