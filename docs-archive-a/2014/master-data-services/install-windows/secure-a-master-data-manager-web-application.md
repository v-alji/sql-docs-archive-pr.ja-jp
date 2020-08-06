---
title: マスター データ マネージャー Web アプリケーションのセキュリティ保護 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 8f2ee807c2cd474542f701226d08427ade8279e3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738497"
---
# <a name="secure-a-master-data-manager-web-application"></a><span data-ttu-id="f2536-102">マスター データ マネージャー Web アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f2536-102">Secure a Master Data Manager Web Application</span></span>
  <span data-ttu-id="f2536-103">HTTPS を使用して [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションをセキュリティ保護できます。</span><span class="sxs-lookup"><span data-stu-id="f2536-103">You can secure the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application with HTTPS.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2536-104">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションは、HTTP または HTTPS のいずれかを使用できますが、両方を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f2536-104">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application can use either HTTP or HTTPS, but not both.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f2536-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="f2536-105">Prerequisites</span></span>  
 <span data-ttu-id="f2536-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="f2536-106">To perform the procedure:</span></span>  
  
-   <span data-ttu-id="f2536-107">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] がインストールされている Web サーバーの管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2536-107">You must be an administrator on the web server where [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] is installed.</span></span>  
  
-   <span data-ttu-id="f2536-108">MDS が Web サーバーにインストールされていて、Web アプリケーションが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2536-108">MDS must be installed on the web server, and a web application must exist.</span></span> <span data-ttu-id="f2536-109">詳細については、「 [マスター データ サービスのインストール](install-master-data-services.md) 」および「 [マスター データ マネージャー Web アプリケーションの作成 &#40;マスター データ サービス&#41;](create-a-master-data-manager-web-application-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2536-109">For more information, see [Install Master Data Services](install-master-data-services.md) and [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).</span></span>  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a><span data-ttu-id="f2536-110">HTTPS を使用してマスター データ マネージャー Web アプリケーションをセキュリティ保護するには</span><span class="sxs-lookup"><span data-stu-id="f2536-110">To secure the Master Data Manager web application with HTTPS</span></span>  
  
1.  <span data-ttu-id="f2536-111">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションが HTTP を使用して正しく構成されていることを確認した後、IIS で証明書を作成します。</span><span class="sxs-lookup"><span data-stu-id="f2536-111">After you have confirmed that the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application is configured correctly with HTTP, create a certificate in IIS.</span></span> <span data-ttu-id="f2536-112">詳細については、「 [IIS 7 でサーバー証明書を構成する](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2536-112">For more information, see [Configuring Server Certificates in IIS 7](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).</span></span>  
  
2.  <span data-ttu-id="f2536-113">**[接続]** ペインの **[サイト]** で、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションをホストするサイトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2536-113">In the **Connections** pane, under **Sites**, click the site that hosts the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
3.  <span data-ttu-id="f2536-114">**[操作]** ウィンドウで、**[バインド]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2536-114">In the **Actions** pane, click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="f2536-115">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2536-115">Click **Add**.</span></span>  
  
5.  <span data-ttu-id="f2536-116">一覧から、 **[https]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f2536-116">From the list, select **https**.</span></span>  
  
6.  <span data-ttu-id="f2536-117">SSL 証明書を選択します。</span><span class="sxs-lookup"><span data-stu-id="f2536-117">Select the SSL certificate.</span></span>  
  
7.  <span data-ttu-id="f2536-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2536-118">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="f2536-119">省略可能。</span><span class="sxs-lookup"><span data-stu-id="f2536-119">Optional.</span></span> <span data-ttu-id="f2536-120">HTTP を削除してユーザーが HTTPS のみを使用してサイトにアクセスできるようにするには、一覧の **[http]** の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2536-120">To remove HTTP so that users can access the site with HTTPS only, from the list, click the row with **http**.</span></span> <span data-ttu-id="f2536-121">**[削除]** をクリックし、確認のダイアログ ボックスで **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2536-121">Click **Remove** and on the confirmation dialog box, click **Yes**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f2536-122">HTTP を削除した後に basicHttp 構成および wsHttpBinding 構成を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2536-122">You must change basicHttp and wsHttpBinding configurations after removing HTTP.</span></span>  
  
9. <span data-ttu-id="f2536-123">**[サイト バインド]** ダイアログ ボックスを閉じるには、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f2536-123">To close the **Site Bindings** dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="f2536-124">ここで、*ドライブ*: services\webapplication です。からファイル web.config を開きます。</span><span class="sxs-lookup"><span data-stu-id="f2536-124">Now open the web.config file from *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\WebApplication.</span></span>  
  
11. <span data-ttu-id="f2536-125">" `<security mode="Message">` " という文字列を探して、" `<security mode="Transport">`" に変更します。</span><span class="sxs-lookup"><span data-stu-id="f2536-125">Find the string `<security mode="Message">` and change it to `<security mode="Transport">`.</span></span>  
  
12. <span data-ttu-id="f2536-126">ファイルを保存して閉じます。</span><span class="sxs-lookup"><span data-stu-id="f2536-126">Save and close the file.</span></span> <span data-ttu-id="f2536-127">エラーが発生した場合は、UAC が有効になっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f2536-127">If you get an error, it could be because you have UAC enabled.</span></span> <span data-ttu-id="f2536-128">詳細については、 [ユーザー アカウント制御の無効化](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2536-128">For more information, see [Turn off User Account Control](https://technet.microsoft.com/library/cc709691\(WS.10\).aspx).</span></span> <span data-ttu-id="f2536-129">これで、ユーザーが HTTPS を使用してサイトにアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f2536-129">Users should now be able to use HTTPS to access the site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2536-130">参照</span><span class="sxs-lookup"><span data-stu-id="f2536-130">See Also</span></span>  
 [<span data-ttu-id="f2536-131">マスター データ マネージャー Web アプリケーションの作成 &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="f2536-131">Create a Master Data Manager Web Application &#40;Master Data Services&#41;</span></span>](create-a-master-data-manager-web-application-master-data-services.md)  
  
  
