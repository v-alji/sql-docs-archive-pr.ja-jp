---
title: 接続済みサーバーの登録
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1d337d2da7d305165307745fb02526e37b53bbd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634772"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a><span data-ttu-id="44058-102">接続済みのサーバーの登録 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="44058-102">Register a Connected Server (SQL Server Management Studio)</span></span>
  <span data-ttu-id="44058-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でサーバーを登録する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="44058-103">This topic describes how to register servers in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="44058-104">サーバーを登録することによって、頻繁にアクセスするサーバーの接続情報を保存しておくことができます。</span><span class="sxs-lookup"><span data-stu-id="44058-104">By registering the server, you can save the connection information for servers that you access frequently.</span></span> <span data-ttu-id="44058-105">サーバーの登録は、接続する前か、またはオブジェクト エクスプローラーから接続するときに実行できます。</span><span class="sxs-lookup"><span data-stu-id="44058-105">A server can be registered before connecting, or at the time of connection from Object Explorer.</span></span>  
  
 <span data-ttu-id="44058-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="44058-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="44058-107">**サーバーを登録する方法:**</span><span class="sxs-lookup"><span data-stu-id="44058-107">**To register a server, using:**</span></span>  
  
     [<span data-ttu-id="44058-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="44058-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="44058-109">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="44058-109">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-register-a-connected-server"></a><span data-ttu-id="44058-110">接続済みのサーバーを登録するには</span><span class="sxs-lookup"><span data-stu-id="44058-110">To register a connected server</span></span>  
  
1.  <span data-ttu-id="44058-111">オブジェクト エクスプローラーで、接続済みのサーバーを右クリックし、 **[登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="44058-111">In Object Explorer, right-click a server to which you already are connected, and then click **Register**.</span></span>  
  
     <span data-ttu-id="44058-112">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="44058-112">**Server name**</span></span>  
     <span data-ttu-id="44058-113">登録するサーバーに使用する名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="44058-113">Enter the name you want to use for the registered server.</span></span> <span data-ttu-id="44058-114">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してローカル サーバーまたはリモート サーバーを登録することにより、以降の接続で使用するサーバー接続情報を格納できます。</span><span class="sxs-lookup"><span data-stu-id="44058-114">Registering a local or remote server using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] lets you store the server connection information for future connections.</span></span> <span data-ttu-id="44058-115">このフィールドの既定値は、サーバーに接続したときに入力したサーバー名です。</span><span class="sxs-lookup"><span data-stu-id="44058-115">This field defaults to the server name entered when you were connecting to the server.</span></span> <span data-ttu-id="44058-116">このサーバー名を維持するか、別の使いやすい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="44058-116">You can retain this server name or enter another easy-to-use name for the server.</span></span>  
  
     <span data-ttu-id="44058-117">**[サーバーの説明]**</span><span class="sxs-lookup"><span data-stu-id="44058-117">**Server description**</span></span>  
     <span data-ttu-id="44058-118">サーバーの説明をオプションで入力します。</span><span class="sxs-lookup"><span data-stu-id="44058-118">Enter an optional description of the server.</span></span> <span data-ttu-id="44058-119">最大 250 文字以内で指定します。</span><span class="sxs-lookup"><span data-stu-id="44058-119">The maximum number of characters allowed is 250.</span></span>  
  
     <span data-ttu-id="44058-120">**[サーバー グループの選択]**</span><span class="sxs-lookup"><span data-stu-id="44058-120">**Select a server group**</span></span>  
     <span data-ttu-id="44058-121">サーバー登録を保存するサーバー グループを選択します。</span><span class="sxs-lookup"><span data-stu-id="44058-121">Select the server group where you want to save the server registration.</span></span>  
  
     <span data-ttu-id="44058-122">**新しいグループ**</span><span class="sxs-lookup"><span data-stu-id="44058-122">**New Group**</span></span>  
     <span data-ttu-id="44058-123">クリックすると、登録するサーバー用の新しいサーバー グループを作成するための **[新しいグループ]** ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="44058-123">Click to launch the **New Group** dialog box, where you can create a new server group for the registered server.</span></span>  
  
     <span data-ttu-id="44058-124">**および**</span><span class="sxs-lookup"><span data-stu-id="44058-124">**Save**</span></span>  
     <span data-ttu-id="44058-125">クリックすると、入力した情報を保存して登録済みサーバーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="44058-125">Click to save the information you have entered and create a registered server.</span></span>  
  
  
