---
title: '[サーバーへの接続] ([ログイン] ページ) (Analysis Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoas.login.f1
ms.assetid: fb012bc8-5105-438a-afcc-74264ebae035
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0cdbb890693c6f00d8515194804b96b6483cb956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740368"
---
# <a name="connect-to-server-login-page-analysis-services"></a><span data-ttu-id="b5055-102">[サーバーへの接続] ([ログイン] ページ) (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="b5055-102">Connect to Server (Login Page) Analysis Services</span></span>
  <span data-ttu-id="b5055-103">このタブを使用すると、に接続するときに、次のオプションを表示または指定 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="b5055-103">Use this tab to view or specify the following options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="b5055-104">Options</span><span class="sxs-lookup"><span data-stu-id="b5055-104">Options</span></span>  
 <span data-ttu-id="b5055-105">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="b5055-105">**Server type**</span></span>  
 <span data-ttu-id="b5055-106">オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5055-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="b5055-107">ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b5055-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="b5055-108">[登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b5055-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="b5055-109">別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5055-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="b5055-110">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="b5055-110">**Server name**</span></span>  
 <span data-ttu-id="b5055-111">接続するサーバー インスタンスを選択します。</span><span class="sxs-lookup"><span data-stu-id="b5055-111">Select the server instance to connect to.</span></span> <span data-ttu-id="b5055-112">既定では、最後に接続していたサーバー インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b5055-112">The server instance last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="b5055-113">**認証**</span><span class="sxs-lookup"><span data-stu-id="b5055-113">**Authentication**</span></span>  
 <span data-ttu-id="b5055-114">Analysis Services のインスタンスに接続するときは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows 認証モードがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b5055-114">The following authentication modes are supported when connecting to an instance of Analysis Services: [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication.</span></span>  
  
 <span data-ttu-id="b5055-115">**Windows 認証モード ([Windows 認証])**</span><span class="sxs-lookup"><span data-stu-id="b5055-115">**Windows Authentication Mode (Windows Authentication)**</span></span>  
 <span data-ttu-id="b5055-116">Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="b5055-116">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="b5055-117">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="b5055-117">**Connect**</span></span>  
 <span data-ttu-id="b5055-118">上で選択したサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="b5055-118">Connect to the server selected above.</span></span>  
  
 <span data-ttu-id="b5055-119">**Options**</span><span class="sxs-lookup"><span data-stu-id="b5055-119">**Options**</span></span>  
 <span data-ttu-id="b5055-120">クリックすると、ダイアログが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="b5055-120">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
