---
title: マスター データ マネージャー Web サービス プロキシ クラスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 8bdab026-a0c0-41f3-9d36-f3919c23247f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4f25d749f829357f6541f14073e654bade27215
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646186"
---
# <a name="create-master-data-manager-web-service-proxy-classes"></a><span data-ttu-id="895c1-102">マスター データ マネージャー Web サービス プロキシ クラスの作成</span><span class="sxs-lookup"><span data-stu-id="895c1-102">Create Master Data Manager Web Service Proxy Classes</span></span>
  <span data-ttu-id="895c1-103">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web サービスを使用すると、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web サイトにアクセスできる任意のコンピューターから、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の機能をプログラム経由で使用できます。</span><span class="sxs-lookup"><span data-stu-id="895c1-103">The [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web service lets you make programmatic use of the features of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] from any computer that can access your [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web site.</span></span> <span data-ttu-id="895c1-104">Web サービスにアクセスするコードの記述を開始する前に、プロキシ クラスを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="895c1-104">Before you can start writing code to access the web service, you must generate proxy classes.</span></span> <span data-ttu-id="895c1-105">Web サービス操作の実行に使用する主要なプロキシ クラスは、<xref:Microsoft.MasterDataServices.ServiceClient> クラスです。このクラスは、<xref:Microsoft.MasterDataServices.IService> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="895c1-105">The main proxy class you use to perform web service operations is the <xref:Microsoft.MasterDataServices.ServiceClient> class, which implements the <xref:Microsoft.MasterDataServices.IService> interface.</span></span>  
  
## <a name="enable-web-service-metadata-publishing"></a><span data-ttu-id="895c1-106">Web サービス メタデータ パブリッシュの有効化</span><span class="sxs-lookup"><span data-stu-id="895c1-106">Enable Web Service Metadata Publishing</span></span>  
 <span data-ttu-id="895c1-107">プロキシ クラスを生成する前に、Web サービス メタデータ パブリッシュを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="895c1-107">Before you can generate proxy classes, you must enable web service metadata publishing.</span></span> <span data-ttu-id="895c1-108">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="895c1-108">Follow these steps to do this:</span></span>  
  
1.  <span data-ttu-id="895c1-109">テキスト エディターで [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="895c1-109">Open the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web.config file in a text editor.</span></span> <span data-ttu-id="895c1-110">このファイルは、[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] インストール パスの WebApplication フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="895c1-110">This file is in the WebApplication folder of the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] installation path.</span></span>  
  
2.  <span data-ttu-id="895c1-111">の下のセクションを探し `mdsWsHttpBehavior` **\<serviceBehaviors>** ます。</span><span class="sxs-lookup"><span data-stu-id="895c1-111">Find the `mdsWsHttpBehavior` section under **\<serviceBehaviors>**.</span></span> <span data-ttu-id="895c1-112">要素の **\<serviceMetadata>** 場合は、 `httpGetEnabled` をに設定 `true` します。</span><span class="sxs-lookup"><span data-stu-id="895c1-112">For the **\<serviceMetadata>** element, set `httpGetEnabled` to `true`.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="895c1-113">Web サービスを SSL (Secure Sockets Layer) を介して有効にするには、web.config ファイルの `httpsGetEnabled` セクションで、`true` を `mdsWsHttpBehavior` に設定します。</span><span class="sxs-lookup"><span data-stu-id="895c1-113">If you want to enable Web services over Secure Sockets Layer (SSL), set `httpsGetEnabled` to `true` in the `mdsWsHttpBehavior` section of the web.config file.</span></span> <span data-ttu-id="895c1-114">さらに、SSL 用に構成されるように `mdsWsHTTPBinding` を変更し、非 SSL セクションをコメント アウトする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="895c1-114">You also need to change `mdsWsHTTPBinding` so that it is configured for SSL, as well, and comment out the non-SSL section.</span></span>  
  
3.  <span data-ttu-id="895c1-115">変更をファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="895c1-115">Save changes to the file.</span></span>  
  
4.  <span data-ttu-id="895c1-116">サービス URL (たとえば、http://yourserver/MDS/service/service.svc) を参照して、メタデータのパブリッシュをテストします。</span><span class="sxs-lookup"><span data-stu-id="895c1-116">Test metadata publishing by browsing to the service URL, for example: http://yourserver/MDS/service/service.svc.</span></span> <span data-ttu-id="895c1-117">メタデータ パブリッシュが有効化されると、</span><span class="sxs-lookup"><span data-stu-id="895c1-117">If metadata publishing is enabled, a page is displayed that begins with</span></span>   
    <span data-ttu-id="895c1-118">"サービスを作成しました。" で始まるページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="895c1-118">"You have created a service."</span></span>  
  
## <a name="creating-proxy-classes-by-using-visual-studio"></a><span data-ttu-id="895c1-119">Visual Studio を使用してプロキシ クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="895c1-119">Creating Proxy Classes by Using Visual Studio</span></span>  
 <span data-ttu-id="895c1-120">Visual Studio 2010 がインストールされている場合、プロキシ クラスを生成する最もシンプルな方法は、プロジェクトに**サービス参照**を追加することです。</span><span class="sxs-lookup"><span data-stu-id="895c1-120">If you have Visual Studio 2010 installed, the simplest way to generate proxy classes is to add a **Service Reference** to your project.</span></span> <span data-ttu-id="895c1-121">サービス参照のアドレスは、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションの URL に、/service/service.svc を付加したものです。</span><span class="sxs-lookup"><span data-stu-id="895c1-121">The address of the service reference is the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, appended with /service/service.svc.</span></span> <span data-ttu-id="895c1-122">(例: http://yourserver/MDS/service/service.svc)。</span><span class="sxs-lookup"><span data-stu-id="895c1-122">For example: http://yourserver/MDS/service/service.svc.</span></span> <span data-ttu-id="895c1-123">詳細については、「[方法: サービス参照を追加、更新、または削除する](https://go.microsoft.com/fwlink/?LinkId=221167)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="895c1-123">For more information, see [How to: Add, Update, or Remove a Service Reference](https://go.microsoft.com/fwlink/?LinkId=221167).</span></span>  
  
## <a name="creating-proxy-classes-by-using-svcutilexe"></a><span data-ttu-id="895c1-124">Svcutil.exe を使用してプロキシ クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="895c1-124">Creating Proxy Classes by Using Svcutil.exe</span></span>  
 <span data-ttu-id="895c1-125">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] コンピューターに Svcutil.exe を使用するには、または Windows SDK がインストールされている必要があり [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="895c1-125">You must have either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows SDK installed in order to have Svcutil.exe on your computer.</span></span> <span data-ttu-id="895c1-126">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を使用する場合は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] コマンド プロンプトでコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="895c1-126">If you use [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], you must use the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] command prompt to run the command.</span></span> <span data-ttu-id="895c1-127">詳細については、「[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027)」および「[サービス メタデータからの WCF クライアントの生成](https://go.microsoft.com/fwlink/?LinkId=164821)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="895c1-127">For more information, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](https://go.microsoft.com/fwlink/?LinkId=165027) and [Generating a WCF Client from Service Metadata](https://go.microsoft.com/fwlink/?LinkId=164821).</span></span>  
  
 <span data-ttu-id="895c1-128">Svcutil.exe を使用して一連の C# プロキシ クラスを作成するには、次のようなコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="895c1-128">To create a set of C# proxy classes by using Svcutil.exe, use a command such as the following:</span></span>  
  
```  
svcutil.exe http://<server_name:port>/<virtual_path>/Service/Service.svc   
/out:<proxy_name>.cs /messageContract /tcv:Version35   
/noconfig /ct:System.Collections.ObjectModel.Collection`1   
/namespace:*,Microsoft.MasterDataServices  
```  
  
 <span data-ttu-id="895c1-129">この場合、</span><span class="sxs-lookup"><span data-stu-id="895c1-129">Where:</span></span>  
  
-   <span data-ttu-id="895c1-130">*servername*:*port* は、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] をホストするコンピューターのコンピューター名およびポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="895c1-130">*servername*:*port* are the computer name and port number of the computer that hosts [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="895c1-131">*virtual_path* には、インターネット インフォメーション サービス (IIS) の [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の仮想パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="895c1-131">*virtual_path* is the virtual path of [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in Internet Information Services (IIS).</span></span>  
  
-   <span data-ttu-id="895c1-132">*proxy_name* には、生成されるプロキシ ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="895c1-132">*proxy_name* is the name for the generated proxy file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895c1-133">参照</span><span class="sxs-lookup"><span data-stu-id="895c1-133">See Also</span></span>  
 [<span data-ttu-id="895c1-134">Web サービス操作の分類 &#40;マスター データ サービス&#41;</span><span class="sxs-lookup"><span data-stu-id="895c1-134">Categorized Web Service Operations &#40;Master Data Services&#41;</span></span>](categorized-web-service-operations-master-data-services.md)  
  
  
