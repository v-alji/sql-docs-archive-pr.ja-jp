---
title: '[ツールボックス アイテムの選択] ([メンテナンス タスク] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vs.chooseitems.maintenance_tasks
- VS.ToolboxPages.Maintenance_Tasks
helpviewer_keywords:
- Customize Toolbox dialog box
ms.assetid: b92c9054-7479-45d8-a54c-c1bb6699bdb3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28c90cd0abc76a7ae721ff0580aa119c3c5639b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717211"
---
# <a name="choose-toolbox-items-maintenance-tasks-page"></a><span data-ttu-id="82230-102">[ツールボックス アイテムの選択] ([メンテナンス タスク] ページ)</span><span class="sxs-lookup"><span data-stu-id="82230-102">Choose Toolbox Items (Maintenance Tasks Page)</span></span>
  <span data-ttu-id="82230-103">**[ツールボックス アイテムの選択]** ダイアログ ボックスのこのタブには、コンピューターに登録されているメンテナンス タスク コンポーネントがすべて一覧表示され、ツールボックスに表示されているメンテナンス タスクを変更できます。</span><span class="sxs-lookup"><span data-stu-id="82230-103">This tab of the **Customize Toolbox** dialog box displays a list of all maintenancetask components registered on your computer and makes it possible for you to change the ones that are displayed in the Toolbox.</span></span> <span data-ttu-id="82230-104">**[ツールボックス アイテムの選択]** ダイアログ ボックスは、 **[ツール]** メニューから開けます。</span><span class="sxs-lookup"><span data-stu-id="82230-104">You can open the **Customize Toolbox** dialog box from the **Tools** menu.</span></span> <span data-ttu-id="82230-105">コンポーネントの一覧を並べ替えるには、列見出しを選択します。</span><span class="sxs-lookup"><span data-stu-id="82230-105">To sort the list of components, select any column heading.</span></span>  
  
## <a name="options"></a><span data-ttu-id="82230-106">Options</span><span class="sxs-lookup"><span data-stu-id="82230-106">Options</span></span>  
 <span data-ttu-id="82230-107">**[メンテナンス タスク]** タブには次の列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="82230-107">The **Maintenance Tasks** tab includes the following columns of information.</span></span>  
  
 <span data-ttu-id="82230-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="82230-108">**Name**</span></span>  
 <span data-ttu-id="82230-109">使用可能なコンポーネントの名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="82230-109">Displays the names of available components.</span></span> <span data-ttu-id="82230-110">それぞれの名前の前に、チェック ボックスがあります。</span><span class="sxs-lookup"><span data-stu-id="82230-110">Preceding each name is a check box.</span></span> <span data-ttu-id="82230-111">このチェック ボックスがオンの場合、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] がコンピューターのレジストリでそのコンポーネントのエントリを検出したことを示します。</span><span class="sxs-lookup"><span data-stu-id="82230-111">If selected, a check box indicates that [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] has found an entry for the component in your computer's registry.</span></span> <span data-ttu-id="82230-112">そのコンポーネントはアクティブな **[ツールボックス]** タブに既に表示されているか、 **[OK]** をクリックすると追加されます。</span><span class="sxs-lookup"><span data-stu-id="82230-112">The component is either already displayed on the active **Toolbox** tab, or it will be added to it when you click **OK**.</span></span> <span data-ttu-id="82230-113">このチェック ボックスがオフの場合、コンポーネントが現在 **[ツールボックス]** に表示されていないか、 **[OK]** をクリックすると **[ツールボックス]** から削除されます。</span><span class="sxs-lookup"><span data-stu-id="82230-113">If cleared, a check box indicates that the component is not currently displayed in the **Toolbox**, or that it will be removed from the **Toolbox** when you click **OK**.</span></span>  
  
 <span data-ttu-id="82230-114">**パス**</span><span class="sxs-lookup"><span data-stu-id="82230-114">**Path**</span></span>  
 <span data-ttu-id="82230-115">コンポーネントの完全なパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="82230-115">Displays the full path to the component.</span></span> <span data-ttu-id="82230-116">製品に付属していた既定のコンポーネントを特定するには、この列を使用して並べ替えた後、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio のインストール パスを探します。</span><span class="sxs-lookup"><span data-stu-id="82230-116">To identify the default components that shipped with the product, sort on this column and then locate those stored on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio installation path.</span></span>  
  
 <span data-ttu-id="82230-117">**[最終更新]**</span><span class="sxs-lookup"><span data-stu-id="82230-117">**Last Modified**</span></span>  
 <span data-ttu-id="82230-118">コンポーネントが最後に更新された日付が表示されます。</span><span class="sxs-lookup"><span data-stu-id="82230-118">Displays the date when the component was last modified.</span></span>  
  
 <span data-ttu-id="82230-119">名前をクリックすると、 **[言語]** ボックスおよび **[バージョン]** ボックスにコンポーネントの属性とアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="82230-119">Click on a name to show the attributes of the component in the **Language** and **Version** boxes, along with the icon.</span></span>  
  
## <a name="options"></a><span data-ttu-id="82230-120">Options</span><span class="sxs-lookup"><span data-stu-id="82230-120">Options</span></span>  
 <span data-ttu-id="82230-121">**Language**</span><span class="sxs-lookup"><span data-stu-id="82230-121">**Language**</span></span>  
 <span data-ttu-id="82230-122">コンポーネントの言語です。</span><span class="sxs-lookup"><span data-stu-id="82230-122">The language of the component.</span></span>  
  
 <span data-ttu-id="82230-123">**Version**</span><span class="sxs-lookup"><span data-stu-id="82230-123">**Version**</span></span>  
 <span data-ttu-id="82230-124">コンポーネントのバージョンです。</span><span class="sxs-lookup"><span data-stu-id="82230-124">The version of the component.</span></span>  
  
  
