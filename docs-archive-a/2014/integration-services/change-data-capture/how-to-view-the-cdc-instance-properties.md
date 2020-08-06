---
title: CDC インスタンスのプロパティを表示する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bce9b82-7bbd-41df-b3f4-4b40b8bad474
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86fa298b0e02a16ddbaea220ef7f3d9f6172bf85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716561"
---
# <a name="how-to-view-the-cdc-instance-properties"></a><span data-ttu-id="fb0d2-102">CDC インスタンスのプロパティを表示する方法</span><span class="sxs-lookup"><span data-stu-id="fb0d2-102">How to View the CDC Instance Properties</span></span>
  <span data-ttu-id="fb0d2-103">この手順では、インスタンスの操作を管理するために作成するインスタンスの情報を、CDC デザイナー コンソールを使用して表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-103">This procedure describes how to use the CDC Designer Console to view information about the instances that you create to help manage the operation of the instances.</span></span>  
  
### <a name="to-view-information-about-a-specific-instance"></a><span data-ttu-id="fb0d2-104">特定のインスタンスに関する情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="fb0d2-104">To view information about a specific instance</span></span>  
  
1.  <span data-ttu-id="fb0d2-105">**[スタート]** メニューの **[CDC デザイナー コンソール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-105">From the **Start** menu, select the **CDC Designer Console**.</span></span>  
  
2.  <span data-ttu-id="fb0d2-106">左側のペインで **[Change Data Capture]** を展開し、表示するインスタンスが含まれているサービスを展開します。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-106">In the left pane, expand **Change Data Capture** then expand the service that contains the instance you want to view.</span></span>  
  
3.  <span data-ttu-id="fb0d2-107">操作するインスタンスの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-107">Select the name of an instance you want to work with.</span></span>  
  
     <span data-ttu-id="fb0d2-108">インスタンスに関する情報は、CDC デザイナー コンソールの中央部分に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-108">The information about the instance is displayed in the center part of the CDC Designer Console.</span></span> <span data-ttu-id="fb0d2-109">この部分は 4 つのタブに分かれています。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-109">It is divided into four tabs.</span></span> <span data-ttu-id="fb0d2-110">タブはいずれも読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-110">All of the tabs are read only.</span></span>  
  
     <span data-ttu-id="fb0d2-111">**状態**</span><span class="sxs-lookup"><span data-stu-id="fb0d2-111">**Status**</span></span>  
     <span data-ttu-id="fb0d2-112">このタブには、インスタンスの変更データ キャプチャの現在の状態に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-112">This tab displays the information about the current status of the change data capture for the instance.</span></span> <span data-ttu-id="fb0d2-113">このタブに表示される内容の詳細については、「 **Manage a CDC Instance** 」の「 [ビューアーのタブ](manage-a-cdc-instance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-113">For information about what is displayed in this tab, see the **Viewer Tabs** section in [Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
     <span data-ttu-id="fb0d2-114">**Oracle**</span><span class="sxs-lookup"><span data-stu-id="fb0d2-114">**Oracle**</span></span>  
     <span data-ttu-id="fb0d2-115">このタブには、CDC インスタンスと Oracle ソース データベースに関する一般的な情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-115">This tab displays general information about the CDC instance and the Oracle source database.</span></span> <span data-ttu-id="fb0d2-116">このタブに表示される内容の詳細については、「 [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-116">For information about what is displayed in this tab, see [Edit the Oracle Database Properties](edit-the-oracle-database-properties.md).</span></span>  
  
     <span data-ttu-id="fb0d2-117">**テーブル**</span><span class="sxs-lookup"><span data-stu-id="fb0d2-117">**Tables**</span></span>  
     <span data-ttu-id="fb0d2-118">このタブには、変更データ キャプチャに含まれるテーブルに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-118">This tab displays information about the tables included in the change data capture.</span></span> <span data-ttu-id="fb0d2-119">キャプチャされる列も表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-119">It also lists the columns that are captured.</span></span> <span data-ttu-id="fb0d2-120">このタブに表示される内容の詳細については、「 [Edit Tables](edit-tables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-120">For information about what is displayed in this tab, see [Edit Tables](edit-tables.md).</span></span>  
  
     <span data-ttu-id="fb0d2-121">**詳細**</span><span class="sxs-lookup"><span data-stu-id="fb0d2-121">**Advanced**</span></span>  
     <span data-ttu-id="fb0d2-122">このタブには、プロパティ エディターで定義する詳細プロパティの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-122">This tab displays a list of advanced properties that you define in the properties editor.</span></span> <span data-ttu-id="fb0d2-123">このタブに表示される内容の詳細については、「 [Edit the Advanced Properties](edit-the-advanced-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb0d2-123">For information about what is displayed in this tab, see [Edit the Advanced Properties](edit-the-advanced-properties.md).</span></span>  
  
  
