---
title: ユーザー定義イベントの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2323dc4da3d1a8a67dad41ea189877ade25eff0e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742745"
---
# <a name="create-a-user-defined-event"></a><span data-ttu-id="3ef56-102">ユーザー定義イベントの作成</span><span class="sxs-lookup"><span data-stu-id="3ef56-102">Create a User-Defined Event</span></span>
  <span data-ttu-id="3ef56-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって定義済みのイベント以外のイベントを監視するには、ユーザー定義イベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ef56-103">You can create user-defined events if you want to monitor events other than events that are predefined by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3ef56-104">また、各ユーザー定義イベントに対して重大度レベルを割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="3ef56-104">You can also assign a severity level to each user-defined event.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ef56-105">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用中に、各ユーザー定義イベント メッセージに対して **[Windows アプリケーション イベント ログに書き込む]** オプションを選択して、そのメッセージがログに書き込まれるように設定できます。</span><span class="sxs-lookup"><span data-stu-id="3ef56-105">When using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select the **Write to Windows application event log** option for each user-defined event message, to ensure that the messages are logged.</span></span> <span data-ttu-id="3ef56-106">既定では、ユーザー定義メッセージが生成された場合でも、その重大度が 19 より低い場合は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログに送られません。</span><span class="sxs-lookup"><span data-stu-id="3ef56-106">By default, user-defined messages of severity lower than 19 are not sent to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application log when they occur.</span></span> <span data-ttu-id="3ef56-107">したがって、重大度が 19 より低いユーザー定義メッセージは、SQL Server エージェントの警告をトリガーしません。</span><span class="sxs-lookup"><span data-stu-id="3ef56-107">User-defined messages of severity lower than 19 therefore do not trigger SQL Server Agent alerts.</span></span>  
  
 <span data-ttu-id="3ef56-108">ユーザー定義イベントには、それぞれ一意のメッセージ番号が付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ef56-108">User-defined events must have a unique message number.</span></span> <span data-ttu-id="3ef56-109">ユーザー定義イベントのメッセージ番号は、50,000 より大きくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ef56-109">Message numbers for a user-defined event must be greater than 50,000.</span></span> <span data-ttu-id="3ef56-110">イベントに対するメッセージを複数の言語で定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="3ef56-110">You can define messages for the event in multiple languages.</span></span> <span data-ttu-id="3ef56-111">ただし、他の言語のメッセージを追加するには、 **En-US** エラー メッセージが存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ef56-111">However, an **En-US** error message must exist before messages in other languages can be added.</span></span>  
  
 <span data-ttu-id="3ef56-112">複数言語の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境を管理する場合は、サポートされている各言語でユーザー定義メッセージを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3ef56-112">If you administer a multiple-language [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] environment, create user-defined messages in each of the languages that are supported.</span></span> <span data-ttu-id="3ef56-113">たとえば、英語サーバーとドイツ語サーバーの両方で使用する新しいイベント メッセージを作成する場合、イベント番号と重大度はどちらのサーバーに対しても同じものを使用しますが、各サーバーに異なる言語を割り当ててください。</span><span class="sxs-lookup"><span data-stu-id="3ef56-113">For example, if you are creating a new event message to be used on both an English and a German server, use the same message number and severity for both, but assign a different language to each.</span></span>  
  
 <span data-ttu-id="3ef56-114">次のタスクでは、ユーザー定義イベントの作成方法とイベントに応答する警告についての情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="3ef56-114">The following tasks provide information about how to create user-defined events and alerts that respond to them:</span></span>  
  
 <span data-ttu-id="3ef56-115">**メッセージ番号に基づいた警告を作成するには**</span><span class="sxs-lookup"><span data-stu-id="3ef56-115">**To create an alert based on a message number**</span></span>  
  
-   [<span data-ttu-id="3ef56-116">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ef56-116">SQL Server Management Studio</span></span>](create-an-alert-using-an-error-number.md)  
  
-   [<span data-ttu-id="3ef56-117">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ef56-117">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="3ef56-118">**重大度レベルに基づいた警告を作成するには**</span><span class="sxs-lookup"><span data-stu-id="3ef56-118">**To create an alert based on severity levels**</span></span>  
  
-   [<span data-ttu-id="3ef56-119">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ef56-119">SQL Server Management Studio</span></span>](create-an-alert-using-severity-level.md)  
  
-   [<span data-ttu-id="3ef56-120">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ef56-120">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 <span data-ttu-id="3ef56-121">**警告に対する応答を定義するには**</span><span class="sxs-lookup"><span data-stu-id="3ef56-121">**To define the response to an alert**</span></span>  
  
-   [<span data-ttu-id="3ef56-122">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ef56-122">SQL Server Management Studio</span></span>](../sql-server-management-studio-ssms.md)  
  
-   [<span data-ttu-id="3ef56-123">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ef56-123">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 <span data-ttu-id="3ef56-124">**ユーザー定義のイベント エラー メッセージを作成するには**</span><span class="sxs-lookup"><span data-stu-id="3ef56-124">**To create a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="3ef56-125">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ef56-125">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 <span data-ttu-id="3ef56-126">**ユーザー定義のイベント エラー メッセージを変更するには**</span><span class="sxs-lookup"><span data-stu-id="3ef56-126">**To modify a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="3ef56-127">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ef56-127">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 <span data-ttu-id="3ef56-128">**ユーザー定義のイベント エラー メッセージを削除するには**</span><span class="sxs-lookup"><span data-stu-id="3ef56-128">**To delete a user-defined event error message**</span></span>  
  
-   [<span data-ttu-id="3ef56-129">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ef56-129">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 <span data-ttu-id="3ef56-130">**警告を無効にしたり、再び有効にするには**</span><span class="sxs-lookup"><span data-stu-id="3ef56-130">**To disable or reactivate an alert**</span></span>  
  
-   [<span data-ttu-id="3ef56-131">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="3ef56-131">SQL Server Management Studio</span></span>](disable-or-reactivate-an-alert.md)  
  
-   [<span data-ttu-id="3ef56-132">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="3ef56-132">Transact-SQL</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="3ef56-133">参照</span><span class="sxs-lookup"><span data-stu-id="3ef56-133">See Also</span></span>  
 [<span data-ttu-id="3ef56-134">sp_update_alert &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="3ef56-134">sp_update_alert &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
  
