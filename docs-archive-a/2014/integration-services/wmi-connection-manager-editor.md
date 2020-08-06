---
title: WMI 接続マネージャーエディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.wmiconnection.f1
helpviewer_keywords:
- WMI Connection Manager Editor
ms.assetid: 0ef2c913-0779-4a07-989e-3361cd83170b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e85cdd2157c8ebe4cb9e6b53f8c3b47ff102a7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644516"
---
# <a name="wmi-connection-manager-editor"></a><span data-ttu-id="bfb39-102">WMI 接続マネージャー エディター</span><span class="sxs-lookup"><span data-stu-id="bfb39-102">WMI Connection Manager Editor</span></span>
  <span data-ttu-id="bfb39-103">**[WMI 接続マネージャー]** ダイアログ ボックスを使用すると、サーバーに対する Microsoft Windows Management Instrumentation (WMI) 接続を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bfb39-103">Use the **WMI Connection Manager** dialog box to specify a Microsoft Windows Management Instrumentation (WMI) connection to a server.</span></span>  
  
 <span data-ttu-id="bfb39-104">WMI 接続マネージャーの詳細については、「 [WMI Connection Manager](connection-manager/wmi-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfb39-104">To learn more about the WMI connection manager, see [WMI Connection Manager](connection-manager/wmi-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="bfb39-105">Options</span><span class="sxs-lookup"><span data-stu-id="bfb39-105">Options</span></span>  
 <span data-ttu-id="bfb39-106">**名前**</span><span class="sxs-lookup"><span data-stu-id="bfb39-106">**Name**</span></span>  
 <span data-ttu-id="bfb39-107">接続マネージャーの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bfb39-107">Provide a unique name for the connection manager.</span></span>  
  
 <span data-ttu-id="bfb39-108">**説明**</span><span class="sxs-lookup"><span data-stu-id="bfb39-108">**Description**</span></span>  
 <span data-ttu-id="bfb39-109">接続マネージャーの説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="bfb39-109">Describe the connection manager.</span></span> <span data-ttu-id="bfb39-110">パッケージを自己文書化して目的を明確にし、保守が容易になるように、接続マネージャーの目的について記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bfb39-110">As a best practice, describe the connection manager in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="bfb39-111">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="bfb39-111">**Server name**</span></span>  
 <span data-ttu-id="bfb39-112">WMI 接続の対象となるサーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bfb39-112">Provide the name of the server to which you want to make the WMI connection.</span></span>  
  
 <span data-ttu-id="bfb39-113">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="bfb39-113">**Namespace**</span></span>  
 <span data-ttu-id="bfb39-114">WMI 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="bfb39-114">Specify the WMI namespace.</span></span>  
  
 <span data-ttu-id="bfb39-115">**Windows 認証を使用する**</span><span class="sxs-lookup"><span data-stu-id="bfb39-115">**Use Windows authentication**</span></span>  
 <span data-ttu-id="bfb39-116">Windows 認証を使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="bfb39-116">Select to use Windows Authentication.</span></span> <span data-ttu-id="bfb39-117">Windows 認証を使用すると、接続の際にユーザー名とパスワードを入力する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="bfb39-117">If you use Windows Authentication, you do not need to provide a user name or password for the connection.</span></span>  
  
 <span data-ttu-id="bfb39-118">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="bfb39-118">**User name**</span></span>  
 <span data-ttu-id="bfb39-119">Windows 認証を使用しない場合、接続に使用するユーザー名を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfb39-119">If you do not use Windows Authentication, you must provide a user name for the connection.</span></span>  
  
 <span data-ttu-id="bfb39-120">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="bfb39-120">**Password**</span></span>  
 <span data-ttu-id="bfb39-121">Windows 認証を使用しない場合、接続に使用するパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfb39-121">If you do not use Windows Authentication, you must provide the password for the connection.</span></span>  
  
 <span data-ttu-id="bfb39-122">**テスト**</span><span class="sxs-lookup"><span data-stu-id="bfb39-122">**Test**</span></span>  
 <span data-ttu-id="bfb39-123">接続マネージャーの設定をテストします。</span><span class="sxs-lookup"><span data-stu-id="bfb39-123">Test the connection manager settings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb39-124">参照</span><span class="sxs-lookup"><span data-stu-id="bfb39-124">See Also</span></span>  
 <span data-ttu-id="bfb39-125">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bfb39-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="bfb39-126">[構成管理のための WMI プロバイダーの概念](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="bfb39-126">[WMI Provider for Configuration Management Concepts](../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="bfb39-127">WMI Provider for Server Events の概念</span><span class="sxs-lookup"><span data-stu-id="bfb39-127">WMI Provider for Server Events Concepts</span></span>](../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
  
  
