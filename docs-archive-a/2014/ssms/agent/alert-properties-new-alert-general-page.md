---
title: '[警告のプロパティ]-[新しい警告] ([全般] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.general.f1
ms.assetid: f5c11610-62e3-44df-9800-a5dc35be4a09
author: stevestein
ms.author: sstein
ms.openlocfilehash: 471b0062ecc805e83020495e422f8914baec5f71
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737500"
---
# <a name="alert-properties-new-alert-general-page"></a><span data-ttu-id="91549-102">[警告のプロパティ]-[新しい警告] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="91549-102">Alert Properties-New Alert (General Page)</span></span>
  <span data-ttu-id="91549-103">このページを使用すると、エージェントの警告の全般プロパティを表示したり、変更したり [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="91549-103">Use this page to view and modify the general properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="91549-104">Options</span><span class="sxs-lookup"><span data-stu-id="91549-104">Options</span></span>  
 <span data-ttu-id="91549-105">**名前**</span><span class="sxs-lookup"><span data-stu-id="91549-105">**Name**</span></span>  
 <span data-ttu-id="91549-106">警告の名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="91549-106">Change the name of the alert.</span></span>  
  
 <span data-ttu-id="91549-107">**有効化**</span><span class="sxs-lookup"><span data-stu-id="91549-107">**Enable**</span></span>  
 <span data-ttu-id="91549-108">警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="91549-108">Enable the alert.</span></span> <span data-ttu-id="91549-109">警告が有効でない場合、警告に指定されたアクションは発生しません。</span><span class="sxs-lookup"><span data-stu-id="91549-109">When the alert is not enabled, the actions specified in the alert do not occur.</span></span>  
  
 <span data-ttu-id="91549-110">**Type**</span><span class="sxs-lookup"><span data-stu-id="91549-110">**Type**</span></span>  
 <span data-ttu-id="91549-111">警告の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="91549-111">Select the type of alert:</span></span>  
  
-   <span data-ttu-id="91549-112">**SQL Server イベント警告** は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows イベント ログ内のメッセージに応答します。</span><span class="sxs-lookup"><span data-stu-id="91549-112">**SQL Server event alert** responds to messages in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows event log.</span></span>  
  
-   <span data-ttu-id="91549-113">**SQL Server パフォーマンス条件警告** は、パフォーマンス カウンター内の特定の条件に応答します。</span><span class="sxs-lookup"><span data-stu-id="91549-113">**SQL Server performance condition alert** responds to a specific condition in a performance counter.</span></span>  
  
-   <span data-ttu-id="91549-114">**WMI イベント警告** は、WMI (Windows Management Instrumentation) イベントに応答します。</span><span class="sxs-lookup"><span data-stu-id="91549-114">**WMI event alert** responds to a Windows Management Instrumentation (WMI) event.</span></span>  
  
## <a name="sql-server-event-alert-options"></a><span data-ttu-id="91549-115">SQL Server イベント警告のオプション</span><span class="sxs-lookup"><span data-stu-id="91549-115">SQL Server Event Alert Options</span></span>  
 <span data-ttu-id="91549-116">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="91549-116">**Database name**</span></span>  
 <span data-ttu-id="91549-117">イベントの対象のデータベースを指定します。イベントが発生するデータベースに関係なくメッセージに応答するには、 **[すべてのデータベース]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="91549-117">Specify a database for the event, or **all databases** to respond to a message regardless of the database where the event occurs.</span></span>  
  
 <span data-ttu-id="91549-118">**エラー番号**</span><span class="sxs-lookup"><span data-stu-id="91549-118">**Error number**</span></span>  
 <span data-ttu-id="91549-119">このイベントがエラーに応答することを指定し、エラー番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-119">Specify that this event responds to an error, and specify the error number.</span></span>  
  
 <span data-ttu-id="91549-120">**Severity**</span><span class="sxs-lookup"><span data-stu-id="91549-120">**Severity**</span></span>  
 <span data-ttu-id="91549-121">このイベントが特定の重大度レベルのすべてのメッセージに応答することを指定し、重大度レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-121">Specify that this event responds to any message with a specific severity level, and specify the severity level.</span></span>  
  
 <span data-ttu-id="91549-122">**[メッセージに次の内容が含まれている場合に警告する]**</span><span class="sxs-lookup"><span data-stu-id="91549-122">**Raise alert when message contains**</span></span>  
 <span data-ttu-id="91549-123">特定の文字列でイベントをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="91549-123">Filter events by a specific string.</span></span> <span data-ttu-id="91549-124">このオプションを選択した場合、警告は特定の文字列が含まれるイベントに対してだけ応答します。</span><span class="sxs-lookup"><span data-stu-id="91549-124">When this option is selected, the alert only responds to events that contain a specific string.</span></span>  
  
 <span data-ttu-id="91549-125">**メッセージテキスト**</span><span class="sxs-lookup"><span data-stu-id="91549-125">**Message text**</span></span>  
 <span data-ttu-id="91549-126">イベントをフィルター処理するために使用する文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-126">Specify the string to use to filter events.</span></span>  
  
## <a name="sql-server-performance-condition-alerts"></a><span data-ttu-id="91549-127">SQL Server パフォーマンス条件警告</span><span class="sxs-lookup"><span data-stu-id="91549-127">SQL Server Performance Condition Alerts</span></span>  
 <span data-ttu-id="91549-128">**Object**</span><span class="sxs-lookup"><span data-stu-id="91549-128">**Object**</span></span>  
 <span data-ttu-id="91549-129">監視対象のパフォーマンス オブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-129">Specify the performance object to monitor.</span></span>  
  
 <span data-ttu-id="91549-130">**カウンター**</span><span class="sxs-lookup"><span data-stu-id="91549-130">**Counter**</span></span>  
 <span data-ttu-id="91549-131">監視対象のパフォーマンス オブジェクト内のカウンターを指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-131">Specify the counter within the performance object to monitor.</span></span>  
  
 <span data-ttu-id="91549-132">**インスタンス**</span><span class="sxs-lookup"><span data-stu-id="91549-132">**Instance**</span></span>  
 <span data-ttu-id="91549-133">監視対象のカウンターのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-133">Specify the instance of the counter to monitor.</span></span>  
  
 <span data-ttu-id="91549-134">**[警告カウンター]**</span><span class="sxs-lookup"><span data-stu-id="91549-134">**Alert if counter**</span></span>  
 <span data-ttu-id="91549-135">警告が応答するカウンターの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-135">Specify the behavior of the counter that the alert responds to.</span></span> <span data-ttu-id="91549-136">たとえば、 **[Free space in tempdb (KB)]** カウンターの値が特定の値を下回る条件や、 **[SQL Compilations/sec]** が特定の値を上回る条件に応答するように警告を設定できます。</span><span class="sxs-lookup"><span data-stu-id="91549-136">For example, you may want the alert to respond to a condition where the value of the **Free space in tempdb (KB)** counter falls below a certain value, or you may want the alert to respond to a condition where the **SQL Compilations/sec** rises above a certain value.</span></span>  
  
 <span data-ttu-id="91549-137">**Value**</span><span class="sxs-lookup"><span data-stu-id="91549-137">**Value**</span></span>  
 <span data-ttu-id="91549-138">カウンターの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-138">Specify a value for the counter.</span></span>  
  
## <a name="wmi-event-alert-options"></a><span data-ttu-id="91549-139">WMI イベント警告のオプション</span><span class="sxs-lookup"><span data-stu-id="91549-139">WMI Event Alert Options</span></span>  
 <span data-ttu-id="91549-140">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="91549-140">**Namespace**</span></span>  
 <span data-ttu-id="91549-141">WQL (WMI Query Language) ステートメントに使用する名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-141">Specify the namespace to use for the WMI Query Language (WQL) statement.</span></span> <span data-ttu-id="91549-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが実行されているコンピューター上の名前空間だけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="91549-142">Only namespaces on the computer that runs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent are supported.</span></span>  
  
 <span data-ttu-id="91549-143">**クエリ**</span><span class="sxs-lookup"><span data-stu-id="91549-143">**Query**</span></span>  
 <span data-ttu-id="91549-144">警告が応答するイベントを識別する WQL ステートメントを指定します。</span><span class="sxs-lookup"><span data-stu-id="91549-144">Specify the WQL statement that identifies the event that the alert responds to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91549-145">参照</span><span class="sxs-lookup"><span data-stu-id="91549-145">See Also</span></span>  
 <span data-ttu-id="91549-146">[Alerts](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="91549-146">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="91549-147">[WMI Provider for Server Events での WQL の使用](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md) </span><span class="sxs-lookup"><span data-stu-id="91549-147">[Using WQL with the WMI Provider for Server Events](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md) </span></span>  
 <span data-ttu-id="91549-148">[エラー番号を使用して警告を作成する](create-an-alert-using-an-error-number.md) </span><span class="sxs-lookup"><span data-stu-id="91549-148">[Create an Alert Using an Error Number](create-an-alert-using-an-error-number.md) </span></span>  
 [<span data-ttu-id="91549-149">Create an Alert Using Severity Level</span><span class="sxs-lookup"><span data-stu-id="91549-149">Create an Alert Using Severity Level</span></span>](create-an-alert-using-severity-level.md)  
  
  
