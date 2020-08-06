---
title: データベースの処理権限の許可 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 69ba952e-09ae-49a9-9297-00e32e8e89a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6ada30e3fb509bd1ffd210485ce0e34b7bf86fb7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631300"
---
# <a name="granting-process-database-permissions"></a><span data-ttu-id="9a3ec-102">データベースの処理権限の許可</span><span class="sxs-lookup"><span data-stu-id="9a3ec-102">Granting Process Database Permissions</span></span>
  <span data-ttu-id="9a3ec-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスをインストールすると、そのインスタンス内の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバー管理者ロールのすべてのメンバーは、サーバー全体について [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンス内で任意のタスクを実行する権限を与えられます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-103">After you install an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], all members of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server administrator role in that instance have server-wide permissions to perform any task within the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="9a3ec-104">既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンス内のオブジェクトを管理および表示する権限は他のユーザーに一切与えられません。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-104">By default, no other users have any permission to administer or view any objects in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

 <span data-ttu-id="9a3ec-105">サーバー管理者ロールのメンバーは、他のユーザーをロールのメンバーにすることにより、サーバー全体にわたる管理アクセス権をそのユーザーに許可できます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-105">A member of the server administrator role can grant users administrative access on a server-wide basis by making them members of the role.</span></span> <span data-ttu-id="9a3ec-106">また、データベース レベルで制限付きの、または完全な管理権限やアクセス権を他のユーザーに付与することで、より狭い範囲の権限をそのユーザーに与えることもできます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-106">A member of the server administrator role can also grant users access on a more limited basis by granting them limited or complete administrative or access permissions at the database level.</span></span> <span data-ttu-id="9a3ec-107">制限付きの管理権限として、データベース レベル、キューブ レベル、またはディメンション レベルでの定義の処理権限や読み取り権限があります。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-107">Limited administrative permissions include process or read definition permissions at the database, cube, or dimension level.</span></span>

 <span data-ttu-id="9a3ec-108">このトピックの作業では、Process Database Objects というセキュリティ ロールを定義します。このロールのメンバーには、すべてのデータベース オブジェクトを処理する権限が与えられますが、データベース内のデータを表示する権限は与えられません。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-108">In the tasks in this topic, you will define a Process Database Objects security role that grants members of the role permission to process all database objects, but no permission to view data within the database.</span></span>

## <a name="defining-a-process-database-objects-security-role"></a><span data-ttu-id="9a3ec-109">Process Database Objects セキュリティ ロールの定義</span><span class="sxs-lookup"><span data-stu-id="9a3ec-109">Defining a Process Database Objects Security Role</span></span>

1.  <span data-ttu-id="9a3ec-110">ソリューション エクスプローラーで **[ロール]** を右クリックし、 **[新しいロール]** をクリックして、ロール デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-110">In Solution Explorer, right-click **Roles** and then click **New Role** to open the Role Designer.</span></span>

2.  <span data-ttu-id="9a3ec-111">**[データベースの処理]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-111">Click the **Process database** check box.</span></span>

3.  <span data-ttu-id="9a3ec-112">プロパティウィンドウで、この新しいロールの**Name**プロパティをに変更し `Process Database Objects Role` ます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-112">In the Properties window, change the **Name** property for this new role to `Process Database Objects Role`.</span></span>

     <span data-ttu-id="9a3ec-113">![ロール デザイナー](../../2014/tutorials/media/l10-security-1.png "ロール デザイナー")</span><span class="sxs-lookup"><span data-stu-id="9a3ec-113">![Role Designer](../../2014/tutorials/media/l10-security-1.png "Role Designer")</span></span>

4.  <span data-ttu-id="9a3ec-114">ロール デザイナーの **[メンバーシップ]** タブに切り替えて、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-114">Switch to the **Membership** tab of Role Designer and click **Add**.</span></span>

5.  <span data-ttu-id="9a3ec-115">このロールのメンバーになる Windows ドメイン ユーザーまたはグループのアカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-115">Enter the accounts of the Windows domain users or groups who will be members of this role.</span></span> <span data-ttu-id="9a3ec-116">アカウント情報を確認するために **[名前の確認]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-116">Click **Check Names** to verify the account information, and then click **OK**.</span></span>

6.  <span data-ttu-id="9a3ec-117">ロール デザイナーの **[キューブ]** タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-117">Switch to the **Cubes** tab of Role Designer.</span></span>

     <span data-ttu-id="9a3ec-118">次の図に示すとおり、このロールのメンバーにはこのデータベースを処理する権限が与えられていますが、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブ内のデータへのアクセス権がなく、ローカル キューブ/ドリルスルー アクセスを行うことができません。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-118">Notice that members of this role have permissions to process this database, but have no permission to access the data in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube and have no local cube/drillthrough access, as shown in the following image.</span></span>

     <span data-ttu-id="9a3ec-119">![ロール デザイナーの [キューブ] タブ](../../2014/tutorials/media/l10-security-2.png "ロール デザイナーの [キューブ] タブ")</span><span class="sxs-lookup"><span data-stu-id="9a3ec-119">![Cubes tab of Role Designer](../../2014/tutorials/media/l10-security-2.png "Cubes tab of Role Designer")</span></span>

7.  <span data-ttu-id="9a3ec-120">ロール デザイナーの **[ディメンション]** タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-120">Switch to the **Dimensions** tab of Role Designer.</span></span>

     <span data-ttu-id="9a3ec-121">このロールのメンバーにはこのデータベース内のすべてのディメンション オブジェクトを処理する権限が与えられ、既定では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial データベース内の各ディメンション オブジェクトにアクセスするための読み取り権限も与えられます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-121">Notice that members of this role have permissions to process all dimension objects in this database, and, by default, have read permissions to access each dimension object in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial database.</span></span>

8.  <span data-ttu-id="9a3ec-122">**[ビルド]** メニューの **[Analysis Services Tutorial の配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-122">On the **Build** menu, click **Deploy Analysis Services Tutorial**.</span></span>

     <span data-ttu-id="9a3ec-123">これで、Process Database Objects セキュリティ ロールが正常に定義され、配置されました。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-123">You have now successfully defined and deployed the Process Database Objects security role.</span></span> <span data-ttu-id="9a3ec-124">キューブが実稼働環境に配置された後、その配置されたキューブの管理者は、ユーザーをこのロールに追加することにより、処理作業を必要に応じて特定のユーザーに委任することができます。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-124">After a cube is deployed to the production environment, the administrators of the deployed cube can add users to this role as required to delegate processing responsibilities to specific users.</span></span>

> [!NOTE]
>  <span data-ttu-id="9a3ec-125">レッスン 10 の操作内容が反映されたプロジェクトを入手するには、サンプルをダウンロードしてインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-125">A completed project for Lesson 10 is available by downloading and installing the samples.</span></span> <span data-ttu-id="9a3ec-126">詳細については、「 [Analysis Services 多次元モデリング チュートリアル用のサンプル データおよびプロジェクトのインストール](install-sample-data-and-projects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a3ec-126">For more information, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a3ec-127">参照</span><span class="sxs-lookup"><span data-stu-id="9a3ec-127">See Also</span></span>
 [<span data-ttu-id="9a3ec-128">ロールと権限 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="9a3ec-128">Roles and Permissions &#40;Analysis Services&#41;</span></span>](multidimensional-models/roles-and-permissions-analysis-services.md)


