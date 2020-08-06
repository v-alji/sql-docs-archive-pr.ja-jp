---
title: サーバー環境の作成とマップ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isenvprop.variables.f1
- sql12.ssis.ssms.iscreateenv.f1
- sql12.ssis.ssms.isenvprop.permissions.f1
- sql12.ssis.ssms.isenvprop.general.f1
ms.assetid: b1cbb697-713f-48e4-b234-b23724d87451
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9331b5078effb562931f45c48bd8ff975c1d1998
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639574"
---
# <a name="create-and-map-a-server-environment"></a><span data-ttu-id="3c8cb-102">サーバー環境の作成とマップ</span><span class="sxs-lookup"><span data-stu-id="3c8cb-102">Create and Map a Server Environment</span></span>
  <span data-ttu-id="3c8cb-103">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サーバーに配置したプロジェクトに含まれるパッケージに合わせたランタイム値を指定するためのサーバー環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-103">You create a server environment to specify runtime values for packages contained in a project you've deployed to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="3c8cb-104">特定のパッケージ、エントリ ポイント パッケージ、または特定のプロジェクト内のすべてのパッケージに対して、環境変数をパラメーターにマップできるようになります。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-104">You can then map the environment variables to parameters, for a specific package, for entry-point packages, or for all the packages in a given project.</span></span> <span data-ttu-id="3c8cb-105">エントリ ポイント パッケージは、通常、子パッケージを実行する親パッケージです。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-105">An entry-point package is typically a parent package that executes a child package.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3c8cb-106">特定の実行で、パッケージは単一のサーバー環境に含まれている値だけで実行できます。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-106">For a given execution, a package can execute only with the values contained in a single server environment.</span></span>  
  
 <span data-ttu-id="3c8cb-107">サーバー環境、環境参照、および環境変数の一覧のビューに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-107">You can query views for a list of server environments, environment references, and environment variables.</span></span> <span data-ttu-id="3c8cb-108">環境、環境参照、および環境変数を追加、削除、変更するストアド プロシージャを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-108">You can also call stored to add, delete, and modify environments, environment references, and environment variables.</span></span> <span data-ttu-id="3c8cb-109">詳細については、「 [SSIS カタログ](catalog/ssis-catalog.md)」の「**サーバー環境、サーバー変数、およびサーバー環境の参照**」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-109">For more information, see the **Server Environments, Server Variables and Server Environment References** section in [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
### <a name="to-create-and-use-a-server-environment"></a><span data-ttu-id="3c8cb-110">サーバー環境を作成して使用するには</span><span class="sxs-lookup"><span data-stu-id="3c8cb-110">To create and use a server environment</span></span>  
  
1.  <span data-ttu-id="3c8cb-111">で、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクトエクスプローラーの [カタログ> **SSISDB** ] ノードを展開し、環境を作成するプロジェクトの [**環境**] フォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-111">In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], expand the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Catalogs> **SSISDB** node in Object Explorer, and locate the **Environments** folder of the project for which you want to create an environment.</span></span>  
  
2.  <span data-ttu-id="3c8cb-112">**[環境]** フォルダーを右クリックし、 **[環境の作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-112">Right-click the **Environments** folder, and then click **Create Environment**.</span></span>  
  
3.  <span data-ttu-id="3c8cb-113">環境の名前、および必要に応じて説明を入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-113">Type a name for the environment and optionally a description, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="3c8cb-114">新しい環境を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-114">Right-click the new environment and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="3c8cb-115">**[変数]** ページで、次の手順を実行して変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-115">On the **Variables** page, do the following to add a variable.</span></span>  
  
    1.  <span data-ttu-id="3c8cb-116">変数の **[型]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-116">Select the **Type** for the variable.</span></span> <span data-ttu-id="3c8cb-117">変数の名前は、変数にマップするプロジェクトパラメーターの名前と一致する必要**はありません**。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-117">The name of the variable **does not** need to match the name of the project parameter that you map to the variable.</span></span>  
  
    2.  <span data-ttu-id="3c8cb-118">必要に応じて、変数の **[説明]** を入力します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-118">Enter an optional **Description** for the variable.</span></span>  
  
    3.  <span data-ttu-id="3c8cb-119">環境変数の **[値]** を入力します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-119">Enter the **Value** for the environment variable.</span></span>  
  
         <span data-ttu-id="3c8cb-120">環境変数の名前のルールについては、「 **SSIS Catalog** 」の「 [環境変数](catalog/ssis-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-120">For information about the rules for environment variable names, see the **Environment Variable** section in [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
    4.  <span data-ttu-id="3c8cb-121">**[機微]** チェック ボックスをオンまたはオフにして、変数に機微な値が含まれているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-121">Indicate whether the variable contains sensitive value, by selecting or clearing the **Sensitive** checkbox.</span></span>  
  
         <span data-ttu-id="3c8cb-122">**[機微]** をオンにすると、変数値が **[値]** のフィールドに表示されません。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-122">If you select **Sensitive**, the variable value does not display in the **Value** field.</span></span>  
  
         <span data-ttu-id="3c8cb-123">機微な値は、SSISDB カタログで暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-123">Sensitive values are encrypted in the SSISDB catalog.</span></span> <span data-ttu-id="3c8cb-124">暗号化の詳細については、「 [SSIS Catalog](catalog/ssis-catalog.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-124">For more information about the encryption, see [SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
6.  <span data-ttu-id="3c8cb-125">**[権限]** ページで、次の手順を実行して、選択したユーザーに対して権限とロールを許可または拒否します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-125">On the **Permissions** page, grant or deny permissions for selected users and roles by doing the following.</span></span>  
  
    1.  <span data-ttu-id="3c8cb-126">**[参照]** をクリックし、 **[すべてのプリンシパルを参照]** ダイアログ ボックスで 1 つ以上のユーザーおよびロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-126">Click **Browse**, and then select one or more users and roles in the **Browse All Principals** dialog box.</span></span>  
  
    2.  <span data-ttu-id="3c8cb-127">**[ログインまたはロール]** 領域で、権限を許可または拒否するユーザーまたはロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-127">In the **Logins or roles** area, select the user or role that you want to grant or deny permissions for.</span></span>  
  
    3.  <span data-ttu-id="3c8cb-128">**[明示]** 領域で、各権限の横にある **[許可]** または **[拒否]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-128">In the **Explicit** area, click **Grant** or **Deny** next to each permission.</span></span>  
  
7.  <span data-ttu-id="3c8cb-129">環境のスクリプトを作成するには、 **[スクリプト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-129">To script the environment, click **Script**.</span></span> <span data-ttu-id="3c8cb-130">既定では、新しいクエリ エディター ウィンドウにスクリプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-130">By default, the script displays in a new Query Editor window.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="3c8cb-131">スクリプトを作成した後、または変数を追加するなど環境プロパティを変更した後に **[スクリプト]** をクリックしてから、**[環境のプロパティ]** ダイアログ ボックスで **[OK]** をクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-131">You need to click **Script** after you've made one or changes to the environment properties, such as adding a variable, and before you click **OK** in the **Environment Properties** dialog box.</span></span> <span data-ttu-id="3c8cb-132">このようにしないと、スクリプトは生成されません。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-132">Otherwise, a script is not generated.</span></span>  
  
8.  <span data-ttu-id="3c8cb-133">**[OK]** をクリックして、変更を環境プロパティに保存します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-133">Click **OK** to save your changes to the environment properties.</span></span>  
  
9. <span data-ttu-id="3c8cb-134">オブジェクト エクスプローラーで **[SSISDB]** ノードの下の **[プロジェクト]** フォルダーを展開し、プロジェクトを右クリックして **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-134">Under the **SSISDB** node in Object Explorer, expand the **Projects** folder, right-click the project, and then click **Configure**.</span></span>  
  
10. <span data-ttu-id="3c8cb-135">**[参照]** ページで、 **[追加]** をクリックして環境を追加し、 **[OK]** をクリックして参照を環境に保存します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-135">On the **References** page, click **Add** to add an environment, and then click **OK** to save the reference to the environment.</span></span>  
  
11. <span data-ttu-id="3c8cb-136">プロジェクトをもう一度右クリックし、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-136">Right-click the project again, and then click **Configure**.</span></span>  
  
12. <span data-ttu-id="3c8cb-137">環境変数を、デザイン時にパッケージに追加したパラメーターにマップするか、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトをプロジェクト配置モデルに変換したときに生成されたパラメーターにマップするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-137">To map the environment variable to a parameter that you added to the package at design-time or to a parameter that was generated when you converted the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the project deployment model, do the following.,</span></span>  
  
    1.  <span data-ttu-id="3c8cb-138">**[パラメーター]** ページの **[パラメーター]** タブで、 **[値]** フィールドの横にある参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-138">In the **Parameters** tab on the **Parameters** page, click the browse button next to the **Value** field.</span></span>  
  
    2.  <span data-ttu-id="3c8cb-139">**[環境変数を使用する]** をクリックし、作成した環境変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-139">Click **Use environment variable**, and then select the environment variable you created.</span></span>  
  
13. <span data-ttu-id="3c8cb-140">環境変数を接続マネージャーのプロパティにマップするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-140">To map the environment variable to a connection manager property, do the following.</span></span> <span data-ttu-id="3c8cb-141">パラメーターは、SSIS サーバー上で接続マネージャー プロパティ用に自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-141">Parameters are automatically generated on the SSIS server for the connection manager properties.</span></span>  
  
    1.  <span data-ttu-id="3c8cb-142">**[パラメーター]** ページの **[接続マネージャー]** タブで、**[値]** フィールドの横にある [参照] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-142">In the **Connection Managers** tab on the **Parameters** page, click the browse button next to the **Value** field.</span></span>  
  
    2.  <span data-ttu-id="3c8cb-143">**[環境変数を使用する]** をクリックし、作成した環境変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-143">Click **Use environment variable**, and then select the environment variable you created.</span></span>  
  
14. <span data-ttu-id="3c8cb-144">**[OK]** をクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="3c8cb-144">Click **OK** twice to save your changes.</span></span>  
  
  
