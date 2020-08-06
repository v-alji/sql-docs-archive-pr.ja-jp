---
title: '[ログイン転送タスクエディター] ([ログイン] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.logins.f1
helpviewer_keywords:
- Transfer Logins Task Editor
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33fea6c78df75b7eebe8987f952dce33bdc4407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646208"
---
# <a name="transfer-logins-task-editor-logins-page"></a><span data-ttu-id="7dc5a-102">[ログイン転送タスク エディター] ([ログイン] ページ)</span><span class="sxs-lookup"><span data-stu-id="7dc5a-102">Transfer Logins Task Editor (Logins Page)</span></span>
  <span data-ttu-id="7dc5a-103">**[ログイン転送タスク エディター]** ダイアログ ボックスの **[ログイン]** ページを使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスから別のインスタンスへと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインをコピーする際のプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-103">Use the **Logins** page of the **Transfer Logins Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="7dc5a-104">このタスクの詳細については、「 [ログイン転送タスク](control-flow/transfer-logins-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-104">For more information about this task, see [Transfer Logins Task](control-flow/transfer-logins-task.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7dc5a-105">ログイン転送タスクを実行すると、転送先のサーバー上でランダムなパスワードを使用してログインが作成され、パスワードが無効になります。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-105">When the Transfer Logins task is executed, logins are created on the destination server with random passwords and the passwords are disabled.</span></span> <span data-ttu-id="7dc5a-106">このログインを使用するには、 **sysadmin** 固定サーバー ロールのメンバーでパスワードを変更し、そのパスワードを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-106">To use these logins, a member of the **sysadmin** fixed server role must change the passwords and then enable them.</span></span> <span data-ttu-id="7dc5a-107">**sa** ログインは転送できません。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-107">The **sa** login cannot be transferred.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7dc5a-108">オプション</span><span class="sxs-lookup"><span data-stu-id="7dc5a-108">Options</span></span>  
 <span data-ttu-id="7dc5a-109">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-109">**SourceConnection**</span></span>  
 <span data-ttu-id="7dc5a-110">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送元サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-110">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="7dc5a-111">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-111">**DestinationConnection**</span></span>  
 <span data-ttu-id="7dc5a-112">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送先サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-112">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="7dc5a-113">**[LoginsToTransfer]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-113">**LoginsToTransfer**</span></span>  
 <span data-ttu-id="7dc5a-114">転送元サーバーから転送先サーバーにコピーされる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインを選択します。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-114">Select the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins to copy from the source to the destination server.</span></span> <span data-ttu-id="7dc5a-115">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-115">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="7dc5a-116">値</span><span class="sxs-lookup"><span data-stu-id="7dc5a-116">Value</span></span>|<span data-ttu-id="7dc5a-117">説明</span><span class="sxs-lookup"><span data-stu-id="7dc5a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7dc5a-118">**[AllLogins]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-118">**AllLogins**</span></span>|<span data-ttu-id="7dc5a-119">転送元サーバーのすべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインが転送先サーバーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-119">All [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] logins on the source server will be copied to the destination server.</span></span>|  
|<span data-ttu-id="7dc5a-120">**[SelectedLogins]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-120">**SelectedLogins**</span></span>|<span data-ttu-id="7dc5a-121">**[LoginsList]** に指定されているログインのみが転送先サーバーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-121">Only logins specified with **LoginsList** will be copied to the destination server.</span></span>|  
|<span data-ttu-id="7dc5a-122">**[AllLoginsFromSelectedDatabases]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-122">**AllLoginsFromSelectedDatabases**</span></span>|<span data-ttu-id="7dc5a-123">**[DatabasesList]** で指定されているデータベース内のすべてのログインが転送先サーバーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-123">All logins from the databases specified with **DatabasesList** will be copied to the destination server.</span></span>|  
  
 <span data-ttu-id="7dc5a-124">**[LoginsList]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-124">**LoginsList**</span></span>  
 <span data-ttu-id="7dc5a-125">転送先サーバーにコピーする、転送元サーバーのログインを選択します。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-125">Select the logins on the source server to be copied to the destination server.</span></span> <span data-ttu-id="7dc5a-126">このオプションは、 **[LoginsToTransfer]** を **[SelectedLogins]** に設定した場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-126">This option is only available when **SelectedLogins** is selected for **LoginsToTransfer**.</span></span>  
  
 <span data-ttu-id="7dc5a-127">**[DatabasesList]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-127">**DatabasesList**</span></span>  
 <span data-ttu-id="7dc5a-128">転送先サーバーにコピーするログインが含まれる、転送元サーバー上のデータベースを選択します。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-128">Select the databases on the source server that contain logins to be copied to the destination server.</span></span> <span data-ttu-id="7dc5a-129">このオプションは、 **[LoginsToTransfer]** を **[AllLoginsFromSelectedDatabases]** に設定した場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-129">This option is only available when **AllLoginsFromSelectedDatabases** is selected for **LoginsToTransfer**.</span></span>  
  
 <span data-ttu-id="7dc5a-130">**[IfObjectExists]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-130">**IfObjectExists**</span></span>  
 <span data-ttu-id="7dc5a-131">転送先サーバーに同じ名前のログインが既に存在していた場合の処理方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-131">Select how the task should handle logins of the same name that already exist on the destination server.</span></span>  
  
 <span data-ttu-id="7dc5a-132">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-132">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="7dc5a-133">値</span><span class="sxs-lookup"><span data-stu-id="7dc5a-133">Value</span></span>|<span data-ttu-id="7dc5a-134">説明</span><span class="sxs-lookup"><span data-stu-id="7dc5a-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7dc5a-135">**[FailTask]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-135">**FailTask**</span></span>|<span data-ttu-id="7dc5a-136">転送先サーバーに同じ名前のログインが既に存在していた場合、タスクが失敗します。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-136">Task fails if logins of the same name already exist on the destination server.</span></span>|  
|<span data-ttu-id="7dc5a-137">**Overwrite**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-137">**Overwrite**</span></span>|<span data-ttu-id="7dc5a-138">転送先サーバーにある同じ名前のログインは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-138">Task overwrites logins of the same name on the destination server.</span></span>|  
|<span data-ttu-id="7dc5a-139">**Skip**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-139">**Skip**</span></span>|<span data-ttu-id="7dc5a-140">転送先サーバーにある同じ名前のログインはスキップされます。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-140">Task skips logins of the same name that exist on the destination server.</span></span>|  
  
 <span data-ttu-id="7dc5a-141">**[CopySids]**</span><span class="sxs-lookup"><span data-stu-id="7dc5a-141">**CopySids**</span></span>  
 <span data-ttu-id="7dc5a-142">ログインに関連付けられたセキュリティ識別子を転送先サーバーにコピーするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-142">Select whether the security identifiers associated with the logins should be copied to the destination server.</span></span> <span data-ttu-id="7dc5a-143">ログイン転送タスクをデータベース転送タスクと同時に使用する場合、 **[CopySids]** を **[True]** に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-143">**CopySids** must be set to **True** if the Transfer Logins task is used along with the Transfer Database task.</span></span> <span data-ttu-id="7dc5a-144">そのように設定しなかった場合、コピーされたログインは転送されたデータベースで認識されなくなります。</span><span class="sxs-lookup"><span data-stu-id="7dc5a-144">Otherwise, the copied logins will not be recognized by the transferred database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc5a-145">参照</span><span class="sxs-lookup"><span data-stu-id="7dc5a-145">See Also</span></span>  
 <span data-ttu-id="7dc5a-146">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7dc5a-146">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="7dc5a-147">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="7dc5a-147">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="7dc5a-148">[[ログイン転送タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="7dc5a-148">[Transfer Logins Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="7dc5a-149">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="7dc5a-149">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="7dc5a-150">[SMO 接続マネージャー](connection-manager/smo-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="7dc5a-150">[SMO Connection Manager](connection-manager/smo-connection-manager.md) </span></span>  
 <span data-ttu-id="7dc5a-151">[強力なパスワード](../relational-databases/security/strong-passwords.md) </span><span class="sxs-lookup"><span data-stu-id="7dc5a-151">[Strong Passwords](../relational-databases/security/strong-passwords.md) </span></span>  
 [<span data-ttu-id="7dc5a-152">SQL Server インストールにおけるセキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="7dc5a-152">Security Considerations for a SQL Server Installation</span></span>](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
