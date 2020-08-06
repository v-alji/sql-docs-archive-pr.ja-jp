---
title: データベースのパブリッシュ (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 98b2914e-7147-40af-ba7d-87253bbe8bf9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 652f2341d24c19e6c5ce34196b0e1c4dc5b09084
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640060"
---
# <a name="publish-a-database-sql-server-management-studio"></a><span data-ttu-id="9a597-102">データベースのパブリッシュ (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="9a597-102">Publish a Database (SQL Server Management Studio)</span></span>
  <span data-ttu-id="9a597-103">**スクリプトの生成とパブリッシュ ウィザード** を使用して、データベース全体または個々のデータベース オブジェクトを Web ホスティング プロバイダーにパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="9a597-103">You can use the **Generate and Publish Scripts Wizard** to publish an entire database or individual database objects to a Web hosting provider.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9a597-104">以前のバージョンでは、このトピックで説明する機能がデータベース パブリッシュ ウィザードで提供されていました。</span><span class="sxs-lookup"><span data-stu-id="9a597-104">The functionality described in this topic used to be provided by the Publish Database Wizard.</span></span> <span data-ttu-id="9a597-105">今回のバージョンから、パブリッシュ機能はスクリプトの生成とパブリッシュ ウィザードに追加され、データベース パブリッシュ ウィザードは廃止されました。</span><span class="sxs-lookup"><span data-stu-id="9a597-105">The publishing functionality has been added to the Generate and Publish Scripts Wizard, and the Publish Database Wizard has been discontinued.</span></span>  
  
## <a name="generate-and-publish-scripts-wizard"></a><span data-ttu-id="9a597-106">スクリプトの生成とパブリッシュ ウィザード</span><span class="sxs-lookup"><span data-stu-id="9a597-106">Generate and Publish Scripts Wizard</span></span>  
 <span data-ttu-id="9a597-107">スクリプトの生成とパブリッシュ ウィザードを使用し、データベース全体または選択したデータベース オブジェクトを Web ホスティング プロバイダーにパブリッシュできます。</span><span class="sxs-lookup"><span data-stu-id="9a597-107">The Generate and Publish Scripts Wizard can be used to publish a database or selected database objects to a Web hosting provider.</span></span> <span data-ttu-id="9a597-108">SQL Server Web ホスティング プロバイダーは、Web サービスの接続インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a597-108">A SQL Server Web hosting provider is a connectivity interface to a Web service.</span></span> <span data-ttu-id="9a597-109">この Web サービスを作成するには、CodePlex 上にある SQL Server Hosting Toolkit の Database Publishing Services プロジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a597-109">The Web service is created by using the Database Publishing Services project from the SQL Server Hosting Toolkit on CodePlex.</span></span> <span data-ttu-id="9a597-110">この Web サービスにより、Web ホスティング事業者の顧客は、スクリプトの生成とパブリッシュ ウィザードを使用して、各自のデータベースをサービスに簡単にパブリッシュできるようになります。</span><span class="sxs-lookup"><span data-stu-id="9a597-110">The Web service makes it easy for the Web hoster customers to publish their databases to the service by using the Generate and Publish Scripts Wizard.</span></span> <span data-ttu-id="9a597-111">SQL Server Hosting Toolkit のダウンロードの詳細については、「 [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9a597-111">For more information about downloading the SQL Server Hosting Toolkit, see [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025).</span></span>  
  
 <span data-ttu-id="9a597-112">スクリプトの生成とパブリッシュ ウィザードを使用して、データベース転送用のスクリプトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a597-112">The Generate and Publish Scripts Wizard can also be used to create a script for transferring a database.</span></span>  
  
#### <a name="to-publish-a-database-to-a-web-service"></a><span data-ttu-id="9a597-113">Web サービスにデータベースをパブリッシュするには</span><span class="sxs-lookup"><span data-stu-id="9a597-113">To publish a database to a Web service</span></span>  
  
1.  <span data-ttu-id="9a597-114">オブジェクト エクスプローラーで **[データベース]** を展開してデータベースを右クリックし、 **[タスク]** をポイントして **[スクリプトの生成とパブリッシュ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a597-114">In Object Explorer, expand **Databases**, right-click a database, point to **Tasks**, and then click **Generate and Publish Scripts**.</span></span> <span data-ttu-id="9a597-115">ウィザードの手順に従って、パブリッシュするデータベース オブジェクトのスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9a597-115">Follow the steps in the wizard to script the database objects for publishing.</span></span>  
  
2.  <span data-ttu-id="9a597-116">**[オブジェクトの選択]** ページで、Web ホスティング サービスにパブリッシュするオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="9a597-116">On the **Choose Objects** page, select the objects to be published to the Web hosting service.</span></span>  
  
3.  <span data-ttu-id="9a597-117">**[スクリプト作成オプションの設定]** ページで、 **[Web サービスにパブリッシュ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9a597-117">On the **Set Scripting Options** page, select **Publish to Web Service**.</span></span>  
  
    1.  <span data-ttu-id="9a597-118">**[プロバイダー]** ボックスで、使用する Web サービスのプロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a597-118">In the **Provider** box, specify the provider for your Web service.</span></span> <span data-ttu-id="9a597-119">Web ホスティング プロバイダーを構成していない場合は、 **[プロバイダーの管理]** をクリックして **[プロバイダーの管理]** ダイアログ ボックスを表示し、使用する Web サービスのプロバイダーを構成します。</span><span class="sxs-lookup"><span data-stu-id="9a597-119">If you have not configured a Web hosting provider, select **Manage Providers** and use the **Manage Providers** dialog box to configure a provider for your Web service.</span></span>  
  
    2.  <span data-ttu-id="9a597-120">パブリッシングの詳細オプションを指定するには、 **[Web サービスにパブリッシュ]** セクションの **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a597-120">To specify advanced publishing options, select the **Advanced** button in the **Publish to Web Service** section.</span></span>  
  
4.  <span data-ttu-id="9a597-121">**[概要]** ページで選択内容を確認します。</span><span class="sxs-lookup"><span data-stu-id="9a597-121">On the **Summary** page, review your selections.</span></span> <span data-ttu-id="9a597-122">選択内容を変更するには、 **[戻る]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a597-122">Click **Previous** to change your selections.</span></span> <span data-ttu-id="9a597-123">選択したオブジェクトをパブリッシュするには、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a597-123">Click **Next** to publish the objects you selected.</span></span>  
  
5.  <span data-ttu-id="9a597-124">**[スクリプトの保存またはパブリッシュ]** ページで、パブリケーションの進行状況を監視します。</span><span class="sxs-lookup"><span data-stu-id="9a597-124">On the **Save or Publish Scripts** page, monitor the progress of the publication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a597-125">参照</span><span class="sxs-lookup"><span data-stu-id="9a597-125">See Also</span></span>  
 <span data-ttu-id="9a597-126">[スクリプトの生成 &#40;SQL Server Management Studio&#41;](../scripting/generate-scripts-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="9a597-126">[Generate Scripts &#40;SQL Server Management Studio&#41;](../scripting/generate-scripts-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="9a597-127">他のサーバーへのデータベースのコピー</span><span class="sxs-lookup"><span data-stu-id="9a597-127">Copy Databases to Other Servers</span></span>](copy-databases-to-other-servers.md)  
  
  
