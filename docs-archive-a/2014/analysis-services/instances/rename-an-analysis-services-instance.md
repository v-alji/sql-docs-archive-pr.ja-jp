---
title: Analysis Services インスタンスの名前を変更する |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 763986d82dda7424f2187daf401424fd256ddd64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716930"
---
# <a name="rename-an-analysis-services-instance"></a><span data-ttu-id="b049c-102">Analysis Services インスタンスの名前変更</span><span class="sxs-lookup"><span data-stu-id="b049c-102">Rename an Analysis Services Instance</span></span>
  <span data-ttu-id="b049c-103">の既存のインスタンスの名前を変更する [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、[**インスタンス名の変更**] ダイアログボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b049c-103">You can rename an existing instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] by using the **Rename Instance** dialog box.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b049c-104">インスタンスの名前を変更しているとき、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool が高度な特権で実行され、インスタンスに関連付けられている Windows サービス名、セキュリティ アカウント、およびレジストリ エントリが更新されます。</span><span class="sxs-lookup"><span data-stu-id="b049c-104">While renaming the instance, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool runs under elevated privileges, updating the Windows service name, security accounts, and registry entries associated with that instance.</span></span> <span data-ttu-id="b049c-105">これらのアクションを確実に実行するため、このツールは必ずローカルのシステム管理者として実行してください。</span><span class="sxs-lookup"><span data-stu-id="b049c-105">To ensure that these actions are performed, be sure to run this tool as a local system administrator.</span></span>  
  
 <span data-ttu-id="b049c-106">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool では、元のインスタンスのために作成されたプログラム フォルダーは変更されません。</span><span class="sxs-lookup"><span data-stu-id="b049c-106">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool does not modify the program folder that was created for the original instance.</span></span> <span data-ttu-id="b049c-107">変更後のインスタンス名に合わせてプログラムのフォルダー名を変更することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="b049c-107">Do not modify the program folder name to match the instance you are renaming.</span></span> <span data-ttu-id="b049c-108">プログラム フォルダーの名前を変更すると、セットアップ プログラムによるインストールの修復やアンインストールに支障が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b049c-108">Changing a program folder name can prevent Setup from repairing or uninstalling the installation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b049c-109">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename Tool のクラスター環境での使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b049c-109">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instance Rename tool is not supported for use in a cluster environment.</span></span>  
  
### <a name="to-rename-an-instance-of-analysis-services"></a><span data-ttu-id="b049c-110">Analysis Services のインスタンス名を変更するには</span><span class="sxs-lookup"><span data-stu-id="b049c-110">To rename an instance of Analysis Services</span></span>  
  
1.  <span data-ttu-id="b049c-111">C:\Program Server\110\tools\binn\managementstudio SQL から**インスタンス名変更**ツール、 **asinstancerename.exe**を起動します。</span><span class="sxs-lookup"><span data-stu-id="b049c-111">Launch the **Instance Rename** tool, **asinstancerename.exe**, from C:\Program Files\Microsoft SQL Server\110\Tools\Binn\ManagementStudio.</span></span>  
  
2.  <span data-ttu-id="b049c-112">**[インスタンス名の変更]** ダイアログ ボックスの **[名前を変更するインスタンス]** 一覧で、名前を変更するインスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="b049c-112">In the **Rename Instance** dialog box, in the **Instance to rename** list, select the instance that you want to rename.</span></span>  
  
3.  <span data-ttu-id="b049c-113">**[新しいインスタンス名]** ボックスに、インスタンスの新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b049c-113">In the **New instance name** box, enter the new name for the instance.</span></span>  
  
4.  <span data-ttu-id="b049c-114">ユーザー名とパスワードが正しいことを確認して、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b049c-114">Verify that the user name and password are correct, and then click **Rename**.</span></span>  
  
     <span data-ttu-id="b049c-115">名前の変更には、Analysis Services インスタンスの停止と再起動が伴います。</span><span class="sxs-lookup"><span data-stu-id="b049c-115">The Analysis Services instance will be stopped and restarted as part of the name change.</span></span>  
  
### <a name="post-rename-checklist"></a><span data-ttu-id="b049c-116">名前変更後のチェック リスト</span><span class="sxs-lookup"><span data-stu-id="b049c-116">Post-rename checklist</span></span>  
  
1.  <span data-ttu-id="b049c-117">名前変更後のインスタンス上で実行されているデータベースに再度アクセスするためには、Excel などのクライアント アプリケーションからデータ接続を手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b049c-117">To resume access to databases that are running on the renamed instance, you will need to manually update the data connections in Excel or other client applications.</span></span> <span data-ttu-id="b049c-118">また、Reporting Services の共有データ ソース、Excel ODC ファイル、BI Semantic Model 接続ファイルなど、名前の変更されたインスタンスを参照している可能性のある定義済みの接続をすべてチェックしてください。</span><span class="sxs-lookup"><span data-stu-id="b049c-118">Also check any predefined connections, such as Reporting Services shared data sources, Excel ODC files, or BI Semantic Model connection files that might reference the instance you just renamed.</span></span> <span data-ttu-id="b049c-119">詳細については、「 [Analysis Services への接続](connect-to-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b049c-119">For more information, see [Connect to Analysis Services](connect-to-analysis-services.md).</span></span>  
  
2.  <span data-ttu-id="b049c-120">データベースのバックアップや同期、処理などに普段使用している PowerShell スクリプトまたは AMO スクリプトを更新します。</span><span class="sxs-lookup"><span data-stu-id="b049c-120">Update PowerShell scripts or AMO scripts that you routinely use to backup, synchronize, or process databases.</span></span>  
  
3.  <span data-ttu-id="b049c-121">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用する [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]プロジェクトのプロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="b049c-121">Update project properties for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projects that you work with in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="b049c-122">テーブル モードのサーバー インスタンスの場合は、model.bim ファイルの [ワークスペース サーバー] プロパティと、プロジェクトの [サーバー] プロパティを必ず更新してください。</span><span class="sxs-lookup"><span data-stu-id="b049c-122">For tabular mode server instances, be sure to update the Workspace Server property on the model.bim file, as well as the Server property on the project.</span></span>  
  
4.  <span data-ttu-id="b049c-123">サービス アカウントの指定方法によっては、データへのアクセス権をサービスに付与するデータベース ログインまたはファイル権限を更新する必要があります (サービス アカウントを使用してデータを処理する場合や、別のサーバー上のリンク オブジェクトにアクセスする場合など)。</span><span class="sxs-lookup"><span data-stu-id="b049c-123">Depending on how you specified the service account, you might need to update database logins or file permissions that grant data access rights to the service (for example, if you use the service account to process data or access linked objects on another server).</span></span>  
  
     <span data-ttu-id="b049c-124">仮想アカウントを使用してサービスを準備した場合は、データベース ログインまたはファイル権限を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b049c-124">Updating a database login or file permissions will be necessary if you used a virtual account to provision the service.</span></span> <span data-ttu-id="b049c-125">仮想アカウントはインスタンス名に依存するため、インスタンスの名前を変更した場合、同時に仮想アカウントも更新されます。</span><span class="sxs-lookup"><span data-stu-id="b049c-125">Virtual accounts are based on the instance name, so if you rename the instance, the virtual account is also updated at the same time.</span></span> <span data-ttu-id="b049c-126">つまり、変更前のインスタンス用に作成したログインや権限はすべて無効になります。</span><span class="sxs-lookup"><span data-stu-id="b049c-126">This means that any previous logins or permissions that you created for the previous instance are no longer valid.</span></span>  
  
     <span data-ttu-id="b049c-127">具体的な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b049c-127">The following example provides an illustration.</span></span> <span data-ttu-id="b049c-128">既定の仮想アカウントを使用して "表形式" という名前のインスタンスとしてテーブルモードサーバーをインストールしたとします。その結果、次のように構成されます。</span><span class="sxs-lookup"><span data-stu-id="b049c-128">Suppose you installed a tabular mode server as an instance named "Tabular" using the default virtual account, resulting in the following configuration:</span></span>  
  
    1.  <span data-ttu-id="b049c-129">インスタンス名 = \<server> \ 表形式</span><span class="sxs-lookup"><span data-stu-id="b049c-129">Instance name = \<server>\TABULAR</span></span>  
  
    2.  <span data-ttu-id="b049c-130">サービス名 = MSOLAP$TABULAR</span><span class="sxs-lookup"><span data-stu-id="b049c-130">Service name = MSOLAP$TABULAR</span></span>  
  
    3.  <span data-ttu-id="b049c-131">仮想アカウント = NT Service\ MSOLAP$TABULAR</span><span class="sxs-lookup"><span data-stu-id="b049c-131">Virtual account = NT Service\ MSOLAP$TABULAR</span></span>  
  
     <span data-ttu-id="b049c-132">ここで、インスタンスの名前を "TAB2" に変更したとします。</span><span class="sxs-lookup"><span data-stu-id="b049c-132">Now suppose you rename the instance to "TAB2".</span></span> <span data-ttu-id="b049c-133">名前を変更したことで、必要な構成も次のように変わります。</span><span class="sxs-lookup"><span data-stu-id="b049c-133">As a result of the name change, your configuration would now look like the following:</span></span>  
  
    1.  <span data-ttu-id="b049c-134">インスタンス名 = \<server> \ タブ2</span><span class="sxs-lookup"><span data-stu-id="b049c-134">Instance name = \<server>\TAB2</span></span>  
  
    2.  <span data-ttu-id="b049c-135">サービス名 = MSOLAP$TAB2</span><span class="sxs-lookup"><span data-stu-id="b049c-135">Service name = MSOLAP$TAB2</span></span>  
  
    3.  <span data-ttu-id="b049c-136">仮想アカウント = NT Service\ MSOLAP$TAB2</span><span class="sxs-lookup"><span data-stu-id="b049c-136">Virtual account = NT Service\ MSOLAP$TAB2</span></span>  
  
     <span data-ttu-id="b049c-137">ご覧のとおり、以前に "NT サービス \ MSOLAP $ 表形式" に許可されていたデータベースおよびファイルのアクセス許可は無効になりました。</span><span class="sxs-lookup"><span data-stu-id="b049c-137">As you can see, database and file permissions that were previously granted to "NT Service\ MSOLAP$TABULAR" are no longer valid.</span></span> <span data-ttu-id="b049c-138">サービスによって実行されるタスクと操作が以前と同じように実行されるようにするには、新しいデータベースとファイルのアクセス許可を "NT Service \ MSOLAP $ TAB2" に付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b049c-138">To ensure that tasks and operations performed by the service run as before, you would now need to grant new database and file permissions to "NT Service\ MSOLAP$TAB2".</span></span>  
  
  
