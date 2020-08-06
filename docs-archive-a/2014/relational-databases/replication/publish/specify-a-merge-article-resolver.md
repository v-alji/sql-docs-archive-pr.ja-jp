---
title: マージ アーティクル競合回避モジュールの指定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
- merge replication conflict resolution [SQL Server replication], merge article resolvers
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ca32ef4936f31ca5c75dfc2df1eb965d17f7b039
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717853"
---
# <a name="specify-a-merge-article-resolver"></a><span data-ttu-id="2e9ff-102">マージ アーティクル競合回避モジュールの指定</span><span class="sxs-lookup"><span data-stu-id="2e9ff-102">Specify a Merge Article Resolver</span></span>
  <span data-ttu-id="2e9ff-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ アーティクル競合回避モジュールを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-103">This topic describes how to specify a merge article resolver in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="2e9ff-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="2e9ff-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="2e9ff-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="2e9ff-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="2e9ff-106">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="2e9ff-106">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="2e9ff-107">**マージ アーティクル競合回避モジュールを指定するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="2e9ff-107">**To specify a merge article resolver, using:**</span></span>  
  
     [<span data-ttu-id="2e9ff-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="2e9ff-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="2e9ff-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="2e9ff-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="2e9ff-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="2e9ff-110">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="2e9ff-111">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2e9ff-111">Recommendations</span></span>  
  
-   <span data-ttu-id="2e9ff-112">マージ レプリケーションでは、以下の競合回避モジュールが使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-112">Merge replication allows the following types of article resolvers:</span></span>  
  
    -   <span data-ttu-id="2e9ff-113">既定の競合回避モジュール。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-113">The default resolver.</span></span> <span data-ttu-id="2e9ff-114">既定の競合回避モジュールの動作は、サブスクリプションがクライアント サブスクリプションまたはサーバー サブスクリプションのどちらであるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-114">The behavior of the default resolver depends on whether the subscription is a client subscription or a server subscription.</span></span> <span data-ttu-id="2e9ff-115">サブスクリプションの種類の指定について詳しくは、「[マージ サブスクリプションの種類と競合解決の優先度の指定 &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-115">For more information about specifying subscription type, see [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../specify-a-merge-subscription-type-and-conflict-resolution-priority.md).</span></span>  
  
    -   <span data-ttu-id="2e9ff-116">ユーザーの作成したカスタム競合回避モジュール。ビジネス ロジック ハンドラー (マネージド コードで作成) または COM ベースのカスタム競合回避モジュールです。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-116">A custom resolver you have written, which can be a business logic handler (written in managed code) or a custom COM-based resolver.</span></span> <span data-ttu-id="2e9ff-117">詳細については、「 [マージ レプリケーションの競合検出および解決の詳細](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-117">For more information, see [Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span> <span data-ttu-id="2e9ff-118">競合する行だけでなく、レプリケートされた各行に対して実行するカスタム ロジックを実装する必要がある場合は、「 [マージ アーティクルのビジネス ロジック ハンドラーの実装](../implement-a-business-logic-handler-for-a-merge-article.md)を使用して、マージ アーティクル競合回避モジュールを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-118">If you need to implement custom logic that is executed for each replicated row, not just for conflicting rows, see [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="2e9ff-119">標準の COM ベース競合回避モジュール。[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に含まれています。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-119">A standard COM-based resolver, which is included with [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="2e9ff-120">既定以外の競合回避モジュールを使用する場合は、マージ エージェントが動作しているコンピューターにそのモジュールをコピーして登録する必要があります (ビジネス ロジック ハンドラーを使用している場合は、そのビジネス ロジック ハンドラーもパブリッシャー側で登録する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-120">To use a resolver other than the default resolver, you must copy the resolver to the computer on which the Merge Agent runs and register it (if you are using a business logic handler, it must also be registered at the Publisher).</span></span> <span data-ttu-id="2e9ff-121">マージ エージェントは、以下の場所で実行されます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-121">The Merge Agent runs at:</span></span>  
  
    -   <span data-ttu-id="2e9ff-122">プッシュ サブスクリプションの場合はディストリビューター</span><span class="sxs-lookup"><span data-stu-id="2e9ff-122">The Distributor for a push subscription</span></span>  
  
    -   <span data-ttu-id="2e9ff-123">プル サブスクリプションの場合はサブスクライバー</span><span class="sxs-lookup"><span data-stu-id="2e9ff-123">The Subscriber for a pull subscription</span></span>  
  
    -   <span data-ttu-id="2e9ff-124">Web 同期を使用するプル サブスクリプションの場合は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) サーバー</span><span class="sxs-lookup"><span data-stu-id="2e9ff-124">The [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS) server for a pull subscription that uses Web synchronization</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="2e9ff-125">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="2e9ff-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="2e9ff-126">競合回避モジュールを登録した後、 **[アーティクルのプロパティ - \<Article>]** ダイアログ ボックスの **[競合回避モジュール]** タブでアーティクルが競合回避モジュールを使用するように指定します。このダイアログ ボックスは、パブリケーションの新規作成ウィザードおよび **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスから使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-126">After the resolver is registered, specify that an article should use the resolver on the **Resolver** tab of the **Article Properties - \<Article>** dialog box, which is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="2e9ff-127">ウィザードの使用およびダイアログ ボックスへのアクセスの詳細については、「[パブリケーションの作成](create-a-publication.md)」および「[View and Modify Publication Properties](view-and-modify-publication-properties.md)」 (パブリケーション プロパティの表示および変更) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-127">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-a-resolver"></a><span data-ttu-id="2e9ff-128">競合回避モジュールを指定するには</span><span class="sxs-lookup"><span data-stu-id="2e9ff-128">To specify a resolver</span></span>  
  
1.  <span data-ttu-id="2e9ff-129">パブリケーションの新規作成ウィザードの **[アーティクル]** ページまたは **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスで、テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-129">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table.</span></span>  
  
2.  <span data-ttu-id="2e9ff-130">**[アーティクルのプロパティ]** をクリックしてから、 **[反転表示されたテーブル アーティクルのプロパティを設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-130">Click **Article Properties**, and then click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="2e9ff-131">**[アーティクルのプロパティ - \<Article>]** ページで、 **[競合回避モジュール]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-131">On the **Article Properties - \<Article>** page, click the **Resolver** tab.</span></span>  
  
4.  <span data-ttu-id="2e9ff-132">**[ディストリビューターに登録されたカスタム競合回避モジュールを使用する]** を選択し、一覧から競合回避モジュールをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-132">Select **Use a custom resolver (registered at the Distributor)**, and then in the list, click the resolver.</span></span>  
  
5.  <span data-ttu-id="2e9ff-133">競合回避モジュールが入力 (列名など) を必要とする場合は **[競合回避モジュールが必要とする情報の入力]** ボックスで指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-133">If the resolver requires input (such as a column name), specify it in the **Enter information needed by the resolver** text box.</span></span>  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="2e9ff-134">競合回避モジュールを必要とする各アーティクルについて、この処理を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-134">Repeat this process for each article that requires a resolver.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="2e9ff-135">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="2e9ff-135">Using Transact-SQL</span></span>  
  
#### <a name="to-register-a-custom-conflict-resolver"></a><span data-ttu-id="2e9ff-136">カスタム競合回避モジュールを登録するには</span><span class="sxs-lookup"><span data-stu-id="2e9ff-136">To register a custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="2e9ff-137">固有のカスタム競合回避モジュールを登録する場合は、次のいずれかの種類を作成します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-137">If you plan to register your own custom conflict resolver, create one of the following types:</span></span>  
  
    -   <span data-ttu-id="2e9ff-138">ビジネス ロジック ハンドラーとしてのマネージド コード ベースの競合回避モジュール。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-138">Managed code-based resolver as a business logic handler.</span></span> <span data-ttu-id="2e9ff-139">詳細については、「 [マージ アーティクルのビジネス ロジック ハンドラーの実装](../implement-a-business-logic-handler-for-a-merge-article.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-139">For more information, see [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
    -   <span data-ttu-id="2e9ff-140">ストアド プロシージャ ベースの競合回避モジュールと COM-ベースの競合回避モジュール。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-140">Stored procedure-based resolver and COM-based resolver.</span></span> <span data-ttu-id="2e9ff-141">詳しくは、「 [マージ アーティクルのカスタム競合回避モジュールの実装](../implement-a-custom-conflict-resolver-for-a-merge-article.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-141">For more information, see [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).</span></span>  
  
2.  <span data-ttu-id="2e9ff-142">目的の競合回避モジュールが既に登録されているかを判断するには、パブリッシャーの任意のデータベースに対して [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-142">To determine if the desired resolver is already registered, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) at the Publisher on any database.</span></span> <span data-ttu-id="2e9ff-143">これにより、カスタム競合回避モジュールの説明、およびディストリビューターに登録された各 COM ベースの競合回避モジュールのクラス識別子 (LSID)、またはディストリビューターに登録された各ビジネス ロジック ハンドラーのマネージド アセンブリの情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-143">This displays a description of the custom resolver as well as the class identifier (CLSID) for each COM-based resolver registered at the Distributor or information on the managed assembly for each business logic handler registered at the Distributor.</span></span>  
  
3.  <span data-ttu-id="2e9ff-144">目的のカスタム競合回避モジュールがまだ登録されていない場合は、ディストリビューターで [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-144">If the desired custom resolver is not already registered, execute [sp_registercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql) at the Distributor.</span></span> <span data-ttu-id="2e9ff-145">に競合回避モジュールの名前を指定します **@article_resolver** 。ビジネスロジックハンドラーの場合は、アセンブリのフレンドリ名です。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-145">Specify a name for the resolver for **@article_resolver**; for a business logic handler, this is the friendly name of the assembly.</span></span> <span data-ttu-id="2e9ff-146">COM ベースの競合回避モジュールの場合は、に DLL の CLSID を指定し、ビジネスロジックハンドラーにはの値を、にはを、にはを **@resolver_clsid** `true` **@is_dotnet_assembly** **@dotnet_assembly_name** オーバーライドするクラスの完全修飾名を指定し <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> **@dotnet_class_name** ます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-146">For COM-based resolvers, specify the CLSID of the DLL for **@resolver_clsid**, and for a business logic handler, specify a value of `true` for **@is_dotnet_assembly**, the name of the assembly for **@dotnet_assembly_name**, and the fully-qualified name of the class that overrides <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> for **@dotnet_class_name**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e9ff-147">ビジネスロジックハンドラーアセンブリがマージエージェント実行可能ファイルと同じディレクトリに配置されていない場合、マージエージェントを同期的に起動するアプリケーションと同じディレクトリ、またはグローバルアセンブリキャッシュ (GAC) 内に存在する場合は、のアセンブリ名を使用して完全パスを指定する必要があり **@dotnet_assembly_name** ます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-147">If a business logic handler assembly is not deployed in the same directory as the Merge Agent executable, in the same directory as the application that synchronously starts the Merge Agent, or in the global assembly cache (GAC), you need to specify the full path with the assembly name for **@dotnet_assembly_name**.</span></span>  
  
4.  <span data-ttu-id="2e9ff-148">競合回避モジュールが COM ベースの場合</span><span class="sxs-lookup"><span data-stu-id="2e9ff-148">If the resolver is a COM-based resolver:</span></span>  
  
    -   <span data-ttu-id="2e9ff-149">カスタム競合回避モジュール DLL をプッシュ サブスクリプションのディストリビューター、またはプル サブスクリプションのサブスクライバーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-149">Copy the custom resolver DLL to the Distributor for push subscriptions or to the Subscriber for pull subscriptions.</span></span>  
  
        > [!NOTE]  
        >  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="2e9ff-150">カスタム競合回避モジュールは、 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM ディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-150">custom resolvers can be found in the [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM directory.</span></span>  
  
    -   <span data-ttu-id="2e9ff-151">regsvr32.exe を使用して、カスタム競合回避モジュール DLL をオペレーティング システムに登録します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-151">Use regsvr32.exe to register the custom resolver DLL with the operating system.</span></span> <span data-ttu-id="2e9ff-152">たとえば、次のコマンドをコマンド プロンプトから実行すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver が登録されます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-152">For example, executing the following from the command prompt registers the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver:</span></span>  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  <span data-ttu-id="2e9ff-153">競合回避モジュールがビジネスロジックハンドラーである場合は、アセンブリをマージエージェント実行可能ファイル (replmerg.exe) と同じフォルダー、マージエージェントを呼び出すアプリケーションと同じフォルダー、または **@dotnet_assembly_name** 手順 3. でパラメーターに指定されたフォルダーに配置します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-153">If the resolver is a business logic handler, deploy the assembly in the same folder as the Merge Agent executable (replmerg.exe), in the same folder as an application that invokes the Merge Agent, or in the folder specified for the **@dotnet_assembly_name** parameter in step 3.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2e9ff-154">マージ エージェント実行可能ファイルの既定のインストール場所は、 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM です。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-154">The default installation location of the Merge Agent executable is [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.</span></span>  
  
#### <a name="to-specify-a-custom-resolver-when-defining-a-merge-article"></a><span data-ttu-id="2e9ff-155">マージ アーティクルを定義するときにカスタム競合回避モジュールを指定するには</span><span class="sxs-lookup"><span data-stu-id="2e9ff-155">To specify a custom resolver when defining a merge article</span></span>  
  
1.  <span data-ttu-id="2e9ff-156">カスタム競合回避モジュールを使用する場合は、上記の手順に従って競合回避モジュールを作成および登録します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-156">If you plan to use a custom conflict resolver, create and register the resolver using the above procedure.</span></span>  
  
2.  <span data-ttu-id="2e9ff-157">パブリッシャーで、[sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) を実行し、結果セットの **value** フィールドに示された目的のカスタム競合回避モジュールの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-157">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the desired custom resolver in the **value** field of result set.</span></span>  
  
3.  <span data-ttu-id="2e9ff-158">パブリッシャー側のパブリケーション データベースに対して、[sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-158">At the Publisher on the publication database, execute [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="2e9ff-159">手順 2. の競合回避モジュールの名前をに指定し、 **@article_resolver** パラメーターを使用してカスタム競合回避モジュールに必要な入力を指定し **@resolver_info** ます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-159">Specify the name of the resolver from step 2 for **@article_resolver** and any required input to the custom resolver using the **@resolver_info** parameter.</span></span> <span data-ttu-id="2e9ff-160">ストアドプロシージャベースのカスタム競合回避モジュールの場合 **@resolver_info** は、ストアドプロシージャの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-160">For stored procedure-based custom resolvers, **@resolver_info** is the name of the stored procedure.</span></span> <span data-ttu-id="2e9ff-161">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] によって提供される競合回避モジュールの必須入力の詳細については、「[Microsoft COM ベースの競合回避モジュール](../merge/advanced-merge-replication-conflict-com-based-resolvers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-161">For more information about required input for resolvers supplied by [!INCLUDE[msCoName](../../../includes/msconame-md.md)], see [Microsoft COM-Based Resolvers](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
#### <a name="to-specify-or-change-a-custom-resolver-for-an-existing-merge-article"></a><span data-ttu-id="2e9ff-162">既存のマージ アーティクルに対するカスタム競合回避モジュールを指定または変更するには</span><span class="sxs-lookup"><span data-stu-id="2e9ff-162">To specify or change a custom resolver for an existing merge article</span></span>  
  
1.  <span data-ttu-id="2e9ff-163">アーティクルに対してカスタム競合回避モジュールが定義されているかどうかを判断するには、[sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-163">To determine if a custom resolver has been defined for an article, or to get the name of the resolver, execute [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql).</span></span> <span data-ttu-id="2e9ff-164">アーティクルに対してカスタム競合回避モジュールが定義されている場合は、 **article_resolver** フィールドに名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-164">If there is a custom resolver defined for the article, its name will be displayed in the **article_resolver** field.</span></span> <span data-ttu-id="2e9ff-165">競合回避モジュールに対するすべての入力が結果セットの **resolver_info** フィールドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-165">Any input supplied to the resolver will be displayed in the **resolver_info** field of the result set.</span></span>  
  
2.  <span data-ttu-id="2e9ff-166">パブリッシャーで、[sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) を実行し、結果セットの **value** フィールドに示された目的のカスタム競合回避モジュールの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-166">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the desired custom resolver in the **value** field of the result set.</span></span>  
  
3.  <span data-ttu-id="2e9ff-167">パブリッシャー側のパブリケーション データベースに対して、[sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-167">At the Publisher on the publication database, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="2e9ff-168">**@property** にビジネス ロジック ハンドラーの完全パスを含む **article_resolver** の値を、**@value** に手順 2 の目的のカスタム競合回避モジュールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-168">Specify a value of **article_resolver**, including the full path for business logic handlers, for **@property**, and the name of the desired custom resolver from step 2 for **@value**.</span></span>  
  
4.  <span data-ttu-id="2e9ff-169">カスタム競合回避モジュールの必須入力を変更するには、[sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) を再度実行します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-169">To change any required input for the custom resolver, execute [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) again.</span></span> <span data-ttu-id="2e9ff-170">**@property** に **resolver_info** の値を、**@value** にカスタム競合回避モジュールの必須入力を指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-170">Specify a value of **resolver_info** for **@property** and any required input to the custom resolver for **@value**.</span></span> <span data-ttu-id="2e9ff-171">ストアドプロシージャベースのカスタム競合回避モジュールの場合 **@resolver_info** は、ストアドプロシージャの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-171">For stored procedure-based custom resolvers, **@resolver_info** is the name of the stored procedure.</span></span> <span data-ttu-id="2e9ff-172">必須入力の詳細については、「[Microsoft COM ベースの競合回避モジュール](../merge/advanced-merge-replication-conflict-com-based-resolvers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-172">For more information about required input, see [Microsoft COM-Based Resolvers](../merge/advanced-merge-replication-conflict-com-based-resolvers.md).</span></span>  
  
#### <a name="to-unregister-a-custom-conflict-resolver"></a><span data-ttu-id="2e9ff-173">カスタム競合回避モジュールの登録を解除するには</span><span class="sxs-lookup"><span data-stu-id="2e9ff-173">To unregister a custom conflict resolver</span></span>  
  
1.  <span data-ttu-id="2e9ff-174">パブリッシャーで [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) を実行し、結果セットの **value** フィールドに示された、削除するカスタム競合回避モジュールの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-174">At the Publisher, execute [sp_enumcustomresolvers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql) and note the name of the custom resolver to remove in the **value** field of the result set.</span></span>  
  
2.  <span data-ttu-id="2e9ff-175">ディストリビューターで、[sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-175">Execute [sp_unregistercustomresolver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql) at the Distributor.</span></span> <span data-ttu-id="2e9ff-176">手順 1. で作成したカスタム競合回避モジュールの完全な名前をに指定し **@article_resolver** ます。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-176">Specify the full name of the custom resolver from step 1 for **@article_resolver**.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="2e9ff-177">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="2e9ff-177">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="2e9ff-178">次の例では、新しいアーティクルを作成し、競合が発生したときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UnitPrice **列の平均の計算に** Averaging Conflict Resolver が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-178">This example creates a new article and specifies that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Averaging Conflict Resolver be used to calculate the average of the **UnitPrice** column when conflicts occur.</span></span>  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_addmerge_resolver)]  
  
 <span data-ttu-id="2e9ff-179">次の例では、アーティクルを変更して、競合が発生したときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UnitsOnOrder **列の合計の計算に** Additive Conflict Resolver が使用されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="2e9ff-179">This example changes an article to specify using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver to calculate the sum of the **UnitsOnOrder** column when conflicts occur.</span></span>  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../snippets/tsql/SQL15/replication/howto/tsql/mergearticleresolvers.sql#sp_changemerge_resolver)]  
  
## <a name="see-also"></a><span data-ttu-id="2e9ff-180">参照</span><span class="sxs-lookup"><span data-stu-id="2e9ff-180">See Also</span></span>  
 <span data-ttu-id="2e9ff-181">[Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="2e9ff-181">[Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md) </span></span>  
 [<span data-ttu-id="2e9ff-182">マージ アーティクルのビジネス ロジック ハンドラーの実装</span><span class="sxs-lookup"><span data-stu-id="2e9ff-182">Implement a Business Logic Handler for a Merge Article</span></span>](../implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
