---
title: '[サーバーへの接続] (Integration Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.dtsserver.f1
ms.assetid: 5be897bd-f36c-4c6a-a91a-13d0d016f8b6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8821018c45fdd77c4b3b896afc47b8f5b425af88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740369"
---
# <a name="connect-to-server-integration-services"></a><span data-ttu-id="0b5b1-102">[サーバーへの接続] (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="0b5b1-102">Connect to Server (Integration Services)</span></span>
  <span data-ttu-id="0b5b1-103">このダイアログを使用すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] に接続するときのオプションを表示または指定できます。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-103">Use this dialog to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="0b5b1-104">Options</span><span class="sxs-lookup"><span data-stu-id="0b5b1-104">Options</span></span>  
 <span data-ttu-id="0b5b1-105">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="0b5b1-105">**Server type**</span></span>  
 <span data-ttu-id="0b5b1-106">オブジェクト エクスプローラーからサーバーを登録するときに、接続するサーバーの種類 ( [!INCLUDE[ssDE](../includes/ssde-md.md)]、Analysis Services、Reporting Services、または Integration Services) を選択します。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-106">When registering a server from Object Explorer, select the type of server to connect to: [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services.</span></span> <span data-ttu-id="0b5b1-107">ダイアログの残りの部分には、選択したサーバーの種類に該当するオプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-107">The rest of the dialog shows only the options that apply to the selected server type.</span></span> <span data-ttu-id="0b5b1-108">[登録済みサーバー] を使用してサーバーを登録する場合、[サーバーの種類] ボックスは読み取り専用になり、[登録済みサーバー] コンポーネントに表示されているサーバーの種類と一致する値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-108">When registering a server from Registered Servers, the Server type box is read-only, and matches the type of server displayed in the Registered Servers component.</span></span> <span data-ttu-id="0b5b1-109">別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、[登録済みサーバー] ツール バーの [ [!INCLUDE[ssDE](../includes/ssde-md.md)]]、[Analysis Services]、[Reporting Services]、または [Integration Services] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-109">To register a different type of server, select [!INCLUDE[ssDE](../includes/ssde-md.md)], Analysis Services, Reporting Services, or Integration Services from the Registered Servers toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="0b5b1-110">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="0b5b1-110">**Server name**</span></span>  
 <span data-ttu-id="0b5b1-111">接続するサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-111">Select the server to connect to.</span></span> <span data-ttu-id="0b5b1-112">既定では、最後に接続していたサーバー インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-112">The server instance last connected to is displayed by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0b5b1-113">*\<servername>* \\ *\<instancename>* [!INCLUDE[ssIS](../includes/ssis-md.md)] は、コンピューター上の複数のインスタンスをサポートしていないため、使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-113">Do not use *\<servername>*\\*\<instancename>*, because [!INCLUDE[ssIS](../includes/ssis-md.md)] does not support multiple instances on a computer.</span></span>  
  
 <span data-ttu-id="0b5b1-114">**認証**</span><span class="sxs-lookup"><span data-stu-id="0b5b1-114">**Authentication**</span></span>  
 <span data-ttu-id="0b5b1-115">[!INCLUDE[msCoName](../includes/msconame-md.md)] では [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows 認証だけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-115">Only [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span> <span data-ttu-id="0b5b1-116">Windows 認証モードを使用すると、ユーザーは Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-116">Windows Authentication mode allows a user to connect through a Windows user account.</span></span>  
  
 <span data-ttu-id="0b5b1-117">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="0b5b1-117">**User name**</span></span>  
 <span data-ttu-id="0b5b1-118">[!INCLUDE[ssIS](../includes/ssis-md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-118">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="0b5b1-119">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="0b5b1-119">**Password**</span></span>  
 <span data-ttu-id="0b5b1-120">[!INCLUDE[ssIS](../includes/ssis-md.md)]では Windows 認証しか使用できないため、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-120">This option is not available because only Windows Authentication is available for [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="0b5b1-121">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="0b5b1-121">**Connect**</span></span>  
 <span data-ttu-id="0b5b1-122">クリックすると、上記で選択したサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-122">Click to connect to the server selected above.</span></span>  
  
 <span data-ttu-id="0b5b1-123">**Options**</span><span class="sxs-lookup"><span data-stu-id="0b5b1-123">**Options**</span></span>  
 <span data-ttu-id="0b5b1-124">クリックすると、サーバーの登録やパスワードの保存など、追加のサーバー接続オプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b5b1-124">Click to display additional server connection options, such as registering a server and remembering the password.</span></span>  
  
  
