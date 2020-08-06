---
title: '[HTTP 接続マネージャーエディター] ([プロキシ] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.proxy.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: e831a830-49a3-49c5-8a31-9731fc4fd12e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f8269dbbeb226ffa3f56c226e1a416d99c1e3f13
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632586"
---
# <a name="http-connection-manager-editor-proxy-page"></a><span data-ttu-id="15d30-102">[HTTP 接続マネージャー エディター] ([プロキシ] ページ)</span><span class="sxs-lookup"><span data-stu-id="15d30-102">HTTP Connection Manager Editor (Proxy Page)</span></span>
  <span data-ttu-id="15d30-103">**[HTTP 接続マネージャー エディター]** の **[プロキシ]** タブを使用すると、HTTP 接続マネージャーがプロキシ サーバーを使用するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="15d30-103">Use the **Proxy** tab of the **HTTP Connection Manager Editor** dialog box to configure the HTTP Connection Manager to use a proxy server.</span></span> <span data-ttu-id="15d30-104">HTTP 接続により、パッケージが HTTP を使用してファイルを送受信することで、Web サーバーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="15d30-104">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span>  
  
 <span data-ttu-id="15d30-105">HTTP 接続マネージャーの詳細については、「 [HTTP Connection Manager](connection-manager/http-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15d30-105">To learn more about the HTTP connection manager, see [HTTP Connection Manager](connection-manager/http-connection-manager.md).</span></span> <span data-ttu-id="15d30-106">HTTP 接続マネージャーの一般的な使用シナリオの詳細については、「 [Web Service Task](control-flow/web-service-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15d30-106">To learn more about a common usage scenario for the HTTP Connection Manager, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="15d30-107">Options</span><span class="sxs-lookup"><span data-stu-id="15d30-107">Options</span></span>  
 <span data-ttu-id="15d30-108">**[プロキシを使用する]**</span><span class="sxs-lookup"><span data-stu-id="15d30-108">**Use proxy**</span></span>  
 <span data-ttu-id="15d30-109">HTTP 接続マネージャーでプロキシ サーバーを使用して接続するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="15d30-109">Specify whether you want the HTTP Connection Manager to connect through a proxy server.</span></span>  
  
 <span data-ttu-id="15d30-110">**プロキシ URL**</span><span class="sxs-lookup"><span data-stu-id="15d30-110">**Proxy URL**</span></span>  
 <span data-ttu-id="15d30-111">プロキシ サーバーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="15d30-111">Type the URL for the proxy server.</span></span>  
  
 <span data-ttu-id="15d30-112">**[ローカルではプロキシを使用しない]**</span><span class="sxs-lookup"><span data-stu-id="15d30-112">**Bypass proxy on local**</span></span>  
 <span data-ttu-id="15d30-113">HTTP 接続マネージャーで、ローカル アドレスの場合はプロキシ サーバーを使用しないかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="15d30-113">Specify whether you want the HTTP Connection Manager to bypass the proxy server for local addresses.</span></span>  
  
 <span data-ttu-id="15d30-114">**資格情報の使用**</span><span class="sxs-lookup"><span data-stu-id="15d30-114">**Use credentials**</span></span>  
 <span data-ttu-id="15d30-115">HTTP 接続マネージャーで、プロキシ サーバーに対してセキュリティ資格情報を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="15d30-115">Specify whether you want the HTTP Connection Manager to use security credentials for the proxy server.</span></span>  
  
 <span data-ttu-id="15d30-116">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="15d30-116">**User name**</span></span>  
 <span data-ttu-id="15d30-117">HTTP 接続マネージャーで資格情報を使用する場合は、ユーザー名、パスワード、およびドメインを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d30-117">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="15d30-118">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="15d30-118">**Password**</span></span>  
 <span data-ttu-id="15d30-119">HTTP 接続マネージャーで資格情報を使用する場合は、ユーザー名、パスワード、およびドメインを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d30-119">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="15d30-120">**[ドメイン]**</span><span class="sxs-lookup"><span data-stu-id="15d30-120">**Domain**</span></span>  
 <span data-ttu-id="15d30-121">HTTP 接続マネージャーで資格情報を使用する場合は、ユーザー名、パスワード、およびドメインを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15d30-121">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="15d30-122">**[プロキシ バイパス一覧]**</span><span class="sxs-lookup"><span data-stu-id="15d30-122">**Proxy bypass list**</span></span>  
 <span data-ttu-id="15d30-123">プロキシ サーバーを使用しないアドレスの一覧です。</span><span class="sxs-lookup"><span data-stu-id="15d30-123">The list of addresses for which  you want to bypass the proxy server.</span></span>  
  
 <span data-ttu-id="15d30-124">**[追加]**</span><span class="sxs-lookup"><span data-stu-id="15d30-124">**Add**</span></span>  
 <span data-ttu-id="15d30-125">プロキシ サーバーを使用しないアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="15d30-125">Type an address for which you want to bypass the proxy server.</span></span>  
  
 <span data-ttu-id="15d30-126">**削除**</span><span class="sxs-lookup"><span data-stu-id="15d30-126">**Remove**</span></span>  
 <span data-ttu-id="15d30-127">アドレスを選択した後、 **[削除]** をクリックするとアドレスが削除されます。</span><span class="sxs-lookup"><span data-stu-id="15d30-127">Select an address, and then remove it by clicking **Remove**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d30-128">参照</span><span class="sxs-lookup"><span data-stu-id="15d30-128">See Also</span></span>  
 <span data-ttu-id="15d30-129">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="15d30-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="15d30-130">[[HTTP 接続マネージャー エディター] ([サーバー] ページ)](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span><span class="sxs-lookup"><span data-stu-id="15d30-130">[HTTP Connection Manager Editor &#40;Server Page&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)</span></span>  
  
  
