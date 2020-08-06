---
title: レプリケーション管理オブジェクトの概念 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- replication [SQL Server], RMO
- programming interfaces [SQL Server replication]
- replication [SQL Server], how-to topics
- RMO [SQL Server]
- Replication Management Objects
- programming [SQL Server replication], RMO
ms.assetid: 37476d50-fb47-49e3-9504-3b163ac381d8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0dc41416e0fb585db376c6b72f28f7c30cfff052
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640882"
---
# <a name="replication-management-objects-concepts"></a><span data-ttu-id="cb914-102">Replication Management Objects Concepts</span><span class="sxs-lookup"><span data-stu-id="cb914-102">Replication Management Objects Concepts</span></span>
  <span data-ttu-id="cb914-103">レプリケーション管理オブジェクト (RMO) は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレプリケーション機能をカプセル化するマネージド コード アセンブリです。</span><span class="sxs-lookup"><span data-stu-id="cb914-103">Replication Management Objects (RMO) is a managed code assembly that encapsulates replication functionalities for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cb914-104">RMO は <xref:Microsoft.SqlServer.Replication> 名前空間により実装されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-104">RMO is implemented by the <xref:Microsoft.SqlServer.Replication> namespace.</span></span>  
  
 <span data-ttu-id="cb914-105">以下のセクションのトピックでは、レプリケーション タスクをプログラムから制御する場合の RMO の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb914-105">The topics in the following sections describe how you can use RMO to programmatically control replication tasks:</span></span>  
  
 <span data-ttu-id="cb914-106">[[ディストリビューションの構成]](../configure-distribution.md)</span><span class="sxs-lookup"><span data-stu-id="cb914-106">[Configure Distribution](../configure-distribution.md)</span></span>  
 <span data-ttu-id="cb914-107">このセクションのトピックでは、RMO を使用してパブリッシングおよびディストリビューションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb914-107">Topics in this section show how to use RMO to configure publishing and distribution.</span></span>  
  
 [<span data-ttu-id="cb914-108">パブリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="cb914-108">Create a Publication</span></span>](../publish/create-a-publication.md)  
 <span data-ttu-id="cb914-109">このセクションのトピックでは、RMO を使用してパブリケーションおよびアーティクルを作成、削除、および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb914-109">Topics in this section show how to use RMO to create, delete, and modify publications and articles.</span></span>  
  
 [<span data-ttu-id="cb914-110">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="cb914-110">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
 <span data-ttu-id="cb914-111">このセクションのトピックでは、RMO を使用してサブスクリプションを作成、削除、および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb914-111">Topics in this section show how to use RMO to create, delete, and modify subscriptions.</span></span>  
  
 [<span data-ttu-id="cb914-112">レプリケーション トポロジのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="cb914-112">Secure a Replication Topology</span></span>](../security/view-and-modify-replication-security-settings.md)  
 <span data-ttu-id="cb914-113">このセクションのトピックでは、RMO を使用してセキュリティ設定を表示および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb914-113">Topics in this section show how to use RMO to view and modify security settings.</span></span>  
  
 [<span data-ttu-id="cb914-114">サブスクリプションの同期 &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="cb914-114">Synchronize Subscriptions &#40;Replication&#41;</span></span>](../synchronize-data.md)  
 <span data-ttu-id="cb914-115">ここでは、サブスクリプションを同期する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="cb914-115">Topics in this section show how to synchronize subscriptions.</span></span>  
  
 [<span data-ttu-id="cb914-116">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="cb914-116">Monitoring Replication</span></span>](../monitoring-replication.md)  
 <span data-ttu-id="cb914-117">ここでは、プログラムからレプリケーション トポロジを監視する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="cb914-117">Topics in this section show how to programmatically monitor a replication topology.</span></span>  
  
## <a name="introduction-to-rmo-programming"></a><span data-ttu-id="cb914-118">RMO プログラミングの概要</span><span class="sxs-lookup"><span data-stu-id="cb914-118">Introduction to RMO Programming</span></span>  
 <span data-ttu-id="cb914-119">RMO は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションのすべての機能をプログラミングできるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="cb914-119">RMO is designed for programming all aspects of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replication.</span></span> <span data-ttu-id="cb914-120">RMO の名前空間は <xref:Microsoft.SqlServer.Replication> です。これは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework アセンブリである Microsoft.SqlServer.Rmo.dll により実装されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-120">The RMO namespace is <xref:Microsoft.SqlServer.Replication>, and it is implemented by the Microsoft.SqlServer.Rmo.dll, which is a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework assembly.</span></span> <span data-ttu-id="cb914-121">同様に <xref:Microsoft.SqlServer.Replication> 名前空間に属している Microsoft.SqlServer.Replication.dll アセンブリにより、さまざまなレプリケーション エージェント (スナップショット エージェント、ディストリビューション エージェント、マージ エージェント) のプログラミングのためのマネージド コード インターフェイスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-121">The Microsoft.SqlServer.Replication.dll assembly, which also belongs to the <xref:Microsoft.SqlServer.Replication> namespace, implements a managed code interface for programming the various replication agents (Snapshot Agent, Distribution Agent, and Merge Agent).</span></span> <span data-ttu-id="cb914-122">そのクラスには RMO からアクセスしてサブスクリプションを同期できます。</span><span class="sxs-lookup"><span data-stu-id="cb914-122">Its classes can be accessed from RMO to synchronize subscriptions.</span></span> <span data-ttu-id="cb914-123">Microsoft.SqlServer.Replication.BusinessLogicSupport.dll アセンブリにより実装される、<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 名前空間のクラスを使用して、マージ レプリケーション用のカスタム ビジネス ロジックを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cb914-123">Classes in the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> namespace, implemented by the Microsoft.SqlServer.Replication.BusinessLogicSupport.dll assembly, are used to create custom business logic for merge replication.</span></span> <span data-ttu-id="cb914-124">このアセンブリは RMO から独立しています。</span><span class="sxs-lookup"><span data-stu-id="cb914-124">This assembly is independent from RMO.</span></span>  
  
## <a name="deploying-applications-based-on-rmo"></a><span data-ttu-id="cb914-125">RMO に基づくアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="cb914-125">Deploying Applications Based on RMO</span></span>  
 <span data-ttu-id="cb914-126">RMO は、SQL Server Compact を除く [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のすべてのバージョンに含まれるレプリケーション コンポーネントとクライアント接続コンポーネントに依存しています。</span><span class="sxs-lookup"><span data-stu-id="cb914-126">RMO depends on the replication components and client connectivity components that are included with all versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] except SQL Server Compact.</span></span> <span data-ttu-id="cb914-127">RMO に基づいてアプリケーションを配置するには、アプリケーションを実行するコンピューターに、レプリケーション コンポーネントとクライアント接続コンポーネントを含むバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb914-127">To deploy an application based on RMO, you must install a version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that includes replication components and client connectivity components on the computer on which the application will run.</span></span>  
  
## <a name="getting-started-with-rmo"></a><span data-ttu-id="cb914-128">RMO の概要</span><span class="sxs-lookup"><span data-stu-id="cb914-128">Getting Started with RMO</span></span>  
 <span data-ttu-id="cb914-129">ここでは、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio を使用して単純な RMO プロジェクトを開始する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="cb914-129">This section describes how to start a simple RMO project using [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio.</span></span>  
  
#### <a name="to-create-a-new-microsoft-visual-c-project"></a><span data-ttu-id="cb914-130">新しい Microsoft Visual C# プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="cb914-130">To create a new Microsoft Visual C# project</span></span>  
  
1.  <span data-ttu-id="cb914-131">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="cb914-131">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="cb914-132">**[ファイル]** メニューの **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-132">On the **File** menu, click **NewProject.**</span></span> <span data-ttu-id="cb914-133">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-133">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="cb914-134">**[プロジェクトの種類]** ダイアログ ボックスで **[Visual C# プロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb914-134">In the **Project Types** dialog box, select **Visual C# Projects**.</span></span> <span data-ttu-id="cb914-135">**[テンプレート]** ウィンドウで **[Windows アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb914-135">In the **Templates** pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="cb914-136">(省略可) **[名前]** に、新しいアプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb914-136">(Optional) In **Name**, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="cb914-137">**[OK]** をクリックして、Visual C# Windows テンプレートを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="cb914-137">Click **OK** to load the Visual C# Windows template.</span></span>  
  
6.  <span data-ttu-id="cb914-138">**[プロジェクト]** メニューの **[参照の追加]** 項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb914-138">On the **Project** menu, select **Add Reference** item.</span></span> <span data-ttu-id="cb914-139">**[参照の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-139">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="cb914-140">**[.NET]** タブの一覧から、次のアセンブリを選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-140">Select the following assemblies from the list on the **.NET** tab, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="cb914-141">Microsoft.SqlServer.Replication .NET プログラミング インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb914-141">Microsoft.SqlServer.Replication .NET Programming Interface</span></span>  
  
    -   <span data-ttu-id="cb914-142">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="cb914-142">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
    -   <span data-ttu-id="cb914-143">レプリケーション エージェント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="cb914-143">Replication Agent Library</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb914-144">複数のファイルを選択するには、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながら各ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-144">Use the CTRL key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="cb914-145">(省略可) 手順 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="cb914-145">(Optional) Repeat step 6.</span></span> <span data-ttu-id="cb914-146">**[参照]** タブをクリックして [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM に移動し、Microsoft.SqlServer.Replication.BusinessLogicSupport.dll を選択した後、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-146">Click the **Browse** tab, navigate to [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM, select Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="cb914-147">**[表示]** メニューの **[コード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-147">On the **View** menu, click **Code**.</span></span>  
  
10. <span data-ttu-id="cb914-148">コード内で、名前空間のステートメントの前に次の `using` ステートメントを入力し、RMO 名前空間内の型を修飾します。</span><span class="sxs-lookup"><span data-stu-id="cb914-148">In the code, before the namespace statement, type the following `using` statements to qualify the types in the RMO namespaces:</span></span>  
  
    ```  
    // These namespaces are required.  
    using Microsoft.SqlServer.Replication;  
    using Microsoft.SqlServer.Management.Common;  
    // This namespace is only used when creating custom business  
    // logic for merge replication.  
    using Microsoft.SqlServer.Replication.BusinessLogicSupport;   
    ```  
  
#### <a name="to-create-a-new-microsoft-visual-basic-net-project"></a><span data-ttu-id="cb914-149">新しい Microsoft Visual Basic .NET プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="cb914-149">To create a new Microsoft Visual Basic .NET project</span></span>  
  
1.  <span data-ttu-id="cb914-150">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="cb914-150">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="cb914-151">**[ファイル]** メニューの **[新しいプロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb914-151">On the **File** menu, select **New Project**.</span></span> <span data-ttu-id="cb914-152">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-152">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="cb914-153">[プロジェクトの種類] ウィンドウで **[Visual Basic]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb914-153">In the Project Types pane, select **Visual Basic**.</span></span> <span data-ttu-id="cb914-154">[テンプレート] ウィンドウで **[Windows アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb914-154">In the Templates pane, select **Windows Application**.</span></span>  
  
4.  <span data-ttu-id="cb914-155">(省略可) **[名前]** ボックスに、新しいアプリケーションの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="cb914-155">(Optional) In the **Name** box, type the name of the new application.</span></span>  
  
5.  <span data-ttu-id="cb914-156">**[OK]** をクリックして、Visual Basic Windows テンプレートを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="cb914-156">Click **OK** to load the Visual Basic Windows template.</span></span>  
  
6.  <span data-ttu-id="cb914-157">**[プロジェクト]** メニューの **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cb914-157">On the **Project** menu, select **Add Reference**.</span></span> <span data-ttu-id="cb914-158">**[参照の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-158">The **Add Reference** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="cb914-159">**[.NET]** タブの一覧から、次のアセンブリを選択して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-159">Select the following assemblies from the list on the **.NET** tab, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="cb914-160">Microsoft.SqlServer.Replication .NET プログラミング インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb914-160">Microsoft.SqlServer.Replication .NET Programming Interface</span></span>  
  
    -   <span data-ttu-id="cb914-161">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="cb914-161">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
    -   <span data-ttu-id="cb914-162">レプリケーション エージェント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="cb914-162">Replication Agent Library</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb914-163">複数のファイルを選択するには、&lt;localizedText&gt;Ctrl&lt;/localizedText&gt; キーを押しながら各ファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-163">Use the CTRL key to select more than one file.</span></span>  
  
8.  <span data-ttu-id="cb914-164">(省略可) 手順 6. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="cb914-164">(Optional) Repeat step 6.</span></span> <span data-ttu-id="cb914-165">**[参照]** タブをクリックして [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM に移動し、Microsoft.SqlServer.Replication.BusinessLogicSupport.dll を選択した後、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-165">Click the **Browse** tab, navigate to [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM, select Microsoft.SqlServer.Replication.BusinessLogicSupport.dll, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="cb914-166">**[表示]** メニューの **[コード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cb914-166">On the **View** menu, click **Code**.</span></span>  
  
10. <span data-ttu-id="cb914-167">コード内で、すべての宣言の前に次の `Imports` ステートメントを入力し、RMO 名前空間内の型を修飾します。</span><span class="sxs-lookup"><span data-stu-id="cb914-167">In the code, before any declarations, type the following `Imports` statements to qualify the types in the RMO namespaces.</span></span>  
  
    ```  
    ' These namespaces are required.  
    Imports Microsoft.SqlServer.Replication  
    Imports Microsoft.SqlServer.Management.Common  
    ' This namespace is only used when creating custom business  
    ' logic for merge replication.  
    Imports Microsoft.SqlServer.Replication.BusinessLogicSupport   
    ```  
  
## <a name="connecting-to-a-replication-server"></a><span data-ttu-id="cb914-168">レプリケーション サーバーへの接続</span><span class="sxs-lookup"><span data-stu-id="cb914-168">Connecting to a Replication Server</span></span>  
 <span data-ttu-id="cb914-169">RMO プログラミング オブジェクトでは、<xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスのインスタンスを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスへの接続を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb914-169">RMO programming objects require that a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is made by using an instance of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span> <span data-ttu-id="cb914-170">サーバーへの接続は、RMO プログラミング オブジェクトとは別に作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-170">This connection to the server is made independently of any RMO programming objects.</span></span> <span data-ttu-id="cb914-171">接続はインスタンスの作成中に RMO オブジェクトに渡されるか、オブジェクトの <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに割り当てることで渡されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-171">It is then passed to the RMO object either during instance creation or by assignment to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the object.</span></span> <span data-ttu-id="cb914-172">この方法では、RMO プログラミング オブジェクトおよび接続オブジェクト インスタンスを別々に作成および管理することが可能となり、単一の接続オブジェクトを複数の RMO プログラミング オブジェクトと共に再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="cb914-172">In this manner, an RMO programming object and the connection object instances can be created and managed separately, and a single connection object can be reused with multiple RMO programming objects.</span></span> <span data-ttu-id="cb914-173">レプリケーション サーバーへの接続には、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-173">The following rules apply for connections to a replication server:</span></span>  
  
-   <span data-ttu-id="cb914-174">指定された <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトに、すべての接続プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="cb914-174">All properties for the connection are defined for a given <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="cb914-175">各 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに対する接続に、それぞれ独自の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb914-175">A connection to each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] must have its own <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="cb914-176"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトが、サーバー上で作成またはアクセスされる RMO プログラミング オブジェクトの <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cb914-176">The <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object is assigned to the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property of the RMO programming object being created or accessed on the server.</span></span>  
  
-   <span data-ttu-id="cb914-177"><xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> メソッドにより、サーバーへの接続が開かれます。</span><span class="sxs-lookup"><span data-stu-id="cb914-177">The <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Connect%2A> method opens the connection to the server.</span></span> <span data-ttu-id="cb914-178">接続を使用してサーバー上の RMO プログラミング オブジェクトにアクセスするメソッドを呼び出す前に、このメソッドを呼び出しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb914-178">This method must be called before calling any methods that access the server on any RMO programming objects using the connection.</span></span>  
  
-   <span data-ttu-id="cb914-179">RMO でも SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト) でも、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] への接続には <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用するため、RMO オブジェクトと SMO オブジェクトの両方で同じ接続を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb914-179">Because RMO and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO) both use the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class for connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the same connection can be used by both RMO and SMO objects.</span></span> <span data-ttu-id="cb914-180">詳細については、「[SQL Server のインスタンスへの接続](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb914-180">For more information, see [Connecting to an Instance of SQL Server](../../server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md).</span></span>  
  
-   <span data-ttu-id="cb914-181">接続を作成し、サーバーに正常にログオンするための認証情報はすべて <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトで指定されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-181">All authentication information to make the connection and successfully log on to the server is supplied in the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object.</span></span>  
  
-   <span data-ttu-id="cb914-182">既定は Windows 認証です。</span><span class="sxs-lookup"><span data-stu-id="cb914-182">Windows Authentication is the default.</span></span> <span data-ttu-id="cb914-183">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 認証を使用するには、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> を `false` に設定し、<xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> および <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> に有効な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ログインおよびパスワードを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb914-183">To use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication, <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.LoginSecure%2A> must be set to `false` and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Login%2A> and <xref:Microsoft.SqlServer.Management.Common.ConnectionSettings.Password%2A> must be set to a valid [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logon and password.</span></span> <span data-ttu-id="cb914-184">セキュリティ資格情報は常にセキュリティ保護された状態で保存し、処理する必要があります。可能な限り、実行時に入力するようにします。</span><span class="sxs-lookup"><span data-stu-id="cb914-184">Security credentials must always be stored and handled securely, and supplied at run-time whenever possible.</span></span>  
  
-   <span data-ttu-id="cb914-185">マルチスレッド化されたアプリケーションの場合、各スレッドで別々の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb914-185">For multithreaded applications, a separate <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object should be used in each thread.</span></span>  
  
 <span data-ttu-id="cb914-186">RMO オブジェクトで使用された、アクティブなサーバー接続を閉じるには、<xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> オブジェクトに対して <xref:Microsoft.SqlServer.Management.Common.ServerConnection> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cb914-186">Call the <xref:Microsoft.SqlServer.Management.Common.ConnectionManager.Disconnect%2A> method on the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object to close active server connections used by RMO objects.</span></span>  
  
## <a name="setting-rmo-properties"></a><span data-ttu-id="cb914-187">RMO プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="cb914-187">Setting RMO Properties</span></span>  
 <span data-ttu-id="cb914-188">RMO プログラミング オブジェクトのプロパティは、サーバー上のこれらのレプリケーション オブジェクトのプロパティを表します。</span><span class="sxs-lookup"><span data-stu-id="cb914-188">The properties of RMO programming objects represent the properties of these replication objects at the server.</span></span> <span data-ttu-id="cb914-189">サーバー上に新しいレプリケーション オブジェクトを作成するとき、RMO プロパティを使用してこれらのオブジェクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="cb914-189">When creating new replication objects at the server, RMO properties are used to define these objects.</span></span> <span data-ttu-id="cb914-190">既存のオブジェクトの場合、RMO プロパティは既存のオブジェクトのプロパティを表しますが、変更できるのは書き込み可能または設定可能なプロパティのみです。</span><span class="sxs-lookup"><span data-stu-id="cb914-190">For existing objects, the RMO properties represent the existing object's properties, which can be modified only for properties that are writable or settable.</span></span> <span data-ttu-id="cb914-191">プロパティは、新しいオブジェクトまたは既存のオブジェクトに設定できます。</span><span class="sxs-lookup"><span data-stu-id="cb914-191">Properties can be set on new objects or existing objects.</span></span>  
  
### <a name="setting-properties-for-new-replication-objects"></a><span data-ttu-id="cb914-192">新しいレプリケーション オブジェクトのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="cb914-192">Setting Properties for New Replication Objects</span></span>  
 <span data-ttu-id="cb914-193">サーバーに新しいレプリケーション オブジェクトを作成する際、必要なプロパティをすべて指定した後で、オブジェクトの `Create` メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb914-193">When creating a new replication object at the server, you must specify all required properties before calling the `Create` method of the object.</span></span> <span data-ttu-id="cb914-194">新しいレプリケーション オブジェクトのプロパティの設定の詳細については、「[Configure Publishing and Distribution](../configure-publishing-and-distribution.md)」 (パブリッシングとディストリビューションの構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb914-194">For more information about setting properties for a new replication object, see [Configure Publishing and Distribution](../configure-publishing-and-distribution.md).</span></span>  
  
### <a name="setting-properties-for-existing-replication-objects"></a><span data-ttu-id="cb914-195">既存のレプリケーション オブジェクトのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="cb914-195">Setting Properties for Existing Replication Objects</span></span>  
 <span data-ttu-id="cb914-196">サーバー上に存在するレプリケーション オブジェクトの場合、RMO ではオブジェクトの種類に応じて、プロパティの一部またはすべてを変更することがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="cb914-196">For replication objects that exist at the server, depending on the object, RMO might support the ability to change some or all of its properties.</span></span> <span data-ttu-id="cb914-197">書き込み可能または設定可能なプロパティのみを変更できます。</span><span class="sxs-lookup"><span data-stu-id="cb914-197">Only writable or settable properties can be changed.</span></span> <span data-ttu-id="cb914-198">プロパティを変更するには、`Load` または <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出して、サーバーから現在のプロパティを取得しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb914-198">Before properties can be changed, either the `Load` or the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method must be called to get the current properties from the server.</span></span> <span data-ttu-id="cb914-199">これらのメソッドを呼び出すことは、既存のオブジェクトが変更されることを表します。</span><span class="sxs-lookup"><span data-stu-id="cb914-199">Calling these methods indicates that an existing object is being modified.</span></span>  
  
 <span data-ttu-id="cb914-200">既定では、オブジェクトのプロパティを変更するときに、使用される <xref:Microsoft.SqlServer.Management.Common.ServerConnection> の実行モードに基づいてこれらの変更がサーバーにコミットされます。</span><span class="sxs-lookup"><span data-stu-id="cb914-200">By default, when changing object properties, RMO commits these changes to the server based on the execution mode of the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> being used.</span></span> <span data-ttu-id="cb914-201">オブジェクトのプロパティを取得または変更する前に、<xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> メソッドを使用して、そのオブジェクトがサーバー上に存在するかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="cb914-201">The <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> method can be used to verify that an object exists at the server before attempting to retrieve or change its properties.</span></span> <span data-ttu-id="cb914-202">レプリケーション オブジェクトのプロパティの変更方法の詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../view-and-modify-distributor-and-publisher-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb914-202">For more information about changing the properties of a replication object, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cb914-203">複数の RMO クライアントまたは複数の RMO プログラミング オブジェクト インスタンスが、サーバー上の同じレプリケーション オブジェクトにアクセスする場合、RMO オブジェクトの `Refresh` メソッドを呼び出して、サーバー上のオブジェクトの現在の状態に基づいてプロパティを更新できます。</span><span class="sxs-lookup"><span data-stu-id="cb914-203">When multiple RMO clients or multiple instances of an RMO programming object are accessing the same replication object at the server, the `Refresh` method of the RMO object can be called to update the properties based on the current state of the object at the server.</span></span>  
  
### <a name="caching-property-changes"></a><span data-ttu-id="cb914-204">プロパティの変更のキャッシュ</span><span class="sxs-lookup"><span data-stu-id="cb914-204">Caching Property Changes</span></span>  
 <span data-ttu-id="cb914-205"><xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> プロパティが <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql> に設定されている場合、RMO により生成されるすべての [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントがキャプチャされ、いずれかの実行メソッドを使用して 1 つのバッチで手動で実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb914-205">When the <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes> property is set to <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes.CaptureSql> all [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements generated by RMO are captured so that they can be executed manually in a single batch by using one of the execution methods.</span></span> <span data-ttu-id="cb914-206">RMO を使用するとプロパティの変更をキャッシュでき、オブジェクトの <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを使用して 1 つのバッチでまとめてコミットできます。</span><span class="sxs-lookup"><span data-stu-id="cb914-206">RMO lets you cache property changes and commit them together in a single batch by using the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method of the object.</span></span> <span data-ttu-id="cb914-207">プロパティの変更をキャッシュするには、オブジェクトの <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> プロパティを `true` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb914-207">To cache property changes, the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> property of the object must be set to `true`.</span></span> <span data-ttu-id="cb914-208">RMO におけるプロパティの変更がキャッシュされる場合でも、変更がいつサーバーに送られるのかは <xref:Microsoft.SqlServer.Management.Common.ServerConnection> オブジェクトによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="cb914-208">When caching property changes in RMO, the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object still controls when changes are sent to the server.</span></span> <span data-ttu-id="cb914-209">レプリケーション オブジェクトのプロパティのキャッシュの詳細については、「[ディストリビューターとパブリッシャーのプロパティの表示および変更](../view-and-modify-distributor-and-publisher-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb914-209">For more information about caching property changes for a replication object, see [View and Modify Distributor and Publisher Properties](../view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cb914-210"><xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスでは、プロパティを設定するときに明示的なトランザクションの宣言がサポートされますが、そのようなトランザクションでは内部的なレプリケーション トランザクションに干渉する場合があるため、予期しない結果が生じる可能性があります。RMO では使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="cb914-210">Although the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class supports declaring explicit transactions when setting properties, such transactions may interfere with internal replication transactions, can produce unanticipated results, and should not be used with RMO.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb914-211">例</span><span class="sxs-lookup"><span data-stu-id="cb914-211">Example</span></span>  
 <span data-ttu-id="cb914-212">この例では、プロパティ変更のキャッシュを示します。</span><span class="sxs-lookup"><span data-stu-id="cb914-212">This example demonstrates the caching of property changes.</span></span> <span data-ttu-id="cb914-213">トランザクション パブリケーションの属性に加えられた変更は、明示的にサーバーに送られるまでキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="cb914-213">Changes made to the attributes of a transactional publication are cached until they are explicitly sent to the server.</span></span>  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_ChangeTranPub_cached)]  
  
## <a name="see-also"></a><span data-ttu-id="cb914-214">参照</span><span class="sxs-lookup"><span data-stu-id="cb914-214">See Also</span></span>  
 <span data-ttu-id="cb914-215">[Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="cb914-215">[Replication System Stored Procedures Concepts](replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="cb914-216">レプリケーションのプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="cb914-216">Replication Programming Concepts</span></span>](replication-programming-concepts.md)  
  
  
