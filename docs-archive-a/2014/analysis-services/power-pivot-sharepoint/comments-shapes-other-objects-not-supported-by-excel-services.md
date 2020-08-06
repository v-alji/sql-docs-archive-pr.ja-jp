---
title: '次の機能は Excel Services ではサポートされていないため、表示されないか、一部しか表示されない可能性があります: コメント、図形、またはその他のオブジェクト |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
author: minewiskan
ms.author: owend
ms.openlocfilehash: 67c2989ab89f242fdce2ca64f3c2f361e17d49ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715765"
---
# <a name="the-following-features-are-not-supported-by-excel-services-and-may-not-display-or-may-display-only-partially-comments-shapes-or-other-objects"></a><span data-ttu-id="f29d9-102">次の機能は Excel Services でサポートされておらず、表示されないか、一部しか表示されないことがあります。コメント、図形、またはその他のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="f29d9-102">The following features are not supported by Excel Services and may not display or may display only partially: Comments, Shapes, or other objects</span></span>
  <span data-ttu-id="f29d9-103">このエラーは、PowerPivot フィールドの一覧から PowerPivot ブックにスライサーを追加すると発生します。</span><span class="sxs-lookup"><span data-stu-id="f29d9-103">This error occurs when you add Slicers to a PowerPivot workbook from a PowerPivot Field List.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f29d9-104">詳細</span><span class="sxs-lookup"><span data-stu-id="f29d9-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f29d9-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="f29d9-105">Applies to</span></span>|<span data-ttu-id="f29d9-106">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="f29d9-106">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="f29d9-107">製品バージョン</span><span class="sxs-lookup"><span data-stu-id="f29d9-107">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="f29d9-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f29d9-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="f29d9-109">原因</span><span class="sxs-lookup"><span data-stu-id="f29d9-109">Cause</span></span>|<span data-ttu-id="f29d9-110">Excel Web Access では、PowerPivot フィールドの一覧からブックに追加されたスライサーの位置指定および書式設定の制御に使用される図形オブジェクトを表示することができません。</span><span class="sxs-lookup"><span data-stu-id="f29d9-110">Excel Web Access cannot render the Shape object used to control positioning and formatting of Slicers added to a workbook from the PowerPivot Field List.</span></span>|  
|<span data-ttu-id="f29d9-111">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="f29d9-111">Message Text</span></span>|<span data-ttu-id="f29d9-112">次の機能は Excel Services でサポートされておらず、表示されないか、一部しか表示されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f29d9-112">The following features are not supported by Excel Services and may not display or may display only partially:</span></span><br /><br /> <span data-ttu-id="f29d9-113">コメント、図形、またはその他のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="f29d9-113">Comments, Shapes, or other objects</span></span><br /><br /> <span data-ttu-id="f29d9-114">外部データのクエリなど、一部の機能では、Microsoft Excel でのみ更新できるキャッシュ データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f29d9-114">Some features, such as external data queries, display cached data which can only be refreshed in Microsoft Excel.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f29d9-115">説明</span><span class="sxs-lookup"><span data-stu-id="f29d9-115">Explanation</span></span>  
 <span data-ttu-id="f29d9-116">このエラーが表示されるのは、ブラウザーで PowerPivot ブックを開き、メッセージの [**詳細**] ボタンをクリックした場合です。**サポートされていない機能では、このブックは意図したとおりに表示されない可能性があり**ます。 Web アクセス</span><span class="sxs-lookup"><span data-stu-id="f29d9-116">Excel Web Access shows this error when you open a PowerPivot workbook in a browser and you click the **Details** button for the message, **Unsupported Features This workbook may not display as intended**.</span></span>  
  
 <span data-ttu-id="f29d9-117">このエラーは、Excel の非表示の図形オブジェクトによって制御されるレイアウトを持つスライサーが PowerPivot ブックにある場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="f29d9-117">This error occurs because the PowerPivot workbook contains Slicers whose layout is controlled by a hidden Shape object in Excel.</span></span> <span data-ttu-id="f29d9-118">図形オブジェクトは、水平配置と垂直配置におけるスライサーの書式設定および位置指定を制御します。</span><span class="sxs-lookup"><span data-stu-id="f29d9-118">The Shape object controls the formatting and positioning of the Slicers in horizontal and vertical placements.</span></span>  
  
 <span data-ttu-id="f29d9-119">Excel Services では図形オブジェクトを表示できませんが、このオブジェクトは非表示であるので、表示できないことは問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="f29d9-119">Excel Services cannot render a Shape object, but because the object is hidden, the fact that it does not render is not an issue.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f29d9-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="f29d9-120">User Action</span></span>  
 <span data-ttu-id="f29d9-121">このエラーは無視してかまいません。</span><span class="sxs-lookup"><span data-stu-id="f29d9-121">This error can be ignored.</span></span> <span data-ttu-id="f29d9-122">**[OK]** をクリックして、エラー メッセージを閉じ、ブックとスライサーの使用を問題なく続けることができます。</span><span class="sxs-lookup"><span data-stu-id="f29d9-122">Click **OK** to close the error message and proceed to use the workbook and Slicers with no problem.</span></span>  
  
  
