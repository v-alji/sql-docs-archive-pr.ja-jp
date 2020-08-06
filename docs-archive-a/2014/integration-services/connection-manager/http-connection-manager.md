---
title: HTTP 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- HTTP connection manager
- Web site connections [Integration Services]
- connection managers [Integration Services], HTTP
- Web server connections [Integration Services]
- connections [Integration Services], HTTP
ms.assetid: 26b2b3e1-d02c-46ca-8d31-7aef2bbc3c53
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 10c9f0778faa25aff8db4ad54ecaa8d3ccc5b359
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740200"
---
# <a name="http-connection-manager"></a><span data-ttu-id="2a982-102">HTTP 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="2a982-102">HTTP Connection Manager</span></span>
  <span data-ttu-id="2a982-103">HTTP 接続により、パッケージが HTTP を使用してファイルを送受信することで、Web サーバーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="2a982-103">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span> <span data-ttu-id="2a982-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる Web サービス タスクでは、この接続マネージャーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2a982-104">The Web Service task that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses this connection manager.</span></span>  
  
 <span data-ttu-id="2a982-105">HTTP 接続マネージャーをパッケージに追加するときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時に HTTP 接続を解決する接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージの `Connections` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="2a982-105">When you add an HTTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an HTTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="2a982-106">`ConnectionManagerType`接続マネージャーのプロパティがに設定されています。`HTTP.`</span><span class="sxs-lookup"><span data-stu-id="2a982-106">The `ConnectionManagerType` property of the connection manager is set to `HTTP.`</span></span>  
  
 <span data-ttu-id="2a982-107">HTTP 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="2a982-107">You can configure the HTTP connection manager the following ways:</span></span>  
  
-   <span data-ttu-id="2a982-108">資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a982-108">Use credentials.</span></span> <span data-ttu-id="2a982-109">接続マネージャーが資格情報を使用する場合、プロパティにユーザー名、パスワード、およびドメインが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2a982-109">If the connection manager uses credentials, its properties include the user name, password, and domain.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2a982-110">HTTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2a982-110">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="2a982-111">Windows 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2a982-111">It does not support Windows Authentication.</span></span>  
  
-   <span data-ttu-id="2a982-112">クライアント証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a982-112">Use a client certificate.</span></span> <span data-ttu-id="2a982-113">接続マネージャーがクライアント証明書を使用する場合、プロパティに証明書名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2a982-113">If the connection manager uses a client certificate, its properties include the certificate name.</span></span>  
  
-   <span data-ttu-id="2a982-114">サーバーへの接続のタイムアウトと、データを書き込むチャンク サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a982-114">Provide a time-out for connecting to the server and a chunk size for writing data.</span></span>  
  
-   <span data-ttu-id="2a982-115">プロキシ サーバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="2a982-115">Use a proxy server.</span></span> <span data-ttu-id="2a982-116">プロキシ サーバーは、資格情報を使用するように構成することや、プロキシ サーバーをバイパスして、代わりにローカル アドレスを使用するように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a982-116">The proxy server can also be configured to use credentials and to bypass the proxy server and use local addresses instead.</span></span>  
  
## <a name="configuration-of-the-http-connection-manager"></a><span data-ttu-id="2a982-117">HTTP 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="2a982-117">Configuration of the HTTP Connection Manager</span></span>  
 <span data-ttu-id="2a982-118">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="2a982-118">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2a982-119">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a982-119">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="2a982-120">[[HTTP 接続マネージャー エディター] ([サーバー] ページ)](../http-connection-manager-editor-server-page.md)</span><span class="sxs-lookup"><span data-stu-id="2a982-120">[HTTP Connection Manager Editor &#40;Server Page&#41;](../http-connection-manager-editor-server-page.md)</span></span>  
  
-   <span data-ttu-id="2a982-121">[[HTTP 接続マネージャー エディター] ([プロキシ] ページ)](../http-connection-manager-editor-proxy-page.md)</span><span class="sxs-lookup"><span data-stu-id="2a982-121">[HTTP Connection Manager Editor &#40;Proxy Page&#41;](../http-connection-manager-editor-proxy-page.md)</span></span>  
  
 <span data-ttu-id="2a982-122">プログラムによる接続マネージャーの構成の詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a982-122">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a982-123">参照</span><span class="sxs-lookup"><span data-stu-id="2a982-123">See Also</span></span>  
 <span data-ttu-id="2a982-124">[Web サービスタスク](../control-flow/web-service-task.md) </span><span class="sxs-lookup"><span data-stu-id="2a982-124">[Web Service Task](../control-flow/web-service-task.md) </span></span>  
 [<span data-ttu-id="2a982-125">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="2a982-125">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
