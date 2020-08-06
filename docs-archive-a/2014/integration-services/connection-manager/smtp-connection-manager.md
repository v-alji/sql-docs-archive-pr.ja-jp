---
title: SMTP 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], SMTP
- SMTP connection manager [Integration Services]
- connection managers [Integration Services], SMTP
ms.assetid: 3795d442-714b-4bbb-9acd-75bf277a468a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f3c090ab672790901baae01ae86f8d22e008b4ac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741189"
---
# <a name="smtp-connection-manager"></a><span data-ttu-id="f1e33-102">SMTP 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="f1e33-102">SMTP Connection Manager</span></span>
  <span data-ttu-id="f1e33-103">SMTP 接続マネージャーを使用すると、パッケージから簡易メール転送プロトコル (SMTP) サーバーに接続できます。</span><span class="sxs-lookup"><span data-stu-id="f1e33-103">An SMTP connection manager enables a package to connect to a Simple Mail Transfer Protocol (SMTP) server.</span></span> <span data-ttu-id="f1e33-104">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれるメール送信タスクでは、SMTP 接続マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="f1e33-104">The Send Mail task that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] includes uses an SMTP connection manager.</span></span>  
  
 <span data-ttu-id="f1e33-105">Microsoft Exchange を SMTP サーバーとして使用する場合に、Windows 認証を使用するには SMTP 接続マネージャーの構成を必要とする場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1e33-105">When using Microsoft Exchange as the SMTP server, you may need to configure the SMTP connection manager to use Windows Authentication.</span></span> <span data-ttu-id="f1e33-106">未認証の SMTP 接続を許可しないように Exchange サーバーを構成できます。</span><span class="sxs-lookup"><span data-stu-id="f1e33-106">Exchange servers may be configured to not allow unauthenticated SMTP connections.</span></span>  
  
## <a name="configuration-the-smtp-connection-manager"></a><span data-ttu-id="f1e33-107">SMTP 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="f1e33-107">Configuration the SMTP Connection Manager</span></span>  
 <span data-ttu-id="f1e33-108">SMTP 接続マネージャーをパッケージに追加すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時に SMTP 接続を解決する接続マネージャーが作成され、接続マネージャーのプロパティが設定され、接続マネージャーのパッケージの `Connections` コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f1e33-108">When you add an SMTP connection manager to a package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that will resolve to an SMTP connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span> <span data-ttu-id="f1e33-109">接続マネージャーの `ConnectionManagerType` プロパティは、`SMTP` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f1e33-109">The `ConnectionManagerType` property of the connection manager is set to `SMTP`.</span></span>  
  
 <span data-ttu-id="f1e33-110">SMTP 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="f1e33-110">You can configure an SMTP connection manager in the following ways:</span></span>  
  
-   <span data-ttu-id="f1e33-111">接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1e33-111">Provide a connection string.</span></span>  
  
-   <span data-ttu-id="f1e33-112">SMTP サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1e33-112">Specify the name of an SMTP server.</span></span>  
  
-   <span data-ttu-id="f1e33-113">使用する認証方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1e33-113">Specify the authentication method to use.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f1e33-114">SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f1e33-114">The SMTP connection manager supports only anonymous authentication and Windows Authentication.</span></span> <span data-ttu-id="f1e33-115">基本認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f1e33-115">It does not support basic authentication.</span></span>  
  
-   <span data-ttu-id="f1e33-116">電子メール メッセージを送信するときに、SSL (Secure Sockets Layer) を使用して通信を暗号化するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1e33-116">Specify whether to encrypt communication using Secure Sockets Layer (SSL) when sending e-mail messages.</span></span>  
  
 <span data-ttu-id="f1e33-117">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="f1e33-117">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="f1e33-118">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [SMTP 接続マネージャー エディター](../smtp-connection-manager-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1e33-118">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see [SMTP Connection Manager Editor](../smtp-connection-manager-editor.md).</span></span>  
  
 <span data-ttu-id="f1e33-119">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f1e33-119">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
  
