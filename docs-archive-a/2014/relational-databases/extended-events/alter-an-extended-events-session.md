---
title: 拡張イベント セッションの変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
author: rothja
ms.author: jroth
ms.openlocfilehash: 14be41e48262bc7ebc8aeeaf55185f5e35d0c72e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631031"
---
# <a name="alter-an-extended-events-session"></a><span data-ttu-id="3dc1f-102">拡張イベント セッションの変更</span><span class="sxs-lookup"><span data-stu-id="3dc1f-102">Alter an Extended Events Session</span></span>
  <span data-ttu-id="3dc1f-103">拡張イベント セッションを作成したら、 **SQL Server 拡張イベント ウィザード**を使用して、必要に応じて拡張イベント セッションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-103">After you create an Extended Events session, you can alter it according to your needs using the **SQL Server Extended Events Wizard**.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="3dc1f-104">開始する前に</span><span class="sxs-lookup"><span data-stu-id="3dc1f-104">Before you Begin</span></span>  
 <span data-ttu-id="3dc1f-105">アクティブなセッションおよび非アクティブなセッションのターゲットを変更することはできません。また、アクティブなセッションの詳細プロパティの構成を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-105">You cannot alter a target for active and inactive sessions, and you cannot change the advanced properties configurations for an active session.</span></span>  
  
 <span data-ttu-id="3dc1f-106">アクティブなイベント セッションと非アクティブなイベント セッションの両方に対して、次の変更を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-106">You can make the following alterations to both active and inactive event sessions:</span></span>  
  
-   <span data-ttu-id="3dc1f-107">セッションのイベントの追加または削除、および、イベントの構成 (イベントのフィールド、フィルター、アクションなど) の変更。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-107">Add or remove events from the session, and alter the event configurations such as event fields, filters and actions.</span></span>  
  
-   <span data-ttu-id="3dc1f-108">イベント セッションのターゲットの追加または削除。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-108">Add or remove a target from the event session.</span></span>  
  
-   <span data-ttu-id="3dc1f-109">**[サーバーの起動時にイベント セッションを開始する]** オプションの有効化。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-109">Enable the **Start the event session on server startup** option.</span></span>  
  
 <span data-ttu-id="3dc1f-110">非アクティブなイベント セッションに対しては、次の変更も実行できます。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-110">You can make the following additional alterations to an inactive event session:</span></span>  
  
-   <span data-ttu-id="3dc1f-111">**[イベント間のリレーションシップの追跡]** オプションの有効化。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-111">Enable the **Track the relationship between events** option.</span></span>  
  
-   <span data-ttu-id="3dc1f-112">詳細プロパティの構成の変更。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-112">Change the advanced properties configuration.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3dc1f-113">**SQL Server 拡張イベント ウィザード** では、イベント セッションの変更はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-113">The **SQL Server Extended Events Wizard** does not support event session modification.</span></span>  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a><span data-ttu-id="3dc1f-114">SQL Server 拡張イベント ウィザードを使用して拡張イベント セッションを変更する方法</span><span class="sxs-lookup"><span data-stu-id="3dc1f-114">How to alter an Extended Events session using the SQL Server Extended Events Wizard</span></span>  
  
-   <span data-ttu-id="3dc1f-115">オブジェクト エクスプローラーで **[管理]** を展開し、 **[拡張イベント]** を展開して、 **[セッション]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-115">In Object Explorer, expand **Management**, expand **Extended Events**, and then expand **Sessions**.</span></span>  
  
-   <span data-ttu-id="3dc1f-116">変更するセッションを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-116">Right-click the session you want to alter, and then click **Properties**.</span></span>  
  
-   <span data-ttu-id="3dc1f-117">**[プロパティ]** ダイアログ ボックスで、必要な変更を行い、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3dc1f-117">In the **Properties** dialog box, make the appropriate changes, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc1f-118">参照</span><span class="sxs-lookup"><span data-stu-id="3dc1f-118">See Also</span></span>  
 <span data-ttu-id="3dc1f-119">[Transact-sql&#41;&#40;のイベントセッションの変更](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3dc1f-119">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 [<span data-ttu-id="3dc1f-120">クエリ エディターを使用した拡張イベント セッションの作成</span><span class="sxs-lookup"><span data-stu-id="3dc1f-120">Create an Extended Events Session Using Query Editor</span></span>](../../database-engine/create-an-extended-events-session-using-query-editor.md)  
  
  
