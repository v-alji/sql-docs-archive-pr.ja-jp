---
title: ドメイン管理アクティビティの終了 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ab6505ad-3090-453b-bb01-58435e7fa7c0
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c776674a369bfae8c7da6fa0deabfbd932029570
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715725"
---
# <a name="end-the-domain-management-activity"></a><span data-ttu-id="e9ea4-102">ドメイン管理アクティビティの終了</span><span class="sxs-lookup"><span data-stu-id="e9ea4-102">End the Domain Management Activity</span></span>
  <span data-ttu-id="e9ea4-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のドメイン管理アクティビティを完了、終了、またはキャンセルする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-103">This topic describes how to complete, close, or cancel the domain management activity in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="e9ea4-104">ドメイン管理はウィザードで実行されないため、以下で説明する制御はドメイン管理アクティビティのどのページからでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-104">Domain management is not performed by a wizard, so the controls described below can used from any of the pages of the domain management activity.</span></span>  
  
## <a name="end-domain-management"></a><span data-ttu-id="e9ea4-105">ドメイン管理の終了</span><span class="sxs-lookup"><span data-stu-id="e9ea4-105">End Domain Management</span></span>  
 <span data-ttu-id="e9ea4-106">**[完了]**</span><span class="sxs-lookup"><span data-stu-id="e9ea4-106">**Finish**</span></span>  
 <span data-ttu-id="e9ea4-107">クリックすると、ドメイン管理が完了します。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-107">Click to complete domain management.</span></span> <span data-ttu-id="e9ea4-108">ポップアップ画面で、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-108">A popup will be displayed enabling you to do the following:</span></span>  
  
-   <span data-ttu-id="e9ea4-109">**[はい - ナレッジ ベースを発行して終了]**: 現在のユーザーまたは他のユーザーに対してナレッジ ベースが発行されます。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-109">**Yes - Publish the knowledge base and exit**: The knowledge base will be published for the current user or others to use.</span></span> <span data-ttu-id="e9ea4-110">ナレッジ ベースはロックされず、(ナレッジ ベース テーブルの) ナレッジ ベースの状態が空白に設定されます。ドメイン管理アクティビティとナレッジ検出アクティビティの両方を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-110">The knowledge base will not be locked, the state of the knowledge base (in the knowledge base table) will be set to empty, and both the Domain Management and Knowledge Discovery activities will be available.</span></span> <span data-ttu-id="e9ea4-111">[ナレッジ ベースを開く] 画面に戻ります。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-111">You will be returned to the Open Knowledge Base screen.</span></span>  
  
-   <span data-ttu-id="e9ea4-112">**[いいえ-作業内容をナレッジベースに保存して終了**]: 作業内容が保存され、ナレッジベースがロックされたままになり、ナレッジベースの状態が [作業中] に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-112">**No - Save the work on the knowledge base and exit**: Your work will be saved, the knowledge base will remained locked, and the state of the knowledge base will be set to In work.</span></span> <span data-ttu-id="e9ea4-113">ドメイン管理アクティビティとナレッジ検出アクティビティの両方を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-113">Both the Domain Management and Knowledge Discovery activities will be available.</span></span> <span data-ttu-id="e9ea4-114">ホーム ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-114">You will be returned to the home page.</span></span>  
  
-   <span data-ttu-id="e9ea4-115">**[キャンセル]-現在の画面に表示**されます。ポップアップは閉じられ、[ドメイン管理] 画面に戻ります。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-115">**Cancel - Stay on the current screen**: The popup will be closed and you will be returned to the Domain Management screen.</span></span>  
  
 <span data-ttu-id="e9ea4-116">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="e9ea4-116">**Cancel**</span></span>  
 <span data-ttu-id="e9ea4-117">クリックすると、ドメイン管理アクティビティが終了して作業内容が破棄され、DQS ホーム ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-117">Click to terminate the Domain Management activity, losing your work, and return to the DQS home page.</span></span>  
  
 <span data-ttu-id="e9ea4-118">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="e9ea4-118">**Close**</span></span>  
 <span data-ttu-id="e9ea4-119">クリックすると、作業内容が保存され、DQS ホーム ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-119">Click to save your work, and return to the DQS home page.</span></span> <span data-ttu-id="e9ea4-120">ナレッジ ベースがロックされ、 **[ナレッジ ベースを開く]** 画面のナレッジ ベース テーブルのナレッジ ベースの状態が **[ドメイン管理]** になります。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-120">The knowledge base will be locked, and the state of the knowledge base in the knowledge base table in the **Open Knowledge Base** screen will be **Domain Management**.</span></span> <span data-ttu-id="e9ea4-121">**[閉じる]** をクリックした後でナレッジ検出アクティビティを実行するには、 **[ドメイン管理]** 画面に戻り、 **[完了]** をクリックします。次に、ナレッジ ベースを発行する場合は **[はい]** を、作業内容をナレッジ ベースに保存して終了する場合は **[いいえ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-121">After clicking **Close**, to perform the Knowledge Discovery activity, you would have to return to the **Domain Management** screen, click **Finish**, and then click either **Yes** to publish the knowledge base or **No** to save the work on the knowledge base and exit.</span></span>  <span data-ttu-id="e9ea4-122">ロックされたナレッジ ベースを開く方法の詳細については、「 [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9ea4-122">For more information on opening a locked knowledge base, see [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
  
