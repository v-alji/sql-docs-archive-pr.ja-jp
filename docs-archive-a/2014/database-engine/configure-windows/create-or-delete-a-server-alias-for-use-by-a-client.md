---
title: クライアントが使用するサーバーの別名を作成または削除する (SQL Server 構成マネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- server alias
helpviewer_keywords:
- aliases [SQL Server], deleting
- aliases [SQL Server], creating
ms.assetid: b687e376-ee33-470d-b65a-87246bfefe6f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: bead257b40c33e3640b18890a7d109d774131123
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641867"
---
# <a name="create-or-delete-a-server-alias-for-use-by-a-client-sql-server-configuration-manager"></a><span data-ttu-id="d4d71-102">クライアントが使用するサーバーの別名の作成または削除 (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="d4d71-102">Create or Delete a Server Alias for Use by a Client (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="d4d71-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で SQL Server 構成マネージャーを使用して、サーバー別名を作成または削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4d71-103">This topic describes how to create or delete a server alias in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using SQL Server Configuration Manager.</span></span> <span data-ttu-id="d4d71-104">別名は、接続のために使用できる代替名です。</span><span class="sxs-lookup"><span data-stu-id="d4d71-104">An alias is an alternate name that can be used to make a connection.</span></span> <span data-ttu-id="d4d71-105">別名は、接続文字列の必須要素をカプセル化したものであり、ユーザーが選択した名前でそれらの要素を公開できます。</span><span class="sxs-lookup"><span data-stu-id="d4d71-105">The alias encapsulates the required elements of a connection string, and exposes them with a name chosen by the user.</span></span> <span data-ttu-id="d4d71-106">別名は、任意のクライアント アプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4d71-106">Aliases can be used with any client application.</span></span> <span data-ttu-id="d4d71-107">サーバーの別名を作成すると、クライアント コンピューターはさまざまなネットワーク プロトコルを使用して複数のサーバーに接続できます。プロトコルおよび接続の詳細をそれぞれ指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d4d71-107">By creating server aliases, your client computer can connect to multiple servers using different network protocols, without having to specify the protocol and connection details for each one.</span></span> <span data-ttu-id="d4d71-108">また、さまざまなネットワーク プロトコルを、たとえ頻繁に使用する必要がないプロトコルであっても常に有効にしておくことができます。</span><span class="sxs-lookup"><span data-stu-id="d4d71-108">In addition, you can also have different network protocols enabled all the time, even if you only need to use them occasionally.</span></span> <span data-ttu-id="d4d71-109">既定以外のポート番号または名前付きパイプで受信するようにサーバーを構成し、SQL Server Browser サービスを無効にした場合は、新しいポート番号または名前付きパイプを指定する別名を作成してください。</span><span class="sxs-lookup"><span data-stu-id="d4d71-109">If you have configured the server to listen on a non-default port number or named pipe, and you have disabled the SQL Server Browser service, create an alias that specifies the new port number or named pipe.</span></span>  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> <span data-ttu-id="d4d71-110">SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="d4d71-110">Using SQL Server Configuration Manager</span></span>  
  
#### <a name="to-create-an-alias"></a><span data-ttu-id="d4d71-111">別名を作成するには</span><span class="sxs-lookup"><span data-stu-id="d4d71-111">To create an alias</span></span>  
  
1.  <span data-ttu-id="d4d71-112">SQL Server 構成マネージャーで、 **[SQL Server Native Client の構成]** を展開し、 **[別名]** を右クリックして、 **[新しい別名]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4d71-112">In SQL Server Configuration Manager, expand **SQL Server Native Client Configuration**, right-click **Aliases**, and then click **New Alias**.</span></span>  
  
2.  <span data-ttu-id="d4d71-113">**[別名]** ボックスに別名を入力します。</span><span class="sxs-lookup"><span data-stu-id="d4d71-113">In the **Alias Name** box, type the name of the alias.</span></span> <span data-ttu-id="d4d71-114">クライアント アプリケーションは、接続時にこの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="d4d71-114">Client applications use this name when they connect.</span></span>  
  
3.  <span data-ttu-id="d4d71-115">**[サーバー]** ボックスに、サーバーの名前または IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d4d71-115">In the **Server** box, type the name or IP address of a server.</span></span> <span data-ttu-id="d4d71-116">名前付きインスタンスの場合は、インスタンス名を追加します。</span><span class="sxs-lookup"><span data-stu-id="d4d71-116">For a named instance append the instance name.</span></span>  
  
4.  <span data-ttu-id="d4d71-117">**[プロトコル]** ボックスで、この別名に使用されるプロトコルを選択します。</span><span class="sxs-lookup"><span data-stu-id="d4d71-117">In the **Protocol** box, select the protocol used for this alias.</span></span> <span data-ttu-id="d4d71-118">プロトコルを選択すると、オプション プロパティ ボックスのタイトルが、[ポート番号]、[パイプ名]、または [接続文字列] に変わります。</span><span class="sxs-lookup"><span data-stu-id="d4d71-118">Selecting a protocol, changes the title of the optional properties box to Port No, Pipe Name, or Connection String.</span></span>  
  
 <span data-ttu-id="d4d71-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーのヘルプに記載されている接続文字列は、独自の接続文字列を作成するプログラマにとって役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="d4d71-119">The connection strings described in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager Help can be useful for programmers who create their own connection strings.</span></span> <span data-ttu-id="d4d71-120">この情報にアクセスするには、 **[新しい別名]** ダイアログ ボックスで、F1 キーを押するか、 **[ヘルプ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4d71-120">To access this information, in the **New Alias** dialog box, press F1, or click **Help**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d4d71-121">構成されている別名で間違ったサーバーやインスタンスに接続する場合は、関連付けられているネットワーク プロトコルを無効にし、次にこれを再び有効にします。</span><span class="sxs-lookup"><span data-stu-id="d4d71-121">If a configured alias is connecting to the wrong server or instance, disable and then reenable the associated network protocol.</span></span> <span data-ttu-id="d4d71-122">これによりキャッシュされた接続情報がクリアされ、クライアントに正しく接続できます。</span><span class="sxs-lookup"><span data-stu-id="d4d71-122">Doing this clears any cached connection information and allows the client to connect correctly.</span></span>  
  
#### <a name="to-delete-an-alias"></a><span data-ttu-id="d4d71-123">別名を削除するには</span><span class="sxs-lookup"><span data-stu-id="d4d71-123">To delete an alias</span></span>  
  
1.  <span data-ttu-id="d4d71-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで、 **[SQL Server Native Client の構成]** を展開し、 **[別名]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4d71-124">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, expand **SQL Server Native Client Configuration**, and then click **Aliases**.</span></span>  
  
2.  <span data-ttu-id="d4d71-125">詳細ペインで、削除する別名を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d4d71-125">In the details pane, right-click the alias that you want to delete, and then click **Delete**.</span></span>  
  
  
