---
title: 拡張イベントセッションのスクリプトを作成する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f9fdde-1f13-4292-a4fc-55da826be3b4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 11adc60ae7c7e0f8b8012d06f56c83874d3708ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639633"
---
# <a name="script-an-extended-event-session"></a><span data-ttu-id="b2c2d-102">拡張イベント セッションのスクリプト化</span><span class="sxs-lookup"><span data-stu-id="b2c2d-102">Script an Extended Event Session</span></span>
  <span data-ttu-id="b2c2d-103">このトピックでは、イベント セッションをスクリプト化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-103">This topic describes how to script an event session.</span></span> <span data-ttu-id="b2c2d-104">イベント セッションはエクスポート、変更、または削除できるほか、イベント セッションを削除してから新たに作成し、次のような形式で出力することができます。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-104">You can export, alter, or drop the event session, or drop and create the event session to the following:</span></span>  
  
-   <span data-ttu-id="b2c2d-105">**新しいクエリ エディター ウィンドウ**</span><span class="sxs-lookup"><span data-stu-id="b2c2d-105">**New Query Editor Window**</span></span>  
  
-   <span data-ttu-id="b2c2d-106">**[最近使ったファイル]**</span><span class="sxs-lookup"><span data-stu-id="b2c2d-106">**File**</span></span>  
  
-   <span data-ttu-id="b2c2d-107">**クリップボード**</span><span class="sxs-lookup"><span data-stu-id="b2c2d-107">**Clipboard**</span></span>  
  
-   <span data-ttu-id="b2c2d-108">**エージェント ジョブ**</span><span class="sxs-lookup"><span data-stu-id="b2c2d-108">**Agent Job**</span></span>  
  
### <a name="to-script-an-existing-event-session"></a><span data-ttu-id="b2c2d-109">既存のイベント セッションをスクリプト化するには</span><span class="sxs-lookup"><span data-stu-id="b2c2d-109">To script an existing event session</span></span>  
  
1.  <span data-ttu-id="b2c2d-110">オブジェクト エクスプローラーで **[管理]** ノードを展開し、 **[拡張イベント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-110">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="b2c2d-111">スクリプト化するセッションを右クリックし、 **[セッションをスクリプト化]** をポイントして **[CREATE]** をポイントした後、セッションのスクリプトをどこに出力するかを選択します。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-111">Right-click the session you want to script, point to **Script Session as**, point to **CREATE to**, and then select where you want to script the session.</span></span>  
  
### <a name="to-script-a-new-event-session"></a><span data-ttu-id="b2c2d-112">新しいイベント セッションをスクリプト化するには</span><span class="sxs-lookup"><span data-stu-id="b2c2d-112">To script a new event session</span></span>  
  
1.  <span data-ttu-id="b2c2d-113">オブジェクト エクスプローラーで **[管理]** ノードを展開し、 **[拡張イベント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-113">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="b2c2d-114">**[セッション]** を右クリックし、 **[新しいセッション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-114">Right-click **Sessions**, and then click **New Session**.</span></span>  
  
3.  <span data-ttu-id="b2c2d-115">**[新しいセッション]** の UI でイベント セッションを作成した後、イベント セッション スクリプトの出力先を **[スクリプト]** ボックスの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-115">In the **New Session** UI, create the event session, and then select where you want to script the event session from the **Script** drop-down list.</span></span>  
  
### <a name="to-script-a-modified-event-session"></a><span data-ttu-id="b2c2d-116">イベント セッションに変更を加えてスクリプト化するには</span><span class="sxs-lookup"><span data-stu-id="b2c2d-116">To script a modified event session</span></span>  
  
1.  <span data-ttu-id="b2c2d-117">オブジェクト エクスプローラーで **[管理]** ノードを展開し、 **[拡張イベント]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-117">In Object Explorer, expand the **Management** node, and then expand **Extended Events**.</span></span>  
  
2.  <span data-ttu-id="b2c2d-118">変更するセッションを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-118">Right-click the session you want to modify, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="b2c2d-119">**[セッションのプロパティ]** ダイアログ ボックスでイベント セッションに変更を加えた後、その変更後のセッション スクリプトの出力先を **[スクリプト]** ボックスの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="b2c2d-119">In the **Session Properties** dialog box, modify the event session, and then select where you want to script the modified session from the **Script** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c2d-120">参照</span><span class="sxs-lookup"><span data-stu-id="b2c2d-120">See Also</span></span>  
 [<span data-ttu-id="b2c2d-121">拡張イベント</span><span class="sxs-lookup"><span data-stu-id="b2c2d-121">Extended Events</span></span>](../relational-databases/extended-events/extended-events.md)  
  
  
