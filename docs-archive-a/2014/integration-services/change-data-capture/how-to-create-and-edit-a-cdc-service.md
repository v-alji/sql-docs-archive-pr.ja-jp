---
title: CDC Service を作成および編集する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1b3d47a5-dc89-482d-bbc7-fff04f194c43
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d90534b475901b08fcd2e09acdc0f7976f0fb6e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712298"
---
# <a name="how-to-create-and-edit-a-cdc-service"></a><span data-ttu-id="663a2-102">CDC Service を作成および編集する方法</span><span class="sxs-lookup"><span data-stu-id="663a2-102">How to Create and Edit a CDC Service</span></span>
  <span data-ttu-id="663a2-103">この手順では、CDC Service 構成コンソールから新しい Oracle CDC Service を作成および編集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="663a2-103">These procedures describe how to create and edit a new Oracle CDC Service from the CDC Service Configuration Console.</span></span>  
  
 <span data-ttu-id="663a2-104">この手順を実行する Windows ユーザーには、Oracle CDC サービスが構成されているコンピューター上の管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="663a2-104">This procedure requires a Windows user with administrator privileges on the computer where the Oracle CDC service is configured.</span></span>  
  
### <a name="to-create-a-new-cdc-service"></a><span data-ttu-id="663a2-105">新しい CDC サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="663a2-105">To create a new CDC service</span></span>  
  
1.  <span data-ttu-id="663a2-106">**[スタート]** メニューの **[CDC Service Configuration for Oracle]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="663a2-106">From the **Start** menu, select **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="663a2-107">左側のペインから [ローカルの CDC Service] を右クリックし、[新しいサービス] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="663a2-107">From the left pane, right click Local CDC Services and select New Service</span></span>  
  
     <span data-ttu-id="663a2-108">**[アクション]** ペインから **[新しいサービス]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="663a2-108">You can also click **New Service** from the **Actions** pane.</span></span>  
  
3.  <span data-ttu-id="663a2-109">[新しい Oracle CDC Service] ダイアログ ボックスに必要な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="663a2-109">Type or enter the required information in the New Oracle CDC Service dialog box.</span></span> <span data-ttu-id="663a2-110">[新しい Oracle CDC Service] ダイアログ ボックスに情報を入力する方法については、「 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="663a2-110">See [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) for information on how to enter information in the New Oracle CDC Service dialog box.</span></span>  
  
     <span data-ttu-id="663a2-111">[新しい Oracle CDC Service] ダイアログ ボックスで指定した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインが、サービスの実行時に Oracle CDC Service によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="663a2-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login provided in the New Oracle CDC Service dialog box is used by the Oracle CDC Service when the service runs.</span></span> <span data-ttu-id="663a2-112">このログインは、public 固定サーバー ロールのメンバーであることだけが必要です。その他の権限は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="663a2-112">This login only needs to be a member of the public fixed-server role, no other privileges are needed.</span></span> <span data-ttu-id="663a2-113">新しい Oracle CDC のインスタンスが追加されると、そのログインには、関連付けられている **CDC データベースへの** db_owner [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アクセスが与えられます。</span><span class="sxs-lookup"><span data-stu-id="663a2-113">Once new Oracle CDC Instances are added, that login receives **db_owner** access to the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC databases.</span></span>  
  
4.  <span data-ttu-id="663a2-114">必要な情報の入力が完了したら、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="663a2-114">When you finish entering the required information, click **OK**.</span></span>  
  
     <span data-ttu-id="663a2-115">Oracle CDC Windows Service の定義を作成するには、プログラムに、関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の MSXDBCDC データベースに対する更新アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="663a2-115">To create the Oracle CDC Windows Service definition, the program needs update access to the MSXDBCDC database in the associated [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="663a2-116">**[OK]** をクリックすると、MSXDBCDC データベースに対する更新アクセスを持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを入力するためのダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="663a2-116">When you click **OK**, a dialog box prompts the user to enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login with an update access to the MSXDBCDC database.</span></span>  
  
     <span data-ttu-id="663a2-117">[SQL Server への接続] ダイアログ ボックスに入力するデータについては、「 [Connection to SQL Server](connection-to-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="663a2-117">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="663a2-118">**[OK]** をクリックして、[新しい Oracle CDC Service] ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="663a2-118">Click **OK** to close the New Oracle CDC Service dialog box.</span></span>  
  
### <a name="to-edit-a-cdc-service"></a><span data-ttu-id="663a2-119">CDC サービスを編集するには</span><span class="sxs-lookup"><span data-stu-id="663a2-119">To edit a CDC service</span></span>  
  
1.  <span data-ttu-id="663a2-120">**[スタート]** メニューの **[CDC Service Configuration for Oracle]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="663a2-120">From the **Start** menu, select **CDC Service Configuration for Oracle**.</span></span>  
  
2.  <span data-ttu-id="663a2-121">左側のペインから **[ローカルの CDC Service]** をクリックし、編集するローカル サービスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="663a2-121">From the left pane, select **Local CDC Services** then right-click the local service you want to edit and select **Properties**.</span></span>  
  
     <span data-ttu-id="663a2-122">中央のペインで対象のサービスを選択し、 **[アクション]** ペインから **[プロパティ]** をクリックすることもできます。</span><span class="sxs-lookup"><span data-stu-id="663a2-122">You can also select the service you are working with in the middle and then from the **Actions** pane, click **Properties**.</span></span>  
  
3.  <span data-ttu-id="663a2-123">[CDC Service のプロパティ] ダイアログ ボックスに必要な情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="663a2-123">Type or enter the required information in the CDC Service Properties dialog box.</span></span> <span data-ttu-id="663a2-124">[CDC Service のプロパティ] ダイアログ ボックスに情報を入力する方法については、「 [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="663a2-124">See [Create and Edit an Oracle CDC Service](create-and-edit-an-oracle-cdc-service.md) for information on how to enter information in the CDC Service Properties dialog box.</span></span>  
  
4.  <span data-ttu-id="663a2-125">必要な情報の入力が完了したら、 **[OK]** をクリックします。[SQLServer への接続] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="663a2-125">When you finish entering the required information, Click **OK**, the Connect to SQL Server dialog box opens.</span></span>  
  
     <span data-ttu-id="663a2-126">MSXDBDCDC データベースに対する書き込み権限を持たないログインが新しい Oracle CDC インスタンスの作成を試みると、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="663a2-126">When a login without write permission to the MSXDBDCDC database attempts to create a new Oracle CDC instance an error message is displayed.</span></span> <span data-ttu-id="663a2-127">そのダイアログ ボックスで **[OK]** をクリックします。[SQL Server への接続] ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="663a2-127">Click **OK** in that dialog box to display the Connect to SQL Server dialog box.</span></span> <span data-ttu-id="663a2-128">このダイアログ ボックスには、 **db_owner** データベース ロールなど、MSXDBCDC データベースに対する書き込み権限を持つログインの資格情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="663a2-128">In this dialog box you must enter the credentials for a login that has write permission to the MSXDBCDC database, such the **db_owner** database role.</span></span>  
  
     <span data-ttu-id="663a2-129">[SQL Server への接続] ダイアログ ボックスに入力するデータについては、「 [Connection to SQL Server](connection-to-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="663a2-129">For information about the data you must type into the Connect to SQL Server dialog box, see [Connection to SQL Server](connection-to-sql-server.md).</span></span>  
  
5.  <span data-ttu-id="663a2-130">[Oracle への接続] ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="663a2-130">Click **OK** in the Connect to Oracle dialog box.</span></span> <span data-ttu-id="663a2-131">両方のダイアログ ボックスが閉じ、サービスが更新および登録されます。</span><span class="sxs-lookup"><span data-stu-id="663a2-131">Both dialog boxes close and the service is updated and registered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="663a2-132">参照</span><span class="sxs-lookup"><span data-stu-id="663a2-132">See Also</span></span>  
 <span data-ttu-id="663a2-133">[Attunity の Change Data Capture Designer for Oracle](change-data-capture-designer-for-oracle-by-attunity.md) </span><span class="sxs-lookup"><span data-stu-id="663a2-133">[Change Data Capture Designer for Oracle by Attunity](change-data-capture-designer-for-oracle-by-attunity.md) </span></span>  
 [<span data-ttu-id="663a2-134">Oracle CDC Service の作成と編集</span><span class="sxs-lookup"><span data-stu-id="663a2-134">Create and Edit an Oracle CDC Service</span></span>](create-and-edit-an-oracle-cdc-service.md)  
  
  
