---
title: 'タスク 3: Excel ファイルからドメイン値をインポートする |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 242e8309-1195-495b-9cd5-aa127748c185
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 707a3925bb6d0014e2a1248f904123b076024e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632848"
---
# <a name="task-3-importing-domain-values-from-an-excel-file"></a><span data-ttu-id="c2838-102">タスク 3:Excel ファイルからドメイン値をインポートする</span><span class="sxs-lookup"><span data-stu-id="c2838-102">Task 3: Importing Domain Values from an Excel File</span></span>

  <span data-ttu-id="c2838-103">ここでは、Excel ファイルのワークシートから **State** ドメインの値をインポートします。</span><span class="sxs-lookup"><span data-stu-id="c2838-103">In this task, you import values for the **State** domain from a worksheet of an Excel file.</span></span>

1.  <span data-ttu-id="c2838-104">**[ドメイン リスト]** から **State**ドメインをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2838-104">Click **State** domain in the **Domain list**.</span></span>

2.  <span data-ttu-id="c2838-105">右側のペインで、 **[ドメイン値]** タブがアクティブになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c2838-105">Ensure that the **Domain Values** tab is active in the right pane.</span></span>

3.  <span data-ttu-id="c2838-106">右側のペインのツール バーで、 **[値をインポートします]** の横にある **下矢印** をクリックし、 **[Excel から有効な値をインポートします]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2838-106">In the right pane, from the toolbar, click **down arrow** next to the **Import Values** button, and click **Import Valid Values from Excel**.</span></span>

     <span data-ttu-id="c2838-107">![[Excel から有効な値をインポートします] メニュー](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "[Excel から有効な値をインポートします] メニュー")</span><span class="sxs-lookup"><span data-stu-id="c2838-107">![Import Valid Values from Excel Menu](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "Import Valid Values from Excel Menu")</span></span>

4.  <span data-ttu-id="c2838-108">**[参照]** をクリックし、 **Suppliers.xls**を選択して、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2838-108">Click **Browse**, select **Suppliers.xls**, and click **Open**.</span></span>

5.  <span data-ttu-id="c2838-109">**[ワークシート]** に **StatesToImport$** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2838-109">Select **StatesToImport$** for the **Worksheet**.</span></span>

     <span data-ttu-id="c2838-110">![[ドメイン値のインポート] ダイアログ ボックス](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "[ドメイン値のインポート] ダイアログ ボックス")</span><span class="sxs-lookup"><span data-stu-id="c2838-110">![Import Domain Values Dialog Box](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "Import Domain Values Dialog Box")</span></span>

6.  <span data-ttu-id="c2838-111">**[OK]** をクリックして **[ドメイン値のインポート]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c2838-111">Click **OK** to close the **Import Domain Values** dialog box.</span></span> <span data-ttu-id="c2838-112">インポートしたすべての州の名前が一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2838-112">You should see all the names of states you imported in the list.</span></span> <span data-ttu-id="c2838-113">インポート後は、 **[新規のみ表示]** オプションが自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="c2838-113">Notice that **Show Only New** option is automatically selected after importing.</span></span> <span data-ttu-id="c2838-114">値をインポートするときに、一覧に古い値が表示されない場合は、インポート後にこのオプションが自動的に有効になるためです。</span><span class="sxs-lookup"><span data-stu-id="c2838-114">When you import values and you don't see the old values in the list, it is because this option is automatically enabled after importing.</span></span> <span data-ttu-id="c2838-115">すべての値を表示するには、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="c2838-115">To see all the values, clear the check box.</span></span> <span data-ttu-id="c2838-116">同じ値のセットをもう一度インポートすると、これらはドメインに既に存在するので、値はインポートされません。</span><span class="sxs-lookup"><span data-stu-id="c2838-116">If you import the same set of values again, none of the values are imported as they already exist in the domain.</span></span>

     <span data-ttu-id="c2838-117">![ドメイン値の [新規のみ表示] チェック ボックス](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "ドメイン値の [新規のみ表示] チェック ボックス")</span><span class="sxs-lookup"><span data-stu-id="c2838-117">![Show Only New Checkbox on Domain Values](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "Show Only New Checkbox on Domain Values")</span></span>

## <a name="next-step"></a><span data-ttu-id="c2838-118">次の手順</span><span class="sxs-lookup"><span data-stu-id="c2838-118">Next Step</span></span>
 [<span data-ttu-id="c2838-119">タスク 4: ドメイン ルールを設定する</span><span class="sxs-lookup"><span data-stu-id="c2838-119">Task 4: Setting Domain Rules</span></span>](../../2014/tutorials/task-4-setting-domain-rules.md)


