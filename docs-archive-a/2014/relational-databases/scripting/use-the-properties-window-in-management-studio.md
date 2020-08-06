---
title: Management Studio の [プロパティ] ウィンドウの使用
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
author: rothja
ms.author: jroth
ms.openlocfilehash: 5030bf85fc87482b11e91967ff8fb1baf77a213e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644961"
---
# <a name="use-the-properties-window-in-management-studio"></a><span data-ttu-id="a65b1-102">Management Studio の [プロパティ] ウィンドウの使用</span><span class="sxs-lookup"><span data-stu-id="a65b1-102">Use the Properties Window in Management Studio</span></span>
  <span data-ttu-id="a65b1-103">[プロパティ] ウィンドウには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]内の項目 (接続、プラン表示操作など) の状態や、データベース オブジェクト (テーブル、ビュー、デザイナーなど) の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a65b1-103">The Properties window describes the state of an item in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], such as a connection or a Showplan operator, and information about database objects such as tables, views, and designers.</span></span>  
  
 <span data-ttu-id="a65b1-104">[プロパティ] ウィンドウを使用して、現在の接続のプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a65b1-104">You can use the Properties window to view the properties of the current connection.</span></span> <span data-ttu-id="a65b1-105">[プロパティ] ウィンドウに表示される多くのプロパティは読み取り専用ですが、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]内の別の場所で変更できます。</span><span class="sxs-lookup"><span data-stu-id="a65b1-105">Many properties are read-only in the Properties window but can be changed elsewhere in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="a65b1-106">たとえば、[プロパティ] ウィンドウに表示されるクエリの [データベース] プロパティは読み取り専用ですが、ツール バーからの変更が可能です。</span><span class="sxs-lookup"><span data-stu-id="a65b1-106">For example, the Database property of a query is read-only in the Properties window, but can be changed on the tool bar.</span></span>  
  
### <a name="to-view-properties-using-the-properties-window"></a><span data-ttu-id="a65b1-107">[プロパティ] ウィンドウを使用してプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="a65b1-107">To view properties using the Properties window</span></span>  
  
1.  <span data-ttu-id="a65b1-108">[プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a65b1-108">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
2.  <span data-ttu-id="a65b1-109">表示するオブジェクトにフォーカスを設定します。</span><span class="sxs-lookup"><span data-stu-id="a65b1-109">Set the focus on the object that you want to view.</span></span>  
  
3.  <span data-ttu-id="a65b1-110">[プロパティ] ウィンドウで特定のプロパティを探します。</span><span class="sxs-lookup"><span data-stu-id="a65b1-110">Look for a specific property in the Properties window.</span></span>  
  
### <a name="to-view-connection-properties-of-a-query-window"></a><span data-ttu-id="a65b1-111">クエリ ウィンドウの接続プロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="a65b1-111">To view connection properties of a query window</span></span>  
  
1.  <span data-ttu-id="a65b1-112">[プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a65b1-112">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
2.  <span data-ttu-id="a65b1-113">[プロパティ] ウィンドウですべての接続プロパティを確認できます。</span><span class="sxs-lookup"><span data-stu-id="a65b1-113">In the Properties window, you can see all the connection properties.</span></span>  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a><span data-ttu-id="a65b1-114">プラン表示操作のプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="a65b1-114">To view the properties of a Showplan operator</span></span>  
  
1.  <span data-ttu-id="a65b1-115">**[クエリ]** メニューの **[実際の実行プランを含める]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a65b1-115">On the **Query** menu, click **Include Actual Execution Plan**.</span></span>  
  
2.  <span data-ttu-id="a65b1-116">SQL クエリ エディターで、クエリを入力して実行します。</span><span class="sxs-lookup"><span data-stu-id="a65b1-116">In the SQL Query Editor, type and execute a query.</span></span>  
  
3.  <span data-ttu-id="a65b1-117">[プロパティ] ウィンドウが表示されていない場合は、 **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックするか、F4 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a65b1-117">If the Properties window is not visible, click **Properties Window** on the **View** menu, or press F4.</span></span>  
  
4.  <span data-ttu-id="a65b1-118">SQL クエリ エディターの **[実行プラン]** タブでオペレーターのアイコンをクリックすると、[プロパティ] ウィンドウにそのオペレーターの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a65b1-118">On the **Execution plan** tab of the SQL Query Editor click the icons of the operators to view information about the operators in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65b1-119">参照</span><span class="sxs-lookup"><span data-stu-id="a65b1-119">See Also</span></span>  
 <span data-ttu-id="a65b1-120">[[プロパティ] ウィンドウ &#40;Management Studio&#41;](../../ssms/properties-window-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="a65b1-120">[Properties Window &#40;Management Studio&#41;](../../ssms/properties-window-management-studio.md)</span></span>  
  
  
