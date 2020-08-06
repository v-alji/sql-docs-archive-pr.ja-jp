---
title: '[サーバーへの接続]([ログイン] ページ) (Integration Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 285518f4a1f3d9180d2c3c07a41bf75a00ea3593
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740363"
---
# <a name="connect-to-server-login-page-integration-services"></a><span data-ttu-id="a4a5e-102">[サーバーへの接続] ([ログイン] ページ) (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="a4a5e-102">Connect to Server (Login Page) Integration Services</span></span>
  <span data-ttu-id="a4a5e-103">このタブを使用すると、に接続するときに、次のオプションを表示または指定 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-103">Use this tab to view or specify the following options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="a4a5e-104">Options</span><span class="sxs-lookup"><span data-stu-id="a4a5e-104">Options</span></span>  
 <span data-ttu-id="a4a5e-105">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="a4a5e-105">**Server type**</span></span>  
 <span data-ttu-id="a4a5e-106">オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="a4a5e-107">ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="a4a5e-108">[登録済みサーバー] を使用してサーバーを登録する場合、 **[サーバーの種類]** ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-108">When registering a server from Registered Servers, the **Server type** box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="a4a5e-109">別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="a4a5e-110">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="a4a5e-110">**Server name**</span></span>  
 <span data-ttu-id="a4a5e-111">接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-111">Select the server to connect to.</span></span> <span data-ttu-id="a4a5e-112">既定では、最後に接続していたサーバー インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-112">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4a5e-113">*\<servername>* \\ *\<instancename>* [!INCLUDE[ssIS](../includes/ssis-md.md)] は、コンピューター上の複数のインスタンスをサポートしていないため、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-113">Do not use *\<servername>*\\*\<instancename>*, because [!INCLUDE[ssIS](../includes/ssis-md.md)] does not support multiple instances on a computer.</span></span>  
  
 <span data-ttu-id="a4a5e-114">**認証**</span><span class="sxs-lookup"><span data-stu-id="a4a5e-114">**Authentication**</span></span>  
 <span data-ttu-id="a4a5e-115">[!INCLUDE[msCoName](../includes/msconame-md.md)] では [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows 認証だけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-115">Only [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span> <span data-ttu-id="a4a5e-116">Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-116">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="a4a5e-117">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="a4a5e-117">**User name**</span></span>  
 <span data-ttu-id="a4a5e-118">[!INCLUDE[ssIS](../includes/ssis-md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-118">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="a4a5e-119">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="a4a5e-119">**Password**</span></span>  
 <span data-ttu-id="a4a5e-120">[!INCLUDE[ssIS](../includes/ssis-md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-120">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="a4a5e-121">**パスワードの記録**</span><span class="sxs-lookup"><span data-stu-id="a4a5e-121">**Remember password**</span></span>  
 <span data-ttu-id="a4a5e-122">[!INCLUDE[ssIS](../includes/ssis-md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-122">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="a4a5e-123">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="a4a5e-123">**Connect**</span></span>  
 <span data-ttu-id="a4a5e-124">上で選択したサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-124">Connect to the server selected above.</span></span>  
  
 <span data-ttu-id="a4a5e-125">**Options**</span><span class="sxs-lookup"><span data-stu-id="a4a5e-125">**Options**</span></span>  
 <span data-ttu-id="a4a5e-126">クリックすると、ダイアログが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="a4a5e-126">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
  
