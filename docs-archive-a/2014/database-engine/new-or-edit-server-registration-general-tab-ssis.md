---
title: '[新規作成] または [サーバー登録の編集] ([全般] タブ) (SSIS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.general.dts.f1
ms.assetid: b586b736-344b-4e42-83ee-96f66ad433a5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 4968c3f98b8bab5b2e641e6fb1e30a6d682f9b50
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644620"
---
# <a name="new-or-edit-server-registration-general-tab-ssis"></a><span data-ttu-id="2d4bb-102">[新規サーバーの登録] または [サーバー登録プロパティの編集] ([全般] タブ) (SSIS)</span><span class="sxs-lookup"><span data-stu-id="2d4bb-102">New or Edit Server Registration (General Tab) (SSIS)</span></span>
  <span data-ttu-id="2d4bb-103">このタブを使用すると、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]を登録するときのオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-103">Use this tab to specify options when registering [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2d4bb-104">このページにアクセスするには、[登録済みサーバー] で、 **[登録済みサーバー]** ツール バーの **[Integration Services]** をクリックし、登録済みサーバー グループを右クリックして、 **[新規作成]** をポイントし、 **[サーバーの登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-104">To access this page, in Registered Servers, click **Integration Services** on the **Registered Servers** toolbar, right-click any registered servers group, point to **New**, and then click **Server Registration**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2d4bb-105">Options</span><span class="sxs-lookup"><span data-stu-id="2d4bb-105">Options</span></span>  
 <span data-ttu-id="2d4bb-106">**サーバーの種類**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-106">**Server type**</span></span>  
 <span data-ttu-id="2d4bb-107">[登録済みサーバー] でサーバーを登録する場合は、 **[サーバーの種類]** ボックスは読み取り専用になっており、そのサーバーは [登録済みサーバー] に表示されるサーバーの種類に一致します。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-107">When a server is registered in Registered Servers, the **Server type** box is read-only, and it matches the type of server displayed in Registered Servers.</span></span> <span data-ttu-id="2d4bb-108">別の種類のサーバーを登録するには、新しいサーバーの登録を開始する前に、**[登録済みサーバー]** ツール バーの **[データベース エンジン]**、**[分析サーバー]**、**[Reporting Services]**、**[SQL Server Compact** **Edition]**、または **[Integration Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-108">To register a different type of server, click **Database Engine**, **Analysis Server**, **Reporting Services**, **SQL Server Compact** **Edition**, or **Integration Services** on the **Registered Servers** toolbar before starting to register a new server.</span></span>  
  
 <span data-ttu-id="2d4bb-109">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-109">**Server name**</span></span>  
 <span data-ttu-id="2d4bb-110">接続先のサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-110">Select the server to which to connect.</span></span> <span data-ttu-id="2d4bb-111">既定では、最後に接続していたサーバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-111">The server last connected to is displayed by default.</span></span>  
  
 <span data-ttu-id="2d4bb-112">**認証**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-112">**Authentication**</span></span>  
 <span data-ttu-id="2d4bb-113">Windows 認証モードを使用すると、ユーザーは [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows ユーザー アカウントを使用して接続できます。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-113">Windows Authentication mode allows a user to connect through a [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows user account.</span></span>  
  
 <span data-ttu-id="2d4bb-114">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-114">**User name**</span></span>  
 <span data-ttu-id="2d4bb-115">このオプションは、このリリースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-115">This option is not available in this release.</span></span>  
  
 <span data-ttu-id="2d4bb-116">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-116">**Password**</span></span>  
 <span data-ttu-id="2d4bb-117">このオプションは、このリリースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-117">This option is not available in this release.</span></span>  
  
 <span data-ttu-id="2d4bb-118">**パスワードの記録**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-118">**Remember password**</span></span>  
 <span data-ttu-id="2d4bb-119">このオプションは、このリリースでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-119">This option is not available in this release.</span></span>  
  
 <span data-ttu-id="2d4bb-120">**[登録済みサーバーの名前]**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-120">**Registered server name**</span></span>  
 <span data-ttu-id="2d4bb-121">**[登録済みサーバー]** に表示する名前です。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-121">The name you want to appear in **Registered Servers**.</span></span> <span data-ttu-id="2d4bb-122">この名前は、 **[サーバー名]** ボックスの名前と一致する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-122">This name does not have to match the **Server name** box.</span></span>  
  
 <span data-ttu-id="2d4bb-123">**[登録済みサーバーの説明]**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-123">**Registered server description**</span></span>  
 <span data-ttu-id="2d4bb-124">サーバーの説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-124">Enter an optional description of the server.</span></span>  
  
 <span data-ttu-id="2d4bb-125">**テスト**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-125">**Test**</span></span>  
 <span data-ttu-id="2d4bb-126">クリックすると、 **[サーバー名]** で選択されたサーバーへの接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-126">Click to test the connection to the server selected in **Server name**.</span></span>  
  
 <span data-ttu-id="2d4bb-127">**および**</span><span class="sxs-lookup"><span data-stu-id="2d4bb-127">**Save**</span></span>  
 <span data-ttu-id="2d4bb-128">クリックすると、[登録済みサーバー] の設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="2d4bb-128">Click to save the Registered Servers settings.</span></span>  
  
  
