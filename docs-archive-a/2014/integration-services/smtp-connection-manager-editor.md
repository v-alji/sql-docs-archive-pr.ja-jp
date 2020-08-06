---
title: SMTP 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.smtpconnection.f1
helpviewer_keywords:
- SMTP Connection Manager Editor
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e14ed49f64b9faca40f575fc6760a8d25c0d4573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742349"
---
# <a name="smtp-connection-manager-editor"></a><span data-ttu-id="d397e-102">SMTP 接続マネージャー エディター</span><span class="sxs-lookup"><span data-stu-id="d397e-102">SMTP Connection Manager Editor</span></span>
  <span data-ttu-id="d397e-103">**[SMTP 接続マネージャー エディター]** ダイアログ ボックスを使用すると、SMTP (Simple Mail Transfer Protocol) サーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d397e-103">Use the **SMTP Connection Manager Editor** dialog box to specify a Simple Mail Transfer Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="d397e-104">SMTP 接続マネージャーの詳細については、「 [SMTP Connection Manager](connection-manager/smtp-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d397e-104">To learn more about the SMTP connection manager, see [SMTP Connection Manager](connection-manager/smtp-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="d397e-105">Options</span><span class="sxs-lookup"><span data-stu-id="d397e-105">Options</span></span>  
 <span data-ttu-id="d397e-106">**名前**</span><span class="sxs-lookup"><span data-stu-id="d397e-106">**Name**</span></span>  
 <span data-ttu-id="d397e-107">接続マネージャーの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d397e-107">Provide a unique name for the connection manager.</span></span>  
  
 <span data-ttu-id="d397e-108">**説明**</span><span class="sxs-lookup"><span data-stu-id="d397e-108">**Description**</span></span>  
 <span data-ttu-id="d397e-109">接続マネージャーの説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="d397e-109">Describe the connection manager.</span></span> <span data-ttu-id="d397e-110">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続マネージャーの目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d397e-110">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="d397e-111">**[SMTP サーバー]**</span><span class="sxs-lookup"><span data-stu-id="d397e-111">**SMTP server**</span></span>  
 <span data-ttu-id="d397e-112">SMTP サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d397e-112">Provide the name of the SMTP server.</span></span>  
  
 <span data-ttu-id="d397e-113">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="d397e-113">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="d397e-114">選択すると、Windows 認証を使用してサーバーへのアクセスを認証する SMTP サーバーで、メールが送信されます。</span><span class="sxs-lookup"><span data-stu-id="d397e-114">Select to send mail using an SMTP server that uses Windows Authentication to authenticate access to the server.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d397e-115">SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d397e-115">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="d397e-116">基本認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d397e-116">It does not support basic authentication.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d397e-117">Microsoft Exchange を SMTP サーバーとして使用する場合は、[ **Windows 認証を使用**する] をに設定することが必要になる場合があり `True` ます。</span><span class="sxs-lookup"><span data-stu-id="d397e-117">When using Microsoft Exchange as the SMTP server, you may need to set **Use Windows Authentication** to `True`.</span></span> <span data-ttu-id="d397e-118">未認証の SMTP 接続を許可しないように Exchange サーバーを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d397e-118">Exchange servers may be configured to disallow unauthenticated SMTP connections.</span></span>  
  
 <span data-ttu-id="d397e-119">**[SSL (Secure Sockets Layer) を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="d397e-119">**Enable Secure Sockets Layer (SSL)**</span></span>  
 <span data-ttu-id="d397e-120">選択すると、電子メール メッセージの送信時に SSL (Secure Sockets Layer) を使用して通信が暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="d397e-120">Select to encrypt communication using Secure Sockets Layer (SSL) when sending e-mail messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d397e-121">参照</span><span class="sxs-lookup"><span data-stu-id="d397e-121">See Also</span></span>  
 [<span data-ttu-id="d397e-122">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="d397e-122">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
