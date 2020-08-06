---
title: '[サーバーへの接続] (Analysis Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.analysisserver.f1
ms.assetid: 7e277d22-8d4b-422e-8882-7c5dd7a6d915
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b3530f38534e09ef19e77293880129274dfc211b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711022"
---
# <a name="connect-to-server-analysis-services"></a><span data-ttu-id="77b47-102">[サーバーへの接続] (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="77b47-102">Connect to Server (Analysis Services)</span></span>
  <span data-ttu-id="77b47-103">このダイアログを使用すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に接続するときのオプションを表示または指定できます。</span><span class="sxs-lookup"><span data-stu-id="77b47-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="77b47-104">Options</span><span class="sxs-lookup"><span data-stu-id="77b47-104">Options</span></span>  
 <span data-ttu-id="77b47-105">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="77b47-105">**Server type**</span></span>  
 <span data-ttu-id="77b47-106">オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。</span><span class="sxs-lookup"><span data-stu-id="77b47-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="77b47-107">ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="77b47-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="77b47-108">[登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="77b47-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="77b47-109">別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。</span><span class="sxs-lookup"><span data-stu-id="77b47-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="77b47-110">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="77b47-110">**Server name**</span></span>  
 <span data-ttu-id="77b47-111">接続するサーバー インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="77b47-111">Select the server instance to connect to.</span></span> <span data-ttu-id="77b47-112">既定では、最後に接続していたサーバー インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="77b47-112">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="77b47-113">**認証**</span><span class="sxs-lookup"><span data-stu-id="77b47-113">**Authentication**</span></span>  
 <span data-ttu-id="77b47-114">Analysis Services のインスタンスに接続するときは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 認証モードがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="77b47-114">The following authentication modes are supported when connecting to an instance of Analysis Services: [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="77b47-115">**Windows 認証モード ([Windows 認証])**</span><span class="sxs-lookup"><span data-stu-id="77b47-115">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="77b47-116">**Windows 認証**モードを使用すると、ユーザーは windows ユーザーアカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="77b47-116">**Windows Authentication** mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="77b47-117">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="77b47-117">**User name**</span></span>  
 <span data-ttu-id="77b47-118">このオプションは、このリリースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="77b47-118">This option is not available in this release.</span></span> <span data-ttu-id="77b47-119">接続に使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="77b47-119">Enter the user name to connect with.</span></span> <span data-ttu-id="77b47-120">このオプションは、 **Windows 認証**を使用した接続を選択した場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="77b47-120">This option is only available if you have selected to connect using **Windows Authentication**.</span></span>  
  
 <span data-ttu-id="77b47-121">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="77b47-121">**Password**</span></span>  
 <span data-ttu-id="77b47-122">このオプションは、このリリースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="77b47-122">This option is not available in this release.</span></span> <span data-ttu-id="77b47-123">ログインのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="77b47-123">Enter the password for the login.</span></span> <span data-ttu-id="77b47-124">このオプションは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証を使用した接続を選択した場合のみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="77b47-124">This option is only editable if you have selected to connect using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="77b47-125">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="77b47-125">**Connect**</span></span>  
 <span data-ttu-id="77b47-126">クリックすると、上記で選択したサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="77b47-126">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="77b47-127">**Options**</span><span class="sxs-lookup"><span data-stu-id="77b47-127">**Options**</span></span>  
 <span data-ttu-id="77b47-128">クリックすると、サーバーの登録やパスワードの保存など、追加のサーバー接続オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="77b47-128">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
