---
title: '[新しいリンクレポート] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fefb46e8-6901-4d50-a3f8-7c49ad72e7b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 61138e51cfd9bb6e1ee124dd4aa3bc224d8aebcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643201"
---
# <a name="new-linked-report-page-report-manager"></a><span data-ttu-id="c74e0-102">[新しいリンク レポート] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="c74e0-102">New Linked Report Page (Report Manager)</span></span>
  <span data-ttu-id="c74e0-103">[新しいリンク レポート] ページではリンク レポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-103">Use the New Linked Report page to create a linked report.</span></span> <span data-ttu-id="c74e0-104">リンク レポートは、独自の設定やプロパティが含まれているレポートですが、別のレポートのレポート定義にリンクしています。</span><span class="sxs-lookup"><span data-stu-id="c74e0-104">A linked report is a report with settings and properties of its own, but links to the report definition of another report.</span></span> <span data-ttu-id="c74e0-105">リンク レポートは、特定のグループまたはユーザーによって異なる基本レポート (たとえば、パラメーターとして指定された地域コードに基づいて別のデータを返す地域レポート) がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-105">Linked reports are useful when you have a base report that you want to vary for specific groups or users; for example, a regional report that returns different data based on a regional code that you specify as a parameter.</span></span> <span data-ttu-id="c74e0-106">通常、リンク レポートは、各レポート インスタンスに異なるパラメーター値を設定して保存する場合に、パラメーター化されたレポートから作成します。</span><span class="sxs-lookup"><span data-stu-id="c74e0-106">A linked report is typically created from a parameterized report when you want to vary and then save different parameter values with each report instance.</span></span> <span data-ttu-id="c74e0-107">ただし、ユーザーがアクセスできる任意のレポートからリンク レポートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-107">However, you can create a linked report from any report to which you have access.</span></span>  
  
 <span data-ttu-id="c74e0-108">リンク レポートは、独自の名前、説明、場所、パラメーター プロパティ、レポート実行プロパティ、レポート ヒストリ プロパティ、権限、およびサブスクリプションを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-108">A linked report can have its own name, description, location, parameter properties, report execution properties, report history properties, permissions, and subscriptions.</span></span> <span data-ttu-id="c74e0-109">ただし、リンク レポートでは、レポート定義を提供する基本レポートのデータ ソース プロパティとレイアウトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c74e0-109">However, a linked report must use the data source properties and layout of the base report that provides the report definition.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="c74e0-110">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="c74e0-110">Navigation</span></span>  
 <span data-ttu-id="c74e0-111">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c74e0-111">Use the following procedures to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-linked-report-page-from-the-contents-page"></a><span data-ttu-id="c74e0-112">[コンテンツ] ページから [新しいリンク レポート] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="c74e0-112">To open the New Linked Report page from the Contents page</span></span>  
  
1.  <span data-ttu-id="c74e0-113">レポート マネージャーを開き、リンク レポートを作成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="c74e0-113">Open Report Manager, and locate a report for which you want to create a linked report.</span></span>  
  
2.  <span data-ttu-id="c74e0-114">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c74e0-114">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="c74e0-115">ドロップダウン メニューの **[リンク レポートの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c74e0-115">In the drop-down menu, click **Create Linked Report**.</span></span>  
  
###### <a name="to-open-the-new-linked-report-page-from-the-general-properties-page-of-a-report"></a><span data-ttu-id="c74e0-116">レポートの [全般] プロパティ ページから [新しいリンク レポート] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="c74e0-116">To open the New Linked Report page from the General properties page of a report</span></span>  
  
1.  <span data-ttu-id="c74e0-117">レポート マネージャーを開き、リンク レポートを作成するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="c74e0-117">Open Report Manager, and locate a report for which you want to create a linked report.</span></span>  
  
2.  <span data-ttu-id="c74e0-118">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c74e0-118">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="c74e0-119">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c74e0-119">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="c74e0-120">この操作により、レポートの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-120">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="c74e0-121">アイテムのツール バーの **[リンク レポートの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c74e0-121">In the item toolbar, click **Create Linked Report**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c74e0-122">Options</span><span class="sxs-lookup"><span data-stu-id="c74e0-122">Options</span></span>  
 <span data-ttu-id="c74e0-123">**名前**</span><span class="sxs-lookup"><span data-stu-id="c74e0-123">**Name**</span></span>  
 <span data-ttu-id="c74e0-124">リンク レポートの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c74e0-124">Specify the name of the linked report.</span></span> <span data-ttu-id="c74e0-125">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c74e0-125">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="c74e0-126">また、スペースおよび特定の記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-126">It can also include spaces and certain symbols.</span></span> <span data-ttu-id="c74e0-127">ただし、名前を指定する場合は、次の文字は使用できません。; ?</span><span class="sxs-lookup"><span data-stu-id="c74e0-127">However, you must not use the characters ; ?</span></span> <span data-ttu-id="c74e0-128">: \@ & = +、$/\* \< > |"またはの名前を指定する場合。</span><span class="sxs-lookup"><span data-stu-id="c74e0-128">: \@ & = + , $ / \* \< > | " or / when specifying a name.</span></span>  
  
 <span data-ttu-id="c74e0-129">**説明**</span><span class="sxs-lookup"><span data-stu-id="c74e0-129">**Description**</span></span>  
 <span data-ttu-id="c74e0-130">レポートの内容の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="c74e0-130">Type a description of the report contents.</span></span> <span data-ttu-id="c74e0-131">この説明は、レポートへのアクセス権を持っているユーザーの [コンテンツ] ページに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-131">This description appears in the Contents page to users who have permission to access the report.</span></span>  
  
 <span data-ttu-id="c74e0-132">**場所**</span><span class="sxs-lookup"><span data-stu-id="c74e0-132">**Location**</span></span>  
 <span data-ttu-id="c74e0-133">レポートを含むフォルダーのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c74e0-133">Specify the folder path that contains the report.</span></span> <span data-ttu-id="c74e0-134">既定では、基本レポートの兄弟としてリンク レポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-134">By default, linked reports are created as siblings to the base report.</span></span> <span data-ttu-id="c74e0-135">**[場所の変更]** をクリックすると、別のフォルダーにリンク レポートを格納できます。</span><span class="sxs-lookup"><span data-stu-id="c74e0-135">Click **Change Location** to put the linked report in a different folder.</span></span>  
  
 <span data-ttu-id="c74e0-136">**[OK]**</span><span class="sxs-lookup"><span data-stu-id="c74e0-136">**OK**</span></span>  
 <span data-ttu-id="c74e0-137">**[OK]** をクリックすると、変更が保存され、基本レポートの [全般] プロパティ ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="c74e0-137">Click **OK** to save your changes and return to the General properties page of the base report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74e0-138">参照</span><span class="sxs-lookup"><span data-stu-id="c74e0-138">See Also</span></span>  
 <span data-ttu-id="c74e0-139">[リンクレポートを作成する](reports/create-a-linked-report.md) </span><span class="sxs-lookup"><span data-stu-id="c74e0-139">[Create a Linked Report](reports/create-a-linked-report.md) </span></span>  
 <span data-ttu-id="c74e0-140">[[全般] プロパティページ、レポート &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="c74e0-140">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 [<span data-ttu-id="c74e0-141">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="c74e0-141">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
