---
title: SQL Server のプロパティ ([詳細設定] タブ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2ffd10fd-bac1-478f-9cff-96ed6c8b787f
author: stevestein
ms.author: sstein
ms.openlocfilehash: a9a77fd0a43627b49bb8719f6fa943408f64fcca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631441"
---
# <a name="sql-server-properties-advanced-tab"></a><span data-ttu-id="5085d-102">[SQL Server のプロパティ] ダイアログ ボックス ([詳細設定] タブ)</span><span class="sxs-lookup"><span data-stu-id="5085d-102">SQL Server Properties (Advanced Tab)</span></span>
  <span data-ttu-id="5085d-103">**[詳細設定]** タブには、以下のプロパティが既定で表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-103">The following properties appear on the **Advanced** tab by default.</span></span> <span data-ttu-id="5085d-104">カスタム プロパティが定義されていれば、そのプロパティと値もこのタブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-104">If custom properties are defined, they also appear on this tab, with their values.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5085d-105">オプション</span><span class="sxs-lookup"><span data-stu-id="5085d-105">Options</span></span>  
 <span data-ttu-id="5085d-106">**クラスター化インデックス**</span><span class="sxs-lookup"><span data-stu-id="5085d-106">**Clustered**</span></span>  
 <span data-ttu-id="5085d-107">このサービスがクラスター サーバーのリソースとしてインストールされているかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-107">Indicates if this service is installed as a resource of a clustered server.</span></span>  
  
 <span data-ttu-id="5085d-108">**[カスタマー フィードバック レポート]**</span><span class="sxs-lookup"><span data-stu-id="5085d-108">**Customer Feedback Reporting**</span></span>  
 <span data-ttu-id="5085d-109">サービス品質の監視がこのサービスで有効になっているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="5085d-109">Indicates whether Service Quality Monitoring has been enabled on this service.</span></span> <span data-ttu-id="5085d-110">カスタマー フィードバック報告の詳細については、オンライン ブックの「エラー レポートと使用状況レポートの設定」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="5085d-110">For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span>  
  
 <span data-ttu-id="5085d-111">**[データ パス]**</span><span class="sxs-lookup"><span data-stu-id="5085d-111">**Data Path**</span></span>  
 <span data-ttu-id="5085d-112">このインストールの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バイナリへのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-112">Displays the path to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5085d-113">**[ダンプ ディレクトリ]**</span><span class="sxs-lookup"><span data-stu-id="5085d-113">**Dump Directory**</span></span>  
 <span data-ttu-id="5085d-114">エラー発生時にメモリ ダンプが配置される場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-114">Displays the location where memory dumps are placed in case of an error.</span></span>  
  
 <span data-ttu-id="5085d-115">**[エラー報告]**</span><span class="sxs-lookup"><span data-stu-id="5085d-115">**Error Reporting**</span></span>  
 <span data-ttu-id="5085d-116">**[はい]** に設定した場合、重大な障害が発生したときに、ワトソン博士プログラムによって [!INCLUDE[msCoName](../../includes/msconame-md.md)] またはエラー サーバーに情報が転送されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-116">When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../includes/msconame-md.md)] or your error server if a serious failure occurs.</span></span> <span data-ttu-id="5085d-117">エラー報告の詳細については、オンライン ブックの「エラー レポートと使用状況レポートの設定」を検索してください。</span><span class="sxs-lookup"><span data-stu-id="5085d-117">For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."</span></span> <span data-ttu-id="5085d-118">この値を変更するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] オブジェクト エクスプローラーでサーバーを右クリックし、 **[プロパティ]** をクリックし、 **[その他のサーバーの設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5085d-118">To change this value, in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Object Explorer, right-click your server, click **Properties**, and then click the **Misc. Server Settings** page.</span></span> <span data-ttu-id="5085d-119">**[エラー報告]** 領域にオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-119">The options are presented in the **Information Reporting** area.</span></span>  
  
 <span data-ttu-id="5085d-120">**ファイル バージョン**</span><span class="sxs-lookup"><span data-stu-id="5085d-120">**File Version**</span></span>  
 <span data-ttu-id="5085d-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 実行可能ファイルのバージョンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-121">Displays the version of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] executable.</span></span>  
  
 <span data-ttu-id="5085d-122">**インストール パス**</span><span class="sxs-lookup"><span data-stu-id="5085d-122">**Install Path**</span></span>  
 <span data-ttu-id="5085d-123">このインストールの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バイナリへのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-123">Displays the path to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] binaries for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5085d-124">**インスタンス ID**</span><span class="sxs-lookup"><span data-stu-id="5085d-124">**Instance ID**</span></span>  
 <span data-ttu-id="5085d-125">このサービスを使用した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-125">Indicates the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that used this service.</span></span>  
  
 <span data-ttu-id="5085d-126">**Language**</span><span class="sxs-lookup"><span data-stu-id="5085d-126">**Language**</span></span>  
 <span data-ttu-id="5085d-127">サーバー メッセージの既定の言語が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-127">Displays the default language for server messages.</span></span>  
  
 <span data-ttu-id="5085d-128">**[レジストリ ルート]**</span><span class="sxs-lookup"><span data-stu-id="5085d-128">**Registry Root**</span></span>  
 <span data-ttu-id="5085d-129">このアプリケーションが使用するレジストリ キーの場所が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-129">Displays the location of the registry keys used by this application.</span></span>  
  
 <span data-ttu-id="5085d-130">**[Service Pack のレベル]**</span><span class="sxs-lookup"><span data-stu-id="5085d-130">**Service Pack Level**</span></span>  
 <span data-ttu-id="5085d-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこのインスタンスのサービス パック レベルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-131">Displays the service pack level of this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5085d-132">**[SKU 名]**</span><span class="sxs-lookup"><span data-stu-id="5085d-132">**SKU Name**</span></span>  
 <span data-ttu-id="5085d-133">製品の SKU (Stock Keeping Unit、製品のエディションとも呼ばれます) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-133">Displays the product stock keeping unit (SKU), sometimes called the product edition.</span></span>  
  
 <span data-ttu-id="5085d-134">**起動時のパラメーター**</span><span class="sxs-lookup"><span data-stu-id="5085d-134">**Startup Parameters**</span></span>  
 <span data-ttu-id="5085d-135">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが使用する起動時のパラメーターが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-135">Lists any startup parameters that are used by this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5085d-136">各パラメーターはセミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="5085d-136">Parameters are separated by semi-colons.</span></span> <span data-ttu-id="5085d-137">既定のパラメーターには、master データベースのデータ ファイル (`master.mdf`) のパス、master データベースのログ ファイル (`mastlog.ldf`) のパス、エラー ログ ファイルのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5085d-137">The default parameters include the paths to the data file for the master database (`master.mdf`), the log file for the master database (`mastlog.ldf`), and the error log file.</span></span> <span data-ttu-id="5085d-138">起動時のパラメーターの構文については、オンライン ブックの **「SQL Server サービスのスタートアップ オプションの使用」** を検索してください。</span><span class="sxs-lookup"><span data-stu-id="5085d-138">For the syntax of startup parameters, search Books Online for the topic **Using the SQL Server Service Startup Options.**</span></span>  
  
 <span data-ttu-id="5085d-139">**[SKU (Stock Keeping Unit)]**</span><span class="sxs-lookup"><span data-stu-id="5085d-139">**Stock Keeping Unit**</span></span>  
 <span data-ttu-id="5085d-140">製品の SKU (Stock Keeping Unit) 番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-140">Displays the product stock keeping unit (SKU) number.</span></span>  
  
 <span data-ttu-id="5085d-141">**バージョン**</span><span class="sxs-lookup"><span data-stu-id="5085d-141">**Version**</span></span>  
 <span data-ttu-id="5085d-142">この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスのバージョン番号が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5085d-142">Displays the version number of this instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5085d-143">**[仮想サーバー名]**</span><span class="sxs-lookup"><span data-stu-id="5085d-143">**Virtual Server Name**</span></span>  
 <span data-ttu-id="5085d-144">**がクラスター サーバーにインストールされている場合の** 仮想サーバー名 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="5085d-144">**Virtual Server Name** when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed on a clustered server.</span></span>  
  
  
