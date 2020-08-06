---
title: '[ソースの選択] ダイアログ ボックス | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.dmf.selectsource.f1
ms.assetid: d664c2e5-dd0c-4da8-b27d-aa4ee4fc0ffd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 535d211d6827477fcf029accc27a9000e8c695c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740854"
---
# <a name="select-source-dialog-box"></a><span data-ttu-id="4dab2-102">[ソースの選択] ダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="4dab2-102">Select Source Dialog Box</span></span>
  <span data-ttu-id="4dab2-103">このダイアログ ボックスを使用すると、実行するポリシーのソースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="4dab2-103">Use this dialog box to select the source of the policies to be run.</span></span> <span data-ttu-id="4dab2-104">ポリシーを含む 1 つ以上の XML ファイルを選択するには、 **[ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-104">To select one or more XML files that contain policies, select **Files**.</span></span> <span data-ttu-id="4dab2-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス上にあるポリシーを実行するには、 **[サーバー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-105">To run the policies that are found on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select **Server**.</span></span>  
  
 <span data-ttu-id="4dab2-106">このダイアログ ボックスは、複数の方法で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="4dab2-106">You can open this dialog box in several ways.</span></span>  
  
 <span data-ttu-id="4dab2-107">**このダイアログ ボックスを開くには**</span><span class="sxs-lookup"><span data-stu-id="4dab2-107">**To open this dialog box**</span></span>  
  
-   <span data-ttu-id="4dab2-108">[登録済みサーバー] で、 **[ローカル サーバー グループ]** を右クリックするか、 **[ローカル サーバー グループ]** または **[中央管理サーバー]** の下にあるサーバーを右クリックして、 **[ポリシーの評価]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dab2-108">In Registered Servers, right-click **Local Server Groups** or any server under **Local Server Groups**, or any server under **Central Management Servers**, and then select **Evaluate Policies**.</span></span> <span data-ttu-id="4dab2-109">**[ポリシーの評価]** ダイアログ ボックスの **[ポリシーの選択]** ページで、参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dab2-109">In the **Policy Selection** page of the **Evaluate Policies** dialog box, click the Browse (**...**) button.</span></span>  
  
-   <span data-ttu-id="4dab2-110">オブジェクト エクスプローラーで、 **[管理]** 、 **[ポリシー管理]** の順に展開し、 **[ポリシー]** を右クリックして **[ポリシーのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dab2-110">In Object Explorer, expand **Management**, expand **Policy Management**, right-click **Policies**, and select **Import Policy**.</span></span> <span data-ttu-id="4dab2-111">**[インポート]** ダイアログ ボックスで、参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dab2-111">In the **Import** dialog box, click the Browse (**...**) button.</span></span>  
  
-   <span data-ttu-id="4dab2-112">オブジェクト エクスプローラーで、サーバー、データベース、またはデータベース オブジェクトを右クリックし、 **[ポリシー]** 、 **[評価]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dab2-112">In Object Explorer, right-click a server, database, or database object, select **Policies**, and then select **Evaluate**.</span></span> <span data-ttu-id="4dab2-113">**[ポリシーの評価]** ダイアログ ボックスの **[ポリシーの選択]** ページで、参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dab2-113">In the **Policy Selection** page of the **Evaluate Policies** dialog box, click the Browse (**...**) button.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4dab2-114">オプション</span><span class="sxs-lookup"><span data-stu-id="4dab2-114">Options</span></span>  
 <span data-ttu-id="4dab2-115">**[ファイル]**</span><span class="sxs-lookup"><span data-stu-id="4dab2-115">**Files**</span></span>  
 <span data-ttu-id="4dab2-116">ポリシーを含む 1 つ以上の XML ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-116">Select one or more XML files that contain policies.</span></span>  
  
 <span data-ttu-id="4dab2-117">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="4dab2-117">**Server**</span></span>  
 <span data-ttu-id="4dab2-118">実行するポリシーを含むサーバーを選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4dab2-118">Enables you to select a server that contains the policies that you want to run.</span></span>  
  
 <span data-ttu-id="4dab2-119">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="4dab2-119">**Server type**</span></span>  
 <span data-ttu-id="4dab2-120">ポリシーを含んでいるのは [!INCLUDE[ssDE](../../includes/ssde-md.md)] サーバーだけです。</span><span class="sxs-lookup"><span data-stu-id="4dab2-120">Only [!INCLUDE[ssDE](../../includes/ssde-md.md)] servers contain policies.</span></span> <span data-ttu-id="4dab2-121">このボックスは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="4dab2-121">This box is read-only.</span></span>  
  
 <span data-ttu-id="4dab2-122">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="4dab2-122">**Server name**</span></span>  
 <span data-ttu-id="4dab2-123">接続するサーバー インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-123">Select the server instance to connect to.</span></span> <span data-ttu-id="4dab2-124">既定では、最後に接続していたサーバー インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4dab2-124">By default, the server instance last connected to is displayed.</span></span>  
  
 <span data-ttu-id="4dab2-125">**認証**</span><span class="sxs-lookup"><span data-stu-id="4dab2-125">**Authentication**</span></span>  
 <span data-ttu-id="4dab2-126">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続する際には、2 つの認証モードのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-126">Two authentication modes are available when you connect to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="4dab2-127">**Windows 認証モード ([Windows 認証])**</span><span class="sxs-lookup"><span data-stu-id="4dab2-127">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="4dab2-128">Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="4dab2-128">Windows Authentication mode allows for a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="4dab2-129">**SQL Server 認証**</span><span class="sxs-lookup"><span data-stu-id="4dab2-129">**SQL Server Authentication**</span></span>  
 <span data-ttu-id="4dab2-130">指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。</span><span class="sxs-lookup"><span data-stu-id="4dab2-130">When a user connects with a specified login name and password from a nontrusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication itself by checking whether a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and whether the specified password matches the one previously recorded.</span></span> <span data-ttu-id="4dab2-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログイン アカウントが設定されていない場合、認証は失敗し、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="4dab2-131">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not have a login account set, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4dab2-132">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-132">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="4dab2-133">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="4dab2-133">**User name**</span></span>  
 <span data-ttu-id="4dab2-134">接続に使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-134">Enter the user name to connect with.</span></span> <span data-ttu-id="4dab2-135">このオプションは、Windows 認証を使用した接続を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4dab2-135">This option is available only if you have selected to connect by using Windows Authentication.</span></span>  
  
 <span data-ttu-id="4dab2-136">**Login**</span><span class="sxs-lookup"><span data-stu-id="4dab2-136">**Login**</span></span>  
 <span data-ttu-id="4dab2-137">接続に使用するログインを入力します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-137">Enter the login to connect with.</span></span> <span data-ttu-id="4dab2-138">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4dab2-138">This option is available only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="4dab2-139">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="4dab2-139">**Password**</span></span>  
 <span data-ttu-id="4dab2-140">ログインのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="4dab2-140">Enter the password for the login.</span></span> <span data-ttu-id="4dab2-141">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合にのみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="4dab2-141">This option is editable only if you have selected to connect by using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dab2-142">参照</span><span class="sxs-lookup"><span data-stu-id="4dab2-142">See Also</span></span>  
 <span data-ttu-id="4dab2-143">[[ポリシー管理] ノード &#40;オブジェクト エクスプローラー&#41;](../../ssms/object/object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="4dab2-143">[Policy Management Node &#40;Object Explorer&#41;](../../ssms/object/object-explorer.md) </span></span>  
 [<span data-ttu-id="4dab2-144">ポリシー ベースの管理を使用したサーバーの管理</span><span class="sxs-lookup"><span data-stu-id="4dab2-144">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
