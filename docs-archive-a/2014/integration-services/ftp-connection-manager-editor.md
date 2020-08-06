---
title: FTP 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftpconnectionmanager.f1
helpviewer_keywords:
- FTP Connection Manager Editor
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d14635a4d90c267801f6d372dda5c7bcc7f4869f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743366"
---
# <a name="ftp-connection-manager-editor"></a><span data-ttu-id="5a619-102">FTP 接続マネージャー エディター</span><span class="sxs-lookup"><span data-stu-id="5a619-102">FTP Connection Manager Editor</span></span>
  <span data-ttu-id="5a619-103">**[FTP 接続マネージャー エディター]** ダイアログ ボックスを使用すると、FTP サーバーに接続するためのプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5a619-103">Use the **FTP Connection Manager Editor** dialog box to specify properties for connecting to an FTP server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="5a619-104">FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5a619-104">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="5a619-105">Windows 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="5a619-105">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="5a619-106">FTP 接続マネージャーの詳細については、「 [FTP 接続マネージャー](connection-manager/ftp-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a619-106">To learn more about the FTP connection manager, see [FTP Connection Manager](connection-manager/ftp-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="5a619-107">Options</span><span class="sxs-lookup"><span data-stu-id="5a619-107">Options</span></span>  
 <span data-ttu-id="5a619-108">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="5a619-108">**Server name**</span></span>  
 <span data-ttu-id="5a619-109">FTP サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a619-109">Provide the name of the FTP server.</span></span>  
  
 <span data-ttu-id="5a619-110">**サーバーポート**</span><span class="sxs-lookup"><span data-stu-id="5a619-110">**Server port**</span></span>  
 <span data-ttu-id="5a619-111">接続に使用する FTP サーバーのポート番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a619-111">Specify the port number on the FTP server to use for the connection.</span></span> <span data-ttu-id="5a619-112">このプロパティの既定値は **21**です。</span><span class="sxs-lookup"><span data-stu-id="5a619-112">The default value of this property is **21**.</span></span>  
  
 <span data-ttu-id="5a619-113">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="5a619-113">**User name**</span></span>  
 <span data-ttu-id="5a619-114">FTP サーバーにアクセスするために使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a619-114">Provide a user name to access the FTP server.</span></span> <span data-ttu-id="5a619-115">このプロパティの既定値は **anonymous**です。</span><span class="sxs-lookup"><span data-stu-id="5a619-115">The default value of this property is **anonymous**.</span></span>  
  
 <span data-ttu-id="5a619-116">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="5a619-116">**Password**</span></span>  
 <span data-ttu-id="5a619-117">FTP サーバーにアクセスするために使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a619-117">Provide the password to access the FTP server.</span></span>  
  
 <span data-ttu-id="5a619-118">**[タイムアウト (秒)]**</span><span class="sxs-lookup"><span data-stu-id="5a619-118">**Time-out (in seconds)**</span></span>  
 <span data-ttu-id="5a619-119">タスクがタイムアウトするまでの秒数を指定します。値**0**は、時間が無制限であることを示します。</span><span class="sxs-lookup"><span data-stu-id="5a619-119">Specify the number of seconds the task takes before timing out. A value of **0** indicates an infinite amount of time.</span></span> <span data-ttu-id="5a619-120">このプロパティの既定値は **60**です。</span><span class="sxs-lookup"><span data-stu-id="5a619-120">The default value of this property is **60**.</span></span>  
  
 <span data-ttu-id="5a619-121">**[パッシブ モードを使用する]**</span><span class="sxs-lookup"><span data-stu-id="5a619-121">**Use passive mode**</span></span>  
 <span data-ttu-id="5a619-122">サーバーまたはクライアントのどちらが接続を開始するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a619-122">Specify whether the server or the client initiates the connection.</span></span> <span data-ttu-id="5a619-123">アクティブ モードではサーバーが接続を開始し、パッシブ モードではクライアントが接続を開始します。</span><span class="sxs-lookup"><span data-stu-id="5a619-123">The server initiates the connection in active mode, and the client activates the connection in passive mode.</span></span> <span data-ttu-id="5a619-124">このプロパティの既定値は **アクティブ モード**です。</span><span class="sxs-lookup"><span data-stu-id="5a619-124">The default value of this property is **active mode**.</span></span>  
  
 <span data-ttu-id="5a619-125">**再試行**</span><span class="sxs-lookup"><span data-stu-id="5a619-125">**Retries**</span></span>  
 <span data-ttu-id="5a619-126">接続を試行する回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a619-126">Specify the number of times the task attempts to make a connection.</span></span> <span data-ttu-id="5a619-127">値 **0** は、無制限に再試行を行うことを示します。</span><span class="sxs-lookup"><span data-stu-id="5a619-127">A value of **0** indicates no limit to the number of attempts.</span></span>  
  
 <span data-ttu-id="5a619-128">**[チャンク サイズ (KB)]**</span><span class="sxs-lookup"><span data-stu-id="5a619-128">**Chunk size (in KB)**</span></span>  
 <span data-ttu-id="5a619-129">データを転送するためのチャンク サイズを KB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="5a619-129">Provide a chunk size in kilobytes for transmitting data.</span></span>  
  
 <span data-ttu-id="5a619-130">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="5a619-130">**Test Connection**</span></span>  
 <span data-ttu-id="5a619-131">FTP 接続マネージャーを構成した後に、 **[接続テスト]** をクリックして、接続が利用可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5a619-131">After configuring the FTP Connection Manager, confirm that the connection is viable by clicking **Test Connection**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a619-132">参照</span><span class="sxs-lookup"><span data-stu-id="5a619-132">See Also</span></span>  
 [<span data-ttu-id="5a619-133">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="5a619-133">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
