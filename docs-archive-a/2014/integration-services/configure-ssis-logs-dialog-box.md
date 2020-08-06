---
title: '[SSIS ログの構成] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.configuredtslogs.loggingdetails.f1
- sql12.dts.designer.configuredtslogs.providersandlogs.f1
- sql12.dts.designer.configuredtslogs.containers.f1
helpviewer_keywords:
- Configure SSIS Logs dialog box
ms.assetid: 4b980275-cd9a-4943-8c36-727d51f9a484
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 252b45765fb784790bcca0fb86e2e56e7e7baddc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639595"
---
# <a name="configure-ssis-logs-dialog-box"></a><span data-ttu-id="52d01-102">[SSIS ログの構成] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="52d01-102">Configure SSIS Logs Dialog Box</span></span>
  <span data-ttu-id="52d01-103">**SSIS ログの構成** ダイアログ ボックスを使用して、パッケージのログ記録オプションを定義します。</span><span class="sxs-lookup"><span data-stu-id="52d01-103">Use the **Configure SSIS Logs** dialog box to define logging options for a package.</span></span>  
  
 <span data-ttu-id="52d01-104">**目的に合ったトピックをクリックしてください**</span><span class="sxs-lookup"><span data-stu-id="52d01-104">**What do you want to do?**</span></span>  
  
1.  <span data-ttu-id="52d01-105">[[SSIS ログの構成] ダイアログ ボックスを開く](#open_dialog)</span><span class="sxs-lookup"><span data-stu-id="52d01-105">[Open the Configure SSIS Logs Dialog Box](#open_dialog)</span></span>  
  
2.  <span data-ttu-id="52d01-106">[[コンテナー] ペインでオプションを構成する](#container)</span><span class="sxs-lookup"><span data-stu-id="52d01-106">[Configure the Options in the Containers Pane](#container)</span></span>  
  
3.  <span data-ttu-id="52d01-107">[[プロバイダーとログ] タブでオプションを構成する](#provider)</span><span class="sxs-lookup"><span data-stu-id="52d01-107">[Configure the Options on the Providers and Logs Tab](#provider)</span></span>  
  
4.  <span data-ttu-id="52d01-108">[[詳細] タブでオプションを構成する](#detail)</span><span class="sxs-lookup"><span data-stu-id="52d01-108">[Configure the Options on the Details Tab](#detail)</span></span>  
  
##  <a name="open-the-configure-ssis-logs-dialog-box"></a><a name="open_dialog"></a> <span data-ttu-id="52d01-109">[SSIS ログの構成] ダイアログ ボックスを開く</span><span class="sxs-lookup"><span data-stu-id="52d01-109">Open the Configure SSIS Logs Dialog Box</span></span>  
 <span data-ttu-id="52d01-110">**[SSIS ログの構成] ダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="52d01-110">**To open the Configure SSIS Logs dialog box**</span></span>  
  
-   <span data-ttu-id="52d01-111">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、 **[SSIS]** メニューの **[ログ記録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52d01-111">In the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click **Logging** on the **SSIS** menu.</span></span>  
  
##  <a name="configure-the-options-in-the-containers-pane"></a><a name="container"></a> <span data-ttu-id="52d01-112">[コンテナー] ペインでオプションを構成する</span><span class="sxs-lookup"><span data-stu-id="52d01-112">Configure the Options in the Containers Pane</span></span>  
 <span data-ttu-id="52d01-113">**[SSIS ログの構成]** ダイアログ ボックスの **[コンテナー]** ペインを使用すると、パッケージおよびパッケージのコンテナーでログを有効できます。</span><span class="sxs-lookup"><span data-stu-id="52d01-113">Use the **Containers** pane of the **Configure SSIS Logs** dialog box to enable the package and its containers for logging.</span></span>  
  
### <a name="options"></a><span data-ttu-id="52d01-114">オプション</span><span class="sxs-lookup"><span data-stu-id="52d01-114">Options</span></span>  
 <span data-ttu-id="52d01-115">**Containers**</span><span class="sxs-lookup"><span data-stu-id="52d01-115">**Containers**</span></span>  
 <span data-ttu-id="52d01-116">パッケージとパッケージのコンテナーでログを有効にするには、階層ビューのチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="52d01-116">Select the check boxes in the hierarchical view to enable the package and its containers for logging:</span></span>  
  
-   <span data-ttu-id="52d01-117">オフになっている場合、そのコンテナーでログは無効になります。</span><span class="sxs-lookup"><span data-stu-id="52d01-117">If cleared, the container is not enabled for logging.</span></span> <span data-ttu-id="52d01-118">ログを有効にする場合はオンにします。</span><span class="sxs-lookup"><span data-stu-id="52d01-118">Select to enable logging.</span></span>  
  
-   <span data-ttu-id="52d01-119">淡色表示になっている場合、コンテナーは親のログ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="52d01-119">If dimmed, the container uses the logging options of its parent.</span></span> <span data-ttu-id="52d01-120">このオプションは、パッケージには使用できません。</span><span class="sxs-lookup"><span data-stu-id="52d01-120">This option is not available for the package.</span></span>  
  
-   <span data-ttu-id="52d01-121">オンにすると、コンテナーは固有のログ オプションを定義します。</span><span class="sxs-lookup"><span data-stu-id="52d01-121">If checked, the container defines its own logging options.</span></span>  
  
 <span data-ttu-id="52d01-122">コンテナーが淡色表示になっている場合に、そのコンテナーにログ オプションを設定するには、チェック ボックスを 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="52d01-122">If a container is dimmed and you want to set logging options on the container, click its check box twice.</span></span> <span data-ttu-id="52d01-123">最初のクリックでチェック ボックスがオフになった後、2 番目のクリックでオンになったら、使用するログ プロバイダーを選択し、ログに記録する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="52d01-123">The first click clears the check box, and the second click selects it, enabling you to choose the log providers to use and select the information to log.</span></span>  
  
##  <a name="configure-the-options-on-the-providers-and-logs-tab"></a><a name="provider"></a> <span data-ttu-id="52d01-124">[プロバイダーとログ] タブでオプションを構成する</span><span class="sxs-lookup"><span data-stu-id="52d01-124">Configure the Options on the Providers and Logs Tab</span></span>  
 <span data-ttu-id="52d01-125">**[SSIS ログの構成]** ダイアログ ボックスの **[プロバイダーとログ]** タブを使用すると、ランタイム イベントをキャプチャするログを作成したり構成したりできます。</span><span class="sxs-lookup"><span data-stu-id="52d01-125">Use the **Providers and Logs** tab of the **Configure SSIS Logs** dialog box to create and configure logs for capturing run-time events.</span></span>  
  
### <a name="options"></a><span data-ttu-id="52d01-126">オプション</span><span class="sxs-lookup"><span data-stu-id="52d01-126">Options</span></span>  
 <span data-ttu-id="52d01-127">**[プロバイダーの種類]**</span><span class="sxs-lookup"><span data-stu-id="52d01-127">**Provider type**</span></span>  
 <span data-ttu-id="52d01-128">ログ プロバイダーの種類を一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="52d01-128">Select a type of log provider from the list.</span></span>  
  
 <span data-ttu-id="52d01-129">**追加**</span><span class="sxs-lookup"><span data-stu-id="52d01-129">**Add**</span></span>  
 <span data-ttu-id="52d01-130">パッケージのログ プロバイダーのコレクションに、指定した種類のログを追加します。</span><span class="sxs-lookup"><span data-stu-id="52d01-130">Add a log of the specified type to the collection of log providers of the package.</span></span>  
  
 <span data-ttu-id="52d01-131">**Name**</span><span class="sxs-lookup"><span data-stu-id="52d01-131">**Name**</span></span>  
 <span data-ttu-id="52d01-132">**[SSIS ログの構成]** ダイアログ ボックスの **[コンテナー]** ペインで選択したコンテナーまたはタスクについて、ログを有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="52d01-132">Enable or disable logs for containers or tasks selected in the **Containers** pane of the **Configure SSIS Logs** dialog box, by using the check boxes.</span></span> <span data-ttu-id="52d01-133">[名前] フィールドは編集可能です。</span><span class="sxs-lookup"><span data-stu-id="52d01-133">The name field is editable.</span></span> <span data-ttu-id="52d01-134">プロバイダーの既定の名前を使用するか、わかりやすい一意な名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="52d01-134">Use the default name for the provider, or type a unique descriptive name.</span></span>  
  
 <span data-ttu-id="52d01-135">**説明**</span><span class="sxs-lookup"><span data-stu-id="52d01-135">**Description**</span></span>  
 <span data-ttu-id="52d01-136">[説明] フィールドは編集可能です。</span><span class="sxs-lookup"><span data-stu-id="52d01-136">The description field is editable.</span></span> <span data-ttu-id="52d01-137">クリックして、ログの既定の説明を変更します。</span><span class="sxs-lookup"><span data-stu-id="52d01-137">Click and then modify the default description of the log.</span></span>  
  
 <span data-ttu-id="52d01-138">**構成**</span><span class="sxs-lookup"><span data-stu-id="52d01-138">**Configuration**</span></span>  
 <span data-ttu-id="52d01-139">既存の接続マネージャーを一覧から選択するか、[\<**New connection...**>] をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="52d01-139">Select an existing connection manager in the list, or click \<**New connection...**> to create a new connection manager.</span></span> <span data-ttu-id="52d01-140">ログ プロバイダーの種類によっては、OLE DB 接続マネージャーやファイル接続マネージャーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="52d01-140">Depending on the type of log provider, you can configure an OLE DB connection manager or a File connection manager.</span></span> <span data-ttu-id="52d01-141">[!INCLUDE[msCoName](../includes/msconame-md.md)] Windows イベント ログ用のログ プロバイダーの場合、接続は不要です。</span><span class="sxs-lookup"><span data-stu-id="52d01-141">The log provider for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Event Log requires no connection.</span></span>  
  
 <span data-ttu-id="52d01-142">関連項目:「 [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) 」、「 [File Connection Manager](connection-manager/file-connection-manager.md)」</span><span class="sxs-lookup"><span data-stu-id="52d01-142">Related Topics: [OLE DB Connection Manager](connection-manager/ole-db-connection-manager.md) manager, [File Connection Manager](connection-manager/file-connection-manager.md)</span></span>  
  
 <span data-ttu-id="52d01-143">**削除**</span><span class="sxs-lookup"><span data-stu-id="52d01-143">**Delete**</span></span>  
 <span data-ttu-id="52d01-144">ログ プロバイダーを選択して、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52d01-144">Select a log provider and then click **Delete**.</span></span>  
  
##  <a name="configure-the-options-on-the-details-tab"></a><a name="detail"></a> <span data-ttu-id="52d01-145">[詳細] タブでオプションを構成する</span><span class="sxs-lookup"><span data-stu-id="52d01-145">Configure the Options on the Details Tab</span></span>  
 <span data-ttu-id="52d01-146">**[SSIS ログの構成]** ダイアログ ボックスの **[詳細]** タブで、ログ記録を有効にするイベントと、ログ記録する詳細情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="52d01-146">Use the **Details** tab of the **Configure SSIS Logs** dialog box to specify the events to enable for logging and the information details to log.</span></span> <span data-ttu-id="52d01-147">選択した情報は、パッケージ内のすべてのログ プロバイダーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="52d01-147">The information that you select applies to all the log providers in the package.</span></span> <span data-ttu-id="52d01-148">たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスとテキスト ファイルに別々の情報を書き込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="52d01-148">For example, you cannot write some information to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance and different information to a text file.</span></span>  
  
### <a name="options"></a><span data-ttu-id="52d01-149">オプション</span><span class="sxs-lookup"><span data-stu-id="52d01-149">Options</span></span>  
 <span data-ttu-id="52d01-150">**イベント**</span><span class="sxs-lookup"><span data-stu-id="52d01-150">**Events**</span></span>  
 <span data-ttu-id="52d01-151">イベントのログ記録を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="52d01-151">Enable or disable events for logging.</span></span>  
  
 <span data-ttu-id="52d01-152">**説明**</span><span class="sxs-lookup"><span data-stu-id="52d01-152">**Description**</span></span>  
 <span data-ttu-id="52d01-153">イベントの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="52d01-153">View a description of the event.</span></span>  
  
 <span data-ttu-id="52d01-154">**詳細**</span><span class="sxs-lookup"><span data-stu-id="52d01-154">**Advanced**</span></span>  
 <span data-ttu-id="52d01-155">ログ記録するイベントをオンまたはオフにし、各イベントでログ記録する情報をオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="52d01-155">Select or clear events to log, and select or clear information to log for each event.</span></span> <span data-ttu-id="52d01-156">**[標準]** をクリックすると、ログの詳細情報がイベントの一覧を除いてすべて非表示になります。</span><span class="sxs-lookup"><span data-stu-id="52d01-156">Click **Basic** to hide all logging details, except the list of events.</span></span> <span data-ttu-id="52d01-157">次の情報をログ記録できます。</span><span class="sxs-lookup"><span data-stu-id="52d01-157">The following information is available for logging:</span></span>  
  
|<span data-ttu-id="52d01-158">値</span><span class="sxs-lookup"><span data-stu-id="52d01-158">Value</span></span>|<span data-ttu-id="52d01-159">説明</span><span class="sxs-lookup"><span data-stu-id="52d01-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="52d01-160">**コンピューター**</span><span class="sxs-lookup"><span data-stu-id="52d01-160">**Computer**</span></span>|<span data-ttu-id="52d01-161">ログ記録されたイベントが発生したコンピューターの名前。</span><span class="sxs-lookup"><span data-stu-id="52d01-161">The name of the computer on which the logged event occurred.</span></span>|  
|<span data-ttu-id="52d01-162">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="52d01-162">**Operator**</span></span>|<span data-ttu-id="52d01-163">パッケージを起動した人物のユーザー名。</span><span class="sxs-lookup"><span data-stu-id="52d01-163">The user name of the person who started the package.</span></span>|  
|<span data-ttu-id="52d01-164">**[SourceName]**</span><span class="sxs-lookup"><span data-stu-id="52d01-164">**SourceName**</span></span>|<span data-ttu-id="52d01-165">ログ記録されたイベントが発生したパッケージ、コンテナー、またはタスクの名前。</span><span class="sxs-lookup"><span data-stu-id="52d01-165">The name of the package, container, or task in which the logged event occurred.</span></span>|  
|<span data-ttu-id="52d01-166">**[SourceID]**</span><span class="sxs-lookup"><span data-stu-id="52d01-166">**SourceID**</span></span>|<span data-ttu-id="52d01-167">ログ記録されたイベントが発生したパッケージ、コンテナー、またはタスクの GUID (global unique identifier)。</span><span class="sxs-lookup"><span data-stu-id="52d01-167">The global unique identifier (GUID) of the package, container, or task in which the logged event occurred.</span></span>|  
|<span data-ttu-id="52d01-168">**[ExecutionID]**</span><span class="sxs-lookup"><span data-stu-id="52d01-168">**ExecutionID**</span></span>|<span data-ttu-id="52d01-169">パッケージ実行インスタンスの GUID。</span><span class="sxs-lookup"><span data-stu-id="52d01-169">The global unique identifier of the package execution instance.</span></span>|  
|<span data-ttu-id="52d01-170">**[MessageText]**</span><span class="sxs-lookup"><span data-stu-id="52d01-170">**MessageText**</span></span>|<span data-ttu-id="52d01-171">ログ エントリに関連付けられているメッセージ。</span><span class="sxs-lookup"><span data-stu-id="52d01-171">A message associated with the log entry.</span></span>|  
|<span data-ttu-id="52d01-172">**[DataBytes]**</span><span class="sxs-lookup"><span data-stu-id="52d01-172">**DataBytes**</span></span>|<span data-ttu-id="52d01-173">将来利用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="52d01-173">Reserved for future use.</span></span>|  
  
 <span data-ttu-id="52d01-174">**Basic**</span><span class="sxs-lookup"><span data-stu-id="52d01-174">**Basic**</span></span>  
 <span data-ttu-id="52d01-175">ログ記録するイベントをオンまたはオフにします。</span><span class="sxs-lookup"><span data-stu-id="52d01-175">Select or clear events to log.</span></span> <span data-ttu-id="52d01-176">イベントの一覧を除いて、ログの詳細情報が非表示になります。</span><span class="sxs-lookup"><span data-stu-id="52d01-176">This option hides logging details except the list of events.</span></span> <span data-ttu-id="52d01-177">イベントを選択すると、既定でそのイベントのすべてのログ詳細情報が選択されます。</span><span class="sxs-lookup"><span data-stu-id="52d01-177">If you select an event, all logging details are selected for the event by default.</span></span> <span data-ttu-id="52d01-178">**[詳細設定]** をクリックすると、ログの詳細情報がすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="52d01-178">Click **Advanced** to show all logging details.</span></span>  
  
 <span data-ttu-id="52d01-179">**[読み込み]**</span><span class="sxs-lookup"><span data-stu-id="52d01-179">**Load**</span></span>  
 <span data-ttu-id="52d01-180">ログのオプションを設定するテンプレートとして使用される、既存の XML ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="52d01-180">Specify an existing XML file to use as a template for setting logging options.</span></span>  
  
 <span data-ttu-id="52d01-181">**および**</span><span class="sxs-lookup"><span data-stu-id="52d01-181">**Save**</span></span>  
 <span data-ttu-id="52d01-182">構成の詳細をテンプレートとして XML ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="52d01-182">Save configuration details as a template to an XML file.</span></span>  
  
  
