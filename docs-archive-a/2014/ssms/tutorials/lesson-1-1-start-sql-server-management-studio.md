---
title: SQL Server Management Studio の起動 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 25ffaea6-0eee-4169-8dd0-1da417c28fc6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8fc9de4884da9a4c372eecdeb6fde12cf3c507e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711517"
---
# <a name="start-sql-server-management-studio"></a><span data-ttu-id="9c5a8-102">SQL Server Management Studio の起動</span><span class="sxs-lookup"><span data-stu-id="9c5a8-102">Start SQL Server Management Studio</span></span>
  <span data-ttu-id="9c5a8-103">このチュートリアルを開始する前に、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を開いてみましょう。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-103">To begin this tutorial, let's take a look at [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="opening-sql-server-management-studio"></a><span data-ttu-id="9c5a8-104">SQL Server Management Studio を開く</span><span class="sxs-lookup"><span data-stu-id="9c5a8-104">Opening SQL Server Management Studio</span></span>  
  
#### <a name="to-open-sql-server-management-studio"></a><span data-ttu-id="9c5a8-105">SQL Server Management Studio を開くには</span><span class="sxs-lookup"><span data-stu-id="9c5a8-105">To open SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="9c5a8-106">[**スタート**] ボタンをクリックし、[**すべてのプログラム**]、[] の順にポイントして、 [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] [ **SQL Server Management Studio**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-106">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="9c5a8-107">は、既定ではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-107">is not installed by default.</span></span> <span data-ttu-id="9c5a8-108">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を利用できない場合は、セットアップを実行してインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-108">If [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] is unavailable, install it by running Setup.</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="9c5a8-109">は [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] では使用できません。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-109">is not available with [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].</span></span> [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]<span data-ttu-id="9c5a8-110">Express は、 [Microsoft ダウンロードセンター](https://www.microsoft.com/download/details.aspx?id=14630)から無料でダウンロードできますが、このチュートリアルで説明しているものとは異なるユーザーインターフェイスを備えています。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-110">Express is available as a free download from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=14630), but has a different user interface than is described in this tutorial.</span></span>  
  
2.  <span data-ttu-id="9c5a8-111">**[サーバーへの接続]** ダイアログ ボックスで既定の設定を確認し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-111">In the **Connect to Server** dialog box, verify the default settings, and then click **Connect**.</span></span> <span data-ttu-id="9c5a8-112">接続するには、[**サーバー名**] ボックスに、がインストールされているコンピューターの名前が含まれている必要があり [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-112">To connect, the **Server name** box must contain the name of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="9c5a8-113">[!INCLUDE[ssDE](../../includes/ssde-md.md)]が名前付きインスタンスの場合、[**サーバー名**] ボックスには instance_name> の形式でインスタンス名も含まれている必要があり \<*computer_name*> \\ < *instance_name*ます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-113">If the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is a named instance, the **Server name** box should also contain the instance name in the format \<*computer_name*>\\<*instance_name*>.</span></span>  
  
## <a name="management-studio-components"></a><span data-ttu-id="9c5a8-114">Management Studio のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="9c5a8-114">Management Studio Components</span></span>  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="9c5a8-115">では、情報は種類ごとに専用のウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-115">presents information in windows dedicated to specific types of information.</span></span> <span data-ttu-id="9c5a8-116">データベース情報はオブジェクト エクスプローラーとドキュメント ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-116">Database information is shown in Object Explorer and document windows.</span></span>  
  
-   <span data-ttu-id="9c5a8-117">オブジェクト エクスプローラーには、サーバー上のすべてのデータベース オブジェクトがツリー形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-117">Object Explorer is a tree view of all the database objects in a server.</span></span> <span data-ttu-id="9c5a8-118">たとえば、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のデータベースが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-118">This can include the databases of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="9c5a8-119">オブジェクト エクスプローラーには、接続しているすべてのサーバーの情報が登録されています。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-119">Object Explorer includes information for all servers to which it is connected.</span></span> <span data-ttu-id="9c5a8-120">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]を開くと、前回使用した設定にオブジェクト エクスプローラーを接続するかどうかをたずねられます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-120">When you open [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you are prompted to connect Object Explorer to the settings that were last used.</span></span> <span data-ttu-id="9c5a8-121">[登録済みサーバー] の一覧でサーバーをダブルクリックすると、そのサーバーに接続できますが、接続するサーバーを登録する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-121">You can double-click any server in the Registered Servers component to connect to it, but you do not have to register a server to connect.</span></span>  
  
-   <span data-ttu-id="9c5a8-122">ドキュメント ウィンドウは、 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]の中で最も大きな部分を占めています。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-122">The document window is the largest portion of [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="9c5a8-123">ドキュメント ウィンドウにはクエリ エディターとブラウザー ウィンドウを表示できます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-123">The document windows can contain query editors and browser windows.</span></span> <span data-ttu-id="9c5a8-124">既定では [概要] ページが表示され、現在のコンピューター上にある [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続されます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-124">By default, the Summary page is displayed, connected to the instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)] on the current computer.</span></span>  
  
## <a name="showing-additional-windows"></a><span data-ttu-id="9c5a8-125">その他のウィンドウの表示</span><span class="sxs-lookup"><span data-stu-id="9c5a8-125">Showing Additional Windows</span></span>  
  
#### <a name="to-show-the-registered-servers-window"></a><span data-ttu-id="9c5a8-126">登録済みサーバー ウィンドウを表示するには</span><span class="sxs-lookup"><span data-stu-id="9c5a8-126">To show the Registered Servers window</span></span>  
  
1.  <span data-ttu-id="9c5a8-127">**[表示]** メニューの **[登録済みサーバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-127">On the **View** menu, click **Registered Servers**.</span></span>  
  
     <span data-ttu-id="9c5a8-128">[登録済みサーバー] ウィンドウがオブジェクト エクスプローラーの上に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-128">The Registered Servers window appears above Object Explorer.</span></span> <span data-ttu-id="9c5a8-129">[登録済みサーバー] には、管理頻度の高いサーバーの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-129">Registered Servers lists servers which you manage frequently.</span></span> <span data-ttu-id="9c5a8-130">この一覧にサーバーを追加したり、一覧からサーバーを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-130">You can add and remove servers from this list.</span></span> <span data-ttu-id="9c5a8-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューター上の [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]インスタンスのみが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-131">The only servers listed are the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on the computer where you are running [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span>  
  
2.  <span data-ttu-id="9c5a8-132">サーバーが表示されない場合は、[登録済みサーバー] で [**データベースエンジン**] を右クリックし、[**ローカルサーバーの登録の更新**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9c5a8-132">If your server does not appear, in Registered Servers, right-click **Database Engine**, and then click **Update Local Server Registration**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9c5a8-133">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="9c5a8-133">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9c5a8-134">登録済みサーバーおよびオブジェクト エクスプローラーを使用した接続</span><span class="sxs-lookup"><span data-stu-id="9c5a8-134">Connect with Registered Servers and Object Explorer</span></span>](../object/object-explorer.md)  
  
  
