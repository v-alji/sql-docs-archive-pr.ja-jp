---
title: '[HTTP 接続マネージャーエディター] ([サーバー] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.httpconnection.server.f1
helpviewer_keywords:
- HTTP Connection Manager Editor
ms.assetid: 774778a0-ece6-4971-b93f-b121d8fc1fc1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2349766b11b28ff258496dc966d554d49c7657b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632581"
---
# <a name="http-connection-manager-editor-server-page"></a><span data-ttu-id="0bc2c-102">[HTTP 接続マネージャー エディター] ([サーバー] ページ)</span><span class="sxs-lookup"><span data-stu-id="0bc2c-102">HTTP Connection Manager Editor (Server Page)</span></span>
  <span data-ttu-id="0bc2c-103">**[HTTP 接続マネージャー エディター]** ダイアログ ボックスの **[サーバー]** タブを使用すると、URL やセキュリティ資格情報などのプロパティを指定して、HTTP 接続マネージャーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-103">Use the **Server** tab of the **HTTP Connection Manager Editor** dialog box to configure the HTTP Connection Manager by specifying properties such as the URL and security credentials.</span></span> <span data-ttu-id="0bc2c-104">HTTP 接続により、パッケージが HTTP を使用してファイルを送受信することで、Web サーバーにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-104">An HTTP connection enables a package to access a Web server by using HTTP to send or receive files.</span></span> <span data-ttu-id="0bc2c-105">HTTP 接続マネージャーを構成した後に接続をテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-105">After configuring the HTTP Connection Manager, you can also test the connection.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0bc2c-106">HTTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-106">The HTTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="0bc2c-107">Windows 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-107">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="0bc2c-108">HTTP 接続マネージャーの詳細については、「 [HTTP Connection Manager](connection-manager/http-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-108">To learn more about the HTTP connection manager, see [HTTP Connection Manager](connection-manager/http-connection-manager.md).</span></span> <span data-ttu-id="0bc2c-109">HTTP 接続マネージャーの一般的な使用シナリオの詳細については、「 [Web Service Task](control-flow/web-service-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-109">To learn more about a common usage scenario for the HTTP Connection Manager, see [Web Service Task](control-flow/web-service-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="0bc2c-110">Options</span><span class="sxs-lookup"><span data-stu-id="0bc2c-110">Options</span></span>  
 <span data-ttu-id="0bc2c-111">**[サーバー URL]**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-111">**Server URL**</span></span>  
 <span data-ttu-id="0bc2c-112">サーバーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-112">Type the URL for the server.</span></span>  
  
 <span data-ttu-id="0bc2c-113">**[Web サービス タスク エディター]** の **[全般]** ページにある **[WSDL のダウンロード]** ボタンを使用する場合は、WSDL ファイルの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-113">If you plan to use the **Download WSDL** button on the **General** page of the **Web Service Task Editor** to download a WSDL file, type the URL for the WSDL file.</span></span> <span data-ttu-id="0bc2c-114">この URL は "?wsdl" で終わります。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-114">This URL ends with "?wsdl".</span></span>  
  
 <span data-ttu-id="0bc2c-115">**資格情報の使用**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-115">**Use credentials**</span></span>  
 <span data-ttu-id="0bc2c-116">HTTP 接続マネージャーで、認証のためにユーザーのセキュリティ資格情報を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-116">Specify whether you want the HTTP Connection Manager to use the user's security credentials for authentication.</span></span>  
  
 <span data-ttu-id="0bc2c-117">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-117">**User name**</span></span>  
 <span data-ttu-id="0bc2c-118">HTTP 接続マネージャーで資格情報を使用する場合は、ユーザー名、パスワード、およびドメインを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-118">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="0bc2c-119">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-119">**Password**</span></span>  
 <span data-ttu-id="0bc2c-120">HTTP 接続マネージャーで資格情報を使用する場合は、ユーザー名、パスワード、およびドメインを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-120">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="0bc2c-121">**[ドメイン]**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-121">**Domain**</span></span>  
 <span data-ttu-id="0bc2c-122">HTTP 接続マネージャーで資格情報を使用する場合は、ユーザー名、パスワード、およびドメインを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-122">If the HTTP Connection Manager uses credentials, you must specify a user name, password, and domain.</span></span>  
  
 <span data-ttu-id="0bc2c-123">**[クライアント証明書を使用する]**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-123">**Use client certificate**</span></span>  
 <span data-ttu-id="0bc2c-124">HTTP 接続マネージャーで、認証のためにクライアント証明書を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-124">Specify whether you want the HTTP Connection Manager to use a client certificate for authentication.</span></span>  
  
 <span data-ttu-id="0bc2c-125">**[MSSQLSERVER のプロトコルのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-125">**Certificate**</span></span>  
 <span data-ttu-id="0bc2c-126">**[証明書の選択]** ダイアログ ボックスを使用して、一覧から証明書を選択します。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-126">Select a certificate from the list by using the **Select Certificate** dialog box.</span></span> <span data-ttu-id="0bc2c-127">テキスト ボックスに、この証明書に関連付けられている名前が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-127">The text box displays the name associated with this certificate.</span></span>  
  
 <span data-ttu-id="0bc2c-128">**[タイムアウト (秒)]**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-128">**Time-out (in seconds)**</span></span>  
 <span data-ttu-id="0bc2c-129">Web サーバーへの接続のタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-129">Provide a time-out for connecting to the Web server.</span></span> <span data-ttu-id="0bc2c-130">このプロパティの既定値は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-130">The default value of this property is 30 seconds.</span></span>  
  
 <span data-ttu-id="0bc2c-131">**[チャンク サイズ (KB)]**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-131">**Chunk size (in KB)**</span></span>  
 <span data-ttu-id="0bc2c-132">データを書き込むためのチャンクのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-132">Provide a chunk size for writing data.</span></span>  
  
 <span data-ttu-id="0bc2c-133">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="0bc2c-133">**Test Connection**</span></span>  
 <span data-ttu-id="0bc2c-134">HTTP 接続マネージャーを構成した後に、 **[接続テスト]** をクリックして、接続が利用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0bc2c-134">After configuring the HTTP Connection Manager, confirm that the connection is viable by clicking **Test Connection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc2c-135">参照</span><span class="sxs-lookup"><span data-stu-id="0bc2c-135">See Also</span></span>  
 <span data-ttu-id="0bc2c-136">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0bc2c-136">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="0bc2c-137">[[HTTP 接続マネージャー エディター] ([プロキシ] ページ)](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)</span><span class="sxs-lookup"><span data-stu-id="0bc2c-137">[HTTP Connection Manager Editor &#40;Proxy Page&#41;](../../2014/integration-services/http-connection-manager-editor-proxy-page.md)</span></span>  
  
  
