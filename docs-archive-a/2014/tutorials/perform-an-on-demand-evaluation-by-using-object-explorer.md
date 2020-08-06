---
title: オブジェクトエクスプローラー | を使用して要求時評価を実行します。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: ee6d3b79-18bc-49d3-8a1d-0c0905b990f0
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e32876978ac462af361986d84e11ef3dc0f278e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631415"
---
# <a name="perform-an-on-demand-evaluation-by-using-object-explorer"></a><span data-ttu-id="cd846-102">オブジェクト エクスプローラーを使用した要求時評価の実行</span><span class="sxs-lookup"><span data-stu-id="cd846-102">Perform an On-Demand Evaluation by Using Object Explorer</span></span>
  <span data-ttu-id="cd846-103">ここでは、オブジェクト エクスプローラーを使用して、[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] の単一インスタンス上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に対して、ベスト プラクティス ポリシーの要求時評価を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd846-103">In this task, you will use Object Explorer to perform an on-demand evaluation of best practices policies for the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] on a single instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd846-104">単一インスタンス上のポリシーの評価は、登録済みサーバーを通じて行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="cd846-104">You can also evaluate policies on a single instance through Registered Servers.</span></span> <span data-ttu-id="cd846-105">詳細については、「[登録済みサーバーを使用したオンデマンド評価の実行](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd846-105">For more information, see [Perform an On-Demand Evaluation by Using Registered Servers](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cd846-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="cd846-106">Prerequisites</span></span>  
 <span data-ttu-id="cd846-107">このレッスンでは、[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] の [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd846-107">This lesson is based on the version of [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd846-108">を実行しているインスタンスに対してベストプラクティスポリシーの要求時評価を実行するには、 [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] 「[登録済みサーバーを使用して要求時評価を実行](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)する」の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd846-108">To perform an on-demand evaluation of best practices policies against instances that are running [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], you must use the procedure in the topic [Perform an On-Demand Evaluation by Using Registered Servers](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md).</span></span>  
  
### <a name="to-perform-an-on-demand-evaluation-by-using-object-explorer"></a><span data-ttu-id="cd846-109">オブジェクト エクスプローラーを使用して要求時評価を実行するには</span><span class="sxs-lookup"><span data-stu-id="cd846-109">To perform an on-demand evaluation by using Object Explorer</span></span>  
  
1.  <span data-ttu-id="cd846-110">を起動 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] し、に接続し [!INCLUDE[ssDE](../includes/ssde-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="cd846-110">Start [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], and then connect to the [!INCLUDE[ssDE](../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cd846-111">オブジェクトエクスプローラーで、[**管理**]、[**ポリシー管理**] の順に展開し、[**ポリシー**] を右クリックして、[**評価**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-111">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Policies**, and then click **Evaluate**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cd846-112">既定では、ローカル インスタンスがポリシーのソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd846-112">By default, the local instance is used as the source of the policies.</span></span> <span data-ttu-id="cd846-113">ベスト プラクティス ポリシーを以前にインポートしている場合は、作成済みのポリシーがあれば、それと共に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd846-113">If you have previously imported best practices policies, they will be listed, together with any other policies that you have created.</span></span> <span data-ttu-id="cd846-114">インポートされたベストプラクティスポリシーを選択し、[**評価**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-114">You can select any of the imported best practices policies, and then click **Evaluate**.</span></span> <span data-ttu-id="cd846-115">ベスト プラクティス ポリシーをインポートしていない場合には、この手順を続行します。</span><span class="sxs-lookup"><span data-stu-id="cd846-115">If you have not imported the best practices policies, continue with this procedure.</span></span>  
  
3.  <span data-ttu-id="cd846-116">[**ポリシーの評価**] ダイアログボックスの [**ソース**] ボックスの横にある省略記号ボタン ([**...**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-116">In the **Evaluate Policies** dialog box, next to the **Source** box, click the ellipsis (**...**) button.</span></span>  
  
4.  <span data-ttu-id="cd846-117">[**ソースの選択**] ダイアログボックスで、評価するポリシーファイルのソースとして [**ファイル**] または [**サーバー** ] を選択できます。</span><span class="sxs-lookup"><span data-stu-id="cd846-117">In the **Select Source** dialog box, you can select either **Files** or **Server** as the source of the policy files to evaluate.</span></span> <span data-ttu-id="cd846-118">[**サーバー**] をクリックすると、以前にローカルサーバーまたはリモートサーバー上のポリシーベースの管理にインポートされたベストプラクティスポリシーの要求時評価を実行できます。</span><span class="sxs-lookup"><span data-stu-id="cd846-118">If you click **Server**, you can perform an on-demand evaluation of any best practices policies that were previously imported into Policy-Based Management on a local or remote server.</span></span> <span data-ttu-id="cd846-119">このチュートリアルでは、[**ファイル**] をクリックし、評価する個々のポリシーファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd846-119">In this tutorial, you will click **Files**, and then select the individual policy files that you want to evaluate.</span></span> <span data-ttu-id="cd846-120">そのためには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="cd846-120">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="cd846-121">[**ファイル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-121">Click **Files**.</span></span>  
  
    2.  <span data-ttu-id="cd846-122">[**ファイル**] の横にある省略記号ボタン ([.**..**]) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-122">Next to **Files**, click the ellipsis (**...**) button.</span></span>  
  
    3.  <span data-ttu-id="cd846-123">**[ポリシーの選択**] ダイアログボックスで、次のフォルダーに移動します。このフォルダーには、ベストプラクティスポリシーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cd846-123">In the **Select Policy** dialog box, browse to the following folder, which contains the best practices policies:</span></span>  
  
         <span data-ttu-id="cd846-124">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span><span class="sxs-lookup"><span data-stu-id="cd846-124">**C:\Program Files (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="cd846-125">ファイル パスは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プログラム ファイルのインストール先、32 ビットまたは 64 ビットのどちらのオペレーティング システムを実行しているか、および言語識別子によって異なることがあります。</span><span class="sxs-lookup"><span data-stu-id="cd846-125">The file path may vary, depending on where you installed the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] program files, whether you are running a 32-bit or 64-bit operating system, and the language identifier.</span></span>  
  
    4.  <span data-ttu-id="cd846-126">評価する1つまたは複数の .xml ポリシーファイルを選択し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-126">Select one or more .xml policy files to evaluate, and then click **Open**.</span></span>  
  
         <span data-ttu-id="cd846-127">選択したファイルの一覧が [**ファイル**] ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd846-127">The list of selected files appears in the **Files** box.</span></span>  
  
    5.  <span data-ttu-id="cd846-128">[**ソースの選択**] ダイアログボックスで、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-128">In the **Select Source** dialog box, click **OK**.</span></span>  
  
    6.  <span data-ttu-id="cd846-129">[**ポリシーの読み込み**] ダイアログボックスが表示されたら、[**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-129">If the **Loading Policies** dialog box appears, click **Close**.</span></span>  
  
     <span data-ttu-id="cd846-130">選択したポリシーは、[ポリシーの**選択**] ページに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd846-130">The policies that you selected are listed on the **Policy Selection** page.</span></span> <span data-ttu-id="cd846-131">ポリシーの横に警告アイコンが表示された場合、そのポリシーにスクリプトが含まれていることを示します。</span><span class="sxs-lookup"><span data-stu-id="cd846-131">Be aware that a warning icon next to a policy indicates that the policy contains scripts.</span></span>  
  
5.  <span data-ttu-id="cd846-132">[**評価**] をクリックしてポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="cd846-132">Click **Evaluate** to evaluate the policies.</span></span>  
  
     <span data-ttu-id="cd846-133">**結果**テーブルには、各ポリシーの結果が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd846-133">In the **Results** table, the results for each policy are listed.</span></span> <span data-ttu-id="cd846-134">赤い "x" アイコンは、ポリシーに準拠していないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="cd846-134">A red "x" icon indicates that policy compliance failed.</span></span>  
  
6.  <span data-ttu-id="cd846-135">一部のポリシー エラーでは、ポリシー ベースの管理機能によってポリシーへの準拠を対象に直ちに適用できます。</span><span class="sxs-lookup"><span data-stu-id="cd846-135">For some policy failures, Policy-Based Management enables you to immediately enforce policy compliance on the target.</span></span> <span data-ttu-id="cd846-136">このようなエラーの場合、エラーが発生したポリシーの横にチェック ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd846-136">For such failures, a check box will appear next to the failed policy.</span></span> <span data-ttu-id="cd846-137">チェックボックスをオンにすると、[**適用**] ボタンが使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cd846-137">If you select the check box, the **Apply** button becomes available.</span></span> <span data-ttu-id="cd846-138">[**適用**] をクリックすると、準拠していない設定がターゲットインスタンスで自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="cd846-138">When you click **Apply**, the noncompliant setting will be automatically updated on the target instance.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="cd846-139">ポリシー設定を十分に理解してから、対象インスタンスを自動更新してください。</span><span class="sxs-lookup"><span data-stu-id="cd846-139">Make sure that you fully understand the policy setting before automatically updating a target instance.</span></span> <span data-ttu-id="cd846-140">1つ以上のチェックボックスをオンにした後、[**スクリプト**] をクリックし、出力場所を選択して、変更を適用する前に基になるコードを確認できるようにすることをお勧めし [!INCLUDE[tsql](../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="cd846-140">We recommend that after you select one or more check boxes, you click **Script**, and choose an output location so that you can review the underlying [!INCLUDE[tsql](../includes/tsql-md.md)] code before you apply the changes.</span></span>  
  
7.  <span data-ttu-id="cd846-141">ポリシーの詳細な結果を表示するには、[**結果**] テーブルでポリシーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cd846-141">To view detailed results for a policy, click the policy in the **Results** table.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="cd846-142">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="cd846-142">Next Task in Lesson</span></span>  
 [<span data-ttu-id="cd846-143">登録済みサーバーを使用した要求時評価の実行</span><span class="sxs-lookup"><span data-stu-id="cd846-143">Perform an On-Demand Evaluation by Using Registered Servers</span></span>](../../2014/tutorials/perform-an-on-demand-evaluation-by-using-registered-servers.md)  
  
  
